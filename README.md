# IXD 415 — Starter Repo

Design for Emerging Technology · Fall 2026

This is your setup for the semester and your first website. Work through
it top to bottom. It takes about 30 minutes the first time.

If something doesn't work, that is normal and not a sign about you.
Copy the error message and bring it to class — reading errors out loud
is a skill we're going to practice.

---

## What you're installing and why

| Tool | What it is | Why you care |
|---|---|---|
| **VS Code** | A text editor | It's what your engineers use. Same window, same words. |
| **Git** | Version history | Named snapshots of your work you can always get back to. |
| **GitHub CLI** | A login helper | Makes GitHub stop asking for passwords. One command. |
| **A GitHub account** | Where repos live | Also: a portfolio you'll still be using in five years. |

---

## Step 0 — Make a GitHub account

Go to [github.com](https://github.com) and sign up.

**Pick your username carefully.** It becomes a URL that people will see
— `github.com/yourname` — and it's going on your résumé. Use something
you'd say out loud in an interview.

Use your school email and you can also claim the
[Student Developer Pack](https://education.github.com/pack), which is
free and includes a real domain name for a year.

---

## Step 1 — Install the tools

### On a Mac

Install [VS Code](https://code.visualstudio.com/) — download, drag to
Applications, open it.

Then open **Terminal** (Cmd+Space, type "terminal", Enter) and paste:

```bash
xcode-select --install
```

That installs git. Click through the dialog. It takes a few minutes.

Then install the GitHub CLI:

```bash
brew install gh
```

If that says `command not found: brew`, install
[Homebrew](https://brew.sh) first, then run it again.

### On Windows

Install [VS Code](https://code.visualstudio.com/) — download, run the
installer, accept the defaults.

Install [Git for Windows](https://gitforwindows.org/). Accept the
defaults **except** when it asks about the default editor — choose
VS Code. This also gives you **Git Bash**, which is the terminal you'll
use all semester. Not PowerShell. Not Command Prompt. Git Bash.

Install the [GitHub CLI](https://cli.github.com/).

Then open **Git Bash** from the Start menu for everything below.

---

## Step 2 — Tell git who you are

Same commands on both platforms. Paste them one at a time into your
terminal, using your own name and the email on your GitHub account:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Then these three, exactly as written:

```bash
git config --global init.defaultBranch main
git config --global pull.rebase false
git config --global core.editor "code --wait"
```

That last one matters more than it looks. Without it, git will
occasionally drop you into a 1970s text editor called `vim` that you
cannot escape from without knowing a secret. With it, git opens VS Code
instead. You're welcome.

---

## Step 3 — Log in to GitHub

```bash
gh auth login
```

Answer the prompts:

- **GitHub.com**
- **HTTPS**
- **Yes**, authenticate git with your credentials
- **Login with a web browser** — copy the code it shows you, press
  Enter, paste the code in the browser window that opens

Done. You will never be asked for a GitHub password in the terminal
again.

---

## Step 4 — Get this repo onto your computer

In your terminal:

```bash
cd ~
mkdir ixd415
cd ixd415
```

You just made a folder and moved into it. `cd` means "change
directory" — it's how you walk around your own computer by typing.

Now clone the starter (your instructor will give you the URL):

```bash
git clone <REPO-URL-GOES-HERE>
cd ixd415-starter
code .
```

`code .` means "open VS Code, here." The dot means *this folder*.

VS Code will ask if you want to install the recommended extensions.
Say yes.

> **Mac note:** if `code .` doesn't work, open VS Code, press
> `Cmd+Shift+P`, type "shell command", and pick
> *Install 'code' command in PATH*. Then try again.

---

## Step 5 — Your first commit

Open `index.html` in VS Code. Find the line with your name placeholder
and change it to your actual name. Save.

Now, in the terminal (use the one **inside VS Code** — Ctrl+` opens it,
and it's already in the right folder):

```bash
git status
```

Read what it says. Git is telling you it noticed `index.html` changed.
Get in the habit of running `git status` constantly — it is never
destructive and it always tells you where you are.

```bash
git add index.html
```

You just **staged** that file — told git "this change is part of the
next snapshot." Run `git status` again and watch the color change.

```bash
git commit -m "Add my name to the homepage"
```

That's a commit: a named snapshot. The message is for the human who
reads it later, which is usually you, confused, in three weeks. Write
what changed and why, not "update" or "stuff."

```bash
git push
```

Now it's on GitHub. Go look at it in your browser. That file is on the
internet.

---

## Step 6 — Turn on GitHub Pages

On GitHub, in your repo: **Settings → Pages → Source → Deploy from a
branch → main → /(root) → Save**.

Wait about a minute, then visit:

```
https://YOUR-USERNAME.github.io/ixd415-starter/
```

That's your website. Every time you `git push`, it updates.

---

## The seven commands that get you through the semester

```bash
git status                  # where am I? what changed? (run constantly)
git add <file>              # stage a change for the next snapshot
git add .                   # stage everything that changed
git commit -m "message"     # take the snapshot
git push                    # send it to GitHub
git pull                    # get everyone else's changes
git log --oneline           # see the history
```

That's it. That's the whole set for now. There are hundreds of other
git commands and you will not need them this semester.

---

## What's in this folder

```
ixd415-starter/
├── index.html          your homepage — edit this
├── style.css           how it looks — edit this too
├── notes.md            markdown practice; also your class notes
├── .gitignore          files git deliberately ignores
├── .gitattributes      settles Mac/Windows line-ending differences
└── .vscode/            shared editor settings, so we all match
```

The files starting with a dot are configuration. They're hidden in
Finder and Explorer, visible in VS Code. Open them — they're commented,
and reading other people's config is a legitimate way to learn.

---

## When something breaks

**"I typed something and now my terminal won't respond."**
Press `Ctrl+C`. That cancels whatever's running. It's safe.

**"I'm stuck in a weird full-screen text thing."**
That's `vim` or `less`. Press `q`. If that fails, press `Esc`, then
type `:q!` and Enter. Then go back and run the `core.editor` command
from Step 2 so it stops happening.

**"git says something about 'divergent branches' / rejected push."**
Someone else pushed before you. Run `git pull`, then `git push`.

**"There's a merge conflict."**
Good — this is a normal Tuesday, not an emergency. VS Code will show
you both versions side by side. We'll do this together in class.

**"I broke everything and want to start over."**
You almost certainly didn't break it — git makes losing committed work
genuinely hard. Bring the error message to class before deleting
anything.
