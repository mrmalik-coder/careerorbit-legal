# CareerOrbit Legal Website

Standalone, static legal pages prepared for the separate
`mrmalik-coder/careerorbit-legal` repository. These files are **not approved,
published, or legal advice**. Owner and qualified legal review are required
before publication.

## Files

- `index.html` — homepage linking to both documents
- `privacy.html` — implementation-informed Privacy Policy draft
- `terms.html` — Terms & Conditions draft
- `styles.css` — shared responsive styles

The site has no JavaScript, analytics, external font, or paid dependency.
Relative links are suitable for a project GitHub Pages site.

## Owner review checklist

Resolve remaining owner and counsel decisions before publication:

- Legal review of the public operator disclosure for Sajid Manzoor as an
  individual, not a company or registered legal entity. Do not imply or invent
  a registered business address, company registration, NTN, or other credentials.
- Publication date: replace `[TO BE SET BEFORE PUBLICATION]` with an owner-approved
  date when publication is scheduled.
- Privacy contact is
  `sajidmanzoor347@gmail.com`, but confirm that it is monitored.
- Minimum account age is 16, subject to counsel's review of children's privacy
  and eligibility obligations.
- Pakistan is the intended jurisdiction, subject to legal review of governing
  law, applicable privacy rights, liability, and dispute terms.
- The deployed release's data regions, providers, and processor/subprocessor
  disclosures.
- Retention and deletion across live systems and backups. The server-side
  account-deletion workflow is not deployed; do not promise self-service
  deletion or fixed 30/90-day cleanup.
- Wallet, transaction, audit, application, support, and company-record
  retention/anonymization decisions.
- Referral rewards are not active and must not be presented as benefits.

Confirmed details: CareerOrbit; Sajid Manzoor as an individual operator (not a
company or registered legal entity); privacy/legal contact
`sajidmanzoor347@gmail.com`; minimum age 16; intended jurisdiction Pakistan,
subject to qualified Pakistani legal counsel review. No registered address,
company registration, NTN, or other legal credential was supplied.

The Privacy Policy describes the current implementation as verified in the
mobile source, not a guarantee of how future builds or services will operate.
Re-check it against the release build and backend before approval.

## Firebase Staging verification (read-only)

Checks used existing local Firebase CLI authentication and explicitly targeted
`careerorbit-staging`. Production was not queried.

| Service | Finding | Location / limitation |
|---|---|---|
| Cloud Firestore | Default `(default)` database exists; `FIRESTORE_NATIVE`, `STANDARD` edition. | Verified location: `asia-south1` (Mumbai, India). |
| Firebase Hosting | Site `careerorbit-staging`; default URL `https://careerorbit-staging.web.app`. | A Pakistan-only data location is not verified or claimed. |
| Realtime Database | No instances found. | Not configured in this Staging project based on the CLI listing. |
| Cloud Storage for Firebase | The installed Firebase CLI had no bucket-list command; `gcloud` was not installed/on PATH. | Bucket existence and location are **not verified**. Reviewed mobile import code does not upload source images/PDFs to Firebase Storage. |
| Cloud Functions | `functions:list --project=careerorbit-staging` returned `Failed to list functions for careerorbit-staging`; no specific missing permission was provided. | Deployment and function regions are **not verified**. Local `firebase.json` source configuration does not prove deployment. |
| Firebase Authentication | Mobile source includes email/password and Google sign-in flows. | Enabled Firebase providers were not verified. Firebase's privacy documentation states Authentication processes end-user information in US data centers; Google sign-in also involves Google. |
| Firebase Cloud Messaging | Android push-token registration and notification handling exist in source. | FCM delivery configuration/status was not independently verified. No Pakistan-only location is claimed. |

The Firestore location is a Staging fact only; no Production resource was
inspected, and release configuration must be checked separately. Project IDs
and SDK initialization do not establish physical resource locations. Firebase
Hosting/FCM are not described as having Pakistan-only storage. Analytics,
advertising, and crash-reporting SDKs were not found in the reviewed mobile
dependency manifest.

## Pakistani legal review and authoritative references

The Ministry of IT and Telecommunication legislation page lists Personal Data
Protection Bills, including the May 2023 Bill, as **Draft**. Do not describe a
draft bill as enacted law; counsel should confirm applicable enacted law and its
interpretation. The legal drafts are not a claim of legal compliance.

- [Firebase privacy and data processing](https://firebase.google.com/support/privacy)
- [Firebase project and product locations](https://firebase.google.com/docs/projects/locations)
- [Cloud Firestore locations](https://firebase.google.com/docs/firestore/locations)
- [Pakistan Ministry of IT and Telecommunication — Legislations](https://www.moitt.gov.pk/Legislations)
- [GitHub Pages overview](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages)
- [GitHub Pages publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [Securing GitHub Pages with HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)

## Future GitHub Pages setup (not performed)

No repository was created, no Pages setting was changed, and nothing was
published. After owner/counsel approval, the owner may create a **public**
repository named `careerorbit-legal` under `mrmalik-coder`, then:

1. Do not initialize it with another README or license if uploading this
   prepared folder directly.
2. Copy the contents of this folder into the repository root. Do not copy
   application `.env` files, Firebase configuration, credentials, or signing
   material.
3. In repository **Settings → Pages**, choose **Deploy from a branch**, select
   `main` and the `/ (root)` folder, then save.
4. Wait for the Pages deployment to complete. Confirm HTTPS is enabled and
   both pages load publicly with correct relative navigation.
5. Verify these expected project-site URLs before using them:
   - `https://mrmalik-coder.github.io/careerorbit-legal/`
   - `https://mrmalik-coder.github.io/careerorbit-legal/privacy.html`
   - `https://mrmalik-coder.github.io/careerorbit-legal/terms.html`

These are proposed addresses only and are not live/verified at the time this
README was prepared. Do not enter the Privacy Policy URL in LinkedIn until the
page is publicly reachable over HTTPS and owner-approved.

## LinkedIn Developer App checklist

Known state supplied by the owner: the LinkedIn Developer App exists and the
CareerOrbit Company Page association/verification is approved; the Privacy
Policy URL is not yet published, and OpenID Connect product access has not been
requested.

After review and publication:

1. In [LinkedIn Developer Portal](https://www.linkedin.com/developers/), select
   the CareerOrbit app and confirm its Company Page association.
2. Add the verified HTTPS Privacy Policy URL in app settings.
3. Open **Products** and request **Sign In with LinkedIn using OpenID Connect**.
4. Review LinkedIn's current product terms, consent requirements, redirect URI
   settings, and approved scopes. Expected OIDC scopes are `openid`, `profile`,
   and `email`; these provide identity/lite-profile claims, not CV work history
   or education import.
5. Do not add a client secret to this mobile app or a public repository. Keep
   confidential OAuth configuration on an approved server-side secret store.

Official reference:
[Sign In with LinkedIn using OpenID Connect](https://learn.microsoft.com/en-us/linkedin/consumer/integrations/self-serve/sign-in-with-linkedin-v2).

## App-side LinkedIn readiness

The current app has Google sign-in through Expo Auth Session and Firebase
`signInWithCredential`, plus email-verification deep-link handling. No LinkedIn
OIDC provider flow, OAuth callback route, redirect URI, token validation
endpoint, or LinkedIn-to-Firebase identity-linking flow was found in the
reviewed mobile auth surfaces. The existing email action route is not a LinkedIn
callback. LinkedIn URL scraping is not implemented or permitted by this plan.

Before implementation, obtain product approval and confirmed LinkedIn app
settings, then design an authorization-code flow with state/PKCE, an explicitly
registered redirect URI, server-side code exchange and ID-token validation
against LinkedIn discovery/JWKS, and a Firebase account-linking strategy that
preserves the existing UID and handles same-email conflicts without silent
linking. Do not implement from assumed callback values or place secrets in the
mobile bundle.

## Publication verification

- [ ] Legal placeholders resolved and text approved by owner/counsel.
- [ ] Public operator identity disclosure and effective dates approved.
- [ ] Publication date placeholder replaced when publication is scheduled.
- [ ] Contact mailbox monitoring confirmed.
- [ ] Release Firebase configuration, providers, locations, retention, and
      deletion claims verified.
- [ ] Only these static files are in the separate repository.
- [ ] Repository is public and Pages is enabled on `main` / root.
- [ ] HTTPS works and all three URLs above resolve.
- [ ] Privacy and Terms links work on desktop and mobile.
- [ ] Contact address is monitored.
- [ ] Published policy URLs are entered in LinkedIn only after public verification.
