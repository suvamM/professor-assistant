# professor-assistant

A super helpful professor assistant for professors (mainly assistant professors :D )

## Overview

This repository hosts the **professor-assistant-marketplace** — a Copilot CLI plugin marketplace designed to reduce the workload of professors, primarily assistant professors, through intelligent AI-powered automation.

### What's Inside

- **Marketplace**: `professor-assistant-marketplace` — a registry of plugins for academia
- **Plugin**: `professor-assistant-plugin` — bundles the agent and skills below
- **Agent**: `professor-assistant` — a warm, knowledgeable academic companion
- **Skill**: `welcome-researcher` — greets a user, searches for their academic profile, and provides a personalized summary of their work

## Installation

### GitHub Copilot CLI
Follow the instructions outlined [here](https://docs.github.com/en/copilot/how-tos/copilot-cli/set-up-copilot-cli/install-copilot-cli).

### Add the Marketplace

```bash
copilot plugin marketplace add suvamm/professor-assistant
```

### Install the Plugin

```bash
copilot plugin install professor-assistant-plugin@professor-assistant-marketplace
```

### Verify Installation

```bash
copilot plugin list
```

Inside a Copilot CLI session, verify the agent and skill loaded:

```
/agent
/skills list
```

## Usage

Start a Copilot CLI session and invoke the agent:

```
Use the professor-assistant agent to welcome me
```

Or invoke the skill directly:

```
Use the /welcome-researcher skill
```

The agent will:

1. Ask for your **name** and **institutional affiliation**
2. Search the internet for your academic profile and publications
3. Provide a **friendly, personalized welcome** with a summary of your research

## Repository Structure

```
professor-assistant/
├── .github/
│   └── plugin/
│       └── marketplace.json                         # Marketplace registry
├── plugins/
│   └── professor-assistant-plugin/
│       ├── plugin.json                              # Plugin manifest
│       ├── agents/
│       │   └── professor-assistant.agent.md         # Agent definition
│       └── skills/
│           └── welcome-researcher/
│               └── SKILL.md                         # Welcome & summarize skill
├── README.md
└── LICENSE
```

## Roadmap

The professor-assistant agent will progressively gain new skills, including:

- 📚 Course material preparation
- 📝 Research paper review assistance
- 🎓 Student query management
- 💰 Grant writing support
- 📋 Administrative task automation

## License

[MIT](LICENSE)
