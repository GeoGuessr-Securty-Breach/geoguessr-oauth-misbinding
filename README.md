# OAuth Misbinding Vulnerability in GeoGuessr

**Discovered:** June 2025  
**Disclosure status:** Unacknowledged as of July 3, 2025  

This repo documents an OAuth account misbinding flaw in GeoGuessr's Google login flow that allows authenticated users to be routed into another user's account.

## 🧩 TL;DR

- A user who signed up with Google OAuth was repeatedly routed into an account that was not theirs.
- This persisted across multiple sessions, browsers, devices, and full cache clears — even after reauthenticating with Google.
- Attempts to report this through support and executive escalation were ignored over a multi-day period.
- This behavior poses security, privacy, and regulatory concerns.

## 🕒 Timeline

- **April 28, 2025** – Target account (the incorrect one) was created.
- **Early June 2025** – Reporter signs up for GeoGuessr using Google OAuth.
- **June 28, 2025** – Reporter receives a “come back and play” email from GeoGuessr. The login link routes them into someone else’s account.
- 					– Attempts to reset session, clear cache, and reauth fail. The misbinding persists.
- 					– Reporter contacts GeoGuessr support. Receives only a vacation auto-response.
- **July 2, 2025** – Reporter escalates to GeoGuessr CEO and CTO via verified email addresses.
- **July 3, 2025** – No response after full business day in their time zone.

## 🔁 Reproduction Summary

1. Click login button from official email
2. Log in via Google OAuth
3. User is routed into a different, pre-existing account

## 🚨 Security Concerns

- Unauthorized access to another user's account
- Potential exposure of paid subscription or payment details
- Possibility of unintended access to minors’ profiles
- Violation of GDPR, CCPA, COPPA, and PCI-DSS (in theory or practice)

## 📜 Regulatory and Compliance Implications

The misbinding flaw, even in a game platform, raises red flags under:
- **GDPR** (EU): Unauthorized data access and processing
- **CCPA** (California): Privacy and behavioral data handling
- **COPPA** (US): If child accounts are involved
- **PCI DSS 4.0**: Payment access tied to authenticated user ID

## 🛡️ Reporter Background

The reporter has worked with:
- PCI-regulated e-commerce data
- DoD and municipal infrastructure systems
- User credential encryption and secure session handling

This disclosure is made with the same urgency and care expected in high-sensitivity environments.

## 📣 Requested Actions

1. **Temporarily disable OAuth login**
2. **Fix session/account binding logic**
3. **Audit for misbound accounts**
4. **Post a public security notice or postmortem**

## 📫 Responsible Disclosure Path

| Date       | Action                                     | Response |
|------------|--------------------------------------------|----------|
| June 28    | Reported to support                        | None (auto-reply only) |
| July 2     | Escalated to CEO and CTO via direct email  | None |
| July 3     | Full business day later — still no reply   | ❌ |

---

This repo exists because multiple responsible disclosure attempts were ignored.

The flaw is real. The risk is real. Hopefully, this documentation encourages remediation and responsible practices.
