# Señas en Misión: El viaje de Lucas (LSC)

Página web educativa e interactiva para aprender vocabulario básico de **Lengua de Señas Colombiana (LSC)**, dirigida a estudiantes de décimo grado (16–18 años). Acompaña a **Lucas** por cinco escenarios de Bogotá y aplica las señas en situaciones cotidianas.

**Sitio publicado:** https://carriondulce14-rgb.github.io/FINAL-PAGE-LUCAS/

El proyecto es un único archivo `index.html` (HTML + CSS con Tailwind por CDN + JavaScript). No requiere compilación ni dependencias instaladas.

---

## Cómo ver los cambios reflejados en el enlace

El sitio se publica con **GitHub Pages** desde la rama **`main`**, carpeta raíz (`/`). Todo lo que esté en `main/index.html` es lo que muestra el enlace. Los cambios hechos en otras ramas **no** aparecen hasta que lleguen a `main`.

### Flujo recomendado (con Pull Request)

1. Trabaja en una rama (por ejemplo `evolucion-lsc-senas-en-mision`) y abre un Pull Request hacia `main`.
2. **Fusiona (merge) el Pull Request a `main`.** Al hacer merge, GitHub Pages detecta el cambio en `main` y reconstruye el sitio automáticamente.
3. Espera **1–2 minutos** y recarga el enlace. Si no ves el cambio, fuerza la recarga sin caché:
   - Windows/Linux: `Ctrl + F5`
   - macOS: `Cmd + Shift + R`

### Alternativa (edición directa en `main`)

Si editas `index.html` directamente en la rama `main` (push o edición desde la web de GitHub), Pages también reconstruye solo. Úsalo con cuidado: `main` es la rama publicada en producción.

### Verificar que Pages está activo y apuntando a `main`

En el repositorio: **Settings → Pages**. Debe mostrar:

- **Source:** Deploy from a branch
- **Branch:** `main` — carpeta `/ (root)`

Si no está activado, selecciónalo ahí y guarda; en unos minutos el enlace quedará disponible.

### Comprobar el estado del despliegue

- Pestaña **Actions** del repositorio: la ejecución más reciente de *pages build and deployment* debe aparecer en verde.
- O desde la terminal con GitHub CLI:

  ```bash
  gh api repos/carriondulce14-rgb/FINAL-PAGE-LUCAS/pages --jq '.status, .html_url, .source'
  ```

---

## Ejecutar el proyecto en local

Al ser un solo archivo estático, basta con abrir `index.html` en el navegador. Para que todo (incluidos los posibles videos) funcione igual que en producción, es mejor servirlo por HTTP:

```bash
# Opción 1: Python
python3 -m http.server 8000
# luego abre http://localhost:8000

# Opción 2: Node (npx)
npx serve .
```

> Nota: la página usa Tailwind, Lucide y Google Fonts por CDN, así que necesita conexión a internet para verse con el estilo completo. Si un CDN no está disponible, la página incluye estilos base de respaldo y sigue siendo utilizable.

---

## Estructura de la experiencia

Ruta de aprendizaje recomendada (marcada con un *stepper* en la barra superior):

1. **Inicio** — presentación del proyecto.
2. **Misión** — presentación de Lucas y los objetivos.
3. **Entrenamiento** — aprendizaje del vocabulario (material multimedia por seña).
4. **Aventura** — cinco capítulos con decisiones que cambian la historia.
5. **Evaluación** — juego de memoria como instrumento de evaluación.
6. **Diccionario** — consulta y repaso libre de las 12 señas.

El progreso (capítulos completados, decisiones, final, estrellas, entrenamiento y evaluación) se guarda en el navegador con `localStorage`, así que puedes cerrar y continuar después. Hay un botón para reiniciar el progreso (pide confirmación).

---

## Añadir los videos demostrativos de LSC (pendiente)

Las señas incluyen un **espacio multimedia preparado**, pero **no traen videos reales**: no se simula ninguna demostración. Para incorporarlos:

1. Graba o consigue el video de cada seña con una **persona competente en LSC** (nativa o intérprete certificada).
2. Guarda los archivos en el repositorio (por ejemplo en una carpeta `videos/`).
3. En `index.html`, dentro del objeto `LSC_MODULES`, asigna la ruta en el campo `videoSrc` de la seña correspondiente. Ejemplo:

   ```js
   { id: 'hola', name: 'HOLA', /* ... */, videoSrc: 'videos/hola.mp4' }
   ```

4. Al tener `videoSrc`, el reproductor (reproducir / pausar / repetir) aparece automáticamente en Entrenamiento, Aventura, Evaluación y Diccionario.

> **Importante:** el material demostrativo debe ser revisado por una persona competente en LSC antes de usarse como referencia oficial.

---

## Accesibilidad

- Navegación por teclado y foco visible.
- Etiquetas ARIA y textos alternativos.
- Contraste suficiente e indicadores que no dependen solo del color.
- Controles de reproducción/pausa y opción para **reducir animaciones**.
- Diseño adaptable a celulares, tabletas y computadores.
