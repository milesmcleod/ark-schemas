# Contributing to ark-schemas

Schemas in this registry are the recommended defaults for [ark](https://github.com/milesmcleod/ark). They're opinionated starting points - most users will customize them for their own projects.

## Proposing changes

Open an issue before submitting a PR for schema changes. Schema changes affect every project that pulls from this registry, so they need discussion first.

## Adding new schemas

If you have a schema that would be broadly useful (not project-specific), open an issue describing the use case. Good candidates are schemas that represent common artifact types across many teams - things like `epic`, `rfc`, `incident`, `retrospective`.

## Schema format

See `ark schema-help` for the full format reference. Every schema here should:

- Have a clear `name` that describes the artifact type
- Use `\d{3,}` patterns for IDs (not `\d{3}` - allows growth beyond 999)
- Include `created` and `updated` date fields as derived
- Include a sensible `template` for new artifacts

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
