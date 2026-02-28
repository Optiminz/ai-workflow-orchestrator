# Content Writing Workflow Overview

This document provides a visual overview of the content writing workflow, showing how personas collaborate across 4 phases to produce high-quality content.

---

## Workflow Type: Linear

Content writing follows a **linear workflow** with targeted iteration as needed:

```
┌─────────────────────────────────────────────────────────────┐
│                    PHASE 1: PLANNING                        │
│  Define topic, audience, keywords, and outline             │
├─────────────────────────────────────────────────────────────┤
│  Content Strategist:                                        │
│    1.1 → Content Brief (topic, audience, goals, angle)     │
│    1.2 → Keyword Research (primary + secondary keywords)   │
│    1.3 → Content Outline (H2/H3 structure)                 │
│                                                             │
│  Output: Brief, keyword strategy, outline                  │
│  Gate: ✅ Brief approved → Advance to Phase 2             │
└─────────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────────┐
│                    PHASE 2: CREATION                        │
│  Write first draft following approved outline              │
├─────────────────────────────────────────────────────────────┤
│  Content Writer:                                            │
│    2.1 → First Draft (1,200-1,800 words, brand voice)     │
│                                                             │
│  Content Strategist:                                        │
│    2.2 → Media Planning (images, videos, infographics)     │
│                                                             │
│  Output: Draft v1, media plan                              │
│  Gate: ✅ Draft complete → Advance to Phase 3             │
└─────────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────────┐
│                  PHASE 3: REFINEMENT                        │
│  Optimize, verify, and polish                              │
├─────────────────────────────────────────────────────────────┤
│  SEO Specialist:                                            │
│    3.1 → SEO Optimization (keywords, readability, meta)    │
│    Output: Draft v2 (optimized)                            │
│                                                             │
│  Fact Checker:                                              │
│    3.2 → Fact-Checking (verify claims, add citations)      │
│    Output: Draft v3 (verified)                             │
│                                                             │
│  Editor:                                                    │
│    3.3 → Editing (voice, flow, grammar, CTA)               │
│    Output: Draft v4-FINAL (publication-ready)              │
│                                                             │
│  Gate: ✅ All issues resolved → Advance to Phase 4        │
└─────────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────────┐
│                   PHASE 4: PUBLISHING                       │
│  Prepare for publication and distribution                  │
├─────────────────────────────────────────────────────────────┤
│  SEO Specialist:                                            │
│    4.1 → Meta Optimization (title, description, alt text)  │
│                                                             │
│  Content Strategist:                                        │
│    4.2 → Distribution Checklist (promotion plan)           │
│                                                             │
│  Output: Meta tags, distribution plan                      │
│  Gate: ✅ Ready to publish → PUBLISH                      │
└─────────────────────────────────────────────────────────────┘
```

---

## Persona Responsibilities by Phase

| Phase | Persona | Responsibility | Output |
|-------|---------|----------------|--------|
| **1** | Content Strategist | Topic, audience, keywords, outline | Brief, keyword strategy, outline |
| **2** | Content Writer | First draft with brand voice | Draft v1 |
| **2** | Content Strategist | Media planning | Media plan |
| **3** | SEO Specialist | Keyword optimization, readability | Draft v2 + SEO report |
| **3** | Fact Checker | Verify claims, add citations | Draft v3 + fact-check report |
| **3** | Editor | Polish voice, flow, grammar | Draft v4-FINAL + editing report |
| **4** | SEO Specialist | Meta tags, alt text | Meta tags document |
| **4** | Content Strategist | Distribution plan | Distribution checklist |

---

## Iteration Points

While the workflow is linear, iteration happens within phases:

```
Draft v1 → SEO Review → Draft v2 → Fact Check → Draft v3 → Edit → Draft v4-FINAL
     ↑_____________↓              ↑__________↓           ↑______↓
     (If major SEO issues)       (If facts need fixing) (If clarity issues)
```

**When to iterate:**
- **After SEO review:** If keyword density is off or readability is low
- **After fact-checking:** If claims can't be verified or errors found
- **After editing:** If tone is inconsistent or grammar needs fixes

**When NOT to iterate:**
- Don't go back to Phase 1 (brief) unless the topic is fundamentally wrong
- Don't skip phases (e.g., publishing before fact-checking)

---

## Artifact Flow

```
artifacts/
  ├── 01-content-brief.md          (Content Strategist, Phase 1)
  ├── 01-keyword-strategy.md       (SEO Specialist, Phase 1)
  ├── 01-content-outline.md        (Content Strategist, Phase 1)
  ├── 02-draft-v1.md               (Content Writer, Phase 2)
  ├── 02-media-plan.md             (Content Strategist, Phase 2)
  ├── 03-seo-report.md             (SEO Specialist, Phase 3)
  ├── 02-draft-v2.md               (After SEO optimization)
  ├── 04-fact-check-report.md      (Fact Checker, Phase 3)
  ├── 02-draft-v3.md               (After fact-checking)
  ├── 05-editing-report.md         (Editor, Phase 3)
  ├── 02-draft-v4-FINAL.md         (Publication-ready)
  ├── 06-meta-tags.md              (SEO Specialist, Phase 4)
  └── 07-distribution-checklist.md (Content Strategist, Phase 4)
```

**Key Pattern:** Each persona produces a reviewable artifact, not just verbal feedback.

---

## Quality Gates

Each phase has a gate that must pass before advancing:

### Phase 1 Gate: Strategy Approved
- [ ] Topic is clearly defined
- [ ] Audience is specific (not "everyone")
- [ ] Keywords are realistic (achievable competition)
- [ ] Outline logically serves audience
- [ ] Stakeholder/lead approves brief

### Phase 2 Gate: Draft Complete
- [ ] Word count target met (within 10%)
- [ ] Follows approved outline structure
- [ ] Brand voice is consistent
- [ ] All sections from outline covered
- [ ] CTA is included

### Phase 3 Gate: Quality Standards Met
- [ ] SEO: Keyword density 1-2%, readability >60
- [ ] Facts: All claims verified or removed
- [ ] Editing: No grammar errors, voice consistent
- [ ] No CRITICAL issues remaining
- [ ] Draft is publication-ready

### Phase 4 Gate: Ready to Publish
- [ ] Meta tags created and compelling
- [ ] All images have alt text
- [ ] Distribution plan created
- [ ] CMS/publishing platform ready
- [ ] Final approval given

---

## Timeline Estimates

**Typical timeline for 1,800-word blog post:**

| Phase | Time Estimate | Can Run in Parallel? |
|-------|---------------|----------------------|
| Phase 1: Planning | 1-2 hours | No (sequential) |
| Phase 2: Creation | 2-3 hours | Media plan can start after draft starts |
| Phase 3: Refinement | 2-3 hours | SEO, Fact-check, Edit run sequentially |
| Phase 4: Publishing | 30 minutes | Both tasks quick |
| **Total** | **6-9 hours** | With iteration: 8-12 hours |

**Faster workflow for shorter content (e.g., 500-word post):**
- Phase 1: 30 minutes
- Phase 2: 1 hour
- Phase 3: 1-2 hours
- Phase 4: 20 minutes
- **Total:** 3-4 hours

---

## Solo Practitioner Workflow

When working alone, you invoke each persona sequentially:

```
1. You as Content Strategist → Create brief
2. You review brief → Approve or iterate
3. You as Content Writer → Create draft
4. You as SEO Specialist → Review and optimize
5. You as Fact Checker → Verify claims
6. You as Editor → Final polish
7. You as Content Strategist → Plan distribution
8. Publish!
```

**Key insight:** Each persona gives you a different perspective. When you switch personas, you're checking your own work from a different angle.

---

## Team Workflow

When working with a team, assign personas to people:

### Option 1: Full Team
- **Person A:** Content Strategist (planning + distribution)
- **Person B:** Content Writer (drafting)
- **Person C:** SEO Specialist (optimization + meta tags)
- **Person D:** Fact Checker (verification)
- **Person E:** Editor (final polish)

### Option 2: Small Team (2-3 people)
- **Person A:** Strategist + Writer (Phases 1-2)
- **Person B:** SEO + Fact Checker (Phase 3)
- **Person C:** Editor (Phase 3) + Distribution (Phase 4)

### Option 3: Solo + AI
- **You:** Strategic decisions, approval gates
- **AI:** Execute each persona's tasks
- **You:** Review each persona's output, accept/reject

---

## Cross-Persona Dialogue Example

```markdown
## SEO Specialist → Content Writer (After Phase 3.1)

> **Issue (Line 234):** Primary keyword appears 12 times (2.8% density).
> Target is 1-2%. Recommend removing 4-6 instances.
>
> **Priority:** HIGH
>
> **Specific instances to remove:**
> - Line 234: Remove from this paragraph
> - Line 567: Use "PM tools" variation instead
> - Line 789: Not needed in conclusion

## Content Writer Response

> ✅ Removed 5 instances (lines 234, 567, 789, 890, 1023)
> ✅ Keyword density now 1.5% (acceptable)
> ✅ Updated draft to v2
> ✅ Ready for Fact Checker

## Fact Checker → Content Writer (After Phase 3.2)

> **Issue (Line 456):** Claim "Most startups abandon PM tool in 6 months"
> cannot be verified. No authoritative source found.
>
> **Priority:** CRITICAL
>
> **Recommendation:** Either remove claim or soften to "Many startups
> frequently switch PM tools in their first year" (more defensible)

## Content Writer Response

> ✅ Softened claim to recommended wording
> ✅ Updated draft to v3
> ✅ Ready for Editor
```

This dialogue is documented in `artifacts/workflow-log.md` or inline in the reports.

---

## Common Workflow Patterns

### Pattern 1: SEO-First Content
```
Heavy focus on keyword research and optimization
Best for: Traffic-focused content, competitive keywords
Extra time in: Phase 1 (keyword research) + Phase 3 (SEO optimization)
```

### Pattern 2: Thought Leadership
```
Light SEO, heavy on unique insights and voice
Best for: Brand awareness, executive content
Extra time in: Phase 1 (angle development) + Phase 3 (editing for voice)
Skip: Keyword stuffing, aggressive SEO tactics
```

### Pattern 3: Fast-Turnaround Content
```
Simplified workflow, merge some personas
Best for: News, updates, time-sensitive content
Shortcuts: Combine SEO + Editing, skip fact-checking if opinion-based
Timeline: 2-3 hours instead of 6-9
```

### Pattern 4: High-Stakes Content
```
Extra rigor, more review cycles
Best for: Whitepapers, research, compliance-heavy industries
Extra phases: Legal review, subject matter expert review, multiple editing passes
Timeline: 12-20 hours
```

---

## Success Criteria

### Phase 1 Success
- Clear, specific brief with realistic keywords
- Outline serves audience journey
- Stakeholders aligned on direction

### Phase 2 Success
- Engaging draft that follows outline
- Brand voice is consistent
- CTA is clear and compelling

### Phase 3 Success
- SEO optimized (keywords, readability, meta)
- Facts verified with citations
- No grammar errors, voice polished

### Phase 4 Success
- Meta tags entice clicks
- Distribution plan maximizes reach
- Content is published and promoted

---

## Tools & Resources

**Planning (Phase 1):**
- Keyword research: Ahrefs, SEMrush, Google Keyword Planner
- Audience research: Google Analytics, surveys, interviews
- Competitive analysis: Ahrefs, BuzzSumo

**Creation (Phase 2):**
- Writing: Google Docs, Notion, Markdown editor
- Grammar: Grammarly, Hemingway Editor
- Visuals: Canva, Unsplash, Figma

**Refinement (Phase 3):**
- SEO: Yoast, Surfer SEO, Clearscope
- Readability: Hemingway Editor, Grammarly
- Fact-checking: Google Scholar, original sources, industry reports

**Publishing (Phase 4):**
- CMS: WordPress, Webflow, Ghost, Medium
- Analytics: Google Analytics, Search Console
- Distribution: Buffer, Hootsuite, Mailchimp

---

## Next Steps

1. **Choose a constitution template** from `templates/` (blog, marketing, or technical)
2. **Start with Phase 1** using the [Content Brief prompt](../prompts/phase-1-planning/1.1-content-brief.md)
3. **Follow the workflow** through all 4 phases
4. **Track your artifacts** in the artifacts/ folder
5. **Iterate as needed** but maintain the phase structure

**Ready to start?** → [Phase 1: Content Brief](../prompts/phase-1-planning/1.1-content-brief.md)
