# FacturaDirecta Help Center

Snapshot versionado del Help Center principal de FacturaDirecta.

El contenido se sincroniza desde Intercom, pero el repo usa un nombre genérico porque en el futuro puede alimentar otros canales, agentes o procesos de revisión.

## Estructura

```text
articles/          # snapshot de artículos existentes en Intercom, publicados o draft
drafts/            # borradores o propuestas locales antes de crear artículo en Intercom
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
- La definición completa del formato está en `../intercom-sync/README.md`, sección `Article Format`.

## Sincronización

La herramienta vive en `../intercom-sync`.

```bash
node ../intercom-sync/dist/cli/index.js validate
node ../intercom-sync/dist/cli/index.js pull --dry-run
node ../intercom-sync/dist/cli/index.js pull
node ../intercom-sync/dist/cli/index.js diff
node ../intercom-sync/dist/cli/index.js reconcile
```
