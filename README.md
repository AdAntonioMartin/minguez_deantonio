# Memorial Familia Mínguez - De Antonio

Datos de este memorial: las personas de la rama Mínguez – De Antonio, sus lazos
y sus fotografías. El código de la web vive en
[family-tree-engine](https://github.com/AdAntonioMartin/family-tree-engine) y
llega como dependencia, así que aquí no hay nada de HTML, CSS ni JavaScript.

## Puesta en marcha

```bash
npm install
npm run serve      # construye dist/ y lo sirve en http://localhost:4321
npm run check      # construye y valida los datos — pásalo antes de terminar
npm run smoke      # prueba en un Chrome real: las 3 páginas, teclado y móvil
```

`npm run build` produce `dist/`, que es lo que se publica. `dist/` no se
versiona.

## Qué hay aquí

| Ruta | Qué es |
|---|---|
| `site.config.json` | Nombre, dominio, idioma y tema del sitio |
| `data/personas/<id>.json` | Una ficha por persona (14) |
| `data/personas-index.json` | Mapa `id → ruta` |
| `data/unions.json` | Las 5 uniones: parejas e hijos. Única fuente de parentesco |
| `data/trees/index.json` | La vista del árbol y su persona raíz |
| `data/lista.json` | Qué personas y columnas muestra el listado |
| `images/personas/` | Fotos servidas, en tres tamaños y dos formatos |

El árbol se recorta desde `luis-de-antonio-minguez`, que desciende de las dos
líneas (De Antonio y Mínguez) y por eso alcanza a las 14 personas: desde un
antepasado de una sola de las ramas quedarían fuera los ascendientes de la otra.

## Alta de una persona

1. Crear `data/personas/<id>.json` (el `id` debe cumplir `^[a-z0-9-]+$`).
2. Añadir la entrada `id → ruta` en `data/personas-index.json`.
3. Referenciarla en `data/unions.json`.
4. `npm run add-photo -- <id> <foto> [--hero]` para sus fotografías.
5. `npm run check`.

## Relación con martin-tapias-memorial

Estas 14 personas **también están** en
[martin-tapias-memorial](https://github.com/AdAntonioMartin/martin-tapias-memorial),
que reúne el árbol completo de 161 personas y donde esta rama es la vista
`?tree=deantonio`.

Son copias independientes: **editar una ficha aquí no la actualiza allí**, ni al
revés. Si corriges una fecha o añades una foto de alguien que aparece en los dos
sitios, hay que hacerlo en ambos o quedarán divergentes.

## Publicación

Cada push a `main` dispara el workflow que construye `dist/` y lo publica en
GitHub Pages. En **Ajustes → Pages**, el origen debe ser **GitHub Actions**.
