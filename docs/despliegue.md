# Despliegue — Feria de Ciencias · Puertas del Sol

Cómo publicar la app en internet. Hay dos opciones: tu hosting (Nuthost/cPanel) o GitHub Pages (gratis).

---

## Opción A — Hosting Nuthost via cPanel ✅ (recomendada)

### 1. Crear el subdominio (solo la primera vez)

1. Ingresá a tu cPanel de Nuthost.
2. Buscá **Subdominios** (*Subdomains*).
3. Completá los campos:
   - **Subdominio:** `feria` (quedará como `feria.pds.edu.ar`)
   - **Dominio:** `pds.edu.ar`
   - **Raíz del documento:** dejá lo que cPanel sugiere o escribí `public_html/feria`
4. Hacé clic en **Crear**.

### 2. Subir el archivo

1. En cPanel → **Administrador de archivos** (*File Manager*).
2. Navegá a `public_html/feria` (la carpeta del subdominio recién creado).
3. Botón **Subir** → seleccioná `index.html` (el de la raíz del proyecto).
4. Esperá que la barra llegue al 100%.

### 3. Verificar

Abrí `feria.pds.edu.ar` en el celular. Debería verse la app completa.

### Actualizar cuando haya cambios

1. Pedile a quien edita el código el nuevo `index.html`.
2. En File Manager → `public_html/feria` → clic derecho en el `index.html` viejo → **Delete**.
3. Subí el nuevo `index.html`.
4. En el celular recargá la página (mantené presionado el botón recargar → "Vaciar caché y recargar").

---

## Opción B — GitHub Pages (gratis, sin hosting propio)

Útil si querés compartir un link público sin tocar el hosting.

1. En el repositorio de GitHub: **Settings** → **Pages** (barra lateral izquierda).
2. En *Source* seleccioná **Deploy from a branch**.
3. Rama: `main` / Carpeta: `/ (root)`.
4. Hacé clic en **Save**.
5. En unos minutos el sitio estará disponible en:
   `https://pablokaegi.github.io/feria_de_ciencias_pds/`

> ⚠️ GitHub Pages sirve `index.html` de la raíz automáticamente. No necesitás hacer nada más.

---

## Cuadro comparativo

| | Nuthost/cPanel | GitHub Pages |
|---|---|---|
| URL propia (`feria.pds.edu.ar`) | ✅ | ❌ (URL de GitHub) |
| Gratis | Incluido en tu plan | ✅ Siempre gratis |
| Pasos para actualizar | Subir archivo manualmente | `git push` |
| Velocidad | Depende del plan | Buena |
