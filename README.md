# GroceryGenie
Track grocery inventory and plan meals using ingedients on hand. 

### 1) Host the folder (HTTPS required)
- **GitHub Pages**: push files to a repo → Settings → Pages → Deploy from branch → root → save → open the public URL.
- **Netlify**: drag-and-drop the folder in the dashboard; copy the assigned HTTPS URL.

> If your host expects `index.html`, rename `grocergenie-pwa-index.html` → `index.html` (and keep the same folder structure).

### 2) Install as a PWA
- **Android/Chrome**: open your URL → browser menu → **Install app** (or **Add to Home screen**).
- **iOS/Safari**: Share → **Add to Home Screen** (uses `icons/apple-touch-icon.png`).  
- **Desktop (Chrome/Edge)**: Address-bar “Install” icon or browser menu.  
  _Note: there’s no service worker yet, so “offline” isn’t enabled (see Roadmap)._

---

## 🧩 Embed in Canva

- In **Canva** (desktop editor): **Apps → Embed** (search for “Embed”, icon `</>`) → paste your public URL → **Add to design**.
- If **Embed** isn’t visible: try a **Presentation/Whiteboard/Doc**, or open the **Embed** app page and click **Use in a design**. Some team/org settings can hide apps.
- **Camera in an iframe**: The Canva editor renders the app in an iframe. Many browsers block camera access in iframes, so **live scanning may not work inside the editor**. Publish your Canva site or add a link/QR to **open the app in a new tab** for full camera access.

Tip: Add a button in your design labeled **“Open GrocerGenie in a new tab”** pointing to your URL, and/or a QR Code (Canva has a QR app).

---

## 🔧 How It Works

- **Scan**: Uses the [BarcodeDetector API](https://developer.mozilla.org/en-US/docs/Web/API/Barcode_Detection_API). If unsupported, you can still type a barcode and use **Lookup**.
- **Auto-lookup**: Queries **Open Food Facts** by barcode to suggest a name and rough category. You can edit before saving.
- **Storage**: Items, devices, and settings are kept in `localStorage` (private to your device). Use **Export/Import** to move data.
- **Recipes**: A small built‑in set with required ingredients and compatible devices. The planner ranks by % of ingredients you currently have and penalizes recipes that need devices you don’t own (configurable).

---

## 🛠️ Development (optional)

You can run this as a single HTML file in any static host. If you want a local dev workflow:

1. Create a React project (e.g., Vite), add Tailwind, and copy the app code into `src/App.jsx`.
2. Ensure the UI includes the scanner component, OFF lookup helper, and localStorage persistence keys:
   - `grocergenie_items_v2`
   - `grocergenie_devices_v1`
   - `grocergenie_settings_v1`
3. Build & deploy to any static host.

> The provided `grocergenie-pwa-index.html` already inlines React/Tailwind via CDNs for a no-build setup.

---

## ⚙️ Configuration & Extensibility

- **Add more recipes**: Edit the `RECIPES` array (name, ingredients, devices, steps).  
- **Device types**: Update `DEVICE_TYPES` to match your kitchen.  
- **Matching logic**: Tweak the minimum match threshold (`>= 0.35`) or the device penalty factor (defaults to `× 0.1` when missing a device).  
- **Expiry badges**: Adjust thresholds in `expStatus()` for your preferences.

---

## 🔐 Privacy & Security

- Your pantry data never leaves your browser unless you export it.  
- Scanning requires **camera permission** granted by you.  
- When embedded in Canva or any iframe, camera permissions may be limited by the host page and browser security model.

---

## 🧯 Troubleshooting

- **No camera / scan button disabled**: Ensure HTTPS and that your browser supports `BarcodeDetector`. If not, type the barcode manually and use **Lookup**.\
- **Nothing happens on Lookup**: Some barcodes aren’t in the Open Food Facts database. You can enter item info manually. \
- **Canva shows but can’t scan**: Open the app URL directly in a new tab (outside the Canva iframe). \
- **Install/PWA option missing**: Confirm the manifest loads (DevTools → Application → “Manifest”). Make sure you deployed with the `manifest.webmanifest` and `icons/` next to your HTML file.

---

## 📜 Attribution & License

- **Open Food Facts**: Product data comes from the Open Food Facts database, available under the [Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/1-0/). Trademarks are the property of their respective owners.
- **Project License**: MIT (feel free to change). See [`LICENSE`](LICENSE) if you add one.

---

## 🗺️ Roadmap

- [ ] Service Worker for **offline caching** and faster loads.  
- [ ] Switch photos from `localStorage` → **IndexedDB** for capacity.  
- [ ] Optional **account sync** (e.g., Supabase/Firebase).  
- [ ] **Recipe API** integration + nutrition filters.  
- [ ] OCR on product photos to extract text/ingredients.  
- [ ] Bulk add via CSV import.

---

## 🙌 Acknowledgements

- Open Food Facts community and contributors.  
- MDN for the Barcode Detection API docs.

---

## Screenshots (optional)

Drop images (or animated GIFs) here to showcase scanning, planner, and inventory views.
"""

with open("/mnt/data/README.md", "w", encoding="utf-8") as f:
    f.write(readme)

"/mnt/data/README.md created"
