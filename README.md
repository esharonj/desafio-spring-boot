# Documentación de la API

Este repositorio contiene APIs para el manejo de Usuarios, Estados de Tarea y Tareas.

## Para el manejo de Usuarios

## Api de manejo de Usuarios

### Generar Token de Usuario

Endpoint para generar un token JWT para un usuario.

- **URL:** `/api/usuario/generaToken`
- **Método:** `POST`
- **Parámetros de la Solicitud:**
  - `usuarioDTO` (en el cuerpo de la solicitud): Objeto UsuarioDTO con las credenciales del usuario.
- **Respuestas:**
  - **Éxito (200):**
    - Token generado exitosamente.
    - Respuesta: String (Token JWT).
  - **Error (401):**
    - Credenciales inválidas.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Insertar Usuario

Endpoint para insertar un nuevo usuario.

- **URL:** `/api/usuario/insertaUsuario`
- **Método:** `POST`
- **Parámetros de la Solicitud:**
  - `usuarioDTO` (en el cuerpo de la solicitud): Objeto UsuarioDTO con los datos del usuario a insertar.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Usuario ingresado exitosamente.
    - Respuesta: Mensaje de éxito.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Lista de Usuarios

Endpoint para obtener la lista de usuarios.

- **URL:** `/api/usuario/listaUsuario`
- **Método:** `GET`
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: Lista de UsuarioDTO.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error (401):**
    - No existen registros.
    - Respuesta: Mensaje de error.

### Eliminar Usuario por ID

Endpoint para eliminar un usuario por su ID.

- **URL:** `/api/usuario/{id}`
- **Método:** `DELETE`
- **Parámetros de la Solicitud:**
  - `id` (en la URL): ID del usuario a eliminar.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (204):**
    - Usuario eliminado exitosamente.
    - Respuesta: Sin contenido.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Actualizar Usuario

Endpoint para actualizar un usuario.

- **URL:** `/api/usuario/actualizaUsuario`
- **Método:** `PUT`
- **Parámetros de la Solicitud:**
  - `usuarioDTO` (en el cuerpo de la solicitud): Objeto UsuarioDTO con los datos actualizados del usuario.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: UsuarioDTO actualizado.
  - **Error (404):**
    - El usuario no fue encontrado.
    - Respuesta: Mensaje de error.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

## Tener Presente

Esta API utiliza tokens JWT para la autenticación en todos los servicios con excepción el servicio que genera token "generaToken". Asegúrate de incluir el token JWT válido en la cabecera de todas las solicitudes autorizadas.


## Api de manejo de Estados de Tareas

### Insertar Estado de Tarea

Endpoint para insertar un nuevo estado de tarea.

- **URL:** `/api/estadotarea/insertaEstadoTarea`
- **Método:** `POST`
- **Parámetros de la Solicitud:**
  - `nombre` (en el cuerpo de la solicitud): Nombre del estado de la tarea a insertar.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (201):**
    - Estado de Tarea creado exitosamente.
    - Respuesta: EstadoTareaEntity.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Obtener Lista de Estados de Tarea

Endpoint para obtener todos los estados de tarea.

- **URL:** `/api/estadotarea/listaEstadosTarea`
- **Método:** `GET`
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: Lista de EstadoTareaDTO.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Obtener Estado de Tarea por ID

Endpoint para obtener el estado de tarea por su ID.

- **URL:** `/api/estadotarea/obtieneEstadoTareaPorId/{id}`
- **Método:** `GET`
- **Parámetros de la Solicitud:**
  - `id` (en la URL): ID del estado de tarea.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: Optional<Object>.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Eliminar Estado de Tarea por ID

Endpoint para eliminar el estado de tarea por su ID.

- **URL:** `/api/estadotarea/eliminaEstadoTareaPorId/{id}`
- **Método:** `DELETE`
- **Parámetros de la Solicitud:**
  - `id` (en la URL): ID del estado de tarea.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: Mensaje de éxito.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Actualizar Estado de Tarea

Endpoint para actualizar el estado de una tarea.

- **URL:** `/api/estadotarea/actualizaEstadosTarea`
- **Método:** `PUT`
- **Parámetros de la Solicitud:**
  - `estadoTareaDTO` (en el cuerpo de la solicitud): Objeto EstadoTareaDTO.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: EstadoTareaDTO actualizado.
  - **Error (404):**
    - El estado de tarea no fue encontrado.
    - Respuesta: Mensaje de error.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.
	
## Tener Presente

Esta API utiliza tokens JWT para la autenticación. Asegúrate de incluir el token JWT válido en la cabecera de todas las solicitudes autorizadas.
	

## Api de manejo de Tareas

### Insertar Tarea

Endpoint para insertar una nueva tarea.

- **URL:** `/api/tarea/insertaTarea`
- **Método:** `POST`
- **Parámetros de la Solicitud:**
  - `tareaDTO` (en el cuerpo de la solicitud): Datos de la tarea a insertar.
    - Campos requeridos: `idEstadoTarea`, y otros campos de la tarea.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (201):**
    - Tarea creada exitosamente.
    - Respuesta: TareaDTO.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Obtener Lista de Tareas

Endpoint para obtener la lista de todas las tareas.

- **URL:** `/api/tarea/listaTarea`
- **Método:** `GET`
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: Lista de TareaDTO.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Obtener Tarea por ID

Endpoint para obtener una tarea por su ID.

- **URL:** `/api/tarea/obtienePorId/{id}`
- **Método:** `GET`
- **Parámetros de la Solicitud:**
  - `id` (en la URL): ID de la tarea.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: Optional<TareaDTO>.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error (404):**
    - Tarea no encontrada.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Eliminar Tarea por ID

Endpoint para eliminar una tarea por su ID.

- **URL:** `/api/tarea/eliminaTareaPorId/{id}`
- **Método:** `DELETE`
- **Parámetros de la Solicitud:**
  - `id` (en la URL): ID de la tarea.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: Mensaje de éxito.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

### Actualizar Tarea

Endpoint para actualizar una tarea.

- **URL:** `/api/tarea/actualizaTarea`
- **Método:** `PUT`
- **Parámetros de la Solicitud:**
  - `tareaDTO` (en el cuerpo de la solicitud): Datos de la tarea a actualizar.
    - Campos requeridos: `idEstadoTarea`, y otros campos de la tarea.
- **Cabecera:**
  - `Authorization`: Token JWT válido.
- **Respuestas:**
  - **Éxito (200):**
    - Operación exitosa.
    - Respuesta: TareaDTO actualizado.
  - **Error (401):**
    - Token JWT no válido.
    - Respuesta: Mensaje de error.
  - **Error (404):**
    - La tarea no fue encontrada.
    - Respuesta: Mensaje de error.
  - **Error Interno del Servidor (500):**
    - Error interno del servidor.
    - Respuesta: Mensaje de error detallado.

## Información Adicional

Este controlador utiliza tokens JWT para la autenticación. Asegúrate de incluir el token JWT válido en la cabecera de todas las solicitudes autorizadas.

**Archivo de Pruebas Postman:**
Se adjunta el archivo de pruebas Postman llamado "Apis.postman_collection.json". Puedes importar este archivo en Postman para realizar pruebas rápidas de la API.

	
	