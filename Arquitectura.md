

# Documento de Arquitectura del Sistema de Gestión de Órdenes y Entregas

## 1. Introducción  
Este documento describe la arquitectura inicial del sistema de gestión de órdenes y entregas, incluyendo requisitos funcionales, requisitos de calidad y restricciones clave que deben ser consideradas en el diseño del software.

**Equipo:** 6

**Integrantes:**
- Juan Manuel Arango 2259571 G51
- Alex García Castañeda 2259517 G51
- Juan Sebastián Gómez Agudelo 2259474 G50
- Stiven Henao Aricapa 2259603 G50
- Víctor Manuel Hernández Ortíz 2259520 G51
- Tina María Torres Tascón 2259729 G51
  
**Fecha:** 20/02/2025  

---

## 2. Requisitos Funcionales  
Los requisitos funcionales se presentan en forma de **historias de usuario**, especificando los **criterios de aceptación**.

### **Historias de Usuario**
| **ID**    | **Historia de Usuario**                                                                                                           | **Criterios de Aceptación**                                                                                                                                                                                                                                                                                            |
| --------- | --------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **US-01** | Como cliente registrado, quiero iniciar sesión en la plataforma para acceder a mi historial de pedidos y realizar nuevas compras. | - El usuario debe ingresar un correo y contraseña válidos.<br>- Si las credenciales son correctas, el usuario es redirigido a su perfil.<br>- Si las credenciales son incorrectas, se muestra un mensaje de error sin revelar detalles específicos.<br>- El usuario puede solicitar un restablecimiento de contraseña. |
| **US-02** | Como nuevo cliente, quiero poder registrarme en la plataforma con mi correo y una contraseña, para poder realizar compras y gestionar mis pedidos. | - El sistema debe permitir el registro con un correo electrónico único y una contraseña segura. <br> - La contraseña debe cumplir con requisitos mínimos de seguridad. <br> - Si el usuario intenta registrarse con un correo ya en uso, debe recibir un mensaje de error. <br> - Si se cumple con lo adecuado se debe redirigir al perfil del us                                                                                                                                                                                                                                                                                   |
| **US-03** | _[Agregar historia de usuario]_                                                                                                   | _[Agregar criterios de aceptación]_                                                                                                                                                                                                                                                                                    |
| **US-04** | _[Agregar historia de usuario]_                                                                                                   | _[Agregar criterios de aceptación]_                                                                                                                                                                                                                                                                                    |

>  **Instrucciones:**  
> - Completar al menos **tres historias de usuario**.  
> - Asegurar que cada historia tenga criterios de aceptación claros y verificables.  

---

## 3. Requisitos de Calidad  
Los requisitos de calidad se presentan en forma de **historias de calidad**, siguiendo la estructura de Len Bass.

### **Historias de Calidad**
| **ID**   | **Fuente** | **Estímulo** | **Artefactos** | **Entorno** | **Respuesta** | **Medida de Respuesta** |
|----------|-----------|-------------|---------------|------------|-------------|-----------------|
| **RQ-01** | Desarrollador | Se solicita modificar la lógica de asignación de pedidos para incluir nuevos criterios de prioridad. | Código y configuración de reglas de negocio. | Tiempo de ejecución | Se debe modificar, probar y desplegar la nueva lógica de asignación. | El esfuerzo requerido no debe superar 2 horas de trabajo y no deben generarse más de 2 defectos nuevos. |
| *RQ-02* | Usuario | El usuario desea tiempos de respuesta mejores y una alta fluidez en la interfaz gráfica | Código Frontend (optimización de renderizado y carga de recursos) y estructuración de la interfaz. | Despliegue cuando existe un tráfico alto. | Se debe mejorar la estructura del codigo frontend con la finalidad de optimizar tiempos de carga | El tiempo de carga del frontend debe ser menor a 1.5 segundos en la mayoria de casos y considerando conexion a internet estable. |
| *RQ-03* | Backend Spring Boot | Una solicitud de actualización masiva de precios de productos enviada por el administrador de la tienda. | Microservicio de Gestión de Productos, Base de Datos, Sistema de Logs (Grafana) |Producción, con operaciones CRUD concurrentes sobre el inventario. | El microservicio procesa la actualización de precios en lotes para optimizar el uso de recursos y evitar bloqueos en la base de datos. Se genera un log detallado del proceso y se notifica al administrador cuando la operación finaliza| Tiempo de procesamiento de la actualización masiva (≤ 2 minutos para 1000 productos), porcentaje de actualizaciones exitosas (≥ 99%), tiempo de notificación al administrador (≤ 30 segundos después de completarse la operación).|
| *RQ-04* | Equipo de Seguridad| 	Se ha identificado que algunos microservicios exponen endpoints sin autenticación ni autorización adecuadas, lo que podría permitir accesos no autorizados | API Gateway, autenticación y configuración de permisos en microservicios. | Producción y entornos de prueba con ataques simulados. |Se debe implementar autenticación basada en JWT/OAuth2 en todos los microservicios, aplicar control de acceso basado en roles (RBAC) y restringir tráfico no autorizado en el API Gateway. | Todas las solicitudes a endpoints protegidos deben ser autenticadas y autorizadas correctamente, con una tasa de éxito del 100% en pruebas de seguridad con herramientas como OWASP ZAP o Burp Suite. |

>  **Instrucciones:**  
> - Completar al menos **tres historias de calidad**, alineadas con atributos clave como **rendimiento, escalabilidad y seguridad**.  
> - Definir cómo se medirá la respuesta esperada ante la situación planteada.  

---

## 4. Restricciones del Sistema  
Las restricciones establecen **limitaciones** en la arquitectura del sistema, ya sean tecnológicas, de negocio, regulatorias o de infraestructura.

### **Lista de Restricciones**
| **Tipo de Restricción** | **Descripción** |
|------------------------|----------------|
| Tecnológica | El sistema debe desarrollarse utilizando **Spring Boot y PostgreSQL**, debido a la infraestructura actual de la empresa y su compatibilidad con otros sistemas internos. |
| _[Agregar otro tipo]_ | _[Describir la restricción]_ |

>  **Tipos de restricciones:**  
> - **Tecnológicas:** Lenguajes, frameworks o herramientas que deben utilizarse.  
> - **De negocio:** Normativas o estándares de la empresa.  
> - **Regulatorias:** Cumplimiento de normativas legales o de seguridad.  
> - **De infraestructura:** Limitaciones en hardware, red o almacenamiento.  


---

## 5. Formato de Entrega  
- **Formato:** Markdown (`.md`) en el repositorio de Codelabs, El documento debe llamarse `Arquitectura.md`.  
- **Extensión máxima:** 3 páginas.  

---

## **Tiempo estimado para completar el ejercicio: 50 minutos**  
**15 min** → Definir **3 historias de usuario con criterios de aceptación**.  
**15 min** → Definir **3 historias de calidad alineadas con atributos clave**.  
**10 min** → Identificar **2 restricciones relevantes**.  
**10 min** → Revisión y ajustes finales del documento.  
