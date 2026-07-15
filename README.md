# Moe-dev Configs ~ ♡

A collection of devcontainer configurations for different projects. I use and tested these with VSCode and Podman. All templates use official images, run as non-root user, and keep your host filesystem clean.

## What's inside?

- [**deno**](src/deno) - For Deno projects
- [**node**](src/node) - For Node.js projects (with pnpm)
- [**python-uv**](src/python-uv) - For Python projects using uv
- [**monorepo-uv-pnpm**](src/monorepo-uv-pnpm) - For projects with both Python (uv) and Node.js (pnpm)

## How to use?

You can use these templates in two ways (choose the one you like!). For example, if you want to use the **monorepo-uv-pnpm** template:

### Method 1: VSCode Dev Container Extension (Recommended) ~

1. Make sure you have [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension installed in VS Code.
2. Press `F1` to open Command Palette and run `Dev Containers: Add Dev Container Configuration Files...`.
  - Select "Add configuration to workspace" or "Add configuration to user data folder".
3. Next, when it asks to select a template, paste the template's URL: `ghcr.io/cheapnightbot/moe-dev-configs/monorepo-uv-pnpm:latest`.
4. **Important:** Create required directories before reopening in container:
   ```bash
   mkdir -p frontend/node_modules backend/.venv
   ```
5. Press `F1` and run `Dev Containers: Reopen in Container`.

Alternatively, you can use the [Dev Container CLI](https://github.com/devcontainers/cli) to apply a template:

```bash
devcontainer templates apply \
  --template-id ghcr.io/cheapnightbot/moe-dev-configs/monorepo-uv-pnpm \
  --workspace-folder /path/to/your/project
```

### Method 2: Manual Copy ~

1. Copy the `.devcontainer` folder from the template you want (e.g. `src/monorepo-uv-pnpm/.devcontainer`) to the root of your project.
  - Create required directories. See [Important Notes](#important-notes) below.
  - Optionally, modify `.devcontainer/devcontainer.json` and/or `.devcontainer/compose.yml` as needed (add extensions, expose ports, etc.).
2. Make sure you have [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension installed in VS Code.
3. Press `F1` to open Command Palette and run `Dev Containers: Reopen in Container`.

> Me think you can also use in GitHub Codespaces, but I did not try it ~

## Important Notes

For Podman, make sure to set `userns` to `keep-id`. Me simply set it in `containers.conf` file instead of `compose.yml`. You can check Podman docs for more information. But here quickly how to set it:

```bash
sudo vi /usr/share/containers/containers.conf
```

- Then find the line that says `#userns = "host"` (you can press `/` key, type `userns` and press enter/return key to find it), replace it with `userns = "keep-id"`.

Also make sure to create `node_modules` and `.venv` directories on the host before running/opening in the devcontainer to prevent permissions for these folders on host:

> No modules / packages will be saved inside these folders on the host. But they need to exist on the host.

- For **deno** and **node**, create `node_modules` at the root of the project folder on the host.
- For **python-uv**, create `.venv` at the root of the project folder on the host.
- For **monorepo-uv-pnpm**, create `node_modules` inside the "frontend" directory & `.venv` inside the "backend" directory.
