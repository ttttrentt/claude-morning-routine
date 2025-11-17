---
description: Review active goals and push for progress
thinking: extended
allowed-tools:
  - Read
  - Edit(*)
  - Bash(find:*)
  - Bash(date:*)
  - Bash(grep:*)
tags:
  - goals
  - morning
status: active
---

## Context

- **Today's Date:** !`date +%Y-%m-%d`
- **Goals Folder:** Goals/ (or configured location)
- **Active Goals:** !`find Goals -name "*.md" -type f 2>/dev/null | head -10`

## Your task

Help the user review their active goals and guide them to take meaningful action.

**Process:**

1. **Find and read active goals:**
   - Read goal files from the Goals folder
   - Look for YAML frontmatter with fields like: `status`, `start`, `end`, `frequency`
   - Extract last 3-5 log entries from each goal
   - Identify "Next review:" questions in recent entries

2. **Build presentation with embedded questions:**
   For each goal, create an entry with:
   - Title with emoji prefix
   - Progress bar (if start/end dates exist)
   - Last log entry (FULL text with emphasis)
   - Contextual questions based on the log

   **Question generation strategy:**

   A. **Check for "Next review:" questions in logs**
      - If found, use those questions (designed for follow-up)

   B. **Otherwise generate based on context:**
      - **Active work goals:** "What's the ONE thing that must get done today?"
      - **If deadline < 7 days:** "You have X days left. Are you on track?"
      - **If blocker mentioned:** "What's blocking you? How can we address it?"
      - **Backlog goals:** "Which idea resonates most? What would the outline look like?"

3. **Present everything together:**
   ```
   ## Your Active Goals (N total)

   **1. [Emoji] [Goal Name]** ([Deadline if exists])
   Progress: [████████░░░░] 60% complete • 15 days left
   Last update: YYYY-MM-DD (X days ago)
   [FULL last log entry with ALL CAPS emphasis, bold key terms]

   - ❓ **[Contextual question based on log]**
   - ❓ **[Second question if applicable]**

   **2. [Next Goal]** ...

   ---

   Just start responding to whatever questions resonate. Go at your own pace.
   ```

4. **Listen and engage:**
   - User responds to ANY questions in ANY order
   - Push for specificity: vague "work on X" → "Which specific task/section?"
   - Suggest creating new goals when ideas emerge

5. **Update goal logs:**
   - After gathering responses, update each goal's log section
   - Append entries with format: `- YYYY-MM-DD: [entry text]`
   - Include: actions planned, insights, blockers, new ideas
   - Add "Next review:" questions if follow-up needed

**Progress bar calculation:**
- Parse YAML: `start` and `end` dates
- Calculate: `days_elapsed`, `total_days`, `days_remaining`
- Progress: `(days_elapsed / total_days) * 100`
- Bar: 20 blocks total, each = 5%
- If overdue: `⚠️ OVERDUE by X days`

**Important:**
- Present goals WITH questions immediately
- Be proactive for backlog goals - don't accept "no progress"
- Push for specificity while staying conversational
- Use extended thinking mode for contextual questions
