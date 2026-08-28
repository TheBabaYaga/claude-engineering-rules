# How to apply ASD-STE100 without the dictionary

Read this with `writing-rules.md`. That file gives the 53 rules. This file tells you which of them you can apply, and how hard to apply them.

## The problem

STE has two kinds of rule.

**Structural rules** describe the shape of a sentence. They are self-contained. You can apply them from the rule text alone.

**Lexical rules** point at ASD's dictionary: 875 approved words, each with one approved meaning and one approved part of speech. You do not have that dictionary. Without it, the lexical rules become a preference for plain words, not a standard you can check.

Apply the structural rules fully. Apply the lexical rules as a direction, and do not claim compliance you cannot prove.

| Kind | Rules | What to do |
|---|---|---|
| Structural | 1.7 thru 1.11, 1.13, 1.14, 2.1, 2.2, 3.2 thru 3.6, 4.1 thru 4.5, 5.1 thru 5.5, 6.1 thru 6.6, 7.1 thru 7.3, 8.1 thru 8.7, 9.1, 9.3, 9.4 | Apply fully. |
| Lexical | 1.1 thru 1.6, 1.12, 3.1, 3.7, 9.2 | Take the plainest, most common word. Use the same word for the same thing every time. Do not say the text is dictionary-compliant. |

## Two modes

Select a mode from the type of text. Do not announce the mode.

**Strict** — error messages, tool descriptions, prompts, instructions for another agent, safety text, procedures, API docs. A wrong reading has a cost here. Apply every structural rule, and the 20-word cap.

**STE-flavored** — chat replies, explanations, README files, PR descriptions, commit messages, changelogs. Apply the structural rules. Drop the one-word-one-meaning lockdown. Prose needs some range, and a strict rewrite of prose reads as a personality transplant.

## Three deliberate departures

STE was built for aircraft manuals. Three of its rules cost information in other text. Keep the information.

1. **Hedges are content.** "The request may have failed" and "the request failed" are different claims. A length cap tempts you to cut the hedge. Do not cut it. Confidence is part of the message.
2. **The present perfect sometimes carries meaning.** Rule 3.4 removes it. But "the job has completed" (and its output is available now) says more than "the job completed" (at some past point). Keep the compound form when the simple form loses the meaning. Elsewhere, obey rule 3.4.
3. **Precision beats brevity.** If a shorter sentence drops a condition, a scope limit, or a number, keep the longer sentence. Rule 4.2 agrees: do not remove words to make a sentence shorter.

## Scan checklist

Six habits make machine-written English hard to read. Each one is mechanical. You can point at the word that breaks it.

1. **Synonym rotation** — the same thing gets three names ("the user", "the customer", "the client"). The reader cannot tell if that is one thing or three. Pick one name. (Rules 1.11, 9.4)
2. **Hedge stacking** — "it is important to note that this may potentially help to improve". State the claim, or delete it.
3. **Nominalization** — an action frozen into a noun: "perform an analysis of", "provides assistance to". Use the verb: "analyze", "helps". (Rule 3.7)
4. **Marketing adjectives** — seamless, robust, powerful, cutting-edge, effortless, blazing-fast. Delete them, or give the measurement that earns the claim.
5. **Long compound sentences** — several ideas joined by a semicolon or a dash. One idea in one sentence. (Rules 4.1, 5.2, 8.1)
6. **Soft phrasal verbs** — spin up, reach out, dive into, kick off, roll out. Use the plain verb: start, contact, read, begin, release. (Rule 9.3)

## Where STE does not apply

- Code, identifiers, file paths, command output, and log lines.
- Quoted text from another source.
- A commit message subject line, where Conventional Commits sets the form.
- Text where voice or persuasion is the point.

## What STE cannot do

STE fixes the form of a text. It does not fix the substance. A paragraph with nothing to say becomes a short, clean paragraph with nothing to say. Say that instead of polishing it.

Do not compress past the point of clarity. The target is no ambiguity, not the fewest words.
