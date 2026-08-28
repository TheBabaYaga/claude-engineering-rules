# ASD-STE100 — before and after

These examples are written for this repository. They are not from the standard. Each one names the rule it fixes. Refer to `writing-rules.md` for the rule text.

## Sentence length and one instruction per sentence (5.1, 5.2, 4.1)

> **Before:** To deploy the service, first make sure that the migration has run against staging, and then, after you have confirmed the health check returns 200, promote the build to production and notify the channel.

> **After:**
> 1. Run the migration against staging.
> 2. Make sure that the health check returns 200.
> 3. Promote the build to production.
> 4. Send a message to the channel.

One instruction in one step. Each step is a command. The reader can stop after any step.

## Active voice (3.6)

> **Before:** The token is refreshed by the middleware when the session is validated.

> **After:** The middleware refreshes the token when it validates the session.

Passive voice hides who acts. Rule 3.6 permits it in descriptive text only when the agent is unknown.

## Simple tenses (3.2, 3.4)

> **Before:** We have removed the legacy endpoint and the client libraries have been updated.

> **After:** We removed the legacy endpoint. We updated the client libraries.

Note the exception in `applying-ste.md`: keep the present perfect when it carries current relevance that the simple past loses.

## Nominalization (3.7)

> **Before:** The service performs a validation of the payload and provides notification to the caller.

> **After:** The service validates the payload. Then it notifies the caller.

## Phrasal verbs (9.3)

> **Before:** Spin up a worker, reach out to the API, and kick off the sync.

> **After:** Start a worker. Send a request to the API. Start the sync.

A two-word verb has a meaning that its parts do not predict. "Kick off" and "kick" are unrelated.

## One word, one meaning (1.11, 9.4)

> **Before:** The client sends a request. The consumer receives a token. The caller then retries.

> **After:** The client sends a request. The client receives a token. The client then retries.

Three names for one thing make the reader look for three things.

## Multi-word nouns (2.1, 2.2)

> **Before:** the agent task queue priority handler configuration

> **After:** the configuration for the handler that sets the priority of the task queue

Five stacked nouns hide the relations between them. Three words is the maximum.

## Omission and articles (4.2, 4.5)

> **Before:** Files not backed up will be lost.

> **After:** The system deletes each file that it did not copy to the backup.

The first sentence has two readings: all files, or only the files without a backup.

## The semicolon (8.1)

> **Before:** The build failed; the cache was stale.

> **After:** The build failed because the cache was stale.

STE bans the semicolon. It permits every other standard mark, the em dash included.

## Safety instructions (7.1, 7.2, 7.3)

> **Before:** Note that running this against production may result in data loss if the dry-run flag is omitted.

> **After:** WARNING: Do not run this command against production without the `--dry-run` flag. The command deletes every row that it does not match.

The command comes first. The explanation of the risk follows it.

## Keep the hedge

> **Before:** The request may have timed out.

> **Wrong after:** The request timed out.

> **Right after:** The request may have timed out.

A shorter sentence that upgrades a hedge to a fact is a different claim, not a simplification. This is the most common way an STE rewrite goes wrong.

## Latin abbreviations and marketing words (GR-6, checklist item 4)

> **Before:** The new pipeline is a robust, seamless solution that handles most formats (e.g. JSON, CSV, etc.).

> **After:** The new pipeline reads JSON and CSV. It rejects other formats with an error.

Delete the adjective that claims quality. Give the fact that earns it.
