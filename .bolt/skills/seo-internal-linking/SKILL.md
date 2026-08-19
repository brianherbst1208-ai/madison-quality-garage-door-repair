---
name: seo-internal-linking
description: Audit and improve internal linking for SEO on multi-page static websites. Use whenever the user asks about internal links, SEO links, linking strategy, orphan pages, link equity, or whether pages are properly linked together. Also use when the user asks "are there any internal links you recommend for SEO?" or similar. Covers link audits, finding orphan pages, identifying under-linked high-value pages, and adding contextual in-body links from authoritative pages.
---

# SEO Internal Linking

Internal links are links from one page on a site to another page on the same site. They help search engines discover pages, understand site structure, and pass authority from strong pages to pages that need it. This skill covers auditing an existing site's internal links and fixing the most impactful gaps.

## When to use this skill

Use whenever the user asks about internal linking for SEO purposes, including questions like:

- "Are there any internal links you recommend for SEO?"
- "Can you improve our internal linking?"
- "Do we have any orphan pages?"
- "Should we link from the homepage to our location/service pages?"

Also use proactively when building or reviewing a multi-page site with service pages, location/city pages, or any hub-and-spoke content structure.

## The audit

Before recommending changes, understand the current linking structure. For a static HTML site:

1. **Read every HTML file** and extract all internal links (href values pointing to other .html pages on the same site, not external URLs, not same-page anchors like `#`).

2. **Distinguish structural links from contextual links.** Most sites have repeated header navigation and footer links that appear on every page. These are structural. The links that matter most for SEO are **contextual in-body links** — links embedded in page content that pass topical relevance and authority from one page to another.

3. **Build an inbound link count for each page** — how many other pages link TO it. Pages with low inbound counts, especially high-value pages like city/location landing pages or service pages, are the priority targets.

## What to look for

### High-priority issues

- **Homepage not linking to key pages.** The homepage is typically the most authoritative page on a site. If it doesn't link to location/city pages, service pages, or other high-value landing pages, those pages miss out on the strongest source of link equity. This is the single most common and highest-impact gap.

- **Orphan pages** — pages that no other page links to. These are unreachable through internal links and may not be discovered by search engines. Either link to them or remove them if unused.

- **High-value pages with only footer links.** Pages like FAQ, blog posts, or resource pages that are only linked from the footer get minimal SEO value. They need at least one contextual in-body link from a relevant content page.

- **City names in body copy that aren't hyperlinked.** If a page mentions city names or service areas in its text but doesn't link those mentions to the corresponding location pages, that's a missed opportunity for both users and search engines.

### Lower-priority issues

- **Self-referential links** — a page linking to itself in a "related services" or "our services" list. These pass no link equity and add no value. Remove them.

- **Missing cross-links between related services.** Service pages should link to related service pages (e.g., spring repair links to cable repair) so users and search engines can navigate between them.

- **Hub pages not linking to their children.** If there's a services overview page or a service-areas hub page, it should link to every individual service or location page beneath it.

## How to fix

### 1. Link the homepage to all key pages

Turn city names and service names in the homepage body copy into clickable links to their respective pages. Also consider adding a grid of location cards or a service linklist to the homepage, each card linking to the corresponding page.

Example — before:
```html
<p>We proudly serve Madison, Sun Prairie, Verona, and nearby communities.</p>
```

After:
```html
<p>We proudly serve <a href="garage-door-repair-in-madison.html">Madison</a>,
<a href="garage-door-repair-in-sun-prairie.html">Sun Prairie</a>,
<a href="garage-door-repair-in-verona.html">Verona</a>, and nearby communities.</p>
```

### 2. Add contextual links to footer-only pages

If a page like FAQ is only linked from the footer, add at least one in-body link from a relevant page. For example, if the homepage has an FAQ section, add a "See more questions" link at the bottom pointing to the full FAQ page.

### 3. Connect orphan pages

For pages like thank-you pages that exist but aren't linked from anywhere:
- If it's a form-confirmation page, add it as the form's redirect destination (e.g., a hidden `_next` field for Formspree forms).
- If it's genuinely unused, remove it rather than leaving it orphaned.

### 4. Remove self-links

On each service page's "related services" or "our services" linklist, remove the link to the current page itself. Keep the cross-links to the other services intact. Be careful not to remove the page's link from the header navigation dropdown — only remove it from the in-body linklist.

## Verification

After making changes:

1. Rebuild the site (run `npm run build` or equivalent).
2. Verify that the homepage now links to all key pages by grepping for the expected hrefs in the built output.
3. Verify that no nav dropdown links were accidentally removed — each service page's dropdown should still contain all service links.
4. Verify that linklists have the correct number of items (original count minus one for the removed self-link).
5. Confirm the build completes without errors.

## Key principles

- **The homepage is the strongest page.** Links from it carry the most weight. Prioritize adding homepage links to your most important target pages.
- **Contextual links beat navigation links.** A link embedded in body copy surrounded by relevant text passes more topical relevance than a link in a footer or nav bar.
- **Use descriptive anchor text.** "Madison garage door repair" as link text is better for SEO than "click here" or "learn more."
- **Every page should be reachable.** No orphan pages. If a page exists, at least one other page should link to it.
- **Bidirectional linking.** If a service page links to a location page, the location page should link back to the service page. Hub pages should link to their children, and children should link back to the hub.
