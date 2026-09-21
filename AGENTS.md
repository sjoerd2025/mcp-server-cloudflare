# AGENTS.md

## Repository overview

This repository is a pnpm/Turbo monorepo for Cloudflare MCP servers. The main top-level directories are:

- `apps/`: individual MCP server applications, each with its own package and often its own CONTRIBUTING/README guidance.
- `packages/`: shared workspace packages used by one or more apps.

The repository root contains the shared tooling and workspace scripts used across the monorepo.

## Working conventions

- Make small, targeted changes that match existing patterns in the surrounding code.
- Prefer updating existing files and conventions over introducing new abstractions.
- If you change an app under `apps/`, read that app's local `README.md` and `CONTRIBUTING.md` before making changes.
- Keep changes consistent with the shared formatting and linting configuration in `.prettierrc.json` and `.oxlintrc.json`.
- Preserve workspace dependency conventions and avoid introducing ad hoc version pinning.

## Common commands

Run these from the repository root:

- `pnpm install` - install dependencies
- `pnpm dev:setup` - create the local development environment file from the template
- `pnpm dev` - start the local development stack
- `pnpm build` - build the workspace
- `pnpm test` - run the test suite
- `pnpm check` - run formatting, dependency, lint, typecheck, and test validation
- `pnpm check:deps` - validate dependency version consistency
- `pnpm update-deps` - update dependencies while preserving syncpack rules

For targeted test runs, use Vitest directly when appropriate, for example:

- `pnpm test -- <path-to-test>`

## Validation expectations

- For code changes, run the most relevant validation command before finishing.
- For documentation-only changes, a formatting check on the touched Markdown file is usually sufficient.
- If a change affects a specific app, prefer app-specific validation when available.

## Environment and secrets

Many apps require Cloudflare credentials and other local configuration values. Use the existing environment template and local files such as `.env.development.local` rather than hardcoding secrets.

Do not commit secrets, tokens, or credentials. Keep sensitive values local.

## Repo-specific notes

- This repository uses Turbo for workspace orchestration and pnpm workspaces.
- `DEVELOPMENT.md` contains the local development workflow and port reference.
- `CONTRIBUTING.md` contains the monorepo architecture and testing guidance.
- `README.md` provides the high-level product and server overview.
