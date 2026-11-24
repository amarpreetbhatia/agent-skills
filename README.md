# Agent Skills

[![skills.sh](https://skills.sh/b/amarpreetbhatia/agent-skills)](https://skills.sh/amarpreetbhatia/agent-skills)

A personal collection of reusable AI agent skills designed to reduce repetitive work and provide consistent workflows across projects.

## About

These skills give coding agents structured, repeatable instructions for common development tasks. They include setup guidance, recommended conventions, validation steps, and project-specific workflows.

## Available Skills

| Skill | Description |
| --- | --- |
| [Web App Builder](./skills/web-app-builder/SKILL.md) | Scaffold and configure production-ready Modern.js applications with microfrontend, BFF, Docker, and deployment support. |

### Web App Builder

Use `web-app-builder` when you want to:

- Create a new Modern.js web application
- Configure microfrontend module federation
- Enable and structure BFF APIs
- Add a production-oriented Docker setup
- Follow the official Modern.js setup and validation workflow

The skill uses current official documentation, preserves existing project files, and validates the generated project with the appropriate package manager and framework commands.

## Installation

You can install all skills from this repository using the [skills CLI](https://skills.sh):

```bash
npx skills add https://github.com/amarpreetbhatia/agent-skills.git
```

To install only the Web App Builder skill:

```bash
npx skills add https://github.com/amarpreetbhatia/agent-skills.git --skill web-app-builder
```

The CLI may ask which coding agent or project location should receive the skill. Choose the options that match your setup.

## Prerequisites

- Node.js and npm
- `npx` (included with modern npm installations)
- Network access for installing skills and dependency packages

The Web App Builder skill may also require a supported package manager such as pnpm, npm, or Yarn, and Docker when container support is being used.

## Usage

After installation, ask your coding agent to perform a task covered by one of the available skills. For example:

```text
Use the web-app-builder skill to create a TypeScript Modern.js application.
Configure it as a microfrontend host and include BFF support.
```

The agent will apply the skill's workflow to the current project.

## Repository Structure

```text
agent-skills/
├── skills/
│   └── web-app-builder/
│       └── SKILL.md
└── skills-lock.json
```

- `skills/` contains the reusable skill definitions.
- `SKILL.md` describes a skill's purpose and workflow.
- `skills-lock.json` records installed skill metadata.

## Adding a New Skill

Create a new directory under `skills/` and add a `SKILL.md` file. The file should include:

- A unique skill name
- A clear description
- Prerequisites and compatibility requirements
- A repeatable workflow
- Validation steps

Then commit and push the skill so it can be installed directly from this repository.

## Repository

Source: [github.com/amarpreetbhatia/agent-skills](https://github.com/amarpreetbhatia/agent-skills)
