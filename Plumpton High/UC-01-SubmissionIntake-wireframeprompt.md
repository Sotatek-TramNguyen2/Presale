# UC-01 Submission Intake — Figma Make Prompt

## Description
Design a single-page form (Admin/Tutor interface) allowing educators to submit student essays/presentations for AI grading. This is the entry point to the grading workflow.

## Design Intent
- **Purpose:** Collect student submission metadata and essay content in a clean, accessible form
- **Audience:** Admin/Tutor (educational staff)
- **Context:** Plumpton High's internal grading tool for Advanced English and other subjects
- **Visual Priority:** Form clarity, input validation feedback, subject/level selection

## Layout Structure

### Header Section
- **Top Navigation Bar** (full width, white background)
  - Left: Plumpton High branding (icon + "Plumpton High" text, navy color)
  - Right: "New Submission" heading badge or status indicator
  - Border-bottom: light gray divider

### Main Content (Centered Card Layout)

#### Section 1: Student Information
- **Label:** "Student Details"
- **Fields:**
  - Student Name: Text input (required), placeholder "e.g., Jake Williams"
  - Student ID: Text input (optional), placeholder "e.g., STU-2024-001"
  - Date of Submission: Date picker (auto-fill to today, disabled for past dates)

#### Section 2: Assessment Selection
- **Label:** "Assessment & Subject"
- **Dropdown 1 - Subject:** 
  - Options: "Advanced English", "Chemistry", "Mathematics", "History", etc.
  - Default: "-- Select Subject --"
  - Required field
- **Dropdown 2 - Assessment Type:**
  - Dynamically populated based on subject selection
  - Options: "Essay", "Short Response", "Practical Report", etc.
- **Rubric Assignment:**
  - Rubric selector (loaded from Knowledge Base)
  - Display rubric name as badge (gray background)
  - "Change Rubric" link below

#### Section 3: Essay/Content Input
- **Label:** "Submission Content"
- **Large Text Area:**
  - Min height: 300px, expandable
  - Placeholder: "Paste your student's essay or presentation text here..."
  - Character counter at bottom-right (e.g., "1,245 / 5,000 characters")
  - Copy-paste support, no formatting stripped (preserve for syntax highlighting if Chemistry)

#### Section 4: Optional Notes
- **Label:** "Tutor Notes (Optional)"
- **Small Text Area (150px):**
  - Placeholder: "Add any context or special instructions for the AI grader..."

### Action Buttons (Bottom-right)
- **Cancel Button:** Secondary button, gray border, white background
- **Submit for Grading:** Primary button, navy background, white text, triggers processing flow

## States & Interactions

### Input Validation
- Required fields marked with red asterisk (*)
- On blur: Show validation error below field (red text, small font)
  - "Student Name is required"
  - "Please select a subject"
- Submit button disabled (gray, no cursor) until all required fields valid

### Subject Selection Flow
- When user selects subject → populate Assessment Type dropdown
- When user changes subject → clear previously selected rubric (show confirmation toast)

### Submission State
- On click "Submit for Grading":
  - Button shows loading spinner (rotating icon)
  - Button text changes to "Submitting..."
  - All inputs disabled
  - After 2-3 seconds → Success toast: "Submission received. Redirecting to Grading Dashboard..."
  - Redirect to UC-04 (Grading Report) after 1.5s delay

## Color Palette
- **Primary Navy:** #1e3a5f (buttons, headers, accents)
- **White:** #ffffff (backgrounds, cards)
- **Light Gray:** #f4f6f9 (page background)
- **Border Gray:** #e2e8f0 (dividers, input borders)
- **Text Dark:** #1e293b (labels, descriptions)
- **Text Muted:** #64748b (hints, secondary text)
- **Error Red:** #dc2626 (validation errors)
- **Success Green:** #16a34a (success feedback)

## Accessibility & Typography
- **Font Family:** System fonts (-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif)
- **Field Labels:** 12px, font-weight 700, uppercase letter-spacing (0.06em)
- **Input Text:** 14px, regular weight
- **Instructions:** 12px, gray text, line-height 1.5
- **Button Text:** 13px, font-weight 600

## Notes for Figma Make
- Use native HTML form components (no custom input masking on Student ID)
- Ensure keyboard navigation (Tab order: Name → ID → Date → Subject → Assessment → Rubric → Content → Notes → Buttons)
- Apply focus states (2px blue outline on inputs)
- Responsive layout: On mobile, form should stack vertically (full-width inputs, buttons 100% width)
