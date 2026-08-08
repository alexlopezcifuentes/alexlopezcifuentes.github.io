# alexlopezcifuentes.github.io

Web personal, construida sobre la plantilla
[academicpages](https://github.com/academicpages/academicpages.github.io)
(Jekyll) y publicada gratis en GitHub Pages.

**En produccion:** <https://alexlopezcifuentes.github.io>

---

## Como funciona, en una frase

El contenido son ficheros de texto (Markdown y YAML) en este repo. Cada vez que
haces `git push`, un GitHub Action reconstruye el HTML y lo publica. No hay base
de datos, no hay servidor, no hay nada que mantener ni actualizar.

## Lo que se toca a diario

| Quiero...                        | Toco...                              |
|----------------------------------|--------------------------------------|
| Anadir una noticia               | `_data/news.yml`                     |
| Anadir un paper                  | un fichero nuevo en `_publications/` |
| Anadir una charla                | un fichero nuevo en `_talks/`        |
| Anadir una asignatura            | un fichero nuevo en `_teaching/`     |
| Editar la bio de la portada      | `_pages/about.md`                    |
| Cambiar nombre, redes, tema      | `_config.yml`                        |
| Cambiar el menu de arriba        | `_data/navigation.yml`               |
| Subir un PDF                     | `files/` → queda en `/files/loquesea.pdf` |
| Cambiar la foto                  | `images/profile.jpg`                 |

## Anadir una noticia

La seccion "Latest news" de la portada sale entera de `_data/news.yml`. Anadir
una novedad son dos lineas, y **no hay que tocar la bio**: para eso existe esta
seccion.

```yaml
- date: 2026-11-02
  text: >-
    Texto en Markdown, con **negritas** y [enlaces](https://ejemplo.com).
```

Se ordenan solas por fecha, de mas nueva a mas vieja, asi que da igual donde la
pegues dentro del fichero. La portada muestra las 5 mas recientes; ese numero se
cambia en `_pages/about.md`, en la linea `{% raw %}{% include news.html limit=5 %}{% endraw %}`.

## Anadir una publicacion

Crea `_publications/AAAA-MM-DD-slug-corto.md`. El nombre del fichero solo
importa para el orden; lo que se muestra sale del bloque de arriba:

```markdown
---
title: "Titulo exacto del paper"
collection: publications
category: manuscripts     # manuscripts | conferences | chapters | preprints | theses
permalink: /publication/2026-slug-corto
excerpt: 'Una o dos frases. Esto es lo que Google ensena como descripcion.'
date: 2026-03-15
venue: 'Nombre de la revista o congreso'
paperurl: 'https://doi.org/10.xxxx/xxxxx'
citation: 'Autores. (2026). &quot;Titulo.&quot; <i>Venue</i>, vol(num), pags.'
---

Texto libre en Markdown: resumen, enlace al codigo, figuras, lo que quieras.
```

Las categorias y sus titulos se definen en `publication_category` dentro de
`_config.yml`. El paper aparece solo en `/publications/`.

## Anadir una charla

Igual, en `_talks/AAAA-MM-DD-slug.md`:

```markdown
---
title: "Titulo de la charla"
collection: talks
type: "Workshop presentation"   # Talk | Tutorial | Conference proceedings talk | ...
permalink: /talks/2026-03-15-slug
venue: "Nombre del sitio o del workshop"
date: 2026-03-15
location: "Ciudad, Pais"
---
```

## Anadir una asignatura

En `_teaching/AAAA-periodo-slug.md`:

```markdown
---
title: "Nombre de la asignatura"
collection: teaching
type: "Undergraduate course"      # o "Graduate course", "Workshop", ...
permalink: /teaching/2026-nombre-asignatura
venue: "Universidad, Departamento"
date: 2026-09-01                  # inicio del curso
location: "Madrid, Spain"
---

Que se da en la asignatura, tu papel en ella, enlaces a material.
```

## Ver los cambios en local antes de publicar

El Ruby que trae macOS es demasiado viejo para Jekyll, asi que usamos Docker:

```bash
docker compose up          # primera vez tarda unos minutos
```

Abre <http://localhost:4000>. Se recarga solo al guardar un fichero, **excepto**
`_config.yml`: si tocas ese, `docker compose restart`.

Para comprobar que compila sin errores, igual que hace el CI:

```bash
docker compose run --rm jekyll-site jekyll build --strict_front_matter --destination /tmp/_site_check
```

El `--destination` no es opcional. Ese comando compila con `_config.yml` a
secas, es decir con `url: https://alexlopezcifuentes.github.io`, y si lo dejas
escribir en `_site/` machaca lo que esta sirviendo el contenedor: la web sigue
cargando pero busca el CSS en el dominio de produccion y la ves sin estilos.
Si te pasa, se arregla con `docker compose restart`.

## Publicar

```bash
git add -A
git commit -m "Add paper X"
git push
```

El Action de `.github/workflows/deploy.yml` hace el resto (aprox. 1 minuto).
Puedes ver el progreso en la pestana **Actions** del repo.

---

## SEO: que esta puesto y que hay que hacer a mano

Ya configurado en el repo:

- `jekyll-sitemap` genera `/sitemap.xml` en cada build.
- `robots.txt` apunta a ese sitemap.
- `_includes/schema-person.html` emite datos estructurados
  [schema.org/Person](https://schema.org/Person) en la portada: nombre, variantes
  del nombre, puesto, empresa, universidad, temas y `sameAs` hacia Scholar,
  LinkedIn y GitHub. Esto es lo que le dice a Google que este dominio y esos
  perfiles son la misma persona.
- Cada pagina lleva `<title>`, `meta description`, canonical y Open Graph.

Pendiente de hacer a mano (una vez, ver seccion de tareas abajo):

1. Dar de alta el sitio en [Google Search Console](https://search.google.com/search-console)
   y pegar el token en `google_site_verification` de `_config.yml`.
2. Enviar `https://alexlopezcifuentes.github.io/sitemap.xml` desde Search Console.
3. Poner el enlace a la web en LinkedIn, GitHub y Google Scholar. Los enlaces
   entrantes desde perfiles con autoridad son, con diferencia, lo que mas acelera
   el posicionamiento por nombre propio.
El ORCID ya esta puesto y enlazado desde el JSON-LD.

## Estructura del repo

```
_config.yml            configuracion global: identidad, redes, SEO, categorias
_data/navigation.yml   menu de la cabecera
_pages/                paginas sueltas (portada y listados)
_publications/         un fichero por paper
_talks/                un fichero por charla
_teaching/             un fichero por asignatura
_posts/                blog (vacio de momento)
_includes/             fragmentos HTML del tema
_layouts/              plantillas de pagina
_sass/                 estilos
files/                 PDFs y adjuntos
images/                imagenes, foto de perfil y favicons
images/news/           miniaturas de la seccion de noticias
```

Para cambiar el aspecto sin tocar CSS, `site_theme` en `_config.yml` acepta
`default`, `air`, `sunrise`, `mint`, `dirt` y `contrast`.
