# `🧬 Manbot` Skills Repository

## Table of Contents
- [What is Manbot?](#user-content--what-is-manbot)
- [Repository Structure](#user-content--repository-structure)
- [How to Use & Create Skills](#user-content--how-to-use--create-skills)
- [Skill Anatomy](#user-content--skill-anatomy)
- [Security & Best Practices](#user-content--security--best-practices)
- [Adding a New Skill](#user-content--adding-a-new-skill)
- [License](#user-content--license)
- [Contribution Guidelines](#user-content--contribution-guidelines)
- [Documentation](#user-content--documentation)

The `🧬 Manbot Skills` repository is a central hub for managing, sharing, and extending a collection of AI‑agent skills. Each skill lives in its own underscored folder (e.g., `_skill_name/`) with a `SKILL.md` that contains Markdown‑formatted instructions and front‑matter. These Markdown files are queried by the Manbot tooling system so the agent can discover, load, and execute skills automatically.

## 🧬 What is Manbot?

[Manbot](https://manbothq.github.io) is a **multi-process AI platform** featuring type-safe IPC and capability-graph execution. Unlike traditional chatbots, Manbot is architected for heavy-duty tasks that require time and significant processing power—such as multi-step planning, deep research, and autonomous tool use.

## Repository Structure

```
📁 .
├── _skill_name
│   └── SKILL.md
├── _skill_name
│   └── SKILL.md
├── _skill_name
│   └── SKILL.md
├── _skill_name
│   └── SKILL.md
└── README.md
```

> **Note:** The structure above is just an example.

## 🛠 How to Use & Create Skills

Skills in this repository follow the **AgentSkills** specification, making them compatible with `manbot` tooling system.

### Skill Anatomy
Each skill is defined by a `SKILL.md` file located inside an underscored directory (e.g., `my-skill/SKILL.md`). The file consists of markdown instructions.

```markdown
> Description: Brief skill description

# Instructions
Detailed guidance for the AI agent on how to use the tools or logic provided in this skill.
```

---

## 🛡 Security & Best Practices

When adding or developing new skills, follow these guidelines to ensure the safety and reliability of your Manbot instance:

- **Verification:** Always treat third-party skills as untrusted code. Review the `SKILL.md` content and any associated scripts before adding them to your repository.
- **Principle of Least Privilege:** If a skill requires external binaries, Ensure they are scoped to only the necessary directories and permissions.
- **RAG Optimization:** Use clear, semantic headings in the markdown body. This helps the system accurately chunk and retrieve relevant information during task execution.
- **Local-First:** Prefer tools and scripts that run locally to maintain the privacy and performance goals of Manbot.

---

## 🚀 Adding a New Skill

You can add a new skill directly from Telegram with the following command:

```text
/add_skill <URL_TO_SKILL_MD>
```

The tool will automatically:
1. Download the Markdown file.
2. Create a folder prefixed with an underscore (`_`) based on the skill name.
3. Place the `SKILL.md` inside that folder, making it immediately available to the Manbot agent.

## 📄 License

This repository is distributed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 🤝 Contribution Guidelines

- Fork the repository and create a new branch for your skill.
- Follow the **Skill Anatomy** section when writing a new skill.
- Commit and push the new skill folder and its `SKILL.md`.
- Submit a pull request for review.
- Ensure your changes are documented in the README.

## 📚 Documentation

Additional documentation can be found in the `docs/` folder of this repository. Feel free to add new markdown files or update existing ones.
