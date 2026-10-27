# Public portfolio guidance

This repository is Mindwire's public documentation library. The implementation and development history belong to a separate private workshop. Keep independent Git histories and preserve repository visibility. Never mirror, import, or publish private code or history here.

## Content and evidence

Inspect current implementation, Git history, documentation, and available evidence before writing. Publish an accurate account of purpose, current behavior, architecture decisions, verified results, known limitations, and priorities. Distinguish completed work, implemented but unverified behavior, and future plans. Never invent historical milestones, metrics, results, or evidence. Keep original dates and scope when reusing checks; documentation-only changes do not require application tests.

Never include credentials, the Kalshi private key, confidential material, internal logs, raw recovery transcripts, private conversation links, machine-specific paths, or private implementation identifiers. Inspect media and selected files before committing. Preserve third-party attribution. The private workshop maintains implementation-to-publication traceability; do not reproduce that private ledger here.

## When to publish

Treat portfolio documentation as part of completing a major milestone, meaningful problem resolution, implemented architectural decision or pivot, or substantial feature. Also publish when the owner says “log this for the public repo.” Group related small changes into the relevant entry; routine edits belong in Git history. Keep the portfolio current during future development without waiting for these instructions to be repeated.

## Voice

Write from the project owner's perspective in natural professional technical prose. Use first person for intent, decisions, priorities, tradeoffs, and judgment. Make the system, mechanism, or result the subject when explaining behavior and evidence. Use connected paragraphs, varied openings, and direct headings such as Architecture, Verification, and Remaining work.

Start with the goal or concrete problem, then explain why the change was necessary, the actual mechanism, how it works, evidence, and tradeoffs or remaining work. Support rationale with implementation and available evidence. Do not fabricate personal hands-on testing, authorship, or participation. Preserve attribution. Avoid filler, inflated claims, unexplained jargon, or lists without purpose.

Portfolio prose must not narrate conversations or instructions to an assistant, or use “The user requested,” “I updated,” or “As an AI.”

## Library and completion

The README owns purpose and navigation; `docs/status.md` owns current capability status; `docs/architecture.md` owns the system reference; `case-studies/` explains focused decisions; dated `verification/` entries retain evidence; `CHANGELOG.md` is the short chronological index. Update existing references when scope changes. Avoid duplicate sources of truth or one growing document.

Before publication, review factual claims, links, staged files, media, credentials, and private information. Follow established branch and pull-request policies, preserve unrelated edits, and never rewrite shared history or merge a PR without explicit authorization. Commit and push completed documentation, then verify remote commit IDs and readable published entries. A pushed branch or PR is not a merged default-branch update or a deployed application. Preserve pending work and report the exact gap if publication fails. Finish with a concise account and direct links to the published entries.
