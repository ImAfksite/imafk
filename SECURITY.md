---

### 2. `SECURITY.md`

```markdown
# Security Policy

## Supported Versions

The following table indicates the versions of the I’M AFK platform currently monitored for security updates and patches.

| Component / Version | Supported          | Status                                 |
| ------------------- | ------------------ | -------------------------------------- |
| v3.x (Current)      | :white_check_mark: | Active support & continuous monitoring |
| v2.x                | :white_check_mark: | Security patches only                  |
| < v2.0              | :x:                | Deprecated                             |

---

## Security & Sandboxing Architecture

I’M AFK executes third-party and community-submitted web applications using a zero-trust, client-side sandboxing model:

1. **Isolated Iframe Sandboxes**:
   - All executable scripts run within sandboxed `<iframe>` contexts restricted via the `sandbox` attribute (`allow-scripts`, `allow-forms`, `allow-pointer-lock`, `allow-modals`, `allow-same-origin`).
   - Third-party code is prevented from accessing parent window storage, authentication cookies, or navigation controls outside its sandbox context.

2. **Static Code Analysis**:
   - The administrative operations panel (`admin.html`) runs automated heuristic static scans across all catalog submissions to detect:
     - Embedded cryptocurrency mining scripts
     - Arbitrary dynamic `eval()` execution vectors
     - Parent window location manipulation / frame escape attempts
     - Suspicious third-party network outbound requests

3. **Client-Side Storage Isolation**:
   - Studio files, snapshots, and user preferences reside exclusively within the user's browser `localStorage` and memory buffers, eliminating server-side credential leakage risks.

---

## Reporting a Vulnerability

We prioritize platform integrity and user safety. If you discover a security vulnerability or exploit within our core files, sandboxing logic, or database integrations, please follow these steps:

### 1. Primary Reporting Channels
- **Support Dispatch Portal**: Submit a report via [`contact.html`](contact.html) selecting **Report Broken Project / Bug** or **Copyright/DMCA**.
- **Security Email**: Dispatch vulnerability details to `security@imafk.net` or `admin@imafk.net`.
- **GitHub Security Advisory**: Open a private advisory on the repository at [github.com/imafksite/imafk/security/advisories](https://github.com/imafksite/imafk).

### 2. Report Details to Include
Please provide a comprehensive summary to expedite verification:
- Type of issue (e.g., Sandbox Escape, XSS vector, Supabase RLS bypass, DoS loop).
- Clear, step-by-step reproduction instructions or a minimal Proof of Concept (PoC).
- Affected files, endpoints, or browser configurations.

### 3. Response SLA
- **Initial Acknowledgment**: Within **24 hours**.
- **Triage & Remediation Plan**: Within **48 to 72 hours**.
- **Public Disclosure**: Coordinated disclosure after patches are deployed to the live network.
