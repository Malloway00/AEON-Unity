# 📦 AEON Unity 6 — Launch Structure (Updated)

---

## 🧠 Core AI System
---

### **OpenRouterChat.cs**
- Online/offline toggleable GPT-style input  
- Detects `>commands`, structured prompts, and mnemonic patterns  
- Spinner animation for LLM load and processing  
- Supports `>load`, `>save`, `>image`, `>debugdump`, `>academic`, etc.  
- Detects fallback state if local LLM fails  

### **StartupPrompt.cs**
- Banner prompt and pre-session directive loader  
- Serialized `StartupPrompt.asset` object  

### **ChatBar.cs**
- Handles Enter key + Shift+Enter multiline support  
- Dynamic input sizing and drag-safe scrolling  

### **ChatLogManager.cs**
- Saves/reloads chat logs (`Fiction`, `Academic`, `Simlog`)  
- Platform-safe file access  
- Supports `LoadByKeyword()` and `LoadMostRecent()`  

---

## 🧠 Local LLM Subsystem
---

### **ChatSettingsPanel.cs (LLM Section)**
- Auto-detects single `.gguf` model in `StreamingAssets/LLM/Models`  
- Toggle Local LLM to start `koboldcpp` backend  
- VRAM detection with fallback methods  
- Spinner animation while verifying server health  
- Automatic fallback to OpenRouter if LLM fails  
- `RefreshLLMModel()` checks for new `.gguf` files  

### **LocalLLMRouter.cs**
- Sends requests to `localhost:5002`  
- Contextual prompt building with AEON modules  
- Validates backend health before usage  

---

## 🎨 Image Generation (Local Stable Diffusion)
---

### **AeonImageRouter.cs**
- Takes prompt → enriches via LLM → sends to SD backend `/txt2img`  
- Decodes multi-image grids from base64  

### **ImageGenPreview.cs**
- Displays up to 4 thumbnails with full preview overlay  
- Supports `SaveImage(index)` and `SaveAllImages()`  
- Right-click save functionality  

### **AeonSaveManager.cs**
- Saves prompt + PNG to: Documents/AEON Logs/{yyyyMMdd}/images/

- Prompt sanitization and timestamp-based uniqueness  

---

## 🧩 Symbolic Routing
---

### **SymbolicRouter.cs**
- Intercepts user input to inject matching modules by drift type or linguistic pressure  
- Falls back to intro prompt fragments if no match  
- Full symbolic routing available to all users  

### **SymbolicTagDatabase.cs / SymbolicTagProfile.cs**
- Tag-to-module matching via `AEON_TagIndex.json`  
- Profiles define `driftTypes`, `fallbackTriggers`, and `injectionCues`  

---

## ⚙ Settings & Configuration
---

### **ChatSettingsPanel.cs**
- Unified settings for API key, OpenRouter model, Stable Diffusion, and LLM  
- Manages SD subprocess and `koboldcpp` launch  
- Safely terminates all subprocesses when toggled off  
- Professional VRAM detection and warnings  

---

## 🛠 Debugging & Error Handling
---

### **DebugDumpManager.cs**
- Captures Unity + subprocess stdout + SD stderr  
- `>debugdump` writes to: Documents/AEON Logs/{yyyyMMdd}/debug/debug_dump_{HHmmss}.txt


### **OfflineInstallFailoverDialog.cs**
- Professional error dialogs for setup failures  
- One-click debug log saving with context  
- Manual opening for troubleshooting  
- User-friendly error explanations  

---

## 🎨 Professional UI
---

### **SimpleSplashScreen.cs**
- AEON branding with golden seal logo  
- “Built to Remember” tagline  
- Smooth loading transitions  
- Developer credit and version display  

---

## 📁 Folder Structure
---

Assets/
├── Scripts/
│ └── AEON/
│ ├── ChatLog/
│ ├── Debugging/
│ ├── ImageGeneration/
│ └── UI/
├── StreamingAssets/
│ ├── AEON/ # 17 linguistic modules
│ ├── StableDiffuseMinimal/
│ ├── Python/ # bundled with pynvml
│ ├── LLM/
│ │ ├── Backend/ # koboldcpp.exe
│ │ └── Models/ # single .gguf auto-detected
│ └── get_vram.py
├── Settings/
│ └── StartupPrompt.asset
Documents/
└── AEON Logs/
├── {yyyyMMdd}/logs/
├── {yyyyMMdd}/images/
└── {yyyyMMdd}/debug/
---

## 📌 Release Notes & Dependencies
---

- Python 3.10+ bundled for SD with `pynvml` for VRAM detection  
- `uvicorn`, `torch`, `accelerate`, `diffusers` preinstalled in virtual environment  
- `auto_setup_unix.sh` installs LLM/SD backend for macOS/Linux  
- Single `.gguf` model auto-detection (user-swappable)  
- Cross-platform file paths and subprocess management  

---

## ✅ Launch-Ready Confirmation
---

| Status | Description |
|:--:|:--|
| ✅ | All critical systems present and tested |
| ✅ | Professional splash screen and branding |
| ✅ | Thread-safe subprocess handling and logging |
| ✅ | Comprehensive error handling |
| ✅ | Fallbacks for both LLM and SD |
| ✅ | Platform-compliant save paths |
| ✅ | Local backends working — SD (5001) + LLM (5002) |
| ✅ | Multi-image grid preview support |
| ✅ | GPU VRAM detection across devices |
| ✅ | Access to all 17 linguistic modules |

---

## 🚀 AEON Launch Plan (Simplified)
---

**Timeline:**
- **Ready Now:** All systems complete and tested  
- **Packaging:** Export Windows, macOS, and Linux builds  
- **Launch:** Publish on Itch.io and release trailer  

---

## 💵 Pricing Model (Ethical & Simple)
---

### 🟢 AEON Complete — $30 (One-time)
**Includes:**
- Fiction and academic simulation modes  
- Local LLM + cloud AI support  
- Stable Diffusion integration  
- Symbolic routing and mnemonic collapse  
- 17 linguistic simulation modules  
- Export tools and academic formatting  

### 🏛 Institutional Support — $10/seat/month
**Includes:**
- All Complete features +  
- Technical support and training materials  
- Bulk deployment assistance  
- Integration with campus systems  
- Update guarantees  

### 🟤 Indigenous & Tribal Communities — Free
**Includes:**
- Full AEON license at no cost  
- Priority feature requests  
- Dedicated language recovery tools  
- Community contribution opportunities  
- Cultural preservation partnership  

---

## 🎯 Core Values & Philosophy
---

- **No artificial restrictions** — Full access for a fair price  
- **Cultural preservation** — Language recovery is a human right  
- **Ethical pricing** — Value-based, not extraction-based  
- **Academic accessibility** — Knowledge should not be gatekept  
- **Technical excellence** — Professional-grade engineering  

> **Result:** AEON as it should be — powerful, accessible, and ethically priced.
