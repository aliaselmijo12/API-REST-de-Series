# API REST de Series (Spring Boot)

Este proyecto es una API REST completa para la gestión de un catálogo de series de televisión, implementada con **Java 17/21**, **Spring Boot**, **Spring Data JPA**, **Lombok** y una base de datos en memoria **H2**.

---

## 🛠️ Tecnologías Utilizadas

* **Lenguaje:** Java (17/21)
* **Framework:** Spring Boot 3.x
* **Persistencia:** Spring Data JPA / Hibernate
* **Base de Datos:** H2 Database (en memoria)
* **Herramientas de Productividad:** Lombok
* **Gestor de Dependencias:** Maven
* **Estructura de Paquetes:** `com.CordovaZabala.series_api`

---

## 📂 Estructura del Proyecto

El código fuente sigue una arquitectura en capas limpia y desacoplada:

```text
src/main/java/com/CordovaZabala/series_api/
├── controller/       # Manejo de peticiones HTTP y endpoints REST
│   └── SerieController.java
├── service/          # Lógica de negocio de la aplicación
│   └── SerieService.java
├── repository/       # Capa de acceso a datos (Spring Data JPA)
│   └── SerieRepository.java
└── models/           # Entidades de base de datos
    └── Serie.java
```

---

## ⚙️ Requisitos de Ejecución

1. Tener instalado **JDK 17** o superior.
2. Tener instalado **Apache Maven** (o utilizar el wrapper `./mvnw` incluido).

---

## 🚀 Cómo Ejecutar la Aplicación

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/TU_USUARIO/TU_REPOSITORIO.git
   cd series-api
   ```

2. **Compilar y ejecutar la aplicación:**
   ```bash
   mvn spring-boot:run
   ```

3. La API estará activa y lista para recibir peticiones en:
   * **URL Base HTTP:** `http://localhost:8080/api/series`
   * *(Si configuraste HTTPS)*: `https://localhost:8443/api/series`

---

## 🗄️ Acceso a la Consola H2

Puedes verificar directamente las tablas y datos guardados en la base de datos en memoria ingresando desde tu navegador:

* **URL de la consola:** `http://localhost:8080/h2-console`
* **JDBC URL:** `jdbc:h2:mem:seriesdb`
* **User Name:** `sa`
* **Password:** *(dejar en blanco)*

---

## 📌 Documentación de Endpoints (API REST)

### Entidad `Serie`
| Campo | Tipo | Descripción |
| :--- | :--- | :--- |
| `id` | `Long` | Identificador único autogenerado |
| `titulo` | `String` | Nombre de la serie |
| `plataforma` | `String` | Plataforma de streaming (Netflix, HBO, Prime, etc.) |
| `calificacion` | `Double` | Calificación de 1.0 a 10.0 |

---

### Resumen de Rutas

| Método | Endpoint | Descripción | Estado HTTP Esperado |
| :--- | :--- | :--- | :--- |
| **GET** | `/api/series` | Listar todas las series | `200 OK` |
| **GET** | `/api/series/{id}` | Buscar una serie por ID | `200 OK` / `404 Not Found` |
| **POST** | `/api/series` | Crear una nueva serie | `201 Created` |
| **PUT** | `/api/series/{id}` | Actualizar una serie existente | `200 OK` / `404 Not Found` |
| **DELETE** | `/api/series/{id}` | Eliminar una serie por ID | `204 No Content` / `404 Not Found` |

---

### Ejemplos de Peticiones

#### 1. Crear una Serie (`POST /api/series`)
* **Headers:** `Content-Type: application/json`
* **Body:**
```json
{
  "titulo": "Breaking Bad",
  "plataforma": "Netflix",
  "calificacion": 9.5
}
```

#### 2. Actualizar una Serie (`PUT /api/series/1`)
* **Headers:** `Content-Type: application/json`
* **Body:**
```json
{
  "titulo": "Breaking Bad (Edición Especial)",
  "plataforma": "Netflix",
  "calificacion": 9.8
}
```