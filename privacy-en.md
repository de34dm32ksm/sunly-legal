---
title: Privacy Policy
layout: page
---

# Privacy Policy — Sunly

**Last updated:** May 2, 2026 · **Version:** 1.0

> **Note:** This is the English translation of the German privacy policy. In the event of any conflict or inconsistency, the German version (`Sunly_Datenschutzerklaerung_DE.md`) prevails.

---

## 1. Controller

The controller within the meaning of the General Data Protection Regulation (GDPR) and other national data protection laws of the Member States, as well as other data protection regulations, is:

**Marius Alexander Becker**
Schleusingerstraße 41
58840 Plettenberg
Germany

Email: mail@mariusbecker.me

Sunly is a **private, non-commercial hobby project**. There is no statutory obligation to appoint a Data Protection Officer (Art. 37 GDPR) as the relevant thresholds are not exceeded.

---

## 2. Scope

This Privacy Policy applies to the **Sunly** mobile application (hereinafter "the App") for Android, published under the bundle identifier `com.mariusbecker.sunnysafe`. It informs users (hereinafter "you") about the nature, scope and purpose of the processing of personal data.

The App is exclusively for wellness and lifestyle purposes (UV index tracking, tanning planning, vitamin D estimation). It is **not a medical device** within the meaning of Regulation (EU) 2017/745 (MDR) and does not replace any medical advice, diagnosis or treatment.

---

## 3. Principle: Local Data Storage

Sunly is designed as a **data-minimal, locally operating app**. There is:

- ❌ **No cloud account and no server-side user database** at Sunly
- ❌ **No login, no registration, no email collection** on our side
- ❌ **No tracking**, no advertising IDs, no analytics (Google Analytics, Firebase Analytics, AppsFlyer, etc.)
- ✅ Profile, sessions, photos and settings are stored **exclusively locally** on your device (Android `localStorage` + filesystem)

When you uninstall the App, all locally stored data is completely removed.

Despite this architecture, three specific functions involve data flows to external processors. These are transparently described in the following sections.

---

## 4. Sub-Processors

Data processing agreements pursuant to Art. 28 GDPR are in place with all sub-processors listed below. The contractual documents are held by the Controller and can be inspected upon request.

### 4.1 Google Cloud (Vertex AI · Frankfurt)

**Provider:** Google Ireland Limited, Gordon House, Barrow Street, Dublin 4, Ireland (EU headquarters). Parent company: Google LLC, USA.

**Purpose of processing:** AI-supported estimation of your skin type, skin tone and eye color based on a selfie photo. The result is used exclusively to personalize your individual tanning plan (recommended sun exposure time per side, sun protection factor, optimal tanning window).

**Data transmitted:** Selfie photo (JPEG, base64-encoded) + a text prompt provided by the Controller. **No** further profile data, location data or device IDs are transmitted.

**Processing region:** `europe-west3` (Frankfurt am Main, Germany). The data does not leave the European Union.

**Retention period at the processor:** The photo is processed solely for the duration of the inference and is **not stored**. Use for training the underlying AI models is excluded under the Google Cloud Data Processing Addendum (DPA).

**Legal basis:** Art. 6(1)(a) GDPR (consent), supplemented by Art. 9(2)(a) GDPR (explicit consent) where applicable.

**Consent mechanism:** Detailed disclosures about the data flow (Cloudflare edge → Vertex AI Frankfurt), storage guarantees and training opt-out are available on the in-app Privacy screen, the Wellness notice and the Onboarding info overlay before any photo is taken. Consent is granted by actively triggering the photo capture and can be withdrawn at any time.

**Locale-specific consent dialog (DE interface):** Users running the German interface (`de` locale) additionally see a dedicated modal consent dialog before the first AI-assisted scan. The dialog contains a **mandatory confirmation checkbox** worded as:

> *"Ich bin mindestens 16 Jahre alt und willige in die Verarbeitung meines Fotos durch Vertex AI Frankfurt gemäß Art. 9 DSGVO ein."*
> (English: *"I am at least 16 years old and consent to the processing of my photo by Vertex AI Frankfurt pursuant to Art. 9 GDPR."*)

This single declaration covers **two facts**: (a) the minimum age under Art. 8 GDPR in conjunction with § 8 BDSG, and (b) explicit consent to processing of biometric-like features under Art. 9(2)(a) GDPR. Processing only begins after the user actively checks the box and taps the primary button. The consent record is stored locally (`localStorage` key `sunny:aiConsent`) with timestamp, version (`v1.1`), locale, minimum age and confirmation flag.

**Important:** The modal is shown **only** when the user actively chooses the AI-scan path. Users who choose the alternative questionnaire path during onboarding do not process any photo and therefore do not trigger Art. 9 processing — a separate minimum-age confirmation is not required in that case, since no special-category data is being processed.

Users on the English interface receive the same disclosures through the in-app Privacy screen, the Wellness notice and the Onboarding info overlay; given that the App is primarily targeted at non-EU markets in English, no separate explicit-consent modal is shown.

**Withdrawal:** You can withdraw consent any time via *Profile → Reset data*; this also removes the local consent record. Alternatively, you can skip the scan entirely (questionnaire path with the same outcome).

**Notice on special categories (Art. 9 GDPR):** Since the selfie may contain biometric-like features, the consent mechanism described above is designed to satisfy Art. 9(2)(a) GDPR. Processing is not for the unique identification of a person, but exclusively for skin type estimation in a wellness context.

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

### 4.4 Open-Meteo (Weather and UV Data)

**Provider:** Open-Meteo, Bundesgasse 5, 3011 Bern, Switzerland.

**Purpose of processing:** Retrieval of the current UV index, weather and UV forecast for your location to personalize tanning and sun protection recommendations.

**Data transmitted:** Geographic coordinates (latitude and longitude). **No user identifier** is transmitted — requests cannot be attributed to a person.

**Processing region:** Switzerland (recognized as a safe third country under Art. 45 GDPR in conjunction with the EU Commission's adequacy decision).

**Legal basis:** Art. 6(1)(f) GDPR (legitimate interest in providing the core "UV tracking" function).

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

## 7. Push Notifications

Sunly uses **Android LocalNotifications** for UV warnings, daily push updates and routine notifications. These are scheduled and triggered **entirely on your device** — there is **no push server** at Sunly or any third party (no Firebase Cloud Messaging, no OneSignal, no APNS routing through external servers).

You can disable notifications at any time via the Profile menu ("Notifications") or the Android system settings.

**Legal basis:** Art. 6(1)(a) GDPR (consent through actively granting the notification permission on first launch).

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
- **OAuth 2.0 / Service Account authentication** for the Vertex AI interface (no API key in the distributed app bundle)
- **Cloudflare edge protection** with IP-based rate limiting (30 requests per hour) and Web Application Firewall
- **Local photo storage** in the sandboxed Capacitor filesystem (no access by other apps)
- **Crash report filter** (`beforeSend` hook) automatically removes potential image data from stack traces before transmission to Sentry
- **Production log gate** suppresses all non-essential console output in release builds

---

## 14. Currency and Modification of this Privacy Policy

This Privacy Policy is currently effective in the version stated above (last updated: May 2, 2026). Further development of the App or legal changes may require modification. The current Privacy Policy can be viewed at any time in the Profile menu under "Privacy".

---

**End of Privacy Policy**

---

## Appendix: Notes for Legal Review (remove before publication)

Before public launch, an attorney specializing in IT/data protection law should review the following points in particular:

1. **Art. 9 GDPR**: Classification of photo processing (biometric?) — currently classified as "not for identification". Second opinion recommended.
2. **Consent mechanism** for photo scan: Implementation as a tap action is customary, but an additional modal consent prompt may be required.
3. **Wellness vs. medical device**: Current architecture (no `sunDamage`/`recoveryNeed` score, clear disclaimers) should reliably avoid MDR classification — confirmation advisable.
4. **Standard Contractual Clauses** for Cloudflare and Google: Contractual documents are in place, verify formal coverage.
5. **Supervisory authority**: LfDI NRW identified as competent (main establishment Plettenberg). Lead authority to be clarified for multiple establishments.
