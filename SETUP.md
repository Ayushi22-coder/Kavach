# 🛡️ KAVACH — Setup Instructions (Mock Mode · No Server Needed)

## Files you actually need
- `KAVACH_App.html` — the entire app, self-contained

That's it. **You no longer need:**
- ❌ `server.js`
- ❌ `package.json`
- ❌ `npm install`
- ❌ An Anthropic API key
- ❌ Any running terminal/server

This version uses realistic pre-written responses instead of live AI calls — perfect for demos, zero cost, zero setup friction, zero risk of failure during judging.

---

## ⚡ How to Run (2 options)

### Option A — Just double-click it (simplest)
Double-click `KAVACH_App.html` → opens directly in your default browser → done.

### Option B — Use VS Code Live Server (nicer dev experience)
1. Open the folder in VS Code (`File → Open Folder`)
2. Install **Live Server** extension if you don't have it (`Ctrl+Shift+X` → search "Live Server" by Ritwick Dey → Install)
3. Right-click `KAVACH_App.html` → **Open with Live Server**

Either way, the app works immediately.

---

## ✅ How to Demo It

Click any of the 5 quick scenario buttons in the sidebar or welcome screen:
- 👮 CBI officer call
- 📹 Video call fake warrant
- 📦 Fake customs parcel
- 🏠 Digital house arrest
- 📜 Fake court notice

Each gives a realistic 🔴 HIGH RISK verdict with red flags and action steps within ~1-2 seconds (simulated thinking delay).

You can also type your own scenario — it intelligently matches keywords (CBI, ED, customs, warrant, video call, payment, etc.) to pick the most relevant response.

Try the **"What is digital arrest?"** chip too — shows a 🟢 LOW RISK informational response, proving the system isn't just always returning HIGH.

---

## 🌍 Other Features Still Fully Working

- Language switcher (UI labels change; for a fully translated demo response you'd need to wire in IndicTrans2 later)
- WhatsApp tab — same mock engine, shorter message-style responses
- Architecture tab — static info, always works
- Pitch Deck tab — static info, always works
- Evidence panel — session ID, timestamps, alert counter all update live
- "Escalate to MHA Portal" button — shows the evidence packet popup

---

## 🔮 If You Later Want Live AI (Optional, Costs Money)

If you want to upgrade back to real Claude AI responses later (e.g. after the hackathon, with API credits):
1. You'd need `server.js` and `package.json` again (ask and I'll regenerate them)
2. Add Anthropic API credits at console.anthropic.com → Plans & Billing
3. Swap the mock response engine back to live `fetch()` calls

But for your hackathon demo — **this mock version is actually the safer choice.** No internet dependency, no API downtime risk, completely consistent every single time you present it.
