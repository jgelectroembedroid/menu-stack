# Tupper Sync

App de una sola página (HTML/CSS/JS, sin dependencias externas salvo tipografías de Google Fonts) con el plan de menús de 3 semanas de Juan y Arantxa: calendario, menú del día, macros de Juan, lista de la compra y cocina por lotes.

Todos los datos están embebidos en `index.html` (no hay backend ni base de datos). Cuando cambies el plan, hay que regenerar este archivo desde el Excel maestro y volver a subirlo — no se edita a mano.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (puede ser privado o público; si es privado necesitas GitHub Pro/Team/Enterprise para poder publicar Pages desde un repo privado — con público no hace falta).
2. Sube estos 2 archivos a la raíz del repositorio (o a una carpeta `docs/` si prefieres esa opción en el paso 4):
   - `index.html`
   - `.nojekyll` (evita que GitHub intente procesar el sitio con Jekyll; es un archivo vacío, es normal)
3. Haz commit y push a la rama principal (`main`).
4. En el repositorio, ve a **Settings → Pages**.
5. En "Build and deployment" → "Source", elige **Deploy from a branch**.
6. En "Branch", elige `main` y la carpeta `/ (root)` (o `/docs` si subiste los archivos ahí). Guarda.
7. Espera 1-2 minutos. GitHub te dará la URL, normalmente:
   `https://<tu-usuario-de-github>.github.io/<nombre-del-repo>/`

Si quieres que la app esté directamente en `https://<tu-usuario>.github.io/` (sin subcarpeta), el repositorio se tiene que llamar exactamente `<tu-usuario>.github.io`.

## Comandos rápidos (si usas git desde terminal)

```bash
mkdir tupper-sync && cd tupper-sync
git init
cp /ruta/a/index.html .
cp /ruta/a/.nojekyll .
git add .
git commit -m "Publica Tupper Sync"
git branch -M main
git remote add origin https://github.com/<tu-usuario>/<nombre-del-repo>.git
git push -u origin main
```

Luego activa Pages siguiendo los pasos 4-6 de arriba.

## Notas

- La app usa `localStorage` del navegador para recordar qué casillas de compra y de cocina has marcado. Es por dispositivo/navegador: si abres la web en el móvil y en el portátil, cada uno guarda su propio progreso por separado.
- No requiere ningún proceso de build (no hay `npm install` ni compilación). Es HTML estático puro — subir el archivo tal cual es suficiente.
- Para actualizar el contenido en el futuro (nuevas semanas, cambios de menú), sustituye `index.html` por la versión nueva y vuelve a hacer commit + push; GitHub Pages se actualiza solo en 1-2 minutos.
