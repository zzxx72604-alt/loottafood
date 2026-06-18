# LoottaFood — Run, Host & Test Guide

A food‑ordering web app (Angular frontend + Node/Express + MongoDB backend).
Customers browse a menu, favorite items, rate them, and order; admins manage the
menu from a dashboard.

---

## 1. Prerequisites

- **Node.js** 18+ and **npm**
- **MongoDB** running (local `mongodb://localhost:27017`, or a MongoDB Atlas URL)
- A modern browser (Chrome/Edge/Safari/Firefox)

---

## 2. One‑time setup (install packages)

From the **project root** (`foodmine`), a single install sets up everything
(root, frontend, and backend — handled automatically):

```bash
cd foodmine
npm install        # installs root + frontend + backend (uses --force for the frontend)
```

### Backend environment file
Make sure `backend/src/.env` exists with:

```
MONGO_URI=mongodb://localhost:27017/loottafood
JWT_SECRET=any-long-random-secret-string
PORT=5000
```

---

## 3. Run it (development)

### Easiest — one command (runs BOTH servers)
From the **project root** (`foodmine`):

```bash
npm install     # one time — installs root + frontend + backend
npm run dev     # starts the backend AND the frontend together
```

`npm run dev` launches the backend (API on :5000) and the frontend (on :4200,
bound to 0.0.0.0 so phones on your Wi‑Fi can reach it). This is why the page looked
empty before — running only the frontend means there's no backend to load the menu from.

### Or run them separately (two terminals)
```bash
# Terminal A — backend API on http://localhost:5000
cd backend
npm start

# Terminal B — frontend on http://localhost:4200
cd frontend
ng serve
```

Open **http://localhost:4200**.

### Seed the data (first run)
In your browser, visit these once:

- `http://localhost:5000/api/users/seed`  → creates sample users
- `http://localhost:5000/api/foods/seed`  → loads the 12 menu items

To force‑reload the menu after editing items in code:
`http://localhost:5000/api/foods/seed?force=true`

---

## 4. Create / use an admin account

**Option A – built‑in admin (easiest):**
1. Run `…/api/users/seed` (above).
2. Log in with **john@gmail.com** / **12345**.
3. Click your name (top‑right) → **Dashboard**.

**Option B – make your own account admin:**
1. Register an account in the app (e.g. `you@gmail.com`).
2. Visit `http://localhost:5000/api/users/makeAdmin/you@gmail.com`.
3. **Log out and log back in** (admin status is stored in the login token).
4. Click your name → **Dashboard**.

> The `makeAdmin` route is a development helper — remove it before any real deployment.

---

## 5. What to test

- **Menu & search** — browse, search, filter by category, **Sort** (price / top‑rated),
  **On sale only** toggle.
- **Card hover/hold** — hover (desktop) or press‑hold (mobile) a card to reveal its description overlay.
- **Food page** — favorite (♥), tap stars to rate, **You may also like** recommendations, Add to Cart.
- **Dark mode** — 🌙 / ☀️ toggle in the header (remembered per browser).
- **Order flow** — Cart → Checkout (name, address, map) → Payment (ABA / KHQR / Wing / WeChat / Alipay / ACLEDA) → Track.
- **Orders page** — re‑order, delete (with undo), all with confirmations.
- **Profile** — edit name/email and change password.
- **Admin Dashboard** — add/edit/delete items, set **discount %**, **drag to reorder**, image **preview + upload**.

> Favorites and your personal star ratings are stored in the browser (localStorage),
> so they’re per‑device for now.

---

## 6. Test on a phone / tablet (and hiding your IP)

Everything now runs through **one port (4200)** — the dev server proxies `/api`
to the backend — so there are **no code edits or CORS changes** needed.

### Same Wi‑Fi (LAN)
1. `npm run dev` (the frontend is already exposed on `0.0.0.0`).
2. Find your IP: `ipconfig` → IPv4 (e.g. `192.168.1.20`).
3. On the phone (same Wi‑Fi), open `http://192.168.1.20:4200`.
4. QR: point it at `http://192.168.1.20:4200`.

### Hide your IP / share from anywhere — ngrok
1. Install ngrok (https://ngrok.com), then run `npm run dev`.
2. In a second terminal: `ngrok http 4200`.
3. Copy the public URL it prints (e.g. `https://abc123.ngrok-free.app`).
4. Open that URL on any device; for the table QR, encode **that** URL.

Notes:
- The free ngrok URL **changes every restart**, so regenerate the QR each session.
- First-time visitors see an ngrok "Visit Site" page (free tier).
- For a permanent, branded link, deploy instead (section 7).

### The table QR
Make a QR that encodes the URL from above (LAN IP or the ngrok link) with any QR
generator, print it, and place it on tables — customers scan → menu opens → they order.
The header **📷 ScanMe** button can also display a QR image saved at
`frontend/src/assets/scan-qr.jpg`.

## 7. Build for production

```bash
cd frontend
ng build --configuration production    # outputs into backend/built/public
```
Then the backend serves the built app. For real public access (and "order from home"),
deploy the backend + MongoDB to a host (e.g. Render/Railway/VPS) so the app has a
public URL — then your table QR points to that domain.

---

## 8. Where to put images (future updates)
Drop files in `frontend/src/assets/` (see `UPLOAD-HERE.txt` there):
- `scan-qr.jpg` — the ScanMe order QR
- `logo.png` — header logo (ask to wire it in)
- `profile-default.png` — default profile avatar

---

## 9. Quick recommendations
- For a class demo on one screen: just `localhost:4200` is fine.
- For an in‑store demo with phones: use the Wi‑Fi/LAN steps in section 6.
- For "order from anywhere": deploy it (section 7).
- Keep uploaded images small; menu images uploaded via the admin form are stored in the database as data, which is fine for a demo but not for large catalogs.

---

## 10. Notifications (orders)

A 🔔 bell appears in the header when logged in (polls every ~20s, no spinner):

- **Admin** — the badge shows the number of **paid orders waiting** to be handled.
  Open it → click a notification → goes to **Manage Orders** to mark them delivered.
- **Customer** — the badge shows when an order has been **delivered/completed**.
  Opening the bell clears the badge (the "seen" state is remembered per browser).

Flow: customer pays → admin's bell shows a new request → admin marks delivered →
customer's bell shows "Your order has been delivered".

---

## 11. Deleting customer data (users / orders)

There is **no in‑app "delete user" screen** — user accounts and orders live in MongoDB,
so you remove them from the database directly.

**Option A — MongoDB Compass / Atlas (visual):**
1. Open your database (the one in `MONGO_URI`).
2. `users` collection → find the user (by `email`) → **delete document**.
3. `orders` collection → delete that user's orders (filter by their `user` id).

**Option B — mongosh (command line):**
```js
use loottafood
// delete one user
db.users.deleteOne({ email: "customer@example.com" })
// delete that user's orders (use the _id you saw above)
db.orders.deleteMany({ user: ObjectId("PASTE_USER_ID_HERE") })
// or wipe ALL orders / ALL non-admin users (careful!)
db.orders.deleteMany({})
db.users.deleteMany({ isAdmin: false })
```

**Other resets:**
- Reload the menu to defaults: visit `/api/foods/seed?force=true`.
- A customer's **favorites & star ratings** are stored in the browser (localStorage),
  not the database — clear them via the browser (DevTools → Application → Local Storage)
  or by signing in on a fresh browser/profile.

> Tip: never expose database credentials publicly, and remove the dev `makeAdmin`
> route before deploying.
