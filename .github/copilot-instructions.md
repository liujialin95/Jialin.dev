# Copilot Instructions — Jialin.dev

## Project overview

Personal portfolio/CV site for Jialin Liu, a D365FO (Dynamics 365 Finance & Operations) technical consultant. Built on the [Styleshout "Hola" template](https://www.styleshout.com/). Deployed to GitHub Pages at `jialin.dev` (CNAME).

**No build system.** Pure static HTML/CSS/JS — edit files directly. The only server-side component is `inc/sendEmail.php` (contact form), which requires a PHP host to function.

## File structure

| Path | Purpose |
|------|---------|
| `index.html` | Main single-page site (Home → About → Contact) |
| `css/main.css` | Primary stylesheet — has a TOC at the top, use it to navigate |
| `css/base.css` | Reset/base styles |
| `css/vendor.css` | Third-party CSS bundled together |
| `js/main.js` | All custom JS behaviour (jQuery-wrapped IIFE) |
| `js/plugins.js` | Bundled third-party JS plugins |
| `inc/sendEmail.php` | Contact form email handler |
| `images/` | Hero, avatars — see conventions below |

## Color palette

| Role | Name | HEX |
|------|------|-----|
| Background | Cream white | `#F7F3ED` |
| Body text | Warm black | `#2C2C2C` |
| Headings | Deep black | `#111111` |
| Links/accents | Deep coffee | `#6B4F4F` |
| Link hover | Muted mauve | `#8C6E6E` |
| Dividers/borders | Light brown-gray | `#E5DED6` |

- Hero (`#home`) and Contact (`#contact`) sections keep dark overlays over background images — do not remove these overlays.
- On the hero overlay, use `#E5DED6` for accent elements (h3 line, scroll arrow, social label) so they remain readable against the dark background.

## Key conventions

### Page sections
- Sections: `#home`, `#about`, `#contact` (Works and Blog sections have been removed).
- Each section has `id="..."` matching its nav `href`.
- Sections that should trigger nav highlighting need the class `target-section` so Waypoints can track them.

### Skill bars
Use the `.progress.percentXX` pattern:
```html
<div class="progress percent85"><span>85%</span></div>
<strong>Skill Name</strong>
```
Valid values in use: `percent65`, `percent70`, `percent75`, `percent80`, `percent85`, `percent100`.

### Timeline entries
```html
<div class="timeline__block">
    <div class="timeline__bullet"></div>
    <div class="timeline__header">
        <p class="timeline__timeframe">Month YYYY - Month YYYY</p>
        <h3>Company Name</h3>
        <h5>Role Title</h5>
    </div>
    <div class="timeline__desc"><p>...</p></div>
</div>
```

### Smooth scrolling
Add class `smoothscroll` to any anchor pointing at an on-page `#id` — `main.js` handles the animation.

### CSS organisation
`css/main.css` is structured by component with `#` comment headers. Each logical section has a TOC entry at the top of the file — match new styles to the nearest existing section rather than appending at the end.

## Social links
Footer and home social links: **Instagram** and **LinkedIn** only. Facebook and Twitter have been removed.

## Attribution requirement
Per the template license (`readme.txt`), the Styleshout credit link in the footer **must not be removed** unless the one-time attribution removal fee has been paid.

## Contact form
`inc/sendEmail.php` POSTs to `liujialin95@gmail.com`. The PHP `mail()` function requires a server-side PHP host — this does **not** work on vanilla GitHub Pages. If deploying purely to GitHub Pages, the contact form will silently fail unless proxied through a service like Formspree or a separate backend.
