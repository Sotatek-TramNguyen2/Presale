# UC-03 AI Grading Engine — Figma Make Prompt

## Description
Design a real-time progress indicator & processing dashboard that displays the AI grading status. Shows when Sota Agents are analyzing the submission and provides feedback during processing.

## Design Intent
- **Purpose:** Provide transparent visibility into AI processing; reassure users the system is working
- **Audience:** Admin/Tutor (observing AI work)
- **Context:** Between UC-02 (rubric selection) and UC-04 (grading report); typically 15-45 seconds processing time
- **Visual Priority:** Progress clarity, status messages, processing indicators, error states

## Layout Structure

### Header Section
- **Top Navigation Bar** (white background, border-bottom divider)
  - Left: Plumpton High branding
  - Center: "AI Grading in Progress" heading (with animated pulse dot, green color #16a34a)
  - Right: Student name + Subject label (e.g., "Jake Williams • Advanced English")

### Main Content (Centered Card)

#### Processing Status Card
- **Background:** White, border 1px gray (#e2e8f0), border-radius 12px
- **Padding:** 36px 28px
- **Width:** 500px (max), responsive on mobile

#### Section 1: Progress Indicator
- **Visual:** Circular progress ring (120px diameter, centered)
  - **Outer Ring:** Gray background (#e2e8f0), thickness 8px
  - **Progress Arc:** Blue (#3b82f6), animated filling from 0% to 100%
  - **Center Text:**
    - Top: Current percentage (e.g., "45%"), 24px, bold
    - Bottom: "Processing" (11px, gray, light)

#### Section 2: Status Timeline (Below progress ring)
- **Title:** "Analysis Steps" (12px, bold, uppercase, gray)
- **Timeline Items (3 items, vertical stack):**

  1. **✓ Rubric Loaded** (Completed state)
     - Checkmark icon (green, #16a34a)
     - Status text: "Rubric Loaded" (13px)
     - Timestamp: "0.2s" (11px, muted)
  
  2. **⧖ Knowledge Embedding** (In-progress state)
     - Animated spinning icon (blue, #3b82f6)
     - Status text: "Processing NESA Syllabus Outcomes..." (13px)
     - Sub-text: "Contextualizing assessment criteria" (11px, gray)
     - Duration: "15s elapsed" (11px, muted)
  
  3. **⚪ Content Analysis** (Pending state)
     - Hollow circle icon (gray)
     - Status text: "Content Analysis" (13px, muted)
     - Sub-text: "Will begin shortly" (11px, gray)

- **Divider lines** between timeline items (thin, gray)

#### Section 3: Real-time Log (Optional Expandable)
- **Toggle:** "Show Detailed Log" (11px, blue link, cursor pointer)
- **Log Content (collapsed by default, expands on click):**
  - **Background:** Light gray (#f8fafc), border-radius 8px, 12px padding, max-height 150px, scrollable
  - **Monospace Font:** 11px, family: "Courier New"
  - **Sample log entries:**
    ```
    [14:32:15] Submission received (2,150 tokens)
    [14:32:15] Rubric parsing: Band 6 criteria extracted
    [14:32:16] NESA syllabus embedding initiated...
    [14:32:28] Context vectors loaded (1,247 embeddings)
    [14:32:29] Content analysis starting...
    ```

#### Section 4: Actions (While processing)
- **Button:** "Cancel Grading" (secondary, gray border, 100% width below)
  - On hover: Show tooltip "This will stop AI processing and return to submission form"
  - On click: Show confirmation modal "Are you sure?" → Cancel / Confirm

#### Section 5: Estimated Completion
- **Text:** "Estimated time remaining: ~20 seconds" (12px, navy text, centered below timeline)
- **Updates every 5 seconds** based on actual processing elapsed time

## States & Interactions

### Initial Load (0% progress)
- Progress ring at 0%
- Timeline: Step 1 & 2 pending, step 3 pending
- Estimated time: "~60 seconds"

### Mid-Processing (45% progress)
- Progress ring animates smoothly to 45%
- Timeline: Step 1 completed (checkmark), Step 2 in progress (spinning), Step 3 pending
- Estimated time updates dynamically

### Completion (100% progress)
- Progress ring fully filled (blue)
- All timeline steps show checkmarks
- After 1.5 seconds delay → Auto-transition to UC-04 (Grading Report)
- Alternative: Show "Grading Complete" message with "View Report" button

### Error/Timeout States

#### Timeout (>120s with no response)
- Progress ring stops animating
- Status text: "⚠ Processing Timeout"
- Show error message: "The AI grading process has timed out. Please try again or contact support."
- Timeline step 2 shows red X icon (#dc2626)
- Buttons: "Retry" (primary) / "Go Back" (secondary)

#### Network Error
- Similar to timeout
- Show: "Network error detected. Please check your connection and retry."

## Color Palette
- **Primary Navy:** #1e3a5f
- **Primary Blue:** #3b82f6
- **Success Green:** #16a34a
- **Error Red:** #dc2626
- **Text Dark:** #1e293b
- **Text Muted:** #64748b
- **Border:** #e2e8f0
- **Background Light:** #f8fafc
- **Background Page:** #f4f6f9

## Typography
- **Progress Percentage:** 24px, font-weight 900, color dark
- **Status Heading:** 13px, font-weight 700
- **Status Sub-text:** 11px, color muted
- **Timeline labels:** 13px, font-weight 600
- **Log text:** 11px, monospace font

## Animations
- **Progress Ring:** Linear animation filling over estimated duration (~60s typical)
- **Spinning Icon (in-progress):** 360° rotation, 1.5s loop, continuous
- **Pulse Dot (header):** 1.5s fade in/out, green color
- **Timeline Transitions:** 300ms fade-in for completed steps

## Notes for Figma Make
- Use SVG for progress ring (circular stroke with CSS animation)
- Implement actual WebSocket or Server-Sent Events (SSE) for real-time progress updates
- Log entries scroll automatically; add "clear log" button in expanded state
- On mobile: Progress ring scales down to 100px; timeline text becomes 12px
- Implement keyboard shortcut: ESC to cancel grading (show confirmation modal)
- Aria-live region on log container for screen reader announcements of status changes
