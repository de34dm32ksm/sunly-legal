---
title: Privacy Policy
layout: page
---

# Privacy Policy — Sunly

**Last updated:** June 2, 2026 · **Version:** 1.9

> **Note:** This is the English translation of the German privacy policy. In the event of any conflict or inconsistency, the German version (`Sunly_Datenschutzerklaerung_DE.md`) prevails.

---

## 1. Controller

The controller within the meaning of the General Data Protection Regulation (GDPR) and other national data protection laws of the Member States, as well as other data protection regulations, is:

**Marius Alexander Becker**
Schleusingerstraße 41
58840 Plettenberg
Germany

Email: mail@mariusbecker.me

Sunly is operated privately and on a non-commercial basis. There is no statutory obligation to appoint a Data Protection Officer (Art. 37 GDPR) as the relevant thresholds are not exceeded.

---

## 2. Scope

This Privacy Policy applies to the **Sunly** mobile application (hereinafter "the App") for **Android and iOS**, published under the application/bundle ID `com.mariusbecker.sunly`. It informs users (hereinafter "you") about the nature, scope and purpose of the processing of personal data. On iOS, the App uses the `UNUserNotificationCenter` API for local notifications — the `SCHEDULE_EXACT_ALARM` permission described in Section 7.1 is Android-specific and does not apply on iOS.

The App is exclusively for wellness and lifestyle purposes (UV index tracking, tanning planning, vitamin D estimation). It is **not a medical device** within the meaning of Regulation (EU) 2017/745 (MDR) and does not replace any medical advice, diagnosis or treatment.

---

## 3. Principle: Local Data Storage

Sunly is designed as a **data-minimal, locally operating app**.

**What Sunly does NOT have:**

- ❌ **No cloud account and no server-side user database** at Sunly
- ❌ **No login, no registration, no email collection** on our side
- ❌ **No marketing/behavioral tracking, no advertising IDs**, no classic analytics tools (Google Analytics, Firebase Analytics, AppsFlyer, etc.)
- ❌ **No push server** (no Firebase Cloud Messaging, no OneSignal) — all notifications are scheduled locally on your device

**What stays local on your device (never leaves it):**

- ✅ **Profile**: skin type, eye color, gender, desired tan, settings
- ✅ **Sessions**: tanning history, streaks, vitamin D estimates
- ✅ **Progress photos**: up to 50 selfies that you yourself save for tanning progress comparison (Capacitor `Directory.DATA`)
- ✅ **Consent records and app cache** (UV-data cache, geocoding cache)

When you uninstall the App, all this local data is completely removed.

**What does leave your device (full transparency, nothing hidden):**

- ⚠️ **AI scan photo**: when you actively start the optional AI skin-type scan, the selfie is sent to Google Vertex AI (Frankfurt) — for analysis only, **not stored there**, not used for AI model training (Google Cloud DPA). Details: Section 4.1.
- ⚠️ **Anonymous crash reports** for bug fixing, sent to Sentry (Frankfurt) — switchable off in *Profile → Crash reports*. Details: Section 4.3.
- ⚠️ **GPS coordinates** to Open-Meteo (Switzerland) for UV / weather data, without any user identifier. Details: Section 4.4.
- ⚠️ **Technical connection metadata** (IP, user agent, ASN) on AI-scan calls through the Cloudflare edge for abuse prevention (max. 30 days edge logs). Details: Section 4.2.

All four external data flows are individually documented in Sections 4.1-4.4 with sub-processor, processing region, retention period and legal basis.

---

## 4. Sub-Processors

Data processing agreements pursuant to Art. 28 GDPR are in place with all sub-processors listed below. The contractual documents are held by the Controller and can be inspected upon request.

### 4.1 Google Cloud (Vertex AI · Frankfurt)

**Provider:** Google Ireland Limited, Gordon House, Barrow Street, Dublin 4, Ireland (EU headquarters). Parent company: Google LLC, USA.

**What is processed — and what is explicitly NOT:**

*What is processed:*

- A user-captured facial image (selfie, JPEG) actively taken by the user
- Optionally, the onboarding responses for skin-type self-assessment (alternative path without a photo, if the user declines the scan)

*What the app explicitly does NOT do:*

- The app does **not** collect or store **biometric identifiers** within the meaning of Art. 4(14) GDPR
- The app does **not** create or store **facial-recognition templates / face embeddings / FaceIDs**
- The app does **not** perform **identity verification**
- The app does **not** match faces against any database
- The photo is **not** used to re-identify the user across later sessions
- The photo is **not** passed on for AI model training (Google Cloud DPA)
- The app does **not** derive emotional, medical or psychological assessments

**Purpose of processing:** AI-supported estimation of your skin type (Fitzpatrick I–VI), skin tone and eye color based on a selfie photo. The result is used exclusively to personalize your individual tanning plan (recommended sun exposure time per side, sun protection factor, optimal tanning window).

**How the data is used:**

The selfie image is used solely to:

- Analyze visible skin characteristics (such as tone, redness, tan lines, eye color)
- Generate personalized tanning and sun-protection recommendations within the app

**The image is NOT used for:**

- Facial recognition or biometric identification
- User re-identification across sessions
- Advertising, marketing, or profiling outside of tanning personalization
- Resale, rental, or commercial exploitation of the image data
- AI model training (contractually excluded under Google Cloud DPA)

**Data transmitted:** Selfie photo (JPEG, base64-encoded), a text prompt provided by the Controller, and the app language (`de` or `en`, so the AI returns its reasoning in the right language). **No** further profile data (skin type, eye color, etc.), location data or persistent device IDs are transmitted.

**Processing region:** `europe-west3` (Frankfurt am Main, Germany). The data does not leave the European Union.

**Storage and retention:**

- **At Vertex AI Frankfurt:** The photo is processed solely for the duration of the inference (typically < 5 seconds) and is **not stored**. Use for training the underlying AI models is excluded under the Google Cloud Data Processing Addendum (DPA).
- **At Sunly:** Sunly does not operate any servers on which photo or analysis data could be retained. Only the analysis result (skin type, skin tone, eye color as plain-text values) is stored locally on your device.
- **Locally on your device:** You can delete analysis results at any time via *Profile → Reset data* — all values and consent records will then be removed.

**Legal basis:** Art. 6(1)(a) GDPR (consent), supplemented by Art. 9(2)(a) GDPR (explicit consent) where applicable.

**Consent mechanism:** Before the first AI-assisted scan, the App displays a modal consent dialog that describes the data flow (Cloudflare edge → Vertex AI Frankfurt), the storage and training guarantees, and the right of withdrawal. The dialog contains:

- the title "🤖 KI-Foto-Analyse" / "🤖 AI photo analysis",
- a brief description of the data flow ("Your selfie is briefly analysed by Vertex AI in Frankfurt — not stored."),
- an explicit disclaimer with the wording: *"By tapping 'I agree' you accept Sunly's [Privacy Policy] and [Terms] (16+)."* — the bracketed links open the respective full texts directly in the App,
- a primary action button **"I agree"** / **"Einverstanden"** (yellow, prominent),
- optionally a secondary "Skip · answer questions instead" button (onboarding path) that fully bypasses the AI analysis.

Only by actively tapping the "I agree" button does the user confirm **two facts** in a single declaration: (a) the minimum age under Art. 8 GDPR in conjunction with § 8 BDSG ("16+"), and (b) explicit consent to the processing of biometric-like features under Art. 9(2)(a) GDPR. This construction (an unambiguous primary button with linked disclaimer) qualifies as a "clear affirmative action" under Recital 32 GDPR and is a valid form of consent.

The consent record is stored locally (`localStorage` key `sunny:aiConsent`) with timestamp, version (`v1.2`), locale, minimum-age flags (`ageConfirmed: true`, `minimumAge: 16`) and flow identifier (`flow: 'minimal-button'`).

**Important:** The modal is shown **before every first AI-scan attempt — regardless of the app language**. Users who choose the alternative questionnaire path during onboarding do not process any photo and therefore do not trigger Art. 9 processing — a separate minimum-age confirmation is not required in that case, since no special-category data is being processed.

**Withdrawal:** You can withdraw consent any time via *Profile → Reset data*; this also removes the local consent record. Alternatively, you can skip the scan entirely (questionnaire path with the same outcome).

**Notice on special categories (Art. 9 GDPR):** Since the selfie may contain biometric-like features, the consent mechanism described above is designed to satisfy Art. 9(2)(a) GDPR. Processing is not for the unique identification of a person, but exclusively for skin type estimation in a wellness context.

**Notice on Fitzpatrick classification:** The Fitzpatrick scale (I–VI) used in the AI response is originally a dermatological standard. Sunly uses it exclusively in a **wellness / lifestyle context** as a statistical estimate to personalize the tanning plan — it does **not** replace a medical skin-type assessment, is **not a medical diagnosis**, and Sunly is **not a medical device** within the meaning of Regulation (EU) 2017/745 (MDR). You can manually override the result at any time (see Section 11).

**Contractual documents:** Cloud Data Processing Addendum, Standard Contractual Clauses (EU C2P), Sub-Processor list — available at https://cloud.google.com/terms/data-processing-addendum and https://cloud.google.com/terms/subprocessors.

### 4.2 Cloudflare (Edge Proxy)

**Provider:** Cloudflare, Inc., 101 Townsend St, San Francisco, CA 94107, USA. EU representative: Cloudflare Germany GmbH, Rosental 7, 80331 Munich.

**Purpose of processing:** Cloudflare operates an **edge worker as a secure proxy** between the Sunly App and Google Vertex AI. This architecture allows the secret API key to be kept server-side (rather than in the distributed app bundle), significantly increasing the security of the AI interface.

**Data transmitted:**

- **From the photo scan:** The photo and prompt data described in 4.1 are routed for a few seconds via the Cloudflare edge (no caching, no logging of image content).
- **Technical connection data:** As part of request forwarding, Cloudflare processes typical HTTP metadata (IP address, timestamp, user agent, ASN) for abuse prevention and rate limiting. The IP is held only briefly and not merged with other data sets.

**Processing region:** Cloudflare operates a global edge network; routing occurs through the geographically nearest edge location, typically within the EU.

**Retention period:** Edge logs for abuse prevention are retained for a maximum of 30 days under Cloudflare's standard DPA and then deleted.

**Legal basis:** Art. 6(1)(f) GDPR (legitimate interest in the security of the API interface and protection against abuse).

**Contractual documents:** Cloudflare Customer Data Processing Addendum, Sub-Processor list — available at https://www.cloudflare.com/cloudflare-customer-dpa/ and https://www.cloudflare.com/gdpr/subprocessors/.

### 4.3 Sentry (Crash Reporting · Frankfurt)

**Provider:** Functional Software, Inc. dba Sentry, 45 Fremont Street, 8th Floor, San Francisco, CA 94105, USA. EU representation: Sentry GmbH, based in Vienna, Austria (group entity responsible for EU customers).

**Purpose of processing:** Detection and resolution of software errors that lead to crashes or unexpected app behavior. This data enables security and stability improvements.

**Data transmitted:**

- Stack trace and error message
- App version, device model, operating system version
- Browser/WebView version, configured language
- Recent user actions before the error ("breadcrumbs" — anonymized, without image content or personal profile data)

**Not transmitted:** IP addresses (deactivated in the Sentry configuration via `sendDefaultPii: false`), photo content, profile data (skin type, desired tan, etc.), location data or authentication data.

**Processing region:** `ingest.de.sentry.io` (Frankfurt am Main, Germany). The data storage region was explicitly set to "European Union (EU)" during Sentry account setup; subsequent changes are not possible.

**Retention period:** 30 days, then automatic deletion (Sentry Free plan standard).

**Legal basis:** Art. 6(1)(f) GDPR (legitimate interest in the stability and security of the App).

**Right to object (Art. 21 GDPR):** You may object to the transmission of crash reports at any time by setting the toggle to "Off" in the App under **Profile → Crash reports**. This deactivates the Sentry library and no further crash data will be transmitted from that point on.

**Contractual documents:** Sentry Data Processing Addendum (Version 5.1.0 or higher) — formally accepted by the Controller.

### 4.4 Open-Meteo (Weather, UV and Geocoding Data)

**Provider:** Open-Meteo, Bundesgasse 5, 3011 Bern, Switzerland.

**Purpose of processing:**

- Retrieval of the current UV index, weather and UV forecast for your location (`api.open-meteo.com`).
- Retrieval of air-quality data in addition to weather (`air-quality-api.open-meteo.com`).
- Resolution of city names to coordinates when you manually search for a city in the app (`geocoding-api.open-meteo.com`).

**Data transmitted:**

- On the automatic GPS path: geographic coordinates (latitude and longitude).
- On the manual city search path: the city name you entered (e.g. "Munich") plus locale.

In both cases, **no user identifier** is transmitted — requests cannot be attributed to any person.

**Processing region:** Switzerland (recognized as a safe third country under Art. 45 GDPR in conjunction with the EU Commission's adequacy decision).

**Legal basis:** Art. 6(1)(f) GDPR (legitimate interest in providing the core "UV tracking" function).

### 4.5 Web Fonts (Google Fonts and Fontshare)

**Providers:**

- **Google Fonts** — Google Ireland Limited, Gordon House, Barrow Street, Dublin 4, Ireland (for Manrope, Outfit, Roboto Mono, Inter via `fonts.googleapis.com`).
- **Fontshare** — Indian Type Foundry Pvt. Ltd., 11 Lalita Park, Laxmi Nagar, Delhi 110092, India (for Satoshi and Cabinet Grotesk via `api.fontshare.com`).

**Purpose of processing:** Delivery of the app UI fonts on first start. The `display=optional` strategy ensures that if the connection fails after ~100 ms, the system font is used (no layout shift).

**Data transmitted:** IP address, user agent, referrer (from the WebView).

**Processing region:** Global CDN networks (Google: incl. EU; Fontshare: incl. EU/USA/India). Fontshare involves India — no adequacy decision; Fontshare relies on its own Standard Contractual Clauses (see Fontshare Privacy Policy).

**Legal basis:** Art. 6(1)(f) GDPR (legitimate interest in consistent, legible typography).

**Planned mitigation:** Fonts will be bundled locally in the app in a future version, eliminating this data flow entirely.

### 4.6 OpenStreetMap Foundation (Reverse Geocoding)

**Provider:** OpenStreetMap Foundation, St John's Innovation Centre, Cowley Road, Cambridge, CB4 0WS, United Kingdom.

**Purpose of processing:** Reverse geocoding of GPS coordinates to readable city names via the `nominatim.openstreetmap.org` endpoint (e.g. "48.13, 11.58" → "Munich, DE"). Used in addition to Open-Meteo because Nominatim provides more precise city labels for UI display.

**Data transmitted:** Latitude and longitude, locale, static user agent (`Sunly/1.0`). No user identifier.

**Processing region:** United Kingdom (recognized as a safe third country under Art. 45 GDPR in conjunction with the UK adequacy decision of 28 June 2021).

**Retention:** Nominatim keeps standard webserver logs per OSMF Privacy Policy (max. 14 days). Requests are deleted thereafter.

**Legal basis:** Art. 6(1)(f) GDPR (legitimate interest in precise city-name display in the UI).

---

## 5. Local Data Processing in the App

The following data is stored **exclusively on your device** (Android `localStorage` and app-internal filesystem) and is never transmitted to external parties unless explicitly stated in this Policy:

| Category | Content | Storage |
|---|---|---|
| Profile | Skin type, eye color, gender, desired tan, sun protection preferences | localStorage |
| Sessions | Date, duration, streak, completed tanning sessions | localStorage |
| Photos | Selfie history for tanning progress (max. 50 photos) | App filesystem (Capacitor `Directory.DATA`) |
| Settings | Language, notification toggles, vibration toggle, crash report opt-out | localStorage |
| App cache | UV data cache (15-min TTL), geocoding cache | localStorage |

This local data is only visible to you and persons with access to your device. When you uninstall the App, it is completely removed.

---

## 6. Location Data

If you grant the App location access, your GPS coordinates are

- held only briefly in device memory,
- sent only to Open-Meteo (anonymously, with no personal reference) (see Section 4.4),
- not stored in Sunly-internal logs or external analytics services.

You can revoke location access at any time in the Android system settings. Without location, the App continues to work, but without location-specific UV data.

---

## 7. Push Notifications and Step Vibrations

Sunly uses **Android LocalNotifications** and the system `AlarmManager.setAlarmClock()` API for UV warnings, daily push updates, routine notifications and tanning step vibrations. These are scheduled and triggered **entirely on your device** — there is **no push server** at Sunly or any third party (no Firebase Cloud Messaging, no OneSignal, no APNS routing through external servers).

You can disable notifications at any time via the Profile menu ("Notifications") or the Android system settings.

**Legal basis:** Art. 6(1)(a) GDPR (consent through actively granting the notification permission on first launch).

### 7.1 Punctual step vibrations (`SCHEDULE_EXACT_ALARM`, special app access)

Tanning step timers must fire on time to the second, because excessive UV exposure can lead to skin redness or sunburn. To make sure Android serves the system alarm-clock API used by Sunly with guaranteed precise timing — even in standby mode — the app declares the `SCHEDULE_EXACT_ALARM` permission.

**Properties of this permission:**

- **Purpose:** Allows the app exclusively to use `AlarmManager.setAlarmClock()` and `setExactAndAllowWhileIdle()` to schedule precisely timed local alarm-clock alarms for the next step end of an active tanning session. Without this permission, Android (from version 12 / API 31) groups alarms with up to 15 minutes of delay — unusable for a tanning timer.
- **No background data processing:** This permission allows **no** background data processing, **no** tracking, **no** extension of the app's runtime. It applies only to the timing precision of local alarms you started yourself.
- **When the permission is active:** On Android 12 and 13 (API 31–33), `SCHEDULE_EXACT_ALARM` is automatically granted by the system on first app launch for apps that declare it in the manifest. On Android 14+ (API 34+) it is disabled by default for newly installed apps; you can enable or revoke it at any time under *Settings → Apps → Sunly → Special app access → Alarms & reminders*.
- **Works without it too:** If the permission is denied, the app uses the system alarm-clock API (`AlarmManager.setAlarmClock()`) as its preferred path — this API is doze-bypass-capable even without a special permission, because it is treated like a classic alarm clock. Foreground vibrations (app open) are punctual either way, since the timing is then driven by JavaScript.

**Note on the discontinued battery exemption:** Earlier versions of the app (≤ 1.1.31) used the `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` permission to avoid vibration alarm delays on restrictive OEM modes (Samsung, Xiaomi). This permission was removed in version 1.1.32 and replaced with the combination of `SCHEDULE_EXACT_ALARM` and a 5-second WakeLock in the alarm receiver — functionally equivalent, but more privacy-friendly and without interfering with the system battery strategy.

**Legal basis:** Art. 6(1)(a) GDPR (consent) and Art. 6(1)(b) GDPR (contractual necessity — punctual step vibrations are a core function of the app). On Android 13+ no separate user action is required; on Android 12 the special app access is automatically granted by the system at install time and can be revoked at any time.

---

## 8. Third-Country Transfers

As described in Section 4, processing operations are configured so that inference and storage occur **within the European Union** (Google Vertex AI in Frankfurt, Sentry in Frankfurt). However, the EU parent companies (Google LLC, Functional Software/Sentry, Cloudflare Inc. — all USA) may potentially have access to processing in the context of maintenance and support.

For such constellations, the following safeguards are in place:

- **EU Standard Contractual Clauses (SCCs)** pursuant to Implementing Decision (EU) 2021/914 — Module 2 (Controller-to-Processor)
- For Sentry additionally: **EU-US Data Privacy Framework** certification
- Cloud provider DPAs explicitly prohibiting the use of customer data for AI model training or other secondary purposes

---

## 9. Retention Period

| Data category | Retention period |
|---|---|
| Local profile / session / photo data | Until you uninstall the App |
| Photo at Vertex AI Frankfurt | Not stored (only transient inference, < 5 seconds) |
| Cloudflare edge logs | Max. 30 days |
| Sentry crash reports | Max. 30 days |
| Open-Meteo requests | Anonymous, not attributable to any person |

No retention beyond these periods takes place.

---

## 10. Your Rights as a Data Subject

Under the GDPR, you have the following rights:

- **Right of access (Art. 15)** — information about which data we process about you.
- **Right to rectification (Art. 16)** — correction of inaccurate data.
- **Right to erasure (Art. 17, "right to be forgotten")** — deletion of your data.
- **Right to restriction of processing (Art. 18)**.
- **Right to data portability (Art. 20)** — provision of your data in a machine-readable format.
- **Right to object (Art. 21)** — particularly against processing based on legitimate interests (e.g., crash reporting via Sentry).
- **Right to withdraw consent (Art. 7(3))** — e.g., for the photo analysis or push notifications.
- **Right to lodge a complaint with a supervisory authority (Art. 77)** — particularly with the competent State Data Protection Authority of North Rhine-Westphalia:

> Die Landesbeauftragte für Datenschutz und Informationsfreiheit Nordrhein-Westfalen
> Postfach 20 04 44, 40102 Düsseldorf, Germany
> Phone: +49 211 38424-0
> Email: poststelle@ldi.nrw.de
> Website: https://www.ldi.nrw.de

**Practical implementation:** Since Sunly does not operate a server-side user database, requests for access and deletion can be fulfilled in most cases by uninstalling the App. For data held by sub-processors (Google, Cloudflare, Sentry), please contact us using the details in Section 1 — we will forward your request to the respective processor without undue delay.

---

## 11. Automated Decision-Making (Art. 22 GDPR)

The AI-based skin type estimation in Section 4.1 does **not** constitute automated decision-making with legal effect within the meaning of Art. 22 GDPR:

- The result is shown to you only as a recommendation
- You can discard the result at any time or manually adjust your skin type (Profile → Skin type)
- No legal consequences or significant adverse effects arise

The processing serves exclusively to personalize wellness recommendations.

---

## 12. Cookies

The Sunly App is a native Android application and uses **no cookies**. The storage technology underlying the WebView (`localStorage`) is used exclusively for local app state management and is not transmitted to external parties.

---

## 13. Data Security

We implement the following technical and organizational measures:

- **Transport encryption (TLS 1.2+)** for all external API connections
- **OAuth 2.0 / Service Account authentication** for the Vertex AI interface: the Google service-account key resides exclusively on the Cloudflare worker (as a worker secret), **not** in the distributed app bundle. The app bundle only contains a simple worker-shared key that does NOT enable Google Cloud authentication — it merely makes external direct calls to the worker endpoint harder (soft protection, not an auth mechanism).
- **Cloudflare edge protection** with IP-based rate limiting (30 requests per hour) and Web Application Firewall
- **Local photo storage** in the sandboxed Capacitor filesystem (no access by other apps)
- **Crash report filter** (`beforeSend` hook) automatically removes potential image data from stack traces before transmission to Sentry
- **Production log gate** suppresses all non-essential console output in release builds

---

## 14. Currency and Modification of this Privacy Policy

This Privacy Policy is currently effective in the version stated above (last updated: May 9, 2026, version 1.8). Further development of the App or legal changes may require modification. The current Privacy Policy can be viewed at any time in the Profile menu under "Privacy".

**Changes in v1.8 vs. v1.7 (May 9, 2026, app version 1.1.32):**

- Section 7.1 substantially rewritten: the opt-in `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` permission was **fully removed** and replaced with the `SCHEDULE_EXACT_ALARM` permission. The latter is classically a "special app access" and the path explicitly endorsed by the Google Play Store for timer/alarm apps.
- Additionally, the WakeLock in the alarm receiver was extended from 3 to 5 seconds, so that on aggressively optimized OEMs (Samsung One UI, Xiaomi MIUI), the vibration motor and the step-end notification are reliably processed completely before the system falls back into deep sleep.
- Architectural rationale: the previous battery exemption was considered a HIGH-risk permission in the Play Console and could have triggered longer review cycles. The new combination of `SCHEDULE_EXACT_ALARM` + extended WakeLock achieves the same outcome — punctual step vibrations even in standby — without interfering with the system battery strategy.

**Changes in v1.7 vs. v1.6 (May 9, 2026):**

- New Section 7.1 "Battery exemption for punctual step vibrations" — describes the opt-in `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` permission, requested exclusively when the user actively enables Routine Vibration (never automatically). *(Fully replaced by `SCHEDULE_EXACT_ALARM` in v1.8.)*
- Architectural background: previously the app implemented the step timer via a Foreground Service with `FOREGROUND_SERVICE_SPECIAL_USE` permission. This was replaced with the Play-Store-compliant `AlarmManager.setAlarmClock()` mechanism — which makes the opt-in battery exemption necessary for punctual background triggers on restrictive OEMs (Samsung etc.).
- Section 7 title expanded from "Push Notifications" to "Push Notifications and Step Vibrations" because the mechanism now also covers local step-end alerts via `AlarmManager`.

**Changes in v1.6 vs. v1.5 (May 8, 2026 — final pre-submission audit):**

- Section 4.1 expanded with "Notice on Fitzpatrick classification" — explicit wellness/lifestyle disambiguation; clarifies that Fitzpatrick I–VI is used only as a statistical estimate in a wellness context, not as a medical diagnosis, not as a medical device under MDR.
- Section 4.4 expanded: subdomain `air-quality-api.open-meteo.com` for air-quality data — previously implicitly subsumed under "api.open-meteo.com", now explicitly listed.

**Changes in v1.5 vs. v1.4 (May 8, 2026):**

- New Section 15 "Links to Third-Party Sites" with a clear liability disclaimer for external links.
- New Section 16 "Children's Privacy" with explicit 16+ confirmation, explicit no-collection-of-children's-data commitment, and a parental contact path. Format aligned with Apple / Google Play expectations for child-protection disclaimers.

**Changes in v1.4 vs. v1.3 (May 8, 2026):**

- Section 4.1 expanded with two additional sub-blocks following an approved-template format (Apple / Play Store): "How the data is used" (positive list: skin tone, redness, tan lines, eye color → personalized plan) and "The image is NOT used for" (negative list: facial recognition, re-identification, advertising, resale, model training).
- Section 4.1 restructured "Storage and retention" as its own consolidated block covering three storage layers (Vertex AI / Sunly servers / locally on device) including explicit deletion instructions.

**Changes in v1.3 vs. v1.2 (May 8, 2026):**

- Section 4.1 expanded with an explicit block "What is processed — and what is explicitly NOT": scope limitation of the photo analysis (no biometric identifier, no face embedding, no identity verification, no database matching, no re-identification, no emotional/medical assessment). Format aligned with Play Store Data Safety and Apple App Privacy requirements for transparent scope limitation of photo/AI features.

**Changes in v1.2 vs. v1.1 (May 8, 2026):**

- Section 3 restructured into "What Sunly does NOT have" / "What stays local" / "What does leave your device" — photo data flow clearly separated into progress photos vs. AI scan photo.
- Section 4.1 expanded: locale is now sent along with the Vertex AI inference; consent mechanism precisely described as "unambiguous primary button with linked disclaimer" (instead of "mandatory confirmation checkbox"); modal is shown regardless of app language.
- Section 4.4 expanded: city name as an alternative search parameter alongside coordinates.
- New Section 4.5 (web fonts: Google Fonts + Fontshare).
- New Section 4.6 (OpenStreetMap reverse geocoding).
- Section 13 clarified: distinction between service-account key (worker secret) and worker-shared key (soft protection in bundle).

---

## 15. Links to Third-Party Sites

This Privacy Policy and certain in-app areas (e.g. the App-Information screen, contract-document links) may contain references to external websites — including the privacy policies of Google Cloud, Cloudflare, Sentry, Open-Meteo, Fontshare and the OpenStreetMap Foundation.

These external sites are **not operated by the provider**. The provider has no control over their content, availability or privacy practices. We strongly recommend reading the privacy policies of the linked third-party sites before using them.

Liability for the content of linked third-party sites is excluded to the extent permitted by law.

---

## 16. Children's Privacy

Sunly is intended exclusively for users aged **16 and over**. The App is not designed for use by children under 16:

- On the AI skin-type scan path, the user actively confirms the minimum age via the consent modal (see Section 4.1).
- On the questionnaire path, age of majority is part of the accepted Terms of Service (Section 7 of the Terms).
- There are no age-appropriate contents or features specifically targeting children.

**We do not knowingly collect personal information from children under the age of 16.** Should we become aware that such data has been transmitted to one of our sub-processors (e.g. via the AI-scan photo), we will promptly initiate deletion of all such data at the relevant sub-processor.

**To parents or legal guardians:** If you have reasonable grounds to believe that your child under 16 has used the App and submitted personal information, please contact mail@mariusbecker.me without delay. We will review the matter immediately and arrange deletion of all relevant data at the sub-processors.

---

**End of Privacy Policy**
