# DS-III

**Equipo:** 6
**Integrantes:**
- Juan Manuel Arango 2259571 G51
- Alex García Castañeda 2259517 G51
- Juan Sebastián Gómez Agudelo 2259474 G50
- Stiven Henao Aricapa 2259603 G50
- Víctor Manuel Hernández Ortíz 2259520 G51
- Tina María Torres Tascón 2259729 G51
  
**Fecha:** 20/02/2025  

## 3. Requisitos de Calidad  
Los requisitos de calidad se presentan en forma de **historias de calidad**, siguiendo la estructura de Len Bass.

### **Historias de Calidad**
| **ID**   | **Fuente** | **Estímulo** | **Artefactos** | **Entorno** | **Respuesta** | **Medida de Respuesta** |
|----------|-----------|-------------|---------------|------------|-------------|-----------------|
| **RQ-01** | Desarrollador | Se solicita modificar la lógica de asignación de pedidos para incluir nuevos criterios de prioridad. | Código y configuración de reglas de negocio. | Tiempo de ejecución | Se debe modificar, probar y desplegar la nueva lógica de asignación. | El esfuerzo requerido no debe superar 2 horas de trabajo y no deben generarse más de 2 defectos nuevos. |
| *RQ-02* | Usuario | El usuario desea tiempos de respuesta mejores y una alta fluidez en la interfaz gráfica | Código Frontend (optimización de renderizado y carga de recursos) y estructuración de la interfaz. | Despliegue cuando existe un tráfico alto. | Se debe mejorar la estructura del codigo frontend con la finalidad de optimizar tiempos de carga | El tiempo de carga del frontend debe ser menor a 1.5 segundos en la mayoria de casos y considerando conexion a internet estable. |
| *RQ-03* | Backend Spring Boot | Una solicitud de actualización masiva de precios de productos enviada por el administrador de la tienda. | Microservicio de Gestión de Productos, Base de Datos, Sistema de Logs (Grafana) |Producción, con operaciones CRUD concurrentes sobre el inventario. | El microservicio procesa la actualización de precios en lotes para optimizar el uso de recursos y evitar bloqueos en la base de datos. Se genera un log detallado del proceso y se notifica al administrador cuando la operación finaliza| Tiempo de procesamiento de la actualización masiva (≤ 2 minutos para 1000 productos), porcentaje de actualizaciones exitosas (≥ 99%), tiempo de notificación al administrador (≤ 30 segundos después de completarse la operación).|
| *RQ-04* | Equipo de Seguridad| 	Se ha identificado que algunos microservicios exponen endpoints sin autenticación ni autorización adecuadas, lo que podría permitir accesos no autorizados | API Gateway, autenticación y configuración de permisos en microservicios. | Producción y entornos de prueba con ataques simulados. |Se debe implementar autenticación basada en JWT/OAuth2 en todos los microservicios, aplicar control de acceso basado en roles (RBAC) y restringir tráfico no autorizado en el API Gateway. | Todas las solicitudes a endpoints protegidos deben ser autenticadas y autorizadas correctamente, con una tasa de éxito del 100% en pruebas de seguridad con herramientas como OWASP ZAP o Burp Suite. |
