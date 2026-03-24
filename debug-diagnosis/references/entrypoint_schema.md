# Entrypoint Schema

Use a compact structured description of the execution entrypoint.

Recommended fields:

- `type`
- `label`
- `command`
- `path`
- `arguments`
- `environment`
- `reproduction_notes`

Supported conceptual entrypoint types:

- `cli_script`
- `phpunit_test`
- `web_handler`
- `queue_worker`
- `scheduled_command`
- `node_script`
- `other`
