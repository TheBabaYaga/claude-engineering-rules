# No AI slop — how to apply the rules

Read this with the `## No AI slop` section of `CLAUDE.md`. That section gives the rules. This file tells you how hard to apply them, which standard wins where two rules disagree, and where neither applies.

## What each standard fixes

`CLAUDE.md` carries two prose standards. They fail in opposite directions, which is why it carries both.

ASD-STE100 fixes the **form** of a sentence: the tense, the voice, the length, the word choice. A text that obeys it is easy to parse. STE cannot tell you whether the sentence was worth writing.

The no-slop rules fix the **substance**: is the sentence specific, does it add a fact, does it back its claims. A text that obeys them says something. The rules cannot tell you whether the sentence is easy to read.

Apply both. Run the no-slop rules first, because a clean STE rewrite of an empty paragraph gives you a short, clean, empty paragraph.

## Order of work

1. Write the substance. Name the thing, the number, the date, or the mechanism.
2. Run the swap test on each sentence. Cut or fix what survives it.
3. Remove the shapes and the listed words.
4. Apply the STE structural rules to what is left.
5. Read it once against the pre-send check in both sections of `CLAUDE.md`.

## Where the two standards agree

Four rules appear in both. Apply them once.

| Rule | STE | No slop |
|---|---|---|
| One name for one thing | 1.11, 9.4 | Failure 5 |
| Use the verb, not the noun | 3.7 | Failure 4, the noun dressed as a verb |
| Active voice | 3.6 | Failure 1, portable motive |
| Delete the unearned quality adjective | GR-6 | Failure 4 |

Both standards also protect a hedge. STE protects it as a deliberate departure from its own length caps. The no-slop rules cut an empty qualifier and keep a real one.

## Where they disagree

**1. Voice.** STE flattens voice on purpose. It was built so that a reader with poor English cannot misread an aircraft manual. The no-slop rules protect voice, because a flat text reads as machine-written even when every fact is right.

Split the rule by who owns the text.

| Text | Standard |
|---|---|
| Prose you write | STE wins. Flatten it. |
| A draft of mine that you edit | No slop wins. Keep my voice, and never rewrite my words into STE. |
| My Slack messages | Neither. Use the `my-voice` skill. |

**2. Lists.** STE rule 4.1 wants a vertical list for a sequence of three or more steps. The no-slop rules call a bullet list decoration when two sentences of prose read better.

Use a list for a real sequence of steps, a real set of options, or a real table of values. Use prose for reasoning, for an explanation, and for a comparison of two things.

**3. The em dash.** STE permits it. The no-slop rules restrict it. The restriction wins. A label separator in a list, a table, or a heading is not affected.

**4. Sentence variety.** The STE caps of 20 and 25 words push every sentence toward the same short shape. The no-slop rules call three identical shapes in a row a failure.

Keep the cap. Vary the shape inside it. A six-word sentence next to an eighteen-word sentence obeys both standards.

**5. Fragments.** STE rule 4.5 wants the articles and complete sentences. The no-slop rules permit a fragment that belongs to the writer.

Write complete sentences in your own prose. Keep my fragments in my draft.

**6. Brevity against precision.** No conflict, and both standards say so. STE rule 4.2 forbids you to remove words to make a sentence shorter. The no-slop rules protect the specific fact. Keep the longer sentence when the shorter one drops a condition, a scope limit, or a number.

## How hard to apply each rule

Failures 1 thru 4 are absolute. A portable sentence, an unbacked claim, and an invented number are wrong in every kind of text.

Failure 5 is a default, not a law. Formatting serves the content, and some content needs a table, a list, or a heading over a short section. The test still holds: remove it, and see whether you lost information.

## Where the rules do not apply

- Code, identifiers, file paths, command output, and log lines.
- Quoted text from another source.
- A listed word used as an example of the failure, or as the correct technical term. "Leverage" is banned as a verb for "use". It stays in "financial leverage".
- A commit message subject line, where Conventional Commits sets the form.
- My own words in my own draft.

## What the rules cannot do

They remove the tells of machine-written text. They do not supply a point.

A paragraph with nothing to say passes every check once you delete enough of it. The honest output is to say that the paragraph has no point, and ask what the point should be. Do not polish it and return it.

The same holds for a detect request. When I ask whether a text reads as AI, name the failure and quote the line. A named failure is evidence that I can check. Do not score the text, and do not guess who wrote it, because you cannot know.
