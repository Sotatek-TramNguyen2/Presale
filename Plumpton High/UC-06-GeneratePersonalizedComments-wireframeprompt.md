# UC-06 Generate Personalized Comments — Figma Make Prompt

## Description
Design an automated comment generation interface where AI analyzes grading results and generates personalized, academically rigorous feedback for students in English. This creates tailored coaching comments based on performance data.

## Design Intent
- **Purpose:** Auto-generate student-facing feedback comments that are personalized, actionable, and academically appropriate
- **Audience:** Admin/Tutor (generating feedback); Students (consuming feedback, displayed elsewhere)
- **Context:** Post-grading step; uses AI grading results to synthesize feedback; exported to student report
- **Visual Priority:** Comment quality preview, tone/style selection, approval workflow, bulk generation capability

## Layout Structure

### Header Section
- **Top Navigation Bar** (white background, border-bottom divider):
  - Left: Plumpton High branding
  - Center: "Generate Student Feedback" heading
  - Right: Breadcrumb or context (e.g., "Advanced English • Grade 11A")

### Main Content: Three-Section Workflow

---

## Section 1: Feedback Generation Settings (Left Panel, 30% width)

### Settings Card (white bg, 1px border, 16px padding, border-radius 8px)

- **Title:** "Feedback Parameters" (13px, bold, uppercase, gray)

#### Field 1: Feedback Scope
- **Label:** "What should feedback cover?" (12px, bold)
- **Checkboxes** (multiple select):
  - ☑ Overall performance summary
  - ☑ Strengths and accomplishments
  - ☑ Areas for improvement
  - ☑ Specific actionable next steps
  - ☑ Encouragement for future attempts

#### Field 2: Tone & Style
- **Label:** "Tone of feedback" (12px, bold)
- **Radio buttons:**
  - ○ Formal Academic (default)
  - ○ Supportive & Encouraging
  - ○ Constructive Challenge
  - ○ Mixed (balances all)
- **Tooltip:** "Affects wording and emphasis of generated comments"

#### Field 3: Audience Level
- **Label:** "Student maturity level" (12px, bold)
- **Dropdown:**
  - Options: "Year 9", "Year 10", "Year 11", "Year 12"
  - Default: Auto-detect from student year level (pre-selected)
  - Affects: Vocabulary complexity, example depth

#### Field 4: Comment Length
- **Label:** "Feedback length" (12px, bold)
- **Slider** (range 100-500 words):
  - Default: 250 words
  - Display value: "~250 words" (right of slider, updated in real-time)
  - Tooltip: "Longer feedback includes more detailed examples"

#### Field 5: Include References (Optional)
- **Label:** "Include specific rubric criteria?" (12px, bold)
- **Toggle Switch** (on/off):
  - When ON: "Comments will reference specific rubric criteria (e.g., 'Your Ideas & Analysis score of 7/9...')"
  - Default: ON

#### Action Button
- **Generate Comments Button** (primary, navy, full-width, 14px padding):
  - Text: "🤖 Generate Feedback"
  - Disabled (gray) until at least one feedback checkbox is selected
  - On hover: Tooltip "Processing time: ~15-30 seconds"

---

## Section 2: Preview Area (Center Panel, 70% width)

### Preview Container

#### Sub-Section 2a: Student Info Header (sticky top)
- **White background, 1px border-bottom, 12px padding:**
  - Row 1: "Student: Jake Williams" (14px, bold) + "ID: STU-2024-001" (12px, gray, right-aligned)
  - Row 2: "Subject: Advanced English" (12px, gray) + "Submission: Oct 15, 2024" (12px, gray, right-aligned)
  - Row 3: "Current Grade: Band 3 (42/50)" (13px, bold, navy)

#### Sub-Section 2b: Generated Feedback Preview (Main content area)
- **Card:** White background, 1px border gray, border-radius 8px, 20px padding, min-height 300px
- **Display loading state initially:**
  - Skeleton loaders: 3 lines of gray boxes (shimmer animation)
  - Text: "Generating personalized feedback..." (12px, gray, centered)

- **After generation completes:**
  - **Feedback Text:**
    - Font: 14px, line-height 1.75, color dark (#1e293b)
    - Paragraph 1 (Overall performance): 3-4 sentences
    - Paragraph 2 (Strengths): 2-3 bullet points or flowing text
    - Paragraph 3 (Areas for improvement): 2-3 bullet points or flowing text
    - Paragraph 4 (Next steps): Specific, actionable recommendations
    - Closing sentence: Encouragement for future work

  - **Example Generated Text:**
    ```
    Dear Jake,

    Thank you for submitting your essay on technological impact. Your response demonstrates solid understanding of the topic and good organizational skills, placing you at Band 3 level. I've provided detailed feedback below to help you progress toward Band 4.

    What's Working Well:
    • Your paragraphs are clearly structured with topic sentences and supporting details
    • You've integrated quotations naturally into your arguments
    • Your introduction sets up the essay scope clearly

    Areas to Develop:
    • Deepen your analysis by asking "why?" and "so what?" for each key point
    • Incorporate counter-arguments to strengthen your credibility
    • Vary your sentence openings to maintain reader engagement

    To reach Band 4, focus on:
    1. Adding one sentence of analysis after each piece of evidence
    2. Including at least one acknowledging of alternative perspectives
    3. Refining word choices in your conclusion to emphasize key takeaways

    I'm confident that with attention to these areas, your next submission will show marked improvement. Keep up the good work!
    ```

  - **Inline Formatting (optional):**
    - Bold text: Strong recommendations, key criteria names
    - Italics: Example phrases, emphasis
    - Bullet points: For strength/development lists

#### Sub-Section 2c: Quality Indicators (Below feedback text)
- **Small info cards (displayed as flex row, 12px font, gray text):**
  - 📊 Readability: "Flesch-Kincaid Grade 10.2"
  - 🎯 Specificity: "5 actionable items mentioned"
  - 💡 Personalization Score: "87% personalized to student performance"

---

## Section 3: Actions & Management (Bottom, full-width)

### Preview Actions (Sticky footer)

#### Row 1: Edit & Regenerate
- **Button 1:** "✏️ Edit Comment" (secondary, 30% width)
  - Opens inline editor (textarea) allowing manual refinement
  - Show: "Changes will be saved locally; original comment preserved"
- **Button 2:** "🔄 Regenerate" (secondary, 30% width)
  - Re-run generation with current settings
  - Show confirmation: "This will create a new version. Continue?"
- **Button 3:** "📋 Copy" (secondary, 20% width)
  - Copies feedback text to clipboard
  - Toast: "Feedback copied to clipboard"
- **Button 4:** "⏬ Download" (secondary, 20% width)
  - Export as .docx or .txt file
  - Filename: "Feedback_JakeWilliams_Oct2024.docx"

#### Row 2: Approval & Delivery
- **Button 1:** "✅ Approve & Send" (primary, navy, 50% width)
  - Opens modal: "Send this feedback to Jake Williams?"
  - Options: "Send Now" / "Schedule for [Date]" / "Save as Draft"
  - On confirm → Toast: "Feedback sent to student. They will receive notification."
  - Button changes to "✓ Sent" (disabled, gray)

- **Button 2:** "💾 Save as Draft" (secondary, 50% width)
  - Saves comment to drafts folder
  - Toast: "Comment saved as draft. You can edit and send later."

---

## Additional Features (Accessible via icons/menus)

### Bulk Generation (Menu option: "Generate for batch")
- **Modal/Panel:** "Generate Feedback for Multiple Students"
- **Input:** Select students from class/cohort (checklist or table)
- **Settings:** Same as Section 1, applied to all selected students
- **Action:** "Batch Generate" button
- **Output:** Progress bar showing "3 / 15 students processed..."
- **Result:** Downloadable ZIP with all feedback documents

### Comment History/Versions
- **Dropdown/Accordion:** "View previous versions" (if any generated before)
- **Display:** List of prior generations with timestamps
- **Compare:** Side-by-side view option
- **Restore:** Revert to previous version button

### Template Management (Advanced)
- **Gear icon → Settings:**
  - Save current settings as template (e.g., "Standard Encouraging Tone")
  - Manage saved templates (edit, delete, rename)
  - Load template → Pre-fill all settings

---

## States & Interactions

### Initial Load
- Section 1: All checkboxes checked, tone = "Formal Academic", length slider @ 250 words
- Section 2: Empty preview, placeholder text "Click 'Generate Feedback' to create personalized comments"
- Section 3: All buttons disabled (gray)

### Generation Flow
1. User adjusts settings in Section 1 (checkboxes, tone, length)
2. Clicks "Generate Feedback" → Section 2 shows skeleton loaders (shimmer animation)
3. After ~20 seconds → Feedback text appears, animated fade-in (200ms)
4. Quality indicators appear below text
5. Buttons in Section 3 become enabled (blue primary, clickable secondary)

### Edit Mode (after "Edit Comment" clicked)
- Feedback text becomes editable textarea
- Show: "Editing mode. Changes are temporary. Save to confirm."
- Buttons: "Save Changes" (primary) / "Discard" (secondary)
- On "Save Changes" → Return to preview mode, show toast "Comment updated"

### Approval Flow
1. User reviews feedback (preview state)
2. Clicks "Approve & Send"
3. Modal: "Send Feedback to Jake Williams?" with date/schedule options
4. On "Send Now" → Button animates (brief loading state) → Changes to "✓ Sent" (disabled)
5. Toast: "Feedback delivered. Student will be notified via email."

### Error States

#### Generation Failed
- Section 2 shows error message: "Failed to generate feedback. Please try again or contact support."
- Buttons: "Retry" (primary) / "Go Back" (secondary)

#### Network Error During Bulk Generation
- Progress bar stops
- Error message: "Network error at student 7/15. Retry from last checkpoint?"
- Options: "Retry" / "Save progress" / "Cancel"

---

## Color Palette
- **Primary Navy:** #1e3a5f
- **Primary Blue:** #3b82f6
- **Success Green:** #16a34a
- **Error Red:** #dc2626
- **Text Dark:** #1e293b
- **Text Muted:** #64748b
- **Border:** #e2e8f0
- **Background Light:** #fafbfc
- **Background Page:** #f4f6f9

## Typography
- **Settings label:** 12px, bold
- **Feedback text:** 14px, line-height 1.75, color dark
- **Quality indicators:** 12px, gray
- **Button text:** 13px, font-weight 600

## Animations
- **Skeleton loading:** Shimmer effect (left-to-right, 1.5s loop)
- **Feedback fade-in:** 200ms ease-in
- **Button state change:** 300ms transition from disabled to enabled (opacity + color)
- **Toast notifications:** Slide-in from top-right (200ms), auto-dismiss after 4s

## Notes for Figma Make
- Settings panel (Section 1) should be collapsible on mobile (hamburger menu)
- Feedback preview text should be selectable and copyable (text-select: enabled)
- Support dark mode: Invert colors for preview background if system preference dark
- Keyboard shortcuts:
  - Ctrl+Enter to generate
  - Ctrl+Shift+E to edit
  - Ctrl+S to save/approve
- Accessibility:
  - Use semantic HTML (<aside> for settings, <article> for feedback, <footer> for actions)
  - ARIA labels on toggles and checkboxes
  - Screen reader should announce quality indicators
- Print-friendly: Hide buttons, enlarge feedback text to 16px, add header/footer with student name and date
- Email template: If "Send" chosen, feedback auto-formatted as email HTML (white bg, readable font, proper margins)
