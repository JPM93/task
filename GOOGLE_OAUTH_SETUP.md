# Google OAuth Client ID Setup for TaskFlow Pro

## 1. Create a Google Cloud Project
- Go to [Google Cloud Console](https://console.cloud.google.com/).
- Create a new project or select an existing one.
- Enable the **Google Drive API** from the API Library.

## 2. Configure OAuth Consent Screen
- Navigate to **APIs & Services > OAuth consent screen**.
- Choose **External** (or Internal if you have a Workspace domain).
- Fill in app name, user support email, and developer contact.
- Add the scope `https://www.googleapis.com/auth/drive.file` (for creating/managing only files this app creates — not your entire Drive).
- Add test users (your own email at minimum).
- **Important:** While the app stays in **Testing** status, only the test users you added can sign in, and access tokens will expire after 7 days, requiring a fresh sign-in each time. For long-term or multi-user use, you'll need to click **Publish App** to move it to **In production** status. Since `drive.file` is a non-sensitive scope, Google's verification process for it is generally quick, but you should still expect to go through it before publishing.

## 3. Create OAuth 2.0 Client ID
- Go to **Credentials** → **Create Credentials** → **OAuth client ID**.
- Application type: **Web application**.
- Name: `TaskFlow Pro`.
- **Authorized JavaScript origins:** add the exact URL(s) where the app will actually run, for example:
  - `http://localhost:8000` (if testing locally)
  - `https://yourdomain.com` (if hosted on a real domain)
  - **Note:** `file://` origins are **not supported** by Google OAuth at all — this isn't a "might not work" situation, it will always fail. You must serve the app over HTTP/HTTPS. For local testing, run a simple server, e.g.:
    ```
    python3 -m http.server 8000
    ```
    Then add `http://localhost:8000` as an authorized origin.
- **Authorized redirect URIs:** not required for this setup, since TaskFlow Pro uses the token-based (implicit) OAuth flow rather than the redirect-based flow.
- Click **Create**. Note down the **Client ID** — you do **not** need the Client Secret, since this is a frontend-only app.

## 4. Using the Client ID
- In TaskFlow Pro, go to **Settings → Google Drive Sync**.
- Paste your **Client ID**.
- Enter a **Drive Folder Name** (e.g., `TaskFlowBackup`).
- Click **Save Drive Config**.

## 5. Important Notes
- One Client ID can be reused across multiple projects — just make sure the **Authorized JavaScript origins** list includes every domain/local URL you actually use it from.
- The app automatically creates a dedicated folder (with the name you specify) in your Google Drive for backups.
- Access tokens are stored in your browser's `localStorage` and are scoped per logged-in TaskFlow Pro user.
- If your app is still in **Testing** mode, tokens expire after 7 days — you'll simply be prompted to sign in again when that happens.

## 6. Testing
- After configuration, click **Backup** to upload a JSON file to the specified Drive folder. A Google sign-in popup should appear the first time.
- Use **Restore** to list existing backups in that folder and import one.
- If nothing happens when clicking Backup/Restore, open your browser's developer console (F12) to check for script-loading or authentication errors — this is the most common point of failure if the origin isn't correctly registered.
