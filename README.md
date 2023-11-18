# Build
Building the ODA Open API SDK for Rust.

## Tooling
Install [Rust](https://www.rust-lang.org/tools/install).
Install [OpenAPI Generator](https://openapi-generator.tech/docs/installation).

# Generate
Generate a client and server for each ODA Open API.

## TMF634
	openapi-generator generate --generator-name rust --output tmf634-client --additional-properties packageName=tmf634-client -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.1.0/swagger/TMF634-ResourceCatalog-v4.1.0.swagger.json
	openapi-generator generate --generator-name rust-server --output tmf634-server --additional-properties packageName=tmf634-server -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.1.0/swagger/TMF634-ResourceCatalog-v4.1.0.swagger.json

## TMF639
	openapi-generator generate --generator-name rust --output tmf639-client --additional-properties packageName=tmf639-client -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.0.0/swagger/TMF639-ResourceInventory-v4.0.0.swagger.json
	openapi-generator generate --generator-name rust-server --output tmf639-server --additional-properties packageName=tmf639-server -i https://tmf-open-api-table-documents.s3.eu-west-1.amazonaws.com/OpenApiTable/4.0.0/swagger/TMF639-ResourceInventory-v4.0.0.swagger.json

## Build
In each API subdirectory:
	cargo build

## Document
In each API subdirectory:
	cargo doc

