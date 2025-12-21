# Repository Guidelines

## Project Structure & Module Organization

- `.claude/skills/fecfile/` contains the skill content and scripts.
- `.claude/skills/fecfile/SKILL.md` is the main skill entrypoint and usage guide.
- `.claude/skills/fecfile/FORMS.md` and `.claude/skills/fecfile/SCHEDULES.md` document FEC form and schedule mappings.
- `.claude/skills/fecfile/scripts/fetch_filing.py` is the only executable code, used to fetch filings.
- `README.md` and `CLAUDE.md` describe installation, usage, and project context.

## Build, Test, and Development Commands

- `uv run .claude/skills/fecfile/scripts/fetch_filing.py <FILING_ID>`: Fetch a full filing as JSON.
- `uv run .claude/skills/fecfile/scripts/fetch_filing.py <FILING_ID> --summary-only`: Summary only, no itemizations.
- `uv run .claude/skills/fecfile/scripts/fetch_filing.py <FILING_ID> --schedule A`: Limit to a single schedule.
- `uv run .claude/skills/fecfile/scripts/fetch_filing.py <FILING_ID> --stream`: JSONL streaming for large filings.

Dependencies are managed via inline PEP 723 metadata and installed automatically by `uv run`.

## Coding Style & Naming Conventions

- Python uses 4-space indentation and standard library `argparse` conventions.
- Keep functions small and descriptive (e.g., `build_options`, `stream_filing`).
- Prefer straightforward, readable logic over clever abstractions.
- No formatter is enforced; keep code PEP 8–friendly and consistent with `fetch_filing.py`.

## Testing Guidelines

- There is no automated test suite in this repository.
- Validate changes manually by running the script with a known filing ID.
- For large filings, verify `--summary-only` or `--stream` behavior to avoid memory issues.

## Commit & Pull Request Guidelines

- Commit messages are short, imperative, and sentence-style (e.g., “Add streaming mode”).
- Keep commits scoped to a single change or feature.
- PRs should include a concise description, the command(s) used to verify, and sample output when behavior changes.

