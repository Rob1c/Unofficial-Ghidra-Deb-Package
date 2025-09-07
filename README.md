# Unofficial Ghidra Debian Package

This repository provides an **unofficial `.deb` package** for installing [Ghidra](https://github.com/NationalSecurityAgency/ghidra), the open-source reverse engineering framework developed by the National Security Agency (NSA).

## Purpose

The goal of this project is to simplify the installation of Ghidra on Debian-based Linux distributions by offering a pre-built `.deb` package.  
This initiative is intended as a community contribution and is **not affiliated with, endorsed by, or sponsored by the NSA or the official Ghidra development team**.

## ⚖️ License Compliance

Ghidra is distributed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).  
This package fully complies with the terms of that license:

- No modifications have been made to Ghidra's source code.
- No trademarks, logos, or branding from the NSA or Ghidra are used beyond descriptive reference.
- The original license and NOTICE files are included where applicable.

This `.deb` package is provided **as-is**, without warranty or guarantee of functionality. Use at your own discretion.

## 📦 Package Details

- **Version**: `11.4.2`
- **Architecture**: `x86_64 (amd64)`
- **Dependencies**: `openjdk-17-jre, python3, libgtk-3-0`
- **Install location**: `/opt/ghidra/`

## Installation
Via apt (**recommended**, because it automatically resolves dependencies):
```bash
sudo apt install ghidra-[version].deb
```
Or via dpkg:
```bash
sudo dpkg -i ghidra-[version].deb
```
## Compatibility
This package was developed and tested under `Ubuntu 24.04.3 LTS x86_64 `, but it should work fine under every debian-based system.
## Acknowledgements
**All credit for Ghidra goes to the National Security Agency**. This project exists solely to support the reverse engineering community by improving accessibility and usability.


## 🤝 Willingness to Collaborate
If the NSA or the official Ghidra development team finds this packaging effort useful, **I am fully open to transferring ownership, collaborating, or integrating this work into the official distribution channels.** My intention is to support the reverse engineering community and contribute respectfully to the Ghidra ecosystem.

## Feedback & Contributions
If you encounter issues or have suggestions, feel free to open an issue in this repository. You may also consider submitting feedback to [the official Ghidra GitHub](https://github.com/NationalSecurityAgency/ghidra) repository if relevant.

#### **Disclaimer**: This repository is maintained independently and is not affiliated with the United States Government or the NSA. Use of the Ghidra name is purely descriptive and does not imply endorsement.
