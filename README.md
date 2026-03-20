### 1. High-End Emulators → False IMEI + GPS Trust

**The Attack:**
Emulators configured to report specific IMEIs and GPS coordinates,
making fake accounts appear as real physical devices at real locations.

**Defense:**
- IMEI cross-validation — one device, one account. Same IMEI on multiple accounts = instant flag
- Google Play Integrity API — verifies the app is running on a real, certified device
- Hardware fingerprinting — battery behavior, temperature variance, motion sensor
  patterns. Emulators return static or null values for these
- UUID validation — cross-check UUID against IMEI, device model,
  and hardware sensors.

**If AI is Used to Simulate Sensor Data:**
- Difficult to simulate all sensors correctly and consistently at the same time
- Pattern becomes detectable after a few days of data collection
- If multiple accounts share the same device model with identical sensor patterns, that itself is a signal
- Real devices must show: random Wi-Fi transitions, cell tower handoffs,
  packet loss variations, natural battery drain curves

---

### 2. AI-Generated Jitter and Path Simulation

**The Attack:**
AI adds realistic noise to GPS paths and follows real road routes to mimic
legitimate delivery movement, bypassing simple path-based detection.

**Defense:**
- Physics validation — real movement has stop-go behavior, jerk spikes, and
  natural acceleration curves. Simulated paths often fail under this scrutiny
- Time-situation correlation — movement must match real-world context
  (traffic at 9AM, slow zones near schools, etc.)
- Cross-account route analysis — if multiple accounts are following the same
  route with the same speed profile and jitter pattern, that is statistically impossible

---

### 3. Fake GPS Apps

**The Attack:**
Freely available apps (Fake GPS Go, Fly GPS, etc.) allow users to pin their
location anywhere. Requires only developer mode to be enabled.

**Defense:**
- Check if mock location is enabled in developer settings — flag immediately
- If bypassed: root detection + Play Integrity API as fallback layers
- Developer options being enabled on a delivery partner's device is itself a risk signal
- Runtime behavior validation — cross-check GPS against cell tower and Wi-Fi positioning

---

### 4. Desktop Link Spoofing

**The Attack:**
The delivery app is mirrored and controlled from a desktop. Location is fed
through a connected tool, turning the phone into a remotely operated puppet.

**Defense:**
- Detect if USB debugging is active and if the device is connected to a desktop
- Check if screen casting or mirroring is enabled during an active delivery session
- Analyze touch input patterns — desktop-controlled inputs have different
  latency and pressure profiles compared to real finger interactions

---