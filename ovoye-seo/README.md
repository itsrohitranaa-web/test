# Ovoye backend SEO update (2026-10-05)

Upload every file in `upload-to-public_html/` to `public_html/` on ovoye.com (hPanel → File Manager), overwriting the existing files. All six files sit at the root of `public_html`.

| File | Change |
|---|---|
| `index.html` | New meta title/description (+ Open Graph / Twitter), Organization + WebSite JSON-LD in `<head>`, alt text on the hero poster and the three portfolio thumbnails |
| `index.txt`, `__next._full.txt`, `__next.__PAGE__.txt` | Same title/description in the Next.js page data, so client-side navigation shows the same values as the HTML |
| `robots.txt` | Explicit `User-agent: Googlebot` group allowing the whole site (the PHP form handlers stay blocked) |
| `sitemap.xml` | `lastmod` on the homepage |

No visible text, layout or styling changed. To roll back, upload the files in `backup-original/` the same way.

After uploading: hPanel → Websites → ovoye.com → Clear cache, then submit `https://ovoye.com/sitemap.xml` in Google Search Console.

Note: these are edits to the built site. If the site is rebuilt from its Next.js source and re-uploaded, the same changes must be made in the source (root `metadata` export / page `metadata`, a JSON-LD `<script>` in the root layout, `alt` props, `app/robots.ts`, `app/sitemap.ts`) or they will be overwritten.
