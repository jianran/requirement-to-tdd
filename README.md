# requirement-to-tdd

A Claude Code skill repository for requirement-related development guidance.

This project is modeled after the `forrestchang/andrej-karpathy-skills` repository and provides a lightweight skill file for requirement module, class, and test-first feature work.

## Contents

- `CLAUDE.md` — top-level skill metadata and usage guidance
- `skills/requirement-skill/SKILL.md` — requirement-specific instructions for Claude agents
- `EXAMPLES.md` — example workflow and test-first planning

## Purpose

Use this repository when you need to implement or extend requirement-related code without creating a Python library. The skill emphasizes finding existing domain classes, deciding whether a new class is needed, and writing unit tests first.

A small Python package that demonstrates a Claude-style requirement parser and repository skill.

## What this skill does

- Parses structured requirement text into a `Requirement` object
- Validates titles, priorities, statuses, and tags
- Stores requirements in a repository and prevents duplicate titles
- Provides a `ClaudeSkill` adapter for ingesting requirement text and listing parsed requirements

## Install

Create a virtual environment and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -e .
python -m pip install pytest
```

## Usage

Import and use the skill classes from `claude_skill`:

```python
from claude_skill.skill import ClaudeSkill

skill = ClaudeSkill()
requirement_text = """
Title: Checkout flow
Description: Add checkout flow for shopping cart.
Priority: Medium
Status: New
Tags: ecommerce, checkout
"""

requirement = skill.ingest_requirement_text(requirement_text)
print(requirement.summary())
print(skill.list_requirements())
```

## Running tests

Run the unit tests with:

```bash
python -m pytest
```

## Project layout

- `claude_skill/requirements.py` — requirement model and repository
- `claude_skill/skill.py` — parser and Claude skill interface
- `tests/test_requirements.py` — unit tests for parsing and repository behavior
- `pyproject.toml` — package metadata and test configuration
