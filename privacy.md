---
title: Datenschutzerklärung
layout: page
---

# Datenschutzerklärung — Sunly

**Stand:** 8. Mai 2026 · **Version:** 1.1

---

## 1. Verantwortlicher

Verantwortlicher im Sinne der Datenschutz-Grundverordnung (DSGVO) und anderer nationaler Datenschutzgesetze der Mitgliedstaaten sowie sonstiger datenschutzrechtlicher Bestimmungen ist:

**Marius Alexander Becker**
Schleusingerstraße 41
58840 Plettenberg
Deutschland

E-Mail: mail@mariusbecker.me

Sunly wird privat und nicht-kommerziell betrieben. Es gibt keinen gesetzlich vorgeschriebenen Datenschutzbeauftragten (Art. 37 DSGVO), da die Schwellenwerte für eine Bestellpflicht nicht überschritten werden.

---

## 2. Geltungsbereich

Diese Datenschutzerklärung gilt für die mobile Anwendung **Sunly** (im Folgenden „App") für Android, veröffentlicht unter der Application-ID `com.mariusbecker.sunly`. Sie informiert die Nutzer (im Folgenden „du") über Art, Umfang und Zweck der Verarbeitung personenbezogener Daten.

Die App dient ausschließlich Wellness- und Lifestyle-Zwecken (UV-Index-Tracking, Bräunungsplanung, Vitamin-D-Schätzung). Sie ist **kein Medizinprodukt** im Sinne der Verordnung (EU) 2017/745 (MDR) und ersetzt keinerlei ärztliche Beratung, Diagnose oder Behandlung.

---

## 3. Grundsatz: Lokale Datenhaltung

Sunly ist als **datensparsame, lokal arbeitende App** konzipiert. Es gibt:

- ❌ **Keinen Cloud-Account und keine Server-User-Datenbank** bei Sunly selbst
- ❌ **Keine Anmeldung, keinen Login, keine E-Mail-Adresse** beim Anbieter
- ❌ **Kein Marketing-/Verhaltens-Tracking, keine Werbe-IDs**, keine klassischen Analytics-Tools (Google Analytics, Firebase Analytics, AppsFlyer o. Ä.)
- ✅ Profil, Sessions, Fotos und Einstellungen werden **ausschließlich lokal** auf deinem Endgerät gespeichert (Android `localStorage` + Filesystem)

Bei Deinstallation der App werden alle lokal gespeicherten Daten vollständig entfernt.

**Was trotzdem an externe Stellen geht (transparent, nichts versteckt):**

- ⚠️ **Anonyme Crash-Reports** zur Fehlerbehebung an Sentry (Frankfurt) — abschaltbar in *Profil → Crash-Reports*. Details: Abschnitt 4.3.
- ⚠️ **GPS-Koordinaten** an Open-Meteo (Schweiz) für UV-/Wetter-Daten, ohne User-Kennung. Details: Abschnitt 4.4.
- ⚠️ **Optional: Selfie-Foto** an Google Vertex AI (Frankfurt, via Cloudflare-Edge) — nur wenn du aktiv den KI-Scan startest. Details: Abschnitt 4.1.
- ⚠️ **Technische Verbindungs-Metadaten** (IP, User-Agent, ASN) bei Vertex-AI-Calls über Cloudflare-Edge zur Missbrauchs-Abwehr (max. 30 Tage gespeichert). Details: Abschnitt 4.2.

Alle vier sind in den folgenden Abschnitten 4.1-4.4 mit Auftragsverarbeiter, Verarbeitungsregion, Speicherdauer und Rechtsgrundlage dokumentiert.

---

## 4. Auftragsverarbeiter (Sub-Processors)

Mit allen unten genannten Auftragsverarbeitern bestehen Verträge zur Auftragsverarbeitung gemäß Art. 28 DSGVO. Die Vertragsdokumente liegen beim Verantwortlichen vor und können auf Anfrage eingesehen werden.

### 4.1 Google Cloud (Vertex AI · Frankfurt)

**Anbieter:** Google Ireland Limited, Gordon House, Barrow Street, Dublin 4, Irland (Hauptsitz EU). Konzernmutter: Google LLC, USA.

**Verarbeitungszweck:** KI-gestützte Einschätzung deines Hauttyps, Hauttons und deiner Augenfarbe anhand eines Selfie-Fotos. Das Ergebnis dient ausschließlich der Personalisierung deines individuellen Bräunungsplans (empfohlene Sonnenzeit pro Seite, Lichtschutzfaktor, optimales Bräunungsfenster).

**Übermittelte Daten:** Selfie-Foto (JPEG, base64-kodiert) + ein vom Verantwortlichen gestellter Text-Prompt. Es werden **keine** weiteren Profildaten, Standortdaten oder Geräte-IDs übertragen.

**Verarbeitungsregion:** `europe-west3` (Frankfurt am Main, Deutschland). Die Daten verlassen die Europäische Union nicht.

**Speicherdauer beim Auftragsverarbeiter:** Das Foto wird ausschließlich für die Dauer der Inferenz verarbeitet und **nicht gespeichert**. Eine Nutzung zum Training der zugrunde liegenden KI-Modelle ist gemäß Google Cloud Data Processing Addendum (DPA) ausgeschlossen.

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. a DSGVO i. V. m. Art. 9 Abs. 2 lit. a DSGVO (ausdrückliche Einwilligung).

**Einwilligungs-Mechanismus:** Vor dem ersten KI-gestützten Scan blendet die App einen modalen Einwilligungs-Dialog ein, der den Datenfluss (Cloudflare-Edge → Vertex AI Frankfurt), die Speicher- und Trainings-Garantien sowie die Möglichkeit eines Widerrufs konkret beschreibt. Der Dialog enthält eine **Pflicht-Bestätigungs-Checkbox** mit folgendem Wortlaut:

> *„Ich bin mindestens 16 Jahre alt und willige in die Verarbeitung meines Fotos durch Vertex AI Frankfurt gemäß Art. 9 DSGVO ein."*

Damit werden in einer einzigen aktiven Erklärung **zwei Tatsachen** bestätigt: (a) das Mindestalter im Sinne von Art. 8 DSGVO i. V. m. § 8 BDSG, sowie (b) die ausdrückliche Einwilligung in die Verarbeitung biometrieähnlicher Merkmale gem. Art. 9 Abs. 2 lit. a DSGVO. Erst nach aktivem Setzen des Hakens und Antippen des Buttons „Verstanden, einverstanden" beginnt die Verarbeitung. Der Einwilligungs-Nachweis wird mit Zeitstempel, Versionsnummer (`v1.1`), Locale, Mindestalter und Bestätigungs-Flag lokal im App-Speicher (`localStorage`-Schlüssel `sunny:aiConsent`) hinterlegt.

**Wichtiger Hinweis:** Der Modal erscheint **nur**, wenn der User aktiv den KI-Scan-Pfad wählt. User, die im Onboarding den alternativen Fragebogen-Pfad wählen, verarbeiten kein Foto und durchlaufen entsprechend keine Art. 9-Verarbeitung — eine separate Mindestalters-Bestätigung ist in diesem Fall nicht erforderlich, da keine besonders schützenswerten Daten verarbeitet werden.

**Widerruf:** Du kannst die Einwilligung jederzeit über *Profil → Daten zurücksetzen* aufheben. Beim nächsten Scan wird der Einwilligungs-Dialog erneut angezeigt. Alternativ kannst du den Scan vollständig überspringen (Fragebogen-Pfad mit identischem Ergebnis).

**Hinweis zu besonderen Kategorien (Art. 9 DSGVO):** Da das Selfie biometrieähnliche Merkmale enthalten kann, ist der oben beschriebene Einwilligungs-Mechanismus als ausdrückliche Einwilligung im Sinne von Art. 9 Abs. 2 lit. a DSGVO ausgestaltet. Die Verarbeitung dient nicht der eindeutigen Identifizierung einer Person, sondern ausschließlich der Hauttyp-Einschätzung im Wellness-Kontext.

**Vertragsdokumente:** Cloud Data Processing Addendum, Standard Contractual Clauses (EU C2P), Subprocessor-Liste — abrufbar unter https://cloud.google.com/terms/data-processing-addendum bzw. https://cloud.google.com/terms/subprocessors.

### 4.2 Cloudflare (Edge-Proxy)

**Anbieter:** Cloudflare, Inc., 101 Townsend St, San Francisco, CA 94107, USA. Vertretung in der EU: Cloudflare Germany GmbH, Rosental 7, 80331 München.

**Verarbeitungszweck:** Cloudflare betreibt einen **Edge-Worker als sicheren Proxy** zwischen der Sunly-App und Google Vertex AI. Diese Architektur ermöglicht es, den geheimen API-Schlüssel server-seitig vorzuhalten (statt im verteilten App-Bundle), was die Sicherheit der KI-Schnittstelle erheblich erhöht.

**Übermittelte Daten:**

- **Vom Foto-Scan-Vorgang:** Die unter 4.1 beschriebenen Foto- und Prompt-Daten werden für wenige Sekunden über den Cloudflare-Edge weitergeleitet (kein Caching, kein Logging des Bildinhalts).
- **Technische Verbindungsdaten:** Cloudflare verarbeitet im Rahmen der Anfrage-Weiterleitung typische HTTP-Metadaten (IP-Adresse, Zeitstempel, User-Agent, ASN) zur Missbrauchsabwehr und Rate-Limiting. Die IP wird ausschließlich kurzfristig vorgehalten und nicht mit anderen Datensätzen zusammengeführt.

**Verarbeitungsregion:** Cloudflare betreibt ein globales Edge-Netzwerk; das Routing erfolgt über die geografisch nächstgelegene Edge-Lokation, in der Regel innerhalb der EU.

**Speicherdauer:** Edge-Logs zur Missbrauchsabwehr werden gemäß Cloudflare-Standard-DPA für maximal 30 Tage vorgehalten und dann gelöscht.

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse an der Sicherheit der API-Schnittstelle und am Schutz vor Missbrauch).

**Vertragsdokumente:** Cloudflare Customer Data Processing Addendum, Sub-Processor-Liste — abrufbar unter https://www.cloudflare.com/cloudflare-customer-dpa/ bzw. https://www.cloudflare.com/gdpr/subprocessors/.

### 4.3 Sentry (Crash-Reporting · Frankfurt)

**Anbieter:** Functional Software, Inc. dba Sentry, 45 Fremont Street, 8th Floor, San Francisco, CA 94105, USA. Vertretung in der EU: Sentry GmbH, mit Sitz in Wien, Österreich (für EU-Kunden zuständige Konzern-Einheit).

**Verarbeitungszweck:** Erkennung und Behebung von Software-Fehlern, die zu Abstürzen oder unerwartetem Verhalten der App führen. Diese Daten ermöglichen Sicherheits- und Stabilitätsverbesserungen.

**Übermittelte Daten:**

- Stack-Trace und Fehlermeldung
- App-Version, Geräte-Modell, Betriebssystem-Version
- Browser-/WebView-Version, eingestellte Sprache
- Letzte Nutzer-Aktionen vor dem Fehler („Breadcrumbs" — anonymisiert, ohne Bildinhalte oder personenbezogene Profildaten)

**Nicht übermittelt werden:** IP-Adressen (in der Sentry-Konfiguration deaktiviert via `sendDefaultPii: false`), Foto-Inhalte, Profildaten (Hauttyp, Wunsch-Bräune o. Ä.), Standortdaten oder Authentifizierungsdaten.

**Verarbeitungsregion:** `ingest.de.sentry.io` (Frankfurt am Main, Deutschland). Die Datenspeicherregion wurde bei Sentry-Konto-Einrichtung explizit auf „European Union (EU)" festgelegt; eine spätere Änderung ist nicht möglich.

**Speicherdauer:** 30 Tage, danach automatische Löschung (Sentry-Free-Plan-Standard).

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse an der Stabilität und Sicherheit der App).

**Widerspruchsrecht (Art. 21 DSGVO):** Du kannst der Übermittlung von Crash-Reports jederzeit widersprechen, indem du in der App unter **Profil → Crash-Reports** den Schalter auf „Aus" stellst. Damit wird die Sentry-Bibliothek deaktiviert und es werden ab diesem Zeitpunkt keinerlei Crash-Daten mehr übertragen.

**Vertragsdokumente:** Sentry Data Processing Addendum (Version 5.1.0 oder höher) — vom Verantwortlichen formal akzeptiert.

### 4.4 Open-Meteo (Wetter- und UV-Daten)

**Anbieter:** Open-Meteo, Bundesgasse 5, 3011 Bern, Schweiz.

**Verarbeitungszweck:** Abruf des aktuellen UV-Index, des Wetters und der UV-Vorhersage für deinen Standort, um die Bräunungs- und Sonnenschutz-Empfehlungen zu personalisieren.

**Übermittelte Daten:** Geografische Koordinaten (Breiten- und Längengrad). Es wird **keine User-Kennung** übertragen — die Anfragen können einer Person nicht zugeordnet werden.

**Verarbeitungsregion:** Schweiz (gilt nach Art. 45 DSGVO i. V. m. dem Angemessenheitsbeschluss der EU-Kommission als sicherer Drittstaat).

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse an der Bereitstellung der Kernfunktion „UV-Tracking").

---

## 5. Lokale Datenverarbeitung in der App

Folgende Daten werden **ausschließlich auf deinem Endgerät** gespeichert (Android-`localStorage` und App-internes Filesystem) und niemals an externe Stellen übertragen, es sei denn, dies ist in dieser Erklärung ausdrücklich ausgeführt:

| Kategorie | Inhalt | Speicherort |
|---|---|---|
| Profil | Hauttyp, Augenfarbe, Geschlecht, Wunsch-Bräune, Lichtschutz-Präferenzen | localStorage |
| Sessions | Datum, Dauer, Streak, abgeschlossene Bräunungs-Sessions | localStorage |
| Fotos | Selfie-Verlauf für Bräunungs-Fortschritt (max. 50 Fotos) | App-Filesystem (Capacitor `Directory.DATA`) |
| Einstellungen | Sprache, Benachrichtigungs-Schalter, Vibrations-Schalter, Crash-Report-Opt-Out | localStorage |
| App-Cache | UV-Daten-Cache (15-Min-TTL), Geocoding-Cache | localStorage |

Diese lokalen Daten sind nur für dich und Personen mit Zugriff auf dein Gerät einsehbar. Bei Deinstallation der App werden sie vollständig entfernt.

---

## 6. Standortdaten

Wenn du der App den Standortzugriff gewährst, werden deine GPS-Koordinaten

- ausschließlich kurzzeitig im Gerätespeicher gehalten,
- nur an Open-Meteo (anonym, ohne Personenbezug) gesendet (siehe Abschnitt 4.4),
- nicht in Sunly-eigenen Logs oder externen Analysediensten gespeichert.

Du kannst den Standort-Zugriff jederzeit in den Android-Systemeinstellungen widerrufen. Ohne Standort funktioniert die App weiterhin, jedoch ohne ortsspezifische UV-Daten.

---

## 7. Push-Benachrichtigungen

Sunly verwendet **Android-LocalNotifications** für UV-Warnungen, tägliche Push-Updates und Routine-Benachrichtigungen. Diese werden **vollständig auf deinem Endgerät** geplant und ausgelöst — es gibt **keinen Push-Server** bei Sunly oder einem Drittanbieter (kein Firebase Cloud Messaging, kein OneSignal, kein APNS-Routing über externe Server).

Du kannst Benachrichtigungen jederzeit über das Profil-Menü („Benachrichtigungen") oder die Android-Systemeinstellungen abschalten.

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. a DSGVO (Einwilligung durch aktives Erlauben der Benachrichtigungs-Berechtigung beim ersten Aufruf).

---

## 8. Drittland-Übermittlungen

Wie in Abschnitt 4 beschrieben, sind die Verarbeitungen so konfiguriert, dass die Inferenz und Speicherung **innerhalb der Europäischen Union** stattfindet (Google Vertex AI in Frankfurt, Sentry in Frankfurt). Die EU-Konzernmütter (Google LLC, Functional Software/Sentry, Cloudflare Inc. — alle USA) können jedoch im Rahmen von Wartung und Support potenziell Zugriff auf die Verarbeitung haben.

Für solche Konstellationen liegen folgende Garantien vor:

- **EU Standard Contractual Clauses (SCCs)** gemäß Durchführungsbeschluss (EU) 2021/914 — Modul 2 (Controller-to-Processor)
- Bei Sentry zusätzlich: **EU-US Data Privacy Framework**-Zertifizierung
- Cloud-Provider-DPAs mit ausdrücklichem Verbot der Nutzung von Kundendaten zum Training von KI-Modellen oder anderen Sekundärzwecken

---

## 9. Speicherdauer

| Datenkategorie | Speicherdauer |
|---|---|
| Lokale Profil-/Session-/Foto-Daten | Bis zur Deinstallation der App durch dich |
| Foto bei Vertex AI Frankfurt | Nicht gespeichert (nur transiente Inferenz, < 5 Sekunden) |
| Cloudflare Edge-Logs | Max. 30 Tage |
| Sentry Crash-Reports | Max. 30 Tage |
| Open-Meteo Anfragen | Anonym, keiner Person zuordenbar |

Eine über diese Fristen hinausgehende Speicherung findet nicht statt.

---

## 10. Deine Rechte als Betroffener

Du hast nach DSGVO folgende Rechte:

- **Recht auf Auskunft (Art. 15)** — Information darüber, welche Daten wir über dich verarbeiten.
- **Recht auf Berichtigung (Art. 16)** — Korrektur unrichtiger Daten.
- **Recht auf Löschung (Art. 17, „Recht auf Vergessenwerden")** — Löschung deiner Daten.
- **Recht auf Einschränkung der Verarbeitung (Art. 18)**.
- **Recht auf Datenübertragbarkeit (Art. 20)** — Bereitstellung deiner Daten in maschinenlesbarem Format.
- **Recht auf Widerspruch (Art. 21)** — insbesondere gegen Verarbeitungen auf Grundlage berechtigter Interessen (z. B. Crash-Reporting via Sentry).
- **Recht auf Widerruf einer Einwilligung (Art. 7 Abs. 3)** — z. B. für die Foto-Analyse oder Push-Benachrichtigungen.
- **Recht auf Beschwerde bei einer Aufsichtsbehörde (Art. 77)** — insbesondere bei der zuständigen Landesdatenschutzbehörde Nordrhein-Westfalen:

> Die Landesbeauftragte für Datenschutz und Informationsfreiheit Nordrhein-Westfalen
> Postfach 20 04 44, 40102 Düsseldorf
> Telefon: +49 211 38424-0
> E-Mail: poststelle@ldi.nrw.de
> Website: https://www.ldi.nrw.de

**Praktische Umsetzung:** Da Sunly keine Server-seitige Nutzer-Datenbank betreibt, lassen sich Auskunfts- und Löschungs-Begehren in den meisten Fällen durch Deinstallation der App vollständig erfüllen. Für Daten bei den Auftragsverarbeitern (Google, Cloudflare, Sentry) wende dich bitte an die in Abschnitt 1 genannten Kontaktdaten — wir leiten dein Anliegen unverzüglich an den jeweiligen Auftragsverarbeiter weiter.

---

## 11. Automatisierte Entscheidungsfindung (Art. 22 DSGVO)

Die KI-basierte Hauttyp-Einschätzung gemäß Abschnitt 4.1 stellt **keine** automatisierte Entscheidungsfindung mit rechtlicher Wirkung im Sinne von Art. 22 DSGVO dar:

- Das Ergebnis wird dir lediglich als Empfehlung angezeigt
- Du kannst das Ergebnis jederzeit verwerfen oder den Hauttyp manuell anpassen (Profil → Hauttyp)
- Es entstehen keine rechtlichen Konsequenzen oder erheblichen Beeinträchtigungen

Die Verarbeitung dient ausschließlich der Personalisierung von Wellness-Empfehlungen.

---

## 12. Cookies

Die Sunly-App ist eine native Android-Anwendung und verwendet **keine Cookies**. Die in der WebView zugrunde liegende Speichertechnologie (`localStorage`) wird ausschließlich für lokale App-Zustandsverwaltung genutzt und nicht an externe Stellen übertragen.

---

## 13. Datensicherheit

Wir treffen folgende technische und organisatorische Maßnahmen:

- **Transport-Verschlüsselung (TLS 1.2+)** für alle externen API-Verbindungen
- **OAuth 2.0 / Service-Account-Authentifizierung** für die Vertex-AI-Schnittstelle (kein API-Schlüssel im verteilten App-Bundle)
- **Cloudflare-Edge-Schutz** mit IP-basiertem Rate-Limiting (30 Anfragen pro Stunde) und Web Application Firewall
- **Lokale Foto-Speicherung** im sandboxed Capacitor-Filesystem (kein Zugriff durch andere Apps)
- **Crash-Report-Filter** (`beforeSend`-Hook) entfernt automatisch potenzielle Bilddaten aus Stack-Traces vor der Übermittlung an Sentry
- **Production-Log-Gate** unterdrückt im Release-Build alle nicht-essentiellen Console-Ausgaben

---

## 14. Aktualität und Änderung dieser Datenschutzerklärung

Diese Datenschutzerklärung ist aktuell gültig in der oben genannten Version (Stand: 8. Mai 2026). Durch die Weiterentwicklung der App oder rechtliche Änderungen kann eine Anpassung erforderlich werden. Die jeweils aktuelle Datenschutzerklärung kann jederzeit im Profil-Menü unter „Datenschutz" eingesehen werden.

---

**Ende der Datenschutzerklärung**
