Here’s the complete setup for GitHub SSH authentication on Windows using Git Bash.

---

# Step 1 — Check Existing SSH Keys

Open Git Bash:

```bash id="fqyks8"
ls -al ~/.ssh
```

If you see files like:

```bash id="j40wsx"
id_rsa
id_rsa.pub
id_ed25519
id_ed25519.pub
```

you may already have keys.

If not, create one.

---

# Step 2 — Generate SSH Key

Recommended command:

```bash id="g6s0r0"
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Example:

```bash id="zry6zp"
ssh-keygen -t ed25519 -C "kamal@example.com"
```

Press:

* Enter for default file location
* Enter for empty passphrase (or set one)

You’ll see:

```bash id="azv0mi"
Your identification has been saved in /c/Users/YourName/.ssh/id_ed25519
```

---

# Step 3 — Start SSH Agent

Run:

```bash id="tv2u3j"
eval "$(ssh-agent -s)"
```

Then add key:

```bash id="dcbmk0"
ssh-add ~/.ssh/id_ed25519
```

---

# Step 4 — Copy Public Key

Run:

```bash id="u5m64u"
cat ~/.ssh/id_ed25519.pub
```

Copy the full output.

It looks like:

```bash id="kcv9oi"
ssh-ed25519 AAAAC3NzaC1... your_email@example.com
```

---

# Step 5 — Add SSH Key to GitHub

Open:

[GitHub SSH Keys Settings](https://github.com/settings/keys?utm_source=chatgpt.com)

Then:

* Click **New SSH Key**
* Title:

  * `My Windows Laptop`
* Paste copied key
* Save

---

# Step 6 — Test SSH Connection

Run:

```bash id="5f0w4f"
ssh -T git@github.com
```

First time:

```bash id="jjgukm"
Are you sure you want to continue connecting (yes/no)?
```

Type:

```bash id="t25vpm"
yes
```

Expected success message:

```bash id="8dc29f"
Hi kamal-1012! You've successfully authenticated...
```

---

# Step 7 — Change Repository Remote to SSH

Check current remote:

```bash id="gfjlls"
git remote -v
```

If it shows HTTPS:

```bash id="bd9vc4"
https://github.com/kamal-1012/test.git
```

Change it to SSH:

```bash id="h0d9pk"
git remote set-url origin git@github.com:kamal-1012/test.git
```

Verify:

```bash id="n2t18x"
git remote -v
```

Now it should show:

```bash id="wb08b0"
git@github.com:kamal-1012/test.git
```

---

# Step 8 — Push Code

Now simply run:

```bash id="2fhy64"
git push
```

No password needed anymore.

---

# Useful Commands

## Check remote

```bash id="8xh31e"
git remote -v
```

## Check SSH key loaded

```bash id="1czm73"
ssh-add -l
```

## Test GitHub SSH

```bash id="n4z0zw"
ssh -T git@github.com
```

---

# Common Errors

## “Permission denied (publickey)”

Fix:

```bash id="i1vzqv"
ssh-add ~/.ssh/id_ed25519
```

## Wrong remote URL

Fix:

```bash id="fn3wkg"
git remote set-url origin git@github.com:USERNAME/REPO.git
```

---

# Recommended

Use:

* Git Bash
* SSH authentication
* VS Code + Git integration

Tools:

s* [Git for Windows](https://gitforwindows.org/?utm_source=chatgpt.com)
* [Visual Studio Code](https://code.visualstudio.com/?utm_source=chatgpt.com)
