# Contribuir a este fork de models.dev

### Propósito de este documento

- **Objetivos:** Explicar setup, flujo de rama/PR y reglas para contribuir al catálogo sin reescribir el producto ni el dataset.
- **Estructura:** Idioma → setup → flujo de trabajo → comprobaciones antes del PR → reglas.
- **Contenido a integrar según contexto:** Adapta Bun y `bun validate` de este repo. No copies un flujo pnpm/monorepo. El detalle de TOML, `base_model` y el esquema vive en [README.md](README.md) y [AGENTS.md](AGENTS.md).

Idioma: este fichero, `SECURITY.md` y el aviso de fork del README en español. Identificadores de CI y nombres de jobs en inglés (`quality`, `test`, `smoke`). La guía de datos del README (secciones API / Contributing / Schema) se conserva en inglés, como en el upstream.

Lee también [AGENTS.md](AGENTS.md) (contrato del catálogo) y [SECURITY.md](SECURITY.md).

## Este repositorio es un fork

`Alexendros/models.dev` parte de [anomalyco/models.dev](https://github.com/anomalyco/models.dev). La rama por defecto es `dev`. No clones a ciegas el canon de producto: no actives deploy, sync horario ni publicación del SDK en este fork.

## Setup

```bash
bun install
```

Requiere [Bun](https://bun.sh/).

## Flujo de trabajo

Rama `feat/*` / `fix/*` / `docs/*` / `chore/*` → PR contra `dev`. Los agentes Cloud usan `cursor/…`.

Cambios de catálogo (TOML de labs o providers) siguen las reglas de [AGENTS.md](AGENTS.md): `base_model` si el host no creó el modelo; fichero de lab completo si falta; costes en USD/MTok.

## Antes de un PR

```bash
bun validate
bun test
```

- `bun validate` — valida el catálogo contra el esquema (job CI `quality`).
- El job CI `test` corre un subconjunto unitario (schema, helpers, cliente SDK). El `bun test` completo del workspace incluye auditorías del dataset vivo y el snapshot generado del SDK; hoy fallan en el `dev` del upstream y no se reescriben en este fork.
- El job `smoke` comprueba que existen los ficheros P0 y que `models.json` es JSON válido.

Si mueves campos de provider a `models/`, compara la salida generada:

```bash
bun run compare:migrations
```

## Reglas

- No reescribas el frontend, el dataset ni el generador salvo que el cambio sea el objeto del PR.
- No pises `LICENSE` (MIT del proyecto original).
- Conventional Commits. Cuerpo y docs de gobernanza en español; IDs de modelo y campos TOML en inglés.
- Vulnerabilidades: [SECURITY.md](SECURITY.md), no un issue público.
- Sin secretos, `.env` ni claves de Cloudflare/npm en el diff.
- Los workflows `Deploy`, `Sync Model Catalogs` y `Publish SDK` permanecen gated a `anomalyco/models.dev`.
