# No AI slop — words to cut

Source: the `no-ai-slop` skill by Peter Yang, <https://github.com/petergyang/no-ai-slop>. MIT license.

Read this with the plain-word table in the ASD-STE100 section of `CLAUDE.md`. That table replaces a formal word with a common one. This file removes words that carry no meaning at all.

## Banned outright

Never use these. There is no context that earns them.

```text
delve            foster           leverage         utilize
facilitate       empower          streamline       robust
cutting-edge     paradigm shift   game changer     tapestry
realm            beacon           multifaceted     meticulous
intricate        paramount        transformative   elevate
embark           supercharge      harness          ever-evolving
```

Also banned as a reaction: "this is huge", "this changes everything".

Two notes:

- Keep a word when it is the correct technical term. "Leverage" is banned as a verb for "use". It stays in "financial leverage".
- Keep a banned word inside a quote, a code identifier, or an example of the pattern itself.

## Often-empty adverbs

```text
just         literally     honestly      simply       actually
truly        fundamentally importantly   crucially    inherently
inevitably
```

Cut one when it adds nothing. Keep one when it carries emphasis, contrast, or real uncertainty, or when it belongs to the writer's spoken rhythm.

> **Cut:** This is just a simple config change.
> **Keep:** I honestly do not know why the retry fires twice.

## Often-empty phrases

```text
it is worth noting        it is important to note   at the end of the day
when it comes to          at its core               in today's world
in the age of             in the world of           the reality is
the truth is              in terms of               with regard to
in order to               going forward             in this article
let's dive in
```

Cut one when it delays the point. "In order to" becomes "to". "With regard to" becomes "about", or nothing.

Keep a phrase only when it is part of the writer's recognizable voice and the sentence still earns its place.

## Verb phrases to compress

Make the verb do the work. ASD-STE100 rule 3.7 says the same thing.

```text
made a decision        -> decided
has the ability to     -> can
performs a validation  -> validates
provides assistance    -> helps
gives consideration to -> considers
is in agreement with   -> agrees
```

## The claim test

Before you use an adjective that claims quality, give the measurement that earns it. If you have no measurement, delete the adjective.

> **Before:** The pipeline is a robust, seamless solution.
> **After:** The pipeline reads JSON and CSV. It rejects other formats with an error.
