# eleventy-base-blog v9.0.1

Una plantilla de inicio que muestra cómo construir un blog con el generador de sitios Eleventy (usando la versión de lanzamiento [v3.0](https://github.com/11ty/eleventy/releases/tag/v3.0.0)).

## Comenzando

¿Quieres una guía de inicio más detallada?

### Crear y navegar a un directorio:
```sh
mkdir mi-nombre-de-blog
cd mi-nombre-de-blog
```

### Clonar este Repositorio
```sh
git clone https://github.com/11ty/eleventy-base-blog.git .
```

Opcional: Revisa `eleventy.config.js` y `_data/metadata.js` para configurar las opciones y datos del sitio.

### Instalar dependencias
```sh
npm install
```

### Ejecutar Eleventy
Genera una compilación lista para producción en la carpeta `_site`:
```sh
npx @11ty/eleventy
```

O compila y aloja en un servidor de desarrollo local:
```sh
npx @11ty/eleventy --serve
```

O puedes ejecutar en modo de depuración para ver todos los internos.

## Características

- Uso de Eleventy v3 con salida de cero-JavaScript.
- El contenido es exclusivamente pre-renderizado (este es un sitio estático).
- Puede desplegarse fácilmente a una subcarpeta sin cambiar ningún contenido.
- Todas las URLs están desacopladas de la ubicación del contenido en el sistema de archivos.
- Configura las plantillas a través de la Cascada de Datos de Eleventy.
- Enfoque en el rendimiento: puntuación de cuatro cientos en Lighthouse de fábrica.
- 0 Cumulative Layout Shift.
- 0ms Total Blocking Time.
- Recarga en vivo de desarrollo local proporcionada por Eleventy Dev Server.
- Menú de navegación impulsado por el contenido.
- Optimización de imágenes completamente automatizada.
- Salida de cero-JavaScript.
- Soporte para formatos de imagen modernos automáticamente (p. ej. AVIF y WebP).
- Procesa imágenes bajo demanda durante `--serve` para construcciones locales rápidas.
- Prefiere el marcado `<img>` si es posible (un solo formato de imagen) pero cambia automáticamente a `<picture>` para múltiples formatos de imagen.
- Sintaxis automatizada de marcado `<picture>` con `srcset` y `sizes` opcionales.
- Incluye atributos `width/height` para evitar el desplazamiento del diseño del contenido.
- Incluye `loading="lazy"` para la carga perezosa nativa sin JavaScript.
- Incluye `decoding="async"`.
- Las imágenes pueden estar co-ubicadas con los archivos de publicaciones de blog.
- Paquetes de CSS por página a través de `eleventy-plugin-bundle`.
- Resaltador de sintaxis integrado (salida de cero-JavaScript).
- Contenido de borrador: usa `draft: true` para marcar cualquier plantilla como borrador. Los borradores solo se incluyen durante `--serve/--watch` y se excluyen de las compilaciones completas. Esto es impulsado por la API de configuración `addPreprocessor` en `eleventy.config.js`. El validador de esquema mostrará un error si se establece un valor no booleano en la cascada de datos.

### Publicaciones de Blog

- Enlaces automatizados de siguiente/anterior.
- Enlaces profundos accesibles a los encabezados.

### Páginas Generadas

- Páginas de Inicio, Archivo y Acerca de.
- Feed Atom incluido (con fácil cambio de una línea para usar RSS o JSON).
- Páginas de etiquetas de cero mantenimiento (Ver en la Demo).
- Página de contenido no encontrado (404).

### Demostraciones

- [Netlify](https://www.netlify.com)
- [Vercel](https://vercel.com)
- [Cloudflare Pages](https://pages.cloudflare.com)
- [Remix on Glitch](https://glitch.com)
- [GitHub Pages](https://pages.github.com)

### Despliega este sitio en tu propio sitio

Despliega este sitio Eleventy en solo unos pocos clics en estos servicios:

Lee más sobre [Desplegar un proyecto Eleventy en la web](https://www.11ty.dev/docs/deploy/).

- [Despliega esto a Netlify](https://www.netlify.com)
- [Despliega esto a Vercel](https://vercel.com)
- Mira en `.github/workflows/gh-pages.yml.sample` para información sobre el despliegue a GitHub Pages.
- [Pruébalo en Stackblitz](https://stackblitz.com)

### Notas de Implementación

- `content/about/index.md` es un ejemplo de una página de contenido.
- `content/blog/` tiene las publicaciones de blog pero realmente pueden vivir en cualquier directorio. Solo necesitan la etiqueta `posts` para ser incluidas en la colección de publicaciones de blog.
- Usa la clave `eleventyNavigation` (a través del complemento de Navegación de Eleventy) en tu front matter para agregar una plantilla a la navegación del sitio de nivel superior. Esto se usa en `content/index.njk` y `content/about/index.md`.
- El contenido puede estar en cualquier formato de plantilla (las publicaciones de blog no necesitan ser exclusivamente markdown, por ejemplo). Configura los formatos de plantilla compatibles de tu proyecto en `eleventy.config.js` -> `templateFormats`.
- La carpeta `public` en tu directorio de entrada se copiará a la carpeta de salida (a través de `addPassthroughCopy` en el archivo `eleventy.config.js`). Esto significa que `./public/css/*` vivirá en `./_site/css/*` después de que tu compilación se complete.
- Este proyecto usa tres Plantillas de Eleventy:
  - `_includes/layouts/base.njk`: la estructura HTML de nivel superior.
  - `_includes/layouts/home.njk`: la plantilla de la página de inicio (envuelta en `base.njk`).
  - `_includes/layouts/post.njk`: la plantilla de publicación de blog (envuelta en `base.njk`).
- `_includes/postslist.njk` es una inclusión de Nunjucks y es un componente reutilizable utilizado para mostrar una lista de todas las publicaciones. `content/index.njk` tiene un ejemplo de cómo usarlo.

### Política de Seguridad de Contenido

Si tu sitio aplica una Política de Seguridad de Contenido (como deberían hacer los sitios públicos), tienes algunas opciones (elige una):

- En `base.njk`, elimina `<style>{% getBundle "css" %}</style>` y descomenta `<link rel="stylesheet" href="{% getBundleFileUrl "css" %}">`.
- Configura el servidor con la directiva CSP `style-src: 'unsafe-inline'` (menos seguro).

## Beneficios para Usuarios y Desarrolladores

### Para Usuarios:

- **Rendimiento Rápido:** Los sitios estáticos generados con Eleventy son extremadamente rápidos, lo que mejora la experiencia del usuario.
- **Accesibilidad:** Las características como enlaces profundos accesibles y optimización de imágenes mejoran la accesibilidad del sitio.
- **Seguridad:** La salida de cero-JavaScript reduce el riesgo de vulnerabilidades basadas en JavaScript.

### Para Desarrolladores:

- **Facilidad de Despliegue:** Eleventy permite desplegar fácilmente a subcarpetas sin cambiar el contenido, lo que facilita la gestión del sitio.
- **Optimización de Imágenes:** La optimización automatizada de imágenes y el soporte para formatos modernos ahorran tiempo y esfuerzo.
- **Flexibilidad:** La capacidad de usar cualquier formato de plantilla y configurar plantillas a través de la Cascada de Datos de Eleventy ofrece una gran flexibilidad.

##### Esta versión en español de eleventy-base-blog v9 fue traducida y mejorada por [LuisAngelMaciel](https://github.com/luisangelmaciel).
