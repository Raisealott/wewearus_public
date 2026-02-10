# Publishing the We Wear Us site

## 1. GitHub (save and version the code)

1. Create a new repo at [github.com/new](https://github.com/new) (e.g. `we-wear-us-website`). Don’t add a README (you already have files).
2. In your project folder, run:

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/we-wear-us-website.git
   git push -u origin main
   ```

   Replace `YOUR_USERNAME` and the repo name with yours.

## 2. Vercel (host the site)

1. Go to [vercel.com](https://vercel.com) and sign in (GitHub is fine).
2. **Add New Project** → **Import** your GitHub repo (`we-wear-us-website`).
3. Leave **Framework Preset** as “Other” (or “Vite” doesn’t matter for static).
4. **Root Directory:** leave as `.` (repo root).
5. **Build and Output:** this is a static site. Either:
   - Leave **Build Command** empty and **Output Directory** empty; Vercel will serve the root, or
   - Set **Output Directory** to `.` if asked.
6. Click **Deploy**. You’ll get a URL like `we-wear-us-website.vercel.app`.

Vercel will redeploy automatically on every `git push` to `main`.

## 3. Porkbun (use your domain)

1. In **Vercel:** Project → **Settings** → **Domains** → add your domain (e.g. `wewearus.shop` or `www.wewearus.shop`).
2. Vercel will show the DNS records you need.
3. In **Porkbun:** [Porkbun DNS](https://porkbun.com/account/domains) → select your domain → **DNS** / **Edit DNS**.
4. Add the record Vercel asks for:
   - For **apex** (`wewearus.shop`): add an **A** record: name `@`, value `76.76.21.21` (Vercel’s IP; confirm in Vercel’s UI).
   - For **www** (`www.wewearus.shop`): add a **CNAME**: name `www`, value `cname.vercel-dns.com` (or what Vercel shows).
5. Save. DNS can take a few minutes to a few hours to update.
6. In Vercel, add the other variant if you want (e.g. both `wewearus.shop` and `www.wewearus.shop`) and set the one you prefer as primary.

You don’t need Supabase for this site unless you add something that needs a database or auth later.
