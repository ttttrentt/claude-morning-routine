---
description: Review yesterday and identify 3-day patterns
thinking: extended
allowed-tools:
  - Read
  - Bash(find:*)
  - Bash(date:*)
  - Bash(sort:*)
  - Bash(head:*)
  - Bash(tail:*)
tags:
  - workflow-step
---

## Context

- **Today's Date:** !`date +%Y-%m-%d`
- **Yesterday's Date:** !`date -v-1d +%Y-%m-%d`
- **Last 3 Daily Reports:** !`find Daily -name "*Daily Report*" -type f 2>/dev/null | sort -r | head -3`
- **Last 3 Morning Check-ins:** !`find Daily -name "*Morning Check-in*" -type f 2>/dev/null | sort -r | head -3`
- **Last 3 Evening Check-ins:** !`find Daily -name "*Evening Check-in*" -type f 2>/dev/null | sort -r | head -3`

## Your task

Help the user review the last 3 days to extract patterns and inform today's strategy.

**Process:**

1. **Read available daily files:**
   - Read files provided in Context (Morning Check-ins, Daily Reports, Evening Check-ins)
   - Extract key information: timestamps, metrics, quotes, emotional states, insights
   - Work with whatever data is available (skip missing files gracefully)

2. **YESTERDAY SNAPSHOT (present FIRST):**
   - Start with: `## YESTERDAY SNAPSHOT (Yesterday's Date)`
   - Create a vivid reconstruction of yesterday with specific details:
     - **What actually happened (3 bullets max):** Concrete, specific events
     - **Chronological reconstruction:** Break into 4-5 time periods with precise timestamps
       - Use bullet points for each period (NOT paragraph blocks)
       - Include direct quotes from user's reflections
       - Show specific metrics (energy levels, work hours, etc.)
       - Connect cause and effect (what happened AND why)
     - **The arc:** Single-line summary of the day's overall story

3. **Identify patterns across 3 days:**
   - Be specific with dates and data
   - Use direct quotes from reflections
   - Show evolution across days, not just isolated facts

   **Analyze:**
   - **Wins & Progress:** Specific achievements with dates and impact
   - **Blockers & Drains:** Specific obstacles with data
   - **Commitments vs Reality:** What was planned vs what happened
   - **Key insights:** Learnings and realizations (quoted)
   - **Actions from evening check-ins:** Tasks mentioned for "tomorrow"

4. **Present pattern summary:**
   - Start with: `## 3-Day Patterns Summary`
   - Create 4 sections:
     - **Main accomplishments:** Specific achievements with progression
     - **Recurring blockers:** Specific data and patterns
     - **Key patterns:** Connected insights with "why"
     - **Action items from evening check-ins:** Carried-over commitments

**Important:**
- Depth over brevity - be detailed and vivid
- Specificity - exact times, numbers, quotes, dates
- If data is missing, work with what's available
- Use emojis for visual engagement
