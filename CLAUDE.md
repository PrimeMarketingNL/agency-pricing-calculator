# Agency Pricing Calculator — Project Documentation

## Overview
Marketing Savings Calculator web application for Prime (PrimeMarketingNL). Single-page HTML application with quiz-based interface to calculate agency pricing and demonstrate savings.

**Current branch**: `features` (merging to `main`)
**User**: PrimeMarketingNL  
**Email**: info@primemarketing.nl

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

## Recent Work & Current State

### Latest Commits
1. **TESTIMONIAL SLIDER** (`5e01c68`): Added testimonial slider component
2. **bigger buttons and font** (`eff04ab`): UI scaling improvements
3. **updated font style and logo** (`d02dd89`): Visual refinements
4. **updated pricing calculator logic and removed step** (`347f873`): Logic refactor, simplified flow
5. **Add files via upload** (`bfdfe32`): Asset uploads

### Known Characteristics
- Single-page monolithic HTML file (not modularized)
- All styling inline in `<style>` tag
- All logic in `<script>` tag at bottom of HTML
- Quiz-based UX with step progression and state management
- Dynamic price calculations based on user inputs

---

## How to Work on This Project

### Before Starting a Feature
1. Ensure you're on the `features` branch
2. All changes are made in `index.html`
3. Keep CSS and JS organized by section (search for `/* ── SECTION NAME ── */` markers)

### Making Changes
- **CSS changes**: Edit the `<style>` block (lines ~7–???)
- **Logic changes**: Edit the bottom `<script>` block
- **New features**: Add markup in the appropriate section, style it, add logic

### Git Workflow
- Work on `features` branch
- Commit with descriptive messages (follow pattern: action + what changed, e.g., "TESTIMONIAL SLIDER")
- Merge to `main` when feature is complete

### Testing
- Open `index.html` in browser to test
- Test calculator flow end-to-end
- Verify responsive design (uses `clamp()` for fluid sizing)
- Check all fonts load correctly

---

## File Structure
```
agency-pricing-calculator/
├── index.html              (main file — all code)
├── Header font/            (Safiro-Bold.otf)
├── normal text font/       (StabilGrotesk-Regular.otf)
├── Logo/                   (brand assets)
├── .claude/                (Claude Code config)
├── .git/                   (git history)
└── .github/                (CI/CD config)
```

---

## Key Design Decisions
- **Monolithic HTML**: Keeps deployment simple; trade-off is maintainability. Suitable for current scope.
- **Glass-morphism UI**: Fits brand aesthetic with `backdrop-filter: blur()` and `rgba()` backgrounds.
- **Quiz-based UX**: Guides users through calculation step-by-step, good for complex pricing logic.
- **Responsive typography**: Uses `clamp()` to scale fonts fluidly across breakpoints.

---

## Next Feature: [To be specified]
When beginning new feature work, update this section with requirements and approach.
