# Contributing

Thanks for helping improve Professor Skill! Contributions of all sizes are welcome.

## Ways to contribute

- **Report a problem.** Open an issue when a generated skill behaves unexpectedly, the interview asks something confusing, or installation fails. Include the prompt you used, what happened, and what you expected.
- **Improve the generator or template.** Better interview questions, clearer defaults, or fixes to `professor/SKILL.md` and `professor/templates/professor-template.md`.
- **Share an example professor.** A generated skill for a subject not yet covered in `examples/`.

## Privacy first

Generated skills must describe **teaching style only**. Before you submit an example, an issue, or a transcript, remove:

- Professors' names, course numbers, schools, and anything else that identifies a real person
- Your own personal details
- Copied lecture notes, slides, or other course material

Pull requests that include identifying details will be asked to remove them before merging.

## Adding an example professor

1. Create a folder `examples/professor-<slug>/` containing one `SKILL.md`.
2. Make sure `name` in the frontmatter matches the folder name.
3. Check that no `{{` placeholder or `<!--` comment is left over from the template.
4. Test it: run through at least one new topic, one direct problem, one wrong answer, and one request for the answer.
5. In your pull request, name the subject and describe the style in one or two sentences.

## Changing the generator or template

- **One change per pull request.** It keeps the effect of each change easy to see.
- **Write rules as behaviors, not adjectives.** "When the student answers wrong, ask about the step where it went wrong" works better than "be patient".
- **Test before submitting.** Generate a skill with your change and confirm it still behaves as intended. Describe what you tested in the pull request.
- **Keep FIXED sections consistent.** If you change a FIXED section of the template, check that nothing elsewhere refers to the old wording.
- If you change files under `professor/`, bump `version` in `.claude-plugin/plugin.json` so plugin users receive the update.

## Commit messages

Say what changed and why, for example:

```
Add check-in rule for difficult points

Students got lost on hard steps before the end-of-unit check.
```

## License

By contributing, you agree that your contributions are licensed under the MIT License.