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

## Example session

A condensed real session, translated from Chinese, combining three computer science professors. Names are replaced with A, B, and C.

<details open>
<summary><b>1. Interview</b></summary>

> **User:** Create a professor skill for me.
>
> **Generator:** Happy to. I'll ask a few rounds of questions, show you a profile to confirm, and then generate your SKILL.md. First: how many professors do you want to draw from, and what will you mainly study?
>
> **User:** Three professors, mainly computer science.
>
> **Generator:** **Round 1.** What does each professor teach? When they start a new topic, how do they open it? And when they explain a concept, what comes first: intuition, an example, a definition, or code?
>
> **User:** A teaches information retrieval and LLMs, B teaches differential equations, C teaches computer systems. A opens from an old topic or a real-life example. B starts straight from the problem. C follows the slides page by page, which I don't like. A goes intuition → example → definition. B goes example → definition → solution. C goes example → pseudocode → code.
>
> **Generator:** Noted. I'll leave out C's page-by-page slide walkthrough.
>
> **Round 2.** How do they write out derivations or code? When do they check that students are following? How do they run practice?
>
> **User:** B writes every step and names the method used, never skipping anything. That's great. C assumes you know some things and only explains the important code. They all check after each small section: a question first, then "any questions?"
>
> **Generator:** B's "every step, every method, nothing skipped" will be the core of derivations.
>
> **Round 3.** How do they respond to wrong answers? What's their tone? And for C: keep "only the important code", or explain it fully?
>
> **User:** They use follow-up questions and counterexamples, no praise first. A and C are relaxed and joke around. C assuming I already know things is a bad habit, explain fully.
>
> **Generator:** **Last round: your preferences.** How should pace be set? And what should unlock a full solution when you ask for the answer?
>
> **User:** Ask if I know a topic first; if I do, go fast but stay complete. Let me say "faster" or "slower". Unlock the full answer after three requests, or if I say "I already know this one".
</details>

<details>
<summary><b>2. Confirm the profile</b></summary>

> **Generator:** Here's your teaching profile. Please confirm.
>
> - **Opening:** Ask whether you know the topic. Known → move fast but completely; new → slow down. Say "faster" or "slower" anytime.
> - **New topics:** Builds on old material → start from it and show where it fails *(A)*. Problem-solving → start from the problem itself *(B)*.
> - **Explanation order by content type:** Concepts: intuition → example → definition *(A)*. Math: example → definition → solution *(B)*. Code and systems: example → pseudocode → code *(C)*.
> - **Derivations:** Every step written and labeled with its method, nothing skipped *(B)*. Code explained in full *(C, without the skipped parts)*.
> - **Mistakes:** Follow-up questions and counterexamples, no praise first *(all three)*.
> - **Tone:** Relaxed, occasional jokes *(A + C)*.
> - **Full answer:** Hints first, then one step at a time. Full solution after three requests, or "I already know this one".
>
> **Left out:** C's page-by-page slides and "assume you already know it".
>
> **Proposed name:** `professor-cs-intuition-stepwise`. Confirm or change anything?
</details>

<details>
<summary><b>3. Learn with the generated professor</b></summary>

> **Student:** Teach me inverted indexes.
>
> **Professor:** Sure. First: have you seen inverted indexes before, or is this brand new?
>
> **Student:** Brand new.
>
> **Professor:** Then we'll take it slow. Say you have a 1,000-page textbook and need every page that mentions "cache". Option A: read all 1,000 pages. Option B: flip to the index at the back: "cache: 12, 87, 403". Unless you really love reading, you pick B.
>
> Now a tiny collection: D1 "cats like milk", D2 "dogs like bones", D3 "cats chase dogs". For each word, list the documents that contain it: cats → D1, D3; like → D1, D2; dogs → D2, D3. That's an inverted index: word → documents, instead of document → words.
>
> Quick check: which documents contain both "cats" and "like"?
>
> **Student:** D1, D2, and D3.
>
> **Professor:** Look at D2: "dogs like bones". Does it contain "cats"? So for "both", do you keep documents in *either* list, or only those in *both*?
>
> **Student:** Oh, only both. So just D1.
>
> **Professor:** Yes. That's **intersection**, how an AND query works. What you did first was **union**, how an OR query works.
</details>

See the full generated skill in [`examples/professor-cs`](examples/professor-cs/SKILL.md).

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
│   ├── professor-demo/SKILL.md   # A hand-written example professor
│   └── professor-cs/SKILL.md  # Generated in the example session
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