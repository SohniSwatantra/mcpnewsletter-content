---
slug: mcp-weekly-003-workos-mcp-night-auth-md
title: "MCPnewsletter: WorkOS MCP Night, Auth.md, protocol evolution, and mcpc 3.0"
subject: "MCPnewsletter: WorkOS MCP Night, Auth.md, protocol evolution, and mcpc 3.0"
preview_text: "WorkOS MCP Night coverage, Auth.md, the 2026-07-28 MCP spec release candidate, open-source server momentum, Apify mcpc, ALPIC Beacon, and new MCP launches."
---

### Monday, May 25, 2026 | Read time: 4 min

## In this issue

- WorkOS MCP Night: Auth.md and agent-ready authentication
- MCP protocol evolution: the 2026-07-28 specification release candidate
- Open-source MCP servers pass 60K stars in community roundups
- Apify mcpc 3.0
- ALPIC Beacon for MCP app audits
- Latest launches: Kapso, Higgsfield, Ideogram

# Featured

<div class="media-card">
<figure><a href="/posts/workos-mcp-night-2026-highlights"><img src="/media/workos-mcp-night.png" alt="WorkOS MCP Night"></a><figcaption>WorkOS MCP Night</figcaption></figure>
<h3>WorkOS launches Auth.md at MCP Night</h3>
<p>WorkOS introduced <strong>Auth.md</strong>, a way to tell agents how they can become legitimate users.</p>
<p><a href="/posts/workos-mcp-night-2026-highlights">Read the WorkOS update →</a></p>
</div>

<div class="media-card">
<video controls preload="metadata" poster="/media/apify-jan-thumb.jpg"><source src="/media/apify-jan-mcp.mp4" type="video/mp4"></video>
<h3>Apify launches new mcpc version</h3>
<p>Apify mcpc video</p>
<p>Version 3.0 adds <code>mcpc connect</code> auto-discovery for MCP configs, improved x402 support, UX/AX optimizations, fixes, and a brand-new logo with consistent coloring.</p>
<p><a href="https://github.com/apify/mcpc">Open GitHub repo</a> · <a href="/media/apify-jan-mcp.mp4">Watch the short video</a></p>
</div>

<div class="media-card">
<figure><a href="https://beacon.alpic.ai/"><img src="/media/alpic.jpeg" alt="ALPIC Beacon"></a><figcaption>ALPIC Beacon</figcaption></figure>
<h3>ALPIC launches Beacon</h3>
<p>Beacon helps builders audit MCP apps before submitting to ChatGPT and Claude stores.</p>
<p><a href="https://beacon.alpic.ai/">Try Beacon →</a></p>
</div>

# WorkOS MCP Night: Auth.md and the future of agentic authentication

![WorkOS MCP Night 2026](/media/workos-mcp-night-2026-257.jpg)

**Link:** [Read the full MCP Night coverage and photo post](/posts/workos-mcp-night-2026-highlights)

WorkOS hosted MCP Night and introduced **Auth.md**, a machine-readable way for MCP servers and agent-facing apps to describe authentication requirements. The event included demos from AgentCard, AgentMail, Expo, Executor, Cloudflare, and Firecrawl, plus a panel with Cloudflare, ChatPRD, and Sentry.

Enterprise MCP adoption depends on whether agents can be safely authenticated, scoped, approved, and audited. Auth.md is interesting because it treats agents as real software users rather than anonymous scripts bolted onto APIs.

If your MCP server can touch customer data, production systems, billing, or admin workflows, document auth flows clearly. Start with read-only scopes, require explicit approval for risky actions, and make audit trails easy to inspect.

Key quotes from the event included:

<div class="quote-card"><img src="/media/workos-mcp-night-2026-256.jpg" alt="WorkOS MCP Night speaker"><blockquote>“Agent Ready is the next Enterprise Ready.”<br><strong>— Michael Grinich, WorkOS</strong></blockquote></div>

<div class="quote-card"><img src="/media/workos-mcp-night-2026-258.jpg" alt="WorkOS MCP Night audience"><blockquote>“Make something agents want.”<br><strong>— Michael Grinich, WorkOS</strong></blockquote></div>

<div class="quote-card"><img src="/media/workos-mcp-night-2026-268.jpg" alt="WorkOS MCP Night panel"><blockquote>“Your user is changing... whether they are less technical or no longer human.”<br><strong>— Claire Vo, ChatPRD</strong></blockquote></div>

<div class="quote-card"><img src="/media/workos-mcp-night-2026-272.jpg" alt="WorkOS MCP Night discussion"><blockquote>“I'm very anti-let agents sign up for services... but it might be a thing that's necessary.”<br><strong>— David Cramer, Sentry</strong></blockquote></div>

<div class="quote-card"><img src="/media/workos-mcp-night-2026-277.jpg" alt="WorkOS MCP Night demo"><blockquote>“Onboarding happens in somebody else's product.”<br><strong>— Brendan Irvine-Broque, Cloudflare</strong></blockquote></div>

Watch the full video: [https://www.youtube.com/watch?v=a1jx0H4cSWk](https://www.youtube.com/watch?v=a1jx0H4cSWk)

# MCP protocol evolution: the 2026-07-28 specification release candidate

**Link:** [https://modelcontextprotocol.io/blog/2026-07-28-release-candidate](https://modelcontextprotocol.io/blog/2026-07-28-release-candidate)

![David Soria Parra tweet on the MCP 2026-07-28 release candidate](/media/david-soria-mcp-2026-07-28-rc-tweet.png)

David Soria Parra and Den Delimarsky announced the **2026-07-28 MCP specification release candidate**, described as the largest protocol revision since launch. David summarized the shift clearly: “The protocol is now stateless: no handshake, no session id, any request can hit any server instance. Plus extensions as first-class (MCP Apps, Tasks), auth hardening, and a proper deprecation policy so we don't have to do this again.”

The most important change is that MCP becomes **stateless at the protocol layer**. Removing session assumptions makes it easier to run MCP servers on ordinary HTTP infrastructure, behind round-robin load balancers, and without sticky sessions or shared session stores.

Stateless MCP raises the bar for server design. Requests need to carry enough client info, protocol version, and capability metadata to stand alone. Builders should also pay attention to new routing headers, caching fields, extension versioning, and OAuth/OIDC hardening.

Notable changes:

- `initialize` / `initialized` handshake and `Mcp-Session-Id` are removed.
- New `Mcp-Method` and `Mcp-Name` headers improve routing without body inspection.
- `ttlMs` and `cacheScope` add HTTP-style caching patterns.
- MCP Apps and Tasks move into a formal extension model.
- Roots, Sampling, and Logging are deprecated in favor of newer patterns such as OpenTelemetry.

# Open-source MCP servers: 60K stars and growing

**Link:** [Reddit roundup](https://www.reddit.com/r/MCPservers/comments/1lu019w/best_mcp_servers_for_ai_agents_opensourced_60k/)

A community roundup highlighted open-source MCP servers that collectively passed 60K GitHub stars, including Context7, Playwright MCP, Sentry MCP, GitHub MCP, and PostgreSQL MCP.

The most useful MCP servers are clustering around concrete developer workflows: docs lookup, browser verification, error triage, repo operations, and database inspection.

Popularity is not the same as safety. Before connecting a server to sensitive systems, check scopes, maintenance activity, auth model, logging behavior, and whether there is a read-only mode.

# Latest MCP launches

## Kapso MCP

**Link:** [https://x.com/andresmatte/status/2057178931258601809](https://x.com/andresmatte/status/2057178931258601809)

Andrés Matte, [@andresmatte](https://x.com/andresmatte), announced the Kapso MCP:

WhatsApp numbers for agents.

1. Add MCP server
2. “Get a WhatsApp number”

Done — your agent is on WhatsApp.

<div class="media-card"><iframe class="tweet-video" src="https://platform.twitter.com/embed/Tweet.html?id=2057178931258601809" title="Kapso MCP launch video" loading="lazy" allow="fullscreen; autoplay; encrypted-media; picture-in-picture"></iframe><p><a href="https://x.com/i/status/2057178931258601809">Open Kapso launch video on X →</a></p></div>

## Higgsfield AI Personal Clipper

**Link:** [https://x.com/higgsfield_ai/status/2057825719611510790](https://x.com/higgsfield_ai/status/2057825719611510790)

Personal Clipper is available in Claude via Higgsfield MCP.

> Drop the link to your video
> Ask Higgsfield MCP to cut it into X clips based on the most viral moments
> Choose the aspect ratio and subtitle font
> Get X clips ready to post across every social platform

## Ideogram MCP

**Link:** [https://x.com/ideogram_ai/status/2057863035709173993](https://x.com/ideogram_ai/status/2057863035709173993)

Ideogram, [@ideogram_ai](https://x.com/ideogram_ai), is turning Claude into a design agent with Ideogram MCP — generate images, designs, and train custom models without leaving the chat.

Also available in ChatGPT, Cursor, Hermes, and more.

<div class="media-card"><iframe class="tweet-video" src="https://platform.twitter.com/embed/Tweet.html?id=2057863035709173993" title="Ideogram MCP launch video" loading="lazy" allow="fullscreen; autoplay; encrypted-media; picture-in-picture"></iframe><p><a href="https://x.com/i/status/2057863035709173993">Open Ideogram MCP video on X →</a></p></div>

# Community spotlight

## Keyser Faty — AgentCard

AgentCard is focused on agent identity: giving agents a recognizable, portable profile that applications can use to understand who or what is acting. This matters as agents move from anonymous tool callers to participants in authenticated software workflows.

## Adi Singh — AgentMail

AgentMail gives agents an email-native communication layer so they can receive, reason about, and send messages as part of a workflow. For builders, it points toward agents that can operate across existing business channels instead of only inside chat windows.

## Evan Bacon — Expo

Expo is bringing agent-assisted development closer to mobile app workflows. The interesting angle is practical: agents need access to project context, build systems, previews, and deployment paths if they are going to help ship real mobile features.

# MCP meme of the week

![](/media/mcp-meme-auth-md-agent-signup.png)

# Sponsor MCPnewsletter

Want to reach developers building with MCP servers, SDKs, registries, auth, agent tools, and AI infrastructure? Sponsor an upcoming edition of MCPnewsletter.

Send sponsorship inquiries to [contact@mcpnewsletter.com](mailto:contact@mcpnewsletter.com) with your product, launch, or campaign details.

# Getting started

1. Read the spec release candidate: [https://modelcontextprotocol.io/blog/2026-07-28-release-candidate](https://modelcontextprotocol.io/blog/2026-07-28-release-candidate)
2. Watch WorkOS MCP Night: [https://www.youtube.com/watch?v=a1jx0H4cSWk](https://www.youtube.com/watch?v=a1jx0H4cSWk)
3. Review the WorkOS MCP Night photo post: [/posts/workos-mcp-night-2026-highlights](/posts/workos-mcp-night-2026-highlights)
4. Test `mcpc`: [https://github.com/apify/mcpc](https://github.com/apify/mcpc)
5. Audit an MCP app with Beacon: [https://beacon.alpic.ai/](https://beacon.alpic.ai/)

## About MCPnewsletter

MCPnewsletter is a weekly briefing on Model Context Protocol tools, servers, apps, SDKs, registries, community projects, and practical implementation patterns.

Subscribe at: [https://mcpnewsletter.com](https://mcpnewsletter.com)

Contact: contact@mcpnewsletter.com
