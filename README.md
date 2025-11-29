⭐ Claude Code + Gemini Free Setup (Windows Edition – Easy Guide)

Follow these steps exactly. Just copy-paste where needed.

🔹 Step 1 — Get Your FREE Google API Key

Go to Google AI Studio

Click Get API Key

Sign in with your Google account

Click Create API Key

Copy your key (looks like):

AIzaSyAaBbCcDd...


You will need it in Step 2.

🔹 Step 2 — Setup (Windows Friendly)

Open PowerShell (Run as Administrator).

1. Install the required tools
npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router

2. Create config folders
mkdir $HOME\.claude-code-router
mkdir $HOME\.claude

3. Create the router configuration file

Copy-paste this entire block into PowerShell:

@"
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
"@ | Set-Content "$HOME\.claude-code-router\config.json"

4. Verify file was created
cat $HOME\.claude-code-router\config.json

🌟 Step 2.5 — Add Your API Key (Windows Only)

Replace YOUR_KEY_HERE with your real key:

[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'YOUR_KEY_HERE', 'User')


Now CLOSE PowerShell completely and reopen it.

Verify it saved:
echo $env:GOOGLE_API_KEY


If it prints your key → you're good ✔

🔹 Step 3 — Verify the Installation

Run these three commands:

claude --version
ccr version
echo $env:GOOGLE_API_KEY


You should see:

✔ Claude Code version
✔ CCR version
✔ Your API key

If all appear → setup is complete.

🔹 Step 4 — Daily Workflow (How to Use It)
Terminal 1 (Start the router first)
ccr start


Wait until you see:

Service started successfully

Terminal 2 (Your coding terminal)

Go to your project:

cd path\to\your\project


Then choose one of these:

Option A:
ccr code

Option B (activate shell tools):
eval "$(ccr activate)"
claude

🔹 Step 5 — Test It Works

In Terminal 2:

ccr code


Then type:

hi


Expected response:

✔ Claude replies with a greeting
✔ Your free Gemini backend is now working perfectly

✅ DONE! Your Windows setup is complete.

Let me know if you want a PDF version, Mac/Linux version, or YouTube-style tutorial script!
