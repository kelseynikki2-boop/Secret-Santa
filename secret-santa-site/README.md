# Secret Santa Spin

## Put it on GitHub Pages
1. On github.com create a new repository (e.g. `secret-santa`), set it to Public.
2. Upload `index.html` (drag it into the repo, click Commit).
3. Settings > Pages > Source: "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
4. After a minute your link is `https://<your-username>.github.io/secret-santa/`.

Admin panel: open the link with `#admin` on the end, e.g. `.../secret-santa/#admin`, and enter the passcode
(`ADMIN_PASSCODE` near the top of `index.html`, change it before sharing).

## Two modes
**No-setup mode (works as-is, `FIREBASE_URL` empty):** fixed draw, nobody gets themselves. Each phone remembers its own result.
The "Already drawn" list only shows names drawn on that phone, and Reset only clears that phone.

**Shared mode (recommended): everyone sees which names are drawn, draw is random.** One-time setup, free:
1. Go to https://console.firebase.google.com, Add project (turn off Analytics).
2. Build > Realtime Database > Create Database > pick a location > Start in **test mode**.
3. Copy the database URL shown at the top (looks like `https://xxxx-default-rtdb.firebaseio.com`).
4. Open the Rules tab, paste the below, Publish:
   ```
   { "rules": { ".read": true, ".write": true } }
   ```
5. In `index.html`, put the URL in `FIREBASE_URL = "..."`, save, re-upload to GitHub.

Anyone with the link can technically edit the database, which is fine for a family game.
Before sending the link out, open `#admin`, unlock, and press Reset everything to clear your test spins.
