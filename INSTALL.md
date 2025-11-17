# Installation Guide

## Quick Start

1. **Install the plugin**
   - Download or clone this plugin folder
   - Place it in your Claude Code plugins directory
   - Claude Code will auto-detect the plugin on next launch

2. **Set up your vault structure**
   ```bash
   mkdir -p Daily Goals Notes
   ```

3. **Optional: Add Spotify playlist**
   - Create or find a Spotify playlist for your morning routine
   - Right-click playlist → Share → Copy Spotify URI
   - Edit `commands/main.md` and replace `SPOTIFY_PLAYLIST_URI` with your URI

4. **Run your first routine**
   ```
   /morning-routine:main
   ```

## Customization

### Change folder locations

Edit the bash commands in workflow files. For example, in `commands/review-yesterday.md`:

```markdown
- **Last 3 Daily Reports:** !`find Daily -name "*Daily Report*" ...`
```

Change `Daily` to your folder (e.g., `Journal/Daily`).

Do this for all commands that reference folders (Goals, Notes, etc.).

### Modify reflection questions

Edit `commands/check-in.md` and change the questions under "Default questions" section.

### Adjust Pomodoro duration

Edit `commands/schedule-day.md` and change:
```applescript
end date:startTime + (25 * minutes)
```
to your preferred duration (e.g., `30 * minutes`).

### Disable Calendar or Spotify

Edit `commands/main.md` and `commands/schedule-day.md`:
- Remove or comment out the Spotify AppleScript block
- Remove or comment out the Calendar AppleScript sections

## Troubleshooting

**Calendar events not appearing:**
- Verify calendar name matches exactly (case-sensitive)
- Check System Preferences → Privacy → Calendar permissions
- Ensure "Work" calendar exists (or change config to existing calendar)

**Spotify not playing:**
- Ensure Spotify app is installed
- Verify playlist URI is correct
- Check that Spotify is not already playing

**Goals not found:**
- Verify `Goals/` folder exists in vault root
- Check that goal files have `.md` extension
- Ensure goal files have YAML frontmatter
- If using different folder, edit `commands/review-goals.md` to update path

**Workflow stages not progressing:**
- Check that slash commands are prefixed with `/morning-routine:`
- Verify `commands/` folder structure is intact
