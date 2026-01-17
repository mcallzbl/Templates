# Agent Preferences - Templates Workspace

Use these defaults when creating or updating project templates in this repo.

## Copier template conventions
- Use `_templates_suffix: .jinja` in `copier.yml` so only `.jinja` files render.
- Default variables:
  - `project_name`: default `{{ _copier_conf.dst_path.name }}`
  - `project_slug`: `{{ project_name|lower|replace(' ', '-') }}`
  - `package_name`: `{{ project_slug }}`
  - `env_prefix`: `{{ project_name|upper|replace(' ', '_')|replace('-', '_') }}`
  - `author`: default `mcallzbl` (override per template if needed)
- Add `_tasks` to run `python scripts/init_git.py` for git init on create.

