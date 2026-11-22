# Two-step company prompt

Attach the company upload files to one chat in the v2.3 Project. Replace the placeholders with the company and the cutoff printed by the local runner.

## First message

```text
<ticker> <company>
MODE: INTAKE_ONLY
AS_OF_DATE: <YYYY-MM-DD>
Use intake_brief.json and the one-page intake format in CORE_CONTRACT.md.
```

## Follow-up in the same chat

```text
MODE: FULL_ANALYSIS
AS_OF_DATE: <same YYYY-MM-DD>
MODEL_LABEL: <filesystem-safe label, or MODEL_UNDISCLOSED>
Use the preceding accepted intake and its bounded search plan. Complete the applicable analysis and deliver the decision memo.
```

For a single message use MODE: AUTO with the same company, cutoff and attachments.
