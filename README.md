# Swipe Right On Me

A joke dating app where every card is you.

This project is static-first for GitHub Pages (HTML/CSS/JS), with optional
Supabase storage for:

- Swipe event tracking
- Instagram handle submissions (with optional message)

## 1) Add your photos

Put your images in `images/` and update `profiles.js`.

Example profile entry:

```js
{
  id: "me-001",
  name: "You",
  bio: "Your one-liner",
  photo: "./images/me-1.jpg",
}
```

## 2) Set up Supabase

1. Create a Supabase project.
2. Open SQL Editor and run `supabase/schema.sql`.
3. Go to `Project Settings -> API` and copy:
   - Project URL
   - anon public key
4. Put values in `config.js`:

```js
export const APP_CONFIG = {
  supabaseUrl: "https://YOUR_PROJECT_ID.supabase.co",
  supabaseAnonKey: "YOUR_SUPABASE_ANON_KEY",
};
```

Without config, the app still runs visually but storage calls are disabled.

## 3) Run locally

Serve with any static server (for module imports):

```bash
python3 -m http.server 8080
```

Then visit `http://localhost:8080`.

## 4) Deploy to GitHub Pages

1. Push this folder to a GitHub repo.
2. Repo Settings -> Pages.
3. Source: `Deploy from a branch`.
4. Branch: `main`, folder: `/ (root)`.
5. Save.

After deploy, your site is live at
`https://<your-username>.github.io/<repo-name>/`.

## Notes on spam and privacy

- A honeypot field and cooldown are included client-side, but this is not full
  bot protection.
- For stronger protection, add Cloudflare Turnstile or hCaptcha and validate
  token server-side (Cloudflare Worker / Supabase Edge Function).
- Keep in mind GitHub Pages is public. Do not commit private content.
