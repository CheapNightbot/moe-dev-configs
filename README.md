# Moe-dev Configs ~ ♡

A collection of devcontainer configurations for different projects. I use and tested these with VSCode and Podman.

## What's inside?

- **deno** - For Deno projects
- **python-uv** - For Python projects using uv
- **monorepo-uv-pnpm** - For projects with both Python (uv) and Node.js (pnpm)

All templates use official images, run as non-root user, and keep your host filesystem clean.

For Podman, make sure to set `userns` to `keep-id`. Me simply set it in `containers.conf` file instead of `compose.yml`. You can check Podman docs for more information. But here quickly how to set it:

```bash
sudo vi /usr/share/containers/containers.conf
```

- Then find the line that says `#userns = "host"` (you can press `/` key, type `userns` and press enter/return key to find it), replace it with `userns = "keep-id"`.

Also make sure to create `node_modules` and `.venv` directoies on the host before running/opening in the devcontainer to prevent permissions for these folders on host:

> No modules / packages will be saved inside these folders on the host. But they need to exist on the host.

- For **deno**, create `node_modules` at the root of the project folder on the host.
- For **python-uv**, create `.venv` at the root of the project folder on the host.
- For **monorepo-uv-pnpm**, create `node_modules` inside the "frontend" directory & `.venv` inside the "backend" directory.
