# PokePad Plugins Repository

Este es un repositorio de ejemplo que demuestra cómo alojar plugins de PokePad para que la aplicación los pueda descubrir e instalar remotamente.

## Estructura

*   `registry.json`: Es el "índice" de tu repositorio. La aplicación PokePad debe configurarse para leer este archivo. Contiene la lista de todos los plugins disponibles, sus metadatos (como el autor, versión e icono) y la URL directa para descargar el `.zip`.
*   `plugins/`: Esta carpeta contiene los archivos `.zip` empaquetados de cada plugin. Cuando un usuario hace clic en "Instalar", la app descarga el `.zip` desde aquí y lo extrae.
*   `icons/`: (Opcional) Si decides usar imágenes web en lugar de emojis para tus plugins, puedes alojar los archivos `.png` o `.svg` aquí y referenciarlos en el `registry.json`.

## Cómo agregar un nuevo plugin

1.  Comprime tu plugin (asegúrate de que `manifest.json` e `index.js` o `index.html` estén en la raíz del `.zip` o dentro de una única carpeta principal).
2.  Coloca el archivo `.zip` en la carpeta `plugins/`.
3.  Abre el archivo `registry.json` y añade un nuevo objeto al array JSON con la información de tu plugin.
4.  Asegúrate de que la propiedad `downloadUrl` apunte directamente a la ruta *Raw* (cruda) de tu nuevo `.zip`.

## Nota sobre el campo `downloads`

Actualmente el campo `downloads` es estático. Al alojar esto en un servidor estático (como GitHub Pages o Raw files), el número no se actualizará automáticamente. Para automatizar esto en el futuro, podrías usar la API de GitHub Releases o un pequeño backend serverless.
