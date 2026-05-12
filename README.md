# FacturaDirecta Help Center

Snapshot versionado del Help Center principal de FacturaDirecta.

El contenido se sincroniza desde Intercom, pero el repo usa un nombre genérico porque en el futuro puede alimentar otros canales, agentes o procesos de revisión.

## Estructura

```text
articles/          # artículos publicados del Help Center principal
drafts/            # borradores o propuestas antes de publicar
metadata/intercom/ # estado de sincronización
reviews/intercom/  # informes de revisión/reconciliación
mappings/          # relaciones futuras con features, código y owners
evals/fin-ai/      # casos futuros de regresión para Fin AI
```

## Sincronización

La herramienta vive en `../intercom-sync`.

```bash
node ../intercom-sync/dist/cli/index.js validate
node ../intercom-sync/dist/cli/index.js pull --dry-run
node ../intercom-sync/dist/cli/index.js pull
node ../intercom-sync/dist/cli/index.js diff
node ../intercom-sync/dist/cli/index.js reconcile
```
