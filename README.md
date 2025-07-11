# Standalone QNX VM Virtualization

## Overview
This document outlines the architecture and setup for a **Standalone QNX Virtual Machine (VM)** running on a Linux host using QEMU/QNX hypervisor. It enables real-time audio streaming from QNX guest applications to a developer's browser via WebRTC.

## Assumptions
The architecture is based on the assumption that the WebRTC server, including TURN and signaling servers, is provided by QNX.

---
<img width="671" height="353" alt="image" src="https://github.com/user-attachments/assets/575c8277-0ab3-443c-8d84-52419adaf694" />


## Architecture Components

### 1. **Linux Host**
- Base OS that runs the virtualization stack.
- Hosts the QEMU/QNX hypervisor.

### 2. **QEMU/QNX Hypervisor**
- Virtualization layer that manages the QNX Guest OS.
- Provides isolation and resource management.

### 3. **QNX Guest OS**
Contains the following components:
- **native-apps**: Standard QNX applications.
- **Cluster apps**: Intelligent cockpit cluster applications.
- **Safety apps**: Safety-critical applications.
- **io-audio**: QNX audio manager service. Manages audio I/O and routes audio streams.
- **WebRTC Server**: Streams audio data to external clients using WebRTC.

### 4. **Developer PC**
- Runs a **WebRTC client** (e.g., Chrome browser).
- Receives and plays audio streamed from the QNX Guest OS.

### 5. **Local Audio Output**
- Audio output device (e.g., speakers/headphones) connected to the Developer PC.

---

## Data Flow

1. Applications in the QNX Guest OS generate audio data.
2. `io-audio` captures and processes the audio.
3. The **WebRTC server** streams the audio to the Developer PC.
4. The **WebRTC client** (Chrome browser) receives and plays the audio via local output.


