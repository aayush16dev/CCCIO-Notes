

---
# 🕵️ Anonymity & Privacy — Complete Field Guide + Practicals

> **Tags:** #cybersecurity #privacy #anonymity #networking #firefox #tor #vpn
> **Category:** Practical Cybersecurity | Hinglish Notes

---

## 📚 Table of Contents

- [Topic 1 — WebRTC & Firefox Hardening via about:config](#topic-1--webrtc--firefox-hardening-via-aboutconfig)
- [Topic 1.1 — User Agent Spoofing](#topic-11--user-agent-spoofing)
- [Topic 2 — Browser Fingerprinting & Tracking Tools](#topic-2--browser-fingerprinting--tracking-tools)
- [Topic 3 — Key Concepts & Questions](#topic-3--key-concepts--questions)
- [Topic 4 — Private vs Normal Mode: Cookie Comparison](#topic-4--private-vs-normal-mode-cookie-comparison)
- [Topic 5 — DNS Leak Test](#topic-5--dns-leak-test)
- [Topic 6 — Search Engine Comparison: Google vs DuckDuckGo](#topic-6--search-engine-comparison-google-vs-duckduckgo)
- [Topic 7 — Free vs Paid VPN](#topic-7--free-vs-paid-vpn)
- [Topic 8 — Proxy vs VPN](#topic-8--proxy-vs-vpn)
- [Topic 9 — WebRTC Leak Test with VPN](#topic-9--webrtc-leak-test-with-vpn)
- [Topic 10 — Cookie & Tracker Analysis](#topic-10--cookie--tracker-analysis)
- [Topic 11 — Email Anonymity: Gmail vs Temp Mail](#topic-11--email-anonymity-gmail-vs-temp-mail)
- [Topic 12 — Social Media Tracking: Facebook Pixel](#topic-12--social-media-tracking-facebook-pixel)
- [Topic 13 — TOR Browser: Onion Routing & IP Path Analysis](#topic-13--tor-browser-onion-routing--ip-path-analysis)
- [Topic 14 — MAC Address Changer](#topic-14--mac-address-changer)
- [Topic 15 — User-Agent Spoofing (Advanced Practical)](#topic-15--user-agent-spoofing-advanced-practical)
- [Topic 16 — OSINT Reverse Identification & De-anonymisation](#topic-16--osint-reverse-identification--de-anonymisation)
- [Topic 17 — Metadata Removal: Image EXIF Analysis](#topic-17--metadata-removal-image-exif-analysis)
- [Topic 18 — Traffic Analysis (Controlled Lab)](#topic-18--traffic-analysis-controlled-lab)
- [Anonymity Toolkit Reference](#-anonymity-toolkit-reference)

---

## Topic 1 — WebRTC & Firefox Hardening via `about:config`

### 🔍 What is WebRTC?

**WebRTC (Web Real-Time Communication)** ek browser technology hai jo peer-to-peer communication — jaise voice/video calls aur file sharing — **bina external plugins ke** enable karta hai.

> **Critical Privacy Risk:** WebRTC aapka **real IP address leak kar sakta hai** even when you're behind a VPN, kyunki yeh directly system ke network interfaces se connect karta hai.

**WebRTC ke under kya aata hai:**
- Real-time audio/video communication
- Peer-to-peer file transfers
- Live data channels
- No additional plugins required (built into browser)

**Disadvantages of WebRTC:**
- Leaks real user IP (even behind VPN)
- Exposes local network IP addresses
- Enables browser fingerprinting via media device enumeration

---

### 🛠️ How to Disable WebRTC & Harden Firefox

**Step 1 — Verify WebRTC Status**

Visit: [https://whoer.net](https://whoer.net) or [https://browserleaks.com/webrtc](https://browserleaks.com/webrtc)

**Step 2 — Open Advanced Settings**

Firefox address bar mein type karo:
```
about:config
```
"Accept the Risk and Continue" par click karo.

**Step 3 — Apply the Following Settings**

> Use the search bar to find each setting. Double-click to toggle booleans. Agar setting nahi mile → right-click → New → create karein.

---

### ⚙️ Full Firefox Configuration Table

| Setting Name | Value | Purpose |
|---|---|---|
| `media.peerconnection.enabled` | `false` | WebRTC completely disable — IP leak band |
| `media.navigator.enabled` | `false` | Camera/mic auto-access block |
| `privacy.resistFingerprinting` | `true` | Browser generic dikhata hai — screen, timezone, fonts standardize |
| `privacy.firstparty.isolate` | `true` | Cookies per site isolate — cross-site tracking band |
| `privacy.trackingprotection.enabled` | `true` | Firefox built-in tracker blocking activate |
| `privacy.trackingprotection.fingerprinting.enabled` | `true` | Fingerprinting-based tracking scripts block |
| `privacy.trackingprotection.cryptomining.enabled` | `true` | Cryptojacking scripts block (hidden CPU mining) |
| `geo.enabled` | `false` | Geolocation API disable — sites GPS nahi le sakti |
| `network.cookie.cookieBehavior` | `2` | All third-party cookies block |
| `network.cookie.lifetimePolicy` | `2` | Browser band hote hi cookies delete |
| `network.dns.disablePrefetch` | `true` | DNS prefetching disable — pre-visit tracking kam |
| `network.prefetch-next` | `false` | Next pages preload nahi honge |
| `webgl.disabled` | `true` | WebGL disable — GPU-based fingerprinting band |
| `dom.event.clipboardevents.enabled` | `false` | Sites detect nahi kar paayengi copy/paste actions |
| `media.eme.enabled` | `false` | DRM disable (Netflix etc.) — privacy zyada |
| `browser.safebrowsing.phishing.enabled` | `false` | Google Safe Browsing OFF (alternative AV hona chahiye) |
| `browser.safebrowsing.malware.enabled` | `false` | Google Malware check OFF (same caveat) |

> ⚠️ **Note on Safe Browsing:** Only disable if you have alternative security (firewall/antivirus). Otherwise leave enabled.

---

### ✅ Verification

**WebRTC Disabled Check:**
1. Open: [https://browserleaks.com/webrtc](https://browserleaks.com/webrtc)
2. Check for "Local IP Address" and "Public IP Address" fields
3. ✅ Agar koi IP nahi dikh raha — successfully disabled

**Fingerprint Resistance Check:**
1. Visit: [https://coveryourtracks.eff.org/](https://coveryourtracks.eff.org/)
2. Click "Test your browser"
3. Look for: *"Strong protection against fingerprinting"*

**Tor + Proxychains Setup (Reference Commands):**
```bash
service tor start
service tor status
locate proxychains.conf
# nano /etc/proxychains.conf  → edit as needed
proxychains firefox           # start browser through proxychains
```

---

## Topic 1.1 — User Agent Spoofing

### 🤔 What is a User Agent?

> **User Agent** ek **browser ID string** hai — yeh web servers ko batata hai ki aap kaunsa browser, OS aur device use kar rahe ho.

**Example User Agent string:**
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 Chrome/120.0.0.0 Safari/537.36
```

**UA Spoof kyun karte hain?**
- Browser identity ko tracking systems se mask karne ke liye
- Alag OS ya browser jaisa dikhne ke liye

> ⚠️ **Limitation:** UA spoofing browser ID string mask karta hai lekin advanced tracking (fingerprinting, behavioral analysis) nahi rokta.

---

### UA Spoofing vs Fingerprinting

| Feature | UA Spoofing | Fingerprinting |
|---|---|---|
| Kya change hota hai | Browser ID string only | Full device/browser profile |
| Kya hide hota hai | Browser name + OS | Canvas, fonts, resolution, plugins |
| Detect ho sakta hai? | Yes (rendering mismatch) | Yes (still unique) |
| Effectiveness | Low — advanced trackers bypass kar lete hain | Harder to fake |

> UA spoofing changes what you *claim* to be. Fingerprinting detects what you *actually* are.

---

### 🛠️ Method 1 — via `about:config` (Firefox)

1. `about:config` open karo
2. Search: `general.useragent.override`
3. Nahi mile → right-click → New → String
4. Value set karo:
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 Chrome/120.0.0.0 Safari/537.36
```
5. Test karo: Google par search karo "what is my user agent"

### 🛠️ Method 2 — Firefox Extension

Install: [UA Switcher Add-on](https://addons.mozilla.org/en-US/firefox/addon/uaswitcher/)
Toolbar se select karo: Android / iPhone / Windows — ek click mein change.

### 🛠️ Method 3 — Terminal (Kali Linux)

```bash
curl -A "Mozilla/5.0 (iPhone; CPU iPhone OS 15_0 like Mac OS X)" https://httpbin.org/user-agent
```
Server ko fake iPhone User-Agent bhejta hai.

### 🛠️ Method 4 — Burp Suite (Professional)

1. Burp Suite open karo → Proxy ON → Browser proxy set karo
2. Intercept ON → Request capture karo
3. `User-Agent:` header dhundo → custom UA se replace karo → Forward karo

---

## Topic 2 — Browser Fingerprinting & Tracking Tools

### 🔍 What is Browser Fingerprinting?

**Fingerprinting** ek tracking method hai jo multiple browser/device attributes collect karke ek **unique identifier** banata hai — **bina cookies ke**.

**Attributes collected:**
- Screen resolution, color depth
- Installed fonts
- Browser plugins and extensions
- Canvas rendering
- WebGL renderer
- Timezone, language settings
- Hardware concurrency (CPU core count)

> **Key Insight:** Cookies ke unlike, fingerprint **delete nahi ki ja sakti** — yeh hardware aur software properties se derive hoti hai.

---

### Cookie vs Fingerprint

| Property | Cookie | Fingerprint |
|---|---|---|
| Storage | Local (browser) | Derived from device |
| Deletable | ✅ Yes | ❌ No |
| Persistence | Until expiry or cleared | Persistent |
| Requires consent | Yes (legally) | Typically covert |

---

### 🧪 Practical: Normal vs Hardened Browser Fingerprint

**Tools:**

| Tool | URL | Purpose |
|---|---|---|
| AmIUnique | [amiunique.org](https://amiunique.org) | Browser fingerprint uniqueness check |
| BrowserLeaks | [browserleaks.com](https://browserleaks.com) | Comprehensive browser data leak tests |
| Cover Your Tracks | [coveryourtracks.eff.org](https://coveryourtracks.eff.org) | EFF fingerprint & tracker test |

**Part A — Normal Browser:**
1. Fresh browser profile / default settings (no VPN, no extensions)
2. Visit [amiunique.org](https://amiunique.org/fingerprint) → note uniqueness %, WebGL, Canvas, Fonts, Timezone
3. Visit [browserleaks.com](https://browserleaks.com) → check JavaScript, WebRTC, WebGL, Canvas, Audio fingerprint

**Part B — Hardened Browser:**
1. Enable Firefox settings: `privacy.resistFingerprinting = true`, `webgl.disabled = true`, `media.peerconnection.enabled = false`
2. Install: uBlock Origin, Privacy Badger
3. Run same tests again → compare results

---

### 📊 Comparison: Normal vs Hardened

| Parameter | Normal Browser | Hardened Browser |
|---|---|---|
| Fingerprint Uniqueness | High | Low |
| WebGL | Enabled | Disabled |
| Canvas Access | Allowed | Blocked |
| Fonts | Full list | Limited |
| Tracking Risk | High | Reduced |

**Result:** Normal browser easily track ho sakta hai. Hardened browser fingerprint mask/normalize karta hai. Tor Browser sabse standardized fingerprint deta hai.

---

### 🗣️ Viva Q&A — Fingerprinting

**Q: Browser fingerprint kya hota hai?**
Browser fingerprint ek unique digital identity hoti hai jo browser, OS, screen size, fonts, timezone, WebGL, canvas jaise parameters se banti hai. Isse website user ko bina cookies ke bhi track kar sakti hai.

**Q: Cookies aur fingerprinting mein difference?**
Cookies local system mein store hoti hain aur user delete kar sakta hai. Fingerprinting browser/device ki properties se hoti hai aur delete karna mushkil hai. Cookies = stored data; Fingerprinting = device behavior & configuration.

**Q: privacy.resistFingerprinting ka role?**
Yeh Firefox ka feature hai jo browser ki information standardize/spoof karta hai — screen size, timezone, fonts — taaki browser less unique dikhe aur tracking kam ho.

**Q: Tor Browser fingerprint kyun safe hai?**
Tor Browser sab users ko same fingerprint deta hai. Is wajah se individual user ko identify karna mushkil hota hai. *"Tor Browser focuses on uniformity, not uniqueness."*

---

## Topic 3 — Key Concepts & Questions

### 🧠 Definitions

| Term | Definition |
|---|---|
| **Anonymity** | Internet par apni identity hide karna |
| **Real IP** | ISP (Jio, Airtel, BSNL) ka diya hua original IP address |
| **VPN IP** | VPN server ka IP — real IP mask karta hai |
| **DNS Lookup** | Domain name (e.g., google.com) ko IP address mein translate karna |
| **DNS Leak** | DNS queries VPN tunnel bypass karke ISP ke paas jaati hain |
| **DNS Anonymity** | Browsing destinations ISP se hidden rehte hain |
| **Data Profiling** | User behavior collect karke detailed identity profile banana |
| **Proxy** | Intermediary server — browser-level only, no encryption |
| **VPN** | Secure encrypted tunnel for all network traffic |

---

### ❓ Key Questions & Answers

**Q: Anonymity ka misuse kya hai?**
Dark web markets, cybercrime, fraud mein identity hide karte hue illegal activities karna.

**Q: Kya VPN locations 100% accurate hoti hain?**
❌ Nahi. VPN servers approximate ya slightly inaccurate locations show kar sakte hain.

**Q: Kya VPN ke bawajood true IP leak ho sakta hai?**
✅ Haan — WebRTC leaks, DNS leaks, ya browser misconfiguration se.

**Q: Tor Browser privacy-focused OS kaunsa hai?**
**Tails OS** — ek live operating system jo host machine par koi trace nahi chhodta.

**Q: Private/Incognito mode ka purpose?**
Local data (history, cookies) remove karna after session. IP hide nahi karta, ISP tracking nahi rokta.

---

## Topic 4 — Private vs Normal Mode: Cookie Comparison

### 🎯 Concept: Local Tracking

**Objective:** Normal aur Private/Incognito mode mein cookies, history aur local tracking ka comparison karke local tracking ka concept samajhna.

---

### 🧪 Practical Steps

**Part A — Normal Mode:**

1. Browser normal mode mein open karo
2. Shopping/news website visit karo (e.g., amazon.com), 2–3 minutes spend karo
3. Right click → Inspect → **Application** tab → **Storage → Cookies**
4. Website domain select karo — note karo: Name, Value, Domain, Expiry, Tracking IDs
5. Browser close aur reopen karo — same site visit karo

> **Observation:** Website aapko recognize karti hai (preferences / ads same rehte hain)

**Via Browser Settings (Alternative):**
- Chrome: Settings → Privacy & Security → Cookies → See all site data
- Firefox: Settings → Privacy & Security → Cookies and Site Data → Manage Data

**Part B — Incognito/Private Mode:**

1. New Private/Incognito window open karo
2. Same website visit karo, same actions repeat karo
3. Developer Tools → Cookies check karo — cookies sirf temporary hoti hain
4. Window close karo → reopen → website aapko new user treat karegi

---

### 📊 Normal vs Private Mode

| Parameter | Normal Mode | Private Mode |
|---|---|---|
| Cookies | Stored permanently | Temporary (session only) |
| History | Saved | Not saved |
| Login Session | Persist after close | Destroyed on close |
| Local Tracking | Yes | Limited |
| IP exposed to websites | Yes | Yes (same) |
| ISP tracking | Yes | Yes |
| Third-party tracking | Active | Partially reduced |

**Result:** Normal mode mein local tracking possible hai. Private mode sirf local traces remove karta hai — IP, ISP ya fingerprint hide nahi karta.

---

### 🗣️ Viva Q&A — Private Mode

**Q: Private mode ka main purpose?**
Local data privacy. Browser band karte hi history, cookies, cache aur form data delete kar deta hai.

**Q: Kya incognito mode IP hide karta hai?**
❌ Nahi. Incognito mode IP address, ISP ya network identity hide nahi karta.

**Q: Cookies ka role local tracking mein?**
Cookies website ko batati hain: user pehle visit kar chuka hai, login session kaunsa hai, preferences kya hain.

**Q: Private mode vs VPN difference?**

| Private Mode | VPN |
|---|---|
| Local data delete karta hai | IP address hide karta hai |
| History & cookies remove | Network traffic encrypt karta hai |
| ISP tracking nahi rokti | ISP se data hide karta hai |
| Local privacy | Online anonymity |

> *"Private mode local traces hide karta hai, VPN network identity hide karta hai."*

---

## Topic 5 — DNS Leak Test

### 🔍 Concept: DNS Anonymity

**DNS (Domain Name System)** internet ka "phonebook" hai — human-readable domains (google.com) ko IP addresses (142.250.74.46) mein translate karta hai.

> **DNS Leak:** VPN ON hone ke bawajood DNS requests VPN tunnel bypass karke ISP ke DNS server ke paas chali jaati hain — ISP ko pata chal jaata hai kaunsi websites visit ho rahi hain.

---

### 🧪 Practical Steps

**Part A — VPN OFF:**

1. VPN disconnect karo, browser normal mode mein open karo
2. Visit: [dnsleaktest.com](https://www.dnsleaktest.com/)
3. Standard Test click karo → wait karo
4. Note karo: DNS Server IP, Country, ISP/Organization name

> **Observation:** DNS servers aapke real ISP (Airtel, Jio, BSNL) ke dikhte hain — yeh normal hai

**Part B — VPN ON:**

1. VPN connect karo (preferably different country — Netherlands, Singapore)
2. Browser refresh → Extended Test click karo
3. Check karo: DNS Server Country, DNS Provider name

> **Observation:** DNS servers VPN provider ke hone chahiye — ISP ka naam nahi aana chahiye

---

### 📊 DNS Leak Comparison

| Parameter | VPN OFF | VPN ON (Secure) | VPN ON (DNS Leak) |
|---|---|---|---|
| DNS Server Owner | ISP | VPN Provider | ISP (leaked!) |
| DNS Country | India | VPN Country | India |
| Anonymity Level | Low | Improved | Weak |

**DNS Leak Causes:**
- Split tunneling misconfiguration
- OS using fallback DNS
- WebRTC enabled
- VPN disconnect (kill switch OFF)

---

### 🗣️ Viva Q&A — DNS

**Q: DNS leak kya hota hai?**
VPN ON hone ke bawajood DNS requests ISP ke DNS server ke paas chali jaati hain. ISP ko pata chal sakta hai kaunsi websites visit ho rahi hain.

**Q: Standard test aur Extended test mein difference?**
Standard Test: limited DNS servers check. Extended Test: zyada DNS queries bhejkar detailed leakage detection (recommended).

**Q: DNS anonymity ka matlab?**
Websites ke domain names ISP ya third party ko na dikhein — DNS queries sirf VPN/secure DNS provider ko hi jayein.

> *"DNS anonymity ensures that browsing destinations remain hidden from ISP."*

---

## Topic 6 — Search Engine Comparison: Google vs DuckDuckGo

### 🎯 Concept: Data Profiling

**Objective:** Google aur DuckDuckGo ke search behavior, logging aur personalization compare karke data profiling ka concept samajhna.

---

### 🧪 Practical Steps

**Part A — Google (Data Profiling):**

1. Browser normal mode mein, Google account mein login karo
2. Same keyword search karo (e.g., "Best mobile under 20000", "Ethical hacking course") — 2–3 baar
3. Observe: Ads (top & side), location-based results, YouTube/Shopping suggestions
4. Thodi der baad same keyword dubara search karo → results aur personalized ho jaate hain

**Part B — DuckDuckGo (No Profiling):**

1. New tab ya private window → [DuckDuckGo](https://duckduckgo.com)
2. Bilkul same keywords search karo, multiple times
3. Observe: Ads kam hain, no login suggestion, no past search influence — results mostly same rehte hain

---

### 📊 Google vs DuckDuckGo

| Feature | Google | DuckDuckGo |
|---|---|---|
| Search Logging | ✅ Yes | ❌ No |
| User Profiling | ✅ Yes | ❌ No |
| Personalized Results | High | Minimal |
| Ad Type | Behavior-based / profiled | Keyword-based only |
| Privacy Level | Low | High |
| Private mode effectiveness | Only hides local traces | N/A (no profiling) |

> **Key Insight:** *"If you are not paying for the product, you are the product."*

---

### 🗣️ Viva Q&A — Data Profiling

**Q: Data profiling kya hoti hai?**
User ke data (searches, clicks, location, device) collect karke interest-based profile banana, taaki personalized content aur ads dikhaye ja sakein.

**Q: Google personalization kaise karta hai?**
Search history, Google account activity, location, device, cookies, YouTube watch history, Gmail content ke base par results aur ads personalize karta hai.

**Q: DuckDuckGo ads kaise show karta hai?**
User profile create nahi karta. Ads sirf current search keyword ke basis par dikhata hai — past behavior par nahi.

**Q: Private mode Google profiling kyun nahi rokta?**
Private mode sirf local history aur cookies delete karta hai. Google phir bhi IP address, browser fingerprint aur logged-in account se user ko profile kar sakta hai.

---

## Topic 7 — Free vs Paid VPN

### 🔍 Concept: Tunneling & Encryption

> **VPN (Virtual Private Network):** Ek secure encrypted tunnel jo internet traffic ko remote server ke through route karta hai — **anonymity**, **privacy**, aur geo-restrictions bypass ke liye.

**Main Goal:** Encrypt traffic + Hide real IP + Provide anonymity

---

### 🧪 Practical Steps

**Tools:** [speedtest.net](https://speedtest.net) | [whatismyipaddress.com](https://whatismyipaddress.com)

**Free VPN (e.g., ProtonVPN free, Windscribe):**

1. Install aur connect karo
2. Visit whatismyip → note IP, Country, ISP
3. speedtest.net → note Download/Upload speed, Ping
4. Disconnect aur reconnect karo → note IP rotation (same IP repeat ho sakta hai)

**Paid VPN (e.g., NordVPN, ExpressVPN):**

1. Install aur fastest/multi-country server connect karo
2. Same IP check aur speed test repeat karo
3. Multiple reconnects → observe frequent IP rotation
4. Note: Strong encryption + no logs policy

---

### 📊 Free vs Paid VPN

| Feature | Free VPN | Paid VPN |
|---|---|---|
| Speed | Slow (throttled) | Fast / Stable |
| IP Rotation | Limited, repetitive | High, frequent |
| Server Locations | Few | Many (global) |
| Encryption | Basic | AES-256 + advanced protocols |
| Logs | May keep logs | Strict no-logs |
| Tunneling Protocol | Basic | OpenVPN, WireGuard, IKEv2 |
| Reliability | Low | High |

---

### 🗣️ Viva Q&A — VPN

**Q: VPN ka main purpose?**
Internet traffic ko encrypt karna aur IP hide karna, taaki browsing secure aur anonymous ho.

**Q: IP rotation VPN mein kyun important hai?**
IP rotation se user repeated tracking aur profiling se bacha rehta hai. Frequent IP change = online anonymity improve hoti hai.

**Q: Tunneling aur encryption ka relation?**
Tunneling aapke internet traffic ko secure path mein route karta hai. Encryption ensures ki traffic readable na ho agar ISP ya attacker intercept kare.

> *"VPN = secure tunnel + encrypted traffic = privacy & anonymity."*

---

## Topic 8 — Proxy vs VPN

### 📊 Comparison Table

| Feature | Proxy | VPN |
|---|---|---|
| Encryption | ❌ None | ✅ Strong (AES-256) |
| Coverage | Browser/app-specific | System-wide (all traffic) |
| Speed | Generally faster | Can be slower |
| Privacy | Basic (IP masking only) | Strong (IP + traffic encrypted) |
| ISP visibility | Can see content | Cannot see content |
| Use case | Access blocked sites | Full anonymity + privacy |
| Cost | Usually free | Free + paid options |

> **Simple Analogy:**
> **VPN** = Ek secure tunnel ke andar se travel kar rahe ho (safe & hidden)
> **Proxy** = Kisi doosre aadmi ke through message bhej rahe ho (bas identity hide)

**Conclusion:**
- Security + Privacy chahiye → **VPN best**
- Sirf IP hide ya quick access → **Proxy** use kar sakte ho

---

## Topic 9 — WebRTC Leak Test with VPN

### 🎯 Concept: Real IP Leakage via WebRTC

**Objective:** WebRTC ON aur OFF state mein real IP leakage test karna — VPN ke saath bhi actual IP kaise expose ho sakta hai.

---

### 🧪 Practical Steps

**Part A — WebRTC ON (Leak Test):**

1. VPN connect karo (different country server)
2. Browser default settings rakho (WebRTC enabled)
3. Visit: [browserleaks.com](https://browserleaks.com) → WebRTC section open karo
4. Check karo: Public IP, Local IP, Real ISP IP

> **Observation:** VPN ke bawajood agar real/local IP dikhta hai → **WebRTC leak present hai**

**Part B — WebRTC OFF (Protection):**

1. Firefox mein: `about:config` → `media.peerconnection.enabled` → `false` → restart
2. VPN ON rakho → browserleaks WebRTC section dubara check karo

> **Observation:** Sirf VPN IP dikh raha hai — Local/Real IP not visible

---

### 📊 WebRTC ON vs OFF

| Parameter | WebRTC ON (Chrome + VPN) | WebRTC OFF (Firefox + VPN) |
|---|---|---|
| VPN IP | Visible | Visible |
| Real / Local IP | ❌ Leaks | ✅ Not visible |
| IPv6 | May show real IP | Hidden |
| Anonymity Level | Weak | Improved |

---

### 🗣️ Viva Q&A — WebRTC

**Q: WebRTC kya hota hai?**
Web Real-Time Communication — ek browser technology jo audio, video calling aur file sharing ke liye use hoti hai, bina extra plugins ke.

**Q: WebRTC IP leak kaise karta hai?**
WebRTC STUN servers use karta hai jo directly network interfaces query karte hain — VPN tunnel bypass karke real IP reveal kar dete hain.

**Q: WebRTC leak ka best solution?**
Firefox mein `media.peerconnection.enabled = false`, ya WebRTC block extensions, ya Tor Browser use karna.

> *"WebRTC is useful for communication, but risky for anonymity if not disabled."*

---

## Topic 10 — Cookie & Tracker Analysis

### 🎯 Concept: Persistent Tracking

**Objective:** Ek hi website ko multiple times visit karke cookies aur trackers analyze karna — persistent tracking kaise hoti hai.

---

### 🧪 Practical Steps

**Setup:** Privacy Badger extension install karo aur enable rakho.

**Part A — First Visit (Baseline):**

1. Browser normal mode mein popular website visit karo (news/shopping)
2. Privacy Badger icon click karo → note: number of trackers, third-party domains, blocked/allowed
3. Right click → Inspect → Application/Storage → Cookies → note: tracking cookie names, expiry, third-party cookies

> **Observation:** Long expiry wali cookies = persistent cookies

**Part B — Second Visit (Persistent Tracking Test):**

1. Browser completely close karo → reopen
2. Same website visit karo
3. Cookies re-check karo → Privacy Badger se trackers recheck karo

> **Observation:** Cookies pehle se present rehti hain — website user ko recognize kar leti hai

**Part C — Tracker Blocking:**

1. Privacy Badger blocking observe karo → third-party trackers blocked/restricted dikhte hain

---

### 📊 Tracking Lifecycle

| Stage | Behavior |
|---|---|
| First Visit | New cookie + tracking ID created. Profiling begins. |
| Repeat Visit | Same cookies reused. User recognized. Profile enhanced. |
| With Blocker | Reduced cookie creation. Tracking significantly limited. |

```
User visits site → Tracker sets cookie with unique ID
         ↓
User revisits (same or different site with same tracker)
         ↓
Tracker reads cookie → Recognizes user → Profile enhanced
         ↓
Profile used → Personalized ads follow user across the web
```

---

### 🗣️ Viva Q&A — Cookies & Trackers

**Q: Persistent cookie kya hoti hai?**
Wo cookie jo browser close hone ke baad bhi system mein store rehti hai. Website aapko repeat visits mein identify karti hai.

**Q: Tracker aur cookie mein difference?**
Cookie: Small data file, locally stored, website user ko remember karne ke liye. Tracker: Script jo user behavior track karta hai across multiple sites, cookies + fingerprinting dono use kar sakta hai.

**Q: Kya cookies delete karne se tracking khatam ho jaati hai?**
❌ Nahi. Fingerprinting, IP tracking, login-based tracking abhi bhi ho sakti hai.

---

## Topic 11 — Email Anonymity: Gmail vs Temp Mail

### 🔍 Concept: Metadata Leakage

**Email metadata** email headers mein embedded technical data hai — sender identity, recipients, timestamps, mail servers, routing path, timezone.

**Metadata fields:**
- `Message-ID` — Unique identifier
- `From` / `To` — Sender and recipient
- `Subject` — Subject line
- `SPF`, `DKIM`, `DMARC` — Authentication records
- Routing mail servers + timezone info

---

### 🧪 Practical Steps

**Part A — Gmail Header Analysis:**

1. Gmail account mein login karo → receiver email par test mail bhejo
2. Receiver mailbox → email open karo → More options (⋮) → **Show original / View headers**
3. Note karo: From (email ID), Received lines, Mail server details, Time & timezone, Message-ID domain

> **Observation:** Gmail headers mein sender identity aur mail infrastructure clearly visible

**Part B — Temp Mail:**

1. [temp-mail.org](https://temp-mail.org/en/) visit karo → temporary email ID auto-generate
2. Same receiver email par test mail bhejo
3. Receiver mailbox → headers view karo
4. Note karo: Random/temporary email, limited server info, no personal identifier

> **Observation:** Temp mail headers mein personal metadata kam hota hai

---

### 📊 Gmail vs Temp Mail

| Parameter | Gmail | Temp Mail |
|---|---|---|
| Sender Identity | Personal email (linked to account) | Random / temporary |
| Server Info | Detailed (Google servers) | Limited |
| Account Linkage | Required | None |
| Metadata Exposure | High | Low |
| Traceability | Easier | Harder |
| Longevity | Permanent | Self-destructs |

**EXIF Metadata Tool:** [https://www.exifdata.com/](https://www.exifdata.com/) — images ka metadata edit/check karne ke liye.

---

### 🗣️ Viva Q&A — Email Anonymity

**Q: Email header kya hota hai?**
Technical information block jo email ke sender, receiver, servers, timestamps aur routing path ke details contain karta hai. Header = metadata, message body nahi.

**Q: Metadata leakage ka matlab?**
Email ke technical details (sender IP, server info, timezone) se aapki identity ya location leak ho sakti hai — bina email content read kiye.

**Q: Kya email se IP address mil sakta hai?**
✅ Depends: Gmail web interface se usually hide hoti hai. Direct mail clients (Outlook, Thunderbird) mein IP headers mein visible ho sakta hai.

> *"Email headers mein metadata hota hai jo sender identity aur routing reveal kar sakta hai; temp mail anonymity improve karta hai."*

---

## Topic 12 — Social Media Tracking: Facebook Pixel

### 🎯 Concept: Cross-Site Tracking

**Objective:** Facebook Pixel ke through cross-site tracking observe karna — website activity Facebook par ads ko kaise affect karti hai.

---

### 🧪 Practical Steps

**Setup:** [Meta Pixel Helper](https://chromewebstore.google.com/detail/meta-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc) extension install karo.

**Part A — Baseline:**
1. Facebook/Instagram open karo → Ads section note karo (categories, type)

**Part B — Website Visit & Pixel Detection:**
1. Pixel Helper enable karo
2. Shopping/service website visit karo → 2–3 minutes spend karo
3. Pixel Helper icon click karo → check: Pixel detected, Events fired (PageView, ViewContent, AddToCart)

> **Observation:** Website aapki activity Facebook ko send kar rahi hai

**Part C — Cross-Site Effect:**
1. Website close karo → Facebook/Instagram open karo → feed refresh karo
2. Same product/category related ads appear hona = cross-site tracking proof

**Part D — Tracker Blocking:**
1. Privacy Badger / uBlock Origin enable karo → same site dubara visit
2. Pixel Helper se observe karo → Pixel blocked/limited → Facebook feed mein ads effect kam

---

### 📊 Facebook Pixel Tracking

| Scenario | Pixel Activity | Ads Behavior |
|---|---|---|
| Before site visit | No recent event | Generic ads |
| After site visit | PageView / ViewContent | Related product ads |
| With blocker ON | Limited / Blocked | Reduced targeting |

```
User logs into Facebook (gets unique tracking cookie)
          ↓
User visits Site A (Facebook Pixel installed)
          ↓
Pixel fires → Sends event data to Facebook servers
          ↓
User visits Site B (also has Pixel)
          ↓
Combined profile built → Behavioral targeting activated
```

---

### 🗣️ Viva Q&A — Facebook Pixel

**Q: Facebook Pixel kya hota hai?**
Ek small JavaScript code snippet jo websites mein embed hota hai. User activity (page views, clicks, purchases) Facebook ko send karta hai — ads aur analytics ke liye.

**Q: Cross-site tracking kaise hoti hai?**
Same user multiple sites visit karta hai jahan Pixel installed hai → Facebook unified user profile banata hai → behavior track hota hai across sites.

**Q: Kya tracker blockers Pixel ko rok sakte hain?**
✅ Partially. ❌ Fully 100% stop nahi karte, especially logged-in Facebook account ke saath.

> *"Facebook Pixel enables cross-site tracking; blockers reduce but cannot fully eliminate tracking."*

---

## Topic 13 — TOR Browser: Onion Routing & IP Path Analysis

### 🔍 Concept: Onion Routing

> **TOR (The Onion Router):** Open-source, privacy-focused browser jo traffic ko multiple encrypted relays ke through route karta hai — origin trace karna extremely difficult ho jaata hai.

**Onion Routing:** Data multiple layers of encryption mein wrap hota hai. Har relay node ek layer decrypt karke next ko forward karta hai — koi bhi single node origin aur destination dono nahi jaanta.

---

### 🏗️ TOR Routing Structure

```
[Your Device]
     ↓ (encrypted layer 3)
[Entry Node / Guard Node]  ← jaanta hai: aapka real IP | nahi jaanta: destination
     ↓ (encrypted layer 2)
[Middle Relay Node]        ← nahi jaanta: origin ya destination
     ↓ (encrypted layer 1)
[Exit Node]                ← jaanta hai: destination | nahi jaanta: aapka real IP
     ↓
[Website]                  ← sirf Exit Node IP dekhti hai
```

---

### 🧪 Practical Steps

**Tor + Proxychains Setup:**
```bash
service tor start
cd kalitorify/
./kalitorify.sh -t   # automatic transparent proxy via Tor
```
Reference: [https://github.com/brainfucksec/kalitorify](https://github.com/brainfucksec/kalitorify)

**IP Path Comparison:**
1. Normal browser → [whatismyip.com](https://whatismyipaddress.com) → **Real IP + location note karo**
2. Tor Browser install → Connect → Same URL open karo → **Exit node IP + different country**
3. Tor Browser → New Identity → IP check → **Har baar new IP/country**

---

### 📊 Normal Browser vs TOR Browser

| Parameter | Normal Browser | TOR Browser |
|---|---|---|
| IP Visibility | Real IP | Exit Node IP only |
| Location | Real location | Exit node's masked location |
| Encryption | HTTPS/HTTP | Multi-layer onion encryption |
| Anonymity | Low | High |
| Connection Path | Direct | Multi-node relay (3+ hops) |
| Speed | Fast | Slower (relay overhead) |
| Fingerprinting | Unique per user | Standardized (all TOR users identical) |

---

### 🗣️ Viva Q&A — TOR Browser

**Q: Tor Browser kya hota hai?**
Ek special browser jo anonymous browsing provide karta hai using Tor Network (The Onion Router).

**Q: Onion routing ka matlab?**
Data ko multiple encrypted layers mein route karna — jaise onion ke layers — taaki source aur destination separate rahein aur track na kiya ja sake.

**Q: Exit Node kya hota hai?**
Tor network ka last relay jahan traffic internet mein enter hoti hai. Website sirf exit node ka IP dekhti hai.

**Q: Tor Browser anonymity kyun strong hai?**
Multi-layer encryption, real IP hide, traffic multiple nodes se route — single node full path nahi jaanta. Plus: sab TOR users ka same fingerprint.

**Q: Tor Browser ke limitations?**
Speed slow (multi-node routing), malicious exit node traffic sniff kar sakta hai, browser misconfiguration se IP leak, government agencies entry/exit node correlations monitor kar sakti hain.

> *"Tor Browser uses onion routing — traffic passes through multiple encrypted relays, hiding the user's real IP and location."*

---

## Topic 14 — MAC Address Changer

### 🔍 Concept: Hardware Tracking

> **MAC (Media Access Control) address:** Network interface card (NIC) ka hardware ID — 48-bit address (e.g., `00-1A-2B-3C-4D-5E`) — local network communication ke liye use hota hai.

⚠️ **Only on your own system / lab system**

---

### MAC vs IP Address

| Feature | MAC Address | IP Address |
|---|---|---|
| Layer | Layer 2 (Data Link) | Layer 3 (Network) |
| Scope | Local network only | Global / Internet |
| Assigned by | NIC manufacturer | ISP or DHCP server |
| Travels beyond router? | ❌ No | ✅ Yes |
| Permanent | Hardware-level (spoofable) | Dynamic or static |

---

### 🧪 Practical Steps

**Step 1 — Check Current MAC (Before):**

Windows:
```cmd
ipconfig /all
```
"Physical Address" note karo.

Linux:
```bash
ip link show
```

**Step 2 — Internet Disconnect Karo** (MAC change always offline mein)

**Step 3 — MAC Address Change**

*Windows (Device Manager):*
1. Device Manager → Network Adapters → Active adapter → Right click → Properties
2. Advanced tab → Network Address → New MAC enter karo (12 hex digits, no colons)
3. OK → Adapter disable & enable karo

*Linux:*
```bash
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:11:22:33:44:55
sudo ifconfig eth0 up
```

**Step 4 — Verify Change:**
```cmd
ipconfig /all
```

**Step 5 — Reconnect & Test** → Router/network logs mein new device ID dikhegi

---

### 📊 MAC: Before vs After

| State | MAC Address |
|---|---|
| Before | 3C-52-82-A1-B9-10 (original) |
| After | 00-A1-B2-C3-D4-E5 (spoofed) |

---

### 🗣️ Viva Q&A — MAC Address

**Q: MAC address kya hota hai?**
Ek unique hardware ID jo network device ko identify karti hai local network mein.

**Q: Hardware tracking kya hoti hai?**
Devices ko MAC address jaise hardware identifiers ke through track karna.

**Q: Kya MAC change permanent hota hai?**
❌ Nahi. Software se kiya gaya MAC change temporary hai — restart ke baad original MAC wapas aa sakta hai.

**Q: MAC spoofing se anonymity milti hai?**
Limited. MAC change sirf local network tracking se bachata hai. Internet-level anonymity ke liye VPN/Tor chahiye.

**Q: Kya legal hai?**
✅ Apne system par testing & privacy purpose ke liye legal. ❌ Kisi aur ke network mein misuse karna illegal.

> *"MAC address is a hardware identifier used for device-level tracking; changing it helps reduce local network tracking but does not provide full anonymity."*

---

## Topic 15 — User-Agent Spoofing (Advanced Practical)

### 🎯 Concept: Device Identity Masking

**Objective:** Browser ka User-Agent change karke websites ko fake device identity dikhana aur device identity masking concept samajhna.

---

### 🧪 Practical Steps

**Step 1 — Check Current UA (Before):**

Visit: [browserleaks.com/user-agent](https://browserleaks.com/user-agent) ya [whatismybrowser.com](https://whatismybrowser.com)

Note karo: Browser name & version, OS, Device type (Desktop/Mobile)

**Step 2 — Change via Developer Tools:**

*Chrome/Edge:*
1. F12 → DevTools → 3 dots (⋮) → More tools → Network conditions
2. "Use browser default" uncheck karo → Dropdown se Android/iPhone/Firefox select karo

*Firefox (about:config):*
1. `about:config` → Search: `general.useragent.override`
2. String value add karo:
```
Mozilla/5.0 (Linux; Android 13; Pixel 7) AppleWebKit/537.36 Chrome/120 Mobile
```

**Step 3 — Verify (After):**
- Same UA test website dubara open karo → browser/OS/device change dikhega
- Desktop site → Mobile site ban jaati hai; ads & layout change ho sakta hai

---

### 📊 UA: Before vs After

| State | Detected Device |
|---|---|
| Before | Windows 10 — Chrome Desktop |
| After | Android — Chrome Mobile |

---

### 🗣️ Viva Q&A — User-Agent Spoofing

**Q: User-Agent kya hota hai?**
Browser identification string jo device, OS aur browser details batati hai.

**Q: Kya UA spoofing se full anonymity milti hai?**
❌ Nahi. UA spoofing sirf basic identification hide karti hai — fingerprinting, IP, cookies ab bhi track kar sakte hain.

**Q: Websites UA ka use kyun karti hain?**
Responsive layout decide karne, compatibility check, analytics & tracking ke liye.

**Q: User-Agent aur Browser Fingerprint mein difference?**
User-Agent = single visible string. Fingerprint = multiple parameters (fonts, screen, WebGL, timezone, etc.).

> *"User-Agent spoofing masks basic device identity, but full anonymity requires IP protection and fingerprint resistance."*

---

## Topic 16 — OSINT Reverse Identification & De-anonymisation

### 🔍 Concept: De-anonymization

> **De-anonymisation:** Hidden ya anonymous identity ko multiple clues, data points, ya metadata correlate karke reveal karna.

⚠️ **Ethical Note:** Sirf learning purpose ke liye. Real logon ko target/doxx nahi karna. Dummy/consented profile use karein. OSINT = public data only.

**Key Concepts:**
- **OSINT (Open Source Intelligence):** Publicly available sources se intelligence gather karna
- **ID Leakage:** Usernames, images, posting patterns se unintentional identity exposure
- **Cross-platform Correlation:** Shared usernames, images, writing style se accounts link karna

---

### 🧪 Practical Steps

**Step 1 — Dummy Profile Select Karo**

Username (e.g., dark_shadow_07), platform (Instagram/X/GitHub/Forum — dummy), bio + profile pic (public)

**Step 2 — Username OSINT**

```
"username" site:instagram.com
```
ya simply `"username"` search karo. Check: same username multiple sites par? Same bio/writing style?

**Step 3 — Reverse Image Search**

Profile photo download karo → search karo:
- [Google Images](https://images.google.com) — drag/upload
- [Yandex Images](https://yandex.com/images/) — faces ke liye more effective
- [TinEye](https://tineye.com) — exact/modified copies

Check: Same image kahin aur use hui? Stock image ya personal photo?

**Step 4 — Content & Metadata Analysis**

| Technique | What it Reveals |
|---|---|
| Posting time pattern | Timezone → geographic region |
| Activity pattern | Sleep/wake schedule → country |
| Language & slang | Nationality, education, regional identity |
| Cross-platform correlation | Unified identity |
| File metadata (EXIF) | GPS, device, timestamp |

**Step 5 — Hypothesis Build**

Possible country/region, possible profession/interest — probability based, never absolute claim.

---

### 🔄 De-anonymisation Process

```
Collect target data (username, image, post content)
          ↓
Reverse image search + username OSINT
          ↓
Posting time patterns → estimate timezone
          ↓
Cross-platform correlation
          ↓
Metadata extraction (if files available)
          ↓
Build hypothesis → corroborate multiple clues
          ↓
Potential identity inference (with ethical caution)
```

---

### 🗣️ Viva Q&A — OSINT

**Q: OSINT kya hota hai?**
Open Source Intelligence — publicly available information se intelligence collect karna: social media, websites, public records, images, forums.

**Q: Kya OSINT 100% accurate hai?**
❌ Nahi. Probability based hypothesis hai, not courtroom proof. Misidentification possible hai.

**Q: Kya OSINT illegal hai?**
❌ Nahi — agar sirf public data use ho, no hacking/private access, no harassment/misuse.

**Q: De-anonymization se kaise bachein?**
Different usernames, unique images, metadata strip karo, irregular posting times, no cross-platform linking, Tor + Tails OS.

**Q: Investigator ki responsibility?**
Ethics follow karna, assumptions ko facts na banana, misuse se bachna, privacy laws ka dhyan rakhna.

> *"De-anonymisation involves correlating multiple open-source data points to infer identity — it must be done ethically and responsibly."*

---

## Topic 17 — Metadata Removal: Image EXIF Analysis

### 🎯 Concept: Hidden Information Leaks

> **Metadata** = data about data — file ke hidden technical details batata hai.
> **EXIF (Exchangeable Image File Format)** = image metadata: camera model, GPS, timestamp, software.

⚠️ Only on your own images.

---

### 🧪 Practical Steps

**Step 1 — Image Select Karo**

Apni mobile camera se li hui image (GPS ON ke saath best results).

**Step 2 — EXIF Data Check (Before)**

*Online:* [exifdata.com](https://www.exifdata.com/) ya [exif.tools](https://exif.tools)

*Windows:*
Right click → Properties → **Details tab** → note: Camera model, Date & time, GPS location (lat/long), Software used

**Step 3 — Metadata Remove Karo**

*Windows:*
Image → Right click → Properties → Details → **"Remove Properties and Personal Information"** → "Create a copy with all possible properties removed" select karo

*Alternative — Screenshot:*
Screenshot lena original EXIF remove karta hai (new metadata add ho sakta hai)

**Step 4 — EXIF Check (After)**

Same image ka EXIF dubara check karo → GPS missing, camera details removed, timestamps cleared.

---

### 📊 EXIF: Before vs After

| Parameter | Before | After |
|---|---|---|
| Camera Model | Visible | Removed |
| GPS Location | Present (lat/long) | Not present |
| Date/Time | Present | Removed |
| Image Quality | Same | Same (unchanged) |

---

### 🗣️ Viva Q&A — Metadata

**Q: EXIF data kya hota hai?**
Images mein embedded camera, GPS, time jaise technical metadata.

**Q: Metadata removal kyun zaroori hai?**
Online sharing se pehle privacy protect karne ke liye — location aur device trace na ho.

**Q: Screenshot lene se metadata remove hota hai?**
✅ Usually original EXIF nahi hota. ❌ Lekin new metadata (time/device) add ho sakta hai.

**Q: Investigators EXIF ka use kaise karte hain?**
Location verification, timeline creation, device matching ke liye.

> *"EXIF metadata contains hidden technical details that can leak location and device info; removing it is essential for privacy."*

---

## Topic 18 — Traffic Analysis (Controlled Lab)

### 🎯 Concept: Correlation Attacks

⚠️ **Strict Ethics:** Sirf controlled lab / own system. Real networks ya logon par attack nahi. Observation-only.

> **Correlation Attack:** Encrypted traffic ke timing aur size ko match karke source-destination relation infer karna — content decrypt nahi hota, patterns correlate hote hain.

---

### 🧪 Practical Steps

**Lab Setup:**
- System: Own laptop/VM
- Tools: Task Manager / Resource Monitor (basic)
- Scenarios: A) Tor only | B) VPN → Tor

**Step 1 — Baseline (Normal Browser):**

1. Normal browser open → 2–3 text-heavy websites visit karo
2. Observe: Network usage spikes, consistent timing (request → response)

> Baseline = direct & predictable traffic

**Step 2 — Tor Only Traffic:**

1. Tor Browser open → same websites visit karo
2. Observe: Burst-like traffic, higher latency, uniform packet sizes (encryption)

> Content readable nahi — pattern visible hota hai

**Step 3 — VPN → Tor Traffic:**

1. VPN connect karo → Tor Browser open karo → same actions
2. Observe: Extra latency, different timing vs Tor-only, double-encrypted stream

> Double hop = better concealment, but timing patterns still exist

**Step 4 — Timing Correlation (Conceptual):**

Same action (page load) 3–4 baar repeat karo. Note: action start time, peak network time. Similar timing + volume patterns correlate kiye ja sakte hain (theoretical risk).

---

### 📊 Traffic Pattern Comparison

| Scenario | Latency | Pattern Visibility |
|---|---|---|
| Normal | Low | High (clear) |
| Tor only | High | Medium |
| VPN → Tor | Higher | Low–Medium |

> **Key Point:** Encryption ≠ pattern hiding. Content decrypt nahi hota, timing aur volume se correlation possible hai.

---

### 🗣️ Viva Q&A — Traffic Analysis

**Q: Traffic analysis kya hoti hai?**
Encrypted traffic ke timing, size aur frequency observe karke information infer karna.

**Q: Correlation attack ka matlab?**
Entry side aur exit side ke traffic patterns match karke user activity infer karna.

**Q: Tor traffic encrypted hone ke bawajood risk kyun?**
Encryption content hide karta hai — timing aur volume hide nahi karta.

**Q: VPN + Tor ka benefit?**
ISP se Tor usage hide hota hai, extra hop add hota hai → correlation harder, but impossible nahi.

**Q: Kya correlation attacks common hain?**
❌ Daily attackers ke liye nahi. ✅ State-level/large observers ke liye possible.

**Q: Correlation attacks se bachne ke best practices?**
Tor Browser default settings, background noise minimize, random delays use karo, large file downloads Tor par avoid karo.

> *"Correlation attacks infer relationships using traffic timing and volume; Tor reduces risk, but powerful observers can still attempt correlation."*

---

## 🧰 Anonymity Toolkit Reference

| Tool / Technique | Kya Protect Karta Hai | Limitations |
|---|---|---|
| Disable WebRTC | IP leak via browser | Must be done per browser |
| User Agent Spoofing | Browser ID string | Advanced tracking nahi rokta |
| Firefox about:config hardening | Fingerprinting, cookies, trackers | Kuch sites break ho sakti hain |
| Private / Incognito Mode | Local history & cookies | IP hide nahi karta |
| VPN | IP address, traffic encryption | WebRTC/DNS leaks possible |
| Proxy | IP masking (partial) | No encryption |
| TOR Browser | High anonymity, multi-layer encryption | Slow speeds |
| Temp Mail | Email metadata exposure | Server logs may persist |
| Privacy Badger | Third-party trackers | All pixel tracking nahi rokta |
| MAC Spoofing | Local network device ID | Only local; temporary |
| DNS Leak Test | VPN DNS leaks diagnose karta hai | Test tool, fix nahi |
| DuckDuckGo | Search profiling | All tracking prevent nahi karta |
| Reverse Image / OSINT | Anonymous profiles trace karna | Hypothesis only — not always accurate |
| Metadata Removal (EXIF) | GPS, device info in images | New metadata add ho sakta hai |
| Kalitorify | Transparent Tor proxy (system-wide) | Kali Linux specific |

---

## 📋 Level-wise Practical Summary

### 🟢 Basic Level
| Practical | Concept |
|---|---|
| A — IP Address Check | IP exposure samajhna |
| B — Browser Fingerprint Test | Fingerprinting |
| C — Private vs Normal Mode | Local tracking |
| D — DNS Leak Test | DNS anonymity |
| E — Search Engine Comparison | Data profiling |

### 🟡 Intermediate Level
| Practical | Concept |
|---|---|
| VPN Configuration (Free vs Paid) | Tunneling & encryption |
| WebRTC Leak Test with VPN | Real IP leakage |
| Cookie & Tracker Analysis | Persistent tracking |
| Email Anonymity Test | Metadata leakage |
| Social Media Tracking (Facebook Pixel) | Cross-site tracking |

### 🔵 Advanced Level
| Practical | Concept |
|---|---|
| Tor Browser Practical | Onion routing |
| MAC Address Change | Hardware tracking |
| User-Agent Spoofing | Device identity masking |
| OSINT Reverse Identification | De-anonymization |
| Metadata Removal (EXIF) | Hidden info leaks |

### 🔴 Professional / Investigation Level
| Practical | Concept |
|---|---|
| Traffic Analysis (Controlled Lab) | Correlation attacks |

---

> **Final Exam Line:**
> *"True online anonymity requires a layered approach — no single tool is sufficient. VPN hides your IP, Tor provides multi-hop encryption, browser hardening blocks fingerprinting, and responsible behavior prevents OSINT-based de-anonymisation."*
