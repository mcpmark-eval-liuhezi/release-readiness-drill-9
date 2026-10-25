# Release readiness review: axios

Research completed for the quarterly release-readiness review and CI-failure drill.
Primary HTTP dependency: `axios` (npm).

## Latest release

Checked the latest published release of the `axios/axios` repository:

- **Tag:** `v1.20.0`
- **Release name:** `v1.20.0`
- Published: 2026-08-24 (created 2026-08-19), author `jasonsaayman`
- Target: `v1.x`
- URL: https://github.com/axios/axios/releases/tag/v1.20.0

Notable for release readiness: this release carries a security fix hardening runtime option
handling against shared and foreign prototype pollution and normalizing unsafe interceptor
replacement objects (#11141).

## Advisories

Advisories were collected from two sources: the security advisories published on the
`axios/axios` repository, and GitHub's global advisory database filtered to the `axios`
npm package.

Repository security advisories (`axios/axios`):

- `GHSA-542g-h47m-68v8` — **high** — Denial of Service via Unhandled 'error' Event in
  HTTP/2 ClientHttp2Session Initialization

Global advisory database (npm package `axios`):

- `GHSA-j8rh-479h-cp32` — **medium** — Header Injection via Inherited headers After
  Minimal Interceptor

The two most severe advisories found across both sources were selected and their full
records pulled; they are documented in the next section. Both are patched in `1.20.0`.

## Advisory detail

### GHSA-542g-h47m-68v8

- **Advisory id:** `GHSA-542g-h47m-68v8`
- **CVE:** `CVE-2026-101901`
- **Severity:** high
- **Affected versions (global advisory record):** `>= 1.13.0, < 1.20.0`
- **Patched versions (global advisory record):** first_patched_version `1.20.0`
- **Affected/patched as stated on the `axios/axios` repository advisory:**
  vulnerable_version_range `>=1.13.0`, patched_versions `>=1.20.0`
- **Summary:** Axios: Denial of Service via Unhandled 'error' Event in HTTP/2
  ClientHttp2Session Initialization
- **CWEs:** CWE-400 (Uncontrolled Resource Consumption)
- **Workaround:** disable axios HTTP/2 for untrusted or user-influenced destinations and
  use the default HTTP/1.1 adapter until a fixed release is available
- **Links:** https://github.com/axios/axios/security/advisories/GHSA-542g-h47m-68v8,
  https://nvd.nist.gov/vuln/detail/CVE-2026-101901

### GHSA-j8rh-479h-cp32

- **Advisory id:** `GHSA-j8rh-479h-cp32`
- **CVE:** `CVE-2026-101904`
- **Severity:** medium
- **Affected versions:** `>= 1.0.0, < 1.20.0`
- **Patched versions:** first_patched_version `1.20.0`
- **Summary:** Axios: Header Injection via Inherited headers After Minimal Interceptor
- **CWEs:** CWE-74 (Injection), CWE-1321 (Prototype Pollution)
- **Workaround:** interceptors that rebuild config should always set an own `headers`
  property (e.g. preserve `config.headers` or set `headers: {}`)
- **Links:** https://github.com/axios/axios/security/advisories/GHSA-j8rh-479h-cp32,
  https://nvd.nist.gov/vuln/detail/CVE-2026-101904

## Team routing

The authenticated user's team memberships were checked to determine whether there is
anyone to pull in as a reviewer.

Result, exactly as returned by the teams check:

- org: `mcpmark-eval-liuhezi`
- teams: `[]` (empty)

The teams check returned no teams, so it did not surface anyone who can be requested as a
reviewer on a repository under the account. No reviewer request was issued as part of this
drill.
