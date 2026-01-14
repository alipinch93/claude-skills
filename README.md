# Claude Skills

This repository contains all my Claude Skills.

## Skills

### Skill Creator
- **Location**: `skill-creator/`
- **Description**: Create and structure Claude Skills. Use when the user wants to create a new skill, needs help with skill structure, wants to format SKILL.md files, or needs guidance on skill development best practices.
- **Keywords**: skill creation, skill structure, SKILL.md, skill development, Claude skills

### RunGopher Slide Deck Creator
- **Location**: `rungopher-slide-deck/`
- **Description**: Create RunGopher branded slide decks from data or text. Generates HTML slides that convert to PowerPoint PPTX format following RunGopher's brand guidelines.
- **Keywords**: slide deck, presentation, slides, PowerPoint, PPTX, RunGopher branded, pitch deck, branded slides

## Installation

Each skill in this repository can be installed as a Claude Skill by copying the skill folder to your Claude Skills directory:

### Personal Skills (Available across all projects)
```bash
cp -r [skill-name] ~/.claude/skills/
```

### Project Skills (Available in specific project)
```bash
cp -r [skill-name] .claude/skills/
```

## Repository Structure

```
.
├── README.md
├── skill-creator/
│   └── SKILL.md
├── rungopher-slide-deck/
│   └── SKILL.md
└── [future-skill]/
    └── SKILL.md
```
