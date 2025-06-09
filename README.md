# ImageKeylogger

## ⚠️ Critical Warning and Disclaimer
This toolkit is for educational and research purposes only. Creating or distributing keyloggers without explicit consent is:

Illegal in most jurisdictions (violates computer fraud, privacy, and surveillance laws)

Unethical (violates personal privacy and trust)

Punishable by fines and imprisonment in many countries

By using this software, you agree:

You will only test on systems you own

You will never deploy against unsuspecting victims

You take full legal responsibility for any misuse

You understand this violates most platforms' terms of service

This documentation is provided for cybersecurity education to help understand attack vectors and improve defenses.

## 📂 Toolkit Overview
This Python script creates an executable that:

Displays a decoy image when executed

Runs a keylogger in the background

Saves captured keystrokes to a log file

Uses psychological deception (masquerades as an image)

## 🧰 Technical Requirements
Python 3.8+

Required packages:

`pip install pyinstaller keyboard pillow`
Operating System: Windows (macOS/Linux requires modifications)

## 🛠️ Installation & Setup
Create a dedicated directory:

`mkdir KeyloggerIMG && cd KeyloggerIMG`
Save the script as KeyloggerIMG.py

Install dependencies:

`pip install pyinstaller keyboard pillow`

🚀 Usage Instructions
Step 1: Build the Payload
`python image_keylogger.py --image "real_image.jpg" --output "malicious.exe"`
Step 2: Prepare for Distribution
Navigate to the output directory:

bash
cd dist
Rename the executable to match your image:

rename malicious.exe "real_image.jpg.exe"
Verify both files are present:

real_image.jpg.exe (malicious executable)

real_image.jpg (decoy image)

Step 3: Execution Flow (Victim Perspective)
Victim receives both files in same directory

Victim double-clicks real_image.jpg (which is actually real_image.jpg.exe)

System executes payload:

Decoy image opens normally

Keylogger starts in background

Keystrokes saved to syslog_<PID>.dat in same directory

Victim sees only the image, unaware of background activity

Step 4: Accessing Logs
Log files are created in the same directory as the executable

Filename format: syslog_<PROCESS_ID>.dat

Contains timestamped keystroke records

🛡️ Detection and Prevention
How Antivirus Detects This
Signature Detection: Matches against known keylogger patterns

Behavior Analysis: Flags processes that:

Hook keyboard APIs

Show image while running persistently

Create suspicious log files

Heuristic Analysis: Detects PyInstaller packers and obfuscation

Protection Measures
User Education:

Always show file extensions (Windows Explorer Options)

Never open unexpected attachments

Verify file types with Properties > Details

Technical Defenses:

`; Disable executable files from hidden extensions
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]
"HideFileExt"=dword:00000000
Enable Application Whitelisting`

Use endpoint detection and response (EDR) tools

Regular system scans with updated antivirus

Enterprise Protections:

Network traffic analysis for data exfiltration

User behavior analytics (UBA)

Privilege access management

⚖️ Legal and Ethical Considerations
Relevant Laws (United States)
Computer Fraud and Abuse Act (CFAA)

Prohibits unauthorized access to computers

Penalties: Up to 10 years imprisonment, $500k fines

Electronic Communications Privacy Act

Forbids interception of electronic communications

Penalties: Up to 5 years imprisonment

State Laws (e.g., California Penal Code §502)

Additional penalties for computer intrusions

Ethical Testing Framework
Written Consent: Always obtain permission before testing

Scope Definition: Clearly document authorized systems

Data Handling: Immediately destroy collected data after testing

Disclosure: Report findings to system owners

🧪 Safe Testing Environment
Virtual Machine Setup:

bash
# Create isolated environment
virtualbox --createvm "KeyloggerTest" --ostype Windows10_64
virtualbox modifyvm "KeyloggerTest" --natpf1 "guestssh,tcp,,2222,,22"
Safety Protocols:

Disable network connectivity

Use snapshot/revert functionality

Set testing time limits (max 15 minutes)

Never test on production systems

Post-Testing:

Revert VM to clean state

Wipe all logs and artifacts

Document findings for defensive research

📚 Educational Value
This toolkit demonstrates:

Social Engineering Tactics: Exploiting trust in familiar file types

Persistence Techniques: Long-running background processes

Obfuscation Methods: Executable masquerading as media

Defensive Gaps: Why traditional AV sometimes fails

🔚 Conclusion
This documentation has presented a comprehensive view of an image-based keylogger toolkit for educational purposes. Remember:

Ethical cybersecurity professionals:
✅ Build tools to understand attacks
✅ Improve defensive capabilities
✅ Respect privacy and legality
✅ Contribute to safer digital ecosystems

Malicious actors:
❌ Violate privacy laws
❌ Damage trust in technology
❌ Face severe legal consequences
❌ Harm the cybersecurity community

Use this knowledge responsibly to build better defenses, not more effective attacks.
