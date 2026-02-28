# Content Writing Domain

Create high-quality content using AI with brand voice consistency, SEO optimization, and fact-checking.

---

## What's Included

- **5 Personas:** Content Strategist, Writer, SEO Specialist, Fact Checker, Editor
- **12 Prompts:** Organized across 4 phases (planning, creation, refinement, publishing)
- **3 Constitution Templates:** Blog, Marketing, Technical docs
- **1 Workflow Overview:** Linear workflow for content production

---

## Quick Start

### 1. Choose a Constitution Template

Pick a template from [`templates/`](./templates/) that matches your content type:

| Template | Best For | Key Focus |
|----------|----------|-----------|
| **[blog-constitution.md](./templates/blog-constitution.md)** | Company blogs, thought leadership | SEO, brand voice, readability |
| **[marketing-constitution.md](./templates/marketing-constitution.md)** | Landing pages, campaigns | Conversion, CTAs, brand alignment |
| **[technical-constitution.md](./templates/technical-constitution.md)** | Product docs, tutorials | Accuracy, clarity, code examples |

Copy the template to your project and customize it.

### 2. Start with Phase 1: Planning

Use the **[Content Brief prompt](./prompts/phase-1-planning/1.1-content-brief.md)** to create your content strategy.

**Give the prompt to your AI:**
- Claude Code, Cursor, or Replit (as a project prompt)
- Copy-paste into ChatGPT or Claude (for manual workflow)

**Output:** `artifacts/01-content-brief.md`

### 3. Follow the Workflow

See the [Workflow Overview](./workflow/workflow-overview.md) for the full process.

---

## Personas Overview

| # | Persona | Responsibility | When to Use |
|---|---------|----------------|-------------|
| 1 | **[Content Strategist](./personas/01-content-strategist.md)** | Topic selection, audience definition, content brief | Start of every content project |
| 2 | **[Content Writer](./personas/02-content-writer.md)** | First draft creation, storytelling, brand voice | After brief approved |
| 3 | **[SEO Specialist](./personas/03-seo-specialist.md)** | Keyword optimization, meta tags, readability | After draft created |
| 4 | **[Fact Checker](./personas/04-fact-checker.md)** | Verify claims, add citations, ensure accuracy | Before finalization |
| 5 | **[Editor](./personas/05-editor.md)** | Polish voice, flow, clarity, CTA effectiveness | Final review before publishing |

**[View All Persona Details →](./personas/)**

---

## Workflow Phases

### Phase 1: Planning
Define WHAT to write and WHO for (Content Strategist + SEO Specialist)

**Prompts:**
1. [1.1-content-brief.md](./prompts/phase-1-planning/1.1-content-brief.md) - Content strategy and brief
2. [1.2-keyword-research.md](./prompts/phase-1-planning/1.2-keyword-research.md) - SEO keyword research
3. [1.3-outline-creation.md](./prompts/phase-1-planning/1.3-outline-creation.md) - H2/H3 structure

**Outputs:** Content brief, keyword strategy, outline

---

### Phase 2: Creation
Write the first draft (Content Writer + Content Strategist)

**Prompts:**
1. [2.1-first-draft.md](./prompts/phase-2-creation/2.1-first-draft.md) - Create 1200-1800 word draft
2. [2.2-media-planning.md](./prompts/phase-2-creation/2.2-media-planning.md) - Identify image/video opportunities

**Outputs:** First draft, media plan

---

### Phase 3: Refinement
Optimize and polish (SEO Specialist + Fact Checker + Editor)

**Prompts:**
1. [3.1-seo-optimization.md](./prompts/phase-3-refinement/3.1-seo-optimization.md) - Optimize keywords, meta, readability
2. [3.2-fact-checking.md](./prompts/phase-3-refinement/3.2-fact-checking.md) - Verify claims and add citations
3. [3.3-editing.md](./prompts/phase-3-refinement/3.3-editing.md) - Polish voice, flow, clarity

**Outputs:** SEO report, fact-check report, edited final draft

---

### Phase 4: Publishing
Prepare for publication (SEO Specialist + Content Strategist)

**Prompts:**
1. [4.1-meta-optimization.md](./prompts/phase-4-publishing/4.1-meta-optimization.md) - Meta title, description, alt text
2. [4.2-distribution-checklist.md](./prompts/phase-4-publishing/4.2-distribution-checklist.md) - Distribution and promotion plan

**Outputs:** Meta tags, distribution checklist

---

## Workflow Type: Linear

Content writing uses a **linear workflow** with optional iteration:

```
┌─────────────────────────────────────────┐
│  Plan (Phase 1)                         │
│  Brief → Keywords → Outline             │
│  ↓                                       │
│  Create (Phase 2)                       │
│  First Draft → Media Plan               │
│  ↓                                       │
│  Refine (Phase 3)                       │
│  SEO → Fact-Check → Edit                │
│  ↓                                       │
│  Issues Found? → Iterate Draft          │
│  ↓                                       │
│  All Pass? → Publish (Phase 4)          │
│  Meta Tags → Distribution               │
└─────────────────────────────────────────┘
```

Unlike software (iterative), content moves linearly with targeted revisions as needed.

**[View Full Workflow Details →](./workflow/workflow-overview.md)**

---

## Common Workflows by Content Type

### Writing a Blog Post
1. **Content Strategist:** Create brief ([1.1-content-brief](./prompts/phase-1-planning/1.1-content-brief.md))
2. **SEO Specialist:** Research keywords ([1.2-keyword-research](./prompts/phase-1-planning/1.2-keyword-research.md))
3. **Content Strategist:** Build outline ([1.3-outline](./prompts/phase-1-planning/1.3-outline-creation.md))
4. **Writer:** Draft article ([2.1-first-draft](./prompts/phase-2-creation/2.1-first-draft.md))
5. **SEO Specialist:** Optimize ([3.1-seo-optimization](./prompts/phase-3-refinement/3.1-seo-optimization.md))
6. **Fact Checker:** Verify claims ([3.2-fact-checking](./prompts/phase-3-refinement/3.2-fact-checking.md))
7. **Editor:** Final polish ([3.3-editing](./prompts/phase-3-refinement/3.3-editing.md))
8. **SEO Specialist:** Meta tags ([4.1-meta-optimization](./prompts/phase-4-publishing/4.1-meta-optimization.md))

### Quick Social Media Post
1. **Content Strategist:** Brief (simplified)
2. **Writer:** Draft
3. **Editor:** Quick polish
4. Skip fact-checking if not needed
5. Publish

### Technical Documentation
1. **Content Strategist:** Define audience and scope
2. **Writer:** Create draft with code examples
3. **Fact Checker:** Verify technical accuracy
4. **Editor:** Clarity and readability
5. Skip SEO optimization (not search-focused)

---

## Tips for Success

### 1. Start with a Strong Brief
Your content brief should answer:
- **Who:** Target audience (demographics, pain points, search intent)
- **What:** Topic and angle (unique perspective)
- **Why:** Goals (traffic, leads, awareness, education)
- **How:** Format, length, tone, keywords

### 2. Version Your Drafts
Track iteration history:
```
artifacts/02-draft-v1.md  (first draft from writer)
artifacts/02-draft-v2.md  (after SEO optimization)
artifacts/02-draft-v3.md  (after fact-check corrections)
artifacts/02-draft-v4.md  (final after editing)
```

### 3. Use Cross-Persona Dialogue
Document feedback in the artifact or workflow-log:
```markdown
## SEO Specialist → Writer (Draft v1 Review)
> **Issue:** Primary keyword "project management software" only appears 3 times
> **Recommendation:** Add 2-3 more natural mentions in H2 sections
> **Impact:** MEDIUM - Would improve search ranking

## Writer Response
> ✅ Added keyword to sections 2.3 and 4.1
> ✅ Maintained natural flow
> ✅ Updated to draft-v2.md
```

### 4. Fact-Check Everything
For credibility:
- Add citations for statistics and claims
- Link to authoritative sources
- Verify dates, numbers, quotes
- Flag anything that can't be verified

### 5. Optimize for Readability
Not just SEO:
- Short paragraphs (<150 words)
- Bullet points and lists
- Clear headings (H2, H3)
- Strong hook in first 100 words
- Clear CTA at the end

---

## Quality Metrics

### SEO Score (Target: 85/100)
- Primary keyword in title, H1, first 100 words
- Secondary keywords in H2s
- Meta description 150-160 characters
- Image alt text includes keywords
- Internal links (3-5)
- External links to authoritative sources (2-3)
- Readability score >60 (Flesch Reading Ease)

### Brand Voice Alignment
- Tone matches constitution (professional, casual, technical)
- Vocabulary is appropriate for audience
- No jargon unless audience expects it
- CTAs align with brand goals

### Fact-Checking
- All statistics cited
- All claims verifiable
- Dates and numbers accurate
- No plagiarism
- Citations formatted consistently

### Engagement
- Compelling headline
- Hook in first paragraph
- Clear structure with subheadings
- Visual content planned
- Strong CTA

---

## Customization Ideas

### Add a Persona: Brand Voice Specialist
For companies with strict brand guidelines, add a persona that checks every draft for brand compliance before editing.

### Merge Personas: Writer + Editor
For smaller projects or tighter deadlines, combine writing and editing into one persona with a two-pass workflow.

### Add a Phase: Design/Visual
For visual-heavy content (infographics, video scripts), add a design phase between drafting and refinement.

### Skip Personas: Fact Checker
For opinion pieces or personal blogs, fact-checking might not be needed. Skip this persona.

---

## Questions?

- **[Quick Start](../../QUICKSTART.md)** - 5-minute guide to get started
- **[Working Solo](../../docs/guides/working-solo.md)** - Using personas as a solo content creator
- **[Working with Teams](../../docs/guides/working-with-teams.md)** - Team collaboration strategies
- **[Customizing Personas](../../docs/guides/customizing-personas.md)** - Adapt personas for your needs

---

**Ready to start?** → Pick a [constitution template](./templates/), then use your first [prompt](./prompts/)!
