# ⚡ TaskFlow Pro

A self-contained, browser‑based task management application designed for IT teams.  
No backend, no database – everything is stored securely in your browser's localStorage,  
with optional Google Drive backup.  

## ✨ Features

- **Multi‑tenant** – Separate workspaces for each registered user.
- **Tasks with Subtasks** – Break work into smaller steps; each subtask has its own status lifecycle (Pending, In Progress, Completed, Blocked).
- **Rich Text Formatting** – Bold, Italic, Underline, Strikethrough, Code in descriptions.
- **Task Connections** – Link team members and projects to every task.
- **Audit Trail** – Full status change log with timestamps and comments.
- **EOD Report** – Auto‑generate a daily summary (completed vs pending) and copy to clipboard or paste as a Slack code block.
- **Local Storage** – All data persists in localStorage; no server needed.
- **Import / Export** – Backup and restore your entire workspace as JSON.
- **Google Drive Sync** – Manual backup/restore to Google Drive (API keys required).
- **Responsive Sidebar UI** – Works on desktop and mobile.

## 🛠 Tech Stack

- HTML5, CSS3, Vanilla JavaScript (ES6)
- Bootstrap 5 (modals, toasts, layout)
- Font Awesome 6 (icons)
- Google APIs (optional Drive integration)

## 🚀 Getting Started

1. Clone or download `index.html`.
2. Open it in any modern browser.
3. Register a new account (or use existing credentials).
4. Start adding tasks, subtasks, team members, and projects.

> **Note:** Google Drive features require you to replace `YOUR_GOOGLE_API_KEY` and `YOUR_GOOGLE_CLIENT_ID` with your own credentials from the Google Cloud Console.

## 📸 Screenshots

(Add screenshots of dashboard, task modal with subtasks & audit log, EOD report)

## 📄 License

MIT – feel free to use and modify.
