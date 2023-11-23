# Build
Building the ODA Open API SDK for Rust.

## Tooling
Install [Rust](https://www.rust-lang.org/tools/install).\
Install [OpenAPI Generator](https://openapi-generator.tech/docs/installation).

# Generate
Generate a client and server for each ODA Open API.

## TMF634
```bash
openapi-generator-cli generate --generator-name rust-server --output tmf634 --additional-properties packageName=oda_sdk_tmf634 -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.1.0/swagger/TMF634-ResourceCatalog-v4.1.0.swagger.json
```

## TMF639
```bash
openapi-generator-cli generate --generator-name rust-server --output tmf639 --additional-properties packageName=oda_sdk_tmf639 -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.0.0/swagger/TMF639-ResourceInventory-v4.0.0.swagger.json
```

## Patch
Pending resolution of [BUG17136](https://github.com/OpenAPITools/openapi-generator/issues/17136) it is necesssary to patch the generated models for the servers:
```bash
sed -ie '/#\[validate(/a            length(min=1)' tmf{634,639}/src/models.rs
```

## Build SDK
```bash
cargo build --workspace
```

## Document SDK
```bash
cargo doc --workspace
```

## Build Examples
```bash
cargo build --examples --workspace
```

## Run Examples
```bash
cargo run --package oda_sdk_tmf634 --example client -- --help
cargo run --package oda_sdk_tmf634 --example server -- --help
cargo run --package oda_sdk_tmf639 --example client -- --help
cargo run --package oda_sdk_tmf639 --example server -- --help
```

