# AI TimeTracker

**Automatyczny system logowania czasu pracy z ActivityWatch do Tempo/Jira z wsparciem AI**

```
ActivityWatch  ───>  TimeTracker  ───>  Tempo/Jira
 (monitoring)         (web UI)          (worklogs)
```

**Live demo:** https://ai.beecommerce.pl/timetracker

---

# SZYBKA INSTALACJA

## Windows

### Krok 1: Zainstaluj ActivityWatch (WYMAGANE!)

**ActivityWatch musi byc zainstalowany PRZED uruchomieniem TimeTracker!**

1. **Pobierz ActivityWatch:** [activitywatch-v0.13.2-windows-x86_64-setup.exe](https://github.com/ActivityWatch/activitywatch/releases/download/v0.13.2/activitywatch-v0.13.2-windows-x86_64-setup.exe)
2. Uruchom instalator ActivityWatch
3. Po instalacji ActivityWatch uruchomi sie automatycznie (ikona w zasobniku przy zegarku)
4. **Sprawdz:** Otworz http://localhost:5600 - powinienes widziec dashboard

### Krok 2: Zainstaluj TimeTracker

**Pobierz instalator:** [TimeTracker-Setup-x64.exe](https://github.com/gacabartosz/ai-timetracker/raw/main/releases/TimeTracker-Setup-x64.exe) (52 MB)

1. Uruchom pobrany instalator - Node.js jest wbudowany
2. Kliknij "AI TimeTracker" w menu Start
3. Otworzy sie przegladarka z aplikacja na http://localhost:5666/timetracker

### Opcja alternatywna: Portable (bez instalacji)

1. Pobierz `TimeTracker-*-portable.zip` z [GitHub Releases](https://github.com/gacabartosz/ai-timetracker/releases/latest)
2. Wypakuj do dowolnego folderu
3. Uruchom `TimeTracker.bat`

### Opcja 2: Portable (bez instalacji)

1. Pobierz `TimeTracker-*-portable.zip` z [GitHub Releases](https://github.com/gacabartosz/ai-timetracker/releases/latest)
2. Wypakuj do dowolnego folderu
3. Uruchom `TimeTracker.bat`

### Opcja 3: Wszystkie pliki z GitHub Releases

Pobierz najnowszą wersję z [GitHub Releases](https://github.com/gacabartosz/ai-timetracker/releases/latest)

---

## macOS

### Intel Mac

```bash
# 1. Zainstaluj Homebrew (jeśli nie masz)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Zainstaluj Node.js i pnpm
brew install node
npm install -g pnpm

# 3. Zainstaluj ActivityWatch
brew install --cask activitywatch

# 4. Pobierz i uruchom TimeTracker
cd ~/Documents
git clone https://github.com/gacabartosz/ai-timetracker.git
cd ai-timetracker
cp .env.example apps/web/.env.local
# Uzupelnij tokeny w apps/web/.env.local
pnpm install
pnpm dev
```

### Apple Silicon (M1/M2/M3/M4)

```bash
# 1. Zainstaluj Homebrew dla ARM
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Dodaj Homebrew do PATH (Apple Silicon)
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"

# 3. Zainstaluj Node.js i pnpm
brew install node
npm install -g pnpm

# 4. Zainstaluj ActivityWatch
brew install --cask activitywatch

# 5. Pobierz i uruchom TimeTracker
cd ~/Documents
git clone https://github.com/gacabartosz/ai-timetracker.git
cd ai-timetracker
cp .env.example apps/web/.env.local
# Uzupelnij tokeny w apps/web/.env.local
pnpm install
pnpm dev
```

### Uprawnienia ActivityWatch (WAZNE!)

Bez tych uprawnien ActivityWatch nie bedzie zbierac danych!

1. **System Settings** > **Privacy & Security**
2. **Accessibility** - dodaj `ActivityWatch` i zaznacz checkbox
3. **Screen Recording** - dodaj `ActivityWatch` (opcjonalnie, dla tytulow okien)
4. **Input Monitoring** - dodaj `ActivityWatch` (dla watchers klawiatury)

### Autostart (macOS)

```bash
# ActivityWatch
open -a ActivityWatch
# Preferences > "Start on login"

# TimeTracker (z pm2)
npm install -g pm2
cd ~/Documents/ai-timetracker
pm2 start "pnpm dev" --name timetracker
pm2 startup  # Skopiuj i uruchom wyswietlona komende
pm2 save
```

---

## Linux

### Ubuntu / Debian

```bash
# 1. Zainstaluj Node.js 20.x
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs git

# 2. Zainstaluj pnpm
npm install -g pnpm

# 3. Zainstaluj ActivityWatch
sudo snap install activitywatch

# 4. Pobierz i uruchom TimeTracker
cd ~/Documents
git clone https://github.com/gacabartosz/ai-timetracker.git
cd ai-timetracker
cp .env.example apps/web/.env.local
nano apps/web/.env.local  # Uzupelnij tokeny
pnpm install
pnpm dev
```

### Fedora / RHEL

```bash
# 1. Zainstaluj Node.js
sudo dnf install nodejs git

# 2. Zainstaluj pnpm
npm install -g pnpm

# 3. Zainstaluj ActivityWatch (pobierz z activitywatch.net)
wget https://github.com/ActivityWatch/activitywatch/releases/download/v0.12.3/activitywatch-v0.12.3-linux-x86_64.zip
unzip activitywatch-*.zip
cd activitywatch
./aw-qt &

# 4. Pobierz i uruchom TimeTracker
cd ~/Documents
git clone https://github.com/gacabartosz/ai-timetracker.git
cd ai-timetracker
cp .env.example apps/web/.env.local
nano apps/web/.env.local  # Uzupelnij tokeny
pnpm install
pnpm dev
```

### Arch Linux / Manjaro

```bash
# 1. Zainstaluj Node.js i pnpm
sudo pacman -S nodejs npm git
npm install -g pnpm

# 2. Zainstaluj ActivityWatch (AUR)
yay -S activitywatch-bin

# 3. Pobierz i uruchom TimeTracker
cd ~/Documents
git clone https://github.com/gacabartosz/ai-timetracker.git
cd ai-timetracker
cp .env.example apps/web/.env.local
nano apps/web/.env.local  # Uzupelnij tokeny
pnpm install
pnpm dev
```

### openSUSE

```bash
# 1. Zainstaluj Node.js
sudo zypper install nodejs npm git

# 2. Zainstaluj pnpm
npm install -g pnpm

# 3. Zainstaluj ActivityWatch (Flatpak)
flatpak install flathub net.activitywatch.ActivityWatch

# 4. Pobierz i uruchom TimeTracker
cd ~/Documents
git clone https://github.com/gacabartosz/ai-timetracker.git
cd ai-timetracker
cp .env.example apps/web/.env.local
nano apps/web/.env.local
pnpm install
pnpm dev
```

### Docker (wszystkie dystrybucje)

```bash
# ActivityWatch w Docker (eksperymentalne)
docker run -d --name activitywatch \
  -p 5600:5600 \
  -v ~/.local/share/activitywatch:/root/.local/share/activitywatch \
  activitywatch/activitywatch

# TimeTracker
cd ~/Documents
git clone https://github.com/gacabartosz/ai-timetracker.git
cd ai-timetracker
cp .env.example apps/web/.env.local
nano apps/web/.env.local
docker build -t timetracker .
docker run -d --name timetracker \
  -p 5666:5666 \
  --env-file apps/web/.env.local \
  timetracker
```

### Systemd Service (Linux autostart)

```bash
# ActivityWatch
mkdir -p ~/.config/systemd/user
cat > ~/.config/systemd/user/activitywatch.service << 'EOF'
[Unit]
Description=ActivityWatch
After=graphical-session.target

[Service]
Type=simple
ExecStart=/snap/bin/activitywatch
# Lub: ExecStart=/home/USER/activitywatch/aw-qt
Restart=on-failure
RestartSec=5

[Install]
WantedBy=default.target
EOF

systemctl --user daemon-reload
systemctl --user enable activitywatch
systemctl --user start activitywatch

# TimeTracker (z pm2)
npm install -g pm2
cd ~/Documents/ai-timetracker
pm2 start "pnpm dev" --name timetracker
pm2 startup  # Skopiuj i uruchom wyswietlona komende
pm2 save
```

---

# JAK TO DZIALA

```
+---------------------+        HTTP API         +---------------------+
|   ActivityWatch     | <--------------------->|    TimeTracker      |
|  (localhost:5600)   |   GET /api/0/buckets/   |  (localhost:5666)   |
|                     |   GET /api/0/events     |                     |
|  Zbiera dane o      |                         |  Wyswietla dane     |
|  aktywnosciach      |                         |  i loguje do Jira   |
|  (dziala w tle)     |                         |  (strona www)       |
+---------------------+                         +---------------------+
```

**WAZNE:**
- **ActivityWatch** = program dzialajacy w tle, zapisuje co robisz
- **TimeTracker** = strona www, CZYTA dane z ActivityWatch przez API
- **BEZ ActivityWatch TimeTracker NIE BEDZIE DZIALAC!**

---

# GDZIE ACTIVITYWATCH PRZECHOWUJE DANE

| System | Lokalizacja bazy danych |
|--------|------------------------|
| **Windows** | `C:\Users\USER\AppData\Local\activitywatch\aw-server\peewee-sqlite.v2.db` |
| **macOS** | `~/Library/Application Support/activitywatch/aw-server/peewee-sqlite.v2.db` |
| **Linux** | `~/.local/share/activitywatch/aw-server/peewee-sqlite.v2.db` |

**Dane NIE gina po restarcie!** ActivityWatch przechowuje cala historie.

---

# KONFIGURACJA (.env.local)

```bash
# Skopiuj przyklad
cp .env.example apps/web/.env.local

# Edytuj
nano apps/web/.env.local  # Linux/macOS
notepad apps/web\.env.local  # Windows
```

Zawartosc:
```env
# ActivityWatch (nie zmieniaj)
ACTIVITYWATCH_URL=http://localhost:5600

# Tempo API
TEMPO_API_TOKEN=twoj_token_tempo

# Jira API
JIRA_BASE_URL=https://twoja-firma.atlassian.net
JIRA_SERVICE_EMAIL=twoj.email@firma.com
JIRA_API_KEY=twoj_token_jira
```

---

# JAK UZYSKAC TOKENY API

### Token Jira
1. Wejdz: https://id.atlassian.com/manage-profile/security/api-tokens
2. **Create API token** > nazwij "TimeTracker"
3. Skopiuj token > wklej do `JIRA_API_KEY=`

### Token Tempo
1. Jira > Apps > Tempo > Settings > API Integration
2. **New Token** > nazwij "TimeTracker"
3. Uprawnienia: Worklogs (View, Create, Edit)
4. Skopiuj token > wklej do `TEMPO_API_TOKEN=`

---

# ADRESY

| Co | Adres |
|----|-------|
| **TimeTracker** | http://localhost:5666/timetracker |
| **ActivityWatch** | http://localhost:5600 |

---

# ROZWIAZYWANIE PROBLEMOW

### Windows
| Problem | Rozwiazanie |
|---------|-------------|
| "node" nie znaleziony | Zamknij i otworz nowe okno PowerShell |
| "pnpm" nie znaleziony | Uruchom instalator pnpm ponownie |
| Port 5666 zajety | `netstat -ano | findstr :5666` i zabij proces |
| ActivityWatch nie dziala | Sprawdz ikone w zasobniku (przy zegarku) |

### macOS
| Problem | Rozwiazanie |
|---------|-------------|
| ActivityWatch nie zbiera danych | System Settings > Privacy > Accessibility |
| "brew" nie znaleziony | Dodaj `/opt/homebrew/bin` do PATH |
| Brak uprawnien | `sudo chown -R $USER ~/.npm` |

### Linux
| Problem | Rozwiazanie |
|---------|-------------|
| ActivityWatch nie dziala | Zainstaluj `xdotool` i `xprop` |
| Snap nie dziala | `sudo apt install snapd` |
| Port zajety | `lsof -i :5666` lub `fuser 5666/tcp` |

---

# SPRAWDZENIE CZY WSZYSTKO DZIALA

### Test 1: ActivityWatch
- Otworz: http://localhost:5600
- Powinienes widziec dashboard z aktywnosciami
- Jesli puste - poczekaj chwile i odswiez

### Test 2: TimeTracker
- Otworz: http://localhost:5666/timetracker
- W zakladce "Timesheet" powinny byc widoczne aktywnosci

### Jesli TimeTracker nie widzi aktywnosci:
1. Czy ActivityWatch dziala? (http://localhost:5600)
2. Czy plik `.env.local` zawiera `ACTIVITYWATCH_URL=http://localhost:5600`?
3. Czy ActivityWatch ma uprawnienia do zbierania danych?

---

# STRUKTURA PROJEKTU

```
ai-timetracker/
├── apps/web/                    # Aplikacja Next.js
│   ├── src/lib/activitywatch.ts # Integracja z ActivityWatch API
│   └── .env.local               # KONFIGURACJA (tokeny)
├── scripts/windows/             # Skrypty budowania paczki Windows
├── installer/                   # Definicja instalatora (Inno Setup)
├── releases/                    # Pre-built Windows installer (auto-update)
│   └── TimeTracker-Setup-x64.exe
├── .github/workflows/           # GitHub Actions (auto-build)
└── .env.example                 # Szablon konfiguracji
```

---

# AUTO-BUILD

Pliki EXE sa automatycznie budowane i commitowane do folderu `releases/` przy kazdym pushu do `main`.

- **Workflow:** `.github/workflows/build-windows.yml`
- **Status:** Sprawdz zakladke Actions w repozytorium

---

## Licencja

MIT

---

<p align="center">
  <strong>Powered by <a href="https://beecommerce.pl">beecommerce.pl</a></strong>
</p>
