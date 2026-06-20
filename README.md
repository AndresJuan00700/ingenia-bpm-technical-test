# Prueba Técnica - INGENIA BPM

**Candidato:** Andres Juan Benitez Muñoz

Solución al estudio de caso del Directorio de Estudiantes EDUCIT: corrección de 3 bugs y una funcionalidad adicional sobre el prototipo entregado.

## Correcciones realizadas

### Bug 1 - CSS del botón

**Problema:**

El botón no estaba tomando los estilos porque había un error tipográfico en el nombre de la clase CSS.

**Antes:**

```css
.btn-primery
```

**Después:**

```css
.btn-primary
```

**Qué hice:**

Simplemente corregí el nombre de la clase para que coincidiera con la que se estaba usando en el HTML.

---

### Bug 2 - Consumo de la API

**Problema:**

Los usuarios no se mostraban porque el código intentaba acceder a propiedades que no existen en la respuesta de la API.

**Antes:**

```javascript
user.full_name
user.email_address
```

**Después:**

```javascript
user.name
user.email
```

**Qué hice:**

Revisé la respuesta de la API y cambié las propiedades por las correctas para que los nombres y correos se mostraran correctamente.

---

### Bug 3 - Consulta SQL

**Problema:**

La consulta tenía un error porque la tabla esperaba dos valores y solo se estaba enviando uno. Además, no seguía buenas prácticas de seguridad.

**Antes:**

```sql
INSERT INTO estudiantes (nombre, correo) VALUES (userName);
```

**Después:**

```sql
INSERT INTO estudiantes (nombre, correo) VALUES (?, ?);
```

**Qué hice:**

Corregí la cantidad de valores y utilicé placeholders para representar una consulta parametrizada, evitando posibles problemas de SQL Injection. Como este archivo es solo frontend, la consulta queda documentada en el comentario; en un proyecto real se ejecutaría desde un backend usando una librería con soporte para prepared statements (por ejemplo `mysql2` o `pg` en Node.js).

---

## Funcionalidad adicional - Búsqueda en tiempo real

### Qué agregué

Añadí un campo de búsqueda para filtrar usuarios por nombre sin recargar la página.

### Cómo lo hice

* Creé un input de búsqueda.
* Guardé los usuarios obtenidos de la API en una variable `allUsers`.
* Separé la lógica de renderizado en una función `renderUsers()`.
* Creé una función `filterUsers()` para realizar el filtrado.
* Utilicé el evento `oninput` para actualizar los resultados mientras el usuario escribe.

### Resultado

La búsqueda funciona en tiempo real, sin hacer nuevas peticiones a la API y sin necesidad de recargar la página.

---

## Cómo probarlo

Abre el archivo `index.html` directamente en el navegador (no necesita servidor ni instalación, simplemente es abrirlo y se cargará todo).
