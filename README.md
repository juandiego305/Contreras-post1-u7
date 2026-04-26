# Sistema de Gestión de Tareas - Post-Contenido 1 (Unidad 7)

Este proyecto implementa una API REST profesional utilizando **Spring Boot 3**, diseñada bajo una **Arquitectura en Capas Estricta**. El objetivo principal es garantizar la separación de responsabilidades y asegurar que el dominio del sistema permanezca independiente de los detalles técnicos de infraestructura[cite: 893].

## 🏗️ Arquitectura del Sistema
El proyecto sigue el modelo organizativo de cuatro capas con dependencias unidireccionales, donde cada capa solo conoce a la inmediatamente inferior:

1.  **Capa de Presentación (`controller`)**: 
    * Gestiona las solicitudes HTTP mediante `@RestController`.
    * Traduce excepciones de negocio en códigos de estado HTTP semánticos (200, 201, 400, 404) a través de un `@RestControllerAdvice`.
2.  **Capa de Aplicación (`service`)**: 
    * Implementa la lógica de negocio y orquesta las llamadas al repositorio.
    * Es agnóstica a los detalles de la interfaz de usuario o protocolos de comunicación.
3.  **Capa de Dominio (`domain`)**: 
    * El corazón del sistema. Contiene las entidades JPA (`model/`) y las excepciones de negocio (`TareaNotFoundException`).
4.  **Capa de Infraestructura (`repository`)**: 
    * Gestiona la persistencia de datos extendiendo `JpaRepository`.
    * Utiliza una base de datos **H2** en memoria para facilitar las pruebas de laboratorio.

## 🚀 Guía de Ejecución

### Prerrequisitos
* **Java JDK 17** o superior.
* **Maven 3.8+**.

### Instrucciones
1.  Clonar el repositorio:
    ```bash
    git clone [https://github.com/juandiego305/Contreras-post1-u7.git](https://github.com/juandiego305/Contreras-post1-u7.git)
    ```
2.  Compilar el proyecto:
    ```bash
    mvn clean compile
    ```
3.  Ejecutar la aplicación:
    ```bash
    mvn spring-boot:run
    ```
4.  Acceder a la consola H2 (opcional): 
    👉 [http://localhost:8080/h2-console](http://localhost:8080/h2-console)

## 🛰️ Endpoints de la API

| Método | Endpoint | Acción | Código Éxito |
| :--- | :--- | :--- | :--- |
| **GET** | `/api/tareas` | Listar todas las tareas | 200 OK |
| **POST** | `/api/tareas` | Crear una nueva tarea | 201 Created |
| **PATCH** | `/api/tareas/{id}/estado` | Actualizar estado (PENDIENTE, EN_PROGRESO, COMPLETADA) | 200 OK |
| **DELETE** | `/api/tareas/{id}` | Eliminar una tarea permanentemente | 204 No Content |


1.  **POST /api/tareas**: Creación exitosa de una tarea.
2.  **GET /api/tareas**: Listado de tareas registradas.
3.  **400 Bad Request**: Validación fallida al intentar crear una tarea sin título.
4.  **404 Not Found**: Intento de búsqueda o eliminación de un ID inexistente.

## 🧑‍💻 Autor
* **Nombre**: Juan Diego Contreras Garcia
* **Institución**: Universidad Francisco de Paula Santander (UFPS)
* **Programa**: Ingeniería de Sistemas - 2026

---
© 2026 UFPS - Patrones de Diseño de Software
