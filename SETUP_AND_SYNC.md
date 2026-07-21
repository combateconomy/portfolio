# Portfolio — Cross-Computer Setup & Sync Guide

> Purpose: work on the portfolio from ANY computer, always in sync.
> The engine is Git + GitHub. GitHub is the single source of truth in the cloud.
> Each computer PULLS the latest down before working, and PUSHES changes up after.
> Copy this whole file into your Google Drive doc as the master reference.

---

## 0) FILL THESE IN ONCE (your details)
- GitHub username: __________________________
- Portfolio repo URL (HTTPS): https://github.com/__________/__________.git
- Vercel project name: ______________________
- Live portfolio URL: _______________________
- Contabo server IP (other projects only): __________________
- Contabo SSH user: ________________________

---

## 1) THE DAILY CASCADE RESUME PROMPT (paste at the start of every session)
Copy-paste this to Cascade to resume instantly without wasting tokens:

    Let's continue the portfolio course. First read portfolio/PROGRESS.md and
    portfolio/SETUP_AND_SYNC.md, then resume from "NEXT SESSION STARTS HERE".
    Keep the teaching rules: explain before code, 2-3 multiple-choice questions
    to unlock each step, re-explain on wrong answers, and offer a break/end
    option after every 3 questions. Before we start, remind me to `git pull`.

---

## 2) FIRST-TIME SETUP ON A NEW COMPUTER (do once per machine)

### a) Check / install the basics
    git --version        # should print a version (already installed here)
    node --version       # optional, only needed for Vercel CLI later
Install Git (if missing): https://git-scm.com/download/mac  (or `xcode-select --install`)
Install Node.js LTS (optional): https://nodejs.org

### b) Tell Git who you are (once per machine)
    git config --global user.name  "Michael Pereira"
    git config --global user.email "your-github-email@example.com"

### c) Log in to GitHub (easiest: GitHub CLI)
    brew install gh        # if Homebrew is installed; else see cli.github.com
    gh auth login          # choose GitHub.com > HTTPS > login with browser

### d) Clone the portfolio from GitHub (gets the real, connected copy)
    cd ~/CascadeProjects
    git clone <YOUR PORTFOLIO REPO URL>
    cd <repo-folder-name>

> NOTE: On THIS computer the loose files in windsurf-project-5/portfolio are NOT
> connected to GitHub. Prefer the freshly cloned folder above so pull/push work.

---

## 3) THE EVERYDAY SYNC ROUTINE (the important part)

### START of every session — PULL first (get other computer's changes)
    git pull

### END of every session — SAVE and PUSH (send your changes up)
    git add -A
    git commit -m "Describe what changed today"
    git push

### Quick health check anytime
    git status           # what changed / what's staged
    git log --oneline -5 # last 5 saved versions

### The golden rule
- ALWAYS `git pull` BEFORE you start editing.
- ALWAYS `git push` when you finish.
- This is how each computer "pulls down the difference" — GitHub holds the truth.

---

## 4) IF THE TWO COMPUTERS CONFLICT
This happens if you edited the same lines on both machines without pushing/pulling.
    git pull
    # Git marks conflicts in the file between <<<<<<< and >>>>>>> markers.
    # Open the file, keep the correct version, delete the markers.
    git add -A
    git commit -m "Resolve conflict"
    git push
Tip: pushing/pulling often keeps conflicts rare and tiny.

---

## 5) TECH STACK (portfolio)
- HTML — page structure (index.html). DONE: header/nav/main/sections/footer.
- CSS — styling (style.css). NEXT: Step 3.
- JavaScript — small interactivity, added later.
- No frameworks yet (kept simple for learning).
- Version control: Git + GitHub.
- Hosting/deploy: Vercel (auto-deploys from GitHub).

---

## 6) DEPLOY THE PORTFOLIO WITH VERCEL (recommended, free, auto-deploy)
Best method for beginners — no CLI needed:
1. Go to https://vercel.com and log in WITH GitHub.
2. "Add New… > Project" > Import your portfolio GitHub repo.
3. Framework preset: "Other" (it's plain HTML). Click Deploy.
4. Vercel gives you a live URL. Record it in section 0 above.
5. From now on: every `git push` to GitHub = Vercel auto-redeploys. That's it.

Optional CLI (needs Node.js):
    npm i -g vercel
    vercel            # first deploy / link project
    vercel --prod     # deploy to production

---

## 7) CONTABO (your OTHER projects — NOT the portfolio)
Contabo is a VPS (a rented Linux server) where your existing sites live.
Keep it separate from the portfolio. Reference basics:
    ssh <user>@<contabo-ip>        # log into the server
    # deploy method depends on each project (git pull on server, Docker, etc.)
Do NOT mix Contabo with the portfolio flow above. Portfolio = GitHub + Vercel only.

---

## 8) SESSION RULES (teaching contract — do not violate)
- Sessions 30–60 min/day.
- Explain BEFORE writing code; learner must understand first.
- 2–3 multiple-choice questions unlock each step; all correct = advance.
- Wrong answer = re-explain differently, then retry.
- After every 3 questions: offer continue / short break / end for the day.
- Fact-check when challenged; both sides can be wrong.

---

## 9) WHERE PROGRESS LIVES
- portfolio/PROGRESS.md   -> what's learned + "NEXT SESSION STARTS HERE"
- portfolio/SETUP_AND_SYNC.md (this file) -> setup + sync + prompts
Both files are inside the repo, so they sync across computers automatically via Git.
