# Práctica de APIs REST con Postman — Metodología CRUD

## 📌 Descripción de la práctica

Esta práctica consiste en el uso de **Postman** para realizar peticiones HTTP a distintas APIs públicas, aplicando la metodología **CRUD** (Create, Read, Update, Delete). El objetivo es comprender y demostrar el funcionamiento de los cuatro métodos HTTP fundamentales (`GET`, `POST`, `PUT`/`PATCH`, `DELETE`) sobre recursos reales expuestos por diferentes servicios.

La práctica se divide en dos bloques:

1. **APIs 1 a 5**: cinco APIs **distintas**, cada una probada con las operaciones CRUD completas (crear, leer, actualizar y eliminar un recurso).
2. **APIs 6 a 10**: una **misma API** (DummyJSON), pero aplicada sobre **cinco recursos diferentes** (`users`, `products`, `posts`, `todos`, `comments`), repitiendo el ciclo CRUD completo en cada uno.

En total se han documentado **10 flujos CRUD**, con capturas de cada petición y su respuesta correspondiente (código de estado, tiempo de respuesta y tamaño de la respuesta).

---

## 🧩 Metodología CRUD

CRUD es un acrónimo que representa las cuatro operaciones básicas que se pueden realizar sobre cualquier recurso de una base de datos o API:

| Letra | Operación | Método HTTP | Función |
|-------|-----------|-------------|---------|
| **C** | Create (Crear) | `POST` | Añade un nuevo recurso al servidor |
| **R** | Read (Leer) | `GET` | Consulta uno o varios recursos existentes |
| **U** | Update (Actualizar) | `PUT` / `PATCH` | Modifica un recurso ya existente |
| **D** | Delete (Eliminar) | `DELETE` | Elimina un recurso existente |

Esta metodología es la base de cualquier API REST y permite estructurar las pruebas de forma ordenada: por cada recurso se comprueba que se puede crear, consultar, modificar y eliminar correctamente.

---

## 🔍 Explicación de los métodos HTTP utilizados

### `GET`
Se utiliza para **leer/recuperar información** de un recurso sin modificarlo. No envía cuerpo (body) en la petición, salvo casos muy concretos. Es un método **idempotente** y **seguro** (no altera el estado del servidor). En las pruebas, todas las peticiones `GET` devolvieron código **200 OK** junto con el JSON del recurso solicitado.

### `POST`
Se utiliza para **crear un nuevo recurso** en el servidor. Envía un cuerpo JSON con los datos del nuevo elemento. La respuesta habitual es **201 Created**, aunque algunas APIs (como JSONbin.io) devuelven **200 OK**. El servidor suele responder con el recurso creado, incluyendo un identificador (`id`) generado automáticamente.

### `PUT`
Se utiliza para **reemplazar por completo** un recurso existente. Se envía el objeto completo (o los campos que la API espera) y el servidor lo sustituye. Es **idempotente**: repetir la misma petición `PUT` produce siempre el mismo resultado.

### `PATCH`
Se utiliza para **actualizar parcialmente** un recurso, enviando únicamente los campos que se desean modificar (a diferencia de `PUT`, que sustituye el recurso entero). En esta práctica se ha usado en GoRest y RESTFULLapi.dev.

### `DELETE`
Se utiliza para **eliminar un recurso** existente a partir de su identificador. La respuesta puede variar según la API: algunas devuelven **204 No Content** (sin cuerpo), y otras **200 OK** con un mensaje de confirmación en el JSON de respuesta.

---

## 🌐 APIs utilizadas (Bloque 1: 5 APIs distintas)

| # | API | Recurso probado | Autenticación | Métodos probados |
|---|-----|------------------|----------------|-------------------|
| 1 | [GoRest.co.in](https://gorest.co.in) | `users` | Bearer Token | GET, POST, PATCH, DELETE |
| 2 | [JSONbin.io](https://jsonbin.io) | `bins` (b) | X-Master-Key | POST, GET, PUT, DELETE |
| 3 | [RESTFULLapi.dev](https://restful-api.dev) | `objects` | x-api-key | POST, GET, PATCH, DELETE |
| 4 | [Swagger Petstore](https://petstore.swagger.io) | `pet` | Ninguna | POST, GET, PUT, DELETE |
| 5 | [CrudCrud](https://crudcrud.com) | `equipos` | Endpoint privado | POST, GET, PUT, DELETE |

## 🌐 API utilizada (Bloque 2: 1 API, 5 recursos)

| # | API | Recurso | Métodos probados |
|---|-----|---------|-------------------|
| 6 | DummyJSON | `users` | POST (`/add`), GET, PUT, DELETE |
| 7 | DummyJSON | `products` | POST (`/add`), GET, PUT, DELETE |
| 8 | DummyJSON | `posts` | POST (`/add`), GET, PUT, DELETE |
| 9 | DummyJSON | `todos` | POST (`/add`), GET, PUT, DELETE |
| 10 | DummyJSON | `comments` | POST (`/add`), GET, PUT, DELETE |

---

## 📊 Resultados obtenidos — Bloque 1 (APIs distintas)

| API | Método | Código | Tiempo | Tamaño respuesta |
|-----|--------|--------|--------|-------------------|
| GoRest | GET | 200 OK | 367 ms | 2.37 KB |
| GoRest | POST | 201 Created | 868 ms | 1.84 KB |
| GoRest | PATCH | 200 OK | 805 ms | 1.79 KB |
| GoRest | DELETE | 204 No Content | 1.01 s | 1.56 KB |
| JSONbin.io | POST | 200 OK | 258 ms | 842 B |
| JSONbin.io | GET | 200 OK | 254 ms | 842 B |
| JSONbin.io | PUT | 200 OK | 243 ms | 864 B |
| JSONbin.io | DELETE | 200 OK | 527 ms | 830 B |
| RESTFULLapi.dev | POST | 200 OK | 260 ms | 978 B |
| RESTFULLapi.dev | GET | 200 OK | 258 ms | 967 B |
| RESTFULLapi.dev | PATCH | 200 OK | 269 ms | 1 KB |
| RESTFULLapi.dev | DELETE | 200 OK | 225 ms | 948 B |
| Swagger Petstore | POST | 200 OK | 446 ms | 507 B |
| Swagger Petstore | GET | 200 OK | 459 ms | 507 B |
| Swagger Petstore | PUT | 200 OK | 108 ms | 513 B |
| Swagger Petstore | DELETE | 200 OK | 107 ms | 376 B |
| CrudCrud | POST | 201 Created | 163 ms | 642 B |
| CrudCrud | GET | 200 OK | 125 ms | 557 B |
| CrudCrud | PUT | 200 OK | 202 ms | 391 B |
| CrudCrud | DELETE | 200 OK | 75 ms | 391 B |

## 📊 Resultados obtenidos — Bloque 2 (DummyJSON, 5 recursos)

| Recurso | POST | GET | PUT | DELETE |
|---------|------|-----|-----|--------|
| users | 201 · 113 ms · 1.69 KB | 200 · 110 ms · 1.81 KB | 200 · 111 ms · 1.82 KB | 200 · 124 ms · 1.84 KB |
| products | 201 · 115 ms · 1.02 KB | 200 · 112 ms · 1.64 KB | 200 · 171 ms · 1.25 KB | 200 · 121 ms · 1.66 KB |
| posts | 201 · 114 ms · 1.02 KB | 200 · 113 ms · 1.23 KB | 200 · 466 ms · 1.23 KB | 200 · 120 ms · 1.28 KB |
| todos | 201 · 435 ms · 1.03 KB | 200 · 111 ms · 1.04 KB | 200 · 120 ms · 1.04 KB | 200 · 119 ms · 1.07 KB |
| comments | 201 · 110 ms · 1.09 KB | 200 · 115 ms · 1.07 KB | 200 · 119 ms · 1.1 KB | 200 · 454 ms · 1.1 KB |

*(Formato de cada celda: Código HTTP · Tiempo de respuesta · Tamaño de la respuesta)*

---

## 🧠 Comparación y análisis de resultados

- **Códigos de estado:** casi todas las peticiones devolvieron `200 OK`, salvo las operaciones de creación (`POST`), que en la mayoría de APIs devolvieron correctamente **`201 Created`** (GoRest, CrudCrud y las 5 rutas de DummyJSON), siguiendo la buena práctica REST de diferenciar la creación de un recurso de una simple lectura. JSONbin.io y RESTFULLapi.dev, en cambio, devuelven `200 OK` incluso al crear, lo cual no sigue estrictamente el estándar pero sigue siendo funcional.

- **DELETE:** el comportamiento varía bastante entre APIs. GoRest devuelve `204 No Content` (sin cuerpo, tal y como recomienda la especificación HTTP), mientras que el resto de APIs (JSONbin.io, RESTFULLapi.dev, Swagger Petstore, CrudCrud, DummyJSON) devuelven `200 OK` junto con un mensaje o el propio recurso eliminado, lo cual resulta más útil para depuración aunque no sea lo más "puro" según el estándar REST.

- **Tiempos de respuesta:** las APIs con autenticación por token (GoRest) presentan tiempos más altos (hasta ~1 segundo), probablemente por la validación adicional del token y por tratarse de un servicio con base de datos real y persistente. Las APIs simuladas o "mock" (RESTFULLapi.dev, Swagger Petstore, CrudCrud) responden de forma mucho más rápida (entre 75 ms y 460 ms), ya que no siempre persisten los datos de forma permanente.

- **Tamaño de las respuestas:** DummyJSON destaca por devolver respuestas más "pesadas" (hasta 1.84 KB), ya que sus recursos (usuarios, productos) incluyen muchos campos por defecto (dirección, contraseña, imagen, etc.), mientras que APIs más minimalistas como Swagger Petstore o CrudCrud devuelven objetos mucho más ligeros (300–650 B).

- **Persistencia real vs. simulada:** es importante señalar que APIs como **RESTFULLapi.dev**, **Swagger Petstore** y **DummyJSON** son entornos de prueba ("mock APIs"): aceptan las peticiones y devuelven respuestas coherentes, pero **no garantizan que los datos se guarden de forma permanente** en su base de datos. Por el contrario, **GoRest**, **JSONbin.io** y **CrudCrud** sí persisten los datos reales, motivo por el cual se pudo encadenar correctamente el ciclo completo `POST → GET → PUT/PATCH → DELETE` sobre el mismo recurso creado (usando el `id` devuelto por el `POST` en las siguientes peticiones).

- **Consistencia entre bloques:** al probar 5 recursos distintos dentro de una misma API (DummyJSON), se observa que el comportamiento de los códigos de estado es homogéneo (siempre 201 en creación y 200 en el resto), lo cual demuestra que una API bien diseñada mantiene una interfaz consistente independientemente del recurso que se esté gestionando.

---

## ✅ Conclusiones

- Se ha comprobado de forma práctica el funcionamiento de los cuatro métodos HTTP (`GET`, `POST`, `PUT`/`PATCH`, `DELETE`) sobre nueve APIs/recursos distintos, aplicando en todos los casos la metodología **CRUD**.
- Se ha verificado que, aunque el estándar REST recomienda ciertos códigos de estado (201 para creación, 204 para borrado sin contenido), en la práctica cada API implementa estas recomendaciones de forma distinta.
- Se ha comprobado la diferencia entre `PUT` (reemplazo completo) y `PATCH` (actualización parcial) en las APIs que ofrecían ambas opciones.
- La herramienta **Postman** ha permitido documentar de forma clara y visual cada petición, su cabecera de autenticación (cuando aplica), el cuerpo enviado y la respuesta recibida, facilitando la comparación entre servicios.

---

## 🛠️ Herramientas utilizadas

- **Postman** – cliente para el diseño y prueba de peticiones HTTP/API.
- APIs públicas de prueba: GoRest, JSONbin.io, RESTFULLapi.dev, Swagger Petstore, CrudCrud y DummyJSON.
