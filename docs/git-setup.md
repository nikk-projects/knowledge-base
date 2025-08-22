## 🚀 Git Setup & Commands

### 1. Configure Git (One-time Setup)
```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"
````

---

### 2. Clone a Repository

```bash
git clone <repository_url>
```

---

#### ⚠️ Fix for GitHub Authentication

GitHub no longer supports password authentication.
Use a **Personal Access Token (PAT)** instead:

```bash
git clone https://<your_token>@github.com/<username>/<repo_name>.git
```

---

### 3. Stage Files

```bash
git add <file1> <file2>   # Add specific files
git add .                 # Add all files
```

---

### 4. Commit Changes

```bash
git commit -m "Your commit message"
```

---

### 5. Push Changes

```bash
git push -u origin main
```

---

### 6. Add a Remote (if not set already)

```bash
git remote add origin https://<your_token>@github.com/<username>/<repo_name>.git
```
