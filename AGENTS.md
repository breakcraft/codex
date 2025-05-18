# Repository Overview

This repo contains two major implementations of the Codex CLI:

- **`codex-cli/`** – TypeScript source that builds the Node.js version of the CLI.
- **`codex-rs/`** – Rust workspace containing the in-progress native implementation.

Both directories are maintained in parallel and have separate tooling requirements.

Additional resources live under `docs/` and example tasks reside in `codex-cli/examples`.

# Rust (`codex-rs`)

The Rust workspace targets edition **2024** and contains several crates (e.g. `core`, `cli`, `tui`).

Guidelines for changes in this folder:

- Never modify code that references `CODEX_SANDBOX_NETWORK_DISABLED_ENV_VAR`. Tests rely on this variable being set to abort network-dependent logic in the sandbox.
- Run `cargo fmt -- --check` and `cargo clippy --tests -- -D warnings` before pushing.
- Run `cargo test --all-features` to ensure the workspace builds and tests cleanly.

# Codex Repository Guidelines

## Node/TypeScript (codex-cli)

- Requires **Node.js 22+** and **pnpm 10.8.1**.
- Source lives under `codex-cli/src` and is bundled via **esbuild** using `build.mjs`.
- Run `pnpm test`, `pnpm run lint`, and `pnpm run typecheck` before pushing.
- Use `pnpm test:watch` during development for faster feedback.
- Code style is enforced via **ESLint** and **Prettier** (see `.eslintrc.cjs` and `.prettierrc.toml`).
- Git hooks managed by **Husky** automatically format and test code.

## Contributing Workflow

- Start feature branches from `main` and keep them focused.
- Add or update tests when fixing bugs or adding features.
- Document user-facing behaviour updates in the README or help output.
- Keep commits atomic and ensure all checks pass before pushing.
- Sign the CLA by commenting `I have read the CLA Document and I hereby sign the CLA` on your pull request.

## Releasing `codex`

- Run `pnpm stage-release` from `codex-cli/` to prepare an npm package.
