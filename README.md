# 🏎️ ACRally LookAhead Steering Controller

<img width="994" height="1072" alt="1000092343" src="https://github.com/user-attachments/assets/6fc6eded-94d5-49a8-addd-4e978ecc64e5" />

> **Universal Telemetric Camera Bridge for Assetto Corsa Rally (ACRally)**  
> *Developed by ilborga70*

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

## 🛠️ Step-by-Step Setup Guide Without Mod (`dinput8.dll` and `AssettoCorsaRallyHeadTracking.asi`)

> ℹ️ **Notice:** This manual standalone setup guide without mod files will be available as soon as the developers at **SuperNova** include native TrackIR support in an upcoming update.

### 0. Download & Install Prerequisites
- Download and install **OpenTrack**:  
  👉 [OpenTrack Releases (GitHub)](https://github.com/opentrack/opentrack/releases)

---

### 1. Configure LookAhead Steering Controller
1. Extract the LookAhead Steering Controller archive and launch `LookAhead Steering Controller.exe` as Administrator.
2. **Set Steering Degrees:** Enter the exact steering lock value (degrees of rotation) required by the car in-game into the LookAhead Steering Controller.
3. **Match Wheelbase Settings:** Set the exact same degree value directly in your physical wheelbase software (e.g., Fanatec Fanalab, Simucube True Drive, Thrustmaster Control Panel, Moza Pit House).

> 💡 **Important:** Ensure that the steering lock degrees set in the LookAhead Steering Controller, in the in-game car setup, and in your physical wheelbase software are **100% identical** for optimal telemetric precision and response.

### 3. OpenTrack Universal Output Mapping
Open OpenTrack and set **Input** to `UDP over network` (Port `4242`) and **Output** to `freetrack 2.0 Enhanced`.

#### A. Options → Output Matrix
Configure the mapping matrix so a single profile works universally across both LHD and RHD vehicles.

<img width="2041" height="714" alt="New-opentrack-setup" src="https://github.com/user-attachments/assets/1fe6aa41-39e4-4d23-abe0-0bb33232063e" />

### 4. Run & Drive
1. Click **Start** inside OpenTrack.
2. Verify the status in the LookAhead Steering Controller's System Process Status diagnostic panel.
3. Launch **Assetto Corsa Rally** and scendi in pista! 🏎️💨

---

## 🎮 Windows Security & SimRacing: Why exclude the LookAhead Steering Controller? 🏎️💨

Have you noticed this file in the Windows Defender exclusions? Let’s break down why adding `LookAhead Steering Controller.exe` is essential for your setup! 👇

### 🛡️ 1. Preventing False Positives (Unjustified Blocks)
This program is a third-party utility designed to calculate wheel movements and camera angles for racing simulators. Because it reads hardware data and shares it directly with other software (like OpenTrack), Windows Defender might mistake this behavior for malicious activity (like a keylogger). Adding it to your exclusions stops Windows from blocking or deleting it by mistake!

### ⚡ 2. Eliminating Micro-Stuttering & Input Lag
Windows Antivirus scans files in real-time. As shown in the software window, this controller transmits data at a very high frequency (60Hz — 60 times per second). If the antivirus analyzed every single data packet while you were driving, it would cause:
* 📈 Abnormal CPU spikes
* ⏱️ Delayed inputs (input lag)
* 🛑 Micro-stuttering during your races

### 📂 3. Why the Entire D:\ Drive is Excluded
Sim-racers often do this to prevent Microsoft Defender from constantly scanning heavy game files installed on a secondary HDD or SSD. This significantly improves overall loading times and game fluidity!

### 🔬 Is this file 100% safe?
Yes! If you are worried about security, the file has been fully analyzed on Jotti's malware scan. The results show 0/13 scanners reporting malware, meaning top antiviruses like Kaspersky, BitDefender, and Avast found absolutely nothing.

### 🔒 Antivirus False Positives
Since the file was compiled using Win-PS2EXE, any alerts are due to the nature of the compiler wrapper. Don't worry — the code has been reviewed by IT experts and has been found to be completely safe and clean.

🔗 **Check the full safety report here:** [Jotti's Malware Scan Report](https://virusscan.jotti.org/it-IT/filescanjob/g84ynyzizw)

![1000092622](https://github.com/user-attachments/assets/f22a83c0-4dee-49ef-957b-4acb7290bf9d)

---

## 🛡️ Executable Authenticity & Digital Signature

To ensure maximum security and integrity, **LookAhead Steering Controller.exe** is digitally signed by the author (**ilborga70**).

### 🔒 Code Signing & Verification
* **Digital Signature:** The executable is signed using an official Microsoft `signtool.exe` certificate issued to `ilborga70`. This guarantees that the binary has not been tampered with, modified, or corrupted by third parties.
* **Integrity Check (SHA-256):** Each official release includes the exact SHA-256 hash of the `.exe` file. You can verify the file integrity locally via PowerShell:
  ```powershell
  Get-FileHash ".\LookAhead Steering Controller.exe" -Algorithm SHA256
  ```

### ⚠️ Windows SmartScreen Notice & Unblocking Guide
Since the executable uses a personal self-signed root certificate, Windows SmartScreen may block the execution without showing the "Run anyway" button on some systems. 

#### Option A: Quick Unblock File Properties (Recommended)
1. Right-click on `LookAhead Steering Controller.exe` → Select **Properties**.
2. At the bottom of the **General** tab, check the **Unblock** (*Annulla blocco*) checkbox.
3. Click **Apply** and then **OK**.
4. Launch the application normally.

#### Option B: Installing the Public Certificate
To permanently trust all updates from `ilborga70` without SmartScreen warnings:
* **Manual Installation:** Double-click `LookAhead Steering Controller.cer` → **Install Certificate** → Select **Local Machine** → Choose **Trusted Root Certification Authorities** (*Autorità di certificazione radice affidabili*).
* **PowerShell (Admin):**
  ```powershell
  Import-Certificate -FilePath ".\LookAhead Steering Controller.cer" -CertStoreLocation Cert:\LocalMachine\Root
  ```

---

## 📜 Intellectual Property, Copyright & AI Opt-Out

Copyright © 2026 ilborga70. All rights reserved.

LookAhead Steering Controller is an original utility developed and owned by ilborga70.

* 🚫 **No Unauthorized Redistribution:** You may not re-upload, host, or redistribute the binary executable files (`.exe`), plugins (`.dll`, `.asi`), or codebase on any other website, forum, or repository without prior written consent from ilborga70.
* 🏷️ **Attribution & Derivative Concept:** If you develop, publish, or share a similar utility or derivative project inspired by or built upon the methodologies introduced by LookAhead Steering Controller (such as high-frequency 60Hz UDP telemetry bridging or linear calibration matrices), you must explicitly give clear credit and attribute the original concept and work to ilborga70 with a direct link back to this official repository.
* 🤖 **AI Opt-Out & Mining Prohibition:** Text and data mining, scraping, decompilation, and training of Artificial Intelligence (AI) or Machine Learning (ML) models using any part of this project, executable, or codebase are strictly prohibited without prior written consent from the author.
* 📦 **Mod Packaging:** Modpack creators and community developers must link directly to this official repository rather than bundling the software directly.
* 💼 **Non-Commercial Use Only:** This software is provided free for personal, non-commercial use. Commercial monetization or bundling is strictly prohibited.
* 🛡️ **Disclaimer:** Provided "as is" without warranty of any kind.

👨‍💻 **Created by ilborga70** • [Pro-Sim Utilities Hub](https://ilborga70.github.io/Pro-Sim-Utilities-Hub)
