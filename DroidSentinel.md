# 📚 *DroidSentinel Documentation**

## 🔥 **Overview**

**DroidSentinel** is an open-source, static vulnerability scanner designed for Android APK files. It identifies security issues, hardcoded secrets, and potential privacy risks in APKs. The tool provides comprehensive reports with detailed risk scoring, helping security professionals prioritize vulnerabilities.

---

## 🚀 **Installation**

### ✅ **Prerequisites**

- Python 3.6 or higher
    
- `apktool` (automatically installed on Linux/macOS if missing)
    

### 🛠️ **Installation Methods**

#### Option 1: Using pip

```bash
pip install droidsentinel
```

#### Option 2: From source

```bash
git clone https://github.com/CyberNinja/DroidSentinel.git
cd DroidSentinel
pip install -r requirements.txt
```

---

## 💻 **Usage**

### 🔎 **Basic Scan**

```bash
python droidsentinel.py path/to/your/app.apk
```

If installed via pip:

```bash
droidsentinel path/to/your/app.apk
```

### 🔧 **Command-line Options**

- `-o` or `--output`: Save the results to a JSON or text file
    
- `-v` or `--verbose`: Enable detailed output
    
- `--no-color`: Disable colored console output
    
- `--apktool`: Use a custom path for apktool
    

---

## 🔍 **What It Detects**

### 🔑 **API Keys & Secrets**

- Google, Facebook, Twitter API keys
    
- Authentication tokens (Bearer, JWT, Basic)
    
- Database credentials
    
- Hardcoded passwords and secret keys
    

### 📱 **Exported Components**

- Insecure activities accessible by other apps
    
- Public services started by third parties
    
- Broadcast receivers exposed to the system
    
- Public content providers
    

### 🌐 **WebView Vulnerabilities**

- Insecure JavaScript-enabled WebView
    
- File access enabled in WebView
    
- SSL error handling bypasses
    
- JavaScript interfaces vulnerable to injection
    

### ⚠️ **Other Security Issues**

- Insecure file permissions
    
- Improper SSL/TLS implementations
    
- Insecure cryptographic methods
    
- Dangerous permissions usage
    

---

## 📊 **Risk Scoring**

DroidSentinel assigns a **risk score (0-100)** based on multiple security factors, including:

- **Hardcoded Secrets**: Sensitivity and frequency of exposed credentials
    
- **Exported Components**: Insecure activities, services, and receivers
    
- **WebView Configuration**: Risky JavaScript interfaces and mixed-content vulnerabilities
    
- **App Permissions & Configurations**: Use of excessive or dangerous permissions
    

### 🏆 **Risk Score Breakdown**

|**Score Range**|**Risk Level**|🚨 Impact Level|
|---|---|---|
|**75 - 100**|🔥 Critical|Immediate action required|
|**50 - 74**|⚠️ High|Major security concerns|
|**25 - 49**|⚡ Medium|Potential risks|
|**0 - 24**|✅ Low|Minimal risk|

---

## 📊 **Sample Output**

```bash
APK SECURITY ANALYSIS RESULTS
================================================================================

Overall Risk Score: 42/100
Risk Level: Medium

--------------------------------------------------------------------------------
SCAN SUMMARY
--------------------------------------------------------------------------------
  APK File: example.apk
  Scan Date: 2025-03-07 14:30:22
  Total Issues Found: 12
  High Severity Issues: 3
  Medium Severity Issues: 5
  Low Severity Issues: 4

--------------------------------------------------------------------------------
POTENTIAL SECRETS/API KEYS FOUND
--------------------------------------------------------------------------------
[1] API Key found in:
  File: assets/config.json:15
  Value: AIzaSyD8XUgGg3zV7bo1GgL2k2nF9H7x8uKC4Rk
  Context: "apiKey": "AIzaSyD8XUgGg3zV7bo1GgL2k2nF9H7x8uKC4Rk", "authDomain": "example-app.firebaseapp.com"
```

---

## 🤝 **Contributing**

We welcome contributions!

### 🛠️ **How to contribute:**

1. Fork the repository
    
2. Create a new branch (`git checkout -b feature/new-feature`)
    
3. Make your changes
    
4. Commit the changes (`git commit -m "Add new feature"`)
    
5. Push the changes (`git push origin feature/new-feature`)
    
6. Open a Pull Request
    

---

## 🔮 **Upcoming Features**

✨ **Planned Enhancements:**

1. **Native Library Analysis:** Detect hardcoded secrets in native C/C++ `.so` files
    
2. **React Native Support:** Improved analysis for React Native libraries
    
3. **Firebase Vulnerability Detection:** Automatic detection of Firebase misconfigurations
    
4. **Custom Rule Creation:** Define and share custom scanning rules
    
5. **Deep Code Flow Analysis:** Improved tracking of data flow for complex vulnerabilities
    

---

## ⚠️ **Disclaimer**

**DroidSentinel is designed for security professionals.** It assists with vulnerability detection but does not replace:

- Thorough manual code review
    
- Dynamic analysis and pentesting
    
- Proper security design practices
    

**Use responsibly:** Always obtain proper authorization before scanning apps you do not own. The authors assume no liability for misuse.

---

## ❤️ **Acknowledgements**

- **[apktool](https://ibotpeaches.github.io/Apktool/)** for APK decompilation support
    
- Thanks to the mobile security community for defining best practices
    

---

## 🛡️ **License**

DroidSentinel is released under the **MIT License**.  
✅ Free to use and modify with attribution.

---

💡 **Made with ❤️ by [CyberNinja](https://github.com/CyberNinja)**

---

✅ Let me know if you need any changes, additional sections, or web formatting details! 🚀