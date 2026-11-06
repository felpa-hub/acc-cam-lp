# Accesibilidad Web — CAM La Plata

Este repositorio contiene el trabajo de accesibilidad web realizado sobre el sitio del Centro Administrativo Municipal (CAM) de La Plata y su sistema de turnos.

## ¿Qué es este proyecto?

Tomamos los archivos HTML originales del CAM y los adaptamos a los estándares de **a11y (accesibilidad)** siguiendo las pautas **WCAG 2.1** y **W3C**. Cada cambio quedó registrado como un commit separado, agrupado por "clase" de accesibilidad, para que sea fácil revisar y entender qué se modificó en cada etapa.

## Estructura del repositorio

```
acc-cam-lp/
├── source-html/                 # Código fuente ORIGINAL (sin modificar)
│   ├── index.html               # Página principal del CAM
│   ├── tramites/
│   │   ├── comercio.html
│   │   ├── licencias.html
│   │   ├── mesaentrada.html
│   │   ├── obrasparticulares.html
│   │   └── planeamiento.html
│   └── turnos/
│       ├── dem.html             # Login al DEM
│       ├── index.html           # Landing del sistema de turnos
│       └── misdatos.html        # Formulario de turno (3 pasos)
├── README.md                    # Este archivo
└── LICENSE
```

> **Nota:** Los archivos editados con accesibilidad no se suben como carpeta separada en este repositorio; cada cambio quedó registrado como commit sobre `source-html/`. Si necesitan las versiones finales editadas, pueden reconstruirlas aplicando los commits de las clases 1 a 7 sobre el código fuente.

## Cambios aplicados por clase

A continuación, un resumen de cada clase de accesibilidad y qué se corrigió en cada una.

### Clase 1 — Estructura y metadatos
- `<!DOCTYPE html>` como primera declaración del documento (evita modo quirks).
- `<html lang="es">` para que los lectores de pantalla pronuncien en español.
- `<title>` único y descriptivo por página (ej. "Licencias de Conducir | Centro Administrativo Municipal - La Plata").
- `<link rel="home">` en `<head>` para navegación auxiliar.

| Archivo |
|---------|
| `index.html` |
| `tramites/comercio.html` |
| `tramites/licencias.html` |
| `tramites/mesaentrada.html` |
| `tramites/obrasparticulares.html` |
| `tramites/planeamiento.html` |
| `turnos/dem.html` |
| `turnos/index.html` |
| `turnos/misdatos.html` |

### Clase 2 — Imágenes con texto alternativo (`alt`)
- Todas las imágenes informativas tienen un `alt` descriptivo.
- Las imágenes puramente decorativas llevan `alt=""` para que los lectores de pantalla las salteen.
- Se corrigió un `alt="#"` inválido en el logo del login DEM.

| Archivo | Detalle |
|---------|---------|
| `index.html` | 14 imágenes |
| `tramites/comercio.html` | — |
| `tramites/licencias.html` | — |
| `tramites/mesaentrada.html` | — |
| `tramites/obrasparticulares.html` | — |
| `tramites/planeamiento.html` | — |
| `turnos/dem.html` | — |

### Clase 3 — Enlaces y navegación
- Enlace "Saltar al contenido principal" visible al recibir el foco con la tecla Tab (antes estaba oculto con `display: none`, así que los lectores de pantalla nunca lo encontraban).
- Enlaces con `target="_blank"` llevan `rel="noopener noreferrer"` y un aviso para lectores de pantalla: "(abre en una nueva ventana)".
- Iconos de redes sociales: `target="_blank"` movido del `<i>` al `<a>` (era inválido en `<i>`), y cada uno tiene su `aria-label` descriptivo (Instagram, X, Facebook, Radio, Mapa).

| Archivo |
|---------|
| `index.html` |
| `tramites/comercio.html` |
| `tramites/licencias.html` |
| `tramites/mesaentrada.html` |
| `tramites/obrasparticulares.html` |
| `tramites/planeamiento.html` |
| `turnos/dem.html` |
| `turnos/index.html` |
| `turnos/misdatos.html` |

### Clase 4 — Formularios y campos
- Cada `<input>` y `<select>` tiene su `<label>` asociado mediante `for` / `id`.
- Campos obligatorios llevan `required` y `aria-required="true"`.
- El grupo CUIL (3 inputs separados) usa `<fieldset>` y `<legend>` para agruparlo lógicamente.
- Mensajes de error usan `<span class="campo-error" role="alert" aria-live="polite">` para que los lectores de pantalla los anuncien sin interrumpir.
- `pattern`, `minlength`, `maxlength` e `inputmode` para guiar el ingreso de DNI, CUIL y teléfono.

| Archivo |
|---------|
| `turnos/dem.html` |
| `turnos/misdatos.html` |

### Clase 5 — Modales y componentes dinámicos
- Modales con `aria-modal="true"` y `aria-labelledby="popupModalLabel"` para que el lector de pantalla sepa que el fondo está bloqueado y cuál es el nombre del modal.
- Paneles de resultado (éxito / error) con `aria-live="polite"` y `aria-live="assertive"` para anunciar cambios sin recargar la página.

| Archivo |
|---------|
| `index.html` |
| `tramites/comercio.html` |
| `tramites/planeamiento.html` |
| `turnos/misdatos.html` |

### Clase 6 — Jerarquía semántica
- Encabezados en orden lógico sin saltar niveles innecesarios (ej. `h4` → `h2`, `h6` → `h3`, etc.).

| Archivo |
|---------|
| `tramites/comercio.html` |

### Clase 7 — Contenido de terceros
- Enlaces a videos y publicaciones de Instagram en la Galería de videos con `aria-label` avisando que abren en una nueva ventana.

| Archivo |
|---------|
| `index.html` |
