# bring-shopping-list

A Claude Code skill for managing [Bring!](https://www.getbring.com/) shopping lists. Add, remove, complete, and view items on your Bring! shopping list through natural language.

## Installation

Copy this folder into your Claude Code skills directory:

```bash
# personal (available in all projects)
cp -r bring-shopping-list ~/.claude/skills/

# or project-specific
cp -r bring-shopping-list your-project/.claude/skills/
```

### Requirements

- [uv](https://docs.astral.sh/uv/) (Python package runner)
- A Bring! account with email/password login

> **Google login users:** Go to your Bring! account settings and set a separate password for API access.

### Environment Variables

Set these in your shell or in a `.env` file:

```bash
BRING_EMAIL=your-email@example.com
BRING_PASSWORD=your-password
```

## Usage

Once installed, Claude will automatically use this skill when you ask about shopping or groceries:

- "Add milk and eggs to the shopping list"
- "What's on my list?"
- "Remove butter from the list"

### CLI

You can also use the script directly:

```bash
uv run --with bring-api --with python-dotenv python bring.py list
uv run --with bring-api --with python-dotenv python bring.py add "Milk" "Eggs" "Butter:unsalted"
uv run --with bring-api --with python-dotenv python bring.py remove "Milk"
uv run --with bring-api --with python-dotenv python bring.py complete "Eggs"
```

Items support optional specifications via colon syntax: `"Milk:low fat"`, `"Butter:Irish"`.

## How It Works

The skill uses the unofficial [bring-api](https://github.com/miaucl/bring-api) Python package to interact with Bring's API. It authenticates with your credentials, finds your default shopping list, and performs operations on it.

## License

MIT
