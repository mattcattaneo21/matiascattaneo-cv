# Matias Cattaneo — CV

CV web bilingüe (EN/ES) estático, publicado en GitHub Pages.

**Live:** https://mattcattaneo21.github.io/matiascattaneo-cv/

## Estructura

```
matiascattaneo-cv/
├── index.html      # versión en inglés (raíz)
├── es/
│   └── index.html  # versión en español
├── styles.css      # estilos compartidos (tokens claro/oscuro, print)
├── app.js          # toggle de tema + animaciones de scroll-reveal
├── cv_en.md        # fuente del contenido en inglés
├── cv_es.md        # fuente del contenido en español
├── assets/
│   └── profile.jpg # foto de perfil (opcional — placeholder con iniciales si falta)
└── README.md
```

## Arquitectura

- **Idiomas:** inglés en la raíz, español en `/es/`. El switch EN/ES del nav
  son links estáticos entre ambas páginas; cada página declara `hreflang`
  para SEO. No hay toggle de idioma por JavaScript.
- **Tema:** modo claro/oscuro con variables CSS. El botón del nav guarda la
  elección en `localStorage`; sin elección guardada se usa la preferencia
  del sistema (`prefers-color-scheme`). Sin JavaScript, el sistema decide.
- **Animaciones:** hero con entrada escalonada y secciones con scroll-reveal
  (IntersectionObserver). Se desactivan con `prefers-reduced-motion` y sin JS
  el contenido queda siempre visible.
- **PDF:** el botón "Download Resume (PDF)" usa la hoja `@media print`
  (Ctrl+P → guardar como PDF). El PDF siempre sale en claro.

## Fuente de verdad

El contenido vive en `cv_en.md` / `cv_es.md`. **No hay build step**: al editar
el CV, actualizá el `.md` y replicá el cambio en `index.html` y `es/index.html`.

## Foto de perfil

Agregá `assets/profile.jpg` (recomendado cuadrada, ~400×400). Si no existe, el
header muestra las iniciales "MC" como fallback.

## Publicar en GitHub Pages

Push a `main` y luego: **Settings → Pages → Deploy from Branch → main → / (root)**.
