🚀 Claude Code + Gemini Full Setup (Windows Guide)

This guide helps you set up Claude-Code + Gemini Models together using claude-code and claude-code-router.

🔥 STEP 0 — Confirm Node.js

Open PowerShell and run:

node --version


If your Node.js version is not 18+, install it from:
👉 https://nodejs.org

🔥 STEP 1 — GET GOOGLE API KEY

Open: https://aistudio.google.com

Click → Get API Key

Click → Create API Key

Copy the key (example):

AIzaSy........

🔥 STEP 2 — INSTALL REQUIRED TOOLS

Open PowerShell (Run as Administrator) and run:

npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router

🔥 STEP 3 — CREATE CONFIG FOLDERS

Open PowerShell (normal mode) and run:

mkdir $HOME/.claude-code-router
mkdir $HOME/.claude

🔥 STEP 4 — CREATE CONFIG.JSON (WINDOWS VERSION)

On Windows, cat << EOF doesn’t work, so we’ll use Notepad.

Run:

notepad $HOME/.claude-code-router/config.json


Notepad will open → paste this exact JSON:

{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "$GOOGLE_API_KEY",
      "models": [
        "gemini-2.5-flash",
        "gemini-2.0-flash"
      ],
      "transformer": {
        "use": ["gemini"]
      }
    }
  ],
  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "gemini,gemini-2.5-flash",
    "think": "gemini,gemini-2.5-flash",
    "longContext": "gemini,gemini-2.5-flash",
    "longContextThreshold": 60000
  }
}


✔ Save → Close

🔥 STEP 5 — SET YOUR API KEY (WINDOWS METHOD)

Open PowerShell (Run as Admin) and run:

[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'YOUR_KEY_HERE', 'User')


Replace YOUR_KEY_HERE with your actual Google API Key.

Example:

[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'AIzaSyXXXXX...', 'User')


⚠️ IMPORTANT:
Close PowerShell → open a new PowerShell → check:

echo $env:GOOGLE_API_KEY


If your key shows → ✅ Perfect!

🔥 STEP 6 — VERIFY EVERYTHING

Run:

claude --version
ccr version
echo $env:GOOGLE_API_KEY


If all commands return output → ✔ Setup successful

🔥 STEP 7 — DAILY WORKFLOW

Terminal 1:

ccr start


Wait until you see:

✔ Service started successfully


Terminal 2:

cd your-project-folder
ccr code


OR

eval "$(ccr activate)"
claude

🔥 VERIFICATION TEST

Open Terminal:

ccr code


Then type:

hi


If Claude replies → 🎉 Congratulations! FREE CLAUDE CODE + GEMINI WORKING!
