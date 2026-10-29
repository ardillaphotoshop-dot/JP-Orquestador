MODE: CONSERVATIVE_CURATION_V1
TICKER: 2768 Sojitz Corporation
COMPANY: Sojitz Corporation
AS_OF_DATE: 20261029

Inputs: original, unmodified company files plus `source_inventory.json` created by the local processor. Read the project instructions and relevance contract.

1. Match each reviewed file to its `source_id`; do not invent IDs, hashes or page ranges.
2. Inspect sources for document coverage, exact duplicates and low-information pages in trim-eligible presentations only.
3. Explicitly inspect each page you propose omitting. If not demonstrably safe, keep it.
4. Identify decision-critical or material document categories that are truly missing. Search official sources only for these gaps. Supply verified, as-of-consistent source URLs or null.
5. Output a downloadable `<TICKER>_curation_manifest_v1.json` conforming to the supplied schema. Keep all unlisted or unreviewed files. Do not create extracted replacements or modify financial data.
6. Briefly summarize the proposed operations and remaining uncertainties. Do not run Orchestrator Intake or investment valuation.

If tool limits prevent dependable examination of a source, leave it untouched and disclose that limitation. Never imply a complete document/page review if one did not occur.



# CODEX
The processor has two commands.

First, inventory the original files.
python local_processor/curator_processor.py inventory \
  --raw runs/7011/raw_sources \
  --out runs/7011/source_inventory.json \
  --draft runs/7011/curation_manifest_draft.json


Upload the original documents, inventory and draft manifest to the remote Curator.

Second, download and execute the Curator's manifest.
python local_processor/curator_processor.py build \
  --raw runs/7011/raw_sources \
  --inventory runs/7011/source_inventory.json \
  --manifest runs/7011/7011_curation_manifest_v1.json \
  --out runs/7011/build_001
