<img width="1393" height="746" alt="RBR LookAhead Steering Controller v1 2 0 0" src="https://github.com/user-attachments/assets/2d351ee3-cec5-4653-bc41-f6d503d41506" />

<img width="1400" height="954" alt="Why Delivers Cleaner" src="https://github.com/user-attachments/assets/17a0aa01-c6b0-4eaf-98c8-818eee8431b4" />


---

> **Universal Telemetric Camera Bridge for Assetto Corsa Rally (ACRally)**  
> *Developed by ilborga70*

A lightweight, high-frequency (60Hz UDP) telemetry bridge designed to simulate realistic head and camera movement in Assetto Corsa Rally without requiring VR headsets or head-tracking hardware.

## ACRally LookAhead Steering Controller v1.2.0.0

### 🇬🇧 What's New & Fixes
* **Fixed FFB Bumpstop Yaw Inversion (End-Stop Spike Protection):** Resolved an issue on DirectInput steering wheels (e.g., Fanatec CSL bases) where Force Feedback oscillations at full lock caused raw axis spikes (`dwXpos` / `dwRpos`), triggering sudden camera inversion to the opposite side.
* **Raw Input Delta Filter:** Added a frame-to-frame delta threshold in the 60Hz background polling loop to ignore instantaneous full-scale signal jumps caused by bumpstop impacts.
* **Axis Boundary Clamping:** Enforced strict clamping within the configured wheel lock range (`±WheelLock / 2`) and final UDP output values (`Yaw`, `Pitch`, `Roll`).

---

### 🇬🇧 New Features & UI Refresh
* **Complete Interface Redesign (Modern Dark/Light UI):** Full visual overhaul of all controls in a modern flat style featuring Segoe UI typography and refined color palettes for both Light and Dark themes.
* **Advanced Interactive Sliders:** Replaced legacy controls with modern, smooth TrackBar sliders, bidirectionally synchronized in real time with numeric input boxes for pinpoint tuning.
* **Visual LED Status Indicators:** Replaced plain text strings with custom GDI+ circular LEDs (Green/Red/Gray) to monitor DirectInput Wheel connection, OpenTrack process status, and active Simulator detection at a glance.
* **Real-Time Telemetry Monitor:** Added a dedicated visual axis gauge widget for Yaw, Pitch, and Roll to provide live visual feedback of the 60Hz UDP stream.
* **Improved UX & Action Buttons:** Redesigned action buttons (Save, Export, Import, Apply Real-Time) with clean spacing and padding to eliminate any overlapping elements.

### 🚗 Car Database & Simulator Compatibility
* **Expanded Real Car Database:** Updated the list of realistic car steering presets (up to 1080°).
* **Extended Simulator Support ($knownGames):** Added a comprehensive, up-to-date list of all major racing simulators, rally titles, truck/off-road sims, and classic driving games with wheel and head-tracking support (including Assetto Corsa EVO, Le Mans Ultimate, EA Sports WRC, F1 series, BeamNG.drive, iRacing, Automobilista 2, Richard Burns Rally, and many more).

### 🛠️ Fixes & Stability
* **Parser & Encoding Fixes:** Resolved PowerShell parser and UTF-8 character encoding issues (such as the degree symbol °) in localized strings.
* **UI Layout & Spacing Fix:** Adjusted vertical padding and panel heights to prevent sliders from overlapping adjacent labels.
* **Core Logic Preserved:** The underlying DirectInput engine, asynchronous 60Hz UDP background thread, config.json management, and full IT/EN localization/tooltips remain 100% intact for maximum stability and backward compatibility.

---

### 🇬🇧 New Features
* **Pitch Axis Integration:** Added full support for dynamic control of the Pitch axis, allowing you to vertically tilt the camera view based on the steering angle.
* **Dedicated GUI Controls:** Introduced a new Checkbox and NumericUpDown on the right-hand column to enable/disable and finely adjust the intensity of the Pitch Tilt.
* **Extended UDP Telemetry:** The monitoring label at the bottom right now displays the three active axes (Yaw, Pitch, and Roll) in real-time.

### 🛠️ Improvements & Optimizations
* **OpenTrack UDP Protocol:** Updated the 48-byte binary buffer to correctly map Pitch at offset 8..15, alongside Yaw (24..31) and Roll (40..47).
* **Configuration Persistence (`config.json`):** Updated save, load, import, and export functions to include `EnablePitchTilt` and `PitchTiltSens` parameters.
* **Internationalization (i18n):** Added complete translation strings (Italian / English) and related descriptive tooltips for the new controls.

---

## 🛠️ Step-by-Step Setup Guide Without Mod (`dinput8.dll` and `AssettoCorsaRallyHeadTracking.asi`)

> ℹ️ **Notice:** This manual standalone setup guide without mod files will be available as **Soon** as the developers at **SuperNova** include native TrackIR support in an upcoming update.

### 0. Download & Install Prerequisites
- Download and install **OpenTrack**:  
  👉 [OpenTrack Releases (GitHub)](https://github.com/opentrack/opentrack/releases)

---

### 1. Configure LookAhead Steering Controller
1. Extract the `LookAhead Steering Controller` archive and launch `LookAhead Steering Controller.exe` as **Administrator**.
2. **Set Steering Degrees:** Enter the exact steering lock value (degrees of rotation) required by the car in-game into the **LookAhead Steering Controller**.
3. **Match Wheelbase Settings:** Set the exact same degree value directly in your physical wheelbase software (e.g., Fanatec Fanalab, Simucube True Drive, Thrustmaster Control Panel, Moza Pit House).

> 💡 **Important:** Ensure that the steering lock degrees set in the **LookAhead Steering Controller**, in the **in-game car setup**, and in your **physical wheelbase software** are 100% identical for optimal telemetric precision and response.

---

### 2. OpenTrack Universal Output Mapping
Open OpenTrack and set **Input** to `UDP over network` (Port `4242`) and **Output** to `freetrack 2.0 Enhanced`.

#### A. Options → Output Matrix
Configure the mapping matrix so a single profile works universally across both **LHD** and **RHD** vehicles:

<img width="2560" height="1080" alt="New-opentrack-setup" src="https://github.com/user-attachments/assets/1fe6aa41-39e4-4d23-abe0-0bb33232063e" />

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

<img width="700" height="752" alt="jotti" src="https://github.com/user-attachments/assets/914dda32-7ae8-48f0-ad6d-f7c2c24fece6" />

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
