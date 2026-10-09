![Escudo ESPE](assets/image.png)

# Universidad de las Fuerzas Armadas "ESPE"
## Nombre
Carlos Campoverde
Mateo Jarén García Galarza
Jonathan Javier Jaguaco Quituisaca
Erick Patricio Obando Zapato
## Asignatura:
36902-Desarrollo de Software Seguro

## Docente:
Angel Geovanny Cudco Pomoguali


# SecurityShop_ObandoJaguacoCampoverde
SecurityShop
# Actividad 1:

* Crear un repositorio de Github
* Identificar al menos diez activos de SecureShop:
  * Información de usuarios
  * Credenciales
  * Catálogo de productos
  * Precio de productos
  * Microservicio de usuario 
  * MIcroservicio de producto
  * Microservicio de pedido
  * Procesamiento de pago
  * Base de datos de productos
  * Información de pedidos
  * Código fuente de los microservicios
  * Logs y registros de auditoría
  * Base de datos de pedidos
  * Base de datos de usuarios
  * API Gateway 
  * Tokens de sesión (JWT)
  * Carrito de compras
  * Certificados SSL/TLS
  * Sistema de notificaciones
  * Secrets y claves de cifrado



* Clasificar cada activo según:
  * información;
  * software;
  * servicio;
  * infraestructura;
  * datos.

### Responder:
**¿Qué consecuencias tendría para SecureShop que este activo fuera accedido, modificado o quedara indisponible?**

| Activo | Tipo | Consecuencia (Acceso / Modificación / Indisponibilidad) | 3 Amenazas | Control |
| :--- | :--- | :--- | :--- | :--- |
| **Información de usuarios** | Información | Se podría exponer información de los usuarios, afectando su privacidad y confianza en SecureShop. | - Suplantación de identidad<br>- Filtración de datos personales<br>- Alteración de datos personales | Cifrado Absoluto de Datos |
| **Credenciales** | Información sensible | Un acceso no autorizado podría permitir que terceros entren a las cuentas de los usuarios. | - Eliminación de credenciales<br>- Manipulación de información personal<br>- Secuestro de cuenta | Implementar autenticación Multifactor (MFA) |
| **Catálogo de productos** | Información | Su modificación podría mostrar precios, características o productos incorrectos. | - Inyección SQL<br>- Modificación del stock de productos<br>- Modificación de la descripción de productos | Zero Trust, nunca validar el producto basándose en los datos que se envían desde el navegador. |
| **Precio de Productos** | Información | Realizar compras de varios productos al precio más bajo posible, afectando el stock y el dinero obtenido para SecureShop. | - Fraude por interceptación<br>- Sabotaje del catálogo de productos<br>- Ataque de condición de carrera para pagar solo por una compra al hacer múltiples órdenes | Validación estricta en el servidor con bloqueos transaccionales |
| **Microservicio de usuario** | Software | Fallas en el registro y autenticación de los usuarios al intentar loguearse, provocando desconfianza en la tienda. | - Caída del servidor<br>- Bloqueo erróneo de cuentas legítimas<br>- Lentitud al procesar registros o validaciones | Implementar un servicio de autenticación desacoplado al microservicio del usuario. |
| **Microservicio de producto** | Software | La administración de los productos podría dejar de funcionar correctamente, dando valores de stock o precios incorrectos. | - Desincronización con el inventario real<br>- Error en la caché mostrando precios erróneos o antiguos<br>- Caída de la base de datos de los productos | Usar un intermediario para cualquier cambio en el stock o precio, notificando de inmediato y de forma asíncrona. |
| **Microservicio de pedido** | Software | Los clientes no podrían crear, modificar, realizar o consultar sus pedidos. | - Errores al guardar transacciones<br>- Fallas en la consulta para ver el historial y pedidos<br>- Pérdida de comunicación con la pasarela de pagos | Implementar un mecanismo para cortar temporalmente las peticiones repetitivas activando un mecanismo (Circuit Breaker / Rate Limiting). |
| **Procesamiento de pago** | Servicio | Obtener información de pago de los usuarios como: números de tarjetas, CVV y nombres para realizar compras fraudulentas. | - Inyección de código para copiar información sensible<br>- Interceptación de la comunicación de red<br>- Falsificación de la pasarela de pagos para phishing | Externalizar el pago a un proveedor seguro y usar conexión encriptada. |
| **Servidores** | Infraestructura | Falla el servidor provocando que el sitio web no se encuentre disponible. | - Sobrecarga intencional (Ataque DDoS)<br>- Infección por virus (Malware / Ransomware)<br>- Robo de credenciales de acceso para apagado/borrado manual | Implementación de firewalls, monitoreo de accesos y respaldo redundante de infraestructura. |
| **Base de datos de productos** | Datos | Fallas e inconsistencias en el inventario y catálogo de los productos. | - Corrupción de datos<br>- Inyección SQL / Borrado de tablas<br>- Fugas de información de catálogo y precios | Cifrado en reposo, políticas de copias de seguridad continuas y control estricto de acceso. |
| **Código fuente de los microservicios** | Software | Podría exponerse la lógica de negocio, introducir código malicioso o afectar el funcionamiento de los servicios. | - Acceso no autorizado al repositorio<br>- Introducción de código malicioso<br>- Robo de información sobre la lógica de negocio | Control de acceso al repositorio mediante autenticación multifactor (MFA) y permisos por roles. |
| **Logs y registros de auditoría** | Información | Podrían exponerse, alterarse o perderse evidencias importantes para detectar incidentes. | - Eliminación de registros<br>- Alteración de evidencias<br>- Acceso no autorizado a información registrada | Implementar almacenamiento protegido de logs con permisos de escritura restringidos (WORM) y copias de respaldo. |
| **Base de datos de pedidos** | Infraestructura | Podrían exponerse o alterarse pedidos, o impedirse su correcta gestión. | - Acceso no autorizado a los pedidos<br>- Modificación de pedidos<br>- Eliminación de registros de pedidos | Implementar control de acceso basado en roles y cifrado de la información almacenada. |
| **Base de datos de usuarios** | Infraestructura | Podrían exponerse o alterarse datos de usuarios, afectando su autenticación y gestión. | - Acceso no autorizado a datos personales<br>- Modificación de cuentas<br>- Eliminación de información de usuarios | Aplicar control de acceso, cifrado de datos sensibles y autenticación segura. |
| **API Gateway** | Software | Podrían manipularse las solicitudes o interrumpirse el acceso a varios microservicios. | - Interceptación de solicitudes<br>- Envío de solicitudes maliciosas<br>- Ataque de denegación de servicio (DoS) | Implementar autenticación, autorización y un sistema de rate limiting para controlar las solicitudes. |
| **Tokens de sesión (JWT)** | Información sensible | Un atacante podría suplantar la identidad de un usuario legítimo y acceder a sus datos o realizar compras fraudulentas. | - Robo de tokens<br>- Reutilización de tokens expirados<br>- Falsificación de tokens (token forgery) | Uso de tokens de corta duración, rotación de secretos y validación estricta de firma y expiración. |
| **Carrito de compras** | Información | Se podrían modificar cantidades o precios en el carrito, generando pedidos fraudulentos o pérdidas económicas. | - Manipulación del carrito desde el cliente<br>- Ataques de condición de carrera<br>- Inyección de productos no autorizados | Validación total en el servidor y recalculo de precios desde la base de datos. |
| **Certificados SSL/TLS** | Infraestructura | La comunicación dejaría de estar cifrada, permitiendo interceptar datos sensibles de los usuarios. | - Expiración del certificado<br>- Uso de certificados no válidos o autofirmados<br>- Ataques de tipo Man-in-the-Middle | Renovación automática de certificados, uso de autoridades certificadoras confiables y HSTS. |
| **Sistema de notificaciones** | Servicio | Los usuarios podrían no recibir alertas importantes (pedidos, cambios de contraseña) o recibir notificaciones falsas. | - Envío masivo de notificaciones spam<br>- Suplantación de notificaciones<br>- Interrupción del servicio de mensajería | Autenticación de origen, rate limiting y cifrado de los canales de notificación. |
| **Secrets y claves de cifrado** | Información sensible | La exposición de claves permitiría descifrar datos, falsificar tokens o acceder a sistemas internos. | - Filtración de variables de entorno<br>- Almacenamiento inseguro de secretos<br>- Uso de claves débiles o reutilizadas | Gestión centralizada de secretos (Vault), rotación periódica y principio de mínimo privilegio. |