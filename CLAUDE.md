# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Command Noir is an interactive CLI-based educational game that teaches command line skills through a noir detective narrative. Players navigate a directory tree, solving puzzles by executing bash/Python scripts and learning Unix commands.

## Game Architecture

### Directory Structure Pattern

The game follows a nested directory tree structure where:
- Each "room" is a directory containing narrative files (README, story text) and interactive elements (scripts)
- Progression is linear with some branching paths (e.g., level2 splits into `park` and `door-to-progress-bar`)
- Hidden directories use leading dots (`.progress_bar`, `.arcade-room`, `.server-room`) to teach `ls -A`
- Maximum depth reaches 8 levels from root through the deepest path

### File Types and Roles

1. **Narrative files**: Plain text with ASCII art (README, hello, Call, talk-to-hound, etc.)
2. **Executable scripts**: Bash/Python files with shebangs that serve as puzzle gates
   - `search` (bash): Text-to-speech intro script
   - `door-to-progress-bar` (Python): Multi-attempt authentication puzzle
   - `saras-mail` (bash): Email sending script
   - `inspect` (bash): Audio trigger script
   - `fate` (Python): SMS sending script
3. **Tutorial files**: Instructions embedded in story (bar, supercharge-your-python, connection-to-the-outside-world)
4. **Media assets**: Background music/sound effects (.mp3, .wav in `.media/`)

### Key Game Mechanics

**Executable Script Pattern** (`door-to-progress-bar`):
- Uses stateful tracking (`.tries` JSON file) to count player attempts
- Progressive difficulty with multi-step authentication (3 attempts → IP address challenge)
- On success, renames hidden `.progress_bar` directory to `progress_bar` (unlocking mechanic)
- macOS-specific audio playback using `afplay` command
- Python 2 syntax (raw_input, print statements without parentheses, old except syntax)

**Teaching Progression**:
- Level 1: Basic navigation (`ls`, `cd`, `cat`, `man`)
- Level 2a (park): File inspection (`file`), permissions (`chmod u+x`)
- Level 2b (Progress Bar): Python execution, package management (`brew`, `pip`), networking (`nmap`, `ping`, `traceroute`)

### Python Version Note

**UPDATED:** All Python scripts have been modernized to Python 3:
- `print()` functions (not statements)
- `input()` instead of `raw_input()`
- `except OSError as e:` syntax
- Scripts use `#!/usr/bin/env python3` shebang

### Platform Compatibility

**UPDATED:** Game modernized for Raspberry Pi 400 / Debian Linux:
- Audio: `mpg123` or `aplay` (was: macOS `afplay`)
- Text-to-speech: `espeak` (was: macOS `say`)
- Package manager: `apt-get` (was: macOS Homebrew)
- All scripts tested on Python 3 and Bash

## Working with Game Content

### Testing a Puzzle Room

To test a specific room's functionality:

```bash
# Navigate to the room
cd level1/level2/door-to-progress-bar

# Make script executable if needed
chmod u+x door-to-progress-bar

# Run the script
./door-to-progress-bar

# Reset puzzle state (if .tries file exists)
rm .tries

# Check if hidden directory was unlocked
ls -la
```

### Audio Testing

Background music uses `mpg123` (or `aplay` for WAV) on Linux. Audio files are in `.media/` directories:

```bash
# Test audio playback (requires: sudo apt-get install mpg123)
mpg123 level1/level2/door-to-progress-bar/.progress_bar/.media/nothing_is_true.mp3

# Alternative for WAV files
aplay level1/level2/door-to-progress-bar/.progress_bar/.media/scream.wav
```

### Creating New Rooms

When adding new puzzle rooms, follow the established pattern:
1. Create narrative README with ASCII art character
2. Include directional hints: `[forward>> next action]` and `[<<back previous action]`
3. For executable puzzles:
   - Add shebang (`#!/usr/bin/env python` or `#!/bin/bash`)
   - Include ASCII art for visual feedback
   - Use state files (JSON) for multi-attempt puzzles
   - Provide hints after failures
4. Use hidden directories (`.dirname`) for content that should be discovered
5. End successful puzzles with directory unlocking or next step instructions

## Common Patterns

### State Management in Puzzles

Scripts use JSON files to track player progress (Python 3):

```python
import json

def save_tries(count):
    d = {'tries': count}
    with open('.tries', 'w') as outfile:
        json.dump(d, outfile)

# Load state
if os.path.isfile('.tries'):
    with open('.tries') as jsonf:
        d = json.loads(jsonf.read())

# Note: All print statements use Python 3 syntax: print()
```

### Directory Unlocking Mechanism

Hidden directories are revealed by renaming:

```python
if not os.path.exists('progress_bar'):
    os.rename('.progress_bar', 'progress_bar')
```

### Narrative Formatting

- Use ASCII art for characters and atmosphere
- Include command examples in narrative: `` `command` `` or `$ command`
- Provide directional cues: `[forward>> action]` for next steps
- Embed educational content naturally in story dialogue
