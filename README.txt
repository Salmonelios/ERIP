# ⛈️ ERIP: Risk of Rain 2 Telemetry & Emotion Analysis

## 🎯 Overview

**ERIP** (and the **ScienceKit** plugin) is a multi-modal research toolkit designed to synchronize in-game telemetry with external data sources like heart rate monitors and emotion recognition software.

Whether you're studying player stress levels during a Mithrix fight or aggregating item-pick-up efficiency, this project provides the pipeline to move from "raw game chaos" to "structured analytical insights."

---

## 🏗️ Project Structure

The repository is split into two distinct worlds: the **Data Collector** (C#) and the **Data Cruncher** (Python).

```text
.
├── DATASET.csv                # The final unified output
├── RoR2/                      # "ScienceKit" C# Plugin
│   └── source/                # Hooks into RoR2 to extract real-time stats
│       ├── Statistics/        # Loggers for items, kills, health, and inputs
│       └── Entries/           # Data models for telemetry points
└── Python/                    # Data Science Suite
    ├── DataAggregation/       # Specialized modules to merge biometric & game data
    └── Analysis/              # Scripts for heart rate, image emotion, and cleanup

```

---

## 🔌 Components

### 1. The ScienceKit (C# Plugin)

Since we have to play by the game's rules, this component is built in C#. It acts as a BepInEx-style plugin for *Risk of Rain 2* to record:

* **Player Vitals:** Health fluctuates, shields, and "Game Simplifier" states.
* **Input Telemetry:** Every button press and axis movement.
* **World Events:** Enemy spawns, kills, and item acquisitions.
* **Persistence:** Automatically formats and saves data to `RowFormatter` for easy CSV consumption.

### 2. The Analysis Suite (Python)

This is where the heavy lifting happens. Once you have your game logs, these scripts transform raw numbers into research-grade datasets:

* **Biometric Sync:** Processes heart rate data and synchronizes it with game timestamps.
* **Visual Emotion AI:** Analyzes facial expressions (via `image_emotion.py`) to map player reactions to in-game events.
* **Aggregation:** Specialized "Aggregators" for every data type (Items, Buttons, Enemies, etc.) to create a clean, unified `DATASET.csv`.

---

## 🚀 Getting Started

### Data Collection (The Game Side)

1. Ensure you have a BepInEx environment set up for *Risk of Rain 2*.
2. Compile the `ScienceKit` source or drop the DLL into your plugins folder.
3. Play the game. The plugin will generate log files in the specified directory.

### Data Processing (The Python Side)

1. **Install dependencies:**
```bash
pip install pandas numpy opencv-python  # and your specific emotion/HR libraries

```


2. **Run Preparation:** Use `heart_rate_preparation.py` and `image_preparation.py` to clean your external data.
3. **Join the Data:**
Run `data_joining.py` to merge the RoR2 logs with your biometric data.

---

## 🛠️ Requirements

* **Game:** *Risk of Rain 2* (PC version).
* **Environment:** Python 3.x and a .NET Standard 2.0 compatible IDE (like Visual Studio or Rider).
* **External Data:** Designed to work with heart rate monitors and webcam-based emotion tracking.

## 📜 License

This project is intended for educational and research purposes. Please credit the **ScienceKit** framework if used in academic publications.

---

**Would you like me to add a specific "How to Contribute" section or perhaps expand on the technical details of one of the Python aggregators?**