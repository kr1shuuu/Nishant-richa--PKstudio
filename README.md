# Raj Ki Richa · Wedding Invitation

An interactive, single-file digital wedding invitation for **Dr Nishant Raj & Dr Richa Sirmaur** — *Shubh Vivah*, Monday 7 December 2026, ISKCON Rohini, New Delhi.  
`#RajKiRicha`

Open the page, tap the pearl bow to unseal the envelope, and scroll through the story, events, venue, blessings and RSVP — all in one self-contained HTML file with no build step.

## Features

- **Envelope opening** — a navy-and-gold envelope with a pearl bow; tap the bow (or the *Tap to Open* button) to reveal the invitation
- **Ambient effects** — falling petals and leaves, rising pearl bubbles, twinkling particles and pearl bursts, all drawn on canvas/DOM
- **Save-the-date reveal** — tap the *N & R* monogram to reveal the date and start a live countdown (days / hours / minutes / seconds)
- **Scratch-to-reveal card** — scratch the golden heart to uncover the date
- **Meet the couple** — portraits and short introductions of the groom and bride
- **Festivities timeline** — Matkor & Haldi Kalash, Ghritdhari, Shubh Vivah, and the Welcome Ceremony & Reception, each with **Add to Calendar** (Google Calendar link and downloadable `.ics`)
- **Venue & maps** — *Open in Maps* and *Get Directions* links for ISKCON Rohini
- **Guest notes and gift note** — travel and registry information
- **Blessings wall** — guests can leave a wish and give hearts to others' blessings
- **Five-step RSVP** — Response → Events → Guests → Details → Blessing
- **Background music** — *Rang Lageya* (Mohit Chauhan & Rochak Kohli) with a play/pause toggle and a YouTube fallback link
- **Mobile-first and accessible** — responsive layout, ARIA labels on interactive controls, and `prefers-reduced-motion` support

## Quick start

No install or build is needed.

```bash
git clone <your-repo-url>
cd <your-repo>
# open the file directly in a browser
open wedding-invitation-public.html      # macOS
xdg-open wedding-invitation-public.html  # Linux
start wedding-invitation-public.html     # Windows
```

Or serve it locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/wedding-invitation-public.html
```

## Deploy with GitHub Pages

1. Rename `wedding-invitation-public.html` to `index.html` (so the site loads at the root URL).
2. Push to GitHub.
3. Go to **Settings → Pages**, choose your branch and the `/ (root)` folder, and save.
4. Your invitation will be live at `https://<username>.github.io/<repo>/`.

Any static host works as well (Netlify, Vercel, Cloudflare Pages, etc.).

## Project structure

```
.
├── wedding-invitation-public.html   # the entire invitation: HTML, CSS, JS, images and audio
├── assets/
│   └── rang-lageya-chorus.mp3       # optional fallback copy of the music track
└── README.md
```

The images and the music track are embedded in the HTML as base64 data URIs, so the page works as one portable file (about 6 MB). The player falls back to `assets/rang-lageya-chorus.mp3` if the embedded audio fails to load.

## Customising

Everything lives in `wedding-invitation-public.html`. Open it in an editor and search for these:

| What to change | Where to look |
| --- | --- |
| Names, parents' names, bios, section text | the markup between `<body>` and the first `<script>` |
| Wedding date and countdown target | `WEDDING_TARGET` in the script (`new Date("2026-12-07T10:00:00")`) |
| Events, dates, times, venues | the `EVENTS` array in the script |
| Short couple name used in calendar entries | `COUPLE_SHORT` |
| Venue map links | the *Open in Maps* and *Get Directions* `href`s |
| Colours | CSS variables in `:root` (`--bg`, `--gold`, `--ivory`, …) |
| RSVP options and step names | `RSVP_CHOICES` and `STEP_NAMES` |
| Photos | the `<img src="data:image/webp;base64,…">` tags |

**Tip:** the base64 blobs make the file hard to edit by hand. To swap a photo, convert your image to WebP, encode it to base64, and paste it into the matching `<img>` `src`. Alternatively, move the images into `assets/` and reference them by path.

## Fonts

Typography is loaded from Google Fonts: **Great Vibes**, **Playfair Display** and **Cormorant Garamond**. Without a connection, the page falls back to Georgia and a cursive system font.

## Good to know

- **RSVPs and blessings are not saved anywhere.** There is no backend. Submitting the RSVP shows a thank-you message, and blessings appear on the wall only for that visitor's current session; nothing is stored or sent. To collect real responses, connect the form to a service such as Google Forms, Formspree, Supabase or a Google Apps Script web app and post the data from `submitRsvp()`.
- **Share links** — *Post a Story* opens Instagram's story composer; it does not attach a photo.
- **Autoplay** — browsers block audio until the visitor interacts, so music starts when the envelope is opened.

## Browser support

Works in current versions of Chrome, Edge, Safari and Firefox on desktop and mobile.

## Credits

- Design and development: *add your name here*
- Music: *Rang Lageya* by Mohit Chauhan & Rochak Kohli — rights belong to their respective owners. Replace the track with your own licensed or royalty-free audio before sharing the repository widely.
- Fonts: Google Fonts (SIL Open Font License)

## License

*Choose a license (for example MIT) and add a `LICENSE` file, or remove this section if the repository is private or personal.*
