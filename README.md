# IXD 415 Starter Repo

Design for Emerging Technology // Fall 2026

Working through this will set you up on some basic tools and give you the first practice using them. Work through it top to bottom. It might take about 30 minutes the first time.

If something doesn't work, don't worry. Pay attention to the error message you get and we can resolve it together.

---

## What you're installing and why

| Tool | What it is | Why we use it |
|---|---|---|
| **VS Code** | A text editor | The same editor your engineers use. |
| **Git** | Version history | Named snapshots of your work you can always get back to. |
| **GitHub CLI** | A login helper | Makes GitHub stop asking for passwords |
| **A GitHub account** | Where repos live | Also a kind of portfolio |

---

## Step 0. Make a GitHub account

Go to [github.com](https://github.com) and sign up.

**Pick your username carefully.** It becomes a URL that people will see, eg `github.com/yourname`, and you might include it on a resume.

IF you choose to use your KU email and you can also claim the
[Student Developer Pack](https://education.github.com/pack), which is
free and includes a domain name for a year.

---

## Step 1. Install the tools

### On a Mac

Install [VS Code](https://code.visualstudio.com/). Download, drag to
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

Install [VS Code](https://code.visualstudio.com/). Download, run the
installer, accept the defaults.

Install [Git for Windows](https://gitforwindows.org/). Accept the
defaults **except** when it asks about the default editor. Choose
VS Code. This also gives you **Git Bash**, which is the terminal you'll
use this semester.

Install the [GitHub CLI](https://cli.github.com/).

Then open **Git Bash** from the Start menu for everything below.

---

## Step 2. Tell git who you are

Mac & PC use the same commands. Paste this one line at a time into your
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

That last one prevents git from launching a text editor called `vim` that is notoriously confusing and hard to get out of. With it, git opens VS Code
instead.

---

## Step 3. Log in to GitHub

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

## Step 4. Get this repo onto your computer

In your terminal:

```bash
cd ~
mkdir ixd415
cd ixd415
```

You just made a folder and moved into it. `cd` means "change
directory". It's how you walk around your own computer by typing.

Now clone the starter (your instructor will give you the URL):

```bash
git clone https://github.com/mattkirkland/ixd415-starter.git
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

## Step 5. Your first commit

Make a new file inside the `roster` folder, named after yourself in
lowercase with no spaces. For example, `roster/matt.md`. In VS Code you
can right-click the `roster` folder and choose New File.

Put a few lines in it. There is a template in `roster/EXAMPLE.md` to
copy if you want one.

Now open the terminal inside VS Code with Ctrl+` (the key above Tab).
It starts in the right folder already.

```bash
git status
```

Read what it says. Git has noticed your new file and is calling it
untracked, which means it can see the file but is not watching it yet.
Run `git status` often. It is never destructive, and it always tells you
where you are.

```bash
git add roster/yourname.md
```

That is called staging. You have told git this file belongs in the next
snapshot. Run `git status` again and watch the file move to a different
list.

```bash
git commit -m "Add Matt to the roster"
```

That is a commit, a named snapshot. The message is for whoever reads the
history later, which is usually you, a few weeks from now. Say what
changed and why, not "update" or "stuff".

Nothing has left your computer yet. The commit exists only in your local
history. The difference between local and remote is worth holding onto,
because it is what people tend to get muddled about early.

---

## Step 6. Push to the shared repo

Everyone in the class has write access to this repo, and everyone commits
to the same branch, `main`. That is not how most professional teams work,
and we will get to branches and pull requests later. The point for now is
simpler: a repo is a shared thing that many people add to.

First, collect anything that arrived while you were typing:

```bash
git pull
```

Then send yours:

```bash
git push
```

Refresh the repo page on GitHub. Your file is there.

Run `git pull` again in a few minutes and look in the `roster` folder.
Files you did not write will have appeared. Your classmates put them
there, and you now have a copy of their work without asking anyone for it.

### If your push gets rejected

You will probably see this at some point:

```
! [rejected] main -> main (fetch first)
```

It means someone pushed while you were working, so your copy is behind.
Nothing is broken. Run:

```bash
git pull
git push
```

This is also why everyone adds a separate file instead of editing the
same one. Different files means git can combine the work without needing
to ask you anything. When two people change the same lines, git does have
to ask, and that is a merge conflict. We will do one on purpose in class.

---

## Commands you'll use a lot

```bash
git status                  # where am I? what changed? (run constantly)
git add <file>              # stage a change for the next snapshot
git add .                   # stage everything that changed
git commit -m "message"     # take the snapshot
git push                    # send it to GitHub
git pull                    # get everyone else's changes
git log --oneline           # see the history
```

That's the basic set; there are lots more git commands but you shouldn't worry about them until you need them.

---

## What's in this folder

```
ixd415-starter/
├── roster/             one file per student, added in Step 5
├── markdown.md         cheatsheet on markdown
├── .gitignore          files git deliberately ignores
├── .gitattributes      settles Mac/Windows line-ending differences
└── .vscode/            shared editor settings, these are helpful defaults
```

For now, only push changes inside `roster/`.

The files starting with a dot are configuration. They're hidden in
Finder and Explorer, visible in VS Code. But you can open them and read if you want to.

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
This is normal. VS Code will show you both versions side by side. We'll try this together in class.

**"I broke everything and want to start over."**
You probably didn't. Git saves the work you commit and so you've probabyl got a saved version that you can reference. Bring the error message to class before deleting anything. (Or ask claude)
