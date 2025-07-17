# Python for Devops
---
To install **Python** on your system, follow the instructions based on your operating system:

---

### 🔵 **For Windows:**

1. **Download Installer:**

   * Visit: [Download Link](https://www.python.org/downloads](https://www.python.org/downloads/windows/))
   * Click on the latest Python version (e.g., Python 3.12.x)

2. **Run Installer:**

   * **Important:** Check the box **“Add Python to PATH”** at the bottom.
   * Click **“Install Now”**

3. **Verify Installation:**
   Open Command Prompt and run:

   ```bash
   python --version
   ```

   or

   ```bash
   py --version
   ```
<img width="506" height="115" alt="image" src="https://github.com/user-attachments/assets/63160aa2-de94-420a-ae3b-c51c5a2f7b36" />

---

### 🟢 **For Ubuntu / Debian (Linux):**
To install Python and make `python` point to Python 3 on Ubuntu, follow these steps:

---

### ✅ Step 1: **Update your system**

```bash
sudo apt update && sudo apt upgrade -y
```

---

### ✅ Step 2: **Install Python 3**

Ubuntu typically comes with Python 3 pre-installed. But just to be sure:

```bash
sudo apt install python3 -y
```

---

### ✅ Step 3: **Install Python 3's package manager (pip)**

```bash
sudo apt install python3-pip -y
```

---

### ✅ Step 4: **Make `python` point to `python3`**

Ubuntu no longer creates a `python` symlink by default. To manually link:

```bash
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 1
```

Now verify:

```bash
python --version
```

You should see output like:

```
Python 3.x.x
```

---

### ✅ Optional: Set default if multiple python versions

```bash
sudo update-alternatives --config python
```

Choose the appropriate Python 3 version if prompted.

---

Let me know if you also want to make `pip` point to `pip3`.


---

### 🟣 **For macOS:**

1. **Use Homebrew (Recommended):**

   * Install Homebrew if not installed:

     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```
   * Install Python:

     ```bash
     brew install python
     ```

2. **Verify Installation:**

   ```bash
   python3 --version
   ```

---

