# Modelo de datos — Feria de Ciencias · Puertas del Sol

Descripción de qué representa cada estructura de datos de la app.

---

## Niveles (`LV`)

La app divide los proyectos en tres niveles. Cada nivel tiene un esquema de colores propio
que se aplica a los botones del mapa, las tarjetas y los filtros.

| Clave | Nivel | Color principal |
|---|---|---|
| `inicial` | Nivel Inicial (Salas 2–5) | Amarillo/ocre `#e0991a` |
| `primario` | Primario (1° a 6° grado) | Rojo `#c8473b` |
| `secundario` | Secundario (1° a 6° año) | Verde `#4f9d6a` |

---

## Aulas (`rraw`)

Cada elemento representa un espacio físico del colegio que aparece en el plano.

| Campo | Tipo | Descripción |
|---|---|---|
| `id` | string | Identificador único. Prefijo `i`/`p`/`s` + número. |
| `n` | string | Texto corto que se muestra dentro del botón del mapa (ej: `"4°"`). |
| `label` | string | Nombre completo del espacio (ej: `"4° Grado"`). |
| `lv` | string | Nivel al que pertenece: `inicial`, `primario` o `secundario`. |
| `top` | number | Posición vertical en el plano (en %, desde arriba). |
| `left` | number | Posición horizontal en el plano (en %, desde la izquierda). |
| `w` | number | Ancho del botón en el plano (en %). |
| `h` | number | Alto del botón en el plano (en %). |
| `kind` | string | Solo para espacios no académicos: `"amenity"` (WC, buffet). Opcional. |

---

## Proyectos (`PROJ`)

Cada entrada describe el proyecto que presenta un curso.
La clave es el mismo ID que el aula correspondiente.

| Campo | Tipo | Descripción |
|---|---|---|
| `title` | string | Nombre completo del proyecto. |
| `space` | string | Descripción del espacio donde se expone. |
| `docentes` | string | Docentes a cargo (principalmente usado en secundario). |
| `horario` | string | Horario de presentación del proyecto. |

**Pendiente:** agregar campo `participantes` (lista de alumnos) y `qr` (URL del código QR).

---

## Eventos de la Agenda (`ev` / `evTarde`)

### Turno mañana (`ev`)

| Campo | Tipo | Descripción |
|---|---|---|
| `id` | string | ID del aula/proyecto asociado. |
| `time` | string | Hora de inicio (ej: `"9:30"`). |
| `end` | string | Hora de fin (ej: `"10:45"`). |
| `lv` | string | Nivel: `inicial`, `primario` o `secundario`. |
| `room` | string | Nombre del espacio (ej: `"4° Grado"`). |
| `title` | string | Nombre del proyecto. |

La lógica de "Pasando ahora" compara `time` y `end` con la hora actual del dispositivo.

### Turno tarde (`evTarde`)

Actualmente cargado como bloques resumidos. Cada elemento agrupa varios cursos:

| Campo | Tipo | Descripción |
|---|---|---|
| `band` | string | Agrupación de cursos (ej: `"1° y 2° Año"`). |
| `time` | string | Rango horario (ej: `"19:30 – 20:30"`). |
| `items` | string | Proyectos que se presentan en ese bloque. |

**Pendiente:** reemplazar por el mismo formato de `ev` con horarios exactos por curso.

---

## Tarjetas del buscador (`cardsRaw`)

Lista plana de todos los proyectos que aparecen en la sección "Buscar" y "Guardados".

| Campo | Tipo | Descripción |
|---|---|---|
| `id` | string | ID único. Debe coincidir con la clave en `PROJ` para que la ficha funcione. |
| `lv` | string | Nivel del proyecto. |
| `room` | string | Nombre del aula o espacio. |
| `title` | string | Nombre del proyecto. |
| `time` | string | Horario resumido (ej: `"8:30 – 12:30"` o `"Mañana y tarde"`). |

---

## Estado de la app (`state`)

La app maneja un estado interno que controla qué ve el usuario en cada momento:

| Campo | Descripción |
|---|---|
| `tab` | Sección activa: `mapa`, `agenda`, `buscar` o `guardados`. |
| `level` | Filtro de nivel activo en el mapa: `todos`, `inicial`, `primario` o `secundario`. |
| `selectedId` | ID del aula seleccionada (abre la ficha). `null` si no hay ninguna. |
| `query` | Texto del buscador. |
| `saved` | Array de IDs guardados en "Mi recorrido". |
| `locOpen` | Si el panel de "Cómo llegar" está abierto. |
