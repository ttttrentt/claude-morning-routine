---
description: Create today's morning check-in note with reflection questions
allowed-tools:
  - Write
  - Read
  - Bash(date:*)
  - Bash(find:*)
  - Bash(sort:*)
  - Bash(head:*)
  - Bash(tail:*)
status: active
tags:
  - workflow-step
---

## Context

- **Today's Date:** !`date "+%Y-%m-%d"`
- **Template:** See below for default questions
- **Note Filename:** Daily/YYYY-MM-DD. Morning Check-in.md
- **Yesterday's Morning Check-in:** !`find Daily -name "*Morning Check-in*" -type f 2>/dev/null | sort -r | head -2 | tail -1`

## Your task

1. **Carry forward yesterday's ideas:**
   - If yesterday's check-in exists, read it and extract any unfinished ideas
   - These will be included in today's "Ideas of the day" section

2. **Present reflection questions:**
   Greet user warmly and show questions. Format each as a bullet point for proper terminal rendering.

   **Default questions:**
   - How are you feeling this morning? (mood, energy level 1-10)
   - How did you sleep? (quality 1-10, hours)
   - What's your main focus for today?
   - What would make today feel successful?
   - Any ideas, insights, or thoughts to capture?

3. **Listen & respond:**
   - Let user go at their own pace
   - Only ask follow-ups if they skip a section entirely
   - Accept whatever level of detail they provide
   - Actively listen for ideas to populate "Ideas of the day" section
   - Keep prompts simple and concise

4. **Create note:**
   After responses, immediately create `Daily/YYYY-MM-DD. Morning Check-in.md` with:
   - YAML frontmatter: `date`, `mood`, `energy`, `sleep_quality`
   - User's responses organized by section
   - Ideas section with (1) carried-forward ideas and (2) new ideas from today

**Rules:**
- Create note immediately without asking for confirmation
- Preserve authentic voice
- Use sentence case headers
- Format tasks as checkboxes: `- [ ] task`
- Expand ideas with enough detail to understand without context
