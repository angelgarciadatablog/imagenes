# imagenes

Origen único de las imágenes de [angelgarciadatablog.com](https://www.angelgarciadatablog.com).
Se sirven por GitHub Pages y se referencian **siempre por URL absoluta**, desde cualquier repo.

```
https://www.angelgarciadatablog.com/imagenes/<seccion>/<slug>/<archivo>
```

## Por qué un repo aparte

Las imágenes son binarias: cada versión que se sube se queda en el historial de git para
siempre. Manteniéndolas fuera, el repo del blog conserva un historial ligero. Y al haber un
solo origen, la misma imagen sirve al blog, al portafolio y a los casos sin duplicarse.

Referenciarlas por URL absoluta tiene un efecto secundario que importa: los posts del vault
se siguen viendo completos en Obsidian, sin que `publish.py` tenga que copiar nada.

## Estructura

```
blog/<slug-del-post>/         imágenes de un post
portafolio/<slug-del-caso>/   imágenes de un caso del portafolio
assets/                       comunes a todo el sitio
```

Cada carpeta lleva el slug de la página que la usa. Así se sabe siempre a qué pertenece una
imagen y qué borrar cuando se retira esa página.

## Convenciones

- **Nombres en kebab-case**, descriptivos: `revenue-vs-views.png`, no `captura1.png`.
- **El slug de la carpeta es el mismo** que el de la página en la web. Si el slug cambia
  (no debería: el slug es sagrado), hay que actualizar los enlaces a mano — nada avisa de
  que se han roto.
- **PNG** para capturas de pantalla e interfaces, **JPG** para fotografía.
- **Ancho máximo 1600 px.** Una captura de dashboard debería quedar por debajo de 300 KB.
- **Nunca borrar una imagen que siga referenciada.** Borrar aquí rompe la página que la usa,
  y el fallo no aparece hasta que alguien abre esa página.

## Uso

```markdown
![Ingresos frente a vistas](https://www.angelgarciadatablog.com/imagenes/portafolio/ecommerce-performance-insights/revenue-vs-views.png)
```

```html
<img src="https://www.angelgarciadatablog.com/imagenes/portafolio/ecommerce-performance-insights/revenue-vs-views.png"
     alt="Ingresos frente a vistas" loading="lazy" />
```

## Límites

GitHub Pages sirve hasta 1 GB por sitio, con un límite blando de 100 GB de tráfico al mes.
A 200 KB por captura son unas 5.000 imágenes. Si algún día entra video o archivos pesados,
esto deja de ser la herramienta adecuada y toca un bucket.

`assets/pixel.png` es un PNG de 1×1 que sirve para comprobar que Pages sigue entregando
imágenes. No se usa en ninguna página.
