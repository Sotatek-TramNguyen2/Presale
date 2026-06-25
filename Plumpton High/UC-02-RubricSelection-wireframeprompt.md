# UC-02 Rubric Selection — Figma Make Prompt

## Description
Design a rubric browser & selector interface that displays pre-loaded rubrics from Knowledge Base. Tutors select 1-2 rubrics to be applied during AI grading process.

## Design Intent
- **Purpose:** Allow tutors to review and select assessment rubrics before submitting for grading
- **Audience:** Admin/Tutor
- **Context:** Post-submission, pre-AI-grading step; can be accessed from UC-01 form or separate sidebar panel
- **Visual Priority:** Rubric clarity, selection state visibility, quick preview capability

## Layout Structure

### Header Section
- **Top Navigation Bar** (white background, border-bottom divider)
  - Left: Plumpton High branding
  - Center: "Select Rubric(s)" heading
  - Right: "Step 2 of 6" progress indicator (light gray text)

### Main Content Layout

#### Left Panel: Rubric List (60% width)
- **Rubric List Container:**
  - List of rubric cards, each 100% width, 90px height
  - Scrollable (max 4 rubrics visible without scroll)
  - 8px padding between cards
  
- **Rubric Card Design:**
  - **Border:** 1px gray (#e2e8f0), border-radius 8px
  - **Hover State:** Light blue background (#f0f9ff), cursor pointer
  - **Selected State:** 2px solid blue border (#3b82f6), blue background tint, checkmark on right
  - **Content inside card (16px padding):**
    - Row 1: Rubric Name (13px, font-weight 700), Subject Tag (10px, gray, uppercase, right-aligned)
    - Row 2: "Criteria Count: 6" (11px, gray text), Last Updated: 2 weeks ago (11px, muted)

- **Sample Rubrics:**
  1. Advanced English - Band 6 Criteria
  2. Advanced English - Persuasive Essay Rubric
  3. Chemistry - Lab Report Evaluation
  4. Mathematics - Problem Solving Rubric

#### Right Panel: Rubric Preview (40% width)
- **Border-left:** 1px gray divider
- **Background:** Light gray (#fafbfc)
- **Padding:** 20px

- **Preview Content:**
  - **Header:** Rubric Name (16px, bold), Subject tag (10px, badge style)
  - **Description:** 12px, gray text, 2-3 lines describing rubric scope
  - **Criteria Section:**
    - **Title:** "Criteria (6 items)"
    - **List of criteria (scrollable, max 200px height):**
      - Each criterion: 
        - Name (13px, bold): "Ideas & Analysis"
        - Band definitions: "Band 6: Sophisticated...", "Band 5: Strong...", etc. (11px, gray)
        - Divider line between criteria
  - **Footer Actions:**
    - Button: "Select This Rubric" (primary, navy, full-width)
    - (If already selected) Button changes to "Selected" (gray, disabled)

### Selection State Summary (Bottom-left, sticky)
- **Card:** White background, 1px border, border-radius 8px, 20px padding
- **Title:** "Selected Rubric(s)" (13px, bold)
- **Badge List:** Display selected rubric names as small badges
  - Each badge: gray background, 8px border-radius, 8px padding, 11px text, close icon (×)
  - If only 1 rubric selected: "1 rubric selected" (secondary text)
  - If 2 rubrics selected: Show both names as badges; highlight as valid state
- **Counter below badges:** "Max 2 rubrics allowed" (10px, muted text)

### Action Buttons (Bottom-right, sticky)
- **Cancel Button:** Secondary (gray border, white bg)
- **Next / Confirm Selection:** Primary (navy bg), enabled only if 1-2 rubrics selected

## States & Interactions

### Default State
- First rubric in list is pre-highlighted (light background)
- Preview panel shows first rubric content
- "Selected Rubric(s)" shows empty or "(None selected yet)"

### Selection Flow
1. User clicks rubric card → Card border turns blue (2px), checkmark appears
2. Preview panel updates immediately to show selected rubric details
3. Rubric name appears as badge in "Selected Rubric(s)" section
4. If user clicks a second rubric → Add to selected list (now shows 2 badges)
5. If user clicks "×" on badge or third rubric → Unselect (max 2 enforced)

### Hover Effects
- Rubric card: Light blue background, pointer cursor
- Criteria text in preview: Slight underline on hover (no action needed)
- Close button (×) on badge: Change color to red on hover

### Empty State (if no rubrics loaded)
- Show message: "No rubrics available. Contact your administrator."
- Disable "Next" button

## Color Palette
- **Primary Navy:** #1e3a5f
- **Primary Blue:** #3b82f6
- **Selected Blue BG:** #f0f9ff
- **Card Border:** #e2e8f0
- **Text Dark:** #1e293b
- **Text Muted:** #64748b
- **Background Light:** #fafbfc
- **Badge Background:** #e2e8f0
- **Badge Text:** #1e293b

## Typography
- **Rubric Name:** 13px, font-weight 700
- **Criteria Name:** 13px, font-weight 700
- **Band Definition:** 11px, color gray
- **Labels:** 10px, uppercase, letter-spacing 0.06em, color muted
- **Subject Tags:** 10px, font-weight 800

## Notes for Figma Make
- Implement smooth transitions between rubric card selection (150ms fade)
- Left panel is scrollable if >4 rubrics; right panel (preview) is independent scrollable
- Selection checkmark: Use SVG icon (green checkmark, 20px size)
- Keyboard support: Arrow keys to navigate rubric list, Enter to select/deselect
- Responsive: On mobile, stack left/right panels vertically (full-width list above preview)
- Rubric preview content truncates long criterion descriptions; add "Show more" link if text >150 chars
