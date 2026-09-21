# Textos legales de Studeo

Repositorio **público** que sirve únicamente la política de privacidad y los términos de uso de
Studeo, porque App Store y Google Play exigen una dirección web para ellos y no aceptan que estén
solo dentro de la app.

El código de la app está en un repositorio **privado** aparte; aquí no hay nada más que estas
páginas.

## No editar estos archivos a mano

Se generan desde el repositorio de la app, a partir de los **mismos archivos que lee la app**
(`legal/politicaPrivacidad.js` y `legal/terminos.js`), con:

```bash
node scripts/generar-legal.mjs
```

Así la web y la app no pueden decir cosas distintas. Si editas el HTML directamente, el siguiente
cambio en la app lo sobrescribirá y habrás creado justo el problema que esto evita.

Al cambiar un texto legal hay que **actualizar a mano la fecha** de la primera línea en
`legal/*.js`, volver a generar, y copiar aquí los archivos.
