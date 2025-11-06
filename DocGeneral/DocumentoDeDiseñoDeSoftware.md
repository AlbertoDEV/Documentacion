# **Documento de Diseño de Software (DDS/SDD) \- Arquitectura Evolutiva del Portafolio**

Fecha: 30 de septiembre de 2025  
Propósito: Describir la arquitectura técnica y las decisiones de diseño para la implementación de las tres versiones del proyecto de portafolio.

## **1\. Diseño Arquitectónico (Evolución)**

### **1.1. Arquitectura V1.0: "Micro-monolitos"**

* **Estructura:** El sistema es una colección de aplicaciones independientes y aisladas.  
* **Componentes Principales:**  
  1. **Portfolio Front-end:** (HTML/CSS/JS) \- Funciona como un sitio web estático.  
  2. **Proyecto Completo A, B, C:** (Cada uno es un Monolito de 3 capas: Front-end, Back-end Spring Boot, Base de Datos PostgreSQL dedicada).  
  3. **Proyectos Simples:** (HTML/CSS/JS) \- Archivos estáticos.  
* **Interacción:** El Portfolio Front-end se conecta con los Proyectos Completos únicamente a través de **enlaces de navegación externos** (URLs). No hay comunicación a nivel de API entre el Portfolio y los proyectos.  
* **Despliegue:** 5+ servicios separados en Railway (1 Portfolio, 3 Back-ends, 3+ Front-ends, 3 Bases de Datos).

### **1.2. Arquitectura V2.0: "Microservicios Introductorios"**

* **Objetivo:** Reducir el acoplamiento y centralizar servicios transversales.  
* **Componentes Principales:**  
  1. **Portal Unificado Front-end:** (Front-end Monolítico) \- Actúa como una aplicación de una sola página (SPA).  
  2. **Microservicio de Autenticación (Auth-MS):** (Spring Boot) \- Maneja Login/Registro.  
  3. **Back-ends de Proyecto (A, B, C):** (Spring Boot) \- Se enfocan en la lógica de negocio específica de cada proyecto.  
  4. **Base de Datos Centralizada:** (Una única instancia de PostgreSQL).  
* **Interacción:**  
  * El Portal Unificado consume el Auth-MS para la identidad del usuario y los Back-ends de Proyecto para las funcionalidades.  
  * Los Back-ends de Proyecto (A, B, C) acceden a la misma instancia de Base de Datos, utilizando credenciales y esquemas diferentes para garantizar el aislamiento lógico de los datos.  
* **Despliegue:** 4+ servicios separados en Railway (1 Front-end, 1 Auth-MS, 3 Back-ends de Proyecto, 1 Base de Datos central).

### **1.3. Arquitectura V3.0: "Estandarización y Modernización"**

* **Objetivo:** Mejorar la experiencia de usuario y la mantenibilidad del Front-end.  
* **Componentes Principales:**  
  1. **Portal Unificado Angular:** (Reemplaza el Front-end de V2.0) \- Utiliza componentes de Angular y un UI Kit.  
  2. **Backend:** Mantiene la arquitectura de microservicios y base de datos de V2.0.  
* **Diseño UX/UI:**  
  * **Herramienta:** Figma para diseño y prototipado.  
  * **Estrategia:** Creación de un sistema de diseño atómico (Design System) con colores primarios, tipografía (Inter), espaciado, y componentes reutilizables (botones, tarjetas, formularios).  
* **Tecnología Front-end:** Se migra a **Angular** para:  
  * Mejor modularización del código.  
  * Aprovechamiento de la inyección de dependencias para servicios.  
  * Coherencia en la gestión del estado.

## **2\. Tecnologías y Estándares**

| Capa | V1.0 (Inicial) | V2.0 (Transición) | V3.0 (Meta) | Razón de la Elección |  
| Front-end | HTML/CSS/JS (Vanilla) | HTML/CSS/JS (SPA) | Angular | Estandarización, Componentización y Escalabilidad. |  
| Back-end | Spring Boot (Monolítico) | Spring Boot (Microservicios) | Spring Boot (Microservicios) | Experiencia del desarrollador, robustez, ecosistema Java. |  
| Base de Datos | PostgreSQL (3 Instancias) | PostgreSQL (1 Instancia, 3 Esquemas) | PostgreSQL (1 Instancia, 3 Esquemas) | Potencia, confiabilidad y soporte para múltiples esquemas. |  
| Diseño | N/A (Estilo libre) | N/A | Figma | Creación de un lenguaje visual y UI Kit profesional. |  
| Despliegue | Railway | Railway | Railway | Facilidad y soporte para múltiples servicios y bases de datos. |

## **3\. Estrategia de Control de Versiones y Despliegue**

* **Control de Versiones:** Git con ramificación main (producción), develop (pre-producción) y *feature branches* por cada funcionalidad/bug.  
* **CI/CD:** Se utilizará un flujo automatizado de GitHub Actions.  
  1. Push a *feature branch* \-\> Pruebas unitarias/integración.  
  2. Merge a develop \-\> Despliegue automático a Pre-producción (entorno de *staging*).  
  3. Merge a main \-\> Despliegue manual o *push-button* a Producción.