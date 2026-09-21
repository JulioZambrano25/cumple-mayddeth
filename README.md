# Página de cumpleaños

Proyecto web listo para abrir y editar en Visual Studio Code. No necesita instalar Node.js ni dependencias.

## Abrir el proyecto

1. Descomprime el archivo ZIP.
2. Abre Visual Studio Code.
3. Selecciona **Archivo > Abrir carpeta**.
4. Elige la carpeta `proyecto-cumpleanos-vscode`.
5. Abre `index.html`.

Para verlo cómodamente, instala la extensión **Live Server** de Ritwick Dey. Después, haz clic derecho sobre `index.html` y selecciona **Open with Live Server**.

También puedes abrir `index.html` directamente con Chrome, Edge o Firefox.

## Personalizar el contenido

Todo está dentro de `index.html`.

- Busca `[Nombre]` y reemplázalo por el nombre de tu amiga.
- Busca `21 · SEPTIEMBRE · 2026` y cambia la fecha.
- Edita los textos de las secciones “Un poco sobre ti”, “Tres razones” y “Una carta para ti”.
- Los deseos aleatorios están al final del archivo, dentro de la variable `wishes`.

## Agregar una fotografía

1. Copia una foto dentro de la carpeta `imagenes`, por ejemplo `amiga.jpg`.
2. En `index.html`, busca:

```html
<div class="portrait reveal" role="img"
```

3. Sustituye todo ese `div` por:

```html
<div class="portrait reveal">
  <img src="imagenes/amiga.jpg" alt="Fotografía de [Nombre]"
       style="width:100%;height:100%;object-fit:cover">
</div>
```

## Usar una canción MP3

La versión actual incluye una melodía instrumental generada por el navegador, así que funciona sin descargar música.

Para usar una canción propia:

1. Guarda el archivo como `audio/cancion.mp3`.
2. Añade antes de `</body>`:

```html
<audio id="cancion" src="audio/cancion.mp3" loop preload="auto"></audio>
```

3. En el código JavaScript, reemplaza el contenido de las funciones `startMusic` y `stopMusic` por:

```javascript
async function startMusic() {
  const audio = document.querySelector('#cancion');
  await audio.play();
  playing = true;
  document.querySelector('#music').classList.add('playing');
  document.querySelector('#musicText').textContent = 'Pausar música';
}

function stopMusic() {
  document.querySelector('#cancion').pause();
  playing = false;
  document.querySelector('#music').classList.remove('playing');
  document.querySelector('#musicText').textContent = 'Activar música';
}
```

Los celulares suelen bloquear la reproducción automática con sonido. Por eso la página inicia la canción al tocar el regalo o el botón de música.

## Publicar cambios

Puedes publicar gratuitamente la carpeta con GitHub Pages, Netlify o Cloudflare Pages. Para GitHub Pages, sube `index.html` junto con las carpetas `imagenes` y `audio`.

