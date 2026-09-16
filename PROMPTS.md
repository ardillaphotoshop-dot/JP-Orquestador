# JP-Orquestador prompt

Recommended settings:

STEP 1:

Claude: Sonnet 5 / Medium
OpenAI: Terra / Medium

STEP 2:

Claude: Opus 5 / Medium; use High for the complexity triggers above.
OpenAI: Sol / High; test Medium later on uncomplicated issuers.

## STEP 1

MODE: INTAKE_ONLY

AS_OF_DATE: 2026-09-16

Run only the canonical Intake and Readiness component.

Treat a supported `PARSER_VALID` financial handoff as already structurally
and semantically validated by the parser. Do not validate it against the
JSON Schema, re-derive canonical financial observations, or audit unaffected
source series.

Return the required one-page intake output:

1. READINESS: READY | PARTIAL | NOT_READY
2. Identity and as-of line
3. Evidence coverage
4. Financial-handoff status
5. Exceptions ordered by severity
6. Preliminary route/plugin activations
7. FULL ANALYSIS MAY PROCEED | FULL ANALYSIS BLOCKED

Do not perform Company Map classification, valuation, management scoring,
peer research, scenario analysis, or memo generation.

This intake result will be the authoritative upstream handoff for the next
request in this conversation.


## STEP 2

MODE: FULL_ANALYSIS

AS_OF_DATE: 2026-09-16

MODEL_LABEL: CLAUDE_OPUS-5_MEDIUM

MODEL_LABEL: OPENAI_GPT-5.6_SOL-HIGH

Use the immediately preceding INTAKE_ONLY result as the authoritative
completed output of `01_INTAKE_READINESS.md`.

Do not rerun Intake, repeat the evidence inventory, revalidate the financial
handoff, or repeat completed share/accounting/provenance reconciliation.

Start with `02_COMPANY_MAP_AND_ROUTER.md` and complete the remaining applicable
production pipeline.

The original project sources remain available for substantive company analysis.
Consult them selectively for business analysis, normalization, valuation,
governance and decision-relevant evidence. This instruction prohibits repeated
intake validation; it does not prohibit using accepted source evidence needed
for the investment analysis.

If the prior intake status was PARTIAL, address only the exceptions explicitly
identified in that intake. Reopen an accepted intake conclusion only if new
evidence creates a decision-critical contradiction.

Create the final Markdown memo using the project output specification and the
filename MODEL_LABEL supplied above.
