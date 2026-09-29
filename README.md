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
| `unified/task.yml` | Task for a single per-machine store: `project`, `kind`, `increment`, `gate`, `depends_on`, with a `graph:` block for `ark ready` and `ark gates` |
| `unified/increment.yml` | A sequenced slice of a build (the one word for increment, band, milestone), with its own closing gate |
| `unified/ticket.yml` | Knowledge node for a tracker ticket (Jira key as the lookup key); created on first touch |
| `unified/decision.yml` | ADR-shaped decision record, superseded never deleted |
| `unified/fact.yml` | One-paragraph durable fact; `push: true` facts are injected by `ark prime` |
| `unified/retro.yml` | Retrospective on a ticket, increment, or session set: went well, hurt, actions with owner and destination, open until every action lands |

## The unified set

`unified/` is the schema set for running one ark store per machine (`ARK_ROOT`) across many projects. Every artifact carries a `project` field; increments replace per-project notions of bands and milestones; `gate` and `depends_on` drive `ark ready`, and `ark gates` answers "what is waiting on me". Requires ark 0.7.0 or newer for the `graph:` block. Pull all five:

```yaml
# .ark/schemas/task.yml
name: task
registry: https://raw.githubusercontent.com/milesmcleod/ark-schemas/main/unified/task.yml
```

ADRs stay in the product repos; they document the code, not the store.

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
