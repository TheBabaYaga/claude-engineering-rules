# No AI slop — the five failures in full

Read this with the `## No AI slop` section of `CLAUDE.md`. That section gives the five failures and the test for each one. This file names every shape under each failure, and gives a before and after pair for each shape.

The examples are written for this repository. Each "after" keeps the information of the "before" and drops nothing.

## Failure 1 — the sentence is portable

The test: swap the subject for a competitor, another team, or another product. If the sentence still reads as true, it says nothing about the subject.

This is the failure that survives every other check. A portable sentence can be short, active, plain, and grammatical. It is still filler.

**Abstract outcome**

> **Before:** The integration improved efficiency across the team.
> **After:** The integration cut the deploy from 40 minutes to 4.

**Portable praise**

> **Before:** The library has a clean, well-designed API.
> **After:** The library has four public functions and no configuration file.

**Portable motive**

> **Before:** We built this to serve our users better.
> **After:** We built this because support answered the same billing question 60 times a month.

The fix is always the same. Give a name, a number, a date, or a mechanism. If you have none of the four, you have no sentence.

## Failure 2 — the sentence rates a fact instead of adding one

The test: does the sentence add a fact, or does it tell the reader how to weigh one that is already there?

**Importance markers**

> **Before:** The launch marks a pivotal moment for the company.
> **After:** The launch is the company's first paid product.

**Reader guidance**

> **Before:** The key point is that the cache never invalidates. That matters more than it sounds.
> **After:** The cache never invalidates.

If the point needs the extra sentence, the fix is a fact, not an instruction to care.

**The trailing "-ing" clause**

A clause that starts with highlighting, underscoring, reflecting, showcasing, or demonstrating claims to explain what a fact means. It restates the fact in vaguer words.

> **Before:** The release adds file search, highlighting the team's focus on workflow.
> **After:** The release adds file search, so a user finds an old draft without leaving the editor.

**The expert setup**

> **Before:** Here is what most teams get wrong about caching: invalidation is the hard part.
> **After:** Invalidation is the hard part of caching.

**The announcement**

A clause that announces what you are about to say. "It is worth noting", "it is important to note", "the reality is", "at the end of the day", "let's dive in", "in this article".

> **Before:** It is worth noting that the migration is not reversible.
> **After:** The migration is not reversible.

## Failure 3 — the sentence borrows a shape to fake insight

The test: can you state the claim as one plain sentence? Then do that. These five shapes carry rhythm, not meaning.

**The pivot**

"It is not X. It is Y." Also "the question is not X, it is Y" and "it is not just X, but Y".

> **Before:** The problem is not the model. It is the eval.
> **After:** The eval matters more than the model.

**The reveal**

A noun phrase, a colon, then a dramatic clause.

> **Before:** The detail that makes it work: a second agent grades the output.
> **After:** A second agent grades the output, which is what makes it work.

Use a colon for a list, a label, or a quote. Keep sentence case after it, unless grammar, a proper noun, a title, or code requires otherwise.

**The self-answered question**

"What if I told you", "Think about it:", "Plot twist:", or a question that you answer in the next line.

> **Before:** So what actually broke? The retry logic.
> **After:** The retry logic broke.

**The stack**

"X. And Y. And Z." Also the denial run-up: "Not a framework. Not a library. A compiler."

> **Before:** It reads the diff. And it scores it. And it writes the summary.
> **After:** It reads the diff, scores it, and writes the summary.

**The kicker**

A closing metaphor, aphorism, or mic-drop line.

> **Before:** ... and that is why the eval is the moat. Everything else is just plumbing.
> **After:** ... and that is why the eval matters more than the model.

Delete the kicker. Do not rewrite it into a better metaphor, and do not keep its rhythm. End on the clearest concrete sentence that the text already has. If the end needs closure, add a plain takeaway or the next action.

## Failure 4 — the claim has no backing

The test: name the measurement or the source. If you have neither, cut the claim.

**Quality adjective, no measure**

> **Before:** The pipeline is a robust, seamless solution.
> **After:** The pipeline reads JSON and CSV. It rejects other formats with an error.

**Unnamed authority**

"Experts agree", "studies show", "industry reports suggest", "many argue", "widely regarded as".

> **Before:** Studies show that code review catches most defects.
> **After:** Cut the sentence, or name the study.

**Invented precision**

Never produce a number, a benchmark, a quote, or a source that you did not read. A plausible number is worse than no number, because a reader cannot tell it apart from a real one. Ask instead.

**The noun dressed as a verb**

A noun phrase that avoids saying "is" or "has".

> **Before:** The app serves as a centralized hub for sponsor management.
> **After:** The app tracks sponsors, drafts, due dates, and approvals in one place.

## Failure 5 — the form decorates instead of serving

The test: remove the formatting. If no information is lost, leave it removed.

**Decoration to remove**

- An emoji in a heading.
- Bold in the middle of a sentence, for emphasis.
- A heading over a section of two sentences.
- A bullet list where two sentences of prose read better.
- A table with one column of real content.

**One name for one thing**

Do not rotate synonyms for style. The reader looks for three things when you name one thing three ways. ASD-STE100 rule 1.11 says the same.

> **Before:** The agent reviews the draft. The assistant scores the piece. The tool suggests fixes.
> **After:** The agent reviews the draft, scores it, and suggests fixes.

**Rhythm**

Avoid three sentences with the same shape in a row, paragraphs of identical length, and a stack of short fragments. Vary the shape when it helps the point, not for decoration.

**The em dash**

Do not use an em dash inside a sentence. Use a comma, a period, or parentheses.

- Short copy: none.
- A long document: one or two, when they clearly beat the alternatives.
- Never two in one paragraph.

A label separator in a list, a table, or a heading is not this failure. This rule covers prose.
