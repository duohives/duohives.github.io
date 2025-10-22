# DuoHives – Privacy Policy

Last updated: 2025-10-22

This Privacy Policy explains what data the DuoHives Chrome extension and its backend services collect, how we use it, and the choices you have. By using the extension, you agree to this policy.

## Summary
- Single purpose: Provide a Gmail‑integrated CRM sidebar that classifies emails, extracts contacts/companies, and manages deals with the user’s consent.
- We collect only what is necessary to deliver this functionality.
- We do not sell or transfer user data to third parties, except to service providers that power core functionality (Google APIs/Cloud).
- You can request deletion of your data at any time.

## What We Collect
Depending on how you use the extension, we may collect:

1) Authentication information
- Google account ID, email, name, and profile image via Google OAuth (userinfo.email/userinfo.profile).
- OAuth tokens: The backend exchanges the authorization code for access/refresh tokens. The refresh token is stored server‑side (Firestore) for the signed‑in user to access Gmail on their behalf.

2) Personal communications (Gmail)
- With your consent, the backend reads Gmail threads and messages for your mailbox to:
  - Classify whether emails are CRM‑related.
  - Extract company/contact information.
  - Create/update deals and related activity.
- The content/metadata needed for CRM features is stored in Firestore under your user account collections (users/{userId}/…).

3) Personally identifiable information (PII)
- Contact details (e.g., names, email addresses) extracted from your emails.
- Company details derived from email signatures or referenced websites.

4) Product telemetry (minimal)
- Basic service logs (e.g., timestamp, error messages). We do not log browsing history.
- LLM calls: When enabled, we log the prompt input and model output for each model call under `llm_calls/{userId}/{promptName}/{callId}` to help inspect/trace AI behavior. These logs are stored in your Firestore namespace.

We do not intentionally collect: precise location, financial data, health data, or unrelated web activity.

## How We Use Data
- Provide the Gmail‑integrated CRM experience: sidebar UI, email classification, entity extraction, deal management and summaries.
- Maintain and improve the service: debugging, reliability, abuse prevention, and support.
- With your consent, run background processing via Google Cloud Workflows and Cloud Functions to process batches of emails/threads.

## Data Sharing
We do not sell or transfer user data to third parties. We rely on service providers strictly to deliver core functionality:
- Google APIs: Gmail API and OAuth (userinfo endpoints), as authorized by you.
- Google Cloud: Cloud Run (API), Cloud Functions Gen2, Cloud Workflows, Firestore (data storage), Pub/Sub (Gmail watch), and associated IAM services.
- Google GenAI: We send relevant text to the selected model for classification/extraction and store responses in your Firestore. Model inputs/outputs are used only to provide the requested CRM features.

These processors are bound by their terms and operate under your project’s configuration as deployed by our infrastructure.

## Data Retention & Deletion
- Data is retained for as long as you use the service or until you delete it.
- You can request deletion of your data (emails, extracted entities, deals, notes, and LLM logs) by contacting support or by using in‑product delete functions where available.
- On logout, client‑side tokens are cleared. Server‑side refresh tokens are revoked and removed on explicit logout.

## Security
- All communication uses HTTPS/TLS.
- OAuth tokens are stored server‑side; access tokens are short‑lived and cached with expiry.
- Firestore security rules and IAM roles restrict access to your data.
- Pub/Sub push endpoints are protected with OIDC tokens and verified audience/issuer.

## Permissions Rationale
- Host permissions: `https://mail.google.com/*` to render the sidebar and read Gmail labels within Gmail; `https://www.googleapis.com/*` to call Google APIs (e.g., userinfo, Gmail endpoints) with your consent.
- `identity`: Launches Google OAuth (PKCE) for sign‑in; the backend exchanges the code for tokens.
- `storage`: Stores minimal settings (backend URL, preferences) and your session JWT in Chrome local storage.
- `tabs`: Opens Gmail or extension pages in new tabs. We do not read browsing history or pages outside Gmail.
- We do not execute remote code or use `eval`.

## Children’s Privacy
The service is not directed to children. Do not use the extension if you are under the age where consent is required in your jurisdiction.

## Changes to This Policy
We may update this policy from time to time. We will post any changes here with an updated “Last updated” date.

## Contact
If you have questions or requests (including data deletion), contact: support@duohives.com

---

This policy covers both the Chrome extension and the backend services that power it.
