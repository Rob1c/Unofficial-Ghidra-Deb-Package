<table>
  <tr>
    <td width="200">
      <img src="uno-ghidra.png" width="200" alt="Logo">
    </td>
    <td>
      <h1>Unofficial Ghidra Debian Package</h1>
      <img src="https://github.com/Rob1c/Unofficial-Ghidra-Deb-Package/actions/workflows/build.yml/badge.svg" alt="Build Status">     
      <img src="https://img.shields.io/badge/version-12.1.2-blue" alt="Version">
      <img src="https://img.shields.io/badge/license-Apache--2.0-green" alt="License"> 
      <img src="https://img.shields.io/badge/platform-Debian%20Based%20Systems-red" alt="Platform">
      <img src="https://img.shields.io/badge/GPG-signed-success" alt="GPG Signed">
    </td>
  </tr>
</table>

This repository provides an **unofficial `.deb` package** for installing [Ghidra](https://github.com/NationalSecurityAgency/ghidra), the open-source reverse engineering framework developed by the National Security Agency (NSA).

## Purpose

The goal of this project is to simplify the installation of Ghidra on Debian-based Linux distributions by offering a pre-built `.deb` package, kept automatically in sync with upstream releases.
This initiative is intended as a community contribution and is **not affiliated with, endorsed by, or sponsored by the NSA or the official Ghidra development team**.

## ⚖️ License Compliance

Ghidra is distributed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).  
This package fully complies with the terms of that license:

- No modifications have been made to Ghidra's source code.
- No trademarks, logos, or branding from the NSA or Ghidra are used beyond descriptive reference.
- The original license and NOTICE files are included where applicable.

This `.deb` package is provided **as-is**, without warranty or guarantee of functionality. Use at your own discretion.

## 📦 Package Details

- **Latest Version**: `12.1.2`
- **Architecture**: `x86_64 (amd64)`
- **Dependencies**: `openjdk-21-jre, python3, libgtk-3-0`
- **Install location**: `/opt/ghidra/`

## Installation

Download the latest signed `.deb` from [Releases](https://github.com/Rob1c/Unofficial-Ghidra-Deb-Package/releases). **We strongly recommend verifying it first** — see [Verifying a release](#verifying-a-release) below.

Via apt (**recommended over dpkg**, because it automatically resolves dependencies):
```bash
sudo apt install ./ghidra_[version]_amd64.deb
```
Or via dpkg:
```bash
sudo dpkg -i ./ghidra_[version]_amd64.deb
sudo apt -f install   # resolve any missing dependencies
```

> **Note:** a full APT repository (so updates arrive via `apt upgrade`) is planned but not available yet. For now, check [Releases](https://github.com/Rob1c/Unofficial-Ghidra-Deb-Package/releases) for new versions.

## Compatibility
This package was developed and tested under `Ubuntu 24.04.3 LTS x86_64` and `Debian 13 "Trixie" (Stable)`, but it should work fine under every Debian-based system.

---

## Why trust this

This is a third-party package — not an official NSA/Ghidra or Debian artifact. You shouldn't have to take that on faith, so here's exactly what's verifiable and how to check it yourself.

| Concern | What this project does | How to check |
|---|---|---|
| **Are the binaries unmodified?** | Pulled directly from the official [Ghidra GitHub Releases](https://github.com/NationalSecurityAgency/ghidra/releases), zero patching of the application itself | Compare against the upstream release assets/checksums |
| **Is the build process visible?** | 100% built via [GitHub Actions](.github/workflows/build.yml) on a public, auditable workflow — no local/manual builds ever published | Read the workflow file directly, or check the [Actions tab](https://github.com/Rob1c/Unofficial-Ghidra-Deb-Package/actions) for run history |
| **Is the `.deb` itself authentic?** | Every release is signed with a dedicated GPG key | `gpg --verify ghidra_<version>_amd64.deb.asc ghidra_<version>_amd64.deb` |
| **Has it been tampered with after signing?** | SHA256 checksums published and signed for every artifact | `sha256sum -c ghidra_<version>_amd64.deb.sha256` |
| **Will it stay up to date?** | CI checks daily for new upstream Ghidra releases and rebuilds automatically — see [Update policy](#update-policy) | Check the [Actions tab](https://github.com/Rob1c/Unofficial-Ghidra-Deb-Package/actions) for the scheduled run history |
| **Who is responsible for this?** | Maintained by [@Rob1c](https://github.com/Rob1c), single maintainer, no anonymous publishing | Commit history and release authorship are public |

**Signing key fingerprint:** `E1D0 D608 02FA D2B2 578E  5CF4 7649 81E0 7F0E EC38`
Public key: [`ghidra-deb-signing-key.asc`](https://github.com/Rob1c/Unofficial-Ghidra-Deb-Package/blob/main/ghidra-deb-signing-key.asc) · also published on [keyserver.ubuntu.com](https://keyserver.ubuntu.com/pks/lookup?search=E1D0D60802FAD2B2578E5CF4764981E07F0EEC38&op=index)

### Verifying a release

```bash
# Import the key once
curl -fsSL https://raw.githubusercontent.com/Rob1c/Unofficial-Ghidra-Deb-Package/main/ghidra-deb-signing-key.asc | gpg --import

# Verify the fingerprint matches BEFORE trusting it
gpg --fingerprint E1D0D60802FAD2B2578E5CF4764981E07F0EEC38

# Verify the .deb against its signature
gpg --verify ghidra_<version>_amd64.deb.asc ghidra_<version>_amd64.deb

# Verify the checksum file itself is signed and untampered
gpg --verify ghidra_<version>_amd64.deb.sha256.asc ghidra_<version>_amd64.deb.sha256
sha256sum -c ghidra_<version>_amd64.deb.sha256
```

If both checks pass (`gpg` reports `Good signature`), the file you have is byte-for-byte what this project's CI produced and signed.

### Update policy

- CI checks daily (`schedule: cron`) whether a new Ghidra release exists upstream; if so, it rebuilds and re-signs automatically — no manual step required.
- Every release is versioned as `<ghidra-version>-<package-revision>` (e.g. `12.1.2-1`) so you always know exactly which upstream version you're running.

---

## Acknowledgements
**All credit for Ghidra goes to the National Security Agency**. This project exists solely to support the reverse engineering community by improving accessibility and usability.

## 🤝 Willingness to Collaborate
If the NSA or the official Ghidra development team finds this packaging effort useful, **I am fully open to transferring ownership, collaborating, or integrating this work into the official distribution channels.** My intention is to support the reverse engineering community and contribute respectfully to the Ghidra ecosystem.

## Feedback & Contributions
If you encounter issues or have suggestions, feel free to open an issue in this repository. Security-related reports are especially welcome. You may also consider submitting feedback to [the official Ghidra GitHub](https://github.com/NationalSecurityAgency/ghidra) repository if relevant.

#### **Disclaimer**: This repository is maintained independently and is not affiliated with the United States Government or the NSA. Use of the Ghidra name is purely descriptive and does not imply endorsement.
