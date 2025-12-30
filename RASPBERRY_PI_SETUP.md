# Command Noir - Raspberry Pi Setup

Deze versie van Command Noir is gemoderniseerd voor **Raspberry Pi 400** en andere Debian-gebaseerde systemen.

## Wat is er veranderd?

### Python 2 → Python 3
- Alle Python scripts gebruiken nu Python 3
- `print` statements zijn nu functies: `print()`
- `raw_input()` is vervangen door `input()`
- Oude exception syntax is geüpdatet

### macOS → Linux commando's
- `afplay` (audio) → `mpg123` of `aplay`
- `say` (text-to-speech) → `espeak`
- `brew` (Homebrew) → `apt-get`

## Installatie

### 1. Basis requirements (verplicht)

```bash
# Update package lijst
sudo apt-get update

# Installeer basis tools voor het spel
sudo apt-get install nmap wget
```

### 2. Python requirements (voor geavanceerde puzzels)

```bash
# Installeer pip3 (Python package manager)
sudo apt-get install python3-pip

# Installeer Python libraries
pip3 install requests twilio pillow docopt lxml nltk SimpleAES
```

### 3. Audio/multimedia (optioneel, maar aanbevolen)

```bash
# Voor achtergrond muziek en geluidseffecten
sudo apt-get install mpg123

# Voor text-to-speech (Nederlandse spraak)
sudo apt-get install espeak
```

### 4. Mail functionaliteit (optioneel)

```bash
# Als je de email functionaliteit wilt testen
sudo apt-get install mailutils
```

## Het spel starten

```bash
# Ga naar de game directory
cd /pad/naar/CLI-CommandNoir-master

# Start het spel
cat start
```

## Verschillen met de originele versie

### Werkt NIET meer:
- Originele macOS Homebrew installatie instructies
- macOS `afplay` commando voor audio
- macOS `say` commando voor spraak
- Python 2 specifieke syntax

### Werkt WEL:
- Alle basis CLI lessen (cat, ls, cd, man, chmod, etc.)
- Python scripts (nu Python 3)
- Audio effecten (met mpg123)
- Text-to-speech (met espeak)
- Netwerk tools (nmap, ping, traceroute)
- Het volledige verhaal en alle puzzels

## Troubleshooting

### Audio werkt niet
Als je geen geluid hoort, installeer mpg123:
```bash
sudo apt-get install mpg123
```

### Text-to-speech werkt niet
Als de spraak niet werkt, installeer espeak:
```bash
sudo apt-get install espeak
```

### Python errors
Controleer of je Python 3 gebruikt:
```bash
python3 --version
```

Als een Python library ontbreekt:
```bash
pip3 install <library-naam>
```

### Executie permissies
Als een script niet werkt, maak het uitvoerbaar:
```bash
chmod u+x scriptname
```

## Nederlandse versie

Dit spel is volledig vertaald naar het Nederlands, maar behoudt de originele Engelse commando namen (zoals `cat`, `ls`, `cd`, etc.) omdat dit de echte Unix/Linux commando's zijn die je moet leren.

## Gemoderniseerde bestanden

De volgende bestanden zijn aangepast voor Raspberry Pi/Debian:

**Python scripts:**
- `door-to-progress-bar` - Python 2 → 3, afplay → mpg123
- `fate` - Python 2 → 3

**Bash scripts:**
- `search` - say → espeak
- `inspect` - afplay → mpg123/aplay
- `saras-mail` - blijft hetzelfde (gebruikt standaard mail)

**Instructie bestanden:**
- `bar` - Homebrew → apt-get instructies
- `the-gang-of-two` - brew install → apt-get install
- `supercharge-your-python` - macOS pip → Debian pip3

## Veel plezier!

Geniet van je CLI avontuur! 🐱🕵️
