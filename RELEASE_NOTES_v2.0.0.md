# Release Notes v2.0.0

## 🎉 Versie 2.0.0 - Grote Update!

Command Noir is volledig gemoderniseerd voor **Raspberry Pi** en vertaald naar het **Nederlands**!

### ✨ Nieuwe Features

- **🇳🇱 Volledig in het Nederlands** - Alle verhalen, instructies en hints
- **🥧 Raspberry Pi ondersteuning** - Geoptimaliseerd voor Debian/Raspberry Pi OS
- **🐍 Python 3** - Volledig geconverteerd van verouderde Python 2
- **🔊 Linux audio** - mpg123, aplay, espeak ondersteuning
- **📦 apt-get** - Debian package manager in plaats van Homebrew

### 🚀 Snelstart

```bash
git clone git@github.com:dosch/CLI-CommandNoir.git
cd CLI-CommandNoir
sudo apt-get update
sudo apt-get install nmap wget python3-pip
cat start
```

### 📖 Documentatie

- **[HOE_TE_SPELEN.md](HOE_TE_SPELEN.md)** - 🇳🇱 Uitgebreide Nederlandse handleiding
- **[CHANGELOG.md](CHANGELOG.md)** - Volledige lijst van wijzigingen
- **[RASPBERRY_PI_SETUP.md](RASPBERRY_PI_SETUP.md)** - 🇬🇧 English setup guide

### 🔧 Technische Wijzigingen

**Python conversie:**
- `door-to-progress-bar` script → Python 3
- `fate` script → Python 3
- Alle print statements en input functies bijgewerkt

**Linux integratie:**
- `afplay` → `mpg123` / `aplay` (met fallbacks)
- `say` → `espeak -v nl` (Nederlandse stem)
- `brew` → `apt-get`

**Instructiebestanden:**
- Package manager instructies bijgewerkt voor Debian
- Python installatie aangepast voor pip3
- Alle gameplay instructies in het Nederlands

### ⚠️ Breaking Changes

- Niet meer compatibel met Python 2
- macOS specifieke commando's zijn vervangen
- Homebrew instructies zijn vervangen door apt-get

### 📊 Statistieken

- **38 bestanden** gewijzigd
- **1690+ regels** toegevoegd
- **Alle Python scripts** geconverteerd naar Python 3
- **Alle bash scripts** aangepast voor Linux
- **5 nieuwe documentatie bestanden**

### 🙏 Credits

- **Originele game**: [IDArnhem/CLI-CommandNoir](https://github.com/IDArnhem/CLI-CommandNoir)
- **Geïnspireerd door**: Marc Scott's CLI-TreasureHunt
- **Modernisatie & vertaling**: 2025
- **Maintainer**: [dosch](https://github.com/dosch)

---

Veel plezier met het spel! 🐱🕵️

**Download:** [v2.0.0](https://github.com/dosch/CLI-CommandNoir/archive/refs/tags/v2.0.0.zip)
