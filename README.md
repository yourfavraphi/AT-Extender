Original Repository: https://github.com/Dinobeiser/AT-Extender?tab=readme-ov-file

# 🚀 ALDI TALK Datenvolumen-Überwachung & Auto-Update Bot

Ein vollautomatisiertes Python-Skript zur Überwachung des verfügbaren ALDI TALK Datenvolumens. Bei Unterschreitung von 1 GB wird automatisch ein Nachbuchen versucht und eine Telegram-Benachrichtigung gesendet. Optional mit **Auto-Update**, **Sleep-Modus**, **Telegram-Support** und mehr.

---

📢 Updates, Hilfe & Community

🔔 Info-Kanal: @ATExtender_infocenter ( https://t.me/ATExtender_infocenter )

👥 Nutzergruppe: @ATExtender_Usergroup ( https://t.me/ATExtender_Usergroup )

🧑‍💻 Support/Entwickler: @CodyMeal ( https://t.me/CodyMeal )

---

## ✅ Features

- 🔍 Überwacht automatisch dein verbleibendes Datenvolumen
- ↻ Versucht automatische Nachbuchung bei < 1 GB
- 🔔 Sendet Benachrichtigungen über Telegram
- ♻️ Vollautomatischer Auto-Update-Mechanismus
- 🧠 Unterstützt zufällige oder feste Ausführungsintervalle
- 🧪 Entwickelt mit Playwright & Headless-Browser
- 🛠 Einfache Konfiguration via `config.json`

---

## 🛠️ Voraussetzungen

- Python **3.8 oder höher**
- Git (zum Klonen des Repositories)
- Playwright & Browser-Binaries

---

## 🚀 Einrichtung (einmalig)

### 1. Repository klonen

```bash
git clone https://github.com/Dinobeiser/AT-Extender.git
cd AT-Extender
```

### 2. Python venv & Abhängigkeiten installieren

```bash
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

> Falls `requirements.txt` fehlt:
```bash
pip install playwright requests
```

### 3. Playwright-Umgebung initialisieren

```bash
playwright install
```

> Dies lädt automatisch die nötigen Browser (Chromium etc.).

---

## ⚙️ Konfiguration

Erstelle eine Datei namens `config.json` im gleichen Verzeichnis wie das Skript und trage deine Daten wie folgt ein:

```json
{
  "RUFNUMMER": "DeineRufnummer",
  "PASSWORT": "DeinPasswort",
  "TELEGRAM": "0",
  "BOT_TOKEN": "DeinTelegramBotToken",
  "CHAT_ID": "DeineChatID",
  "AUTO_UPDATE": "1",
  "SLEEP_MODE": "random",
  "SLEEP_INTERVAL": "70"
}
```

### Felder erklärt:

| Schlüssel        | Beschreibung                                                                 |
|------------------|------------------------------------------------------------------------------|
| `RUFNUMMER`       | Deine ALDI TALK Nummer (mit 0 am Anfang)                   |
| `PASSWORT`        | Dein Kundenportal-Passwort                                                  |
| `BOT_TOKEN`       | Telegram-Bot-Token von [@BotFather](https://t.me/BotFather)                 |
| `CHAT_ID`         | Deine Telegram-Chat-ID (z. B. via [@userinfobot](https://t.me/userinfobot)) |
| `AUTO_UPDATE`     | `1` für Auto-Update aktivieren, `0` für deaktivieren                        |
| `TELEGRAM`        | `1` für Telegram-Nachrichten, `0` für deaktivieren                          |
| `SLEEP_MODE`      | `"random"` oder `"fixed"`                                                   |
| `SLEEP_INTERVAL`  | Intervall in Sekunden (nur relevant bei `"fixed"`), **min. 70 Sekunden**    |

---

## 🔄 Automatisches Update

Wenn `AUTO_UPDATE` auf `1` gesetzt ist, prüft das Skript bei jedem Start automatisch auf Updates aus dem GitHub-Repo:

- Neue Version? → Skript wird **automatisch ersetzt** und **neu gestartet**!

> Hinweis: Das Skript muss **Schreibrechte** im eigenen Verzeichnis haben. Falls nötig:
```bash
chmod +x at-extender.py
```

---

## 🥪 Skript starten

```bash
python at-extender.py
```

> 💡 Du kannst das Skript auch als `nohup`, `screen`, `tmux` oder Hintergrundprozess laufen lassen, z. B.:

```bash
nohup python at-extender.py &
```

---

## ⏱ Automatisch beim Systemstart (optional)

Du kannst das Skript z. B. via `crontab`, `systemd` oder Autostart in Windows/Linux automatisch starten lassen. Beispiel mit `crontab`:

```bash
crontab -e
```

```cron
@reboot /pfad/zu/deinem/venv/python /pfad/zum/at-extender.py
```

---

## 🚇 Problembehandlung

### ❌ `playwright` Fehler beim ersten Start?

```bash
playwright install
```

### ❌ Skript wird nicht neu gestartet nach Update?

Stelle sicher, dass das Skript ausführbar ist:
```bash
chmod +x at-extender.py
```

### ❌ Telegram funktioniert nicht?

- Prüfe dein `BOT_TOKEN` & `CHAT_ID`
- Stelle sicher, dass dein Bot **dir schreiben darf**
- Teste mit curl:
```bash
curl -X POST "https://api.telegram.org/bot<DEIN_TOKEN>/sendMessage" -d "chat_id=<DEINE_ID>&text=Testnachricht"
```

---

## 🤝 Mithelfen

Verbesserungen, Fehlerberichte oder Pull Requests sind herzlich willkommen!

---
## 💜 Unterstützung & Spenden

Wenn du das Projekt unterstützen möchtest, lass gerne eine Spende da:

BTC: bc1q7rddem4wm6ryp3vqtrkxjq427qyy5yuckku90g

ETH: 0xcBa34A1744d3c89301600182938Fca0134b99A43

LTC: ltc1qzlwynlnsrw0j4etffne8f8mmnjep2xdtnv66wa

---
## 📜 Lizenz

MIT License – free to use and modify.

