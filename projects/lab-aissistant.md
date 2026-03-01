[← Back to Home](../)

---

# AI Lab Assistant — Personal Engineering Log System (Raspberry Pi 4)

**Status:** v0 stable and running on my Raspberry Pi 4. Project still open: **v0.2 Voice Logging Engine** (local speech-to-text + structured lab notes).  
**Focus:** Reliable self-hosted logging + searchable engineering notes + API-first workflow + future hands-free capture.

---

## Objective

Build a lightweight **engineering log system** that lives in my workshop and makes it easy to capture:
- Experiments and measurements (what I tested, what I observed)
- Debugging steps (what changed, what worked, what didn’t)
- Conclusions and next actions (so progress doesn’t evaporate between sessions)

Long term, the goal is a **hands-free lab logger**: I can speak while working, and the assistant generates clean, structured notes automatically.

---

## System Overview (v0)

This is a self-hosted web application running locally on a **Raspberry Pi 4 (4GB RAM)**:

- **OS:** Raspberry Pi OS (updated)
- **Runtime:** Python **3.13** (virtual environment)
- **Web App:** Flask
- **Deployment:** runs as a **systemd service** for reliability
- **Access:** LAN web UI (example: `http://192.168.0.166:5000`)
- **Storage:** filesystem persistence (notes stored in `~/ai-lab-assistant/notes`)

---

## Key Features (v0)

- **Web UI**
  - `/` → note list + search
  - `/add` → manual note entry form
- **API**
  - `/api/note` → POST new notes (supports **JSON** and **form-data**)
- **Persistence**
  - Notes are saved on disk and remain available after reboots/restarts

---

## Validation (v0)

- Flask app deployed as a **systemd** service: `ai-notes.service`
- **Auto-start on boot** confirmed
- API tested successfully from a separate machine using **PowerShell**
- Notes persist correctly in the storage folder and are visible from the web UI

---

## Why filesystem storage in v0?

For the first stable version, the priority is **maximum reliability with minimum moving parts**:
- Easy to inspect and backup
- No database setup/maintenance
- Lightweight for Raspberry Pi constraints

A structured database (e.g., SQLite) can be introduced later if the feature set demands it.

---

## Roadmap

### v0.2 — Voice Logging Engine
- Voice capture from a microphone
- Local speech-to-text (if viable on Raspberry Pi hardware)
- Automatic extraction into structured notes (timestamps, tags, key measurements)

### v0.3+
- Export notes to **Markdown/PDF** for portfolio documentation
- Tags / projects / better filtering
- Optional authentication for API access

---

## Evidence (Screenshots / Photos)

*(To add here)*
- `systemctl status ai-notes.service`
- Web UI home page (`/`) showing search + entries
- Example API POST (PowerShell) and the resulting saved note

---
