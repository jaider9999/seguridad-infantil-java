# seguridad-infantil-java
La seguridad infantil es una de las principales preocupaciones de padres y cuidadores en la actualidad. Muchos menores están expuestos a riesgos al desplazarse entre su hogar, la escuela y otros espacios públicos.  
Este proyecto busca incrementar la tranquilidad de los cuidadores mediante el uso de tecnologías de geolocalización

"Implementación del Login en el Proyecto Seguridad Infantil”

Introducción:
El módulo de autenticación y control de acceso se desarrolló utilizando Spring Boot para el backend, Spring Security para la gestion de usuario, y Thymeleaf para la interfaz visual.
Este módulo forma parte esencial del sistema de Seguridad Infantil, permitiendo que solo usuarios autorizados (administradores o cuidadores) accedan a las funcionalidades del sistema de monitoreo infantil, registro de menores y control de geocercas.

CONFIGURACIÓN DEL PROYECTO: 
El proyecto se generó como una aplicación de Spring Boot con las dependencias: Web, Thymeleaf, Spring Security, Spring Data JPA y el conector MySQL. Esto permite manejar el backend, la lógica de seguridad, la persistencia de datos y las vistas HTML dinámicas.

CONFIGURACIÓN DE LA BASE DE DATOS:
El login se integró con la base de datos PostgreSQL del proyecto, la cual también almacena la información de usuarios, menores, dispositivos GPS y geocercas mediante el archivo application.properties, donde se definieron el nombre de la base de datos, usuario, contraseña, y el dialecto de Hibernate. Spring Boot se encargó de crear las tablas automáticamente gracias a la propiedad spring.jpa.hibernate.ddl-auto=update.

CREACIÓN DE LA ENTIDAD USER :
Se diseñó una clase AppUser con los atributos: id, username, password, role y enabled. Esta entidad fue mapeada a la tabla users mediante la anotación @Entity para almacenar los datos de cada usuario en MySQL.
Configuración del Proyecto
Se agregaron las dependencias en el pom.xml para incluir:
spring-boot-starter-web
spring-boot-starter-security
spring-boot-starter-thymeleaf
spring-boot-starter-data-jpa
org.postgresql:postgresql

REPOSITORIO Y SERVICIO DE USUARIOS:
 El repositorio (UserRepository) extendió JpaRepository para acceder fácilmente a los datos. El servicio (UserService) se encargó de registrar nuevos usuarios, encriptar sus contraseñas con BCryptPasswordEncoder y guardar los registros en la base de datos.
 
IMPLEMENTACIÓN DE SPRING SECURITY:
 Se creó una clase CustomUserDetailsService que implementa UserDetailsService para adaptar los datos de la base de datos a la estructura que Spring Security utiliza para autenticar usuarios. Además, en SecurityConfig se definió el SecurityFilterChain con las rutas públicas y protegidas, y se configuró el login personalizado con Thymeleaf.

 CONTROLADOR DE AUTENTICACIÓN :
El controlador (AuthController) gestiona las rutas /login, /register y /. Permite mostrar los formularios de inicio de sesión y registro, registrar nuevos usuarios y redirigir a la página principal tras un login exitoso.

PLANTILLAS THYMELEAF :
Se crearon tres plantillas principales: - login.html: formulario de inicio de sesión. - register.html: formulario para registrar nuevos usuarios. - index.html: página principal mostrada después de iniciar sesión. Estas vistas utilizan expresiones Thymeleaf para interactuar con los datos del backend y con el modelo del controlador.

FUNCIONAMIENTO GENERAL 
Cuando un usuario se registra, su contraseña se cifra antes de almacenarse. Al iniciar sesión, Spring Security compara la contraseña ingresada con la versión encriptada en la base de datos. Solo los usuarios autenticados pueden acceder a las páginas protegidas; los no autenticados son redirigidos al formulario de login.

Conclusión  El módulo de login garantiza que los datos del sistema de Seguridad Infantil estén protegidos y solo sean accesibles por usuarios verificados. La combinación de Spring Boot, Spring Security y Thymeleaf proporciona una arquitectura segura, escalable y mantenible, alineada con los objetivos del proyecto de monitoreo y protección infantil.
