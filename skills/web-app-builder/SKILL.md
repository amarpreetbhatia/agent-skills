---
name: web-app-builder
description: Scaffold and configure Modern.js web applications. Use when the user asks to create a new Modern.js project or to add microfrontend, BFF, Docker, and modern deployment setup.
compatibility: Requires Node.js with npm, pnpm, or yarn, network access to the current Modern.js documentation, and Docker only when container support is required.
metadata:
  author: amarpreetbhatia
  version: "1.0"
---

# Web App Builder

Use this skill to scaffold a production-oriented Modern.js application that is ready for microfrontend development, BFF integration, and containerized deployment.

## Workflow

1. Inspect the target directory and existing project files.
2. Ask for missing requirements that materially change the scaffold, such as package manager, TypeScript preference, framework mode, application host/remote role, or deployment target.
3. Fetch the current Modern.js guides at `https://modernjs.dev/guides/` before scaffolding.
4. Generate the project with the officially documented Modern.js CLI and the options that match the user's requirements.
5. Configure module federation for microfrontend readiness.
6. Enable the BFF plugin and create a minimal BFF structure only where appropriate.
7. Add a Docker configuration based on the current Node.js LTS release.
8. Install dependencies, run project checks, and fix any scaffold or configuration errors.
9. Summarize the generated structure and the commands needed to run, build, and test the application.

Do not use guessed package names, obsolete CLI flags, or documentation known to differ between Modern.js releases. Verify package and configuration names against the current official guides.

## Modern.js Setup

- Use the latest stable Modern.js package and CLI instructions from the official documentation.
- Preserve any existing project files and do not overwrite them unless the user explicitly approves it.
- Prefer the package manager detected in the repository. If there is no existing package manager, ask or select pnpm as a reasonable default.
- Use TypeScript unless the user explicitly requests JavaScript.
- Keep framework-generated files in their documented locations.
- After scaffolding, inspect `package.json` and the generated configuration before making additional changes.

## Microfrontend Configuration

- Consult `https://modernjs.dev/guides/topic-detail/module-federation/` for the current module federation setup.
- Configure module federation from the application's actual role: host, remote, or both.
- Use unique application and exposed-module names.
- Keep remote entry and exposed API definitions in one clearly identified configuration section.
- Do not enable or expose modules unnecessarily.
- Verify the host can resolve remotes with the URLs and environment variables used by the project.

## BFF Configuration

- Consult `https://modernjs.dev/guides/advanced-features/bff/function.html#enable-bff` for BFF setup.
- Consult `https://modernjs.dev/plugin/official/cli-plugins/plugin-bff.html` for the BFF CLI plugin.
- Enable BFF only in a project mode that supports it.
- Register the official BFF plugin using the current documented syntax.
- Add a small example API route only when it helps demonstrate the setup.
- Keep server-only dependencies and environment variables out of browser code.
- Verify that the framework can build and serve both the web application and BFF routes.

## Docker Configuration

- Base the Docker image on the current Node.js LTS release.
- Prefer a multi-stage build for dependency installation, application build, and runtime.
- Build and start the application using framework-documented commands.
- Set `HOST=0.0.0.0` and expose the port used by the framework, unless the project uses a documented alternative.
- Do not copy local dependencies, build output, environment secrets, or package-manager caches unnecessarily.
- If the project includes BFF or module federation remotes, expose or configure the required ports and runtime environment variables.

The final Dockerfile must support this flow:

```bash
docker build -t <image-name> .
docker run --rm -p <host-port>:<container-port> <image-name>
```

Replace `<host-port>` and `<container-port>` with the project's configured ports.

## Validation

Before finishing:

- Confirm that `SKILL.md` frontmatter has a unique `name` matching this directory name.
- Run the package manager's install and build commands.
- Run the framework's lint, type-check, or test commands when configured.
- Start the application locally and verify that the primary route responds.
- Build and, where practical, run the Docker image.
- Report every assumption and any feature that could not be verified.