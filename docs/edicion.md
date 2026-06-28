# Edición de contenidos — Feria de Ciencias · Puertas del Sol

Todo el contenido editable está en un solo archivo:
**`fuente-editable/Feria de Ciencias.dc.html`**

Abrilo en VS Code. Al final del archivo hay una clase JavaScript con todos los datos.
No toques `support.js` ni `index.html`.

---

## Mapa de los datos

### `LV` — Niveles y colores

Define los tres niveles y sus colores en toda la app.

```js
LV = {
  inicial:    { label: 'Inicial',    color: '#e0991a', ... },
  primario:   { label: 'Primario',   color: '#c8473b', ... },
  secundario: { label: 'Secundario', color: '#4f9d6a', ... },
};
```

Para cambiar un color, modificá `color`, `bg`, `soft`, `stroke` y `deep` del nivel correspondiente.

---

### `LOC` — Dirección y mapa

```js
LOC = {
  name: 'Instituto Puertas del Sol',
  address: 'Blvd. Buenos Aires 750',
  city: 'Oncativo, Córdoba',
  maps: 'https://...',   // link al lugar en Google Maps
  dir: 'https://...',    // link para "cómo llegar" (navegación)
  embed: 'https://...',  // iframe del mapa embebido
};
```

---

### `PROJ` — Proyectos por aula

Cada entrada tiene un ID (`i2`, `p1`, `s3`, etc.) y describe el proyecto de ese curso.

```js
PROJ = {
  s3: {
    title: 'Radio abierta bajo voltaje',         // nombre del proyecto
    space: 'Aula de 3° Año',                     // descripción del espacio
    docentes: 'Terráneo · Zalazar · Lovera',     // docentes a cargo (solo secundario)
    horario: 'Mañana y tarde',                   // horario de presentación
  },
  ...
}
```

**Convención de IDs:**
| Prefijo | Nivel | Ejemplo |
|---|---|---|
| `i` | Inicial | `i2` = Sala de 2 |
| `p` | Primario | `p4` = 4° Grado |
| `s` | Secundario | `s6` = 6° Año |

**Para agregar participantes:** añadí un campo `participantes` al objeto y luego mostralo en el HTML del template (buscá donde se usa `p.docentes` y agregá una línea similar).

**Para agregar QR real:** añadí un campo `qr` con la URL de la imagen y mostralo en la ficha del aula (buscá el `<img>` del QR en el template HTML y reemplazá el src placeholder).

---

### `rraw` — Posición de las aulas en el mapa

Array que define dónde aparece cada aula en el plano del colegio.

```js
rraw = [
  { id: 'p1', n: '1°', label: '1° Grado', lv: 'primario', top: 5, left: 6, w: 25, h: 13 },
  //           ↑ texto  ↑ tooltip         ↑ nivel          ↑ posición en % sobre el plano
]
```

Modificá `top`, `left`, `w`, `h` para mover o redimensionar un aula en el mapa (todos en porcentaje).

---

### `ev` y `evTarde` — Cronograma de la Agenda

`ev` = eventos del turno **mañana** (array, en orden cronológico):

```js
{ id: 'p4', time: '9:30', end: '10:45', lv: 'primario', room: '4° Grado', title: 'Científicos de nuestro cuerpo' }
```

`evTarde` = bloques del turno **tarde** (resumen por banda horaria):

```js
{ band: '1° y 2° Año', time: '19:30 – 20:30', items: 'Ruta productiva · Campamento' }
```

Para cargar los **horarios exactos del turno tarde**, reemplazá `evTarde` con el mismo formato que `ev`.

---

### `cardsRaw` — Tarjetas del buscador

Lista completa de proyectos que aparece en la sección "Buscar". Un elemento por proyecto.

```js
{ id: 's1', lv: 'secundario', room: '1° Año', title: 'Ruta productiva: innovación que conecta', time: 'Mañana y tarde' }
```

Para **agregar un proyecto nuevo**: copiá una línea, asignale un ID único y completá los campos.

---

## Cambios frecuentes

| Qué cambiar | Dónde buscarlo |
|---|---|
| Nombre de un proyecto | `PROJ[id].title` |
| Docentes de un curso | `PROJ[id].docentes` |
| Horario de un curso | `PROJ[id].horario` |
| Colores de un nivel | `LV[nivel].color` y compañeros |
| Horarios del turno mañana | Array `ev` |
| Horarios del turno tarde | Array `evTarde` |
| Proyectos en el buscador | Array `cardsRaw` |
| Posición de un aula en el mapa | `rraw` → `top`, `left`, `w`, `h` |
| Dirección / link de Google Maps | Objeto `LOC` |

---

## Flujo para regenerar `index.html` después de editar

El archivo `index.html` de la raíz es la versión publicable generada a partir del fuente.
Después de editar `Feria de Ciencias.dc.html`, avisale al equipo técnico para regenerarlo,
o usá el archivo `build-index.html` de la misma carpeta como guía del proceso de compilación.
