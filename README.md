# 🏎️ ACRally LookAhead Steering Controller

> **Universal Telemetric Camera Bridge for Assetto Corsa Rally (ACRally)**  
> Developed by **ilborga70**

A lightweight, high-frequency (60Hz UDP) telemetry bridge designed to simulate realistic head and camera movement in Assetto Corsa Rally without requiring VR headsets or head-tracking hardware.

---

## 🆕 What's New in Version 0.9.0.0

- **Dynamic Apex Roll Tilt:** Added natural camera roll/tilt toward the corner apex when steering for enhanced immersion during high-speed cornering and drifting.
- **UI Controls:** Added an **ON/OFF toggle** for the Roll Tilt feature, along with an intensity percentage adjustment slider/spinbox.
- **Complete UDP Telemetry:** Real-time visual display in the GUI for both **Yaw** and **Roll** values sent directly to OpenTrack at 60Hz.
- **JSON Configuration Persistence:** Integrated automatic saving and loading for the Roll Tilt settings into the project's `.json` configuration file.

---

## 🚀 Quick Installation (First Time Only)

1. Download the mod's `.zip` archive.
2. Extract **ALL** the contents of the ZIP directly into the game's root folder:
   ```text
   ...\SteamLibrary\steamapps\common\Assetto Corsa Rally\
   ```
3. Overwrite when prompted by Windows to merge the `acr` folder.  
   > 💡 **Note:** The manual build will add the mod (`LookAhead Steering Controller.exe`) in path (`...\SteamLibrary\steamapps\common\Assetto Corsa Rally\`) and (`dinput8.dll`) (`AssettoCorsaRallyHeadTracking.asi`) in path (`acr\Binaries\Win64\`).

---

## 🎮 How to Use

1. In the game folder, run `LookAhead Steering Controller.exe`.
2. Select your device/steering wheel from the drop-down menu.
3. Adjust the desired sensitivity (recommended starting at 5% for natural movement) and click **Apply Real-Time**.
4. Leave the program open and launch **Assetto Corsa Rally** from Steam.
5. Get in the car and switch to **Cockpit/Helmet View**.
6. Set the actual degrees of the car in use in your driving controller, for example, Lancia Delta (`720°`).
7. Also set the actual degrees of the car in use in the `LookAhead Steering Controller` program, for example, Lancia Delta (`720°`).

---

## 🛠️ Step-by-Step Setup Guide Without Mod (`dinput8.dll` and `AssettoCorsaRallyHeadTracking.asi`)

> ℹ️ **Notice:** This manual standalone setup guide without mod files will be available as soon as the developers at **SuperNova** include native TrackIR support in an upcoming update.

### 0. Download & Install Prerequisites
- Download and install **OpenTrack**:  
  👉 [OpenTrack Releases (GitHub)](https://github.com/opentrack/opentrack/releases)

---

### 1. Configure LookAhead Steering Controller
1. Extract the `LookAhead Steering Controller` archive and launch `LookAhead Steering Controller.exe` as **Administrator**.
2. Set **Wheel Degrees (Lock-to-Lock)** to `1800°`.  
   > 💡 **Technical Note:** Keeping `1800°` as a fixed baseline in the software provides a full 5-rotation dynamic scale (`1800 ÷ 2 = 900°`, `1800 ÷ 3.33 = 540°`, `1800 ÷ 5 = 360°`, `1800 ÷ 10 = 180°`), guaranteeing 100% linear telemetry without rounding errors.  
3. **Important:** Adjust real physical steering lock degrees **exclusively within your wheelbase software** (e.g., Fanatec Fanalab, Simucube True Drive, Thrustmaster Control Panel) to match the car's specifications.

---

### 2. OpenTrack Universal Output Mapping
Open OpenTrack and set **Input** to `UDP over network` (Port `4242`) and **Output** to `freetrack 2.0 Enhanced`.

#### A. Options → Output Matrix
Configure the mapping matrix so a single profile works universally across both **LHD** and **RHD** vehicles:

| Destination | Source | Pre-invert | Post-invert |
| :--- | :--- | :---: | :---: |
| **Yaw** | `Yaw` | ☐ | ☐ |
| **Pitch** | `Roll` | ☐ | ☐ |
| **Roll** | `Roll` | ☐ | ☐ |
| **X** | `Disabled` | ☐ | ☐ |
| **Y** | `Disabled` | ☐ | ☐ |
| **Z** | `Disabled` | ☐ | ☐ |

#### B. Options → Filter Setup
Select the **Accela + Hamilton Filter** and set the parameters as follows:
- **Rotation filtering (Yaw, Pitch, Roll):**
  - **Smoothing:** `1.5°`
  - **Deadzone:** `0.03°`
- **Position filtering (X, Y, Z):**
  - **Smoothing:** `1mm`
  - **Deadzone:** `0.1mm`
- **Rotation Smoothing (Zoomed):**
  - **Max Added:** `0°`
  - **Max Z:** `9.6mm`

---

### 3. Run & Drive
1. Click **Start** inside OpenTrack.
2. Verify the status in the LookAhead Steering Controller's **System Process Status** diagnostic panel.
3. Launch **Assetto Corsa Rally** and scendi in pista! 🏎️💨

---

## 🎮 Windows Security & SimRacing: Why exclude the LookAhead Steering Controller? 🏎️💨

Have you noticed this file in the Windows Defender exclusions? Let’s break down why adding `LookAhead Steering Controller.exe` is essential for your setup! 👇

### 🛡️ 1. Preventing False Positives (Unjustified Blocks)
This program is a third-party utility designed to calculate wheel movements and camera angles for racing simulators. Because it reads hardware data and shares it directly with other software (like OpenTrack), Windows Defender might mistake this behavior for malicious activity (like a keylogger). Adding it to your exclusions stops Windows from blocking or deleting it by mistake!

### ⚡ 2. Eliminating Micro-Stuttering & Input Lag
Windows Antivirus scans files in real-time. As shown in the software window, this controller transmits data at a very high frequency (**60Hz — 60 times per second**). If the antivirus analyzed every single data packet while you were driving, it would cause:
- 📈 **Abnormal CPU spikes**
- ⏱️ **Delayed inputs (input lag)**
- 🛑 **Micro-stuttering during your races**

### 📂 3. Why the Entire D:\ Drive is Excluded
You can also see that the whole `D:\` folder is listed. Sim-racers often do this to prevent Microsoft Defender from constantly scanning heavy game files installed on a secondary HDD or SSD. This significantly improves overall loading times and game fluidity!

---

## 🔬 Is this file 100% safe?

**Yes!** If you are worried about security, the file has been fully analyzed on Jotti's malware scan. The results show **0/13 scanners** reporting malware, meaning top antiviruses like Kaspersky, BitDefender, and Avast found absolutely nothing.

🔗 **Check the full safety report here:** [Jotti's Malware Scan Report](https://virusscan.jotti.org/it-IT/filescanjob/g84ynyzizw)

---

👨‍💻 **Created by ilborga70** • [Pro-Sim Utilities Hub](https://github.com/ilborga70)
