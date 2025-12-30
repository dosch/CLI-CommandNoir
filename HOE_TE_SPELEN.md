# Command Noir - Hoe te Spelen op Raspberry Pi

Welkom bij Command Noir! Dit spel leert je de Unix/Linux command line te gebruiken door middel van een spannend detective verhaal. Deze versie is speciaal aangepast voor **Raspberry Pi 400** en andere Debian-gebaseerde systemen.

## 📋 Wat je nodig hebt

### Hardware
- Raspberry Pi 400 (of elke andere Raspberry Pi met Raspberry Pi OS)
- Toetsenbord en scherm
- Internetverbinding (voor installatie van packages)

### Software
- Raspberry Pi OS (Debian-based)
- Terminal toegang

## 🚀 Snelstart

### Stap 1: Download het spel

```bash
# Kloon de repository
git clone git@github.com:dosch/CLI-CommandNoir.git

# Ga naar de game directory
cd CLI-CommandNoir
```

Of download het als ZIP en pak uit in een map naar keuze.

### Stap 2: Installeer vereiste software

```bash
# Update eerst je package lijst
sudo apt-get update

# Installeer basis tools (VERPLICHT)
sudo apt-get install nmap wget python3-pip
```

### Stap 3: Start het spel!

```bash
# Zorg dat je in de CLI-CommandNoir directory bent
cd CLI-CommandNoir

# Start het spel
cat start
```

Volg de instructies in het spel. Veel plezier! 🎮

## 📦 Volledige Installatie

Voor de beste ervaring en om alle puzzels te kunnen oplossen:

### 1. Systeem packages

```bash
# Update package lijst
sudo apt-get update

# Installeer basis networking tools
sudo apt-get install nmap wget

# Installeer Python package manager
sudo apt-get install python3-pip

# Installeer audio tools (OPTIONEEL maar aanbevolen)
sudo apt-get install mpg123 espeak

# Installeer mail tools (OPTIONEEL)
sudo apt-get install mailutils
```

### 2. Python libraries

```bash
# Installeer Python libraries voor de geavanceerde puzzels
pip3 install requests
pip3 install twilio
pip3 install pillow
pip3 install docopt
pip3 install lxml
pip3 install nltk
pip3 install SimpleAES
```

**Let op:** Deze installatie kan een paar minuten duren, afhankelijk van je internetsnelheid.

### 3. Test de installatie

```bash
# Test of nmap werkt
nmap --version

# Test of Python 3 werkt
python3 --version

# Test of mpg123 werkt (optioneel)
mpg123 --version

# Test of espeak werkt (optioneel)
espeak --version
```

## 🎮 Het Spel Spelen

### Basis commando's die je nodig hebt:

Het spel leert je deze commando's terwijl je speelt, maar hier zijn de allerbelangrijkste:

```bash
cat <bestandsnaam>    # Lees de inhoud van een bestand
ls                    # Toon bestanden in de huidige directory
ls -la                # Toon alle bestanden, inclusief verborgen
cd <directory>        # Ga naar een andere directory
cd ..                 # Ga één niveau omhoog
man <commando>        # Lees de handleiding van een commando
chmod u+x <script>    # Maak een script uitvoerbaar
./<scriptnaam>        # Voer een script uit
```

### Het verhaal

Je speelt een kat wiens vriendin Sara vermist is. Door het gebruik van command line tools probeer je haar te vinden. Je reis voert je door verschillende "kamers" (directories), elk met hun eigen verhaal en puzzels.

### Tips voor beginners

1. **Lees alles zorgvuldig** - De tekst geeft hints over wat je moet doen
2. **Gebruik `ls`** - Kijk vaak welke bestanden in een directory staan
3. **Gebruik `cat`** - Lees alle bestanden om het verhaal te volgen
4. **Gebruik `man`** - Als je niet weet hoe een commando werkt, lees de manual
5. **Maak notities** - Sommige informatie moet je onthouden
6. **Experimenteer** - Je kunt niets kapot maken, het is een spel!

### Navigatie hints in het spel

Het spel geeft je hints in deze vorm:
- `[volgende>> doe dit]` - Dit is de volgende stap
- `[terug>> ga terug]` - Dit zou je terug brengen (niet altijd mogelijk)

## 🔧 Probleemoplossing

### "Permission denied" bij het uitvoeren van een script

**Probleem:** Je probeert een script uit te voeren maar krijgt een foutmelding.

**Oplossing:**
```bash
# Maak het script uitvoerbaar
chmod u+x <scriptnaam>

# Voer het dan uit
./<scriptnaam>
```

### Geen geluid

**Probleem:** De achtergrondmuziek of geluidseffecten werken niet.

**Oplossing:**
```bash
# Installeer mpg123 voor MP3 bestanden
sudo apt-get install mpg123

# Test of het werkt
mpg123 --version
```

Het spel werkt ook zonder geluid, je mist alleen de sfeer!

### Text-to-speech werkt niet

**Probleem:** De spraak functie werkt niet in het `search` script.

**Oplossing:**
```bash
# Installeer espeak
sudo apt-get install espeak

# Test of het werkt met Nederlandse stem
espeak -v nl "Hallo wereld"
```

Ook hier geldt: het spel werkt zonder spraak, het is alleen een leuke extra.

### Python errors

**Probleem:** Een Python script geeft errors over ontbrekende modules.

**Oplossing:**
```bash
# Controleer of je Python 3 gebruikt
python3 --version

# Installeer de ontbrekende module
pip3 install <module-naam>

# Bijvoorbeeld:
pip3 install requests
```

### "command not found: nmap"

**Probleem:** Je hebt nmap nog niet geïnstalleerd.

**Oplossing:**
```bash
sudo apt-get install nmap
```

### Het spel is "stuck" - ik weet niet wat ik moet doen

**Tips:**
1. Lees het laatste tekstbestand opnieuw met `cat`
2. Gebruik `ls -la` om ALLE bestanden te zien (ook verborgen)
3. Verborgen bestanden en directories beginnen met een punt (`.`)
4. Probeer verschillende commando's uit
5. Kijk in de hints onderaan de tekstbestanden `[volgende>> ...]`

## 📝 Veelgestelde Vragen

### Moet ik alle packages installeren?

**Nee!** Het minimum is:
- nmap
- wget
- python3-pip

De rest is optioneel voor een betere ervaring.

### Werkt dit op andere Linux distributies?

**Ja!** Elke Debian-based distributie (Ubuntu, Linux Mint, etc.) zou moeten werken. Gebruik gewoon `apt-get` of `apt` om packages te installeren.

Voor andere distributies (Fedora, Arch, etc.) gebruik je eigen package manager:
- Fedora/RHEL: `dnf install`
- Arch: `pacman -S`

### Kan ik het spel opnieuw spelen?

**Ja!** Sommige scripts maken state files aan (zoals `.tries`). Je kunt deze verwijderen om puzzels opnieuw te spelen:

```bash
# Verwijder state files om opnieuw te beginnen
find . -name ".tries" -delete
```

### Hoeveel tijd kost het om het spel uit te spelen?

Voor beginners: **2-4 uur**
Voor gevorderden: **1-2 uur**

Het hangt af van je command line ervaring!

### Is dit geschikt voor kinderen?

**Ja!** Het spel is educatief en leert belangrijke computer vaardigheden. Het is geschikt voor:
- Kinderen vanaf ~10 jaar (met wat begeleiding)
- Tieners (zelfstandig)
- Volwassenen die Linux willen leren

Het verhaal is luchtig en er zit geen geweld of ongepaste inhoud in.

## 🎯 Wat leer je?

Door dit spel te spelen leer je:

### Niveau 1: Basis
- Bestanden lezen (`cat`)
- Bestanden en directories tonen (`ls`)
- Navigeren door directories (`cd`)
- Handleidingen lezen (`man`)

### Niveau 2: Intermediate
- Bestandsrechten aanpassen (`chmod`)
- Bestandstypes controleren (`file`)
- Scripts uitvoeren
- Verborgen bestanden vinden

### Niveau 3: Gevorderd
- Package management (`apt-get`)
- Python uitvoeren
- Python libraries installeren (`pip3`)
- Netwerk scanning (`nmap`)
- Netwerk diagnostiek (`ping`, `traceroute`)
- Scripting basis

## 🆘 Hulp Nodig?

1. **Lees de in-game hints** - Het spel geeft veel hints
2. **Gebruik `man`** - De manual pages zijn je vriend
3. **Google is je vriend** - Zoek naar het commando + "linux"
4. **Check de CHANGELOG.md** - Voor technische details over wijzigingen
5. **Open een issue op GitHub** - Voor bugs of vragen

## 🎉 Veel Plezier!

Command Noir is een leuke manier om Linux te leren. Neem je tijd, lees alles, en geniet van het verhaal!

Vergeet niet: in Linux is bijna alles mogelijk als je de juiste commando's kent. Dit spel is je eerste stap op weg naar h4xx0r status! 🐱🕵️

---

**Credits:**
- Originele game: IDArnhem
- Nederlandse vertaling & Raspberry Pi aanpassingen: 2025
- Gebaseerd op: CLI-TreasureHunt door Marc Scott
