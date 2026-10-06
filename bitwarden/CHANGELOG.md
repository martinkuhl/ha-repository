## What’s new in 1.37.4

## Changelog
- Check upstream https://github.com/dani-garcia/vaultwarden/releases/tag/1.37.4

### Security Fixes

This release contains security fixes for the following advisories. We strongly advise updating as soon as possible.

- Organization member revocation [GHSA-69q9-v8p6-xvx3] (High, 8.1)
- Two-factor authentication [GHSA-7jg8-8m5x-6j9r] (Medium, 6.8)
- Organization invitations [GHSA-v576-3wvq-xh3c] (Medium, 6.8)
- Attachments [GHSA-q5x6-grh5-fqgc] (Medium, 6.5)
- Organization event logs [GHSA-64mc-4p6f-r7x9] (Medium, 4.3)
- Cipher sharing [GHSA-7ccc-c43j-4p36] (Medium, 4.3)
- Organization API key [GHSA-qwx4-wcv4-mpcv] (Low, 3.8)
- Additional dependency updates and minor security enhancements
- These are private for now, pending CVE assignment and publishing at a later date.

### Upgrade notes

- Reverse proxies: with IP_HEADER=X-Forwarded-For, the client IP is now the rightmost address that isn't in IP_HEADER_TRUSTED_PROXIES (it used to be the leftmost). If you have several proxies in a row, for example a CDN in front of nginx, add all of them to IP_HEADER_TRUSTED_PROXIES. Otherwise the address of the proxy in front is used for rate limiting and logs.
- Sends: bw send receive on CLI 2026.4.2 and older no longer works, the same as against Bitwarden's own servers since v2026.8.0. Creating and managing Sends works on all clients.
- Feature flags: these flags were removed because no client reads them anymore: ssh-agent, ssh-key-vault-item, mutual-tls, anon-addy-self-host-alias, simple-login-self-host-alias, pm-25373-windows-biometrics-v2, pm-26340-linux-biometrics-v2, desktop-ui-migration-milestone-1 to -4, cxp-import-mobile and cxp-export-mobile. If EXPERIMENTAL_CLIENT_FEATURE_FLAGS still lists one of them, startup logs a warning and saving settings in the admin panel fails until it's removed.
- Duo: DUO_USE_IFRAME (the deprecated Traditional Prompt) is removed and ignored if set.
- Custom templates: there's a new email template, email/recover_twofactor, sent after a login with a two-step recovery code.
- The legacy POST /identity/accounts/register and POST /api/accounts/prelogin endpoints are removed. No current client uses them.

### What's Changed
- [Web 2026.9.0] Support the vault banner policy
- Add support for basic auth response client feature flag
- [web-v2026.8.1] store the user key ID
- Add organizationsNew and policiesNew to sync response
- Add pm-32009-new-item-types feature flag
- Update Crates, GHA and JS
- Add pm-34171-card-scanner feature flag
- Set user_created bool for each separate invitation
- Fix revoked org members retaining access to org ciphers
- Ensure all user checked routes are confirmed
- Fix cortex-a53 build issues when using xx-cargo
- Add undetermined-cipher-scenario-logic feature flag
- Add Windows native credential sync to supported feature flags
- Hide the whole change-email section when EMAIL_CHANGE_ALLOWED is false
- Fix Clippy warnings across all targets
- Admin reset: 2fa email fallback need a verified email
- Sends cleanup: remove legacy endpoints and align with upstream
- Remove legacy API endpoints and compatibility code
- Align API with upstream and remove unwraps
- Update crates, Rust and other dependencies
