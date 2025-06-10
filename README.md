# Open5GS + UERANSIM Sandbox

A full-featured, open-source 5G Core and RAN simulation environment using [Open5GS](https://github.com/open5gs/open5gs) and [UERANSIM](https://github.com/aligungr/UERANSIM). This project provides a modular, configurable, and reproducible sandbox for learning, testing, and developing 5G networks on Ubuntu-based systems.

## Overview

This repository integrates:

- **Open5GS**: An open-source implementation of the 4G/5G Core Network.
- **UERANSIM**: A C++-based 5G UE and gNB simulator supporting standalone (SA) deployments.

The sandbox environment is ideal for:

- Academic research
- Feature testing
- Rapid prototyping
- Educational labs

## Repository Structure

```bash
├── open5gs/              # Open5GS core source and modules
│   ├── docker/           # Docker setup for containerized deployment
│   ├── debian/           # Debian packaging configuration
│   ├── install/          # Binary and config install directory
│   ├── lib/              # Core protocol libraries and interfaces
│   ├── src/              # AMF, SMF, UPF, NRF, AUSF, etc.
│   ├── tests/            # Unit and integration tests
│   ├── vagrant/          # Vagrant VM templates
│   └── webui/            # React + Express.js Web UI for management
├── UERANSIM/             # User Equipment and gNB simulator
│   ├── config/           # UE/gNB configuration YAML files
│   ├── src/              # C++ sources: gNB, UE, CLI, binder, ASN.1
│   ├── tools/            # Utilities: ASN specs, Wireshark, binder
│   └── CMakeLists.txt    # Modular CMake build configuration
```

## Setup Instructions

### Prerequisites

- Ubuntu 20.04 or later
- cmake, g++, make, ninja-build
- git, curl, net-tools, iproute2
- Docker (optional for containerized deployments)

### Open5GS Build (Manual)

```bash
cd open5gs/
meson build --prefix=`pwd`/install
ninja -C build
ninja -C build install
```

### UERANSIM Build

```bash
cd UERANSIM/
make build
```

Binaries will be located in UERANSIM/build/.

## Simulation Use Cases

- Standalone 5G Core Testing
- UE Registration + PDU Session
- Interoperability with Free5GC / Custom Core
- Handover & Slice Testing
- VoNR & IMS Simulation (via config)

## WebUI

The Open5GS WebUI provides a graphical interface for managing:

- Subscribers (IMSI, K, OP/OPc)
- Session status
- Slice configuration
- Network topology

Built with React.js and Express.js, available in open5gs/webui/.

## Tools Included

- **nr-binder**: Helper binary to bind simulated UE interfaces
- **ASN.1 definitions**: NGAP, RRC for encoding/decoding
- **Wireshark dissector**: Lua plugin for NG-RAN tracing

## Testing & Validation

- Unit tests, fuzzing, and integration tests in open5gs/tests/
- CLI-driven simulation via nr-cli
- Wireshark supported tracing for NGAP, NAS, and GTP-U

## Maintainers

- Nikhil CP
- @Nikhil-cp1905 | cpnikhil05@gmail.com

## License

This repository includes components under AGPLv3 (Open5GS) and MIT (UERANSIM). See individual subproject directories for license details.
