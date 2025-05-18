# Rust/codex-rs

In the codex-rs folder where the rust code lives:

- Never add or modify any code related to `CODEX_SANDBOX_NETWORK_DISABLED_ENV_VAR`. You operate in a sandbox where `CODEX_SANDBOX_NETWORK_DISABLED=1` will be set whenever you use the `shell` tool. Any existing code that uses `CODEX_SANDBOX_NETWORK_DISABLED_ENV_VAR` was authored with this fact in mind. It is often used to early exit out of tests that the author knew you would not be able to run given your sandbox limitations.

# Codex Repository Guidelines

## Node/TypeScript (codex-cli)

- Requires **Node.js 22+** and **pnpm 10.8.1**.
- Run `pnpm test`, `pnpm run lint`, and `pnpm run typecheck` before pushing.
- Use `pnpm test:watch` during development for faster feedback.
- Git hooks managed by **Husky** automatically format and test code.

## Contributing Workflow

- Start feature branches from `main` and keep them focused.
- Add or update tests when fixing bugs or adding features.
- Document user-facing behaviour updates in the README or help output.
- Keep commits atomic and ensure all checks pass before pushing.
- Sign the CLA by commenting `I have read the CLA Document and I hereby sign the CLA` on your pull request.

## Releasing `codex`

- Run `pnpm stage-release` from `codex-cli/` to prepare an npm package.

