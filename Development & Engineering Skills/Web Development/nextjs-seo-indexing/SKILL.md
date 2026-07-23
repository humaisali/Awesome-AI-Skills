---
name: nextjs-seo-indexing
description: "Fix SEO indexing issues, crawl budget problems, and Search Console coverage errors for Next.js apps. Covers canonical tags, noindex audits, sitemap health, static rendering, and internal linking."
category: seo
risk: safe
source: https://github.com/humaisali
source_type: self
date_added: "2026-05-31"
Maintained & Curated by: Humais Ali
tags: [seo, indexing, nextjs, search-console, crawl-budget, canonical, sitemap]
tools: [claude, cursor, gemini, claude-code]
version: 1.0.0
---

# Next.js SEO Indexing & Crawl Budget Skill

Fix Google Search Console coverage issues, canonical problems, sitemap errors, and crawl budget waste in Next.js apps.

---

## When to Use

- Use when a Next.js site has Google Search Console coverage issues such as duplicate canonicals, accidental noindex, crawl waste, or discovered-but-not-indexed URLs.
- Use when auditing sitemap, robots.txt, redirect, internal-linking, or static-rendering problems before an SEO release.
- Use when you need framework-specific examples for Next.js App Router metadata, `generateMetadata`, `robots.js`, and sitemap routes.

---

## Understanding Search Console Coverage States

| Status | Meaning | Fix |
|--------|---------|-----|
| Crawled â€“ not indexed | Google crawled but chose not to index | Improve content quality + canonical + internal links |
| Duplicate without canonical | Multiple URLs serve same content, no canonical | Add explicit canonical to the preferred URL |
| Excluded by noindex | `noindex` tag present | Remove noindex if page should be indexed |
| Duplicate, Google chose different canonical | Google prefers a different URL than you specified | Align canonical with the URL Google naturally picks |
| Alternative page with proper canonical | Correct â€” non-preferred duplicate pointing to canonical | Expected behavior, not a problem |
| Not found 404 | Page deleted or URL changed | Add redirect or restore page |
| Discovered â€“ not indexed | Google knows it exists but hasn't crawled it | Improve internal linking + crawl budget |
| Page with redirect | Redirect chain or redirect to wrong target | Shorten redirect chain, verify destination |

---

## Step 1 â€” Canonical Audit

### Next.js App Router (metadata export)
```js
// app/blog/my-post/page.js
export const metadata = {
  title: 'My Post Title',
  alternates: {
    canonical: 'https://www.yourdomain.com/blog/my-post',
  },
};
```

### Next.js App Router (generateMetadata)
```js
export async function generateMetadata({ params }) {
  return {
    alternates: {
      canonical: `https://www.yourdomain.com/blog/${params.slug}`,
    },
  };
}
```

### Common canonical mistakes to fix:
```js
// âŒ WRONG â€” relative URL
canonical: '/blog/my-post'

// âŒ WRONG â€” missing trailing slash inconsistency  
// (pick one and stick with it sitewide)

// âœ“ CORRECT â€” absolute URL, consistent scheme + subdomain
canonical: 'https://www.yourdomain.com/blog/my-post'
```

---

## Step 2 â€” Noindex Audit

Find pages that are accidentally noindexed:

```bash
# Search for noindex in metadata
rg -n --glob '*.{js,ts,jsx,tsx}' 'noindex|robots.*noindex' app pages

# Check layout.js â€” a noindex here affects ALL pages
grep -n "robots" app/layout.js
```

In Next.js App Router, `robots` in the root layout applies globally. Only set it there if you want the whole site affected.

```js
// app/layout.js â€” only set robots if you need sitewide control
export const metadata = {
  // âœ“ Allow indexing
  robots: { index: true, follow: true },
  // âŒ This would noindex the entire site:
  // robots: { index: false }
};
```

---

## Step 3 â€” Sitemap Health

### Verify sitemap routes return 200 + valid XML
```bash
curl -sI https://www.yourdomain.com/sitemap.xml | grep -i "content-type\|status"
curl -s https://www.yourdomain.com/sitemap.xml | head -20
```

### Next.js App Router sitemap (recommended pattern)
```js
// app/sitemap.js
export default async function sitemap() {
  const baseUrl = 'https://www.yourdomain.com';
  
  // Static pages
  const staticPages = [
    { url: baseUrl, lastModified: new Date(), changeFrequency: 'daily', priority: 1.0 },
    { url: `${baseUrl}/about`, lastModified: new Date(), changeFrequency: 'monthly', priority: 0.8 },
  ];
  
  // Dynamic pages (fetch from DB or CMS)
  const posts = await getPosts(); // your data fetch
  const dynamicPages = posts.map(post => ({
    url: `${baseUrl}/blog/${post.slug}`,
    lastModified: new Date(post.updatedAt),
    changeFrequency: 'weekly',
    priority: 0.7,
  }));
  
  return [...staticPages, ...dynamicPages];
}
```

### Multiple sitemaps (sitemap index)
```js
// app/sitemap-tools/sitemap.js  
// app/sitemap-blog/sitemap.js
// Each returns an array of URL entries
```

---

## Step 4 â€” Static Rendering Verification

Pages must be statically generated (or SSR with metadata in HTML) for Google to see SEO tags.

```bash
# Check build output â€” pages should show â— (static) not Î» (dynamic)
npm run build 2>&1 | grep -E "â—‹|â—|Î»|/blog|/tools"
```

```text
â—‹  /about             (static)
â—  /blog/[slug]       (SSG)  â† good
Î»  /api/data          (serverless) â† expected for APIs
```

If important pages are `Î»` (fully dynamic with no static generation), add:

```js
// app/blog/[slug]/page.js
export async function generateStaticParams() {
  const posts = await getPosts();
  return posts.map(post => ({ slug: post.slug }));
}
```

---

## Step 5 â€” Internal Linking Audit

Pages with zero internal links are rarely indexed. Every important page should be reachable from:
1. Homepage or navigation
2. A sitemap
3. At least one other content page

```bash
# Find pages that have no inbound links from other pages
# (manual check â€” grep for the slug across all files)
grep -r "/blog/my-orphan-post" --include="*.{js,ts,jsx,tsx,md}" . | grep -v "sitemap\|the-page-itself"
```

---

## Step 6 â€” Redirect Audit

```bash
# Find all redirects in Next.js config
grep -A 3 "redirects" next.config.js

# Check for redirect chains (A â†’ B â†’ C â€” should be A â†’ C)
# Test a suspected chain:
curl -sI https://www.yourdomain.com/old-url | grep -i location
```

```js
// next.config.js â€” keep redirects flat (no chains)
async redirects() {
  return [
    {
      source: https://github.com/humaisali
      destination: '/new-url', // Must NOT itself redirect
      permanent: true, // 308 for SEO
    },
  ];
}
```

---

## Step 7 â€” robots.txt Check

```bash
curl -s https://www.yourdomain.com/robots.txt
```

```text
# âœ“ Good
User-agent: *
Allow: /
Sitemap: https://www.yourdomain.com/sitemap.xml

# âŒ Bad â€” disallows crawling of important content
Disallow: /blog/
Disallow: /tools/
```

```js
// app/robots.js (Next.js App Router)
export default function robots() {
  return {
    rules: { userAgent: '*', allow: '/' },
    sitemap: 'https://www.yourdomain.com/sitemap.xml',
  };
}
```

---

## Indexing Checklist

- [ ] All important pages have absolute canonical URLs
- [ ] No important pages accidentally noindexed
- [ ] Sitemap routes return 200 with valid XML
- [ ] Sitemap submitted to Google Search Console
- [ ] Important pages statically generated (â—) in build output
- [ ] No redirect chains (Aâ†’Bâ†’C should be Aâ†’C)
- [ ] robots.txt allows important content
- [ ] Every important page has â‰¥1 internal inbound link
- [ ] `generateStaticParams` added for dynamic routes with known slugs

## Limitations

- Does not guarantee Google will index a page; final indexing decisions remain with the search engine.
- Requires access to the codebase, deployed URLs, and ideally Google Search Console data for confident diagnosis.
- Treat recommendations that change URL structure, redirects, or canonical policy as production-impacting and review them before deployment.

