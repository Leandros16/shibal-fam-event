# Shibal Fam Event — Tournament Bracket

A real-time double elimination tournament bracket with admin controls and Firebase sync.

## How It Works

- **Viewers** visit the site and see the bracket update in real-time
- **Admin** visits with a secret URL parameter to select winners

## URLs

| Who | URL |
|-----|-----|
| Viewers | `https://yourusername.github.io/shibal-fam-event/` |
| Admin | `https://yourusername.github.io/shibal-fam-event/?admin=shibalfam2026` |

> ⚠️ **Change the admin key!** Open `index.html` and find this line:
> ```js
> const ADMIN_KEY = 'shibalfam2026';
> ```
> Change `shibalfam2026` to your own secret key.

## Deploy to GitHub Pages

1. Create a new repository on GitHub (e.g., `shibal-fam-event`)
2. Upload `index.html` to the repository
3. Go to **Settings → Pages**
4. Under "Source", select **main** branch and **/ (root)**
5. Click **Save**
6. Your site will be live at `https://yourusername.github.io/shibal-fam-event/`

## Firebase Security Rules

Your database is in **test mode** (open to everyone) which expires after 30 days. To keep it working, go to **Firebase Console → Realtime Database → Rules** and set:

```json
{
  "rules": {
    "bracket": {
      ".read": true,
      ".write": true
    }
  }
}
```

This allows anyone to read (for real-time viewing) and write (for admin updates). Since admin access is controlled by the secret URL key, this is fine for a small event.

## Features

- ✅ Double elimination bracket (Winners → Losers → Grand Finals)
- ✅ Real-time sync via Firebase (viewers see updates instantly)
- ✅ Admin mode via secret URL parameter
- ✅ Click-to-select winners (admin only)
- ✅ Undo match results (cascades to downstream matches)
- ✅ Reset entire bracket
- ✅ Champion banner when Grand Finals is decided
- ✅ All-Star Showcase match section
- ✅ Esports-style dark theme
- ✅ Mobile responsive

## Bracket Structure

```
Winners Bracket:
  Match 1: Team A vs Team D
  Match 2: Team B vs Team C
  Match 3 (WB Finals): Winner M1 vs Winner M2

Losers Bracket:
  Match 4: Loser M1 vs Loser M2
  Match 5 (LB Finals): Winner M4 vs Loser M3

Grand Finals:
  Match 6: WB Champion vs LB Champion

All-Star Showcase:
  Top 3 scorers vs Remaining players
```

## Teams

| Team | Players |
|------|---------|
| Team A | miyaw, Aesui, Miaoyi |
| Team B | awii, deiin, Leandree |
| Team C | Gundina, nescafe, svn |
| Team D | zyrk, Kny, lykkie |
