# Professor Skill

Turn the professors you learned best from into a personal AI tutor.

Professor Skill is a [Claude skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that interviews you about how your favorite professors teach, combines their strengths, and generates a new skill that teaches you the same way.

## Why

Every professor has a style. One builds each idea from intuition. Another writes out every step of a derivation so you never get lost. Most AI tutors teach in one generic voice. This project lets you keep what worked for you, drop what didn't, and study with a tutor shaped by the teachers you actually learned from.

## How it works

1. **Interview.** Describe one or more professors: how they introduce new topics, explain ideas, work through derivations, check understanding, run practice, and respond to mistakes. You can answer questions or paste one long description.
2. **Confirm.** Review a profile organized by teaching stage. When you describe several professors, each stage uses the strength you chose. You'll see which parts fell back to sensible defaults, so you can fill them in.
3. **Generate.** Get a ready-to-use `SKILL.md` for your personal professor.
4. **Learn.** Load the new skill and study with it. Tell the generator what doesn't feel right and it updates only that part.

## Features

- **Combine several professors.** Keep each professor's strengths and assign them to the stage where they work best, for example one for explaining concepts and another for derivations.
- **A complete teaching flow.** Every generated professor diagnoses what you already know, motivates new ideas, checks understanding at the right moments, guides you through practice, and wraps up with a summary.
- **Hints before answers.** Ask for the answer and you get a hint, then one step at a time. You choose the phrase, or the number of requests, that unlocks the full solution.
- **Any subject, any language.** The professor replies in the language you write in.
- **Shareable by design.** Generated skills describe teaching style only: no names, courses, schools, or lecture content.

## Repository structure

```
professor-skill/
├── professor/                    # The generator skill
│   ├── SKILL.md                  # Interview, profile, and generation workflow
│   └── templates/
│       └── professor-template.md # Skeleton for every generated skill
├── examples/
│   └── professor-demo/SKILL.md   # A hand-written example professor
├── README.md
└── LICENSE
```

## Installation

**Claude apps (web, desktop, mobile)**
1. Download or clone this repository.
2. Zip the `professor` folder, keeping `templates/` inside it.
3. Upload the zip as a skill in Claude's settings.

**Claude Code**
```bash
git clone https://github.com/WoChiNingMeng12138/professor-skill.git
cp -r professor-skill/professor ~/.claude/skills/
```

**Other AI tools**
Tools that support the Agent Skills format can load the folder directly. For other tools, paste the contents of a generated `SKILL.md` into the system prompt or custom instructions.

## Usage

Start a new conversation and say something like:

> Create a professor skill for me.

> I want Claude to teach like my statistics professor.

Answer the interview questions, confirm the profile, and you'll receive your skill as `professor-<name>/SKILL.md`. Install it the same way as above, then start learning:

> Teach me eigenvectors.

> Can you walk me through this problem?

Want to try a finished professor first? Install `examples/professor-demo` and ask it to teach you something.

## Privacy and content

- Generated skills record **teaching style only**. Names and identifying details you mention during the interview are never written into the file.
- If you paste lecture notes or slides, they are used only to understand how your professor teaches. Course material is not copied into the skill. Please respect your professors' and institutions' rights when sharing generated skills.

## Contributing

Issues and pull requests are welcome, especially:
- Generated skills that behaved unexpectedly (please remove any personal details first)
- Better interview questions or template defaults
- Example professors for other subjects

## License

See [LICENSE](LICENSE).