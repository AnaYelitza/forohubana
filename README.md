# Foro-Hub API

Foro-Hub es una API construida para administrar un foro de discusión, permitiendo la creación, lectura, actualización y eliminación de publicaciones, comentarios y gestión de usuarios y temas.

## Tecnologías Utilizadas

- **Spring Framework**: Framework Java para aplicaciones web y servicios RESTful.
- **Spring Boot**: Facilita la configuración y el desarrollo de aplicaciones basadas en Spring.
- **Java 17**: Versión moderna de Java con mejoras de rendimiento y seguridad.
- **Spring Data JPA**: Acceso y manipulación de datos relacionales con Hibernate.
- **MySQL**: Base de datos relacional para el almacenamiento persistente.
- **JSON Web Tokens (JWT)**: Seguridad y autenticación para APIs RESTful.
- **Maven**: Gestión de dependencias y construcción de proyectos.
- **Git**: Control de versiones distribuido.

## Tabla de Contenidos

- [Instalación](#instalación)
- [Uso](#uso)
- [Endpoints](#endpoints)
  - [Usuarios](#usuarios)
  - [Publicaciones](#publicaciones)
  - [Comentarios](#comentarios)
  - [Temas](#temas)
- [Autenticación](#autenticación)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)

## Instalación

Para configurar y ejecutar Foro-Hub:

1. Clona el repositorio:
    ```sh
    git clone https://github.com/tu_usuario/foro-hub.git
    ```
2. Ve al directorio del proyecto:
    ```sh
    cd foro-hub
    ```
3. Compila el proyecto y descarga las dependencias:
    ```sh
    mvn clean install
    ```
4. Configura las variables de entorno en `application.properties`:
    ```properties
    server.port=8080
    spring.datasource.url=jdbc:mysql://localhost:3306/forohub
    spring.datasource.username=tu_usuario
    spring.datasource.password=tu_contraseña
    jwt.secret=tu_secreto_jwt
    ```

5. Ejecuta la aplicación:
    ```sh
    mvn spring-boot:run
    ```

## Uso

Autentica a los usuarios con JWT, restringiendo las operaciones de modificación y eliminación solo a los propietarios de los recursos.

## Endpoints

### Usuarios

- **Registro de usuario**
  - `POST /api/users`
  - Body: 
    ```json
    {
      "username": "string",
      "email": "string",
      "password": "string"
    }
    ```

- **Obtener información de un usuario**
  - `GET /api/users/:id`
  - Solo accesible por el propietario.

- **Actualizar un usuario**
  - `PUT /api/users/:id`
  - Body: 
    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```

- **Eliminar un usuario**
  - `DELETE /api/users/:id`
  - Solo accesible por el propietario.

### Publicaciones

- **Crear una nueva publicación**
  - `POST /api/posts`
  - Body: 
    ```json
    {
      "title": "string",
      "content": "string"
    }
    ```

- **Obtener todas las publicaciones**
  - `GET /api/posts`

- **Actualizar una publicación**
  - `PUT /api/posts/:id`
  - Body:
    ```json
    {
      "title": "string",
      "content": "string"
    }
    ```

- **Eliminar una publicación**
  - `DELETE /api/posts/:id`

### Comentarios

- **Agregar un comentario a una publicación**
  - `POST /api/posts/:postId/comments`
  - Body: 
    ```json
    {
      "content": "string"
    }
    ```

- **Obtener todos los comentarios de una publicación**
  - `GET /api/posts/:postId/comments`

- **Actualizar un comentario**
  - `PUT /api/comments/:id`
  - Body:
    ```json
    {
      "content": "string"
    }
    ```

- **Eliminar un comentario**
  - `DELETE /api/comments/:id`

## Autenticación

Foro-Hub utiliza JWT para autenticar a los usuarios. Los usuarios deben incluir el token en el encabezado de autorización en las solicitudes a los endpoints protegidos.

## Contribuciones

Contribuir es fácil. Sigue estos pasos:

1. Realiza un fork del proyecto.
2. Crea una rama (`git checkout -b nueva-funcionalidad`).
3. Realiza tus cambios y haz commits (`git commit -am 'Agregar nueva funcionalidad'`).
4. Sube tus cambios (`git push origin nueva-funcionalidad`).
5. Abre un Pull Request.

## Licencia

Foro-Hub está bajo la licencia [MIT License](LICENSE).
