# Engineer Wala Cafe: website (front-end)

Single-page site: plain HTML + CSS + JS, koi build step nahi.

## Chalane ka tareeka
- `index.html` ko seedha browser mein kholo, ya `npx serve .` / VS Code Live Server se chalao.
- Fonts (Alfa Slab One, DM Sans, Space Mono) Google Fonts se aate hain, isliye internet chahiye.

## Folder
- `index.html`: poora page (CSS aur JS isi file mein)
- `assets/cafe-interior.jpg`, `assets/cafe-counter.jpg`: AI concept renders (real photos aane par replace karna)
- `assets/favicon.svg`: cup + `</>` mark

## Database jodna (Antigravity mein)
`index.html` ke script ke shuru mein `DEMO_MODE = true` aur ek `api` object hai. Abhi sab data `localStorage` mein jaata hai.
In functions ko Firebase ya Supabase calls se replace karo, UI code nahi badalna padega:

| Function | Kaam | Table / path suggestion |
|---|---|---|
| `api.getVotes()` / `api.vote(zone)` / `api.getMyVote()` | Location poll | `votes(zone, voter_id, created_at)` |
| `api.createPass({name, phone, role})` / `api.getMyPass()` | VIP pass (ticket number `EWC-0001`) | `passes(id, name, phone, role, created_at)` |
| `api.getCards()` / `api.addCard(card)` | Community wall | `wall_cards(type, name, text, approved, created_at)` |

Production se pehle zaroor karna:
- Duplicate vote / duplicate phone ka server-side check.
- Phone number privacy: sirf zaroorat ho toh save karo, aur database rules lagao.
- Wall cards par moderation (`approved` flag).
- QR placeholder ko asli QR se replace karo (pass number encode karke).
- Domain `engineerwalacafe.in` + Vercel deploy.

## Baaki cheezein
- Prices (`₹99`, `₹1,499 - ₹2,499`) context file ke planned numbers hain.
- Page par "Example card" wale notes sirf demo ke liye hain, hata dena.
