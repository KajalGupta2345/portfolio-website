# 🔑 SSH in GitHub

## Definition

SSH (Secure Shell) ek secure authentication method hai jo local machine ko GitHub se connect karta hai. SSH key pair ka use karke users repositories ko access, push aur pull kar sakte hain bina har baar username aur password enter kiye.

---

## Use

* Secure authentication ke liye
* Git push aur pull operations ke liye
* Password-less login ke liye
* GitHub repositories manage karne ke liye

---

## Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

### Example

```bash
ssh-keygen -t ed25519 -C "kajal@example.com"
```

---

## Start SSH Agent

```bash
eval "$(ssh-agent -s)"
```

---

## Add SSH Key

```bash
ssh-add ~/.ssh/id_ed25519
```

---

## View Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the generated public key and add it to GitHub.

---

## Add SSH Key to GitHub

1. Open GitHub Settings.
2. Click **SSH and GPG Keys**.
3. Click **New SSH Key**.
4. Enter a title.
5. Paste the public key.
6. Click **Add SSH Key**.

---

## Test SSH Connection

```bash
ssh -T git@github.com
```

### Output

```text
Hi username! You've successfully authenticated.
```

---

## Check Current Remote URL

```bash
git remote -v
```

---

## Change HTTPS to SSH

### Syntax

```bash
git remote set-url origin git@github.com:username/repository.git
```

### Example

```bash
git remote set-url origin git@github.com:KajalGupta2345/FoodieHub-.git
```

---

## Verify SSH Remote

```bash
git remote -v
```

### Output

```text
origin  git@github.com:username/repository.git
```

---

# 👥 Multiple GitHub Accounts on One System Using SSH

## Definition

SSH ki help se ek hi system par multiple GitHub accounts use kiye ja sakte hain. Har GitHub account ke liye alag SSH key generate ki jati hai aur SSH config file ke through unhe manage kiya jata hai.

---

## Use

* Personal aur Work GitHub account ek saath use karna
* Different repositories ko different accounts se manage karna
* Account switching ki zarurat na padna

---

## Generate SSH Keys for Multiple Accounts

### Personal Account

```bash
ssh-keygen -t ed25519 -C "personal@gmail.com" -f ~/.ssh/id_ed25519_personal
```

### Work Account

```bash
ssh-keygen -t ed25519 -C "work@company.com" -f ~/.ssh/id_ed25519_work
```

---

## Add Keys to SSH Agent

```bash
ssh-add ~/.ssh/id_ed25519_personal
ssh-add ~/.ssh/id_ed25519_work
```

---

## Create SSH Config File

File Location:

```text
~/.ssh/config
```

### Configuration

```text
Host github-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_personal

Host github-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_work
```

---

## Test Connections

### Personal Account

```bash
ssh -T git@github-personal
```

### Work Account

```bash
ssh -T git@github-work
```

---

## Clone Repository Using Specific Account

### Personal Account

```bash
git clone git@github-personal:username/repository.git
```

### Work Account

```bash
git clone git@github-work:company/repository.git
```

---

## Verify Config

```bash
ssh -T git@github-personal
ssh -T git@github-work
```

### Output

```text
Hi PersonalUser! You've successfully authenticated.
```

```text
Hi WorkUser! You've successfully authenticated.
```
