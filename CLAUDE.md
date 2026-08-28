## Markdown formatting

Always specify a language on fenced code blocks, even for plain text. Use ```text for prose, output, or anything without a more specific language. Never leave the opening fence bare.

## ASD-STE100 Simplified Technical English

Always write in ASD-STE100 Simplified Technical English, unless I tell you otherwise. Apply it to all prose for a human reader: chat replies, explanations, docs, code comments, commit message bodies, PR descriptions, and UI copy. The goal is text I can read quickly and understand on the first pass.

Core rules. Apply these every time:

- Use the active voice. Use the passive voice only when the actor is unknown.
- Use simple tenses only: infinitive, imperative, simple past, simple present, simple future, and past participle as an adjective.
- Keep an instruction to 20 words or less. Keep a description to 25 words or less.
- Write one instruction in one sentence. Use a vertical list for a sequence of three or more steps.
- Give each paragraph one topic and six sentences or less.
- Use one word for one meaning. Use the same term for the same thing every time.
- Use plain, everyday words. Do not use jargon, or formal and padded prose.
- Do not use a semicolon, a phrasal verb ("spin up", "reach out"), or a Latin abbreviation ("e.g.", "i.e.", "etc.").
- Keep a multi-word noun to three words or less.
- Use the articles "a", "an", and "the". Do not remove words to make a sentence shorter.
- Use an "-ing" form only inside a technical noun.
- In a safety instruction, put the command or the condition first. The explanation follows it.

Never remove a hedge, a condition, or a number to make a sentence shorter. "May have failed" is not "failed".

Reference files are in `~/.claude/references/asd-ste100/`. Read the applicable file when you need more than the list above:

- `writing-rules.md` — all 53 rules and the 8 general recommendations, by number.
- `applying-ste.md` — the two modes, the structural and lexical split, the three deliberate departures, and where STE does not apply.
- `examples.md` — before and after pairs.

Exceptions: code, identifiers, file paths, command output, and quoted text do not change. A style rule elsewhere in this file, or a direct instruction from me, has priority.

Source: ASD-STE100 Issue 9 (15 January 2025), free from <https://www.asd-ste100.org/>. It has 53 writing rules, a dictionary of 875 approved words, and 1274 words with approved alternatives. Issue 10 is due in January 2028. The dictionary is proprietary and is not available to you. Follow the rules, and do not claim dictionary compliance.

## Secrets

Keep every secret out of version control, and out of any file that I could publish.

- Never print a secret value in the terminal. When you inspect a config file, print the key names only.
- Never commit a `.env` file, a private key, or a token. Run `git check-ignore -v <file>` first.
- Tell me at once if a secret reaches your output, a log, or a commit. Treat that secret as compromised.

## Git safety

Ask me before any command that destroys work.

- Never force-push to a shared branch. Use `--force-with-lease`, and only on a branch that is mine.
- Do not rewrite published history unless I ask for it.
- Before `reset --hard`, `clean -fd`, `checkout -- .`, `stash drop`, or a branch delete, show me what it discards. Then ask.
- Never delete or rename a remote branch.
- Commit and push only when I ask.

## JavaScript and TypeScript

Detect the project toolchain first, then match it. Do not add a second tool for the same job.

- Read the lockfile to select the package manager: `pnpm-lock.yaml` for pnpm, `bun.lock` for bun, `yarn.lock` for yarn, `package-lock.json` for npm.
- Never create a second lockfile. Never change the package manager without my approval.
- Respect `.nvmrc` and `.node-version`. Select the version with nvm.
- Use the test runner, the linter, and the formatter that the project already has.
- Run the project typecheck script before you report a change as complete. A type error is a failure.
- Do not use `any`. Do not use a type assertion to hide a type error.
- In a test, use `@total-typescript/shoehorn` for partial data instead of `as`.

## Python

Use pyenv to manage and switch between Python versions. Select the version with `pyenv local <version>` (writes `.python-version`) or `pyenv shell <version>` for the current session, and install new versions with `pyenv install <version>`. Don't reach for system Python, brew-installed Python, or asdf. Layer venv/uv/poetry on top of the pyenv-selected interpreter.

When a Python script fails with a version-mismatch error (for example `Python 3.11+ is required`, `tomllib not found`, `SyntaxError` from new syntax, or any "requires Python X.Y" message), try pyenv first before any manual workaround:

1. Check available versions: `pyenv versions`
2. Activate one that satisfies the requirement: `pyenv shell <version>` (or `pyenv local <version>` if it should persist for the project).
3. If no installed version qualifies, install one: `pyenv install <version>`, then activate it.
4. Retry the original command.

A manual workaround (for example, executing the script's fallback instructions or porting the code) is acceptable only if pyenv itself fails — install errors, build failures, missing build deps, or the requested version genuinely being unavailable. In that case, surface the pyenv failure to the user and explain the workaround you're switching to before proceeding.

## Shell scripts

**Verify shell scripts with shellcheck when it's available.** After writing or editing a sh/bash script, run `shellcheck <script>` and fix the findings (or justify ignoring them with a targeted `# shellcheck disable=SCxxxx` comment — never blanket-disable). Check availability with `command -v shellcheck`. If it's not installed, skip silently — don't install it unprompted.

Note: shellcheck does not support zsh, so `.zshrc` and other zsh files are out of scope.

## GitHub Actions

**Pin third-party actions to a full commit SHA, not a tag.** Tags are mutable. If the action's repo is compromised, an attacker who can push a new tag pointing at a malicious commit silently re-targets every workflow that references the tag. SHAs are immutable. This is standard supply-chain hardening — Aikido, GitHub's own security guidance, and most CI security policies all flag tag-pinned third-party actions.

Convention: `uses: <owner>/<repo>@<full-40-char-sha>  # <version-tag>` — the trailing comment preserves human-readable version context for future bumps. Look up the SHA via `gh api repos/<owner>/<repo>/git/refs/tags/<tag>` (or the tags endpoint).

Scope:

- **Third-party actions** (`googleapis/*`, `aws-actions/*`, `hashicorp/*`, vendor SDKs, community actions): always SHA-pin.
- **First-party actions** (`actions/*` — GitHub's own org): tag-pinning is acceptable per GitHub's own posture. SHA-pin if the project's threat model warrants it.
- **Quasi-first-party** (`docker/*`, `azure/*`): match the project's existing convention. If unclear, SHA-pin — the marginal cost is one `gh api` lookup.

When bumping a SHA-pinned action, update both the SHA and the trailing comment in the same edit, and verify the new SHA against the tag the comment claims (`git ls-remote` or `gh api`).

## Commit messages

**In repos that use conventional-commits-driven release tooling, every commit message must follow the [Conventional Commits](https://www.conventionalcommits.org/) spec.** A wrong prefix is not cosmetic — it produces the wrong version bump (or no bump at all) when the release tool scans history, and that lands in customer-facing release notes.

Detect the tooling first. Not every repo uses it:

- `release-please-config.json` / `.release-please-manifest.json` → release-please. Default visible types: `feat`, `fix`, `perf`, `revert` (and `feat!`/`BREAKING CHANGE:` for major bumps). Other types (`docs`, `style`, `chore`, `refactor`, `test`, `build`, `ci`) parse fine but don't trigger releases or appear in the default changelog.
- `.cz.toml` / `.cz.yaml` / `cz.json` → commitizen-tools.
- `.releaserc` / `release.config.*` → semantic-release.
- `commitlint.config.*` → commitlint enforcement.

Format:

```text
<type>[optional scope][!]: <description>

[optional body]

[optional footer(s), for example BREAKING CHANGE: ...]
```

Examples:

- `feat(api): add /v2/users endpoint` — minor bump
- `fix(parser): handle null input` — patch bump
- `feat!: drop legacy /users endpoint` — major bump (or minor pre-1.0 if `bump-major-pre-major: false`)
- `chore: bump dependencies` — no bump
- `ci: pin docker/build-push-action to SHA` — no bump

Rules for me when committing in such a repo:

1. **Never invent a type** — stick to the canonical set.
2. **Match the scope of the change** — single-purpose commits. Don't mix `feat:` and `fix:` work.
3. **Use `!` or `BREAKING CHANGE:` deliberately** — a stray `!` will silently major-bump prod next release.
4. **When unsure of the type, prefer the lower-severity one** — `refactor:` over `feat:` if behaviour didn't change.

## Pull requests

**Default to small, reviewable, stacked PRs.** A PR should do one thing and be reviewable in one sitting. When a change is bigger than that, split it into a stack of PRs that build on each other — each independently testable — rather than one large PR.

- Slice vertically when it aids review, for example: docs → schema/migration → API spec → implementation.
- If a PR's diff is getting big, split it further before opening.
- When main moves, keep the whole stack updated so every PR upward carries the change.

## Coding Guidelines

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

### 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:

- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

### 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:

- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:

```text
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

### 5. Test-Driven Development by Default

**Where possible, work test-first. TDD is the default way of working, not an opt-in.**

The loop: red → green → refactor.

- Write a failing test that captures the requirement or reproduces the bug.
- Run it and watch it fail — a test that never failed proves nothing.
- Write the minimum code to make it pass.
- Refactor with the test as a safety net.

"Where possible" means TDD may be skipped only when it genuinely doesn't fit: throwaway prototypes/spikes, pure config or docs changes, or code whose behaviour can't be meaningfully asserted in a test. When skipping, say so and why — don't skip silently.
