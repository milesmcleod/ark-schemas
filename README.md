# ark-schemas

Reusable schema definitions for [ark](https://github.com/milesmcleod/ark) - human-legible, agent-optimized project artifact management.

## Usage

Reference a schema in your `.ark/schemas/` file:

```yaml
name: task
registry: https://raw.githubusercontent.com/milesmcleod/ark-schemas/main/task.yml
```

Then run `ark registry-pull` to fetch the latest version.

## Available schemas

| Schema | Description |
|---|---|
| `task.yml` | Task/backlog management with priority ordering |
| `spec.yml` | Gherkin-style feature specifications |
| `adr.yml` | Architectural Decision Records |
| `base-task.yml` | Base task schema for inheritance |

## Extending

Use `extends` in your local schema to inherit from a base:

```yaml
name: my-task
extends: base-task
fields:
  - name: project
    type: enum
    required: true
    values: [frontend, backend, infra]
```

## License

MIT
