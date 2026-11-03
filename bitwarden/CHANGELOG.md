## What’s new in 1.37.5

## Changelog
- Check upstream https://github.com/dani-garcia/vaultwarden/releases/tag/1.37.5

### Security Fixes

This release contains security fixes for the following advisories. We strongly advise updating as soon as possible.

Website icons [GHSA-x9cq-f669-vrr4] (Medium, 5.3)
Emergency access [GHSA-9pjj-f9g5-3x4c] (Medium, 4.3)
These are private for now, pending CVE assignment and publishing at a later date.

### Note

This update is required for web vault 2026.7.1+ to turn two-step login methods on or off, and for 2026.9.0+ to take over an account through emergency access. Please update before reporting any issues with them.

### Upgrade notes

- Web vault: the bundled web vault is now v2026.10.1. If you serve your own web vault older than v2026.7.1, you might have compatibility issues.
- Configuration: invalid values now stop startup with an error. Numeric options have tighter types, so negative or too large values are rejected, for example above 65535 for LOGIN_RATELIMIT_MAX_BURST, TRASH_AUTO_DELETE_DAYS, EVENTS_DAYS_RETAIN or SMTP_TIMEOUT, or above 255 for EMAIL_ATTEMPTS_LIMIT. The rate limit *_SECONDS and *_MAX_BURST options, DATABASE_TIMEOUT and DATABASE_IDLE_TIMEOUT must be at least 1, DATABASE_MIN_CONNS can't be larger than DATABASE_MAX_CONNS, and DUO_CONTEXT_PURGE_SCHEDULE and PURGE_INCOMPLETE_SSO_AUTH must be empty or a valid cron expression.

### What's Changed
- Close WebSocket connections that stop responding
- Validate the Duo and SSO purge schedules on startup
- docs: fix "runnning" typo in playwright README
- docs: fix Playwright test env link
- Fix group import to update groups on data change
- [Web 2026.9.0] Support new Emergency Access password payload
- [Web 2026.9.0] Support new account recovery password payload
- [web-v2026.7.1] 2FA userVerificationToken for Authenticator, Email and Duo
- Fix email 2FA for SSO logins on iOS and Android
- Update web-vault to v2026.8.0
- Add revision_date to org policies
- Add Windows desktop Autotype feature flags and policy support
- Add biometrics-sdk-ipc feature flag (closes #7812)
- Delete auth requests when deleting a user
- Add unsupported riscv64 architecture
- api/icons: fix typos in the minimum PNG size comment
- docs: fix connect-src description grammar
- Update dependencies
- Misc fixes regarding jobs and config
- Send null org key for unconfirmed members in sync
- Return stored manage flag for groups in collections/details
- Fix bulk cipher share response for SDK clients
- Upgrade to Rocket v0.5.2
- Fix typo in vaultwarden.env
- Remove expired cookies from the icon cookie jar
- fix(attachments): enforce quota at v2 metadata reservation
- Align cipher org checks & attachment notification with upstream
- Document two feature flags in .env.template
- Fix push device unregistration endpoint
- Don't return internal error details in bulk member responses; gate SSO token logging
- [Web 2026.9.0] Add Fill Assist + Policy support
- Add registration email verification clicked endpoint
- Make 2FA remember duration configurable
- Bump user revision once for bulk cipher move
- Send logout notification when deleting a user
- Two small fixes for upstream parity
- Add missing HTTP auth and policy revocation audit events
- Clippy fixes, crate and web-vault updates
- Escape request values in log messages
