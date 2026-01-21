# PRD Generator

A collection of templates and best practices for writing Product Requirements Documents (PRDs).

## Repository Structure

```
.
├── prd/                    # PRD templates and guidelines
│   ├── prd_template.md     # Comprehensive PRD template (English)
│   ├── prd_template_zh.md  # PRD template (Chinese)
│   └── what-is-excellent-prd.md  # Guidelines for writing excellent PRDs
├── ux/                     # UX design resources
│   └── stitch_template.md  # Stitch prompting guide for UI/UX design
└── pet-soul/               # Example project PRDs
    ├── idea.md
    ├── prd.md
    ├── prd-zh.md
    ├── ux-v1.md
    └── ux-v2.md
```

## PRD Structure

PRDs follow a "Zoom In" structure:

1. **Context & Strategy (The "Why")** - Problem statement, goals, success metrics
2. **The Audience (The "Who")** - Target personas and user stories
3. **The Solution (The "What")** - Functional requirements, UX/design, technical requirements
4. **Release & Logistics (The "How")** - Scope, phasing, dependencies

## Prioritization System

Requirements use the P-system:

| Priority | Meaning |
|----------|---------|
| **P0** | Critical / Must Have |
| **P1** | Important / Should Have |
| **P2** | Nice to Have |

## Getting Started

1. Copy `prd/prd_template.md` as your starting point
2. Review `prd/what-is-excellent-prd.md` for best practices
3. Fill in the sections relevant to your project
4. Delete sections you don't need

## Key Principles

- **Be concise and scannable** - Avoid walls of text
- **Prioritize ruthlessly** - Tag every requirement with P0/P1/P2
- **Show, don't tell** - Include wireframes and diagrams
- **Keep it alive** - Update the document as requirements evolve
- **Define "Done"** - Include clear acceptance criteria
