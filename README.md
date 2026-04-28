# Prototype Hub

A code-based prototyping workspace for product designers. Build and share interactive Back Market prototypes — no coding required, no terminal, no installs.

> Setup takes about 5 minutes and only happens once. After that, you just talk to Claude.

---

## What you need

Two downloads. That's it.

### 1. Claude Code desktop app

Download from [claude.ai/download](https://claude.ai/download) and install it like any Mac app.

---

### 2. GitHub CLI

This lets Claude connect to your GitHub account to publish your hub.

Download the installer from **[cli.github.com](https://cli.github.com)** — click the macOS `.pkg` file, open it, and follow the installer. No Terminal needed.

---

### 3. A GitHub account

If you don't have one, [sign up here](https://github.com/signup) — it's free.

---

## Setup — do this once

### Step 1 — Create your own copy of the hub

**Why:** Claude Code's repo browser only shows repositories on your own GitHub account. By creating your own copy here, it will appear in Claude Code automatically — no URLs or downloads needed.

1. At the top of this page on GitHub, click the green **"Use this template"** button
2. Click **"Create a new repository"**
3. Give it a name like `[your-team]-hub` or `design-prototypes`
4. Leave everything else as default and click **"Create repository"**

You now have your own copy of the hub on your GitHub account.

---

### Step 2 — Open it in Claude Code

1. Open the **Claude Code** desktop app
2. Click the **"+"** button at the bottom of the window
3. Search for the name you just gave your repository and select it

Claude Code connects to your GitHub repo automatically — no downloading or unzipping needed.

---

### Step 3 — Tell Claude to set everything up

Type the following and press Enter:

```
set me up
```

Claude will ask for your name and team name. Answer those two questions — it handles everything else from there.

**At some point during setup, Claude will need to connect to your GitHub account.** It will run a command that shows you:
- A **one-time code** (8 characters, like `XXXX-XXXX`)
- A **URL** to open in your browser

Open the URL, enter the code, and approve the connection. Then come back to Claude Code — it will carry on automatically.

> **If the code or URL appear blank:** Type `gh auth login` into the terminal panel and press Enter. Choose "GitHub.com", then "HTTPS", then "Login with a web browser".

Once it's done, Claude will give you your hub URL. That link is permanent — share it any time.

---

## Daily use

Open Claude Code, open your project folder, and start talking.

**Start a session:**
> *"Open my hub"*

**Create a new prototype:**
> *"Create a new prototype for the payments redesign"*

Share your PRD or brief and Claude will build it out.

**Share your work:**
> *"Deploy"*

Claude pushes your changes to GitHub. Your hub URL updates within seconds — no build step, no waiting.

---

## Your hub URL

Your hub is always live at:
```
https://[your-github-username].github.io/[your-repo-name]/
```

Share this link with anyone — no login required.
