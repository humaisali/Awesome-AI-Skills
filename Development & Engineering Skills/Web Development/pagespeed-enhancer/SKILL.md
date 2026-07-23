---
name: pagespeed-enhancer
description: "Scan, audit, and fix web performance issues across all four Lighthouse/PageSpeed Insights pillars â€” Performance, Accessibility, Best Practices, and SEO â€” in structured batches."
risk: safe
source: https://github.com/humaisali
date_added: "2026-06-14"
Maintained & Curated by: Humais Ali
---

# PageSpeed Enhancer Skill

A structured, batch-wise audit-and-fix workflow for all four Lighthouse pillars. Always follow the batch flow in order. Never jump straight to fixes without completing the scan and risk assessment phases.

---

## When to Use This Skill

- User pastes a PageSpeed Insights report or mentions Lighthouse scores
- User asks to improve Core Web Vitals (LCP, FCP, CLS, TBT, SI)
- User needs help with render-blocking resources, unused JavaScript, image optimisation, security headers, ARIA compliance, or SEO meta-tag fixes
- User asks "why is my LCP slow", "fix accessibility issues", "improve my SEO score", or "my site scores 80 on performance"
- Any mention of PageSpeed, Lighthouse, Web Vitals, or site speed

---

## High-Level Workflow

```
PHASE 1 â†’ Ingest Report & Parse Scores
PHASE 2 â†’ Batch Scan (4 sections, parallel analysis)
PHASE 3 â†’ Consolidated Risk Report (changes ranked by impact vs risk)
PHASE 4 â†’ Fix Batches (applied in safe order: low-risk â†’ high-risk)
PHASE 5 â†’ Verification Checklist
```

---

## PHASE 1 â€” Ingest & Classify

When the user provides a PageSpeed Insights report (pasted text, screenshot, or URL):

1. Extract the four pillar scores: Performance, Accessibility, Best Practices, SEO.
2. Extract each flagged metric with its value and Lighthouse weight.
3. Identify the **critical path bottleneck** (the single issue most responsible for the lowest pillar score).
4. Output a **Score Summary Table**:

```
| Pillar          | Score | Status  | Critical Issue                      |
|-----------------|-------|---------|-------------------------------------|
| Performance     | 80    | âš ï¸ Warn | LCP 4.0s â€” element render delay     |
| Accessibility   | 100   | âœ… Pass | â€”                                   |
| Best Practices  | 100   | âœ… Pass | CSP missing (unscored)              |
| SEO             | 100   | âœ… Pass | â€”                                   |
```

Then proceed immediately to Phase 2 without waiting for user input unless the report is ambiguous.

---

## PHASE 2 â€” Batch Scan (4 Sections)

Run all four section scans. Present as collapsible sections in output.

### Batch A â€” Performance Scan

Audit these in order (highest Lighthouse weight first):

| Audit | Metric Impact | Key Questions |
|-------|--------------|---------------|
| LCP breakdown | LCP | Is the LCP element lazily loaded? Is TTFB > 600ms? Is element render delay > 1s? |
| Render-blocking resources | FCP, LCP | Which CSS/JS files block the critical path? Can they be deferred or inlined? |
| CSS `@import` rules | FCP, LCP | Are external stylesheets loaded via `@import url()` in CSS? This is **2x render-blocking** â€” browser must fetch CSS, parse it, then fetch imported CSS. Use `<link>` instead. |
| Unused JavaScript | FCP, LCP, TBT | What % of the main bundle is unused? Is code-splitting possible? |
| Network dependency tree | LCP | What is the critical path chain? Max latency? |
| Forced reflows | TBT | Which JS functions query geometry after DOM mutation? |
| Image delivery | FCP, LCP | Are images in WebP/AVIF? Are above-fold images lazy-loaded? |
| Speed Index | SI | Is page visually progressive or does it paint all at once? |
| CLS culprits | CLS | Any images without width/height? Any late-injected content? |
| JavaScript execution time | TBT | Total parse + compile + evaluate time? |
| Long main-thread tasks | TBT | Tasks > 50ms? Starting when? |
| Bundled asset sizes | FCP, LCP, TBT | Check `dist/` output: any single JS chunk > 500KB gzipped? CSS > 100KB? Code-splitting creating proper vendor chunks? |

For each audit item, output:
- **Finding**: What the report says
- **Root Cause**: Why it's happening
- **Fix Category**: Quick Win / Medium Effort / Refactor Required

### Batch B â€” Accessibility Scan

Focus on any failed audits. For a 100-score page, still check:

| Check | What to Verify |
|-------|---------------|
| ARIA attribute correctness | All `aria-*` attributes match element roles |
| Colour contrast | All text meets WCAG AA (4.5:1 normal, 3:1 large) |
| Image alt text quality | Alt text is descriptive, not filename-style |
| Keyboard navigation | All interactive elements reachable by Tab |
| Skip links | Present and focusable |
| Heading hierarchy | No skipped levels (h1 â†’ h2 â†’ h3) |
| Touch target size | Min 44Ã—44px on mobile |
| Form labels | Every input has an associated label |
| `lang` attribute | `<html lang="en">` present and valid BCP 47 |
| `font-display` | Set to `swap` or `optional` to prevent FOIT |

### Batch C â€” Best Practices Scan

Security headers are often unflagged by Lighthouse score but are critical. Check ALL deployment targets:

| Check | Header/Setting | Where to Configure | Severity |
|-------|---------------|-------------------|----------|
| Content Security Policy | `Content-Security-Policy` | `netlify.toml` `[[headers]]` / `vercel.json` `"headers"` | ðŸ”´ High |
| Cross-Origin-Opener-Policy | `COOP` header | Same as above | ðŸ”´ High |
| Clickjacking protection | `X-Frame-Options` or CSP `frame-ancestors` | Same as above | ðŸ”´ High |
| HSTS configuration | `Strict-Transport-Security` with `includeSubDomains` + `preload` | Same as above | ðŸŸ¡ Medium |
| Trusted Types (DOM XSS) | CSP `require-trusted-types-for 'script'` | Same as above | ðŸŸ¡ Medium |
| X-Content-Type-Options | `nosniff` header | Same as above | ðŸŸ¡ Medium |
| Referrer-Policy | `strict-origin-when-cross-origin` | Same as above | ðŸŸ¡ Medium |
| Permissions-Policy | Restrict camera/mic/geolocation | Same as above | ðŸŸ¡ Medium |
| Third-party cookies | Any `SameSite=None` cookies without `Secure`? | â€” | ðŸŸ¡ Medium |
| Deprecated APIs | Any browser-deprecated JS APIs in use? | â€” | ðŸŸ¢ Low |
| Source maps | Are source maps deployed for debugging? | â€” | ðŸŸ¢ Low |

When both `netlify.toml` and `vercel.json` exist, check BOTH. Each has a different syntax (TOML vs JSON).

### Batch D â€” SEO Scan

| Check | What to Verify |
|-------|---------------|
| `<title>` tag | Present, 50â€“60 chars, includes primary keyword |
| Meta description | Present, 150â€“160 chars, compelling |
| Canonical tag | `<link rel="canonical">` points to correct URL |
| hreflang | Present if multilingual; correct language codes |
| robots.txt | Valid, not blocking key resources |
| Structured data | JSON-LD present; run Schema validator |
| Image alt attributes | Every `<img>` has meaningful alt |
| Link descriptiveness | No "click here" / "read more" link text |
| Crawlability | No `noindex` on important pages |
| HTTP status | 200 on main page and critical resources |
| SPA meta injection | If using react-helmet-async / Next.js Head: verify via "View Page Source", not DevTools Elements â€” meta tags may be JS-injected |

---

## PHASE 3 â€” Risk Report

After completing all four batch scans, output a consolidated **Risk vs Impact Matrix**:

```
| Fix                              | Impact Score | Risk Level | Effort   | Priority |
|----------------------------------|-------------|------------|----------|----------|
| Add defer/async to non-critical JS | High (LCP -0.8s est) | ðŸŸ¢ Low | 1h     | P1       |
| Convert images to WebP/AVIF      | Medium (LCP -0.3s)   | ðŸŸ¢ Low | 2h     | P1       |
| Add CSP header                   | Security    | ðŸŸ¡ Medium  | 3h     | P2       |
| Code-split main JS bundle        | High (TBT -20ms)     | ðŸŸ¡ Medium | 1 day | P2       |
| Fix forced reflows               | Medium (TBT -15ms)   | ðŸ”´ High   | 2 days | P3       |
| Add HSTS preload                 | Security    | ðŸŸ¡ Medium  | 30min  | P2       |
```

**Risk Level Definitions:**
- ðŸŸ¢ Low: Config/header change, no code change. Rollback in < 5 min.
- ðŸŸ¡ Medium: Build config or asset pipeline change. Test in staging first.
- ðŸ”´ High: JavaScript refactor, architectural change. Requires full QA cycle.

Always recommend: fix P1 (Low Risk, High Impact) items first, then P2, then P3.

---

## PHASE 4 â€” Fix Batches

Apply fixes in risk order. For each fix, provide:

1. **What to change** â€” file, line, specific change
2. **Before** (code snippet)
3. **After** (code snippet)
4. **Expected metric improvement** â€” estimated delta
5. **How to verify** â€” what to check after deploying

### Fix Batch 1 â€” Quick Wins (Low Risk, deploy immediately)

Examples from common audits:

**F1.1 â€” Move CSS `@import` to `<link>` tag**

CSS `@import url()` is 2x render-blocking. Move to `<link>` in `<head>`:

```css
/* Before: in index.css */
@import url('https://fonts.googleapis.com/css2?family=Inter&display=swap');
```

```html
<!-- After: in index.html <head> -->
<link rel="preload" as="style" href="https://fonts.googleapis.com/css2?family=Inter&display=swap" />
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter&display=swap" media="print" onload="this.media='all'" />
<noscript><link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter&display=swap" /></noscript>
```

**F1.2 â€” Defer render-blocking CSS (if not above-fold critical)**
```html
<!-- Before -->
<link rel="stylesheet" href="/assets/index.css">

<!-- After: load async, apply on load -->
<link rel="preload" href="/assets/index.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="/assets/index.css"></noscript>
```

**F1.3 â€” Fix broken preconnect (crossorigin mismatch)**
```html
<!-- Before (broken â€” no crossorigin on font CDN) -->
<link rel="preconnect" href="https://api.rss2json.com">

<!-- After -->
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<!-- Only preconnect origins used in critical path, max 4 -->
```

**F1.4 â€” Convert images to WebP**
```bash
# Using cwebp
cwebp -q 80 input.jpeg -o output.webp

# Using sharp (Node.js)
sharp('image.jpeg').webp({ quality: 80 }).toFile('image.webp')

# macOS fallback (sips built-in)
sips -s format webp input.jpeg --out output.webp

# Python Pillow fallback
python3 -c "
from PIL import Image
Image.open('input.jpg').save('output.webp', 'WebP', quality=80)
"
```

**F1.5 â€” Add explicit image dimensions (CLS fix)**
```html
<!-- Before -->
<img src="hero.webp" alt="...">

<!-- After -->
<img src="hero.webp" alt="..." width="800" height="400">
```

**F1.6 â€” Add security headers (netlify.toml)**
```toml
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Strict-Transport-Security = "max-age=31536000; includeSubDomains; preload"
    Cross-Origin-Opener-Policy = "same-origin"
    Permissions-Policy = "camera=(), microphone=(), geolocation=()"
    Content-Security-Policy = "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src https://fonts.gstatic.com; img-src 'self' data:; connect-src 'self' https://api.rss2json.com"
```

**F1.7 â€” Add security headers (vercel.json)**
```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        { "key": "X-Frame-Options", "value": "DENY" },
        { "key": "X-Content-Type-Options", "value": "nosniff" },
        { "key": "Referrer-Policy", "value": "strict-origin-when-cross-origin" },
        { "key": "Strict-Transport-Security", "value": "max-age=31536000; includeSubDomains; preload" },
        { "key": "Cross-Origin-Opener-Policy", "value": "same-origin" },
        { "key": "Permissions-Policy", "value": "camera=(), microphone=(), geolocation=()" },
        { "key": "Content-Security-Policy", "value": "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src https://fonts.gstatic.com; img-src 'self' data:; connect-src 'self' https://api.rss2json.com" }
      ]
    }
  ]
}
```

**F1.8 â€” Self-host Google Fonts (eliminate external CSS request)**

Download woff2 files and serve them locally to remove the Google Fonts CSS round-trip entirely:

```bash
# 1. Download woff2 files from Google Fonts CSS URL
#    Open https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap
#    in a browser, then download each woff2 URL listed in the @font-face blocks.

# 2. Place files in public/fonts/ or src/assets/fonts/
public/fonts/
  inter-v12-latin-400.woff2
  inter-v12-latin-700.woff2

# 3. Add @font-face CSS (load once, no external request)
```

```css
/* src/styles/fonts.css */
@font-face {
  font-family: 'Inter';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url('/fonts/inter-v12-latin-400.woff2') format('woff2');
}

@font-face {
  font-family: 'Inter';
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: url('/fonts/inter-v12-latin-700.woff2') format('woff2');
}
```

```css
/* Remove the old Google Fonts <link> from index.html */
/* Before: */
<link href="https://fonts.googleapis.com/css2?family=Inter&display=swap" rel="stylesheet">

/* After: just use the font-family normally */
body { font-family: 'Inter', sans-serif; }
```

**Result:** Zero external CSS requests, faster FCP/LCP, no FOIT risk, and works offline.

**F1.9 â€” Resize oversized icons**

Icons (favicon, apple-touch-icon, OG image) should never be > 50KB. Check and resize:
```bash
python3 -c "
from PIL import Image
img = Image.open('favicon.png')
img.resize((192, 192)).save('favicon.png', 'PNG', optimize=True)
img.resize((32, 32)).save('favicon-32x32.png', 'PNG', optimize=True)
img.resize((16, 16)).save('favicon-16x16.png', 'PNG', optimize=True)
"
```

### Fix Batch 2 â€” Medium Effort (staging test recommended)

**F2.1 â€” Remove LCP element lazy loading**

The LCP element must NEVER be lazy-loaded:
```html
<!-- Before: wrong â€” LCP image is lazy -->
<img src="hero.webp" loading="lazy" ...>

<!-- After: eager load the above-fold LCP element -->
<img src="hero.webp" loading="eager" fetchpriority="high" ...>
```

**F2.2 â€” Preload LCP image**

âš ï¸ Only works for files in `public/` or with stable URLs. If using Vite/Webpack (content-hashed filenames), use `<picture>` + `fetchPriority="high"` instead:
```html
<!-- For stable URLs (public/ directory): -->
<link rel="preload" as="image" href="/hero.webp" fetchpriority="high">

<!-- For hashed filenames (Vite/Rollup): use component-level approach -->
<picture>
  <source srcSet={webpImage} type="image/webp" />
  <img src={jpgImage} fetchPriority="high" loading="eager" width="1920" height="1080" />
</picture>
```

**F2.3 â€” Reduce unused JS (Vite/Rollup config)**
```js
// vite.config.js â€” enable manual chunking
build: {
  rollupOptions: {
    output: {
      manualChunks: {
        vendor: ['react', 'react-dom'],
        rss: ['rss-parser'],
      }
    }
  }
}
```

**F2.4 â€” Eliminate forced reflows**
```js
// Before: reads layout property inside animation loop
element.addEventListener('scroll', () => {
  const h = element.offsetHeight; // triggers reflow
  doSomething(h);
});

// After: cache geometry reads outside event handlers
const h = element.offsetHeight; // read once
element.addEventListener('scroll', () => {
  doSomething(h);
});
```

**F2.5 â€” Optimise DOM size**

If DOM > 1,500 elements:
- Use virtual scrolling for long lists (react-virtual, TanStack Virtual)
- Lazy-render off-screen sections
- Remove hidden/display:none nodes that never become visible

### Fix Batch 3 â€” Refactor Required (full QA cycle)

**F3.1 â€” External API in critical path (e.g. api.rss2json.com)**

Current: HTML â†’ JS bundle â†’ external API (adds 1,574ms to critical path)

Solution: Move external API calls to build time or server-side:
```js
// Option A: Fetch at build time (Astro/Next.js SSG)
export async function getStaticProps() {
  const res = await fetch('https://api.rss2json.com/v1/api.json?rss_url=...');
  const data = await res.json();
  return { props: { posts: data.items }, revalidate: 3600 };
}

// Option B: Edge function / serverless proxy
// Cache RSS response at CDN edge, return stale-while-revalidate
```

**F3.2 â€” Content Security Policy (full CSP)**

Build the CSP iteratively:
1. Deploy in report-only mode first: `Content-Security-Policy-Report-Only`
2. Check browser console for violations for 48h
3. Whitelist required origins
4. Promote to enforcement mode

---

## PRE-DEPLOY GATE

Before deploying any fix batch, run these checks:

```
Build:
â–¡ npm run build (or equivalent) â€” exits 0
â–¡ npm run lint / typecheck â€” no new errors vs baseline
â–¡ Inspect dist/ output:
   - No single JS chunk > 500KB (gzipped)
   - CSS < 100KB
   - Code-splitting created separate vendor chunks

Asset verification:
â–¡ For Vite/Rollup/Webpack: preload <link> in index.html won't match hashed filenames.
  Use fetchPriority="high" + <picture> on the component instead.
â–¡ Favicons and icons are < 50KB each (not multi-MB source images used as icons)
â–¡ WebP/AVIF versions exist alongside originals

Deploy target:
â–¡ If dual-deployed (Netlify + Vercel), verify headers on BOTH
â–¡ If using SPA framework: verify meta tags via "View Page Source", not DevTools Elements
  (react-helmet-async injects at runtime â€” check prerendered/SSR output)
```

---

## PHASE 5 â€” Verification Checklist

After deploying each fix batch, verify:

```
Performance:
â–¡ Re-run PageSpeed Insights on mobile AND desktop
â–¡ LCP < 2.5s (Good)
â–¡ FCP < 1.8s (Good)
â–¡ TBT < 200ms (Good)
â–¡ CLS < 0.1 (Good)
â–¡ SI < 3.4s (Good)

Accessibility:
â–¡ Run axe DevTools browser extension
â–¡ Navigate page with keyboard only (Tab, Shift+Tab, Enter, Space)
â–¡ Test with screen reader (NVDA/VoiceOver)
â–¡ Check contrast with browser DevTools accessibility panel

Best Practices:
â–¡ Verify security headers at https://securityheaders.com
â–¡ Check HTTPS: no mixed content warnings in DevTools
â–¡ Run Lighthouse Best Practices audit again

SEO:
â–¡ Validate structured data at https://search.google.com/test/rich-results
â–¡ Check robots.txt at /robots.txt
â–¡ Verify canonical tag in page source (View Source, not DevTools)
â–¡ Submit updated sitemap to Google Search Console
```

---

## Output Format Conventions

- Always label outputs: **[SCAN]**, **[RISK]**, **[FIX]**, **[VERIFY]**
- Use emoji severity indicators: ðŸ”´ Critical / ðŸŸ¡ Warning / ðŸŸ¢ Pass / â„¹ï¸ Info
- Always show "Before" and "After" code for every fix
- Always include estimated metric delta (e.g. "Est. LCP improvement: -0.8s")
- Never suggest fixes that conflict with each other â€” sequence matters

---

## Quick Reference: Metric Thresholds

| Metric | Good | Needs Work | Poor |
|--------|------|-----------|------|
| FCP | < 1.8s | 1.8â€“3.0s | > 3.0s |
| LCP | < 2.5s | 2.5â€“4.0s | > 4.0s |
| TBT | < 200ms | 200â€“600ms | > 600ms |
| CLS | < 0.1 | 0.1â€“0.25 | > 0.25 |
| SI | < 3.4s | 3.4â€“5.8s | > 5.8s |

---

## Examples

### Example 1: User pastes a PageSpeed report

**User:** "My site scores 65 on Performance. LCP is 4.2s."

**Agent:**
1. Parses the score summary table â€” identifies LCP as critical bottleneck
2. Runs Batch A scan â€” finds lazy-loaded hero image and render-blocking CSS
3. Outputs risk report: F1.1 (CSS @import â†’ link) ranked P1, F1.5 (LCP image eager) ranked P1
4. Applies Fix Batch 1, verifies with re-test

### Example 2: User asks about slow LCP

**User:** "Why is my LCP slow?"

**Agent:**
1. Asks for a PageSpeed report URL or pasted results
2. Runs LCP-specific audit from Batch A â€” checks TTFB, element render delay, lazy loading
3. Identifies the LCP element, its current loading strategy, and the critical path chain
4. Recommends targeted fix (preload, eager loading, or server response time improvement)

---

## Limitations

- Does not run actual Lighthouse or PageSpeed tests â€” the user must provide the report or URL
- Security header recommendations assume the user controls the deployment platform (Netlify, Vercel, etc.)
- Fixes are general patterns; exact file paths and config syntax may vary by project setup
- Does not cover server-level optimisations (CDN config, PHP opcode caching, database queries, etc.)
- Image conversion commands assume the user has the required tools installed (cwebp, sharp, Pillow)
- CSP guidance uses a report-only iterative approach â€” the final policy must be tuned to each project's actual resource origins

---

## Change Log & Revert Checklist

After each fix batch, log what changed and whether it caused build failures:

| Fix | File(s) Modified | Build Pass? | Errors | Revert Steps |
|-----|-----------------|-------------|--------|-------------|
| F1.1 â€” CSS @import â†’ `<link>` | `index.html`, `src/styles/*.css` | â–¡ Yes â–¡ No | | Restore original `<link>` tags |
| F1.2 â€” Defer render-blocking CSS | `index.html` | â–¡ Yes â–¡ No | | Remove `media="print"` + `onload` |
| F1.4 â€” WebP conversion | `public/images/*.webp` | â–¡ Yes â–¡ No | | Delete .webp files, restore originals |
| F1.5 â€” Image dimensions | `src/components/*.tsx` | â–¡ Yes â–¡ No | | Remove `width`/`height`/`loading` attrs |
| F1.6 â€” Security headers (Netlify) | `netlify.toml` | â–¡ Yes â–¡ No | | Delete the `[[headers]]` block |
| F1.7 â€” Security headers (Vercel) | `vercel.json` | â–¡ Yes â–¡ No | | Remove the `"headers"` array entry |
| F1.8 â€” Self-host fonts | `public/fonts/*.woff2`, `src/styles/fonts.css`, `index.html` | â–¡ Yes â–¡ No | | Delete font files, remove `@font-face`, restore Google Fonts `<link>` |
| F1.9 â€” Resize icons | `public/favicon*`, `public/apple-touch-icon*`, `public/og-image*` | â–¡ Yes â–¡ No | | Restore original icon files |
| F2.1 â€” LCP eager loading | `src/components/*.tsx` | â–¡ Yes â–¡ No | | Change `loading="eager"` back to `loading="lazy"` |
| F2.2 â€” Preload LCP image | `index.html` or `src/components/*.tsx` | â–¡ Yes â–¡ No | | Remove `<link rel="preload">` or revert `<picture>` |
| F2.3 â€” Code-split JS | `vite.config.ts` | â–¡ Yes â–¡ No | | Remove `manualChunks` config |
| F2.4 â€” Fix forced reflows | `src/**/*.ts` | â–¡ Yes â–¡ No | | Revert geometry caching changes |
| F2.5 â€” Optimise DOM | `src/components/*.tsx` | â–¡ Yes â–¡ No | | Restore removed hidden nodes |
| F3.1 â€” External API to build time | `src/**/*.ts`, config files | â–¡ Yes â–¡ No | | Restore client-side fetch |
| F3.2 â€” CSP headers | `netlify.toml` / `vercel.json` | â–¡ Yes â–¡ No | | Remove or relax CSP directives |

If **Build Pass?** is **No**, run `npm run build` to see the exact error, revert the failed fix immediately, and re-test before applying the next batch.

---

## References

See `references/` for deep-dives:
- `references/performance-deep-dive.md` â€” LCP, CLS, TBT root cause trees
- `references/security-headers.md` â€” Complete CSP/HSTS/COOP reference
- `references/image-optimization.md` â€” WebP/AVIF conversion pipelines

