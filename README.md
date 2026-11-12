# btvinh0409.github.io

Developer site, built by GitHub Pages with Jekyll (no build step needed on your machine).

```
index.html            home: intro, apps, principles, contact
<app-id>/index.html   one page per app (3 lines of front matter)
_data/apps.yml        every app's text, links, features and screenshots
_layouts/             default.html (header, footer, contact) · app.html (app page)
_includes/            app-card.html (big dark card) · app-tile.html (small card) · icon.html
assets/css/site.css   shared styles, Vale v2 tokens (light + dark)
assets/img/<app-id>/  icon.png + screenshots per app
app-ads.txt           AdMob, one file for every app — leave at the root
```

## Add a new app

1. **Images** → `assets/img/<app-id>/`
   - `icon.png` — 256 × 256, from the 1024 App Store icon
   - screenshots — raw simulator captures resized to 1100 px tall, JPEG:
     ```bash
     sips -s format jpeg -s formatOptions 82 -Z 1100 raw.png --out assets/img/<app-id>/today.jpg
     ```
2. **Data** → add an entry to `_data/apps.yml` (copy the Vale one):
   - `id`, `name`, `short_name`, `category`, `tagline`, `description`
   - `app_store_id`, `app_store_url` (leave out and set `status: soon` before launch)
   - `privacy_url` — e.g. `/<app-id>/privacy.html`
   - `chips`, `hero_shots` (1 or 2 files), `features` (icon · tone · title · text), `screenshots`
   - optional `theme` (`hero`, `hero_sub`, `hero_chip`, `action`, `on_action`) for the dark card's colors
   - `featured: true` makes it the big card on the home page; others show as small cards
   - Feature icons: see the `when` list in `_includes/icon.html`; tones: `coral`, `mint`, `leaf`, `lav`
3. **Page** → `<app-id>/index.html`:
   ```
   ---
   layout: app
   app: <app-id>
   ---
   ```
   Anything you write below the front matter appears after the screenshots.
4. **Privacy policy** → `<app-id>/privacy.html` (plain HTML or Markdown with `layout: default`).
5. In App Store Connect set the app's **Marketing URL** to `https://btvinh0409.github.io/<app-id>/` so `app-ads.txt` applies to it.

## Preview locally (optional)

```bash
gem install jekyll && jekyll serve
```
Then open http://localhost:4000.
