# UC-04 Grading Report — Figma Make Prompt

## Description
Design the main grading report dashboard displaying AI analysis results. This is the core interface where tutors review detailed grading scores, criteria breakdown, actionable feedback, and manage the final grade.

## Design Intent
- **Purpose:** Present comprehensive AI grading results in structured, scannable format
- **Audience:** Admin/Tutor (for review, approval, modification)
- **Context:** Final output of AI Grading Engine; supports decision-making and student feedback
- **Visual Priority:** Clarity of score, visual hierarchy of criteria, actionable feedback visibility, export/approval actions

## Layout Structure
**Follow exactly as UC-01 for: sidebar, page structure, font, colors, card styles, table styles, dropdown styles, button styles.**

### Header Section
- **Top Strip** (white bg, 1px bottom border gray):
  - Left: Plumpton High brand icon (30×30px navy bg, border-radius 7px) + "Plumpton High" text (15px, bold, navy)
  - Center: Submission date & time (12.5px, gray)
  - Right: "Draft" pill badge (amber background #fffbeb, amber text, uppercase, small font 11px)

### Main Layout: Two-Panel Design

#### Left Panel: Essay Content + Highlighting (60% width, white background)
- **Scrollable Content Area:**
  - **Subject Tag:** "Advanced English" (10px, uppercase, gray, font-weight 800)
  - **Title Row:**
    - Essay Title (22px, bold): e.g., "The Impact of Technology on Modern Society"
    - AI Tag: "🤖 AI Graded" (badge, light blue bg #f0f9ff, border 1px #bae6fd, blue text #0369a1, 10px)
  - **Metadata:** "Student: Jake Williams • ID: STU-2024-001 • Submitted: Oct 15, 2024" (12.5px, gray)
  - **Divider:** 1px gray line

- **Question Box (if applicable):**
  - Background: #fff8f0 (amber tint), border 1px #fed7aa, border-radius 8px, 12px padding
  - **Label:** "PROMPT" (uppercase, 10px, bold, amber text #92400e)
  - **Text:** Display original exam question (12.5px, gray)

- **Essay Body Text:**
  - Font: 14.5px, line-height 1.85, color dark
  - Paragraphs: 16px margin-bottom
  - **Text Highlighting System:**
    - **Yellow (⚙):** Complex sentence structures, key ideas — `background: #fef3c7, border-bottom: 2px #f59e0b`
    - **Orange (🔑):** Strength markers, vocabulary mastery — `background: #ffedd5, border-bottom: 2px #f97316`
    - **Green (✓):** Excellent usage, exemplar phrases — `background: #dcfce7, border-bottom: 2px #16a34a`
    - **Red (×):** Grammar errors, weak constructions — `background: #fee2e2, border-bottom: 2px #ef4444`
    - **Blue (*):** Cross-references to rubric criteria — `background: #dbeafe, border-bottom: 2px #3b82f6`

- **Legend** (at bottom of essay):
  - Small flex row showing all highlight colors with labels
  - Font: 11px, gray text
  - Format: [colored dot] Label | [colored dot] Label | ...

#### Right Panel: Verdict & Scoring (40% width, light gray background #fafbfc)
- **Scrollable Verdict Area (370px width):**
  - **Title:** "Grading Verdict" (16px, bold, dark text)

- **Section 1: Score Card (with Ring Visualization)**
  - **Card Background:** White, 1px border gray, border-radius 10px, 16px padding
  - **Layout:** Flex row (ring on left, score meta on right)
  
  - **Ring Component (80px × 80px):**
    - SVG circular progress ring:
      - **Background ring:** Gray #e2e8f0, thickness 8px
      - **Score arc:** Blue #3b82f6, filled to proportion (e.g., 42/50 = 84%)
      - **Center text overlay:**
        - Numerator: "42" (24px, bold, dark)
        - Fraction bar: thin line
        - Denominator: "50" (11px, gray)
  
  - **Score Meta (right of ring):**
    - **Band Pill:** Inline badge
      - Band 3 style: `background: #fffbeb, color: #a16207, border: 1.5px #fde68a, padding: 4px 12px, border-radius: 20px`
      - Text: "Band 3" (12px, bold, uppercase, letter-spacing 0.06em)
    - **Note:** "Good effort with areas to develop" (11.5px, gray, line-height 1.5)

- **Section 2: Criteria Breakdown** (label "Criteria Assessment" above, 10px uppercase gray)
  - **Criterion Card 1 (6 total):** "Ideas & Analysis"
    - **Card:** White bg, 1px gray border, border-radius 10px, overflow hidden
    - **Top Section (12px padding, border-bottom):**
      - Row 1: Criterion name (13px, bold) + Score badge right-aligned
        - Badge style: `background: #fffbeb, color: #a16207, padding: 3px 9px, border-radius: 12px` (for "Partial")
        - Text: "Partial" (11px, bold, uppercase)
      - Row 2: Level tag (11px, bold) "Demonstrates some analysis..." + Progress track
        - **Progress Track:** 5px height, gray bg #e2e8f0, 100% width
          - **Fill:** Blue bar (75% filled width)
          - **Dot Marker:** 13px white circle, 2.5px blue border, positioned at 75% (represents current level)
    
    - **Body Section (10px padding):**
      - **Feedback Item 1 - Strength:**
        - Label: "✓ STRENGTH" (10px, bold, uppercase, green text #16a34a)
        - Text: "You demonstrated sophisticated analysis of technological impacts..." (12px, line-height 1.6, dark text)
        - Optional emphasis: Italic text for specific example
      
      - **Feedback Item 2 - Development Area:**
        - Label: "✗ AREA FOR DEVELOPMENT" (10px, bold, uppercase, red text #dc2626)
        - Text: "Consider deepening your discussion of counterarguments..." (12px, line-height 1.6, dark text)

  - **Criterion Cards 2-6:** Repeat pattern (all visible on scroll, each ~120px height)

- **Section 3: Overall Feedback Card** (after all criteria)
  - **Card:** White bg, 1px border, 14px padding, border-radius 10px
  - **Title:** "Overall Assessment" (13px, bold)
  - **Summary Text:** "This is a solid Band 3 response showing good organizational skills and understanding of the topic. To advance to Band 4, focus on..." (12px, line-height 1.6)
  
  - **Key Strengths List:**
    - Small cards (`background: #f8fafc, border-radius: 7px, padding: 8px 10px, margin-bottom: 6px`)
    - **Label** (11px, bold, uppercase): "KEY STRENGTH"
    - **Text** (12px, line-height 1.55): "Coherent paragraph structure"
  
  - **Areas to Develop List:**
    - Similar card style (red tint background or border-left red)
    - **Label**: "AREA TO DEVELOP"
    - **Text**: "Deeper evidence integration from source material"

- **Section 4: Action Buttons** (bottom of verdict panel, sticky)
  - **Button:** "Ask AI to Regrade" (secondary, 1px border, full-width, 10px padding)
    - On click: Show modal "Re-grading will run the AI analysis again. Continue?" → Cancel / Re-grade
  - **Divider:** 1px gray line
  - **Button Row (flex, gap 8px):**
    - **Left:** "Draft Comment" (tertiary, gray, 50% width)
    - **Right:** "Approve Grade" (primary, navy, 50% width)
  - **After Approve:** Button state changes to "Grade Approved ✓" (disabled, gray)

## States & Interactions

### Default Load
- Left panel shows essay with highlights (pre-loaded from AI output)
- Right panel shows Score Card filled, all Criteria Cards visible
- Legend shows all 5 highlight types
- "Approve Grade" button is primary (enabled)

### Re-grade Flow
1. Click "Ask AI to Regrade"
2. Modal confirmation appears: "Re-grading will run the AI analysis again. This will take ~30 seconds. Continue?"
3. On confirm → Progress indicator (UC-03 style) shows during re-analysis
4. On completion → Refresh verdict panel with new scores/feedback
5. Show toast: "Re-grading complete. Review new feedback above."

### Draft Comment Flow
1. Click "Draft Comment"
2. Slide-out drawer from right edge (300px width) or modal
3. Show: "Compose feedback for student" textarea
4. Buttons: "Save as Draft" / "Send to Student"
5. Success message: "Comment saved as draft. You can edit anytime before grade approval."

### Approve Flow
1. Click "Approve Grade"
2. Button shows loading spinner (2s)
3. Button text changes: "Approving..." → "Grade Approved ✓"
4. Button disabled, gray background
5. Show toast: "Grade approved and logged. Student feedback pending."
6. Optional: Show "Export Report" link below

### Highlight Hover Interaction
- On hover over highlighted text in essay → Tooltip appears
- Tooltip content: Highlight type + AI annotation (e.g., "Complex Structure • Good variety")
- Position: Above/below text, avoid overflow

## Color Palette
- **Primary Navy:** #1e3a5f
- **Primary Blue:** #3b82f6
- **Success Green:** #16a34a
- **Error Red:** #dc2626
- **Amber:** #d97706
- **Text Dark:** #1e293b
- **Text Muted:** #64748b
- **Border:** #e2e8f0
- **Background Page:** #f4f6f9
- **Background Light:** #fafbfc

## Typography
- Follow UC-01 system defaults

## Responsive Notes
- On tablet/mobile: Stack left/right panels vertically (essay full-width above verdict)
- Verdict panel becomes full-width, scrollable independently
- Ring visualization scales to 70px on mobile
- Buttons stack vertically (100% width)

## Notes for Figma Make
- Verdict panel is always sticky on desktop; auto-scroll to top of criteria when user clicks on essay highlights
- Implement smooth scroll-linking: Click highlight → Auto-scroll verdict to corresponding criterion
- Copy essay text functionality (highlight text → right-click "Copy" context menu)
- Export to PDF: Include all criteria breakdown, scores, feedback
- Print-friendly CSS: Hide top action buttons, optimize spacing for A4 page
- Keyboard: Tab through criteria cards, Enter to expand/collapse details
- Animation: Criteria cards fade-in sequentially as page loads (staggered 100ms delay)
