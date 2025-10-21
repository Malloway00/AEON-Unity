━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📦 AEON UNITY 6 — LAUNCH STRUCTURE (UPDATED)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 🧠 CORE AI SYSTEM
────────────────────────────
🔸 **OpenRouterChat.cs**
- Online/offline toggleable GPT-style input
- Detects `>commands`, structured prompts, and mnemonic patterns
- Spinner animation for LLM load + Thinking
- Supports `>load`, `>save`, `>image`, `>debugdump`, `>academic`, etc.
- Detects fallback state if local LLM fails

🔸 **StartupPrompt.cs**
- Banner prompt & pre-session directive loader
- Serialized `StartupPrompt.asset` object

🔸 **ChatBar.cs**
- Handles enter key + Shift+Enter multiline support
- Dynamic input sizing + drag-safe scrolling

🔸 **ChatLogManager.cs**
- Saves/reloads chat logs (Fiction, Academic, Simlog)
- Platform-safe file access
- Supports `LoadByKeyword()` + `LoadMostRecent()`

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 🧠 LOCAL LLM SUBSYSTEM
────────────────────────────
🔸 **ChatSettingsPanel.cs (LLM Section)**
- Auto-detects single .gguf model in StreamingAssets/LLM/Models
- Toggle Local LLM: starts koboldcpp backend 
- VRAM detection with fallback methods
- Spinner animation while verifying server alive
- Fallback to OpenRouter if LLM fails to respond
- `RefreshLLMModel()` button checks for new .gguf dropped

🔸 **LocalLLMRouter.cs**
- Sends requests to `localhost:5002`
- Contextual prompt building with AEON modules
- Validates backend health before usage

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 🎨 IMAGE GENERATION (LOCAL SD)
────────────────────────────
🔸 **AeonImageRouter.cs**
- Takes prompt → enriches via LLM → sends to SD backend via `/txt2img`
- Decodes multi-image grid from base64

🔸 **ImageGenPreview.cs**
- Displays up to 4 thumbnails + full preview overlay
- `SaveImage(index)`, `SaveAllImages()` support
- Right-click save functionality

🔸 **AeonSaveManager.cs**
- Saves prompt + PNG to: `Documents/AEON Logs/{yyyyMMdd}/images/`
- Prompt sanitization + timestamp-based uniqueness

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 🧩 SYMBOLIC ROUTING
────────────────────────────
🔸 **SymbolicRouter.cs**
- Intercepts input to inject matching modules by drift type or pressure
- Falls back to intro prompt fragments if nothing matches
- Full symbolic routing available to all users

🔸 **SymbolicTagDatabase.cs / SymbolicTagProfile.cs**
- Tag-to-module matchmaker using `AEON_TagIndex.json`
- Profile contains driftTypes, fallbackTriggers, injection cues

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## ⚙ SETTINGS + CONFIG
────────────────────────────
🔸 **ChatSettingsPanel.cs**
- Unified settings for API key, OpenRouter model, Stable Diffusion, LLM model
- Manages SD subprocess and koboldcpp launch
- All subprocesses safely terminated if toggled off
- Professional VRAM detection and warnings

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 🛠 DEBUGGING & ERROR HANDLING
────────────────────────────
🔸 **DebugDumpManager.cs**
- Captures Unity + subprocess stdout + SD stderr
- `>debugdump` writes to: `Documents/AEON Logs/{yyyyMMdd}/debug/debug_dump_{HHmmss}.txt`

🔸 **OfflineInstallFailoverDialog.cs**
- Professional error dialogs for setup failures
- One-click debug log saving with context
- Manual opening for troubleshooting
- User-friendly error explanations

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 🎨 PROFESSIONAL UI
────────────────────────────
🔸 **SimpleSplashScreen.cs**
- Professional AEON branding with golden seal logo
- "Built to Remember" tagline
- Loading progress with smooth transitions
- Developer credit and version display

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 📁 FOLDER STRUCTURE
────────────────────────────
```
Assets/
├── Scripts/
│   └── AEON/
│       ├── ChatLog/
│       ├── Debugging/
│       ├── ImageGeneration/
│       └── UI/
├── StreamingAssets/
│   ├── AEON/ (17 linguistic modules)
│   ├── StableDiffuseMinimal/
│   ├── Python/ (bundled with pynvml)
│   ├── LLM/
│   │   ├── Backend/ ← koboldcpp.exe
│   │   └── Models/  ← Single .gguf auto-detected
│   └── get_vram.py
├── Settings/
│   └── StartupPrompt.asset

Documents/
└── AEON Logs/
    ├── {yyyyMMdd}/logs/
    ├── {yyyyMMdd}/images/
    └── {yyyyMMdd}/debug/
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 📌 RELEASE NOTES & DEPENDENCIES
────────────────────────────
- Python 3.10+ bundled for SD with pynvml for VRAM detection
- `uvicorn`, `torch`, `accelerate`, `diffusers` preinstalled in `venv/`
- `auto_setup_unix.sh` auto-installs LLM/SD backend for Mac/Linux
- Single .gguf model auto-detection (user swaps manually)
- Cross-platform file paths and subprocess management

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## ✅ LAUNCH-READY CONFIRMATION
────────────────────────────
✔ All critical systems present and tested
✔ Professional splash screen with branding
✔ All subprocess handling is thread-safe + logged
✔ Comprehensive error handling with user-friendly dialogs
✔ Fallbacks in place for LLM + SD failure
✔ Save paths platform-compliant
✔ Local backends both working: SD (5001) + LLM (5002)
✔ Multi-image support with grid preview
✔ VRAM detection across GPU types
✔ All 17 linguistic modules accessible

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 🚀 AEON LAUNCH PLAN (SIMPLIFIED)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

### 📅 **Timeline**
🔸 **Ready Now** - All systems complete and tested
🔸 **Package Builds** - Export Windows/Mac/Linux versions  
🔸 **Launch** - Set up itch.io store page and go live

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 💵 PRICING MODEL (ETHICAL & SIMPLE)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

### 🟢 **AEON COMPLETE — $30 (One-time)**
**All features included:**
- Fiction & academic modes
- Local LLM + cloud AI support  
- Stable Diffusion image generation
- Full symbolic routing + mnemonic collapse
- All 17 linguistic simulation modules
- Export tools & academic formatting
- Scan tools & recursive analysis
- Complete AEON experience

### 🏛 **Institutional Support — $10/seat/month**
**Same software + professional services:**
- Technical support contracts
- Training materials & curriculum guides
- Bulk deployment assistance
- Integration with campus systems
- Regular update guarantees

### 🟤 **Indigenous & Tribal Communities — FREE**
**Complete access with community support:**
- Full AEON license at no cost
- Priority feature requests
- Dedicated language recovery tools
- Community contribution opportunities
- Cultural preservation partnership

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## 🎯 **CORE VALUES & PHILOSOPHY**
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- **No artificial restrictions** - Full software for fair price
- **Cultural preservation** - Language recovery as human right  
- **Ethical pricing** - Value-based, not extraction-based
- **Academic accessibility** - Research tools shouldn't be gatekept
- **Technical excellence** - Professional quality throughout

**Result: AEON as it should be - powerful, accessible, and ethically priced.** 🎯
