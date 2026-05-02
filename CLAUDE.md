# Agency Pricing Calculator — Project Documentation

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