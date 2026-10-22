# Publicador Marca Personal

Sitio de apoyo para la herramienta personal con la que Jhon Moreno publica sus
propios reels en Instagram, Facebook y TikTok.

Existe por dos razones concretas:

1. **Meta y TikTok exigen que una app de desarrollador tenga web, términos de
   servicio y política de privacidad accesibles por HTTPS.** Son las tres
   páginas de este repositorio.
2. **La API de Instagram no acepta subir un archivo local**: pide una URL
   pública desde la que descargar el vídeo (`video_url`) y la portada
   (`cover_url`). Facebook y TikTok sí aceptan el binario directamente.

## Regla de operación: borrar el vídeo tras publicar

Los vídeos se suben a `media/` **solo** durante la publicación y se borran en
cuanto el reel está publicado en las redes correspondientes.

```sh
git rm media/<archivo>.mp4 media/<archivo>.jpg
git commit -m "borrar media tras publicar"
git push
```

No es una preferencia: está escrito en los términos y en la política de
privacidad de este mismo sitio, así que dejar un archivo aquí después de
publicar contradice lo que el sitio declara.

Mientras el archivo está en `media/` es público: cualquiera con la dirección
exacta puede descargarlo. Por eso solo se suben vídeos que van a publicarse en
abierto de todos modos, y solo el tiempo imprescindible.

## Páginas

| Archivo | Para qué |
|---|---|
| `index.html` | Web oficial de la app (campo *Web/Desktop URL*) |
| `terminos.html` | *Terms of Service URL* |
| `privacidad.html` | *Privacy Policy URL* |
| `media/` | Alojamiento temporal de vídeo y portada |

Las credenciales de las apps **no** viven aquí: están en el `.env` local del
proyecto de edición, con permisos restringidos y fuera de todo repositorio.
