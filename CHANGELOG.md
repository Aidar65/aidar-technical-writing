# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2026-08-08

### Added
- OpenAPI 3.0 specification for Valve Control REST API (docs/api/v1/valve-control.yaml).
- Interactive Swagger UI console page (docs/api/overview.md).
- mTLS & PKI security specifications (docs/security/pki-tls.md).
- Emergency torque control process diagram in BPMN 2.0 (docs/processes/bpmn-telemetry.md).
- CODESYS ST protection module documentation (docs/industrial/st-code-example.md).

### Fixed
- UTF-8 encoding issues across Markdown artifacts.
- Markdownlint rules compliance across all documentation files.

## [1.0.0] - 2026-08-01

### Added
- Initial MkDocs site structure with Material theme.
- Base GitHub Actions pipeline for automated builds.