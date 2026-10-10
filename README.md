# 404: Gamified TCP/IP Protocol Simulation

[![Engine](https://img.shields.io/badge/Engine-Unity%202D-222c37?logo=unity)](https://unity.com/)
[![Language](https://img.shields.io/badge/Language-C%23-239120?logo=c-sharp)](#)
[![CI](https://github.com/jyliew1912/404-Not-FoundD/actions/workflows/lint-check.yml/badge.svg)](https://github.com/jyliew1912/404-Not-FoundD/actions)

> **Portfolio Note**  
> This is my personal portfolio fork of a 5-person team project.  
> I was responsible for **UI/UX, Scene Management, Global State, and Interactive Item Logic**.

An educational 2D platformer that teaches the 5-layer TCP/IP stack through gameplay. Players solve protocol challenges to restore a disconnected campus network.

[🎮 Download Executable](https://drive.google.com/file/d/1K-p4Imx_Qw9AnSHC-9ILOJ9ofIJY7yrj/view?usp=drive_link) • [📹 Demo Video](https://drive.google.com/file/d/17JK7yR0lvcDW2QUjUkqbSwqxQMnGvOqo/view?usp=drive_link)


## 👩‍💻 My Contributions

I focused on the core game architecture and player-facing systems:

- **Scene Orchestration** — Centralized scene transitions with `SceneManager.LoadSceneAsync` across all 5 TCP/IP levels
- **Global State Management** — Designed the `GameManager` (Singleton) that coordinates protocol flags, stage state, and data flow
- **Interactive Item Logic** — Programmed collectible entities (HTTP status codes, network tokens) and collision pipelines (`OnTriggerEnter2D`)
- **UI/UX Framework** — Built the full dynamic HUD (health, protocol hints, stage metrics) with event-driven updates


## 🌐 Network Protocol Level Mapping

| Level | TCP/IP Layer | Concept Simulated | Game Mechanics |
|:-----:|--------------|-------------------|----------------|
| **05** | Application | HTTP status codes & DoS | Evade DDoS, extract `HTTP 200 OK` |
| **04** | Transport | TCP handshake | Decode payloads to complete handshake |
| **03** | Network | IPv4 & subnet routing | Parse addresses, avoid invalid hops |
| **02** | Data Link | MAC addressing | Decode 48-bit hex addresses |
| **01** | Physical | Throughput & latency | Collect resources under time pressure |


## 🛠 Tech Stack & Architecture

- **Engine**: Unity 2D + Physics + Tilemap  
- **Language**: C#  
- **Patterns**: Singleton Managers, State Pattern, Observer (UnityEvents)

```text
GameManager (Singleton)
├── Gameplay Systems (Character, Collision, Inventory)
├── Persistence Module (Player Profile, Level Progress)
└── Level Layer Logic (L5 → L1)
```


## 🚀 How to Run

**Pre-built:** Download the executable from the link above and run `404.exe`.

**From source:**
```bash
git clone https://github.com/jyliew1912/404-Not-FoundD.git
```
Open in Unity Hub with **Unity 2021.3 LTS**, then Build & Run the scenes: `Login, L5, L4, L3, L2, L1, Win`.



## 👥 Full Team

| Member | Role |
|--------|------|
| **劉靖媛 ([@jyliew1912](https://github.com/jyliew1912))** | UI/UX, Scene Management, Global State, Item Logic |
| 陳湘昀 (@sony0505) | Data Persistence, Camera, Map Optimization, QA |
| 莊昀潔 (@Jayechuang) | Terminal, Pause Menu, 2D Assets |
| 黃煜庭 (@ccuhyt) | Login, Procedural Map, Audio |
| 余沛穎 (@YuPatty) | Player Movement, Score/Health, Documentation |


**Original team repository:** [404-Not-FoundD/Final-Project](https://github.com/404-Not-FoundD/Final-Project)