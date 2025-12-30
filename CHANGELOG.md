# Changelog - Command Noir

Alle belangrijke wijzigingen aan dit project worden gedocumenteerd in dit bestand.

## [2.0.0] - 2025-12-30

### 🎉 Grote Update: Raspberry Pi & Python 3

Deze versie is volledig gemoderniseerd voor Raspberry Pi 400 en andere Debian-gebaseerde systemen.

### ✨ Toegevoegd

- **Nederlandse vertaling**: Het volledige spel is nu in het Nederlands
  - Alle narratieve elementen vertaald
  - Instructies in het Nederlands
  - Originele Unix/Linux commando namen behouden (cat, ls, cd, etc.)

- **Nieuwe documentatie**:
  - `HOE_TE_SPELEN.md` - Nederlandse setup handleiding voor Raspberry Pi
  - `RASPBERRY_PI_SETUP.md` - Engelse setup handleiding
  - `MODERNIZATION_CHANGELOG.md` - Technische details van alle wijzigingen
  - `CHANGELOG.md` - Dit bestand

- **Raspberry Pi ondersteuning**:
  - apt-get package manager instructies
  - Debian-specifieke installatie stappen
  - Linux audio tools (mpg123, aplay)
  - Linux text-to-speech (espeak)

### 🔄 Gewijzigd

- **Python 2 → Python 3**:
  - `door-to-progress-bar` script volledig geconverteerd
  - `fate` script volledig geconverteerd
  - Alle `print` statements → `print()` functies
  - `raw_input()` → `input()`
  - `except E, e:` → `except E as e:`
  - Shebangs: `#!/usr/bin/env python3`

- **macOS → Linux commando's**:
  - `afplay` → `mpg123` / `aplay` (met automatische fallback)
  - `say` → `espeak -v nl` (Nederlandse stem)
  - `brew` → `apt-get`

- **Instructiebestanden aangepast**:
  - `bar` - Homebrew instructies vervangen door apt-get
  - `the-gang-of-two` - Package installatie voor Debian
  - `supercharge-your-python` - pip3 instructies voor Raspberry Pi

- **README.md bijgewerkt**:
  - Nederlandse beschrijving
  - Raspberry Pi badges
  - Link naar setup handleiding

- **CLAUDE.md bijgewerkt**:
  - Python 3 notities
  - Platform compatibility sectie
  - Bijgewerkte code voorbeelden

### 🗑️ Verwijderd

- Python 2 syntax (volledig vervangen door Python 3)
- macOS-specifieke commando's (afplay, say)
- Homebrew installatie instructies (vervangen door apt-get)

### 🔧 Technische Details

**Geconverteerde Python scripts:**
- `level1/level2/door-to-progress-bar/door-to-progress-bar`
- `level1/level2/door-to-progress-bar/.progress_bar/.arcade-room/snake-room/metal-door/fate`

**Aangepaste Bash scripts:**
- `level1/level2/search` (espeak integratie)
- `level1/level2/door-to-progress-bar/.progress_bar/.arcade-room/inspect` (Linux audio)

**Aangepaste instructiebestanden:**
- `level1/level2/door-to-progress-bar/.progress_bar/bar`
- `level1/level2/door-to-progress-bar/.progress_bar/the-gang-of-two`
- `level1/level2/door-to-progress-bar/.progress_bar/.arcade-room/snake-room/supercharge-your-python`

### 🐛 Bugfixes

- Audio speelt nu correct af op Linux systemen
- Scripts werken zonder errors op Python 3
- Graceful fallback als optionele tools (mpg123, espeak) niet geïnstalleerd zijn

### ⚠️ Breaking Changes

- **Niet meer compatibel met macOS specifieke commando's**
- **Python 2 wordt niet meer ondersteund**
- **Homebrew instructies zijn vervangen**

Om het spel op macOS te spelen, installeer eerst de Linux tools via Homebrew:
```bash
brew install mpg123 espeak python3
```

### 📦 Vereisten

**Minimaal (verplicht):**
- Debian/Raspberry Pi OS (of andere Debian-based Linux)
- Python 3.x
- nmap
- wget

**Aanbevolen (voor volledige ervaring):**
- mpg123 (voor achtergrondmuziek)
- espeak (voor text-to-speech)
- python3-pip + libraries (zie HOE_TE_SPELEN.md)

### 🙏 Credits

- **Originele game**: IDArnhem (CLI-CommandNoir)
- **Geïnspireerd door**: Marc Scott (CLI-TreasureHunt)
- **Modernisatie & Nederlandse vertaling**: Claude Code (2025)
- **Repository maintainer**: dosch

---

## [1.0.0] - 2017-11-15

### Originele Release

- Text-based CLI adventure game
- Noir detective verhaal
- Leert basis Unix/Linux commando's
- Python 2 scripts
- macOS compatibiliteit
- Homebrew integratie

[2.0.0]: https://github.com/dosch/CLI-CommandNoir/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/dosch/CLI-CommandNoir/releases/tag/v1.0.0
