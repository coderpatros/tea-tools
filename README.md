# TEA Tools

A collection of tools, libraries, and resources for working with the [Transparency Exchange API (TEA)](https://github.com/CycloneDX/transparency-exchange-api).

TEA is being standardized through ECMA TC54 Task Group 1.

## OpenAPI Schema

An OpenAPI schema for the [TEA v0.4.0-beta.3](https://github.com/CycloneDX/transparency-exchange-api) server specification is included in this repository as [`openapi.yaml`](openapi.yaml).

> **Note:** This schema has been generated from the upstream TEA specification and may contain errors or omissions. Always refer to the [official repository](https://github.com/CycloneDX/transparency-exchange-api) as the authoritative source.

### Limitations

- **Consumer-only API.** Only GET endpoints are defined. The publisher API (creating, updating, and deleting products, components, collections, and artifacts) is planned for after the TEA 1.0 release.
- **No `.well-known/tea` endpoint.** The discovery flow starts with a DNS lookup and a fetch to `https://<domain>/.well-known/tea`, but this well-known endpoint is not part of the OpenAPI spec itself. Its JSON schema is defined separately in the upstream repo at [`discovery/tea-well-known.schema.json`](https://github.com/CycloneDX/transparency-exchange-api/blob/main/discovery/tea-well-known.schema.json).
- **Minimal error response detail.** Error responses for 400 and 401 have empty schemas. The 404 response returns a simple `error-response` object with a single enum field (`OBJECT_UNKNOWN` or `OBJECT_NOT_SHAREABLE`).
- **No mutual TLS representation.** The spec defines Bearer and Basic auth security schemes, but mutual TLS (mTLS) — which is a supported authentication method per the TEA auth specification — cannot be fully represented in OpenAPI.
- **Pagination only on product endpoints.** Paginated responses (`pageOffset`/`pageSize` parameters) are available on product and product release search/listing endpoints, but component release listings return plain arrays.
- **No search for components.** There is a `GET /products` and `GET /productReleases` search endpoint (query by identifier), but no equivalent `GET /components` or `GET /componentReleases` search endpoint exists yet.

## Postman Collection

A Postman collection for the TEA API is included as [`Transparency Exchange API.postman_collection.json`](Transparency%20Exchange%20API.postman_collection.json). Import it into [Postman](https://www.postman.com/) to explore and test TEA API endpoints interactively.

## Tools & Libraries

### sbomify

[sbomify](https://github.com/sbomify) is a product security artifact hub and trust center.

- [sbomify.com](https://sbomify.com/) — Hosted SBOM management platform
- [github.com/sbomify](https://github.com/sbomify) — Open source repositories

### Python Library

- [py-libtea](https://github.com/sbomify/py-libtea) — A Python client library for interacting with TEA-compatible servers. Useful for scripting, automation, and integration into Python-based toolchains.

### .NET Library & Tools

- [TEA .NET library and tools](https://github.com/coderpatros/dotnet-tea) — .NET library for the Transparency Exchange API. Provides client library, CLI and web tools for TEA.

### Reliza / Oolong

[Reliza](https://github.com/relizaio) provides a TEA server implementation:

- [Oolong](https://github.com/relizaio/oolong) — A lightweight TEA server implementation

## Upstream Resources

- [TEA Specification Repository](https://github.com/CycloneDX/transparency-exchange-api)
- [TEA Requirements](https://github.com/CycloneDX/transparency-exchange-api/blob/main/doc/tea-requirements.md)
- [TEA Use Cases](https://github.com/CycloneDX/transparency-exchange-api/blob/main/doc/tea-usecases.md)
- [Discovery Specification](https://github.com/CycloneDX/transparency-exchange-api/blob/main/discovery/readme.md)
- [Authentication Specification](https://github.com/CycloneDX/transparency-exchange-api/blob/main/auth/readme.md)
- [Consumer API Flow](https://github.com/CycloneDX/transparency-exchange-api/blob/main/api-flow/consumer.md)
- [Publisher API Flow](https://github.com/CycloneDX/transparency-exchange-api/blob/main/api-flow/publisher.md)
