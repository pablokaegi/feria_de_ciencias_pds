# Feria de Ciencias · Instituto Puertas del Sol

Mapa interactivo y guía de la **58ª Feria de Ciencias, Tecnologías, Artes, Movimiento e Innovación**.
Pensado para que las familias lo abran desde el celular: qué proyecto presenta cada curso, a qué hora, en qué aula y de qué nivel.

**Fecha:** jueves 2 de julio de 2026 · Mañana 8:30–12:30 · Tarde 17:00–21:00
**Lugar:** Blvd. Buenos Aires 750, Oncativo, Córdoba

---

## 📁 Estructura del proyecto

```
feria_de_ciencias_pds/
├── index.html              ← APP LISTA PARA PUBLICAR (un solo archivo, todo embebido)
├── README.md
└── fuente-editable/        ← el código para editar
    ├── Feria de Ciencias.dc.html   ← la app (se edita acá)
    ├── support.js                  ← motor que necesita el archivo de arriba
    ├── build-index.html            ← copia usada para generar index.html
    └── assets/
        └── logo.png
```

## ▶️ Ver / editar en tu computadora (VS Code)

1. Abrí la carpeta en **VS Code**.
2. Para ver la app: hacé doble clic en `fuente-editable/Feria de Ciencias.dc.html` (se abre en el navegador).
   - Recomendado: instalá la extensión **Live Server** y "Open with Live Server" para que recargue sola al guardar.
3. Editá ese archivo `.dc.html` (textos, datos, colores). `support.js` y `assets/` tienen que quedar al lado.

## 🌐 Publicar en el hosting

**Opción A — un solo archivo (lo más simple):**
Subí **`index.html`** (el de la raíz) a la carpeta `public_html` de tu hosting. Listo.

**Opción B — multi-archivo, todo editable en el server:**
Dentro de `fuente-editable/`, renombrá `Feria de Ciencias.dc.html` a `index.html` y subí ese archivo **junto con** `support.js` y la carpeta `assets/`. Cada vez que edites, volvés a subir.

> En las dos opciones, el mini-mapa de Google y las tipografías se cargan de internet; el resto funciona con poca señal.

## ⬆️ Subir al repositorio (GitHub)

- **Fácil (web):** en el repo → *Add file ▸ Upload files* → arrastrás los archivos → *Commit changes*.
- **Consola (VS Code):**
  ```bash
  git add .
  git commit -m "App de la feria"
  git push
  ```

## 📝 Pendiente de cargar

Participantes por curso · horarios exactos de cada turno · códigos QR reales por proyecto.
