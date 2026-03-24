# Node Inspector Adapter

Status: placeholder adapter definition. Runtime execution is not implemented yet.

Low-level runtime adapter for focused Node.js debugging probes through inspector-compatible workflows.

## Responsibility

- attach to or launch a Node.js debug session when the host project supports it
- place targeted breakpoints or equivalent probes
- read only the requested runtime values
- return structured observations to `debug-checkup`

## Non-Goals

- do not diagnose the bug on your own
- do not decide which hypothesis matters
- do not default to broad step-by-step execution
