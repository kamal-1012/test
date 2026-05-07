# 1. `git clone` — Copy a Repository

## What it does

Downloads a project from GitHub (or another Git server) to your computer.

It copies:

* files
* folders
* commit history
* branches

---

## Syntax

```bash id="50f7xp"
git clone <repository-url>
```

Example:

```bash id="0l3v5m"
git clone https://github.com/user/project.git
```

---

## What happens after clone?

Git creates a folder automatically:

```bash id="x8z0fr"
project/
```

Move into it:

```bash id="h5pq4o"
cd project
```

---

## Example Workflow

```bash id="lhx6nd"
git clone https://github.com/user/project.git
cd project
git status
```

---

## Why beginners use it

You clone when:

* contributing to a project
* downloading your own GitHub repo
* working with team projects

---

# 2. `git status` — Check Current Situation

## What it does

Shows:

* changed files
* new files
* staged files
* current branch

Think of it like:

> “What is happening in my Git project right now?”

---

## Command

```bash id="z0n9m9"
git status
```

---

## Common Output

### Untracked File

```bash id="1jn4z9"
Untracked files:
  app.js
```

Meaning:

* Git sees the file
* but is NOT tracking it yet

---

### Modified File

```bash id="r0k7w9"
modified: index.html
```

Meaning:

* file changed
* changes not staged yet

---

### Staged File

```bash id="h1r5bz"
Changes to be committed:
  new file: style.css
```

Meaning:

* ready for commit

---

## Very Important

Use `git status` frequently.

Most beginners use:

```bash id="cb9rrs"
git status
```

after almost every Git command.

---

# 3. `git add` — Prepare Files for Commit

## What it does

Moves changes into the **staging area**.

Git works in 3 steps:

```text
Working Directory → Staging Area → Commit
```

`git add` moves files to staging.

---

# Imagine This

You edited:

* index.html
* style.css

Git sees changes, but commit won't save them until you ADD them.

---

## Add One File

```bash id="wxrmb9"
git add index.html
```

Only stages that file.

---

## Add Multiple Files

```bash id="6jb4xu"
git add index.html style.css
```

---

## Add Everything

```bash id="9qv2c7"
git add .
```

Very common command.

Means:

> “Stage all changes in current folder.”

---

## Important Beginner Concept

### `git add` DOES NOT save permanently

It only prepares files for commit.

Permanent save happens with:

```bash id="o3tnh4"
git commit
```

---

# 4. `git commit` — Save Snapshot

## What it does

Creates a saved version (snapshot) of your project.

Each commit has:

* unique ID
* author
* timestamp
* message

---

## Basic Syntax

```bash id="2s6c55"
git commit -m "Added login page"
```

---

## What `-m` Means

`-m` = message

You describe what changed.

Good messages:

```bash id="3pxp9i"
git commit -m "Fixed navbar bug"
git commit -m "Added signup form"
git commit -m "Updated CSS styles"
```

Bad message:

```bash id="16l5wb"
git commit -m "stuff"
```

---

# Important Concept

Commit only saves STAGED files.

Example:

```bash id="1n0lbw"
git add app.js
git commit -m "Updated app"
```

Only files added using `git add` are committed.

---

# Think of Commit Like a Game Save Point

```text
Edit files → Add → Commit
```

Commit = checkpoint/save point.

You can return to old commits later.

---

# 5. `git push` — Upload to GitHub

## What it does

Uploads your commits from local computer to GitHub.

---

## Basic Syntax

```bash id="u1x2kt"
git push
```

---

## First Push Usually

```bash id="5v5hyj"
git push -u origin main
```

---

# Breaking This Down

## `origin`

Name of remote repository.

Usually GitHub repo.

---

## `main`

Branch name.

---

## `-u`

Sets default upstream branch.

After this, future pushes can simply be:

```bash id="6s0k1g"
git push
```

---

# Full Beginner Flow

```bash id="z2t7h7"
git add .
git commit -m "Added homepage"
git push
```

---

# Important Beginner Understanding

Without `git push`:

* commits stay only on your computer

After `git push`:

* commits appear on GitHub

---

# 6. `git diff` — See Exact Changes

## What it does

Shows line-by-line differences.

Useful before commit.

---

## Command

```bash id="jz3wzj"
git diff
```

---

# Example

Suppose original file:

```html id="8m7m7l"
<h1>Hello</h1>
```

You change to:

```html id="k2k1xh"
<h1>Hello World</h1>
```

`git diff` shows:

```diff id="0m9g31"
- <h1>Hello</h1>
+ <h1>Hello World</h1>
```

---

# Meaning

```diff id="5jzj3e"
- removed line
+ added line
```

---

# Important Thing Beginners Miss

`git diff` only shows unstaged changes.

After:

```bash id="0n08vx"
git add .
```

normal `git diff` becomes empty.

---

# To See Staged Changes

```bash id="6q0h1k"
git diff --staged
```

OR:

```bash id="tx5o4w"
git diff --cached
```

---

# Real Beginner Workflow (Very Important)

```bash id="hqbmzr"
git status
git diff
git add .
git status
git commit -m "Added new feature"
git push
```

---

# Simple Mental Model

```text
git clone   → download project
git status  → check situation
git diff    → see exact changes
git add     → prepare changes
git commit  → save snapshot
git push    → upload to GitHub
```

---

# Visual Flow

```text
GitHub Repo
     ↓
git clone

Edit Files
     ↓
git status
git diff
     ↓
git add .
     ↓
git commit -m "message"
     ↓
git push
     ↓
Updated GitHub Repo
```
