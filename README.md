# Build
Building the ODA Open API SDK for Rust.

## Tooling
Install [Rust](https://www.rust-lang.org/tools/install).\
Install [OpenAPI Generator](https://openapi-generator.tech/docs/installation).

# Generate
Generate a client and server for each ODA Open API.

## TMF634
```bash
openapi-generator generate --generator-name rust --output tmf634-client --additional-properties packageName=tmf634-client -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.1.0/swagger/TMF634-ResourceCatalog-v4.1.0.swagger.json
openapi-generator generate --generator-name rust-server --output tmf634-server --additional-properties packageName=tmf634-server -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.1.0/swagger/TMF634-ResourceCatalog-v4.1.0.swagger.json
```

## TMF639
```bash
openapi-generator generate --generator-name rust --output tmf639-client --additional-properties packageName=tmf639-client -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.0.0/swagger/TMF639-ResourceInventory-v4.0.0.swagger.json
openapi-generator generate --generator-name rust-server --output tmf639-server --additional-properties packageName=tmf639-server -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.0.0/swagger/TMF639-ResourceInventory-v4.0.0.swagger.json
```

## Patch
Pending resolution of [BUG17136](https://github.com/OpenAPITools/openapi-generator/issues/17136) it is necesssary to patch the generated models for the servers:
```bash
sed -ie '/#\[validate(/a            length(min=1)' tmf{623,639}-server/src/models.rs
```

## Build
In each API subdirectory:
```bash
cargo build
```

## Document
In each API subdirectory:
```bash
cargo doc
```
