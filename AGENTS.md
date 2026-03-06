# AGENTS.md

Guidelines for AI agents working in this repository.

## Repository Overview

This repository contains **Agent Skills** for AI agents following the [Agent Skills specification](https://agentskills.io/specification.md). Skills install to `.agents/skills/` (the cross-agent standard). This repo also serves as a **Claude Code plugin marketplace** via `.claude-plugin/marketplace.json`.

- **Name**: Marketing Skills
- **GitHub**: [andginja/marketingskills](https://github.com/andginja/marketingskills)
- **Creator**: Andre Ginja
- **License**: MIT

## Repository Structure

```
marketingskills/
├── .claude-plugin/
│   └── marketplace.json   # Claude Code plugin marketplace manifest
├── skills/                # Agent Skills (33 skills)
│   └── skill-name/
│       └── SKILL.md       # Required skill file
├── AGENTS.md              # This file
├── CLAUDE.md              # Claude Code instructions
├── LICENSE                # MIT
└── README.md              # Documentation
```

## Agent Skills Specification

Skills follow the [Agent Skills spec](https://agentskills.io/specification.md).

### Required Frontmatter

```yaml
---
name: skill-name
description: What this skill does and when to use it. Include trigger phrases.
metadata:
  author: Andre Ginja
  version: 1.0.0
---
```

### Frontmatter Field Constraints

| Field | Required | Constraints |
|-------|----------|-------------|
| `name` | Yes | 1-64 chars, lowercase `a-z`, numbers, hyphens. Must match directory name. |
| `description` | Yes | 1-1024 chars. Describe what it does and when to use it. |
| `metadata` | No | Key-value pairs (author, version, etc.) |

### Name Field Rules

- Lowercase letters, numbers, and hyphens only
- Cannot start or end with hyphen
- No consecutive hyphens (`--`)
- Must match parent directory name exactly

## Writing Style Guidelines

### Structure
- Keep `SKILL.md` under 500 lines
- Use H2 (`##`) for main sections, H3 (`###`) for subsections
- Use bullet points and numbered lists
- Short paragraphs (2-4 sentences max)

### Tone
- Direct and instructional
- Second person ("You are a conversion rate optimization expert")
- Professional but approachable

### Formatting
- Bold (`**text**`) for key terms
- Code blocks for examples and templates
- Tables for reference data

### Description Field Best Practices

Include:
1. What the skill does
2. When to use it (trigger phrases)
3. Related skills for scope boundaries

## Claude Code Plugin

Install via:

```bash
/plugin marketplace add andginja/marketingskills
```

Or install individual skills:

```bash
npx skills add andginja/marketingskills
```

## Skill Categories

### SEO & Visibility
seo-geo, seo-audit, ai-seo, schema-markup, programmatic-seo, site-architecture, analytics-tracking

### Conversion & Growth
page-cro, signup-flow-cro, form-cro, popup-cro, onboarding-cro, paywall-upgrade-cro, ab-test-setup

### Copy & Content
copywriting, copy-editing, cold-email, email-sequence, content-strategy, social-content

### Strategy & Growth
launch-strategy, pricing-strategy, marketing-ideas, marketing-psychology, competitor-alternatives, free-tool-strategy, referral-program

### Ads & Sales
paid-ads, ad-creative, churn-prevention, revops, sales-enablement, product-marketing-context

## Git Workflow

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

- `feat: add skill-name skill`
- `fix: improve clarity in page-cro`
- `docs: update README`
