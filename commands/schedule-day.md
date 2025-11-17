---
description: Schedule your day with calendar events and task list
allowed-tools:
  - Read
  - Write
  - Bash(osascript:*)
  - Bash(date:*)
tags:
  - workflow-step
---

## Context

- **Today's Date:** !`date +%Y-%m-%d`
- **Current Time:** !`date +%H:%M`
- **Day of Week:** !`date +%A`
- **Calendar Name:** Work (or configured name)

## Your task

Help the user schedule their day by creating calendar events and a task list.

**Process:**

1. **Understand the day:**
   - Recall tasks and priorities from the goal review session
   - Identify high-leverage tasks that should get time blocks
   - Note any fixed commitments (meetings, appointments)

2. **Build schedule with minimal questions:**
   - Use 25-minute Pomodoro blocks for focused work
   - Auto-schedule based on stated priorities
   - Only ask clarifying questions when truly ambiguous
   - Suggest time blocks (morning deep work, afternoon, etc.)

3. **Create calendar events (if enabled):**
   - Use AppleScript to create events in the configured calendar
   - Group AppleScript calls for efficiency
   - Format:
     ```applescript
     tell application "Calendar"
         set workCalendar to calendar "CALENDAR_NAME"
         set todayDate to current date
         set startTime to todayDate
         set hours of startTime to 9
         set minutes of startTime to 0
         make new event at workCalendar with properties {
             summary:"Task Name",
             start date:startTime,
             end date:startTime + (25 * minutes)
         }
     end tell
     ```

4. **Create Daily Tasks file:**
   Create `Daily/YYYY-MM-DD. Daily Tasks.md` with:
   - Time-blocked schedule matching the plan
   - Ranked priorities from goal review
   - Specific deliverables with clear outcomes
   - Success metrics for end of day
   - Key insights from morning check-in
   - Links to related goals

   **Format:**
   ```markdown
   # Daily Tasks - YYYY-MM-DD

   ## Schedule
   - **09:00 - 09:25** - [Task] - 25 min
   - **09:30 - 09:55** - [Task] - 25 min
   - **12:30 - 13:00** - Lunch - 30 min
   ...

   ## Priorities
   1. [ ] High-leverage task 1 (Goal: [[Goal Name]])
   2. [ ] High-leverage task 2
   3. [ ] ...

   ## Success Metrics
   - [ ] Completed X deliverable
   - [ ] Made progress on Y
   ...
   ```

5. **Confirm completion:**
   - Show checkmark ✅ when file created
   - Summarize schedule concisely

**Important:**
- 25-minute Pomodoro sessions with 5-minute breaks (breaks not in calendar)
- Default to "Work" calendar unless configured otherwise
- Be concise - minimize preamble and postamble
- Auto-schedule intelligently to reduce back-and-forth
