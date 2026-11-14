# Security policy

Dalbrot stores health-related data (food log, weight, body details), so security reports are taken seriously.

## Reporting a vulnerability

Please do **not** open a public issue. Report privately through GitHub's
"Report a vulnerability" button on the repository's Security tab, or by email to `[contact email]`.

Include what you found, the steps to reproduce it, and the app version (shown at the bottom of the Me page).

- You get an acknowledgement within 7 days.
- Confirmed problems are fixed as fast as one maintainer can manage, normally within 30 days.
- Please give that time before publishing details.

Good-faith research is welcome: only test with your own data, and do not access, change or delete anyone else's.

## Supported versions

Only the latest released version is supported.

## How Dalbrot is built

- No Dalbrot server and no account. Data lives on the device, or in the user's private claude.ai storage in the web preview.
- No third-party scripts, fonts, analytics or ads. The app makes no network requests of its own.
- Everything read back from storage or from a backup file is validated before use, and all text is escaped before it is shown.
- AI features are off by default and run on the user's own Claude account.
