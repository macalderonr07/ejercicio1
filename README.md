# Ejercicio 1 — Pagina de presentacion personal

Primer ejercicio de HTML semantico, CSS y JavaScript basico: una pagina de
presentacion personal de una sola vista con navegacion interna, seccion "Sobre
mi", seccion de habilidades con un boton para mostrar/ocultar, y un pie de
pagina con contacto y el anio actual generado dinamicamente.

## Estructura del proyecto

```
ejercicio1/
├── index.html   # Estructura semantica: header, nav, main, section, footer
├── styles.css   # Estilos: layout centrado, paleta oscura en header/footer
├── script.js    # Anio dinamico en el footer + toggle de la lista de habilidades
├── foto.jpg     # Imagen de la seccion "Sobre mi"
└── .github/workflows/deploy.yml  # Pipeline de CI/CD a GitHub Pages
```

## Que hace la pagina

- **Header**: titulo y navegacion (`Sobre mi`, `Habilidades`, `Contacto`) con
  enlaces ancla (`#sobre-mi`, `#habilidades`, `#contacto`) hacia las secciones
  del `main`.
- **Sobre mi**: foto de perfil y una breve descripcion.
- **Habilidades**: lista de habilidades (HTML5 semantico, CSS3 basico,
  JavaScript basico) que se puede mostrar/ocultar con un boton, usando
  `classList.toggle` sobre la clase `.oculto`.
- **Footer**: datos de contacto y el anio actual calculado con
  `new Date().getFullYear()`.

## Correcciones aplicadas durante la ingesta a este repo

Al revisar el codigo antes de subirlo se detectaron y corrigieron los
siguientes errores, necesarios para que la pagina funcione y se despliegue
correctamente:

- `<html lang="es>"` tenia la comilla de cierre despues del `>`, lo que dejaba
  la etiqueta `<html>` sin cerrar realmente (el navegador la cerraba recien en
  el `<head>` siguiente). Se corrigio a `<html lang="es">`.
- `initial/scale=1.0` en el `<meta name="viewport">` tenia una barra en vez de
  un guion; se corrigio a `initial-scale=1.0`.
- Los enlaces del `<nav>` apuntaban a `sobre-mi`, `habilidades` y `contacto`
  sin el `#`, por lo que el navegador intentaba navegar a paginas inexistentes
  en vez de hacer scroll a la seccion. Se agrego el `#` a cada `href`.
- El tercer enlace del menu decia "Sobre mi" pero apuntaba a `#contacto`; se
  corrigio el texto a "Contacto" para que coincida con el destino.
- En `styles.css`, la propiedad `front-family` (typo de `font-family`) no
  tenia efecto alguno, dejando la tipografia en el default del navegador; se
  corrigio el nombre de la propiedad.
- El selector `header nav ui` no aplicaba porque el elemento es `<ul>`, no
  `<ui>`; se corrigio a `header nav ul` para que el layout en fila (`flex`)
  del menu funcione.
- La imagen se llamaba `foto.jpg_large` (nombre tipico al descargar una
  imagen desde redes sociales). Se renombro a `foto.jpg` y se actualizo la
  referencia en `index.html` para usar una extension estandar.

## Despliegue

El sitio se despliega automaticamente a **GitHub Pages** mediante GitHub
Actions (`.github/workflows/deploy.yml`) en cada push a `main`, usando las
acciones oficiales `actions/configure-pages`, `actions/upload-pages-artifact`
y `actions/deploy-pages`. No requiere build: al ser HTML/CSS/JS plano, se
publica el contenido del repositorio tal cual.

URL de despliegue: https://macalderonr07.github.io/ejercicio1/

## Autor

Matias Calderon — matiascalderon147@hotmail.com
