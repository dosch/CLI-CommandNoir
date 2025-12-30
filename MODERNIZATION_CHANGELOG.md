# Modernization Changelog

Dit document beschrijft alle wijzigingen die zijn gemaakt om Command Noir te moderniseren van macOS/Python 2 naar Raspberry Pi/Debian/Python 3.

## Datum: 2025-12-30

## Python Scripts Geconverteerd

### 1. `door-to-progress-bar` (level1/level2/door-to-progress-bar/)
**Van:** Python 2
**Naar:** Python 3

**Wijzigingen:**
- Shebang: `#!/usr/bin/env python` → `#!/usr/bin/env python3`
- `print __SKULL__` → `print(__SKULL__)`
- `print "text",` → Input prompt in `input()` functie
- `raw_input()` → `input()`
- `except OSError, e:` → `except OSError as e:`
- `afplay` → `mpg123 -q` met fallback voor ontbrekende mpg123
- Multi-line print statements → `print("""...""")`

### 2. `fate` (level1/level2/door-to-progress-bar/.progress_bar/.arcade-room/snake-room/metal-door/)
**Van:** Python 2
**Naar:** Python 3

**Wijzigingen:**
- Shebang: `#!/usr/bin/env python` → `#!/usr/bin/env python3`
- `print "(!!!)"` → `print("(!!!)")`
- `print "text", var` → `print("text", var)`
- `except Exception, e:` → `except Exception as e:`
- Alle print statements omgezet naar functie aanroepen

## Bash Scripts Aangepast

### 3. `search` (level1/level2/)
**Wijzigingen:**
- `say "Nederlandse text"` → `espeak -v nl "Nederlandse text"`
- Toegevoegd: Check of espeak geïnstalleerd is
- Toegevoegd: Stille fallback als espeak ontbreekt

### 4. `inspect` (level1/level2/door-to-progress-bar/.progress_bar/.arcade-room/)
**Wijzigingen:**
- `afplay ../.media/scream.wav &` → Intelligente fallback:
  1. Probeer `mpg123 -q`
  2. Probeer `aplay`
  3. Stil falen als geen van beide beschikbaar

### 5. `saras-mail` (level1/level2/door-to-progress-bar/.progress_bar/.arcade-room/snake-room/metal-door/.server-room/)
**Wijzigingen:**
- Geen wijzigingen nodig (standaard Unix `mail` commando werkt op Debian)

## Instructie Bestanden Aangepast

### 6. `bar` (level1/level2/door-to-progress-bar/.progress_bar/)
**Van:** Homebrew installatie instructies voor macOS
**Naar:** apt-get instructies voor Debian/Raspberry Pi

**Wijzigingen:**
- Verwijderd: Ruby/Homebrew installatie commando
- Toegevoegd: `sudo apt-get update` uitleg
- Toegevoegd: `sudo apt-get install <package>` syntax

### 7. `the-gang-of-two` (level1/level2/door-to-progress-bar/.progress_bar/)
**Van:** Homebrew package installatie
**Naar:** apt-get package installatie

**Wijzigingen:**
- `brew install nmap` → `sudo apt-get install nmap`
- `brew install wget` → `sudo apt-get install wget`
- Toegevoegd: Optionele audio packages (mpg123, espeak)
- Aangepast: Uitleg over package managers

### 8. `supercharge-your-python` (level1/level2/door-to-progress-bar/.progress_bar/.arcade-room/snake-room/)
**Van:** macOS Python 2 / easy_install
**Naar:** Debian Python 3 / pip3

**Wijzigingen:**
- Referenties naar "Apple's crippled Python" vervangen door Raspberry Pi context
- `sudo easy_install pip` → `sudo apt-get install python3-pip`
- `sudo pip install` → `pip3 install`
- Verwijderd: `sqlite` (standaard in Python 3)
- Aangepast: Uitleg over sudo en package installatie voor Linux

## Documentatie Toegevoegd

### 9. `RASPBERRY_PI_SETUP.md` (nieuw)
Uitgebreide setup gids met:
- Installatie instructies voor alle dependencies
- Troubleshooting sectie
- Uitleg over verschillen met originele versie
- Debian/Raspberry Pi specifieke tips

### 10. `README.md` (bijgewerkt)
- Badge toegevoegd: "🇳🇱 Nederlandse versie | Gemoderniseerd voor Raspberry Pi"
- Verwijzing naar RASPBERRY_PI_SETUP.md
- Feature lijst van modernisaties

### 11. `CLAUDE.md` (bijgewerkt)
- Python versie sectie: Python 2 → Python 3
- Platform compatibility sectie toegevoegd
- Audio testing commando's bijgewerkt
- Code voorbeelden aangepast voor Python 3

## Samenvatting Wijzigingen

### Verwijderde Dependencies (macOS-specifiek):
- ❌ Homebrew (brew)
- ❌ macOS `afplay`
- ❌ macOS `say`
- ❌ Python 2
- ❌ `easy_install`

### Toegevoegde Dependencies (Debian/Linux):
- ✅ apt-get (standaard op Debian)
- ✅ mpg123 (optioneel, voor audio)
- ✅ aplay (alternatief voor audio)
- ✅ espeak (optioneel, voor text-to-speech)
- ✅ Python 3 (standaard op Raspberry Pi OS)
- ✅ pip3

## Backwards Compatibility

**Niet backwards compatible met:**
- macOS specifieke commando's zijn vervangen
- Python 2 is volledig verwijderd
- Originele Homebrew instructies werken niet meer

**Wel forward compatible:**
- Alle basis Unix commando's (cat, ls, cd, chmod, etc.) blijven werken
- Het spel mechanisme is ongewijzigd
- Het verhaal en de puzzel logica blijven hetzelfde
- Alle files/directories structuur is behouden

## Testing

Alle scripts zijn getest:
- ✅ Python 3 syntax check: `python3 -m py_compile`
- ✅ Bash syntax check: `bash -n`
- ✅ Audio commando fallbacks geïmplementeerd
- ✅ Nederlandse vertalingen behouden

## Aanbevolen Minimum Installatie (Raspberry Pi)

```bash
# Basis (verplicht voor alle puzzels)
sudo apt-get update
sudo apt-get install nmap wget python3-pip

# Python libraries (voor geavanceerde puzzels)
pip3 install requests twilio pillow docopt lxml nltk SimpleAES

# Audio/multimedia (optioneel maar aanbevolen)
sudo apt-get install mpg123 espeak
```

## Bekende Beperkingen

1. **Audio:** Sommige audio formaten werken mogelijk niet op alle systemen
2. **Text-to-speech:** Nederlandse stem kwaliteit hangt af van espeak versie
3. **Email:** `mail` commando vereist configuratie voor echte email verzending
4. **Twilio SMS:** Vereist actieve Twilio account (zie fate script)

## Auteurs van Modernisatie

- Originele game: IDArnhem
- Python 3 conversie: Claude Code
- Nederlandse vertaling: Claude Code
- Raspberry Pi aanpassingen: Claude Code
- Datum: 2025-12-30
