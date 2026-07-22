# Comprehensive User Guide: How to Master AI Agent Skills

Welcome to the ultimate guide on how to integrate and use the massive collection of skills from this repository! 

While these skills can be adapted for almost any Large Language Model (like ChatGPT, Gemini, or GitHub Copilot), they are fundamentally designed as **Modular Agent Skills** to be natively consumed by agentic frameworks like **Claude** (Code/Desktop) and the **Antigravity IDE**.

---

## Table of Contents
1. [Understanding the Anatomy of a Skill](#1-understanding-the-anatomy-of-a-skill)
2. [How to Use Skills in Antigravity IDE](#2-how-to-use-skills-in-antigravity-ide)
3. [How to Use Skills in Claude Code (CLI)](#3-how-to-use-skills-in-claude-code-cli)
4. [How to Use Skills in Claude Desktop & Projects](#4-how-to-use-skills-in-claude-desktop--projects)
5. [How to Use Skills in Cursor & Windsurf](#5-how-to-use-skills-in-cursor--windsurf)
6. [Best Practices for Combining Skills](#6-best-practices-for-combining-skills)

---

## 1. Understanding the Anatomy of a Skill

Instead of giving your AI a messy, 5-page prompt every time you start a new chat, an **Agent Skill** encapsulates all that knowledge into a single, structured folder.

Every skill in this repository follows a standard format:

```text
react-best-practices/
├── SKILL.md            <-- The core brain of the skill
└── examples/           <-- (Optional) Example code the AI can read
    └── example_component.jsx
```

### Inside the `SKILL.md`

If you open any `SKILL.md`, you will see two main sections:
- **YAML Frontmatter:** This is metadata at the very top (between `---`). It contains the `name` and `description`. Advanced AI agents read this frontmatter at startup so they know *when* to automatically trigger the skill.
- **Markdown Body:** Contains the actual instructions, rules, constraints, and best practices the AI must follow.

---

## 2. How to Use Skills in Antigravity IDE

Antigravity IDE (built by Google DeepMind) natively understands the concept of modular Skills. It is incredibly easy to give your Antigravity agent superpowers.

### Installation

1.  **Locate the Skill:** Find the skill you want in the relevant category directory of this repository (e.g., `Development & Engineering Skills/Web Development/react-best-practices`).
2.  **Copy the Directory:** Copy the entire folder (e.g., the folder named `react-best-practices`).
3.  **Paste into Antigravity Customization Root:**
    *   **Global Scope:** If you want the skill available across all your projects forever, paste the folder into your global config directory: 
        `C:\Users\YourUsername\.gemini\config\skills\`
    *   **Workspace Scope:** If you only want the skill available in your current specific project, paste it into the local agents folder: 
        `.agents\skills\` (relative to your project's workspace root).
4.  **Restart or Reload:** The Antigravity agent automatically discovers and registers these skills on startup!

### Invocation

You do not need to explicitly tell the agent "Use the react-best-practices skill." 
Antigravity constantly reads the descriptions of installed skills. If you ask the agent: *"Build a React component for a login form,"* the agent will automatically realize it has a `react-best-practices` skill, pull those rules into its context, and write the code flawlessly according to your skill!

---

## 3. How to Use Skills in Claude Code (CLI)

Anthropic's `claude-code` CLI is designed for terminal-based agentic workflows and loves reading markdown files.

### Execution

1. Open your terminal in your project directory.
2. You can directly feed a `SKILL.md` into Claude by piping it or referencing it in your command:
   ```bash
   claude -p "Review my src/ folder and refactor it applying the rules from this skill" < path/to/awesome-ai-skills/Development & Engineering Skills/.../SKILL.md
   ```
3. **Interactive Mode:** If you are already running an interactive `claude` session, you can simply point the agent to the skill dynamically:
   > *"Claude, please read the file at `../awesome-ai-skills/Security & DevOps Skills/Cyber Security/sql-injection-testing/SKILL.md`. I want you to adopt that persona and scan my `app.js` file for vulnerabilities."*

---

## 4. How to Use Skills in Claude Desktop & Projects

If you are using the web version of Claude (Claude.ai) or the Desktop app, you can utilize the "Projects" feature to permanently embed skills.

1. **Create a Project:** In Claude, create a new Project (e.g., "My Next.js Startup").
2. **Upload the Knowledge:** Go into your local `awesome-ai-skills` repository, find the specific `SKILL.md` files that are relevant to your startup (e.g., the Next.js skill, the Tailwind CSS skill, and the copywriting skill). Upload these `.md` files directly into the **Project Knowledge** section.
3. **Set Custom Instructions:** In the "Custom Instructions" box for the project, write:
   > *"You are an expert developer. Before answering any questions or writing code, you must strictly follow the rules, guidelines, and constraints defined in the uploaded SKILL.md documents in your knowledge base."*
4. **Chat:** Every chat within this project will now natively adhere to your highly specialized skills!

---

## 5. How to Use Skills in Cursor & Windsurf

Other popular AI IDEs like **Cursor** and **Windsurf** use rules files (like `.cursorrules` or `.windsurfrules`). 

While they don't dynamically load folders like Antigravity, you can easily adapt our skills:
1. Open the `SKILL.md` you want to use.
2. Copy the text inside the Markdown Body (skip the YAML frontmatter).
3. Paste that text directly into your project's `.cursorrules` file or `.windsurfrules` file.
4. Your IDE's Copilot will now obey those highly specific instructions!

---

## 6. Best Practices for Combining Skills

- **Don't Overload:** Don't install or attach 50 skills at the same time. This will eat up the AI's context window and confuse it. Only attach the skills relevant to your *current* tech stack.
- **Layering:** It is highly effective to combine one overarching architecture skill (e.g., `clean-architecture`) with a specific syntax skill (e.g., `python-fastapi-pro`). 
- **Read the SKILL.md First:** Before trusting an AI to use a skill blindly, open the `SKILL.md` and read it yourself. Ensure the rules inside match your team's coding standards! If they don't, edit the file locally!
