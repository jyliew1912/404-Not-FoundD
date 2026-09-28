# 404: Reconnect — Gamified TCP/IP Network Protocol Simulation

[![Unity](https://img.shields.io/badge/Engine-Unity%202D-222c37?style=for-the-badge&logo=unity)](https://unity.com/)
[![Language](https://img.shields.io/badge/Language-C%23-239120?style=for-the-badge&logo=c-sharp)](https://docs.microsoft.com/en-us/dotnet/csharp/)

> An educational 2D platformer engineered in Unity/C# that bridges computer networking fundamentals with interactive game mechanics. Players solve real-world protocol constraints across the 5 layers of the TCP/IP stack to restore a disconnected campus network.

[🎮 Download Executable](https://drive.google.com/file/d/1K-p4Imx_Qw9AnSHC-9ILOJ9ofIJY7yrj/view?usp=drive_link) • [📹 Watch Demo Video](https://drive.google.com/file/d/17JK7yR0lvcDW2QUjUkqbSwqxQMnGvOqo/view?usp=drive_link)


## 📌 Executive Summary

Network protocol stacks are traditionally taught through abstract diagrams and packet capture analyzers (e.g., Wireshark). **404: Reconnect** translates the abstraction of the 5-layer Internet protocol suite into an interactive state machine where progression requires understanding protocol-specific constraints:
* **Application Layer**: Decoding HTTP status codes and mitigating volumetric traffic anomalies (DoS/DDoS simulations).
* **Transport Layer**: Simulating connection-oriented handshakes and parameter verification.
* **Network Layer**: IP addressing resolution, subnet routing, and routing table exploration.
* **Data Link Layer**: Hexadecimal physical addressing (MAC address) parsing and frame identification.
* **Physical Layer**: Time-bounded signal transmission and throughput simulation under resource constraints.


## 🛠 Tech Stack & Software Architecture

### Core Technologies
* **Engine & Tooling**: Unity Engine, Unity 2D Physics Engine, Tilemap Systems.
* **Language & Runtime**: C# (.NET Framework / Mono Runtime).
* **Data Persistence**: JSON Serialization / Binary Serialization / `PlayerPrefs` for session persistence.
* **VCS**: Git, GitHub flow with modular branching.

### Architectural Patterns
* **Singleton Managers**: Centralized `GameManager`, `AudioManager`, and `UIManager` to preserve persistent game state across asynchronous scene transitions (`DontDestroyOnLoad`).
* **State Pattern**: Implemented for character locomotion (idle, run, multi-jump, invulnerability state machine).
* **Observer Pattern (C# Actions / UnityEvents)**: Decoupled event messaging between collision layers, score trackers, and UI viewmodels.
* **Data Persistence Layer**: Encapsulated state storage capturing player metrics, session timers, and level completion flags.


```text
   ┌────────────────────────────────────────────────────────┐
   │                   GameManager (State)                  │
   └──────────┬─────────────────────────────────┬───────────┘
              │                                 │
     [Events / Actions]                [Data Serialization]
              │                                 │
 ┌────────────▼──────────┐            ┌─────────▼───────────┐
 │   Gameplay Systems    │            │  Persistence Module │
 ├───────────────────────┤            ├─────────────────────┤
 │ • Character Controller│            │ • Player Profile    │
 │ • Collision / Damage  │            │ • Level Progression │
 │ • Inventory & Buffs   │            │ • Session Telemetry │
 └────────────┬──────────┘            └─────────────────────┘
              │
 ┌────────────▼──────────┐
 │  Level Layer Logic    │
 │ (L5 -> L4 -> L3->...) │
 └───────────────────────┘
```


## 🌐 Network Protocol Level Mapping

| Level | TCP/IP Layer | Network Concept Simulated | Interactive Game Mechanics |
| :---: | :--- | :--- | :--- |
| **05** | **Application Layer** | HTTP/1.1 Status Codes & DoS Flood | Evade simulated DDoS attack vectors; evaluate dynamic server response codes to extract `HTTP 200 OK` for pipeline progression. |
| **04** | **Transport Layer** | Connection Handshakes (TCP Reliability) | Decode payload verification attributes dropped by entities to establish an authenticated handshake with the designated peer. |
| **03** | **Network Layer** | IPv4 Addressing & Subnet Routing | Parse address segments and evaluate network gateway paths; invalid hops trigger packet-drop penalties. |
| **02** | **Link Layer** | MAC Addressing & Frame Demuxing | Decode 48-bit hexadecimal hardware addresses through environmental clues to identify legitimate layer-2 interfaces. |
| **01** | **Physical Layer** | Throughput, Resource Latency & Bandwidth | Collect resource units within a deterministic timer constraint to simulate continuous packet delivery across physical media. |


## 👤 Individual Engineering Contributions

### Core Modules Developed
* **Scene Orchestration & Flow Control**:
  * Engineered centralized scene transition pipelines using Unity's `SceneManager.LoadSceneAsync`, guaranteeing seamless level switching across the 5 TCP/IP protocol stages.
  * Managed scene lifecycle events to eliminate dangling references and prevent memory leaks during scene reloads.
* **Global State & Variable Management**:
  * Architected a centralized state management pattern (`GameManager` / Singleton) to coordinate global variables, protocol validation flags, and runtime stage states across decoupled scenes.
  * Designed data flow conduits connecting backend game events to runtime progression logic.
* **Interactive Gameplay & Collectible Item Mechanics**:
  * Programmed scriptable behavior for core collectible entities (e.g., HTTP status code payloads, network tokens, and consumable items).
  * Built trigger-based collision interaction pipelines (`OnTriggerEnter2D`) that handle payload evaluation and dynamic player buff execution.
* **UI/UX Framework & View-State Binding**:
  * Constructed the full dynamic user interface (Canvas architecture, health counters, protocol hint displays, and stage metrics).
  * Decoupled UI rendering from core game logic using event callbacks, ensuring zero-latency HUD updates upon state changes.


## 🎮 Game Systems & Mechanics

* **Locomotion Mechanics**: WASD / Arrow key directional mapping with multi-jump kinematic handling.
* **Dynamic Modifiers & Status Effects**:
  * **Invulnerability State**: Activated via streak consumption; triggers temporary collider layer ignore (`Physics2D.IgnoreLayerCollision`).
  * **Proximity Vector Field (Magnet)**: Pulls nearby collectible colliders toward the player using vector interpolation (`Vector2.MoveTowards`).
  * **Dynamic Timer & Penalty Pipeline**: Real-time decrementing countdown with penalty offsets driven by obstacle triggers.
* **In-Game Terminal & Diagnostics**: An integrated console window enabling runtime debugging, input inspection, and state reset.

## 🚀 Installation & Build Guide

### Running Pre-Built Binaries
1. Download the executable archive from [Google Drive](https://drive.google.com/file/d/1K-p4Imx_Qw9AnSHC-9ILOJ9ofIJY7yrj/view?usp=drive_link).
2. Extract the `.zip` package.
3. Launch `404.exe` (Windows).

### Building from Source
1. Clone your fork:
  ```bash
   git clone https://github.com/jyliew1912/404-Not-FoundD.git
   cd 404-NotFoundD
  ```

2. Open **Unity Hub** and select **Add project from disk**.
3. Launch using Unity **2021.3 LTS** (or the target version specified in `ProjectSettings/ProjectVersion.txt`).
4. Navigate to `File` $\rightarrow$ `Build Settings...`, select target platform, ensure scenes `[Login, L5, L4, L3, L2, L1, Win]` are indexed, and select **Build and Run**.


## 👥 Engineering Team & Contributions

* **劉靖媛** ([@jyliew1912](https://github.com/jyliew1912)) — UI/UX Display Architecture, Interactive Item Logic, Scene Management, Global Variable & State Management.
* **陳湘昀** ([@sony0505](https://github.com/sony0505)) — Data Persistence & File I/O, Dynamic Camera Controller, Map & Tilemap Optimization, Primary Item Mechanics, System Integration, Debugging & QA.
* **莊昀潔** ([@Jayechuang](https://github.com/Jayechuang)) — In-Game Terminal Interface, Pause Menu Subsystem, 2D Asset Illustration, Primary Item Mechanics, Map Optimization, Debugging.
* **黃煜庭** ([@ccuhyt](https://github.com/ccuhyt)) — Authentication & Login Interface, Procedural Map Generation, 2D Asset Illustration, Audio & SFX Engineering.
* **余沛穎** ([@YuPatty](https://github.com/YuPatty)) — Player Kinematics & Locomotion, Score & Health System Architecture, Audio Integration, Item Logic, 2D Art Assets, Technical Documentation & README.


## 📚 References & Academic Resources

* Kurose, J. F., & Ross, K. W. *Computer Networking: A Top-Down Approach*. Pearson.
* Unity Technologies. *Unity 2D Physics Documentation & Best Practices*.
* Gamma, E., Helm, R., Johnson, R., & Vlissides, J. *Design Patterns: Elements of Reusable Object-Oriented Software*. Addison-Wesley.
