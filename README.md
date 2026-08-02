# AI Agent Skills

A public collection of reusable skills for AI agents.

These are workflows and instruction sets I developed while using AI agents on real projects. Some started as very project-specific tools and were later cleaned up and generalized so they can be useful elsewhere.

The repository is intentionally focused on **agent skills**, rather than prompts, code snippets, art, or general project material.

## What is a skill?

A skill is a set of instructions that gives an AI agent a more structured way to handle a recurring task.

Instead of repeatedly explaining the same rules in a conversation, a skill can define:

- what the agent should check
- which sources should be treated as authoritative
- what workflow to follow
- when to ask before making changes
- what should be recorded for later review
- what kinds of mistakes or contradictions to look for

The exact format may vary between tools and agents, but the underlying idea is the same: make useful project knowledge and working habits explicit.

## Skills in this repository

### Validate Project Canon

A consistency checker for narrative games and other story-heavy projects.

It can help an agent check:

- character and location names
- terminology
- dialogue state
- objectives and quest progression
- flags and side effects
- contradictions between implementation and design documents
- stale references left behind after a design change

The skill does not assume a particular repository structure. On first use, it asks where the project's glossary, story bible, design guidelines, implementation files, and contradiction log are kept.

It is designed to flag uncertainty rather than silently invent a resolution.

More skills will be added as I find workflows that are useful enough to generalize and share.

## Why I use skills

AI agents are very good at reading large amounts of project material, finding patterns, and checking mechanical consistency. They are much less reliable when they have to guess which source is correct, infer unwritten canon, or make creative decisions that were never clearly specified.

Skills help narrow that gap.

A useful skill gives the agent enough structure to do the repetitive checking while keeping important decisions with the developer.

## Using these skills

Each skill should be readable on its own.

Before using one:

1. Read it and make sure its assumptions fit your project.
2. Adjust source locations, terminology, or authority rules where needed.
3. Keep important project decisions in explicit documents rather than relying on conversation history.
4. Review changes made by an agent before committing them.

These are working tools, not guarantees. They can reduce inconsistency and missed dependencies, but they still depend on the quality of the project documentation they are given.

## Contributing

If you adapt one of these skills or find a useful improvement, feel free to open an issue or pull request.

I am particularly interested in changes that make a skill more general without making it vague.

## Repository structure

A typical skill is stored as a Markdown file containing metadata followed by the agent instructions.

For example:

```text
skills/
  validate-project-canon/
    SKILL.md
```

Individual skills may include additional examples or supporting files when needed.
