
# Monorepo (Python uv + Node.js pnpm) (monorepo-uv-pnpm)

A monorepo container with both Python (uv) and Node.js (pnpm) with isolated dependencies.



It is assumed that you have `frontend` and `backend` directories at the root of your project.
This creates a named volume overlay for `node_modules` inside `frontend` and `.venv` inside `backend` directory.
Me think there is way to provide/customize these folders via `devcontainer-template.json` options ~


---

_Note: This file was auto-generated from the [devcontainer-template.json](https://github.com/CheapNightbot/moe-dev-configs/blob/main/src/monorepo-uv-pnpm/devcontainer-template.json).  Add additional notes to a `NOTES.md`._
