# Fur Family Cinema - Project Notes

## What This Is

Single-page website for Fur Family Cinema, a pet boarding/daycare/spa/boutique in Lewiston, ID. Built in a lovingly restored movie theater (the former Orchards Cinema). The site leans hard into the cinema theme — curtain animations, ticket stubs, marquee lights, movie poster carousel.

## Client

Fur Family Cinema LLC
3323 10th St., Lewiston, ID 83501
Phone: (208) 413-9647
Text: (833) 978-2881
Email: info@furfamilycinema.com

## Tech Stack

- **Site**: Single `index.html` file (~80KB), fully self-contained HTML/CSS/JS
- **Hosting**: Railway (auto-deploys from GitHub)
- **Live URL**: https://furfamilycinema-site-production.up.railway.app/
- **Container**: Dockerfile serves static files via Nginx
- **Analytics**: Plausible (privacy-focused, no cookies, no consent banner)
- **Fonts**: Google Fonts — Playfair Display, Inter, Bebas Neue
- **No build step**: Everything is vanilla, no frameworks, no bundler

## Design System

- **Theme**: Dark cinema aesthetic, deep purple/navy backgrounds
- **Primary accent**: Teal (`#3CBCB4` / `--gold`)
- **Secondary accent**: Light teal (`#5CE0D8` / `--neon-blue`)
- **Deep purple**: `#2D1065`
- **Dark background**: `#110833`
- **Card background**: `#1a0e40`
- **Text**: Warm cream (`#f0e6d3`)
- **Typography**: Playfair Display for headings, Inter for body, Bebas Neue for labels

## Site Sections

1. **Hero** — Curtain open animation, logo, tagline, CTA buttons
2. **Services** — Boarding, daycare, spa, self-wash, boutique (cinema-themed cards)
3. **Spa Menu** — Detailed grooming/spa service cards
4. **Pricing** — Rate tables styled as movie tickets
5. **Origin Story** ("About") — Company history, press links
6. **Hours & Location** — Business hours, contact info, Google Maps link
7. **Health Requirements** — Vaccination and policy info
8. **FAQ** — Accordion-style Q&A
9. **Jobs** — Employment info
10. **Footer** — Social links (Facebook, Instagram, Yelp), contact info

## Key Features

- **Curtain animation**: Purple curtains open on page load (3s), then removed from DOM
- **Scroll reveal**: Sections fade in via IntersectionObserver (`.reveal` class)
- **Sticky nav**: Locks to top on scroll with backdrop blur
- **Mobile responsive**: Hamburger menu, stacked grid layouts
- **Movie poster carousel**: Showcases services as movie posters
- **Booking links**: Point to Gingr booking system

## External Links & Services

- **Booking**: Gingr (online booking platform for pet care)
- **Analytics**: Plausible — https://plausible.io (paid account, $9/mo)
- **Social**: Facebook, Instagram, Yelp
- **Maps**: Google Maps embed (needs API key for interactive map — currently links only)

## Press Coverage (linked in Origin Story)

- Lewiston Tribune: "Pet day care is former dollar theater's next feature"
- Lewiston Tribune: "Giving pets the star treatment"
- Big Country News Connection: "Sunday Small Business Spotlight: Fur Family Cinema"

## SEO & Sharing

- Full Open Graph tags (Facebook/iMessage/LinkedIn)
- Twitter Card tags
- JSON-LD structured data (LocalBusiness schema with hours, services, rating, geo)
- Custom OG image (`og-image.png`) — dark purple background, logo, teal accent
- Meta description, keywords, canonical URL
- Plausible analytics (cookie-free)

## Accessibility

- Skip-to-content link for keyboard users
- `<main>` landmark element
- `rel="noopener noreferrer"` on all external links

## Files

```
index.html          — The entire site
logo.png            — Logo (used in nav, hero, OG)
og-image.png        — Social share image (generated, dark purple + logo + teal accent)
Dockerfile          — Nginx container for Railway
NOTES.md            — This file
```

## Pending / Future Work

- [ ] Custom domain setup (furfamilycinema.com) — needs DNS pointing + Railway config
- [ ] Google Maps API key for interactive embedded map
- [ ] Google Business Profile optimization
- [ ] Photo gallery with real facility photos
- [ ] Customer testimonials section
- [ ] Seasonal promotions / holiday boarding specials

## Known Quirks

- The curtain animation + scroll reveal combo doesn't play well with headless/automated browsers (IntersectionObserver doesn't fire). Site works perfectly in normal browsers.
- iMessage/Facebook cache OG images aggressively — new shares pick up changes immediately, but previously shared links take time to refresh.

## Developer

KD70 (brian@kd70.com)
