---
title: Datenschutzerklärung
layout: page
---

# Datenschutzerklärung — Sunly

**Stand:** 9. Mai 2026 · **Version:** 1.8

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

Sunly ist als **datensparsame, lokal arbeitende App** konzipiert.

**Was Sunly NICHT hat:**

- ❌ **Keinen Cloud-Account und keine Server-User-Datenbank** bei Sunly selbst
- ❌ **Keine Anmeldung, keinen Login, keine E-Mail-Adresse** beim Anbieter
- ❌ **Kein Marketing-/Verhaltens-Tracking, keine Werbe-IDs**, keine klassischen Analytics-Tools (Google Analytics, Firebase Analytics, AppsFlyer o. Ä.)
- ❌ **Keinen Push-Server** (kein Firebase Cloud Messaging, kein OneSignal) — alle Benachrichtigungen werden lokal auf dem Gerät geplant

**Was lokal auf deinem Gerät bleibt (verlässt es nie):**

- ✅ **Profil**: Hauttyp, Augenfarbe, Geschlecht, Wunsch-Bräune, Einstellungen
- ✅ **Sessions**: Bräunungs-History, Streaks, Vitamin-D-Schätzungen
- ✅ **Verlaufs-Fotos**: bis zu 50 Selfies, die du selbst für den Bräunungs-Fortschritt speicherst (Capacitor `Directory.DATA`)
- ✅ **Einwilligungs-Nachweise und App-Cache** (UV-Daten-Cache, Geocoding-Cache)

Bei Deinstallation der App werden alle diese lokalen Daten vollständig entfernt.

**Was an externe Stellen geht (transparent, nichts versteckt):**

- ⚠️ **KI-Scan-Foto**: Wenn du den optionalen KI-Hauttyp-Scan aktiv startest, wird das Selfie an Google Vertex AI (Frankfurt) gesendet — ausschließlich für die Analyse, **nicht dort gespeichert**, nicht zum KI-Training verwendet (Google Cloud DPA). Details: Abschnitt 4.1.
- ⚠️ **Anonyme Crash-Reports** zur Fehlerbehebung an Sentry (Frankfurt) — abschaltbar in *Profil → Crash-Reports*. Details: Abschnitt 4.3.
- ⚠️ **GPS-Koordinaten** an Open-Meteo (Schweiz) für UV-/Wetter-Daten, ohne User-Kennung. Details: Abschnitt 4.4.
- ⚠️ **Technische Verbindungs-Metadaten** (IP, User-Agent, ASN) bei KI-Scan-Calls über Cloudflare-Edge zur Missbrauchs-Abwehr (max. 30 Tage Edge-Logs). Details: Abschnitt 4.2.

Alle vier externen Datenflüsse sind in den folgenden Abschnitten 4.1-4.4 mit Auftragsverarbeiter, Verarbeitungsregion, Speicherdauer und Rechtsgrundlage einzeln dokumentiert.

---

## 4. Auftragsverarbeiter (Sub-Processors)

Mit allen unten genannten Auftragsverarbeitern bestehen Verträge zur Auftragsverarbeitung gemäß Art. 28 DSGVO. Die Vertragsdokumente liegen beim Verantwortlichen vor und können auf Anfrage eingesehen werden.

### 4.1 Google Cloud (Vertex AI · Frankfurt)

**Anbieter:** Google Ireland Limited, Gordon House, Barrow Street, Dublin 4, Irland (Hauptsitz EU). Konzernmutter: Google LLC, USA.

**Was verarbeitet wird — und was ausdrücklich NICHT:**

*Verarbeitet werden:*

- Ein vom Nutzer aktiv erstelltes Selfie (Gesichts-Foto, JPEG)
- Optional: die im Onboarding gegebenen Antworten zur Hauttyp-Selbst­einschätzung (alternativer Pfad ohne Foto, falls der Nutzer den Scan ablehnt)

*Was die App ausdrücklich NICHT tut:*

- Es werden **keine biometrischen Identifikatoren** im Sinne von Art. 4 Nr. 14 DSGVO erstellt oder gespeichert
- Es werden **keine Gesichtserkennungs-Templates / Face-Embeddings / FaceIDs** angelegt
- Es findet **keine Identitäts-Verifikation** statt
- Es wird **kein biometrischer Abgleich gegen eine Datenbank** durchgeführt
- Das Foto wird **nicht zur Wiedererkennung** des Nutzers bei späteren Sitzungen verwendet
- Das Foto wird **nicht zum KI-Modell-Training** weitergegeben (Google Cloud DPA)
- Es werden **keine emotionalen, gesundheitlichen oder psychologischen Bewertungen** abgeleitet

**Verarbeitungszweck:** KI-gestützte Einschätzung deines Hauttyps (Fitzpatrick I–VI), Hauttons und deiner Augenfarbe anhand eines Selfie-Fotos. Das Ergebnis dient ausschließlich der Personalisierung deines individuellen Bräunungsplans (empfohlene Sonnenzeit pro Seite, Lichtschutzfaktor, optimales Bräunungsfenster).

**Wofür das Foto verwendet wird:**

Das Selfie wird ausschließlich genutzt, um:

- sichtbare Hautmerkmale zu analysieren (Hautton, Rötungen, Tan-Linien, Augenfarbe)
- einen personalisierten Bräunungs- und Sonnenschutz-Plan in der App zu erstellen

**Wofür das Foto NICHT verwendet wird:**

- Gesichtserkennung oder biometrische Identifikation
- Nutzer-Wiedererkennung über Sitzungen hinweg
- Werbung, Marketing oder Profiling außerhalb der Bräunungs-Personalisierung
- Weiterverkauf, Vermietung oder kommerzielle Verwertung der Bilddaten
- KI-Modell-Training (vertraglich durch Google Cloud DPA ausgeschlossen)

**Übermittelte Daten:** Selfie-Foto (JPEG, base64-kodiert), ein vom Verantwortlichen gestellter Text-Prompt sowie die App-Sprache (`de` oder `en`, damit die KI die Begründung in der richtigen Sprache liefert). Es werden **keine** weiteren Profildaten (Hauttyp, Augenfarbe etc.), Standortdaten oder persistenten Geräte-IDs übertragen.

**Verarbeitungsregion:** `europe-west3` (Frankfurt am Main, Deutschland). Die Daten verlassen die Europäische Union nicht.

**Speicherung und Aufbewahrung:**

- **Bei Vertex AI Frankfurt:** Das Foto wird ausschließlich für die Dauer der Inferenz (typisch < 5 Sekunden) verarbeitet und **nicht gespeichert**. Eine Nutzung zum Training der zugrunde liegenden KI-Modelle ist gemäß Google Cloud Data Processing Addendum (DPA) ausgeschlossen.
- **Bei Sunly:** Sunly betreibt keine eigenen Server, auf denen Foto- oder Analyse-Daten landen könnten. Lediglich das Analyse-Ergebnis (Hauttyp, Hautton, Augenfarbe als Klartext-Werte) wird auf deinem Gerät lokal gespeichert.
- **Lokal auf deinem Gerät:** Du kannst Analyse-Ergebnisse jederzeit über *Profil → Daten zurücksetzen* löschen — alle Werte und Einwilligungs-Records werden dann entfernt.

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. a DSGVO i. V. m. Art. 9 Abs. 2 lit. a DSGVO (ausdrückliche Einwilligung).

**Einwilligungs-Mechanismus:** Vor dem ersten KI-gestützten Scan blendet die App einen modalen Einwilligungs-Dialog ein, der den Datenfluss (Cloudflare-Edge → Vertex AI Frankfurt), die Speicher- und Trainings-Garantien sowie die Möglichkeit eines Widerrufs konkret beschreibt. Der Dialog enthält:

- den Titel „🤖 KI-Foto-Analyse" / „🤖 AI photo analysis",
- eine kurze Beschreibung des Datenflusses („Dein Selfie wird kurz von Vertex AI in Frankfurt analysiert — nicht gespeichert."),
- einen ausdrücklichen Disclaimer mit dem Wortlaut: *„Mit ‚Einverstanden' akzeptierst du die [Datenschutzerklärung] und [Nutzungsbedingungen] von Sunly (16+)."* — die in eckigen Klammern angezeigten Links öffnen die jeweiligen Volltexte direkt in der App,
- einen primären Aktions-Button **„Einverstanden"** / **„I agree"** (gelb, prominent),
- optional einen sekundären „Lieber Fragen beantworten"-Button (Onboarding-Pfad), der die KI-Analyse vollständig umgeht.

Erst durch das aktive Antippen des „Einverstanden"-Buttons werden **zwei Tatsachen** in einer Erklärung bestätigt: (a) das Mindestalter im Sinne von Art. 8 DSGVO i. V. m. § 8 BDSG („16+"), sowie (b) die ausdrückliche Einwilligung in die Verarbeitung biometrieähnlicher Merkmale gem. Art. 9 Abs. 2 lit. a DSGVO. Diese Konstruktion (eindeutiger primärer Button mit verlinktem Disclaimer) gilt nach Erwägungsgrund 32 DSGVO als „eindeutige bestätigende Handlung" und damit als gültige Einwilligungsform.

Der Einwilligungs-Nachweis wird mit Zeitstempel, Versionsnummer (`v1.2`), Locale, Mindestalter-Flag (`ageConfirmed: true`, `minimumAge: 16`) und Flow-Kennung (`flow: 'minimal-button'`) lokal im App-Speicher (`localStorage`-Schlüssel `sunny:aiConsent`) hinterlegt.

**Wichtiger Hinweis:** Der Modal erscheint **vor jedem ersten KI-Scan-Versuch — unabhängig von der App-Sprache**. User, die im Onboarding den alternativen Fragebogen-Pfad wählen, verarbeiten kein Foto und durchlaufen entsprechend keine Art. 9-Verarbeitung — eine separate Mindestalters-Bestätigung ist in diesem Fall nicht erforderlich, da keine besonders schützenswerten Daten verarbeitet werden.

**Widerruf:** Du kannst die Einwilligung jederzeit über *Profil → Daten zurücksetzen* aufheben. Beim nächsten Scan wird der Einwilligungs-Dialog erneut angezeigt. Alternativ kannst du den Scan vollständig überspringen (Fragebogen-Pfad mit identischem Ergebnis).

**Hinweis zu besonderen Kategorien (Art. 9 DSGVO):** Da das Selfie biometrieähnliche Merkmale enthalten kann, ist der oben beschriebene Einwilligungs-Mechanismus als ausdrückliche Einwilligung im Sinne von Art. 9 Abs. 2 lit. a DSGVO ausgestaltet. Die Verarbeitung dient nicht der eindeutigen Identifizierung einer Person, sondern ausschließlich der Hauttyp-Einschätzung im Wellness-Kontext.

**Hinweis zur Fitzpatrick-Klassifikation:** Die in der KI-Antwort genutzte Fitzpatrick-Skala (I–VI) ist ursprünglich ein dermatologischer Standard. Sunly verwendet sie ausschließlich im **Wellness-/Lifestyle-Kontext** als statistische Schätzung zur Personalisierung des Bräunungs-Plans — sie ersetzt **nicht** die ärztliche Hauttyp-Bestimmung, ist **keine medizinische Diagnose** und Sunly ist **kein Medizinprodukt** im Sinne der Verordnung (EU) 2017/745 (MDR). Du kannst das Ergebnis jederzeit manuell überschreiben (siehe Abschnitt 11).

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

### 4.4 Open-Meteo (Wetter-, UV- und Geocoding-Daten)

**Anbieter:** Open-Meteo, Bundesgasse 5, 3011 Bern, Schweiz.

**Verarbeitungszweck:**

- Abruf des aktuellen UV-Index, des Wetters und der UV-Vorhersage für deinen Standort (`api.open-meteo.com`).
- Abruf der Luftqualitäts-Daten ergänzend zum Wetter (`air-quality-api.open-meteo.com`).
- Auflösung von Stadt-Namen zu Koordinaten, wenn du in der App manuell eine Stadt suchst (`geocoding-api.open-meteo.com`).

**Übermittelte Daten:**

- Bei automatischem GPS-Pfad: geografische Koordinaten (Breiten- und Längengrad).
- Bei manueller Stadt-Suche: der von dir eingegebene Stadt-Name (z. B. „München") plus Locale.

Es wird in beiden Fällen **keine User-Kennung** übertragen — die Anfragen können keiner Person zugeordnet werden.

**Verarbeitungsregion:** Schweiz (gilt nach Art. 45 DSGVO i. V. m. dem Angemessenheitsbeschluss der EU-Kommission als sicherer Drittstaat).

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse an der Bereitstellung der Kernfunktion „UV-Tracking").

### 4.5 Web-Fonts (Google Fonts und Fontshare)

**Anbieter:**

- **Google Fonts** — Google Ireland Limited, Gordon House, Barrow Street, Dublin 4, Irland (für Manrope, Outfit, Roboto Mono, Inter via `fonts.googleapis.com`).
- **Fontshare** — Indian Type Foundry Pvt. Ltd., 11 Lalita Park, Laxmi Nagar, Delhi 110092, Indien (für Satoshi und Cabinet Grotesk via `api.fontshare.com`).

**Verarbeitungszweck:** Auslieferung der Schriftarten für die App-UI beim ersten Start. Die `display=optional`-Strategie sorgt dafür, dass beim Verbindungsabbruch nach ~100 ms die System-Schriftart genutzt wird (kein Layout-Shift).

**Übermittelte Daten:** IP-Adresse, User-Agent, Referrer (von der WebView).

**Verarbeitungsregion:** Globale CDN-Netze (Google: u. a. EU; Fontshare: u. a. EU/USA/Indien). Bei Fontshare ist Indien betroffen — kein Adäquanzbeschluss; Fontshare beruft sich auf eigene Standardvertragsklauseln (siehe Fontshare-Privacy-Policy).

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse an einheitlicher, lesbarer Typografie).

**Aktuell geplante Mitigation:** Schriftarten werden in einer kommenden Version lokal in das App-Bundle integriert, sodass dieser Datenfluss vollständig entfällt.

### 4.6 OpenStreetMap Foundation (Reverse-Geocoding)

**Anbieter:** OpenStreetMap Foundation, St John's Innovation Centre, Cowley Road, Cambridge, CB4 0WS, Vereinigtes Königreich.

**Verarbeitungszweck:** Reverse-Geocoding von GPS-Koordinaten zu lesbaren Stadt-Namen über den `nominatim.openstreetmap.org`-Endpunkt (z. B. „48.13, 11.58" → „München, DE"). Wird ergänzend zu Open-Meteo eingesetzt, weil Nominatim für die UI-Anzeige präzisere Stadt-Bezeichnungen liefert.

**Übermittelte Daten:** Breiten- und Längengrad, Locale, statischer User-Agent (`Sunly/1.0`). Keine User-Kennung.

**Verarbeitungsregion:** Vereinigtes Königreich (gilt nach Art. 45 DSGVO i. V. m. dem UK-Angemessenheitsbeschluss vom 28. Juni 2021 als sicherer Drittstaat).

**Speicherdauer:** Nominatim führt Standard-Webserver-Logs gemäß OSMF-Privacy-Policy (max. 14 Tage). Anfragen werden anschließend gelöscht.

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse an präziser Stadt-Namens-Anzeige im UI).

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

## 7. Push-Benachrichtigungen und Step-Vibrationen

Sunly verwendet **Android-LocalNotifications** und das System-`AlarmManager.setAlarmClock()`-API für UV-Warnungen, tägliche Push-Updates, Routine-Benachrichtigungen und Bräunungs-Step-Vibrationen. Diese werden **vollständig auf deinem Endgerät** geplant und ausgelöst — es gibt **keinen Push-Server** bei Sunly oder einem Drittanbieter (kein Firebase Cloud Messaging, kein OneSignal, kein APNS-Routing über externe Server).

Du kannst Benachrichtigungen jederzeit über das Profil-Menü („Benachrichtigungen") oder die Android-Systemeinstellungen abschalten.

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. a DSGVO (Einwilligung durch aktives Erlauben der Benachrichtigungs-Berechtigung beim ersten Aufruf).

### 7.1 Sekundengenaue Step-Vibrationen (`SCHEDULE_EXACT_ALARM`, Spezial-App-Zugriff)

Bräunungs-Step-Timer müssen sekundengenau auslösen, weil zu lange UV-Exposition zu Hautrötungen oder Sonnenbrand führen kann. Damit Android das System-Wecker-API von Sunly mit garantiert exakter Zeitstellung bedient — auch im Standby-Modus — deklariert die App die Berechtigung `SCHEDULE_EXACT_ALARM`.

**Eigenschaften der Berechtigung:**

- **Zweck:** Erlaubt der App ausschließlich, mit `AlarmManager.setAlarmClock()` und `setExactAndAllowWhileIdle()` sekundengenaue lokale Wecker-Alarme für das jeweils nächste Step-Ende einer aktiven Bräunungs-Session zu planen. Ohne diese Berechtigung würde Android ab Version 12 (API 31) Alarme um bis zu 15 Minuten zeitlich nach hinten gruppieren — für einen Bräunungs-Timer unbrauchbar.
- **Keine Hintergrund-Datenverarbeitung:** Die Berechtigung erlaubt **keinerlei** Hintergrund-Datenverarbeitung, **kein** Tracking, **kein** Verlängern der App-Laufzeit. Sie wirkt rein zeitlich-präzise auf lokale Alarme, die du selbst gestartet hast.
- **Wann ist die Berechtigung aktiv:** Auf Android 12 und 13 (API 31–33) wird `SCHEDULE_EXACT_ALARM` für Apps, die sie im Manifest deklarieren, beim ersten App-Start automatisch durch das System gewährt. Auf Android 14+ (API 34+) ist sie bei Neuinstallationen standardmäßig deaktiviert; du kannst sie jederzeit unter *Einstellungen → Apps → Sunly → Spezieller App-Zugriff → Wecker und Erinnerungen* aktivieren oder widerrufen.
- **Funktioniert auch ohne:** Wird die Berechtigung verweigert, nutzt die App das System-Wecker-API (`AlarmManager.setAlarmClock()`) als bevorzugten Pfad — diese API ist auch ohne Spezial-Berechtigung doze-bypass-fähig, weil sie wie ein klassischer Wecker behandelt wird. Vibrationen im Vordergrund (App geöffnet) sind in jedem Fall punktgenau, da das Timing dann durch JavaScript getrieben wird.

**Hinweis zur entfallenen Akku-Ausnahme:** Frühere Versionen der App (≤ 1.1.31) verwendeten die Berechtigung `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS`, um auf restriktiven OEM-Modi (Samsung, Xiaomi) die Verzögerung von Vibrations-Alarmen zu vermeiden. Diese Berechtigung wurde in Version 1.1.32 entfernt und durch die Kombination aus `SCHEDULE_EXACT_ALARM` und einem 5-Sekunden-WakeLock im Alarm-Receiver ersetzt — funktional gleichwertig, aber datenschutzfreundlicher und ohne Eingriff in die System-Akku-Strategie.

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. a DSGVO (Einwilligung) bzw. Art. 6 Abs. 1 lit. b DSGVO (Vertragserfüllung — die sekundengenaue Step-Vibration ist Kernfunktion der App). Auf Android 13+ ist keine separate Nutzer-Aktion erforderlich; auf Android 12 wird der Spezial-App-Zugriff vom System bei der Installation automatisch gewährt und kann jederzeit widerrufen werden.

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
- **OAuth 2.0 / Service-Account-Authentifizierung** für die Vertex-AI-Schnittstelle: der Google-Service-Account-Key liegt ausschließlich auf dem Cloudflare-Worker (als Worker-Secret), **nicht** im verteilten App-Bundle. Im App-Bundle existiert lediglich ein einfacher Worker-Shared-Key, der KEINE Google-Cloud-Authentifizierung ermöglicht — er dient nur dazu, fremde Direktaufrufe gegen den Worker-Endpunkt zu erschweren (Soft-Schutz, kein Auth-Mechanismus).
- **Cloudflare-Edge-Schutz** mit IP-basiertem Rate-Limiting (30 Anfragen pro Stunde) und Web Application Firewall
- **Lokale Foto-Speicherung** im sandboxed Capacitor-Filesystem (kein Zugriff durch andere Apps)
- **Crash-Report-Filter** (`beforeSend`-Hook) entfernt automatisch potenzielle Bilddaten aus Stack-Traces vor der Übermittlung an Sentry
- **Production-Log-Gate** unterdrückt im Release-Build alle nicht-essentiellen Console-Ausgaben

---

## 14. Aktualität und Änderung dieser Datenschutzerklärung

Diese Datenschutzerklärung ist aktuell gültig in der oben genannten Version (Stand: 9. Mai 2026, Version 1.8). Durch die Weiterentwicklung der App oder rechtliche Änderungen kann eine Anpassung erforderlich werden. Die jeweils aktuelle Datenschutzerklärung kann jederzeit im Profil-Menü unter „Datenschutz" eingesehen werden.

**Änderungen in v1.8 gegenüber v1.7 (9. Mai 2026, App-Version 1.1.32):**

- Abschnitt 7.1 grundlegend überarbeitet: Die opt-in `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS`-Permission wurde **vollständig entfernt** und durch die `SCHEDULE_EXACT_ALARM`-Berechtigung ersetzt. Diese ist klassisch ein „Spezieller App-Zugriff" und für Timer-/Wecker-Apps der vom Google Play Store ausdrücklich vorgesehene Weg.
- Zusätzlich wurde der WakeLock im Alarm-Receiver von 3 auf 5 Sekunden verlängert, sodass auf aggressiv-optimierten OEMs (Samsung One UI, Xiaomi MIUI) der Vibrationsmotor und die Step-End-Notification zuverlässig vollständig verarbeitet werden, bevor das System in den Tiefschlaf zurückfällt.
- Architektur-Begründung: Die alte Akku-Ausnahme galt im Play Console als HIGH-Risk-Permission und hätte beim Review zu längeren Genehmigungs-Schleifen führen können. Die neue Kombination aus `SCHEDULE_EXACT_ALARM` + verlängerter WakeLock erreicht dasselbe Ergebnis — pünktliche Step-Vibrationen auch im Standby — ohne in die System-Akku-Strategie einzugreifen.

**Änderungen in v1.7 gegenüber v1.6 (9. Mai 2026):**

- Neuer Abschnitt 7.1 „Akku-Ausnahme für punktgenaue Step-Vibrationen" — beschreibt die opt-in `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS`-Permission, die ausschließlich beim aktiven Aktivieren der Routine-Vibration angefragt wird (nicht automatisch). *(In v1.8 vollständig durch `SCHEDULE_EXACT_ALARM` ersetzt.)*
- Architektur-Hintergrund: Vorher implementierte App den Step-Timer über einen Foreground-Service mit `FOREGROUND_SERVICE_SPECIAL_USE`-Permission. Diese wurde durch den Play-Store-konformen `AlarmManager.setAlarmClock()`-Mechanismus ersetzt — daraus resultiert die Notwendigkeit der opt-in Akku-Ausnahme für punktgenaue Background-Trigger auf restriktiven OEMs (Samsung etc.).
- Section 7 Titel erweitert von „Push-Benachrichtigungen" auf „Push-Benachrichtigungen und Step-Vibrationen", weil der Mechanismus jetzt auch lokale Step-End-Alerts via `AlarmManager` umfasst.

**Änderungen in v1.6 gegenüber v1.5 (8. Mai 2026 — finaler Pre-Submission-Audit):**

- Abschnitt 4.1 ergänzt um „Hinweis zur Fitzpatrick-Klassifikation" — explizite Wellness-/Lifestyle-Disambiguierung; klarstellt dass Fitzpatrick I–VI nur als statistische Schätzung im Wellness-Kontext genutzt wird, keine medizinische Diagnose, kein Medizinprodukt im Sinne der MDR.
- Abschnitt 4.4 ergänzt: Subdomain `air-quality-api.open-meteo.com` für Luftqualitäts-Daten — vorher implizit unter „api.open-meteo.com" subsumiert, jetzt explizit gelistet.

**Änderungen in v1.5 gegenüber v1.4 (8. Mai 2026):**

- Neuer Abschnitt 15 „Links zu Drittseiten" mit klarer Haftungs-Abgrenzung für externe Verlinkungen.
- Neuer Abschnitt 16 „Datenschutz für Minderjährige (Kinder-Datenschutz)" mit ausdrücklicher 16+-Bestätigung, expliziter Nicht-Sammlung-von-Kinderdaten-Zusage und Eltern-Kontakt-Pfad. Format orientiert an Apple/Google-Play-Erwartungen für Kinderschutz-Disclaimer.

**Änderungen in v1.4 gegenüber v1.3 (8. Mai 2026):**

- Abschnitt 4.1 ergänzt um zwei zusätzliche Sub-Blöcke nach approved-template-Format (Apple/Play Store): „Wofür das Foto verwendet wird" (positive Liste: Hautton, Rötungen, Tan-Linien, Augenfarbe → personalisierter Plan) und „Wofür das Foto NICHT verwendet wird" (negative Liste: Gesichtserkennung, Wiedererkennung, Werbung, Weiterverkauf, Modell-Training).
- Abschnitt 4.1 strukturiert „Speicherung und Aufbewahrung" als eigenen konsolidierten Block mit drei Speicher-Layern (Vertex AI / Sunly-Server / Lokal auf Gerät) inkl. expliziter Lösch-Anweisung.

**Änderungen in v1.3 gegenüber v1.2 (8. Mai 2026):**

- Abschnitt 4.1 ergänzt um expliziten Block „Was verarbeitet wird — und was ausdrücklich NICHT": Zweck-Begrenzung der Foto-Analyse (kein biometrischer Identifikator, kein Face-Embedding, keine Identitäts-Verifikation, kein DB-Abgleich, keine Wiedererkennung, keine emotionale/gesundheitliche Bewertung). Format orientiert sich an Play-Store-Data-Safety- und Apple-App-Privacy-Anforderungen für transparente Scope-Begrenzung von Foto-/KI-Features.

**Änderungen in v1.2 gegenüber v1.1 (8. Mai 2026):**

- Abschnitt 3 strukturiert in „Was Sunly nicht hat" / „Was lokal bleibt" / „Was an externe Stellen geht" — Foto-Datenfluss klar getrennt nach Verlaufs-Foto vs. KI-Scan-Foto.
- Abschnitt 4.1 ergänzt: Locale wird mit zur Vertex-AI-Inferenz übermittelt; Einwilligungs-Mechanismus präzise als „eindeutiger primärer Button mit verlinktem Disclaimer" beschrieben (statt „Pflicht-Bestätigungs-Checkbox"); Modal erscheint unabhängig von der App-Sprache.
- Abschnitt 4.4 ergänzt: Stadt-Name als alternativer Such-Parameter neben Koordinaten.
- Neuer Abschnitt 4.5 (Web-Fonts: Google Fonts + Fontshare).
- Neuer Abschnitt 4.6 (OpenStreetMap-Reverse-Geocoding).
- Abschnitt 13 präzisiert: Differenzierung Service-Account-Key (Worker-Secret) vs. Worker-Shared-Key (Soft-Schutz im Bundle).

---

## 15. Links zu Drittseiten

Diese Datenschutzerklärung sowie einzelne In-App-Bereiche (z. B. die App-Information, Vertragsdokumenten-Verlinkungen) können Verweise zu externen Webseiten enthalten — u. a. zu den Datenschutz-Erklärungen von Google Cloud, Cloudflare, Sentry, Open-Meteo, Fontshare und der OpenStreetMap Foundation.

Diese externen Seiten werden **nicht vom Anbieter betrieben**. Der Anbieter hat keinen Einfluss auf deren Inhalte, Verfügbarkeit und Datenschutz-Praktiken. Wir empfehlen ausdrücklich, die jeweiligen Datenschutz-Erklärungen der verlinkten Drittseiten vor deren Nutzung zu lesen.

Eine Haftung für die Inhalte verlinkter Drittseiten wird im gesetzlich zulässigen Rahmen ausgeschlossen.

---

## 16. Datenschutz für Minderjährige (Kinder-Datenschutz)

Sunly richtet sich ausschließlich an Personen ab **16 Jahren**. Die App ist nicht für die Nutzung durch Kinder unter 16 bestimmt:

- Im KI-Hauttyp-Scan-Pfad bestätigt der Nutzer aktiv das Mindestalter über den Einwilligungs-Modal (siehe Abschnitt 4.1).
- Im Fragebogen-Pfad ist die Volljährigkeit Bestandteil der akzeptierten Nutzungsbedingungen (Abschnitt 7 der Nutzungsbedingungen).
- Es gibt keine altersgerechten Inhalte oder Funktionen, die gezielt Kinder ansprechen würden.

**Wir sammeln nicht wissentlich personenbezogene Daten von Kindern unter 16 Jahren.** Sollten wir Kenntnis davon erlangen, dass solche Daten an einen unserer Auftragsverarbeiter (z. B. via KI-Scan-Foto) übermittelt wurden, werden wir die Verarbeitung bei dem betroffenen Auftragsverarbeiter unverzüglich anstoßen, alle entsprechenden Daten löschen zu lassen.

**An Eltern oder Erziehungsberechtigte:** Falls du den begründeten Verdacht hast, dass dein Kind unter 16 die App genutzt und dabei personenbezogene Daten übermittelt hat, wende dich bitte umgehend an mail@mariusbecker.me. Wir werden den Sachverhalt unverzüglich prüfen und alle relevanten Daten bei den Auftragsverarbeitern löschen lassen.

---

**Ende der Datenschutzerklärung**
