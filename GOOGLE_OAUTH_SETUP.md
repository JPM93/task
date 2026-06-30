# Google OAuth Client ID Setup for TaskFlow Pro

## 1. Create a Google Cloud Project
- Go to [Google Cloud Console](https://console.cloud.google.com/).
- Create a new project or select an existing one.
- Enable the **Google Drive API** from the API Library.

## 2. Configure OAuth Consent Screen
- Navigate to **APIs & Services > OAuth consent screen**.
- Choose **External** (or Internal if you have a Workspace domain).
- Fill in app name, user support email, and developer contact.
- Add the scope `https://www.googleapis.com/auth/drive.file` (for creating/managing only app files).
- Add test users (your own email at minimum) and publish the app.

## 3. Create OAuth 2.0 Client ID
- Go to **Credentials** → **Create Credentials** → **OAuth client ID**.
- Application type: **Web application**.
- Name: `TaskFlow Pro`.
- Authorized JavaScript origins: add the URL where your `index.html` runs.
  - For local file: `http://localhost` (if using a local server) or `file://` may not work. Use a simple HTTP server.
- Click **Create**. Note down the **Client ID** (you won't need the Client Secret for frontend-only apps).

## 4. Using the Client ID
- In TaskFlow Pro, go to **Settings → Google Drive Sync**.
- Paste your **Client ID**.
- Enter a **Drive Folder Name** (e.g., `TaskFlowBackup`).
- Click **Save Drive Config**.

## 5. Important Notes
- One Client ID can be used in multiple projects. Just ensure the JavaScript origins are updated for each domain/local setup.
- The app creates a dedicated folder in your Google Drive for backups.
- Tokens are stored in your browser's localStorage.

## 6. Testing
- After configuration, click **Backup** to upload a JSON file to the specified Drive folder.
- Use **Restore** to list and import backups.
