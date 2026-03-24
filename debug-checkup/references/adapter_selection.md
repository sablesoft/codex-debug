# Adapter Selection

Choose the narrowest adapter that can answer the current runtime question.

Selection guidance:

- use `php-xdebug` for PHP runtimes that already expose an Xdebug-compatible debugging path
- use `node-inspector` for Node.js runtimes that expose the inspector protocol
- do not select an adapter if the hypothesis can already be resolved from code reasoning alone
- do not select an adapter that would require broad runtime exploration when a focused probe is sufficient

Availability guidance for the current implementation stage:

- treat an adapter as available only when `adapters.yaml` marks it as executable
- do not treat an adapter folder by itself as evidence that the adapter is ready
- if the selected adapter is not yet executable through this skill, report that limitation immediately
