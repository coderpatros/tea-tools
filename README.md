# Transparency Exchange API - OpenAPI Schema

OpenAPI schema for the [Transparency Exchange API (TEA) v0.4.0-beta.3](https://github.com/CycloneDX/transparency-exchange-api) server specification.

> **Note:** This schema has been generated from the upstream TEA specification and may contain errors or omissions. Always refer to the [official repository](https://github.com/CycloneDX/transparency-exchange-api) as the authoritative source.

## Limitations

The current version of the spec has several limitations to be aware of:

- **Consumer-only API.** Only GET endpoints are defined. The publisher API (creating, updating, and deleting products, components, collections, and artifacts) is planned for after the TEA 1.0 release.
- **No `.well-known/tea` endpoint.** The discovery flow starts with a DNS lookup and a fetch to `https://<domain>/.well-known/tea`, but this well-known endpoint is not part of the OpenAPI spec itself. Its JSON schema is defined separately in the upstream repo at [`discovery/tea-well-known.schema.json`](https://github.com/CycloneDX/transparency-exchange-api/blob/main/discovery/tea-well-known.schema.json).
- **Minimal error response detail.** Error responses for 400 and 401 have empty schemas. The 404 response returns a simple `error-response` object with a single enum field (`OBJECT_UNKNOWN` or `OBJECT_NOT_SHAREABLE`).
- **No mutual TLS representation.** The spec defines Bearer and Basic auth security schemes, but mutual TLS (mTLS) — which is a supported authentication method per the TEA auth specification — cannot be fully represented in OpenAPI.
- **Pagination only on product endpoints.** Paginated responses (`pageOffset`/`pageSize` parameters) are available on product and product release search/listing endpoints, but component release listings return plain arrays.
- **No search for components.** There is a `GET /products` and `GET /productReleases` search endpoint (query by identifier), but no equivalent `GET /components` or `GET /componentReleases` search endpoint exists yet.

## Upstream Resources

- [TEA Specification Repository](https://github.com/CycloneDX/transparency-exchange-api)
- [TEA Requirements](https://github.com/CycloneDX/transparency-exchange-api/blob/main/doc/tea-requirements.md)
- [TEA Use Cases](https://github.com/CycloneDX/transparency-exchange-api/blob/main/doc/tea-usecases.md)
- [Discovery Specification](https://github.com/CycloneDX/transparency-exchange-api/blob/main/discovery/readme.md)
- [Authentication Specification](https://github.com/CycloneDX/transparency-exchange-api/blob/main/auth/readme.md)
- [Consumer API Flow](https://github.com/CycloneDX/transparency-exchange-api/blob/main/api-flow/consumer.md)
- [Publisher API Flow](https://github.com/CycloneDX/transparency-exchange-api/blob/main/api-flow/publisher.md)

TEA is being standardized through ECMA TC54 Task Group 1.
