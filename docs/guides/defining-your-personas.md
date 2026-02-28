# Defining Your Personas

**A practical guide to discovering the specialized agents your workflow needs**

---

## What Are Personas?

In the AI Workflow Orchestrator, **personas** are specialized AI agents, each with:
- **One clear responsibility** (separation of concerns)
- **Specific inputs** (artifacts from previous agents)
- **Concrete outputs** (artifacts for next agents)
- **Domain expertise** (deep knowledge in one area)
- **Phase assignment** (r, K, Ω, or α from the adaptive cycle)

**Think of personas like specialized team members:**
- Each has their own expertise
- Each checks the others' work
- Each follows the same constitution (governance rules)
- Each creates reviewable artifacts

---

## Why Personas Matter

### Without Personas (Traditional AI)
```
You: "Write a blog post about AI safety"
AI: [3000 words of generic content]
You: "This doesn't match our brand voice"
AI: [Rewrites everything]
You: "The research is weak"
AI: [Rewrites again]
```

**Problem:** One generalist doing everything leads to:
- Context switching reduces quality
- No specialized expertise
- Hard to iterate methodically
- No built-in quality checks

### With Personas (Orchestrated Workflow)
```
Strategist: "Here's the unique angle and audience"
You: "Approved. Next."

Researcher: "Here are verified facts and sources"
You: "Good. Next."

Writer: "Here's the draft following strategy and using research"
You: "Approved. Next."

Editor: "Found 3 voice violations, fixing..."
Critic: "Quality score: 87/100. Approved for publication."
```

**Benefit:** Specialized agents working sequentially:
- Each focuses on their expertise
- Built-in quality checks
- Methodical iteration
- Transparent process

---

## Discovery Process

### Step 1: Map Your Current Process (10 minutes)

Write down your current workflow as **verbs** (actions):

**Example: Content Writing**
```
Brainstorm → Research → Outline → Write → Edit → Review → Publish
```

**Example: Software Development**
```
Plan → Design → Code → Test → Review → Deploy → Monitor
```

**Example: Product Design**
```
Research → Define → Sketch → Prototype → Test → Refine → Deliver
```

**Your workflow:**
```
___________ → ___________ → ___________ → ___________ → ___________
```

---

### Step 2: Identify Natural Breakpoints (10 minutes)

Where do you currently:
- **Switch contexts** (research mode → writing mode)
- **Change mindsets** (creative → critical)
- **Review work** before continuing
- **Make decisions** that affect downstream work
- **Hand off** to another person/role

**These breakpoints often indicate persona boundaries.**

**Example: Content Writing**
- After research, **review** before outlining
- After outline, **approve structure** before writing
- After draft, **switch to editor mindset**
- After editing, **critical review** for publication

**Mark your breakpoints:**
```
Verb 1 → [REVIEW?] → Verb 2 → [DECISION?] → Verb 3 → [SWITCH CONTEXT?] → Verb 4
```

---

### Step 3: Map to Adaptive Cycle Phases (15 minutes)

For each activity, identify its phase:

#### r-phase (Growth/Exploitation)
**Characteristics:** Exploratory, divergent, fast, gathering

**Questions:**
- Does this activity explore options?
- Does it gather information/resources?
- Is breadth more important than depth here?
- Is uncertainty high?

**Common r-phase personas:**
- Strategist, Researcher, Scout, Analyst, Planner, Requirements Gatherer

---

#### K-phase (Conservation)
**Characteristics:** Structured, convergent, efficient, building

**Questions:**
- Does this activity build/create the main deliverable?
- Does it refine and optimize?
- Is depth more important than breadth here?
- Is the path clearly defined?

**Common K-phase personas:**
- Architect, Builder, Writer, Developer, Editor, Designer, QA, Tester

---

#### Ω-phase (Release/Critique)
**Characteristics:** Evaluative, adversarial, gate-keeping

**Questions:**
- Does this activity evaluate "should this exist?"
- Does it score quality objectively?
- Does it have veto power?
- Is the mindset adversarial/critical?

**Common Ω-phase personas:**
- Critic, Reviewer, Auditor, Red Team, Judge, Quality Gate

---

#### α-phase (Reorganization)
**Characteristics:** Meta, evolutionary, learning, strategic

**Questions:**
- Does this activity learn from failures?
- Does it update the system itself?
- Does it prevent recurring mistakes?
- Is it triggered only on significant failures?

**Common α-phase personas:**
- Evolutionist, Retrospective Lead, System Architect, Learning Officer, Process Improver

---

### Step 4: Define Each Persona (30 minutes)

For each persona you've identified, fill out this template:

```yaml
---
persona:
  id: "[lowercase-hyphenated]"
  name: "[Proper Name]"
  number: "[01-99]"  # For artifact naming
  phase: "[r|K|omega|alpha]"

role:
  primary: "One sentence: what is this persona's job?"
  analogy: "[Real-world role, e.g., 'Product Owner', 'QA Engineer']"
  cannot_do: "What is explicitly NOT this persona's job?"

inputs:
  required:
    - "artifact-name-1"
    - "artifact-name-2"
  optional:
    - "artifact-name-3"

outputs:
  - name: "artifact-name"
    description: "What this artifact contains"
    schema: "path/to/template.md"

expertise:
  - "Domain knowledge area 1"
  - "Domain knowledge area 2"

constraints:
  - "Rule this persona must follow"
  - "Explicit limitation on behavior"

memory_access:
  read: ["context", "memory", "project_learnings", "constitution"]
  write: ["context", "memory"]

checkpoints:
  human_review: "[required|optional|none]"
  review_focus: "What should humans look for?"

characteristics:
  skippable: "[true|false]"
  is_gate: "[true|false]"  # Ω-phase only
  is_evolutionary: "[true|false]"  # α-phase only
---
```

**Example: Content Strategist**

```yaml
---
persona:
  id: "strategist"
  name: "Content Strategist"
  number: "01"
  phase: "r"

role:
  primary: "Define WHAT to create and WHY it matters"
  analogy: "Product Owner"
  cannot_do: "Does NOT write content, research facts, or create structure"

inputs:
  required:
    - "user-brief"  # Initial requirements
  optional:
    - "constitution"

outputs:
  - name: "content-brief"
    description: "Strategic direction, audience, unique angle (UVP)"
    schema: "templates/content-brief-template.md"

expertise:
  - "Content strategy"
  - "Audience analysis"
  - "Competitive differentiation"
  - "SEO and discoverability"

constraints:
  - "Must ask clarifying questions if requirements are vague"
  - "Must define unique angle (UVP) to differentiate from competition"
  - "Must profile target audience explicitly"

memory_access:
  read: ["context", "project_learnings", "constitution"]
  write: ["context", "memory"]

checkpoints:
  human_review: "required"
  review_focus: "Is the angle unique? Is the audience well-defined?"

characteristics:
  skippable: false
  is_gate: false
  is_evolutionary: false
---
```

---

### Step 5: Validate Your Persona Set (10 minutes)

#### Completeness Checklist
- [ ] All work phases covered
- [ ] Clear input/output chain (each persona's outputs feed the next)
- [ ] No overlap in responsibilities
- [ ] Quality gates defined (at least one Ω-phase persona)
- [ ] Learning mechanism exists (at least one α-phase persona)

#### Separation of Concerns Checklist
- [ ] Each persona has ONE primary job
- [ ] No persona does both creation AND critique
- [ ] Research ≠ Writing ≠ Editing ≠ Quality Scoring
- [ ] Different mindsets separated (creative vs. critical)

#### Adaptive Cycle Coverage
- [ ] At least one r-phase persona (exploration)
- [ ] At least one K-phase persona (creation)
- [ ] At least one Ω-phase persona (evaluation)
- [ ] At least one α-phase persona (evolution)

#### Flow Validation
Can you trace a path from user input to final output?
```
User input → [r-phase personas] → [K-phase personas] → [Ω-phase gate] → Complete
                                                               ↓ (if failure)
                                              [α-phase] → Loop back to r-phase
```

---

## Common Patterns by Domain

### Content Creation (Writing, Design, Video)

**Minimum viable (3 personas):**
- **Writer** (K-phase) - Creates content
- **Critic** (Ω-phase) - Scores quality
- **Evolutionist** (α-phase) - Learns from failures

**Standard (5 personas):**
- **Strategist** (r-phase) - Defines angle and audience
- **Architect** (K-phase) - Structures content
- **Writer** (K-phase) - Creates draft
- **Editor** (K-phase) - Validates and refines
- **Critic** (Ω-phase) - Quality gate

**Advanced (7 personas):**
- Add **Researcher** (r-phase) for fact-gathering
- Add **Evolutionist** (α-phase) for system learning

---

### Software Development

**Minimum viable (3 personas):**
- **Developer** (K-phase) - Writes code
- **Reviewer** (Ω-phase) - Code review
- **Learner** (α-phase) - Updates standards

**Standard (5 personas):**
- **Product Owner** (r-phase) - Defines requirements
- **Architect** (K-phase) - Technical design
- **Developer** (K-phase) - Implementation
- **Tester** (K-phase) - Quality validation
- **Reviewer** (Ω-phase) - Code review gate

**Advanced (7+ personas):**
- Add **Requirements Analyst** (r-phase)
- Add **Security Auditor** (Ω-phase)
- Add **Technical Writer** (K-phase)

---

### Product Design

**Standard (5 personas):**
- **User Researcher** (r-phase) - Research needs
- **Problem Framer** (r-phase) - Define problem
- **Designer** (K-phase) - Create solutions
- **Prototyper** (K-phase) - Build mockups
- **Usability Tester** (Ω-phase) - Validate design

**Advanced (7 personas):**
- Add **Design System Maintainer** (α-phase)
- Add **Accessibility Auditor** (Ω-phase)

---

### Scientific Research

**Standard (5 personas):**
- **Literature Reviewer** (r-phase) - Review existing research
- **Hypothesis Generator** (r-phase) - Formulate hypotheses
- **Experimental Designer** (K-phase) - Design experiments
- **Data Analyst** (K-phase) - Analyze results
- **Peer Reviewer** (Ω-phase) - Critical evaluation

---

## Example: Building a Code Review Workflow

### Starting Point
**Current process:**
```
Write code → Self-review → Submit PR → Wait for review → Fix issues → Merge
```

### Breakpoints Identified
- Before PR submission (self-check)
- During review (critical evaluation)
- After feedback (learning)

### Mapped to Adaptive Cycle

**r-phase (Planning):**
- **Planner** - Analyzes requirements, creates implementation strategy

**K-phase (Creation):**
- **Developer** - Writes code following plan
- **Self-Reviewer** - Pre-submission quality check (linting, tests)

**Ω-phase (Critique):**
- **Code Critic** - Reviews for bugs, style, architecture
- **Security Auditor** - Checks for vulnerabilities

**α-phase (Learning):**
- **Pattern Learner** - Extracts lessons from repeated issues, updates coding standards

### Resulting Workflow
```
Planner → Developer → Self-Reviewer → Code Critic → Security Auditor
  ↓ (if critical issues found by Security Auditor)
Pattern Learner → Update coding standards → Next PR starts with learnings
```

---

## Starter Templates by Complexity

### Minimal (3 personas) - ~1-2 hours per project
**Use for:** Simple, straightforward work

```
Creator (K) → Reviewer (Ω) → Learner (α)
```

**Example domains:**
- Quick blog posts
- Simple code changes
- Basic design mockups

---

### Standard (5 personas) - ~2-4 hours per project
**Use for:** Most professional work

```
Strategist (r) → Creator (K) → Validator (K) → Critic (Ω) → Evolutionist (α)
```

**Example domains:**
- Professional blog posts
- Feature development
- Product design sprints

---

### Advanced (7+ personas) - ~4-8 hours per project
**Use for:** High-stakes, complex work

```
Strategist (r) → Researcher (r) → Architect (K) → Creator (K) →
Validator (K) → Critic (Ω) → Auditor (Ω) → Evolutionist (α)
```

**Example domains:**
- Long-form content (whitepapers)
- Major feature development
- Complex design systems

---

## Anti-Patterns to Avoid

### ❌ Too Many Personas
**Symptom:** More than 10 personas
**Problem:** Suggests lack of clarity, over-complication
**Fix:** Consolidate overlapping responsibilities

### ❌ Overlapping Responsibilities
**Symptom:** Two personas do the same thing
**Problem:** Redundant work, unclear ownership
**Fix:** Merge personas or clarify distinct responsibilities

### ❌ Creator Also Critiques
**Symptom:** Same persona builds and judges
**Problem:** Conflict of interest, reduced objectivity
**Fix:** Separate K-phase creators from Ω-phase critics

### ❌ Missing Quality Gates
**Symptom:** No Ω-phase persona
**Problem:** No objective evaluation before shipping
**Fix:** Add at least one Ω-phase critic

### ❌ No Learning Mechanism
**Symptom:** No α-phase persona
**Problem:** Same mistakes repeat forever
**Fix:** Add evolutionist persona triggered on failures

### ❌ Generic "AI Assistant"
**Symptom:** Persona description is vague
**Problem:** Not specialized enough
**Fix:** Define specific expertise and constraints

---

## Testing Your Personas

### Dry Run Test
1. Pick a real project
2. Run through your workflow manually
3. At each persona, ask:
   - Do I have clear inputs?
   - Is my responsibility clear?
   - Can I produce the expected output?
   - Is there overlap with other personas?

### Input/Output Chain Test
Can you trace artifacts from start to finish?
```
user-input.md → persona-1 → artifact-1.md → persona-2 → artifact-2.md → ... → final-output.md
```

### Failure Test
What happens if quality is poor?
- Does Ω-phase catch it?
- Does α-phase learn from it?
- Does the next cycle improve?

---

## Iteration and Refinement

Your personas will evolve. Common adjustments:

**Add specificity:**
- "Editor" → "Voice Editor" + "Fact-Checker"

**Merge redundancy:**
- "Researcher" + "Fact Finder" → "Investigator"

**Split complexity:**
- "Developer" → "Backend Developer" + "Frontend Developer"

**Adjust phases:**
- Move "Tester" from Ω-phase to K-phase (validation not critique)

---

## Next Steps

Once you've defined your personas:

1. **Create agent configs** using [templates/agents/agent-template.yaml](../templates/agents/agent-template.yaml)
2. **Write prompts** for each persona (see [examples/](../examples/) for reference)
3. **Define workflow** using [templates/workflows/workflow-template.yaml](../templates/workflows/workflow-template.yaml)
4. **Test with real project**
5. **Iterate based on learnings**

---

## Related Resources

- **[Core: Adaptive Cycle Framework](../core/adaptive-cycle-framework.md)** - Understanding r→K→Ω→α phases
- **[Guide: Mapping Adaptive Cycles](./mapping-adaptive-cycles.md)** - Map your domain to phases
- **[Guide: Creating Quality Gates](./creating-quality-gates.md)** - Design Ω-phase scoring
- **[Examples](../examples/)** - Reference implementations by domain

---

*Need help defining your personas? Open an issue or discussion on GitHub.*
