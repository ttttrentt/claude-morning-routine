# Morning Routine Workflow for Claude Code

A multi-stage workflow system that helps you start each day with clarity and intention.

## Overview

This workflow orchestrates a complete morning routine through four sequential stages:

```
┌─────────────────────────────────────────────────────────────┐
│                     MORNING ROUTINE                         │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 1: Review Yesterday                                  │
│  • Read last 3 days of daily notes                         │
│  • Extract patterns and insights                           │
│  • Present vivid reconstruction of yesterday               │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 2: Morning Check-in                                  │
│  • Reflection questions (mood, energy, focus)              │
│  • Capture ideas and insights                              │
│  • Create daily note with YAML frontmatter                 │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 3: Review Goals                                      │
│  • Read active goals from Goals folder                     │
│  • Generate contextual questions per goal                  │
│  • Update goal logs with today's plans                     │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Stage 4: Schedule Day                                      │
│  • Build Pomodoro-based schedule                           │
│  • Create Apple Calendar events                            │
│  • Generate Daily Tasks file with priorities               │
└─────────────────────────────────────────────────────────────┘
```

## Installation

1. Clone this repository or download the files
2. Copy the `commands/` folder to `.claude/commands/morning-routine/` in your vault
3. (Optional) Copy templates to your vault for reference
4. Create the required folders in your vault (see structure below)
5. Customize commands to match your preferences (optional)
6. Run `/morning-routine:main` to start your first routine

## Required Vault Structure

The workflow expects this minimal folder structure:

```
your-vault/
├── Daily/              # Daily notes (check-ins, reports)
├── Goals/              # Goal tracking files
└── Notes/              # General notes
```

## Goal File Format

Goals should be markdown files with YAML frontmatter:

```yaml
---
status: "In progress"
start: 2025-11-01
end: 2025-12-15
frequency: "Daily"
---

# Goal Name

## Prerequisites
[Context and background]

## Log
- 2025-11-15: Progress update here
- 2025-11-14: Previous entry
```

## Commands

- `/morning-routine:main` - Run complete routine
- `/morning-routine:review-yesterday` - Review last 3 days
- `/morning-routine:check-in` - Morning reflection only
- `/morning-routine:review-goals` - Goal review only
- `/morning-routine:schedule-day` - Scheduling only

## Features

**Context Efficiency**: The workflow uses targeted file reads and extracts only relevant sections, avoiding full file ingestion.

**Automatic Progression**: All stages flow automatically without manual intervention between steps.

**Contextual Questions**: Goal review generates specific questions based on each goal's recent log entries, not generic prompts.

**Progress Tracking**: Visual progress bars for goals with start/end dates, showing days remaining and completion percentage.

**Calendar Integration**: Optional AppleScript integration to create calendar events (macOS only).

**Spotify Integration**: Optional music playback to start your routine with the right ambiance.

## Platform Support

- Full support: macOS (all features including Calendar and Spotify)
- Partial support: Other platforms (workflow stages work, skip Calendar/Spotify steps)

## Customization

All customization is done by editing the command markdown files directly:

**Change folder paths:**
Edit the `!`find ...`` commands in any workflow stage. For example, in `commands/review-yesterday.md`:
```markdown
- **Last 3 Morning Check-ins:** !`find Daily -name "*Morning Check-in*" ...`
```
Change `Daily` to your folder name (e.g., `Journal/Daily`).

**Change reflection questions:**
Edit `commands/check-in.md` under "Default questions" section.

**Change calendar name:**
Edit `commands/schedule-day.md` and replace `"Work"` with your calendar name.

**Add Spotify playlist:**
Edit `commands/main.md` and replace `SPOTIFY_PLAYLIST_URI` with your playlist URI.

**Adjust Pomodoro duration:**
Edit `commands/schedule-day.md` and change `25 * minutes` to your preferred duration.

**Disable Calendar or Spotify:**
Simply remove or comment out those sections in `commands/main.md` and `commands/schedule-day.md`.

## License

MIT
