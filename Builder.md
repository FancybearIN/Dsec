# 📚 **Android Pentesting Setup – Documentation**

---

## 🔥 **Overview**

The **Android Pentesting Setup** script automates the installation of essential tools and dependencies required for Android application security testing. It supports **Windows**, **Debian-based Linux**, and **Arch-based Linux** distributions.

### 🛠️ **Key Features**

- Automatic installation of:
    
    - **Python & pip**
        
    - **ADB (Android Debug Bridge)**
        
    - **Frida & Frida-server** for dynamic analysis
        
    - **Objection** for runtime security testing
        
    - **Android Studio**
        
    - Required OS libraries
        
- Automated **Frida server** setup and deployment
    
- SELinux disabling for permissive mode
    
- Frida gadget pushing for instrumentation
    
- Burp Suite CA certificate installation for traffic interception
    
- APK package auto-detection and Frida injection
    
- SSL pinning bypass execution
    

---

## 🚀 **Installation**

### ✅ **Prerequisites**

- **Python 3.x** installed
    
- **ADB & Android Studio** (auto-installed if missing)
    
- Internet connection for downloading dependencies
    

### ⚙️ **Supported Platforms**

- **Windows**
    
- **Debian-based Linux** (Ubuntu, Kali, Parrot, etc.)
    
- **Arch-based Linux** (Manjaro, Garuda, etc.)
    

---

## 💻 **Usage**

### 🔥 **Running the Script**

1. **Clone the repository or download the script**
    

```bash
git clone https://github.com/CyberNinja/Android-Pentesting-Setup.git
cd Android-Pentesting-Setup
```

2. **Ensure `anoy.sh` exists** (for Linux users):
    

- This script handles Linux dependency installation.
    
- Make sure `anoy.sh` is in the same directory as the main script.
    

3. **Run the script**
    

```bash
python3 android_pentest_setup.py
```

✅ The script automatically detects your OS and installs the necessary tools.

---

## ⚙️ **Installation Process**

### 🐧 **Linux Installation**

For **Debian** or **Arch-based** systems:

- The script detects the OS (`Debian` or `Arch`).
    
- It runs the `anoy.sh` script with `sudo` to install dependencies.
    
- If `anoy.sh` is missing, it shows an error message.
    

### 🪟 **Windows Installation**

For **Windows**:

- Uses **winget** to install:
    
    - Python
        
    - ADB
        
    - Android Studio (optional)
        
- Installs `frida-tools` and `objection` using `pip`
    

---

## 🔎 **Post-Installation Steps**

### 1️⃣ **Verify Android Emulator Running**

The script asks if you have an Android emulator running:

```bash
Do you have an Android emulator running? (yes/no):
```

If not, start an emulator before proceeding.

---

### 2️⃣ **Architecture Detection**

The script detects the Android device architecture:

```bash
adb shell getprop ro.product.cpu.abi
```

✔️ Example Output:  
`arm64-v8a` or `x86_64`

---

### 3️⃣ **Frida Server Setup**

The script:

- Creates a `frida/` directory
    
- Downloads the **Frida server** binary based on the device architecture
    
- Pushes the server to `/data/local/tmp/`
    
- Sets appropriate permissions
    

✅ Example Commands:

```bash
adb push frida-server-16.6.6-android-arm64 /data/local/tmp/
adb shell chmod 777 /data/local/tmp/frida-server-16.6.6-android-arm64
```

---

### 4️⃣ **Frida Gadget Pushing**

The script automatically pushes the **Frida gadget** (`.so` file) to the device:

```bash
adb push frida-gadget-16.6.6-android-arm64.so /data/local/tmp/gadget.so
adb shell chmod 777 /data/local/tmp/gadget.so
```

---

### 5️⃣ **Burp Suite Certificate Installation**

The script pushes the **Burp Suite CA certificate** to the device:

```bash
adb push burpca-cert-der.crt /data/local/tmp/cert-der.crt
```

💡 This allows **SSL interception** during testing.

---

### 6️⃣ **SSL Pinning Bypass Execution**

- Automatically detects the APK package name using:
    

```bash
frida-ps -Uai | awk 'NR==2 {print $2}'
```

- If the package name isn't detected, you can manually enter it.
    

✔️ Runs the Frida bypass command:

```bash
frida -U -f com.example.app -l ./ssl_pinning.js
```

---

## 📊 **Script Output Example**

```bash
Android Pentesting Setup by CyberNinja
Detected OS: Debian
This script will install the following dependencies:
- Python & pip
- ADB (Android Debug Bridge)
- Frida (for dynamic analysis)
- Objection (for runtime security testing)
- Android Studio
- Required libraries for your OS

Do you want to proceed with the installation? (yes/no): yes

Proceeding with installation on Debian...
Running anoy.sh with sudo...
Installation successful.

Do you have an Android emulator running? (yes/no): yes

Android CPU Architecture: arm64-v8a
Ensuring ADB root access...
SELinux set to Permissive mode

Downloading Frida server...
Pushing Frida server and gadget...
Installing Burp Suite CA certificate...

Auto-detected APK: com.target.app
Running Frida bypass command:
frida -U -f com.target.app -l ./ssl_pinning.js

✅ Android pentesting setup completed successfully!
```

---

## 🚀 **Customization**

### 🔧 **Modify Frida Server Version**

To use a different Frida version, update:

```python
FRIDA_VERSION = "16.6.6"  # Change to desired version
```

### 🔥 **Manual APK Name**

If automatic APK detection fails, enter the package name manually:

```bash
Enter the APK package name to inject Frida: com.example.app
```

---

## 🤝 **Contributing**

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

1. **Custom Android SDK Installation**: Support for older versions
    
2. **Dockerized Setup**: Portable containerized environment
    
3. **Interactive Frida Scripts**: Execute Frida commands interactively
    
4. **Advanced Objection Commands**: Add more Objection runtime hooks
    

---

## ⚠️ **Disclaimer**

**This script is intended for authorized security testing purposes only.**

- **Use with proper authorization**: Scanning apps without permission is illegal.
    
- The authors assume no responsibility for misuse.
    

---

## 🛡️ **License**

**MIT License**  
✅ Free to use, modify, and distribute with attribution.

---

💡 **Made with ❤️ by CyberNinja**

---

✅ Let me know if you need modifications, styling details, or further documentation sections! 🚀