# ACRally-LookAhead-Steering-Controller
LookAhead Steering Controller is a lightweight, standalone suite that converts your steering wheel rotation into toward the inside of a corner, without needing to install or run OpenTrack.

<img width="1376" height="768" alt="1790547821033" src="https://github.com/user-attachments/assets/bdf9f6c3-6b7b-4ef8-9e18-db0d2ad514b3" />


🚀 Quick Installation (First Time Only)
1. Download the mod's .zip archive.
2. Extract ALL the contents of the ZIP directly into the game's root folder:
`...\SteamLibrary\steamapps\common\Assetto Corsa Rally\`
3. Overwrite when prompted by Windows to merge the `acr` folder.

Note: The manual build will add the mod (`LookAhead Steering Controller.exe`) in path (`...\SteamLibrary\steamapps\common\Assetto Corsa Rally\`) and (`dinput8.dll`) (`AssettoCorsaRallyHeadTracking.asi`) in path (`acr\Binaries\Win64\`).

🎮 How to Use
1. In the game folder, run `LookAhead Steering Controller.exe`.
2. Select your device/steering wheel from the drop-down menu.
3. Adjust the desired sensitivity (recommended starting at 5% for natural movement) and click Apply Real-Time.
4. Leave the program open and launch Assetto Corsa Rally from Steam.
5. Get in the car and switch to Cockpit/Helmet View.
6. Set the actual degrees of the car in use in your driving controller, for example, Lancia Delta (720°).
7. Also set the actual degrees of the car in use in the LookAhead Steering Controller program, for example, Lancia Delta (720°).

🛠️ Technical Features
Direct UDP Protocol: Sends data directly to the game engine (zero latency).
No external programs: OpenTrack is not necessary.
Natural Movement Filter: Stabilizes the signal and avoids jerkiness during sudden steering inputs.

🎮 Windows Security & SimRacing: Why exclude the LookAhead Steering Controller? 🏎️💨
Have you noticed this file in the Windows Defender exclusions?
Let’s break down why adding lookahead steering controller.exe is essential for your setup! 👇

🛡️ 1. Preventing False Positives (Unjustified Blocks).
This program is a third-party utility designed to calculate wheel movements and camera angles for racing simulators.
Because it reads hardware data and shares it directly with other software (like OpenTrack), Windows Defender might mistake this behavior for malicious activity (like a keylogger).
Adding it to your exclusions stops Windows from blocking or deleting it by mistake!

⚡ 2. Eliminating Micro-Stuttering & Input Lag.
Windows Antivirus scans files in real-time.
As shown in the software window, this controller transmits data at a very high frequency (60Hz — 60 times per second).
If the antivirus analyzed every single data packet while you were driving, it would cause:

📈 Abnormal CPU spikes
⏱️ Delayed inputs (input lag)
🛑 Micro-stuttering during your races

📂 3. Why the Entire D:\ Drive is Excluded.
You can also see that the whole D:\ folder is listed.
Sim-racers often do this to prevent Microsoft Defender from constantly scanning heavy game files installed on a secondary HDD or SSD.
This significantly improves overall loading times and game fluidity!

🔬 Is this file 100% safe?
Yes! If you are worried about security, the file has been fully analyzed on Jotti's malware scan.
The results show 0/13 scanners reporting malware, meaning top antiviruses like Kaspersky, BitDefender, and Avast found absolutely nothing.

🔗 Check the full safety report here: https://virusscan.jotti.org/it-IT/filescanjob/g84ynyzizw

📜 Credits & Licenses
LookAhead Steering Controller by `ilborga70`
