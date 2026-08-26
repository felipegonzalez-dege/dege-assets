# dege-assets

Assets públicos de **DEGE Muebles** (dege.com.ar) servidos por GitHub Pages.

Existe porque la descripción de los productos de Tiendanube es HTML plano: no
puede usar los helpers del tema, y el banco de imágenes de TN sólo acepta
imágenes. Los videos de la tienda vivían todos en el CDN de un proveedor
externo; esto los trae a un lugar propio, versionado y servido por código.

## Cómo se usa

    <video src="https://felipegonzalez-dege.github.io/dege-assets/video/cumo-sistema.mp4"
           poster="https://felipegonzalez-dege.github.io/dege-assets/video/cumo-sistema-poster.jpg"
           controls playsinline preload="metadata"></video>

## Reglas

- **Repo PÚBLICO.** Nada que no pueda verse en internet.
- Los videos entran ya comprimidos para 4G. El original queda fuera del repo.
  Receta: `ffmpeg -i ORIGINAL.mp4 -vf scale=540:-2 -c:v libx264 -profile:v main
  -preset slow -crf 33 -pix_fmt yuv420p -c:a aac -b:a 56k -ac 1
  -movflags +faststart salida.mp4`
- `+faststart` no es opcional: sin eso el navegador baja el archivo entero
  antes de mostrar el primer frame.

## Contenido

| archivo | qué es | peso |
|---|---|---|
| `video/cumo-sistema.mp4` | Explicación a cámara del Sistema Cumo, 60 s, 540×960. Va en el bloque B00 de la página de producto. | 3,8 MB |

## Imágenes

Van acá las que TN recomprimiría de más. TN sirve máximo 1024×1024 y baja la
calidad a ~1/5 (el conector pasaba de 25 KB a 9,7 KB); GitHub Pages entrega el
archivo tal cual. El filename es la URL pública, así que va con nombre SEO.

    # master lossless en el repo, publicado en q=100 (invisible, 1/3 del peso)
    Image.open(src).save(dest, "WEBP", quality=100, method=6)
