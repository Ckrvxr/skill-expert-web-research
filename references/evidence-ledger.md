# Evidence ledger and output templates

Use only as much structure as the task needs. These are tool-neutral examples, not mandatory API schemas.

## Question map

| ID | Subquestion | Completion condition | Best likely source | Status |
| --- | --- | --- | --- | --- |
| Q1 | What changed? | Date/version and documented change located | Official changelog | Open |
| Q2 | Does it work in practice? | Applicable test with methods/limitations | Independent reproduction | Open |

## Claim ledger

| Claim ID | Bounded claim | Source URL / original origin | Source type | Passage or locator | Dates / version / scope | Access | Support | Gap |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| C1 | Vendor documents feature X for version V | URL, publisher | official-description | Section / short quote | Updated date; V | Full text | Directly supported as documentation | Runtime behavior not tested |
| C2 | Feature X always does Y | URL, same origin as C1 | official-description | No supporting passage | Unknown | Full text | Unresolved | Needs observations; narrow claim |

For claims with multiple sources, use one row per source and repeat the claim ID; record the source type and original origin for each source. Assess corroboration across independent origins, not by counting rows.

Access: full-text / excerpt / snippet-only / inaccessible.
Support: directly-supported / corroborated / tentative-inference / unresolved.
Source type: primary-record / official-description / independent-analysis / reporting / anecdote / unverified-prompt.
These dimensions are separate: an official statement can be accessible and accurately quoted yet not prove an empirical outcome.

## Query log (for substantial investigations)

| Round | Query / extraction question | Purpose | New evidence | Next gap |
| --- | --- | --- | --- | --- |
| 1 | Official definition query | Establish terminology | Definition + version | Need independent behavior |
| 2 | Failure / limitation query | Challenge leading explanation | Counterexample | Resolve version mismatch |

## Minimal machine-readable record

```json
{
  "claim_id": "C1",
  "claim": "The vendor documents feature X for version V.",
  "source_url": "https://example.org/docs",
  "source_type": "official-description",
  "original_origin": "example.org/docs",
  "retrieved_at": "YYYY-MM-DD",
  "published_at": null,
  "scope": "version V",
  "access": "full-text",
  "passage": "Short exact excerpt, or null if unavailable.",
  "locator": "Feature X section",
  "support": "directly-supported",
  "limitations": ["Documented behavior, not independently tested"]
}
```

Do not invent timestamps. Record hashes only if actually calculated; a hash establishes artifact identity, not truth or authorship.
For prompt artifacts record the repository, pinned commit, path, and any mismatched embedded date.
Avoid distributing entire third-party prompts when a short analytical excerpt and link suffice.

## Concise answer skeleton

**Conclusion:** [answer bounded by date/scope].

| Finding | Evidence | Qualification |
| --- | --- | --- |
| ... | Link/citation | ... |

**Limitations:** [material unknowns only].
**Next step:** [optional action].

A source list is optional if inline links already provide traceability. Never replace claim-level citations with an unrelated bibliography.
