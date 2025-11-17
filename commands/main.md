---
description: Complete morning routine workflow
allowed-tools:
  - SlashCommand
  - Bash(osascript:*)
  - Bash(open:*)
  - Bash(date:*)
status: active
tags:
  - workflow
---

## Context

- **Routine Start Time:** !`date +"%H:%M"`
- **Today:** !`date +"%A, %Y-%m-%d"`

## Your task

Orchestrate the complete morning routine by executing stages in sequence.

1. **Start the morning ambiance (optional):**
   - If Spotify integration is configured, play morning playlist:
     ```bash
     osascript -e 'tell application "Spotify"
         if not running then
             launch
             delay 1
         end if
         play track "SPOTIFY_PLAYLIST_URI"
     end tell' && osascript -e 'tell application "System Events" to set visible of process "Spotify" to false'
     ```
   - Greet user warmly

2. **Review yesterday:**
   - Run `/morning-routine:review-yesterday` to get yesterday's snapshot and 3-day patterns
   - Automatically proceed to step 3

3. **Morning check-in:**
   - Run `/morning-routine:check-in`
   - User reflects on yesterday's context while answering questions
   - Automatically proceed to step 4

4. **Review goals:**
   - Run `/morning-routine:review-goals`
   - Interactive Q&A about active goals
   - Automatically proceed to step 5

5. **Schedule the day:**
   - Run `/morning-routine:schedule-day`
   - Creates calendar events based on priorities from goal review
   - Creates Daily Tasks file with time-blocked schedule
   - Automatically proceed to step 6

6. **Complete the routine:**
   - Log routine duration
   - Show: "Morning routine completed: [start time] - [current time]. Ready to start your day!"

**Critical:** Automatically proceed through all stages (1-6) without pausing.
