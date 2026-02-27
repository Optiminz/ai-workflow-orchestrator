# Constitution: [PRODUCT_NAME] Technical Documentation

**Type:** Technical Documentation / Tutorials / API Guides
**Created:** [CONSTITUTION_DATE — YYYY-MM-DD]
**Last Updated:** [CONSTITUTION_DATE — YYYY-MM-DD]

---

## Project Overview

**Documentation Type:** [DOCUMENTATION_TYPE — e.g., API documentation, product docs, technical tutorials]

**Purpose:** [DOCUMENTATION_PURPOSE — One paragraph describing what your documentation covers and who uses it]

**Example:**
```
Purpose: Technical documentation for our API and developer tools.
Audience includes developers integrating our platform, internal engineers,
and technical partners. Focus on accuracy, clarity, and complete code examples.
```

---

## Core Principles

**Remember:** Technical documentation prioritizes accuracy and usability:

1. **Accuracy first** - Incorrect documentation is worse than no documentation
2. **Show, don't just tell** - Every concept needs a code example
3. **Assume nothing** - Explain prerequisites, environment setup, versions
4. **Keep it current** - Update docs with every product change
5. **Test everything** - All code examples must be tested and working

---

## Brand Voice & Tone

### Voice
**Choose one:**
- [ ] Formal & precise (academic, detailed, no ambiguity)
- [ ] Clear & instructional (teacher-like, step-by-step, patient)
- [ ] Conversational & developer-friendly (casual, relatable, practical)

**Your choice:**
```
Voice: Clear & instructional with developer-friendly tone
- Use "you" (second person)
- Technical accuracy but approachable language
- Assume reader is competent but may be new to this specific tool
- Use active voice ("Configure the API" not "The API can be configured")
```

### Tone by Documentation Type
```
API reference: Precise, concise, structured (reference material)
Tutorials: Patient, step-by-step, encouraging (learning material)
Quickstarts: Fast-paced, minimal explanation (get started quickly)
Troubleshooting: Problem-solving, diagnostic, solution-oriented
```

---

## Target Audience

**Primary Audience:**
```
Role: [AUDIENCE_ROLE — e.g., Backend developers]
Experience level: [AUDIENCE_EXPERIENCE — e.g., 2-5 years, comfortable with REST APIs]
Tech stack: [AUDIENCE_TECH_STACK — e.g., Node.js, Python, or Ruby]
Goal: [AUDIENCE_GOAL — e.g., Integrate our API into their application]
Common blockers: [AUDIENCE_COMMON_BLOCKERS — e.g., Authentication, webhook setup, error handling]
```

**Secondary Audience (if applicable):**
```
[e.g., "Frontend developers needing to understand API responses"]
```

---

## Documentation Standards

### Writing Standards
- **Sentence structure:** Short, direct sentences (one idea per sentence)
- **Paragraph length:** 2-3 sentences for concepts, single line for commands
- **Technical terms:** Define on first use, link to glossary
- **Acronyms:** Spell out on first use: "Application Programming Interface (API)"
- **Code formatting:** Use inline `code` for commands, code blocks for examples

### Code Examples

**Requirements:**
- [ ] Every code example must be tested and working
- [ ] Include language identifier: ```python, ```javascript, ```bash
- [ ] Show complete examples (not just snippets when possible)
- [ ] Include error handling (not just happy path)
- [ ] Add comments explaining key lines
- [ ] Specify versions (library versions, API versions, language versions)

**Code Example Template:**
```python
# Python 3.9+
# Requires: requests>=2.28.0

import requests

# Initialize API client with your API key
api_key = "your_api_key_here"
headers = {"Authorization": f"Bearer {api_key}"}

# Make GET request to fetch user data
response = requests.get(
    "https://api.example.com/v1/users/123",
    headers=headers
)

# Handle response
if response.status_code == 200:
    user = response.json()
    print(f"User: {user['name']}")
else:
    print(f"Error: {response.status_code} - {response.text}")
```

### Structure by Documentation Type

#### API Reference
```
# Endpoint Name

Brief description (1-2 sentences)

## Request
- Method: GET / POST / PUT / DELETE
- URL: /v1/resource/{id}
- Authentication: Required / Optional
- Rate limiting: X requests per minute

## Parameters
- id (required): Resource identifier (string)
- filter (optional): Filter results (string)

## Request Example
[Code block]

## Response
- Status: 200 OK
- Content-Type: application/json

## Response Example
[Code block with annotated fields]

## Error Codes
- 400: Bad request (missing required parameter)
- 401: Unauthorized (invalid API key)
- 404: Resource not found
- 429: Rate limit exceeded
```

#### Tutorial
```
# Tutorial Title: What You'll Build

Brief intro (what reader will accomplish)

## Prerequisites
- Skill requirements
- Software/tools needed
- Environment setup

## Step 1: [First Task]
Explanation of what and why
[Code example]
[Expected output]

## Step 2: [Next Task]
[Continue...]

## Testing Your Implementation
[How to verify it works]

## Troubleshooting
[Common issues and solutions]

## Next Steps
[Where to go from here]
```

#### Quickstart
```
# Quickstart: Get Up and Running in 5 Minutes

## 1. Install (1 minute)
[Copy-paste install command]

## 2. Configure (1 minute)
[Minimal config code]

## 3. Make Your First Request (2 minutes)
[Hello world example]

## 4. Next Steps (1 minute)
[Links to deeper docs]
```

---

## Technical Accuracy Standards

### Version Specifications
```
Always specify:
- Programming language version: "Python 3.9+"
- Library versions: "requests>=2.28.0"
- API version: "API v1" or "API v2"
- Deprecated features: Mark clearly with warnings
```

### Code Testing Requirements
- [ ] All code examples tested in target environments
- [ ] Examples use current API/library versions
- [ ] Error cases included (not just success cases)
- [ ] Dependencies listed explicitly
- [ ] Environment variables documented

### Deprecation Warnings
```
⚠️ **Deprecated:** This endpoint is deprecated as of v2.0 and will be removed in v3.0.
Use `/v2/users/{id}` instead. [Migration Guide](link)
```

---

## SEO for Technical Docs

### Search Optimization
- **Title format:** [TITLE_FORMAT — e.g., "[Task] in [Technology]", e.g., "Authentication in Python"]
- **Keywords:** Technical terms developers search (function names, error codes, concepts)
- **Meta description:** Include programming language and key task
- **URL structure:** /docs/[section]/[topic] (e.g., /docs/api/authentication)

### Internal Linking
- Link to related docs (prerequisites, next steps, advanced topics)
- Link to API reference from tutorials
- Link to troubleshooting from error messages
- Create "See Also" sections

---

## Code Snippet Library

**Maintain a library of reusable code snippets:**

### Authentication Examples
```python
# Python authentication
# [Full example...]
```

```javascript
// Node.js authentication
// [Full example...]
```

```ruby
# Ruby authentication
# [Full example...]
```

### Common Patterns
- Pagination
- Error handling
- Rate limiting
- Webhook verification
- File uploads
- Async operations

**Benefits:**
- Consistency across docs
- Easy to maintain (update once, reflects everywhere)
- Tested and verified

---

## Constraints & Guidelines

### What We Don't Do
- ❌ Assume prior knowledge without stating it
- ❌ Skip error handling in examples
- ❌ Use outdated library versions
- ❌ Copy code from Stack Overflow without testing
- ❌ Write wall-of-text explanations (code + brief explanation better)
- ❌ Use "simply", "just", "easy" (what's easy for you may not be for reader)

### Accessibility Requirements
```
- All code examples must be copyable (not images of code)
- Alt text for diagrams and screenshots
- Keyboard navigation for interactive docs
- High contrast for code syntax highlighting
```

---

## Documentation Review Process

### Technical Review Checklist
- [ ] **Accuracy:** All code examples tested and working
- [ ] **Completeness:** Prerequisites, setup, error cases covered
- [ ] **Clarity:** Technical terms defined, acronyms spelled out
- [ ] **Currency:** Uses current versions, no deprecated features (unless noted)
- [ ] **Code quality:** Examples follow language best practices
- [ ] **Links:** All internal/external links work

### Review Team
1. **Technical Writer:** Creates draft, ensures clarity
2. **Engineer (SME):** Verifies technical accuracy
3. **Developer Advocate:** Tests from user perspective
4. **QA/Testing:** Runs all code examples
5. **Documentation Lead:** Final approval

---

## Maintenance & Updates

### When to Update Docs
- **Immediately:** Breaking API changes, security issues
- **Same release:** New features, endpoint changes, parameter updates
- **Next release:** Deprecations, minor improvements
- **Quarterly:** Review for accuracy, update screenshots, refresh examples

### Update Process
1. **Track changes:** Link docs updates to product releases
2. **Version docs:** Maintain docs for current + previous 2 major versions
3. **Changelog:** Document what changed in docs (not just product)
4. **Notify users:** Email list, in-app notices for breaking changes

### Archiving Old Versions
```
/docs/v1/ - Archived, read-only, "Deprecated" banner
/docs/v2/ - Current production version
/docs/v3-beta/ - Next version (beta)
```

---

## Success Metrics

### Usage Metrics
- **Page views:** Most viewed docs (indicates popular features)
- **Search queries:** What users search for (missing docs?)
- **Time on page:** >2 minutes (indicates reading, not bouncing)
- **Copy button clicks:** Track code example usage

### Quality Metrics
- **Support ticket reduction:** Good docs = fewer "how do I..." tickets
- **Developer NPS:** Survey satisfaction with docs
- **Onboarding time:** Time to first successful API call (track in analytics)

### Completeness Metrics
- **API coverage:** 100% of endpoints documented
- **Code language coverage:** Examples in all supported languages
- **Error coverage:** All error codes documented with solutions

### Benchmarks
```
Good technical docs:
- 80%+ of developers find answers without contacting support
- 90%+ code examples work on first try
- 50%+ of developers rate docs as "helpful" or "very helpful"
```

---

## Revision History

| Date | Section | Change | Reason |
|------|---------|--------|--------|
| [Date] | API Reference | Added error code examples | Developer feedback |
| [Date] | Python examples | Updated to Python 3.9+ | Dropped 2.7 support |
| [Date] | Quickstart | Reduced from 10 to 5 minutes | Too long, lost users |

---

**Next Steps:**
1. Customize this template for your technical docs
2. Audit existing docs against these standards
3. Set up code example testing in CI/CD
4. Create style guide for code comments and variable names
