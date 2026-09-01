# claude-engineering-rules

A `CLAUDE.md` for Claude Code, and the writing standard it applies.

Every rule in this file names three things: the tool, the check that proves the
rule held, and the escape hatch. Detect the lockfile, then match it. Detect the
release tool, then pick the commit type. Check `command -v shellcheck`, and skip
silently if it is absent. A rule that an agent cannot verify is a rule the agent
will drift away from.

## What is in it

| Path | What it holds |
| --- | --- |
| `CLAUDE.md` | 11 rule sections: writing, secrets, git safety, JavaScript and TypeScript, Python, shell scripts, GitHub Actions, commit messages, pull requests, and coding process |
| `references/asd-ste100/` | The writing standard, in three files that the agent reads on demand |

## How to install it

```bash
cp CLAUDE.md ~/.claude/CLAUDE.md
mkdir -p ~/.claude/references
cp -R references/asd-ste100 ~/.claude/references/
```

Claude Code reads `~/.claude/CLAUDE.md` in every session, in every project.
The file costs about 2.7k tokens. The three reference files cost nothing until
the agent needs more detail than the core rules give.

### To take the writing standard alone

Copy the `## ASD-STE100 Simplified Technical English` section into your own
`CLAUDE.md`, then copy `references/asd-ste100/`. That section needs no other
part of this file.

## About ASD-STE100

ASD-STE100 Simplified Technical English is a real standard for technical
writing. It has 53 writing rules and a dictionary of 875 approved words.
Aerospace and defence documentation uses it. It suits an agent well, because
the rules are concrete and a reader can check them.

The files in `references/asd-ste100/` paraphrase the rules. They do not copy
ASD's text, explanations, or examples. ASD holds the copyright, and gives free
reproduction rights to eight groups only. Get the standard from
<https://www.asd-ste100.org/>.

These files do not contain the dictionary, which is proprietary. A rule with
the mark **[D]** needs the dictionary, so you cannot apply that rule from this
repo.

`CLAUDE.md` closes that gap by principle instead of by word list. The "Word
choice" block asks for the shortest common word, one term per thing, no
nominalizations, and a short table of plain replacements. The "Check your prose"
block gives the agent five things to correct before it sends prose. You get most
of the benefit of the dictionary, and you need no licence for it.

## About the coding guidelines

Andrej Karpathy wrote a [post on the mistakes that a coding agent
makes](https://x.com/karpathy/status/2015883857489522876). The `## Coding
Guidelines` section answers that post with four principles: think before
coding, simplicity first, surgical changes, and goal-driven execution. The
wording follows
[multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/CLAUDE.md),
which turned the post into agent rules. This repo keeps the four principles,
and adds a fifth on test-driven development.

## What you will want to change

These rules are opinions, and they are mine:

- Python uses pyenv. Change this section if you prefer uv or asdf.
- Node uses nvm, and the lockfile decides the package manager.
- Pull requests are small and stacked.
- The GitHub Actions section names Aikido as one source for the SHA-pinning
  rule.

`CLAUDE.md` addresses the agent as "you", and it calls the owner "I". Keep that
shape when you edit it.

## License

MIT for the files in this repo. Read `LICENSE`. The ASD-STE100 standard itself
is not MIT. Read the section above.
