---
title: Daten löschen / Delete Data
layout: page
---

# Daten löschen — Sunly

**App:** Sunly · **Anbieter:** Marius Alexander Becker

Es gibt **drei Wege**, deine Daten in Sunly zu löschen — alle in deinem Sinne sofort und vollständig.

---

## 🎯 Methode 1 · Direkt in der App (empfohlen)

**Pfad:** `Profil` → `Daten zurücksetzen` → Bestätigung antippen

**Was wird gelöscht:**
- Profil (Hauttyp, Ziele, Wunsch-Bräune)
- Alle Bräunungs-Sessions und Streak
- Foto-Verlauf (bis zu 50 Progress-Fotos)
- Einwilligungs-Nachweise (KI-Scan, AGB-Akzeptanz)
- Einstellungen (Sprache, Vibration, Crash-Reports)
- Cache (Wetter, UV-Daten)

**Wann:** sofort, in 2 Antippvorgängen mit Sicherheitsabfrage. Die App startet danach neu im Onboarding.

---

## 📱 Methode 2 · App deinstallieren

Wenn du die App vom Gerät entfernst, löscht Android automatisch die komplette App-Sandbox — gleicher Effekt wie Methode 1.

---

## 📧 Methode 3 · Daten bei Auftragsverarbeitern

Sunly nutzt drei externe Dienste für einzelne Funktionen:

| Auftragsverarbeiter | Was dort verarbeitet wird | Speicherdauer |
|---|---|---|
| **Google Cloud Vertex AI** (Frankfurt) | Foto bei KI-Hauttyp-Scan | nicht gespeichert (nur Inferenz) |
| **Cloudflare Edge Worker** (EU) | Anfrage-Routing, IP-Adresse | max. 30 Tage (Logs) |
| **Sentry** (Frankfurt) | Crash-Reports (anonym, opt-out) | max. 90 Tage |

Für Lösch-Anfragen bei diesen Dienstleistern, schreibe an:

> **mail@mariusbecker.me**

Bitte erwähne in deiner Mail:
- Dass du Sunly-Nutzer:in bist
- Welchen Datenstand du gelöscht haben möchtest (oder „alle")

Bearbeitung: meist innerhalb von 14 Tagen, max. nach 30 Tagen gem. Art. 12 DSGVO.

---

## ✅ Sentry-Crash-Reports einzeln deaktivieren

Falls du nur die Crash-Reports stoppen willst, ohne den Rest zu löschen:

**Pfad:** `Profil` → `Crash-Reports` → `Aus`

→ Sentry sendet ab sofort keine neuen Reports. Bereits übermittelte Reports werden bei Sentry automatisch nach 30–90 Tagen gelöscht (Standard-Retention).

---

# Delete Data — Sunly

**App:** Sunly · **Provider:** Marius Alexander Becker

There are **three ways** to delete your Sunly data — all immediate and complete.

## 🎯 Method 1 · In-app (recommended)

**Path:** `Profile` → `Reset data` → Confirm

**What gets deleted:**
- Profile (skin type, goals, desired tan)
- All tanning sessions and streak
- Photo history (up to 50 progress photos)
- Consent records (AI scan, Terms acceptance)
- Settings (language, vibration, crash reports)
- Cached weather and UV data

**When:** Immediately, in 2 taps with confirmation dialog. The app restarts in the onboarding flow afterward.

## 📱 Method 2 · Uninstall the app

Removing the app from your device causes Android to delete the entire app sandbox — same effect as Method 1.

## 📧 Method 3 · Sub-processor data

Sunly uses three external services for specific features:

| Sub-processor | What's processed | Retention |
|---|---|---|
| **Google Cloud Vertex AI** (Frankfurt) | Photo during AI skin scan | not stored (inference only) |
| **Cloudflare Edge Worker** (EU) | Request routing, IP address | max. 30 days (logs) |
| **Sentry** (Frankfurt) | Crash reports (anonymous, opt-out) | max. 90 days |

For deletion requests at these processors, email:

> **mail@mariusbecker.me**

Please include in your mail:
- That you're a Sunly user
- Which data state you want deleted (or "all")

Processing: usually within 14 days, max. 30 days per Art. 12 GDPR.

## ✅ Disable Sentry crash reports separately

If you just want to stop crash reports without deleting everything else:

**Path:** `Profile` → `Crash reports` → `Off`

→ Sentry stops sending new reports immediately. Existing reports auto-delete at Sentry after 30–90 days (standard retention).
