# Junipr API — OpenAPI Specification

This repository contains the official [OpenAPI 3.1](https://spec.openapis.org/oas/v3.1.0) specification for the **Junipr API**.

## Endpoints

| Method | Path | Description |
|--------|------|-------------|
| `POST` | `/v1/screenshot` | Capture a screenshot of any URL |
| `POST` | `/v1/pdf` | Generate a PDF from a URL or raw HTML |
| `GET`  | `/v1/metadata` | Extract Open Graph, Twitter Card, and structured data |
| `GET`  | `/health` | Service health check (no auth) |

## Quick start

All authenticated endpoints require an `X-API-Key` header.

```bash
# Screenshot
curl -X POST https://api.junipr.io/v1/screenshot \
  -H "X-API-Key: YOUR_KEY" \
  -H "Content-Type: application/json" \
  -d '{"url": "https://example.com"}' \
  --output screenshot.png

# PDF
curl -X POST https://api.junipr.io/v1/pdf \
  -H "X-API-Key: YOUR_KEY" \
  -H "Content-Type: application/json" \
  -d '{"url": "https://example.com", "format": "Letter"}' \
  --output page.pdf

# Metadata
curl https://api.junipr.io/v1/metadata?url=https://example.com \
  -H "X-API-Key: YOUR_KEY"
```

## Using the spec

### Swagger UI / Redoc

Paste the raw URL of `openapi.yaml` into any OpenAPI viewer:

- **Swagger Editor** — https://editor.swagger.io/?url=https://raw.githubusercontent.com/junipr-labs/openapi/main/openapi.yaml
- **Redoc** — https://redocly.github.io/redoc/?url=https://raw.githubusercontent.com/junipr-labs/openapi/main/openapi.yaml

### Client generation

Generate a typed client in any language with [OpenAPI Generator](https://openapi-generator.tech):

```bash
npx @openapitools/openapi-generator-cli generate \
  -i openapi.yaml \
  -g typescript-fetch \
  -o ./client
```

### Validation

```bash
npx @redocly/cli lint openapi.yaml
```

## SDKs

| Language | Package |
|----------|---------|
| Node.js / TypeScript | [`@junipr/sdk`](https://github.com/junipr-labs/sdk-node) |

## License

[MIT](LICENSE)
