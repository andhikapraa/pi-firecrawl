---
name: firecrawl-research-index
description: Use Firecrawl's Research Index for academic literature searches, passage-level evidence, and related-paper expansion. Trigger for research papers, literature reviews, methods, benchmarks, citations, arXiv, PubMed, DOI, PMID, or related work.
license: MIT
---

# Firecrawl Research Index

Use the dedicated Research Index tools instead of general web search when the task is about scientific literature.

## Workflow

1. Search with `firecrawl_research_search_papers` using a natural-language topic, method, benchmark, author, or category query.
2. Preserve each result's `primaryId` such as `arxiv:...`, `pmid:...`, `pmcid:...`, or `doi:...`. Use it as the stable citation and lookup identifier.
3. Inspect or verify evidence with `firecrawl_research_read_paper`. Pass a focused question to retrieve ranked full-text passages. Do not infer method details, datasets, or numeric results from an abstract when a passage can verify them.
4. Expand from strong seeds with `firecrawl_research_related_papers`. Choose `similar`, `citers`, or `references` based on the question.
5. Synthesize only claims supported by retrieved abstracts or passages. Preserve paper title, identifier, authors, and source links in the final citations.

## Scope

Use the Research Index for literature work. Use normal `firecrawl_search` for ordinary web pages on academic domains, implementation discussions, project pages, and grey literature. Use `firecrawl_scrape` for a known PDF or paper URL that is not present in the index.

The index currently covers arXiv plus major biomedical sources including PubMed, bioRxiv, and medRxiv. Coverage is not universal. If the query concerns another discipline or a missing paper, state the limitation and supplement with Exa or another authoritative source.

## Evidence rules

- Search results identify candidates; they do not prove a claim.
- Passage-level retrieval is the preferred evidence for methods, datasets, limitations, and numeric results.
- Separate an author's claim from an independently verified result.
- Do not present vendor benchmark numbers as independent evaluations. Attribute them to Firecrawl when relevant.
- Deduplicate versions by canonical identifiers and prefer the primary source.
- Do not fabricate citation metadata or claim that a paper supports a statement when the retrieved passage does not.

## Cost and credentials

The Research Index can start without an API key at lower limits. Use the configured Firecrawl API key for higher limits. Do not put keys in prompts, skill files, repository files, or tool arguments unless the tool requires a secret resolver. Keep requests bounded with explicit result and passage limits.

## Completion

A literature search is complete when candidate papers were searched, important claims were verified with paper passages where available, related work was expanded when relevant, coverage limitations were stated, and citations use stable paper identifiers.
