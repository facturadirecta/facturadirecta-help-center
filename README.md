# FacturaDirecta Help Center

Snapshot versionado del Help Center principal de FacturaDirecta.

El contenido se sincroniza desde Intercom, pero el repo usa un nombre genérico porque en el futuro puede alimentar otros canales, agentes o procesos de revisión.

## Estructura

```text
articles/          # snapshot de artículos existentes en Intercom, publicados o draft
drafts/            # borradores o propuestas locales antes de crear artículo en Intercom
assets/intercom/   # backup local de imágenes referenciadas desde artículos de Intercom
metadata/intercom/ # estado de sincronización
reviews/intercom/  # informes de revisión/reconciliación
mappings/          # relaciones futuras con features, código y owners
evals/fin-ai/      # casos futuros de regresión para Fin AI
```

## Formato de artículos

Los archivos en `articles/` y `drafts/` usan Markdown con front matter YAML y cuerpo HTML compatible con Intercom.

- Para artículos existentes en Intercom, el archivo vive en `articles/<intercom_id>.md` y debe incluir `intercom_id`.
- Para propuestas nuevas, el archivo empieza en `drafts/` sin `intercom_id`; al crearlo en Intercom, el flujo lo mueve o materializa como `articles/<nuevo_intercom_id>.md`.
- El cuerpo se guarda como HTML, no como Markdown semántico, porque Intercom devuelve y acepta HTML. Preferimos commitear la forma normalizada por Intercom.
- `created_at`, `updated_at` y `url` son metadatos de snapshot. Pueden cambiar tras un guardado en Intercom y no deben interpretarse como cambios editoriales del contenido.
- La definición completa del formato está en el README de `intercom-sync`, sección `Article Format`.

## Credenciales

El CLI lee las variables de entorno definidas en `.intercom-sync.yml`. Para uso local, crea un `.env` en la raíz de este repo usando `sample.env` como referencia:

```bash
cp sample.env .env
```

Variables esperadas:

- `INTERCOM_ACCESS_TOKEN`: token de acceso a la API de Intercom.
- `INTERCOM_DEFAULT_AUTHOR_ID`: id del autor de Intercom usado por defecto al crear o actualizar artículos.

No commitear `.env`; solo `sample.env` debe vivir en Git.

## Sincronización

La herramienta se ejecuta como comando `intercom-sync`. Para desarrollo local puede instalarse globalmente desde el repo de la herramienta:

```bash
cd ../intercom-sync
npm install
npm run build
npm install -g .
```

Una vez instalado, ejecuta los comandos desde la raíz de este repo para que cargue `.intercom-sync.yml` y `.env`:

```bash
intercom-sync validate
intercom-sync status
intercom-sync pull --dry-run
intercom-sync pull
intercom-sync pull-images
intercom-sync diff
intercom-sync reconcile
```

`intercom-sync pull-images` descarga una copia local de las imágenes remotas referenciadas por los artículos en `assets/intercom/images/` y actualiza `metadata/intercom/assets.json`. No cambia el HTML de los artículos: las URLs de Intercom siguen siendo la referencia canónica.
