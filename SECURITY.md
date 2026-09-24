# Política de seguridad

### Propósito de este documento

- **Objetivos:** Declarar el canal privado de avisos y la superficie de este fork del catálogo.
- **Estructura:** Versiones soportadas → cómo reportar → superficie relevante → alcance.
- **Contenido a integrar según contexto:** Adapta el canal a este repositorio. No copies la política de un SaaS. El dataset TOML es público; no commitees tokens de sync, claves de Cloudflare ni `.env`.

## Versiones soportadas

| Línea | Soportada |
| ----- | --------- |
| Rama `dev` de este fork | Sí (gobernanza y CI P0 de `Alexendros/models.dev`) |
| Catálogo / sitio / SDK de [anomalyco/models.dev](https://github.com/anomalyco/models.dev) | Upstream; este fork no opera ese servicio |

## Cómo reportar una vulnerabilidad

**No abras un issue público** si el hallazgo puede filtrar secretos de automatización (tokens de sync, Cloudflare, npm) o facilitar abuso de la API pública.

1. Preferible: [GitHub Security Advisory](https://github.com/Alexendros/models.dev/security/advisories/new) en este repositorio.
2. Alternativa: correo a [operaciones@alexendros.dev](mailto:operaciones@alexendros.dev).
3. Defectos del producto o del dataset canónico: notifica también a [anomalyco/models.dev](https://github.com/anomalyco/models.dev) **sin** detalles explotables.

Incluye: commit o rama, fichero TOML o script, y un caso **mínimo sintético** (nunca secretos reales). Responderemos en un plazo máximo de 7 días naturales.

## Superficie relevante

- El catálogo (`models/`, `providers/`) es metadato público. Un error de precio o de límites no es por sí solo una vulnerabilidad.
- Los workflows de deploy, sync y publicación del SDK están **gated** a `anomalyco/models.dev` y no deben ejecutarse en este fork.
- No commitees `.env`, tokens de GitHub, `CLOUDFLARE_*` ni credenciales de npm.
- Issues de seguridad del sitio público https://models.dev pertenecen al upstream.

## Alcance

Este repositorio mantiene una copia de trabajo del catálogo y de las herramientas de validación. No opera el sitio, la API de producción ni el paquete npm `@opencode-ai/models`.
