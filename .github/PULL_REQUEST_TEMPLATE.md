<!-- canon-managed: true -->

### Propósito de este documento

- **Objetivos:** Plantilla de PR para describir el cambio y exigir las comprobaciones del catálogo (`bun validate` / `bun test`) y los jobs `quality` / `test` / `smoke`.
- **Estructura:** Qué cambia → checklist (validación, docs, dataset, CI).
- **Contenido a integrar según contexto:** Adapta el checklist a este fork de models.dev. No copies plantillas de otro producto. Deploy, sync y publish del SDK no corren aquí.

## Qué cambia

<!-- feat/fix/docs + alcance en una o dos frases -->

## Checklist

- [ ] `bun validate` y `bun test`
- [ ] Si toca TOML de lab/provider: sigue [AGENTS.md](../AGENTS.md) (`base_model`, override-only, USD/MTok)
- [ ] Docs actualizadas (`README.md` o esta guía) si cambia el contrato de contribución
- [ ] Sin secretos, `.env` ni reescritura del dataset ajena al alcance
- [ ] CI `quality` / `test` / `smoke` en verde
