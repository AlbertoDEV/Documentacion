# **Especificación de Requisitos de Software (ERS/SRS) \- Portafolio Unificado**

Fecha: 30 de septiembre de 2025  
Versión: 1.0 (Base)  
Propósito: Definir los requisitos funcionales y no funcionales que deben cumplirse para cada versión del proyecto de portafolio.

## **1\. Introducción y Requisitos Generales**

### **1.1 Objetivos del Sistema**

1. Servir como tarjeta de presentación profesional del desarrollador.  
2. Centralizar el acceso a todos los proyectos individuales (existentes y futuros).  
3. Demostrar la capacidad del desarrollador para gestionar el ciclo de vida completo de una aplicación (Front-end, Back-end, Bases de Datos, CI/CD).  
4. Evolucionar la arquitectura de los proyectos de forma estructurada.

### **1.2 Requisitos No Funcionales (RNF)**

|

| ID | Categoría | Descripción |  
| RNF-001 | Rendimiento | Los tiempos de carga del Front-end del Portfolio (V1.0) no deben superar los 2 segundos. |  
| RNF-002 | Seguridad | Implementación de medidas básicas de seguridad (e.g., CORS, headers) en los Back-ends de Spring Boot. |  
| RNF-003 | Usabilidad | Diseño 100% responsivo para todos los Front-ends. |  
| RNF-004 | Mantenibilidad | Todos los proyectos deben incluir un archivo README.md detallado. |  
| RNF-005 | Despliegue | Todos los componentes deben estar orquestados y desplegados mediante Railway. |

## **2\. Requisitos por Versión**

### **Versión 1.0: Requisitos Funcionales (RF-V1.0)**

| ID | Descripción | Prioridad |  
| RF-101 | Presentación Personal: El Front-end del Portfolio debe mostrar una biografía, habilidades y datos de contacto del desarrollador. | Alta |  
| RF-102 | Listado de Proyectos Completos: Debe enlazar a los tres proyectos Back/Front/DB independientes. | Alta |  
| RF-103 | Listado de Muestras: Debe mostrar una sección para los proyectos simples (solo HTML/CSS/JS) con acceso directo. | Media |  
| RF-104 | Enlace a Repositorio: Debe proporcionar un enlace visible al repositorio de GitHub del Portafolio. | Alta |  
| RF-105 | Proyectos Aislados: Los tres proyectos completos deben funcionar como aplicaciones monolíticas independientes. | Alta |

### **Versión 2.0: Requisitos Funcionales (RF-V2.0)**

* Asume la consolidación y migración de los elementos de V1.0.  
  | ID | Descripción | Prioridad |  
  | :--- | :--- | :--- |  
  | RF-201 | Portal Unificado: El Front-end debe permitir el acceso a las funcionalidades de los tres proyectos completos sin recargar la página principal (SPA/Navegación simulada). | Alta |  
  | RF-202 | Acceso a Microservicio: El Front-end debe consumir el Microservicio de Login (RF-203) para autenticación de usuarios. | Alta |  
  | RF-203 | Microservicio de Login/Auth: Creación de un servicio Back-end dedicado (Spring Boot) para gestionar el registro y el inicio de sesión de usuarios de forma centralizada. | Alta |  
  | RF-204 | Esquemas Separados: La nueva Base de Datos centralizada debe mantener esquemas de datos separados y aislados lógicamente para cada proyecto. | Alta |

### **Versión 3.0: Requisitos Funcionales (RF-V3.0)**

* Asume que V2.0 está implementado y funcionando.  
  | ID | Descripción | Prioridad |  
  | :--- | :--- | :--- |  
  | RF-301 | Migración a Angular: El Front-end unificado (de V2.0) debe ser reescrito utilizando el framework Angular. | Alta |  
  | RF-302 | Diseño Estándar (Figma): El Front-end en Angular debe implementar el diseño y las directrices de UI/UX creadas en Figma. | Alta |  
  | RF-303 | UI Kit Componentizado: Implementación de un conjunto de componentes de interfaz reutilizables en Angular (basados en Figma) para garantizar la coherencia visual en todos los proyectos. | Alta |  
  | RF-304 | Documentación de Diseño: Creación de un documento de especificación de diseño detallado a partir del archivo de Figma. | Media |