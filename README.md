<img src="../images/bangle.png" align="right" width="100" alt="Bangle.js">

# PWA Test - How to Run and Access on Android

## Step 1: Generate Icons (One Time)

1. Open `generate-icons.html` in Chrome
2. Right-click each canvas → "Save Image As"
3. Save as `icon-192.png` and `icon-512.png` in this folder

## Step 2: Start a Local Server

### Option A: Python (if installed)
```powershell
cd c:\Users\angshuman\bangle-watch\pwa-test
python -m http.server 8080
```

### Option B: Node.js (if installed)
```powershell
npx serve -l 8080
```

### Option C: VS Code Live Server
1. Install "Live Server" extension in VS Code
2. Right-click `index.html` → "Open with Live Server"

## Step 3: Find Your Computer's IP Address

Run this in PowerShell:
```powershell
ipconfig | Select-String "IPv4"
```

Look for something like: `192.168.1.XXX`

## Step 4: Access on Android

1. **Connect your phone to the SAME WiFi** as your computer

2. **Open Chrome on Android** and go to:
   ```
   http://192.168.1.XXX:8080
   ```
   (Replace XXX with your actual IP)

3. **You should see the app!**

## Step 5: Install the PWA

### Method 1: Chrome Prompt
- If Chrome shows an "Install" banner, tap it!

### Method 2: Manual Install
1. Tap the **⋮** menu (3 dots) in Chrome
2. Tap **"Add to Home Screen"** or **"Install App"**
3. Confirm the installation

## Step 6: Test Bluetooth

1. Open the installed PWA from your home screen
2. Tap "Connect to Bangle.js"
3. Select your Bangle.js from the Bluetooth picker
4. Watch the accelerometer data flow!

---

## Troubleshooting

### "Site can't be reached"
- Check both devices are on the same WiFi
- Check Windows Firewall isn't blocking port 8080
- Try temporarily disabling firewall

### "Web Bluetooth not supported"
- Only works in Chrome/Edge (not Firefox/Safari)
- Must be Chrome 56+ on Android

### PWA won't install
- Must be served over HTTPS *or* localhost
- Local network IP (192.168.x.x) should work for testing
- Check manifest.json is valid: https://manifest-validator.appspot.com/

### Bluetooth permission denied
- Go to Android Settings → Apps → Chrome → Permissions → Enable Bluetooth

---

## Making it Work Over Internet (Advanced)

For true "always accessible" from anywhere, you'd need:

1. **ngrok** (free tunneling):
   ```
   ngrok http 8080
   ```
   Gives you a public HTTPS URL

2. **Deploy to GitHub Pages** (free hosting):
   - Push to GitHub
   - Enable Pages in repo settings
   - Access at: https://github.com/angshuman-agarwal/banglejs-ble-pwa


