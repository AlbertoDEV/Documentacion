# Documentación General del Proyecto Restaurant

---

## 00_Introducción

Este documento presenta la visión general del proyecto **Restaurant** desarrollado en https://github.com/AlbertoDEV/Restaurant.  
Incluye los objetivos, alcance, público objetivo y organización de la documentación.

### Objetivos
- Proveer una plataforma para gestionar reservas, pedidos y administración de un restaurante.  
- Orientar tanto a usuarios finales (clientes del restaurante) como al equipo técnico en la comprensión del sistema.

### Alcance
- Usuarios: clientes, camareros, administradores.  
- Funcionalidades: catálogo de platos, carrito de pedidos, reservas de mesas, gestión de usuarios, panel de administración.  
- Tecnologías usadas: (mencionar lenguaje, framework, base de datos, etc.)

### Audiencia de la documentación
- Desarrolladores del proyecto.  
- Equipo de QA y mantenimiento.  
- Administradores del restaurante.

### Organización de la documentación
La documentación se organiza en secciones que cubren desde los requisitos hasta la arquitectura, modelado, interfaz, despliegue y mantenimiento.

---

## 01_Requisitos

### Requisitos funcionales
1. El cliente debe poder ver el menú del restaurante.  
2. El cliente puede añadir platos al carrito y realizar un pedido.  
3. El cliente puede reservar una mesa indicando fecha, hora y número de comensales.  
4. El administrador debe poder gestionar el menú (añadir, eliminar, modificar platos).  
5. El camarero/administrador puede ver los pedidos en curso, cambiar estado (preparando, listo, entregado).  
6. El administrador puede ver estadísticas de ventas, reservas y usuarios.

### Requisitos no funcionales
- Rendimiento: la página de inicio debe cargarse en menos de 3 s en condiciones normales.  
- Seguridad: autenticación para roles de administrador y camarero.  
- Escalabilidad: permitir agregar nuevos módulos (por ejemplo delivery) en el futuro.  
- Usabilidad: interfaz clara, adaptada a móviles.  
- Compatibilidad: soportar los últimos dos navegadores estándar.

### Restricciones
- Base de datos relacional (por ejemplo PostgreSQL).  
- Despliegue en contenedor Docker.  
- Las imágenes de los platos no deben superar 500 KB.

### Suposiciones
- Se asume que el restaurante ya dispone de una infraestructura de red.  
- Los usuarios pueden tener conexión a Internet estable.

---

## 02_Arquitectura

### Visión general
El proyecto se estructura en tres capas principales: presentación (frontend), lógica de negocio (backend) y persistencia (base de datos).  

### Componentes principales
- Frontend: aplicación web basada en React o Vue.  
- Backend: API REST construida con Node.js/Express.  
- Base de datos: PostgreSQL para datos estructurados.

### Patrones de arquitectura
- Separación de capas.  
- Comunicación mediante API REST/JSON.

### Diagrama arquitectónico
(incluir un diagrama o referencia)

### Tecnología
- Servidor Web: Nginx o Apache.  
- Contenedores Docker.  
- Autenticación JWT.

---

## 03_Modelado

### Modelo de dominio
- Usuario (id, nombre, email, rol).  
- Restaurante (id, nombre, dirección, horario).  
- Plato (id, nombre, descripción, precio, categoría, imagen).  
- Pedido (id, usuarioId, fechaHora, estado, total).  
- DetallePedido (id, pedidoId, platoId, cantidad, precioUnitario).  
- Reserva (id, usuarioId, fechaHora, numComensales, estado).

### Relaciones entre entidades
- Un usuario puede hacer muchos pedidos.  
- Un pedido tiene muchos detalles de pedido.  
- Un usuario puede realizar muchas reservas.

### Diagrama entidad‑relación
(ver anexo de diagramas)

---

## 04_Interface_Usuario

### Pantallas principales
- **Inicio:** menú, reservas, contacto, login/registro.  
- **Menú de platos:** listado con filtro por categoría.  
- **Carrito:** resumen de platos seleccionados.  
- **Reservas:** formulario para seleccionar fecha/hora.  
- **Panel de administración:** gestión de platos, pedidos y reservas.

### Directrices de diseño
- Interfaz responsiva.  
- Colores corporativos.  
- Accesibilidad.

---

## 05_Logica_Negocio

### Reglas de negocio
- Un pedido no puede modificarse una vez entregado.  
- Una reserva sólo se confirma si hay mesas disponibles.  
- El total se calcula como suma de cantidad × precio.  
- Solo administradores pueden modificar el menú.

### Flujo de pedido
1. Usuario selecciona platos.  
2. Confirma pedido.  
3. Estado pasa de “Pendiente” a “Preparando” y “Entregado”.

---

## 06_Datos_Persistencia

### Base de datos
PostgreSQL como base relacional.  
Imágenes en sistema de archivos o servicio S3.

### Mecanismos de acceso
- ORM: Sequelize o TypeORM.  
- CRUD para cada entidad.

### Backup y seguridad
- Copia diaria.  
- Hash de contraseñas (bcrypt).  
- Roles diferenciados.

---

## 07_Despliegue

### Entornos
- Desarrollo local con Docker.  
- Producción en servidor remoto.

### Pasos
1. Build Docker.  
2. Push a registro.  
3. Deploy con Compose o Kubernetes.  
4. Configurar variables de entorno.  
5. Verificar logs.

---

## 08_Mantenimiento

### Plan
- Revisión mensual de dependencias.  
- Optimización de base de datos trimestral.  
- Prueba de backup semestral.

### Incidencias
- Sistema de tickets.  
- Respuesta en 24 h para errores críticos.

---

## 09_Glosario

| Término | Definición |
|---------|-------------|
| Usuario | Persona que utiliza el sistema (cliente, camarero, admin). |
| Plato | Elemento del menú del restaurante. |
| Pedido | Conjunto de platos seleccionados por un usuario. |
| Reserva | Petición de mesa para fecha/hora específicas. |
| Rol | Categoría de usuario con permisos definidos. |
| Estado | Fase del pedido o reserva. |

---

## 10_Anexo A – Diagramas
Contiene diagramas de arquitectura, ER y flujo de procesos.

---

## 10_Anexo B – Uso de APIs

### Autenticación
POST /api/auth/login
```
{
  "email": "usuario@example.com",
  "password": "********"
}
```

### Obtener menú de platos
GET /api/platos

### Crear pedido
POST /api/pedidos
```
{
  "usuarioId": 1,
  "detalles": [
    { "platoId": 3, "cantidad": 2 }
  ]
}
```
