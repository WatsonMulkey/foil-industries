---
title: 'Why "NEVER Do X" Fails With LLMs'
description: 'A counterintuitive lesson from building AI-powered applications: prompt instructions are suggestions, not constraints.'
pubDate: 2026-02-03
author: 'Watson Mulkey'
tags: ['AI Engineering', 'LLM', 'Architecture', 'Lessons Learned']
featured: true
draft: false
---

# Why "NEVER Do X" Fails With LLMs

We recently discovered something counterintuitive while building an AI-powered resume generator: **LLMs ignore advisory instructions.** No matter how emphatically you tell them "NEVER do X," they'll occasionally do X anyway.

## The Problem

Our application generates tailored resumes from a user's career data. It pulls achievements, skills, and job history, then asks an LLM to craft compelling bullet points matched to a target job description.

The prompt clearly stated: "NEVER attribute achievements from one job to another. Each bullet point must only reference accomplishments from that specific role."

The LLM did it anyway. Achievements from one employer appeared under a different company. A 32% efficiency improvement at Company A showed up in the Company B section.

We tried everything prompt engineers typically try:
- Adding "CRITICAL:" and "IMPORTANT:" prefixes
- Using caps lock for emphasis
- Repeating the instruction multiple times
- Adding examples of what NOT to do

None of it worked reliably. The model treated these instructions as suggestions, not constraints. It wasn't being malicious—it was doing what LLMs do: generating plausible-sounding text based on patterns, without true understanding of our rules.

## The Fix

The solution wasn't better prompts. It was better architecture.

Instead of showing the LLM all career data simultaneously and asking it to keep things separate, we restructured the entire generation pipeline:

**1. Isolate context per entity.** Generate bullet points for each job independently. When creating content for Company A, the LLM only sees Company A's data. It literally cannot reference Company B's achievements because that information isn't in the context window.

**2. Assemble after generation.** Once we have pre-generated, correctly-attributed bullets for each job, we combine them into the final resume. The assembly step uses the LLM for formatting and flow, but the attribution is already locked in.

**3. Validate post-generation.** We added a validation pass that cross-checks every claim in the output against the source data. If a metric appears in the wrong section, we catch it.

The results were immediate. Misattribution dropped from a recurring problem to essentially zero. The LLM can't misattribute data it never sees.

## The Broader Pattern

This lesson applies far beyond resume generation. Any time you need an LLM to maintain strict boundaries between data sources, **architecture beats prompting.**

Consider RAG (Retrieval-Augmented Generation) systems. When you retrieve five document chunks and ask the LLM to cite sources correctly, it can easily cite Source [1] for information that actually came from Source [3]. The fix is the same: generate responses per-source first, then synthesize.

The same principle applies to multi-tenant systems where user data must stay isolated, chatbots that shouldn't leak conversation context, or any scenario requiring strict data boundaries.

## The Takeaway

When building LLM-powered applications, don't rely on instructions to prevent unwanted behavior. Design systems where the unwanted behavior is **structurally impossible.**

Prompts are suggestions. Architecture is constraint.

---

*Building AI-powered tools and running into similar challenges? [Reach out](mailto:watson@foil.industries)—we'd love to compare notes.*
