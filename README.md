# SearchD Skills

Public Agent Skills and Claude Code plugins for measuring and improving how
brands appear in answer engines.

## Plugins

| Plugin | Skill | Description |
| --- | --- | --- |
| `searchd-aeo-audit` | `searchd-aeo-audit` | Measure buyer-question visibility, competing brands, and cited sources, then render an evidence-first English or Korean HTML report. |

## Install with Claude Code

Add the SearchD marketplace:

```text
/plugin marketplace add runbear-io/searchd-skills
```

Install the AEO audit plugin:

```text
/plugin install searchd-aeo-audit@searchd-skills
```

## Install as a portable Agent Skill

Compatible Agent Skills clients can install the same package directly:

```bash
npx skills add runbear-io/searchd-skills \
  --skill searchd-aeo-audit
```

## Run an audit

Ask the agent for a public-domain audit:

```text
Audit example.com for answer-engine visibility in the United States.
Use 12 buyer questions and render the report in Korean.
```

The audit plugin:

1. Inspects public company pages as untrusted research material.
2. Freezes an unbranded buyer-question panel.
3. Runs isolated neutral research workers.
4. Matches the target brand only after each answer is complete.
5. Preserves completed and failed runs in versioned JSON.
6. Renders a deterministic self-contained HTML report.

## Trust boundary

The target brand, company context, and SearchD promotion are not provided to
neutral research workers. Citation links accept only HTTP or HTTPS URLs with a
valid host.

Every report includes a visible `Powered by searchd.ai` attribution. An
optional agency CTA is added only after measurement, is explicitly labeled as
a commercial publisher message, and is excluded from all audit calculations.

## Validate

```bash
claude plugin validate .

cd searchd-aeo-audit/skills/searchd-aeo-audit
uv run --with pytest pytest -q tests
uvx ruff check .
uvx --with pytest basedpyright
uvx check-jsonschema \
  --schemafile schemas/audit.schema.json \
  examples/searchd-ai-audit.json
```

## License

MIT
