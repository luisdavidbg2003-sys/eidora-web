# Web de Eidora — https://eidora.app

Repositorio **público** con la web de la app Eidora. Antes la app se llamaba Studeo y este
repositorio, `studeo-legal`. Se publica con **GitHub Pages** en el dominio `eidora.app`. El código de
la app está en un repositorio **privado** aparte.

| Archivo | Qué es |
|---|---|
| `index.html` | La portada |
| `privacidad.html`, `terminos.html` | Política de privacidad y términos de uso: las tiendas exigen una dirección web para ellos. Se ven en `eidora.app/privacidad` y `eidora.app/terminos` |
| `404.html` | La página de «no encontrado». **Además recibe los enlaces de «Compartir mazo»** (`eidora.app/mazo/<id>`) y enseña el botón para abrir el mazo en la app |
| `CNAME` | Le dice a GitHub Pages que la web va en `eidora.app`. **No borrarlo** |
| `.nojekyll` | Que GitHub publique los archivos tal cual, sin procesarlos (hará falta para la carpeta `.well-known` de los enlaces universales) |
| `icon.png`, `favicon.png` | Copias de los iconos de la app |
| `compartir.png` | La imagen de 1200×630 que sale al pegar un enlace de la web en WhatsApp, redes, etc. (etiquetas `og:image` de `index.html` y `404.html`). Se dibujó el 27/09/2026 a partir de `icon.png`, con los colores de la web |
| `robots.txt`, `sitemap.xml` | Para buscadores: todo se puede indexar, y la lista de páginas. **Si se añade una página, hay que añadirla al `sitemap.xml`** |

## No editar los textos legales a mano

`privacidad.html` y `terminos.html` se generan desde el repositorio de la app, a partir de los
**mismos archivos que lee la app** (`legal/politicaPrivacidad.js` y `legal/terminos.js`), con:

```bash
node scripts/generar-legal.mjs
```

El script los copia aquí solo si esta carpeta está al lado de la del proyecto, con el nombre
`eidora-web`. Así la web y la app no pueden decir cosas distintas. Si editas el HTML directamente,
el siguiente cambio en la app lo sobrescribirá.

Al cambiar un texto legal hay que **actualizar a mano la fecha** de la primera línea en
`legal/*.js`, volver a generar y subir este repositorio.

## El dominio

Los registros DNS de `eidora.app` están en Dinahosting. La web usa los cuatro registros A de
GitHub Pages para `eidora.app` y un CNAME de `www` a `luisdavidbg2003-sys.github.io`. Los registros
del correo (MX, `mail`) y los de Resend (`resend._domainkey`, `rsend`, `send`, `_dmarc`) **no se
tocan**: son los que hacen funcionar el correo.
