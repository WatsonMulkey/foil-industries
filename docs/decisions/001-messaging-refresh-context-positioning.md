# ADR-001: Messaging Refresh — "Context" Positioning

## Status

Accepted

## Context

FOIL's original site copy ("Solving problems, not just building solutions") was generic and didn't differentiate from other consultancies. Inspired by the Karpathy "bespoke software era" tweet, Watson identified a sharper positioning: the real problem isn't that client problems are unique — it's that their **context** (team size, budget, legacy systems, niche workflows) makes off-the-shelf tools a poor fit.

Additionally, the original copy leaned heavily into tooling/building, when a significant portion of Watson's work (e.g., Bookshop.org) involves process design, teaching teams to think about problems, and organizational change — no custom software required.

## Options Considered

1. **AI-native lead** — Position FOIL primarily as an AI-powered development shop. Fast, modern, technical.
2. **Context-first with AI as one capability** — Lead with the diagnostic skill (figuring out what fits), position AI-native development as the accelerant when software is the answer, but make clear that sometimes the answer is process change.
3. **Pure consulting positioning** — Drop the tooling angle, focus on product strategy and process.

## Decision

**Option 2: Context-first with AI as one capability.** The hero leads with "Your context changes the right answer" and asks qualifying questions (Small team? Tight budget?). The About section explicitly names both paths: process/people work AND custom tooling. AI-native development is positioned as what makes Watson's tooling fast, but product experience is what makes it right.

Key copy decisions:
- Removed the hero support line entirely — it kept trying to do too much
- Changed "WHAT WE DO" eyebrow to "HOW I WORK" — positions services as an approach, not a catalog
- Bespoke Tooling tagline: "Off-the-shelf software was built for someone else's context" — names the problem using the hero's "context" language
- Contact note broadened to "product consulting, process design, and bespoke tooling" — equal billing

## Consequences

- Positions FOIL for both tooling AND consulting engagements (broader funnel)
- "Context" becomes a recurring word/concept across the site — thematic coherence
- AI capabilities are visible but not the entire identity — avoids competing with pure vibe-coders
- The single-page architecture limits SEO potential (one URL, one title tag) — may need to revisit with multi-page structure later
- Added JSON-LD structured data (Organization + Service schemas) and llms.txt for AI search visibility
