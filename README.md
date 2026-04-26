#  KeyFlow

KeyFlow: The Definitive Desktop Experience for YouTube Music
Keystroke-driven. Ad-free. Your music, your way, really.


---

###  How it works
* Uses OAuth service to read your Youtube Liked List and filter out non-music.
* Picks appropriate liked songs depending on context: what you write on the keyboard.

🛠️ Initial Setup
The initial setup is a bit tedious, but you only have to do it once. By providing your own credentials, you ensure 100% privacy and unlimited personal API quota.

1. Generate Your Google OAuth Secrets
KeyFlow requires a client_secret.json to communicate with YouTube Music on your behalf.

Visit the Google Cloud Console: console.cloud.google.com

Create a Project: Click the project dropdown in the top left and select "New Project". Name it KeyFlow.

Enable the API: Go to "APIs & Services" > "Library". Search for "YouTube Data API v3" and click Enable.

Configure Consent Screen: (If prompted) Choose "External" and enter your email. You only need to fill out the required fields.

Create Credentials: * Go to "Credentials" → "Create Credentials" → "OAuth client ID".

Select Application type: Desktop app.

Name it KeyFlow and click Create.

Finalize: Click "Download JSON" on the right side of your new ID. Rename this file to client_secret.json and place it in the root folder of the KeyFlow source code.

2. Initialize and Sync the Environment
We use uv for lightning-fast dependency management. This will automatically create a virtual environment and install everything you need.

Bash
# Initialize the project (only if you just cloned it)
uv init

# Sync dependencies and create the .venv
uv sync
3. Verify the Installation
Before building the standalone app, run KeyFlow locally to ensure your client_secret.json is working correctly:

Bash
# This will trigger the one-time browser login flow
uv run main.py
4. Build the Executable
To package KeyFlow into a single, portable file (so you can run it without a terminal), use the provided PyInstaller specification:

Bash
# Build the standalone application
uv run pyinstaller KeyFlow.spec
✨ Success: After the build finishes, your "astonishingly good" version of YouTube Music will be waiting for you in the dist/ folder.

⚠️ A Note on Security
Never share your client_secret.json or your generated token.pickle file in AppData/KeyFlow with anyone. These files are keys to your YouTube account. The KeyFlow source code is set to ignore these files via .gitignore to keep them safe on your local machine.