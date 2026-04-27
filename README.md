#  KeyFlow

The Definitive Desktop Experience for YouTube Music.

---

###  How it works
* Uses OAuth service to read your Youtube Liked List and filter out non-music.
* Picks appropriate liked songs depending on context: what you write on the keyboard.
* **Prerequisites:** You must have [Git](https://git-scm.com/) and [uv](https://docs.astral.sh/uv/) installed on your system.

##  Initial Setup

Setting up **KeyFlow** takes a few minutes. All commands below should be run in your **CMD** or terminal.

### 1. Clone the Project
```bash
git clone https://github.com/YOUR_USERNAME/KeyFlow.git
cd KeyFlow
```

### 2. Get your Google OAuth Secret
1.  **Console:** Go to [Google Cloud Console](https://console.cloud.google.com/).
2.  **Project:** Create a new project named `KeyFlow`.
3.  **API:** Search for **"YouTube Data API v3"** and click **Enable**.
4.  **Credentials:** * Go to **Credentials** → **Create Credentials** → **OAuth client ID**.
    * Select **Application type:** `Desktop app`.
    * Name it `KeyFlow` and click **Create**.
5.  **Finalize:** Download the JSON, rename it to `client_secret.json`, and move it to the KeyFlow root folder.

---

### 3. Install & Build
We use `uv` for high-performance dependency management. Run these in the CMD:

```bash
# Setup environment
uv sync

# Test the app (Triggers one-time login)
uv run main.py

# Build standalone executable
uv run pyinstaller KeyFlow.spec