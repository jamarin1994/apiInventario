# CRUD con Spring Boot JWT Y PostgreSQL

Este proyecto es un una aplicación CRUD (Crear, Leer, Actualizar y Eliminar) desarrollada utilizando Java 17, Spring Boot 3 y PostgreSQL. La aplicación se encuentra en un entorno de contenedorizado utilizando Docker Compose.

## Tecnologías Utilizadas

- JDK 17
- Spring Boot 3
- Spring security 6
- PostgreSQL 15
- Java JWT
- Docker 

## Configuración del Entorno

Asegúrate de tener instalados los siguientes componentes en tu entorno de desarrollo antes de comenzar:

1. [Docker](https://docs.docker.com/compose/install/)

## Instrucciones de Uso

Sigue estos pasos para ejecutar la aplicación en tu entorno local:


#### Clonar el repositorio en tu máquina local
```
git clone https://github.com/jamarin1994/apiInventario.git
```
#### Navegar al directorio del proyecto
```
cd CRUD-spring-boot-postgresql
```

#### Construir y ejecutar los contenedores de Docker Compose
```
docker compose up -d
```

## Base URL

- [http://localhost:9000](http://localhost:9000)

## Documentación Postman (debido al poco tiempo de la prueba no alcance a documentar la api con swagger pero dejo anexo una CrudSpringBootJwt.postman_collection con los endpoints realizados)

Para facilitar el uso de la API, se proporciona una colección de Postman en la raiz del proyecto llamada "CrudSpringBootJwt.postman_collection". Esta colección contiene todas las llamadas a los endpoints mencionados anteriormente, lo que facilita la interacción y prueba de la API.

Se requiere autenticación para acceder a los endpoints de esta API. Puedes obtener un token JWT mediante los siguientes endpoints:

| Método   | Endpoint                               | Descripción                                |
|----------|----------------------------------------|--------------------------------------------|
| POST     | `/authentication/login`                | Iniciar sesión de usuario                  |
| POST     | `/authentication/sign`                 | Registro de usuario                        |

## Autenticación
- **Iniciar sesión de usuario:** `POST /authentication/login`
    - Cuerpo de la solicitud:
        ```json
        {
            "username": "angel",
            "password": "admin"
        }
        ```
    - Respuesta exitosa:
        ```json
        {
            "jwt": "TOKEN_JWT"
        }
        ```

- **Registro de usuario:** `POST /authentication/sign`
    - Cuerpo de la solicitud:
        ```json
        {
            "username": "angel",
            "password": "admin"
        }
        ```
    - Respuesta exitosa:
        ```json
        {
            "jwt": "TOKEN_JWT"
        }
        ```

## Endpoints de Productos

| Método   | Endpoint                               | Descripción                                |
|----------|----------------------------------------|--------------------------------------------|
| GET      | `/product/list`                        | Obtener todos los productos                |
| GET      | `/product/{id}`                        | Obtener un solo producto                   |
| POST     | `/product/add`                         | Guardar un nuevo producto                  |
| PUT      | `/product/update/{id}`                 | Actualizar un producto existente           |
| DELETE   | `/product/{id}`                        | Eliminar un producto                       |

- **Obtener todos los productos:** `GET /product/list`
    - Respuesta exitosa:
        ```json
        [
            {
                "id": 1,
                "name": "Papa gris",
                "description": "papa gris",
                "createAt": "2023-08-29T19:59:53.943202",
                "amount": 1000,
                "price": 25
            },
            {
                "id": 2,
                "name": "Arroz",
                "description": "arroz blanco desde campo Rd",
                "createAt": "2023-08-29T20:07:41.479372",
                "amount": 1000,
                "price": 25
            }
            // ...otros productos
        ]
        ```

- **Obtener un solo producto:** `GET /product/{id}`
    - Parámetros:
        - `{id}`: ID del producto a consultar
    - Respuesta exitosa:
        ```json
        {
            "id": 1,
            "name": "Papa gris",
            "description": "papa gris",
            "createAt": "2023-08-29T19:59:53.943202",
            "amount": 1000,
            "price": 25
        }
        ```

- **Guardar un nuevo producto:** `POST /product/add`
    - Cuerpo de la solicitud:
        ```json
        {
            "name": "Huevo gris",
            "description": "Huevo de gallina gringa",
            "amount": 1000,
            "price": 10
        }
        ```
    - Respuesta exitosa:
        ```json
        {
            "id": 7,
            "name": "Huevo gris",
            "description": "Huevo de gallina gringa",
            "createAt": "2023-08-30T00:56:09.430315",
            "amount": 1000,
            "price": 10
        }
        ```

- **Actualizar un producto existente:** `PUT /product/update/{id}`
    - Parámetros:
        - `{id}`: ID del producto a actualizar
    - Cuerpo de la solicitud:
        ```json
        {
            "name": "Huevo gris",
            "description": "Huevo de gallina gringa",
            "amount": 1000,
            "price": 10
        }
        ```
    - Respuesta exitosa:
        ```json
        {
            "message": "Producto actualizado exitosamente."
        }
        ```

- **Eliminar un producto:** `DELETE /product/{id}`
    - Parámetros:
        - `{id}`: ID del producto a eliminar
    - Respuesta exitosa:
        ```json
        {
            "message": "Producto eliminado exitosamente.",
            "code": 204,
            "http": "NO_CONTENT"
        }
        ```
Recuerda que debes incluir el token JWT en el encabezado de Autorización de cada solicitud a los endpoints protegidos.


