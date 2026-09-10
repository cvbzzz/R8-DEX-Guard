R8 DEX Guard

An Android application built with Jetpack Compose for code obfuscation and protection of APK / DEX files. It integrates multiple obfuscation strategies through a graphical interface, helping developers strengthen app security before release.

---

✨ Features

Core Obfuscation (Works Independently)

Option Strength Description
Control Flow Flattening ★★★★★ Scrambles control flow structure, greatly increasing reverse-engineering difficulty
Symbol Obfuscation ★★★★★ Renames classes, methods, and fields to remove readability
Logic Obfuscation ★★★★☆ Inserts equivalent logic transformations
Global State Coupling ★★★☆☆ Couples method state to global state, increasing analysis cost

Requires DEX Optimization to Take Effect

· Junk Instructions (during optimization)
· Flattening 2.0 (during optimization)
· Number Obfuscation (during optimization)
· Instruction Substitution (during optimization)

Basic Options

· Strip Debug Info
· Encrypt Resource IDs
· Only Process Classes in Rules
· Skip Interface Classes
· String Encryption
· DEX Optimization

Stealth Protection

· Stealth Protection (merged toggle) ★★★★★
· Insert Fake Branches
· Multi-layer String Encryption

---

🖥️ UI Overview

Top Bar

· Left: Shield icon + title R8 DEX Guard
· Right: ❤️ Sponsor button, opens a sponsor info dialog

File Selection

· Input File: Supports selecting APK or DEX files
  · When an APK is selected, the package name is extracted automatically and filled into Package Filter and Rules
  · When a DEX is selected, DEX mode is enabled
· Output Path: Where the processed file is saved

Parameter Configuration

· Obfuscation Depth: Default 2
· Obfuscation Repeat Count: Default 1
· Package Filter: Only process matching packages
· Rules Text: Class/method matching rules (e.g. com.example.**)
· Dictionary Path: Custom obfuscation dictionary (default /sdcard/dict.txt)
· Mapping Path: Where the mapping file is saved

All paths are persisted via SharedPreferences (dexguard_prefs).

Obfuscation Options

All toggleable options are shown in a checkboxes list, grouped into:

1. Core Obfuscation
2. DEX Optimization Related
3. Basic Options
4. Stealth Protection

Processing Flow

· Displays a progress bar and status text (Ready / Processing / Done)
· Real-time processing log
· On completion, a dialog appears showing success/failure with a message

DEX Mode

When the input is a .dex file:

· Loads the list of classes/methods inside the DEX
· Supports multi-selecting which DEX entries to process
· Shows the currently processed DEX name and method name

---

🏗️ Project Structure

```
com.dexguard.cff
├── ui
│   ├── screens
│   │   └── MainScreen.kt        # Main screen
│   └── theme                    # Theme & colors
├── engine
│   └── ProtectEngine.kt         # Core protection engine (obfuscation / DEX optimization)
```

---

🚀 Getting Started

Requirements

· Android Studio Hedgehog or newer
· Kotlin 1.9+
· Jetpack Compose
· Minimum SDK: according to project config (24+ recommended)
· Storage permission required to read/write APK/DEX files

Build

```bash
git clone <repo-url>
cd R8DexGuard
./gradlew assembleRelease
```

Usage

1. Open the app and grant storage permission
2. Tap "Input File" and select an APK or DEX
3. Configure obfuscation options and parameters as needed
4. Specify the output path
5. Tap "Start Processing" and wait for completion
6. Retrieve the obfuscated file from the output path

---

🔧 Implementation Notes

· State Management: All input state is managed via remember + mutableStateOf
· Preference Persistence: dictPath / mappingPath are automatically written to SharedPreferences through LaunchedEffect
· DEX Mode Detection: inputPath.lowercase().endsWith(".dex")
· Package Extraction: After selecting an APK, the onPackageExtracted callback fills in the package name and rules automatically
· User Feedback: Unified toasts via the onToast callback

---

⚠️ Notes

· Always back up the original APK/DEX before obfuscating
· Some options require DEX Optimization to take effect
· If rules are empty, all classes may be processed — use with caution
· Be patient when processing large files and avoid exiting mid-process

---

❤️ Sponsor

A sponsor entry is available in the top-right corner of the app. Thanks for supporting ongoing maintenance.

---

📄 License

Please fill in according to the actual project (e.g. MIT / Apache-2.0).

QQ群:1055353328