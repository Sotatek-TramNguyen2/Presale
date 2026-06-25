# UC-05 Generate Exemplar — Figma Make Prompt

## Description
Design a Band 6 exemplar generation interface where tutors enter exam questions/prompts and AI automatically generates sample essays that meet the highest assessment standards. This one-click feature creates reference materials for teaching.

## Design Intent
- **Purpose:** Generate Band 6 exemplar essays to serve as teaching benchmarks and student learning models
- **Audience:** Admin/Tutor (curriculum planning, student demonstration)
- **Context:** Standalone workflow or accessed from Dashboard; generates reference essays
- **Visual Priority:** Question input clarity, generation progress, exemplar preview with quality indicators

## Layout Structure

### Header Section
- **Top Navigation Bar** (white background, border-bottom divider):
  - Left: Plumpton High branding
  - Center: "Generate Exemplar Essay" heading
  - Right: Help icon (info tooltip: "Create Band 6 sample essays for teaching and curriculum reference")

### Main Content: Two-Step Workflow

---

## Step 1: Question Input

### Section 1a: Question Entry
- **Card Layout** (white bg, 1px border gray, border-radius 12px, padding 28px):
- **Label:** "Assessment Question / Prompt" (13px, bold, uppercase, gray)
- **Text Area:**
  - Min height: 200px, expandable
  - Placeholder: "Paste your exam question or writing prompt here. E.g., 'Analyze how technological advances have influenced modern communication...'"
  - Character counter: "0 / 2,000 characters" (bottom-right, 11px, gray)
  - Support for multi-line, formatting preserved

### Section 1b: Rubric & Context Selection
- **Field 1 - Associated Rubric:**
  - Label: "Which rubric defines Band 6 for this question?" (12px, bold)
  - Dropdown: Pre-populated from user's saved rubrics
  - Selected: "Advanced English - Academic Writing Rubric" (placeholder)
  - Show: "Band 6 Criteria: Ideas & Analysis (9/9), Structure (9/9), Language (8/9)"

- **Field 2 - Subject/Level (Optional):**
  - Label: "Subject & Level" (12px, bold)
  - Two dropdowns side-by-side:
    - Subject: "Advanced English" (pre-selected based on rubric)
    - Level: "Year 12" (placeholder)

- **Field 3 - Exemplar Tone (Optional):**
  - Label: "Desired Tone/Style" (12px, bold)
  - Radio buttons (display inline):
    - ○ Formal Academic
    - ○ Persuasive
    - ○ Analytical (default selected)
    - ○ Narrative
  - Tooltip: "This influences the writing style of the generated exemplar"

### Section 1c: Action Buttons
- **Generate Button** (primary, navy, full-width, 14px padding):
  - Text: "🚀 Generate Band 6 Exemplar"
  - On hover: Show tooltip "AI will generate a 400-600 word exemplar essay. Processing ~45 seconds."
  - Disabled (gray) until question >50 characters AND rubric selected

- **Clear Button** (secondary, gray border, 50% width, left side):
  - Clears all inputs, requires confirmation modal

---

## Step 2: Generation Progress & Exemplar Preview

### Section 2a: Generation Progress (Appears after clicking Generate)
- **Similar to UC-03 layout, but simplified:**
- **Center Card:**
  - Progress ring (100px) with percentage
  - Status message: "Generating Band 6 Exemplar..." (14px, navy, animated pulse)
  - Timeline:
    - ✓ Question analyzed
    - ⧖ Generating exemplar content...
    - ⚪ Quality verification
  - Estimated time: "~40 seconds remaining"
- **Cancel Button:** "Cancel Generation" (secondary)

### Section 2b: Exemplar Preview (After generation completes, or on separate view)

#### Left Panel: Generated Exemplar Essay (65% width)
- **Header:**
  - Badge: "EXEMPLAR" (red/crimson bg, white text, 10px, bold, uppercase)
  - Rubric Reference: "Based on Advanced English - Academic Writing Rubric" (11px, gray)
  - Generation timestamp: "Generated Oct 16, 2024, 2:30 PM" (10px, muted)

- **Question Display (light orange box, similar to UC-04):**
  - Label: "ORIGINAL PROMPT" (10px, uppercase, bold)
  - Question text (display the input from Step 1)

- **Exemplar Essay Body:**
  - Font: 14.5px, line-height 1.85, color dark
  - Full essay text (400-600 words typically)
  - **Highlighting (optional, shows strengths):**
    - Key topic sentence: Yellow highlight #fef3c7
    - Exemplary vocabulary/phrasing: Orange highlight #ffedd5
    - Strong evidence/examples: Green highlight #dcfce7
  
- **Essay Metadata:**
  - Word count: "542 words" (12px, gray, bottom-left)
  - Readability score: "Flesch-Kincaid: Grade 11.3" (12px, gray)
  - Language: "English (Australian)" (12px, gray)

#### Right Panel: Quality Analysis (35% width, light gray bg #fafbfc)
- **Section 1: Band 6 Criteria Alignment**
  - Title: "Criteria Alignment" (12px, bold, uppercase, gray)
  - List of criteria with checkmarks:
    - ✓ Ideas & Analysis: 9/9 (green text, 12px)
    - ✓ Structure & Organization: 9/9 (green)
    - ✓ Language & Conventions: 8/9 (green)
    - ✓ Vocabulary & Expression: 9/9 (green)
    - Overall: Band 6 (large green badge, center-aligned)

- **Section 2: Key Strengths**
  - Title: "Key Strengths" (11px, bold, uppercase, gray)
  - List items (11px, dark text):
    - "Sophisticated analysis of core concepts"
    - "Seamless paragraph transitions and flow"
    - "Precise and varied vocabulary choices"
    - "Well-integrated evidence from sources"

- **Section 3: Exemplar Notes for Tutors**
  - Title: "Teaching Notes" (11px, bold)
  - Callout box (background: #f0f9ff, border-left 3px blue):
    - Text: "This exemplar demonstrates all Band 6 criteria. Notice how the writer integrates evidence smoothly, uses sophisticated sentence structures, and maintains coherent argument throughout. Use this as a model for student self-assessment." (12px, line-height 1.6)

### Section 2c: Action Buttons (Sticky footer below exemplar)
- **Export as PDF:** "📥 Download PDF" (secondary, 40% width)
- **Copy to Clipboard:** "📋 Copy Text" (secondary, 40% width)
- **Share with Students:** "🔗 Share Link" (primary, navy, 20% width, right)
  - On click: Modal with shareable link + expiration options (7 days / 30 days / No expiration)
- **New Exemplar:** "➕ Generate Another" (secondary, full-width below)

### Section 2d: Alternative Exemplars (If requested)
- **Dropdown/Accordion:** "Show alternative generations (if any)"
- **Display:** List other generated versions with slight variations
  - Version 1 (current): Word count, score
  - Version 2: Word count, score
  - etc.
- **Compare Button:** Side-by-side view toggle

---

## States & Interactions

### Initial State
- Step 1 form visible
- "Generate" button disabled (gray)
- Step 2 hidden

### Form Validation
- Question field: Red error if <50 chars or empty on submit attempt
- Rubric field: Red error if not selected
- Real-time validation feedback below fields

### Generation Flow
1. User enters question + selects rubric → "Generate" button enabled (blue)
2. Click "Generate" → Scroll to Step 2
3. Progress indicator shows (similar to UC-03)
4. After ~45 seconds → Progress hides, exemplar essay appears
5. Exemplar auto-scrolls into view, animated fade-in (200ms)

### Completion State
- Exemplar essay fully rendered with highlighting
- Right panel shows criteria alignment + teaching notes
- All action buttons enabled
- Show success toast: "Exemplar generated successfully!"

### Error State (Generation failed)
- Progress ring stops, shows error icon (red X)
- Error message: "Failed to generate exemplar. Please try again or contact support."
- Buttons: "Retry" (primary) / "Go Back" (secondary)

### Export Actions
- **Download PDF:**
  - Filename: "Exemplar_[Subject]_[QuestionSummary]_[Date].pdf"
  - Includes: Header (Plumpton High), question, essay, criteria alignment, teaching notes
  - Format: Print-friendly, A4 page size
  - Show confirmation: "PDF downloaded successfully"

- **Copy to Clipboard:**
  - Copies essay text only (no formatting)
  - Show toast: "Essay text copied to clipboard (542 words)"

- **Share Link:**
  - Modal appears with URL input (grayed out, read-only)
  - QR code (optional, 120px size)
  - Expiration dropdown: 7 days (default) / 30 days / No expiration
  - Copy link button
  - Sharing settings: "Shared with [n] students" (if previously shared)

---

## Color Palette
- **Primary Navy:** #1e3a5f
- **Primary Blue:** #3b82f6
- **Success Green:** #16a34a
- **Error Red:** #dc2626
- **Amber (exemplar badge):** #d97706
- **Text Dark:** #1e293b
- **Text Muted:** #64748b
- **Border:** #e2e8f0
- **Background Light:** #fafbfc
- **Highlight Yellow:** #fef3c7
- **Highlight Orange:** #ffedd5
- **Highlight Green:** #dcfce7

## Typography
- **Question label:** 13px, bold, uppercase
- **Essay body:** 14.5px, line-height 1.85
- **Metadata:** 11px-12px, gray
- **Criteria score:** 12px, green text, bold
- **Teaching notes:** 12px, line-height 1.6

## Animations
- **Generation progress:** Linear spinner rotation (1.5s loop)
- **Exemplar fade-in:** 300ms fade-in, staggered with highlights appearing 100ms apart
- **Highlighting transitions:** 200ms smooth color fade as highlights appear

## Notes for Figma Make
- Step 2 can be a separate view or card that replaces Step 1 (not side-by-side)
- Exemplar essay text should be selectable (text-select: enabled)
- Implement real-time character counter in question field
- Add "Save exemplar to library" toggle (bottom of right panel) to persist for future reference
- Keyboard support: Tab through form fields, Ctrl+Enter to generate, Ctrl+Shift+C to copy
- Mobile: Stack left/right panels vertically; exemplar essay full-width
- Print styles: Hide buttons, adjust font sizes for readability on paper
- Accessibility: Use semantic HTML (e.g., <article> for exemplar essay, <section> for criteria)
