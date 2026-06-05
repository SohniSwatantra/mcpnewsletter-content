# Contributing to MCP Newsletter

This repo contains the public content archive for [MCPnewsletter.com](https://mcpnewsletter.com).

You can contribute in two ways:

1. **Submit a company/project launch** using the GitHub issue template.
2. **Open a PR** to add or update a newsletter edition.

## Submit a launch or update

Open an issue using **Submit MCP news / launch** and include:

- Project or company name
- Link to announcement, docs, repo, demo, or blog post
- What changed
- Why MCP builders should care
- Any technical caveats, security notes, or implementation details

Please avoid pure marketing copy. The newsletter prioritizes practical signal for developers.

## Add a new edition

Create a Markdown file under:

```txt
content/issues/drafts/
```

Use a filename like:

```txt
004-short-slug.md
```

Recommended item format:

```md
## Title of item

**Link:** https://example.com

**What happened:** One or two sentences.

**Why it matters:** Practical implications for MCP builders.

**Builder note:** Concrete implementation insight, caveat, or question.
```

## Update an existing edition

Edit the relevant file in `content/issues/` and open a PR. Include a short note explaining what changed and why.

## Editorial voice

- Clear, practical, developer-oriented.
- Explain why a link matters, not just what it says.
- Preserve URLs and attribution.
- Make claims cautiously when source material is incomplete.
- Avoid generic AI buzzwords unless quoting source material.
