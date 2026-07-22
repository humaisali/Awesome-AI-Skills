# Contributing to the Ultimate AI Agent Skills Collection

First off, thank you for considering contributing to this repository! It's people like you that make this collection an incredibly powerful resource for the AI community.

We welcome contributions from everyone, whether you're adding a brand new skill, fixing a typo, or improving our documentation.

## How Can I Contribute?

### 1. Add a New Skill

Do you have a specialized prompt or instruction set that makes your AI Agent perform better? Share it!

1.  **Fork the repository** to your own GitHub account.
2.  **Find the right category:** Navigate into the relevant category directory and find the appropriate sub-category for your skill (e.g., `Development & Engineering Skills / Web Development`).
3.  **Create a folder:** Name it descriptively (e.g., `nextjs-app-router-expert`).
4.  **Create a `SKILL.md` file:** Inside your folder, create a `SKILL.md` file. This is the core instruction file.
5.  **Use the standard format:** Your `SKILL.md` must include YAML frontmatter. See the template below.

#### `SKILL.md` Template

```markdown
---
name: "Skill Name"
description: "A short description of what this skill does."
author: "Your Name"
source: "https://github.com/yourusername"
---

# Instructions

[Place the instructions, rules, or system prompt for the AI Agent here.]

# Examples (Optional)

[Provide examples of how the AI should behave.]
```

### 2. Report a Bug or Request a Skill

If you found a skill that contains broken links, bad instructions, or produces poor results, please let us know!
Similarly, if you wish there was a skill for a specific framework but can't find one, request it.

- Navigate to the **Issues** tab.
- Click **New Issue**.
- Select either **Bug Report** or **Skill Request** and fill out the provided template.

## Pull Request Process

1.  Create a new branch in your fork (`git checkout -b feature/new-awesome-skill`).
2.  Commit your changes (`git commit -m 'Add awesome new skill'`).
3.  Push to the branch (`git push origin feature/new-awesome-skill`).
4.  Open a Pull Request against the `main` branch of this repository.
5.  Ensure your PR description clearly explains what you've added or fixed.

## Code of Conduct

Please note that this project is released with a Contributor Code of Conduct. By participating in this project you agree to abide by its terms. Be respectful and constructive in your feedback and code reviews.

Thank you for contributing! 🚀
