# Agency Pricing Calculator — Project Documentation

---

## User Profile

- **The user is not a developer and has zero coding knowledge.** All explanations, plans, and questions must use plain, non-technical language — no jargon, acronyms, or code snippets in user-facing communication unless absolutely necessary.
- Always confirm what a change will look like or do in plain terms before implementing it.
- When asking clarifying questions, phrase them in terms of the end result the user wants to see, not the technical approach.
- The user's input drives all decisions; never assume technical intent — always verify.

## Security & Code Quality Standards

- All code must follow security best practices at all times: no XSS vulnerabilities, no injection risks, no exposed secrets, no unsafe eval or innerHTML with user-controlled data.
- Code must be clean, minimal, and free of dead code or unnecessary complexity.
- Every change must be reviewed by the Code Review Agent before being considered done.
- If a security concern arises at any point in implementation, stop and resolve it before proceeding.

---

## Agent Workflow & Supervision Model

### Role: Supervisor (You)
You are the **supervisor/orchestrator**. You never implement changes yourself. Your responsibilities:
1. Investigate the user's request in the codebase
2. Ask clarifying questions if anything is ambiguous before planning
3. Create a detailed plan with implementation specs per sub-agent
4. Get user approval on the plan before delegating
5. Coordinate parallel work where possible (no overlapping file edits)
6. Route failures back to the responsible agent with clear context
7. Ensure all changes are tested and reviewed before declaring done

---

### Agent Roster

| Agent | Responsibility |
|---|---|
| **Frontend Agent** | HTML structure, CSS, UI logic, UX interactions |
| **Backend Agent** | JS business logic, data processing, calculations, state |
| **Test Agent** | Write and run tests based on implemented changes |
| **Code Review Agent** | Critical review of security, correctness, and expected outcomes |

---

### Workflow

```
User Request
    ↓
Supervisor: investigate codebase, ask follow-up questions if unclear
    ↓
Supervisor: create plan + per-agent implementation specs
    ↓
User approves plan
    ↓
Sub-agents (Frontend / Backend) implement — parallelized where no file conflicts
    ↓
Test Agent: writes and runs tests based on the sub-agent output
    ↓
  [Tests fail?] → Supervisor routes failure details back to responsible agent
       ↓ iterate until tests pass
  [Tests pass?] → Code Review Agent performs critical review
    ↓
  [Review flags issues?] → Supervisor routes feedback to responsible agent
       ↓ iterate until review passes
Done
```

---

### Parallelization Rules
- Frontend and Backend agents **can run in parallel** only when they touch different parts of `index.html` (e.g., frontend edits `<style>` / HTML structure; backend edits `<script>` logic)
- If both agents need to touch the same section, **sequence them** — Backend first, then Frontend, or vice versa as the plan requires
- Always specify exact line ranges or named sections in specs to prevent conflicts

### Implementation Spec Format (per agent)
Each agent spec must include:
- **Goal**: one-sentence summary of what to achieve
- **Files to touch**: exact file(s) and section(s)
- **Inputs**: any data, interfaces, or assumptions from other agents
- **Outputs**: what the next agent (Test/Review) should expect
- **Constraints**: what NOT to change

### Review Criteria (Code Review Agent)
Focus on:
- Security: no XSS, no injection, no exposed secrets
- Correctness: output matches the expected behavior from the spec
- Regression: no unintended side effects on existing features
- Code quality: no dead code, no unnecessary complexity

---

## Tech Stack & Architecture
### Technology
- **Language**: HTML + CSS + JavaScript (single-file monolithic structure)
- **File**: `index.html` (~33KB, contains all HTML, CSS, and JS)
- **Custom Fonts**:
  - Headers: Safiro (Bold, `Header font/Safiro-Bold.otf`)
  - Body text: Stabil Grotesk (Regular, `normal text font/StabilGrotesk-Regular.otf`)

### Design System
- **Color scheme**: Dark background with radial gradients (navy, orange, red accents)
- **Primary accent**: `#FF4A01` (orange)
- **Secondary text**: Orange `#FF895B`
- **UI framework**: Custom CSS with glass-morphism effects (backdrop filters)

### Core Components
1. **Landing section** (`#landing`): Hero with CTA button
2. **Quiz shell** (`#quiz`): Multi-step calculator with progress bar
3. **Steps**: Form-based questionnaire with various input types
   - Button groups (`.pbtn`) for single selections
   - List inputs (`.slist`) for key-value pairs
   - Number inputs with currency symbols
   - Dropdown selectors
4. **Testimonial slider**: Recently added (commit `5e01c68`)

---

### Known Characteristics
- Single-page monolithic HTML file (not modularized)
- All styling inline in `<style>` tag
- All logic in `<script>` tag at bottom of HTML
- Quiz-based UX with step progression and state management
- Dynamic price calculations based on user inputs