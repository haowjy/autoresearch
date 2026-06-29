# autoresearch

A Mars prompt package for coordinating AI research loops in the Meridian ecosystem.

It contains:

- `skills/autoresearch` — reusable method for walking a research tree, designing investigations, supervising runs, reconvening on results, and preserving research memory.
- `agents/autoresearch-lead` — a thin coordination agent that loads the skill, reuses `meridian-dev-workflow`, and delegates nontrivial experiment design to `@design-lead`.

Install or sync it through Mars/Meridian in a downstream project.
