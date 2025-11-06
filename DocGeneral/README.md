# **Proyecto Unificado: Evolución y Reorganización del Portafolio**

## **Introducción**

Este *"proyecto"* es más que un proyecto en sí: es una **reorganización integral** de mis desarrollos personales, no sólo para **publicarlos**, sino también para **demostrar mis capacidades** tanto **técnicas** (programación, arquitectura, despliegue) como **blandas** (*soft skills*) tales como el uso de **Git**, el **proceso de análisis**, la **planificación**, la **documentación técnica** y la **capacidad de mejora continua** de proyectos existentes.

El objetivo es unificar, documentar y evolucionar un conjunto de proyectos previos, construyendo una plataforma profesional que sirva como portafolio técnico y espacio demostrativo.

---

## **1. Resumen Ejecutivo**

El proyecto busca **centralizar y profesionalizar** una colección de desarrollos independientes, organizándolos dentro de un **portafolio principal**.  
Se ejecutará en **tres versiones evolutivas**:

* **V1.0:** Arquitectura inicial basada en micro-monolitos independientes.  
* **V2.0:** Transición a una arquitectura de microservicios con base de datos unificada.  
* **V3.0:** Modernización del front-end mediante Angular y estandarización del diseño UI/UX con Figma.

---

## **2. Objetivos del Sistema**

1. Servir como **tarjeta de presentación profesional** del desarrollador.  
2. **Centralizar el acceso** a todos los proyectos individuales (existentes y futuros).  
3. Mostrar la **capacidad de gestión del ciclo de vida completo** de aplicaciones (Front-end, Back-end, Bases de Datos, CI/CD).  
4. Aplicar una **evolución estructurada y documentada** de la arquitectura.  
5. Consolidar una **metodología profesional** de desarrollo, control de versiones y despliegue.

---

## **3. Estructura de Versiones y Roadmap**

### **Versión 1.0 – Unificación Inicial y Presentación (MVP)**

- **Objetivo:** Reunir los proyectos existentes en un portafolio único.  
- **Arquitectura:** “Micro-monolitos” independientes (Front, Back y DB).  
- **Tecnologías:** HTML/CSS/JS, Spring Boot, PostgreSQL, Railway.  
- **Entregable:** Sitio principal con biografía, habilidades, enlaces a proyectos y repositorios.

### **Versión 2.0 – Unificación Arquitectónica y Microservicios**

- **Objetivo:** Reducir acoplamiento y mejorar escalabilidad.  
- **Arquitectura:** Microservicios con base de datos centralizada (PostgreSQL, múltiples esquemas).  
- **Novedades:**  
  - Front-end SPA unificado.  
  - Microservicio de autenticación.  
  - CI/CD mediante GitHub Actions.  
- **Entregable:** Plataforma unificada con identidad de usuario y comunicación entre módulos.

### **Versión 3.0 – Estandarización UX/UI y Modernización**

- **Objetivo:** Mejorar experiencia de usuario y mantenibilidad.  
- **Arquitectura:** Mantiene microservicios y BD unificada.  
- **Tecnologías:** Angular, Figma, UI Kit propio.  
- **Entregable:** Front-end moderno con componentes reutilizables y diseño estandarizado.

---

## **4. Diseño Arquitectónico Evolutivo**

| Versión | Front-end | Back-end | Base de Datos | Despliegue |  
| :-- | :-- | :-- | :-- | :-- |  
| **V1.0** | HTML/CSS/JS (estático) | Spring Boot (monolítico) | PostgreSQL (3 instancias) | Railway |  
| **V2.0** | SPA (JS unificado) | Spring Boot (microservicios + Auth) | PostgreSQL (1 instancia, 3 esquemas) | Railway + CI/CD |  
| **V3.0** | Angular + UI Kit Figma | Spring Boot (microservicios) | PostgreSQL (unificada) | Railway |

**Gestión de versiones y despliegue:**

- Flujo Git con ramas `main`, `develop`, y *feature branches*.  
- Automatización con GitHub Actions para pruebas, integración y despliegue.  
- Enfoque modular y escalable, con documentación continua.

---

## **5. Requisitos Clave**

### **Funcionales**
- Mostrar biografía, habilidades y contacto.  
- Listar proyectos completos y simples.  
- Enlazar repositorios GitHub.  
- Autenticación centralizada (desde V2.0).  
- Migración a Angular y diseño estandarizado (V3.0).

### **No Funcionales**
- Carga del Front-end < 2 segundos.  
- Seguridad básica (CORS, headers).  
- Diseño responsivo.  
- Documentación exhaustiva (`README.md` en cada módulo).  
- Despliegue orquestado en Railway.

---

## **6. Infraestructura y Entornos**

| Entorno | Descripción | Proveedor | Despliegue |  
| :-- | :-- | :-- | :-- |  
| **Integración (CI)** | Pruebas automáticas unitarias/integración | GitHub Actions | Automático |  
| **Pre-Producción** | Validación final antes del release | Railway | Semi-automático |  
| **Producción** | Acceso público | Railway | Manual/Controlado |

---

## **7. Gestión de Riesgos**

| Riesgo | Impacto | Mitigación |  
| :-- | :-- | :-- |  
| Acoplamiento de datos | Fallos en cascada | Esquemas aislados y redundancia |  
| Complejidad de microservicios | Latencia o debugging difícil | Uso de API Gateway y Swagger |  
| Retraso en migración a Angular | Curva de aprendizaje | Modularización desde V2.0 |

---

## **8. Conclusión**

Este proyecto refleja no solo la **capacidad técnica** del desarrollador, sino también su **madurez profesional**, su enfoque en la **documentación**, la **organización** y la **mejora continua**.  
Más allá de un portafolio, es un **laboratorio evolutivo de software**, diseñado para demostrar conocimientos de **arquitectura, desarrollo ágil, control de versiones y despliegue profesional.**
