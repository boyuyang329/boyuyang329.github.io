---
layout: page
title: ProteinScope
description: An LLM agent that interprets proteomics results with sources
importance: 1
---

ProteinScope is an LLM agent that takes a list of proteins, looks them up in curated databases and the literature, and writes a biological interpretation where each claim can be traced to a source. It is built from scratch, without an agent framework, so every step of the loop is visible.

**What I am studying**

The main question is not only whether the agent can produce a fluent answer, but whether its conclusions are supported by what its tools actually returned. Early runs already showed two failure modes:

- The agent mixed facts from the database with its own background knowledge, then labeled the whole answer as coming from the database.
- When a tool did not return a field (for example, disease annotations), the agent concluded that the database did not contain it.

**Plan**

1. A fixed pipeline: annotation, pathway enrichment, literature search, summary.
2. An agentic version where the model decides which tools to call.
3. An evaluation against published findings from a public ALS plasma proteomics study, comparing the two versions.

Code: [github.com/boyuyang329/proteinscope](https://github.com/boyuyang329/proteinscope)
