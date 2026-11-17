# Current-state audit of kishufarm.com (霧珠ファーム) — as of 2026-11-17

**How this was verified (read first).** `kishufarm.com` / `www.kishufarm.com` are blocked by this session's network policy (proxy 403 on CONNECT; WebFetch ENOTFOUND). The site was instead read through the owner's Vercel account: project `kishufarm-site` has domains `kishufarm.com`, `www.kishufarm.com`, `kishufarm-site.vercel.app`; the production alias `kishufarm-site.vercel.app` was fetched (HTML of 5 pages, sitemap, robots, CSS, contact JS). All pages carry `<link rel="canonical" href="https://kishufarm.com/...">`, so this is the same production build that the custom domain serves. Source links below use the canonical kishufarm.com URLs. **Not done:** screenshots (browser cannot reach either host), `/privacy` body, image files/weights, `/api/contact` behaviour (no form was submitted), SNS accounts.

**Premise correction.** The brief described 霧珠ファーム as a Wakayama/紀州 farm with ume/citrus. The live site says otherwise: it is in **京都府亀岡市** (Kameoka, Kyoto), and "霧珠（きしゅ）" means the bead-like droplets of morning fog, not 紀州. Crops listed are grapes, spinach, garlic, onion. No ume or citrus appears anywhere on the site.

## What pages and sections exist now, and what does each say?

### Takeaway
The site is a 6-URL static Astro site on Vercel (home, about, business, membership, contact, privacy) positioned as a corporate/"3 businesses" site for a Kameoka grape-and-vegetable farm. A membership page already exists (3 plans, pre-registration only); there is no news/blog, no product pages, no shop, and no SNS presence on the site.

### Cited Findings
- Sitemap lists exactly six URLs: `/`, `/about`, `/business`, `/contact`, `/membership`, `/privacy`. — [sitemap-0.xml](https://kishufarm.com/sitemap-0.xml)
- robots.txt is `User-agent: * / Allow: /` with `Sitemap: https://kishufarm.com/sitemap-index.xml`. — [robots.txt](https://kishufarm.com/robots.txt)
- Global nav (4 items): 農園を知る (`/about`), 事業内容 (`/business`), ぶどうの木オーナーになる (`/membership`), button お問い合わせ (`/contact`). Footer repeats these under "SITE", plus a "STORE" column containing only non-linked text "オンラインストア 準備中", and a プライバシーポリシー link. — [Home](https://kishufarm.com/)
- **Home**: title "霧珠ファーム | 京都・亀岡の霧が育てる農園". Hero H1 "霧が育てる 一粒の実り", lead "京都・亀岡 深い朝霧に包まれる盆地で ぶどうと野菜を育てています". Sections in order: ABOUT ("農業を続けられる仕事に", 丹波霧, 3-node chain 育てる/届ける/続ける) → MEMBERSHIP band ("あなたの一本が亀岡の畑に根を張る"; facts "¥30,000〜 / 3プラン（内容調整中）", "2026.11 本募集開始予定", "先行案内の登録は無料・1分") → BUSINESS "3つの事業" (ぶどう栽培・ワイン事業 "先行案内 受付中" / 野菜の生産・卸 "卸のご相談 受付中" / 農業管理アプリ "提供準備中") → CTA band. — [Home](https://kishufarm.com/)
- **About** (`/about`, title "私たちについて"): name origin "霧珠（きしゅ）— 亀岡の朝霧が葉に残す 珠のような雫"; VISION text about making farming profitable by running 生産・販売・IT・マーケティング in one team; 3-photo strip; PROFILE table (名称 霧珠ファーム（KISHU FARM）, 所在地 京都府亀岡市曽我部町寺拍子垣内16-7, 代表 中川 修汰, 主な作物 ぶどう、ほうれん草、にんにく、たまねぎ, 連絡先 info@kishufarm.com); ACCESS with Google Maps iframe ("JR嵯峨野線 亀岡駅から車", field visits by prior inquiry). — [About](https://kishufarm.com/about)
- **Business** (`/business`): 01 VINEYARD — wine grapes grown in partnership with a winery, owner scheme "2026年11月募集開始予定", "ワインの販売体制を整備中（酒類販売免許 取得手続き中）". 02 VEGETABLES — ほうれん草・にんにく・たまねぎ open-field, wholesale to 飲食店・小売・生協, cultivation/pesticide records disclosable. 03 AGRI-TECH — in-house farm record/pesticide app (LINE notification of work reports), image "準備中". — [Business](https://kishufarm.com/business)
- **Membership** (`/membership`, title "ぶどうの木会員権"): hero "¥30,000〜 / 年 · 2026.11 本募集開始予定"; yearly 5-step timeline (1–2月 剪定, 4–5月 誘引・芽かき, 6月 傘掛け, 9月 選果, 9–10月 収穫; participation optional; all plans include ownership of 1 vine + growth-report delivery); PRODUCER block (中川 修汰, one sentence); three plans — ライト ¥30,000/年 (choose 2 of 7 perks), スタンダード ¥50,000/年 (4 of 8), プレミアム ¥100,000/年 (6 of 8). Perks: ワイン3本セット, 野菜セット, 収穫チケット, 農園手伝い, 亀岡BBQ, オーナー会 (Standard/Premium only), ネームプレート作成, エプロン作成. Notes: "初年度は限定本数", "料金・特典は2026年11月の本募集開始時に正式決定…（最終更新: 2026年8月22日）". — [Membership](https://kishufarm.com/membership)
- **Contact** (`/contact`): one form for everything; "通常2営業日以内にご返信します". — [Contact](https://kishufarm.com/contact)
- Local docs describe the wider business differently from the site: four lines (Web事業 = running, ぶどうの木会員権 = 未着手, 新規就農コンサル = 未着手, farm-app = internal use); Web business bases are 柏・横浜. The live site shows three businesses and does not mention the Web/AEO business or consulting. — `/home/user/kishufarm/docs/web-business/01-briefing.md`
- Local strategy docs: "まる曽たまねぎ" branding plan under 霧珠ファーム — person-brand + sales agency for other farmers' produce (代行型), start Nov 2026, flagship = spring 2027 new onions; platforms TikTok + Instagram; first sales venue recommended "産直モール先行（LPは実績が出てから）", decision due 2026-11-30; processed goods not this season. — `/home/user/kishufarm/docs/strategy/maruso-onion-branding.md`

### Inferences
- The site is structured as a company brochure ("3つの事業", B2B wholesale, app) rather than a consumer/fan destination; a visitor arriving from Instagram finds one consumer offer (membership pre-registration) and nothing to buy or follow.
- The owner's statement that they "plan to add a membership page" does not match the live site: the page exists. The real gap is that it is a pre-registration teaser with unfinalised terms, no application flow, no FAQ, no terms.
- CSS still contains unused classes (`.faq`, `.flow`, `.person`, `.plan.featured`, `.utility-bar`, `.web-aeo-pill`, `.svc-grid`), which suggests FAQ / application-flow / producer-profile / Web-AEO sections were built or planned and then removed; they could be reinstated cheaply. — [CSS](https://kishufarm.com/_astro/BaseLayout.tuQ91XXx.css)
- The まる曽たまねぎ brand, the onion direct-sales plan and the 販売代行 model are absent from the site; onion appears only as a crop name.

### Gaps
- `/privacy` content not read. Whether any unlisted pages exist (e.g. 特定商取引法) is unknown; none are in the sitemap or linked.
- Whether the "2026.11 本募集" has actually opened: the page still shows pre-registration and "最終更新 2026年8月22日" on 17 Nov 2026.
- No ume/citrus/Wakayama content found; `09-sales-channels.md` mentions "農業（ぶどう・梅）" once, which conflicts with the site's crop list. Needs owner confirmation.

## What CTAs, forms, SNS links, LINE links and e-commerce links exist now? What is missing?

### Takeaway
Every CTA on the site ends at one generic contact form (email reply within 2 business days). There are zero SNS links, zero LINE links, zero shop links, no newsletter, and no purchase or application capability.

### Cited Findings
- Home CTAs: hero "ぶどうの木会員権を見る" (`/membership`) and "事業内容へ"; membership band "会員権の詳細を見る"; bottom "会員権の先行案内に登録する" (`/contact?type=membership`), "野菜・ぶどうの卸について" (`/contact?type=wholesale`), "その他のお問い合わせ". — [Home](https://kishufarm.com/)
- Membership CTAs: "先行案内に登録する" ×2, "先行案内を申し込む", plus a mobile-only sticky bar "先行案内は無料・登録1分 / 先行案内を受け取る" — all link to `/contact?type=membership`. — [Membership](https://kishufarm.com/membership)
- The contact form has 6 visible fields (種類 select [会員権先行案内 / 卸 / アプリ / 取材・見学 / その他], お名前, 会社名・店舗名, メール, 電話, 内容 textarea; 4 required) plus a hidden honeypot. `?type=membership` preselects the type and prefills the message with "【会員権 先行案内の登録を希望します】". Submission is a JSON POST to same-origin `/api/contact`; on success it fires `gtag('event','generate_lead')` only if `window.gtag` exists. — [Contact](https://kishufarm.com/contact); [contact JS](https://kishufarm.com/_astro/contact.astro_astro_type_script_index_0_lang.IIf2d6m0.js)
- Contact details shown: `info@kishufarm.com` (mailto) and the postal address; no phone number. — [Contact](https://kishufarm.com/contact)
- In the HTML of home, about, business, membership and contact there is no link to Instagram, TikTok, X, Facebook, YouTube, LINE, or any external shop/marketplace; the only external resource is the Google Maps iframe on About. JSON-LD Organization has no `sameAs`. — [Home](https://kishufarm.com/); [About](https://kishufarm.com/about)
- Store status: footer text "オンラインストア 準備中" (a `<span>`, not a link). — [Home](https://kishufarm.com/)
- Local docs state an Instagram account for the farm exists and is a customer-acquisition asset ("kishufarm 本体のInstagramは、農業（ぶどう・梅）の集客資産です"). — `/home/user/kishufarm/docs/web-business/09-sales-channels.md`
- Web searches for "霧珠ファーム", "霧珠ファーム kishufarm" and "kishufarm.com" returned no results about this farm (no SNS profiles, marketplace listings or press found). — [WebSearch, no relevant result]

### Inferences
- Missing entirely: Instagram/TikTok links and feed, LINE公式アカウント friend-add button/QR, online store or marketplace links (食べチョク/ポケマル/BASE/STORES etc.), product listing with prices, newsletter/news, 特定商取引法に基づく表記, shipping/returns info, payment, membership application (as opposed to "notify me") flow, FAQ, member voices/reviews, phone.
- "先行案内は登録1分" is asserted, but the path is a 6-field general inquiry form with a required free-text message; a 1-field email capture or a LINE friend-add would better fit the claim.
- Lead follow-up depends on manual email; there is no channel for the owner's goal of "steadily delivering information" (no LINE, no mail list, no news page, no RSS).

### Gaps
- Instagram/TikTok handles for 霧珠ファーム or まる曽 were not found in the repo or by search; follower counts and bio-link destination unknown.
- Whether a LINE公式アカウント already exists is unknown.
- Whether `/api/contact` stores leads in a list (vs. email notification only) was not tested.

## What does the site look like on mobile vs desktop; first view, load weight, meta/OGP, structured data, platform?

### Takeaway
Technically the site is clean and light (static Astro on Vercel, self-hosted subset font, strict security headers, full meta/OGP/JSON-LD). Visually it is a restrained "mist and grape" brand with serif headings; its weakness is imagery: an abstract SVG hero, three or four reused "イメージ" photos, no producer face and no produce photography. Screenshots could not be taken, so layout notes come from HTML/CSS.

### Cited Findings
- Platform: Vercel project `kishufarm-site`, framework preset none, Node 24.x; assets under `/_astro/` (Astro static build); response header `server: Vercel`. Three production deployments exist, the latest created ≈ 2026-10-24 (UTC), deployed by CLI/API rather than Git (empty deployment meta). — Vercel project API (owner account); [Home](https://kishufarm.com/)
- Security headers: HSTS preload, `X-Frame-Options: DENY`, and CSP `default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'; font-src 'self'; img-src 'self' data:; connect-src 'self'; frame-src https://maps.google.com https://www.google.com; form-action 'self'`. — [Home response headers](https://kishufarm.com/)
- Colours (CSS variables): ink `#182420`, grape `#5c4059` (primary/buttons), grape-deep `#463044` (footer, membership band), moss `#35624d` / `#24513f`, fog `#eef2ef`, mist `#f3eef2`, line `#dce3dd`, paper `#fff`. Radius 6px, max width 1120px. — [CSS](https://kishufarm.com/_astro/BaseLayout.tuQ91XXx.css)
- Typography: headings in self-hosted "Shippori Mincho" (500/600/700, subset woff2, `font-display: swap`); body in system gothic stack (Hiragino Sans / Yu Gothic / Meiryo), 16px, line-height 1.9; labels in system monospace with wide tracking. — [CSS](https://kishufarm.com/_astro/BaseLayout.tuQ91XXx.css)
- Home first view: 76vh hero (62vh on ≤900px) on a pale surface with two animated blurred SVG "grape orbs" and noise texture; H1 + lead + two buttons. No photograph, no product, no price in the first view. — [Home](https://kishufarm.com/); [CSS](https://kishufarm.com/_astro/BaseLayout.tuQ91XXx.css)
- Photography: only `grape-vineyard.webp`, `vegetable-field.webp`, `fresh-vegetables.webp`, `web-work.webp` are referenced; alt texts say "…のイメージ". `grape-vineyard.webp` is reused as the home business thumbnail, the home membership-band photo, the about strip, the business section, and the membership "PRODUCER" photo (labelled "収穫したぶどうを両手で持つ様子"). The app section shows a "準備中" placeholder. — [Home](https://kishufarm.com/); [Membership](https://kishufarm.com/membership); [CSS](https://kishufarm.com/_astro/BaseLayout.tuQ91XXx.css)
- Mobile (≤900px): nav collapses behind a text button "MENU" into a full-width dropdown; all grids become one column; section padding 56px; membership page gets a fixed bottom CTA bar (other pages do not); the year timeline becomes a list at ≤820px; perks grid 2 columns at ≤700px. Sticky header 68px on all sizes. `prefers-reduced-motion` is respected; skip link and `aria-current` present. — [CSS](https://kishufarm.com/_astro/BaseLayout.tuQ91XXx.css)
- Load weight: each page loads one CSS file, one small module script (plus one on contact), self-hosted font subsets, and lazy-loaded WebP images; no third-party scripts in the HTML. Home HTML is inflated by two large inline SVG orb definitions. — [Home](https://kishufarm.com/)
- Meta: unique `<title>` and description per page, canonical, `og:site_name/type/title/description/url/locale`, `twitter:card=summary_large_image`. `og:image` is the same `/images/og-default.jpg` on every page. Home description: "霧珠ファームは京都府亀岡市の農園です。丹波霧が育てるぶどうと野菜の生産・卸、ぶどうの木オーナー制度、農業管理アプリの開発を手がけています。" — [Home](https://kishufarm.com/); [Membership](https://kishufarm.com/membership)
- Structured data: home has `Organization`+`LocalBusiness` (name, alternateName KISHU FARM, email, address, founder 中川修汰, knowsAbout); inner pages have `BreadcrumbList`; membership has `Product` with three `Offer`s (30000/50000/100000 JPY, `availability: PreOrder`). — [Home](https://kishufarm.com/); [Membership](https://kishufarm.com/membership)
- Nav label vs page title mismatch: nav says "農園を知る" / "ぶどうの木オーナーになる", pages are titled "私たちについて" / "ぶどうの木会員権". — [About](https://kishufarm.com/about); [Membership](https://kishufarm.com/membership)

### Inferences
- No analytics tag is present in the fetched HTML, and the CSP (`script-src 'self'`, `connect-src 'self'`) would block GA4/GTM, Meta Pixel and LINE Tag anyway. The form's `gtag` call is therefore currently dead code, so SNS-to-site traffic and conversions are probably not being measured.
- The same CSP blocks an embedded Instagram feed, external shop "buy button" scripts/iframes (BASE/STORES/Shopify), LINE widgets and externally hosted images. Plain outbound links (LINE friend-add URL, marketplace URLs, Instagram profile) work without changes; anything embedded needs a deliberate CSP relaxation.
- With deployments made by CLI and no CMS, every news item or product update currently needs a developer build and deploy; this is a structural obstacle to "steady information delivery" unless a content collection (Markdown) or headless CMS is added.
- The brand system (colours, serif headings, quiet tone) is coherent and reusable for new pages; what is missing is real, specific imagery (owner's face, the actual field, harvest, boxed produce), which matters most for visitors arriving from Instagram/TikTok video.

### Gaps
- No screenshots: mobile/desktop rendering, actual image quality, `og-default.jpg` existence and total page weight in bytes are unverified. To verify, allow `kishufarm.com` (or `kishufarm-site.vercel.app`) in the session's network settings.
- Core Web Vitals / Lighthouse not measured. Search Console / indexing state unknown (search engines returned nothing for the brand name in this session).

## Which gaps most hinder SNS-to-site conversion, membership application, LINE registration and direct sales?

### Takeaway
The blockers are structural, not cosmetic: there is no landing destination for SNS visitors, no low-friction capture (LINE), no way to apply or pay for membership, no shop or legal pages for direct sales, no content stream, and no measurement.

### Cited Findings
- SNS → site: no SNS links, no `sameAs`, no SNS-specific landing page or link hub; first view is abstract with corporate CTAs. — [Home](https://kishufarm.com/)
- Membership: page is pre-order only; terms "内容調整中", count of vines unannounced, text last updated 2026-08-22 while promising a November 2026 opening; no application form, payment, terms/cancellation, FAQ, or member testimonials; producer block is one sentence without a face photo. — [Membership](https://kishufarm.com/membership)
- Membership perk "ワイン3本セット" is listed in every plan while the business page says the liquor sales licence is still being obtained ("酒類販売免許 取得手続き中"). — [Membership](https://kishufarm.com/membership); [Business](https://kishufarm.com/business)
- LINE: no LINE account link, QR or mention for customers anywhere (LINE appears only as an app feature). — [Business](https://kishufarm.com/business)
- Direct sales: store is "準備中" text; no product/price/season/shipping information; no 特定商取引法 page in the sitemap; vegetables are presented only as B2B wholesale ("卸のご相談 受付中"). — [Home](https://kishufarm.com/); [sitemap-0.xml](https://kishufarm.com/sitemap-0.xml)
- Fan-building: no news, blog, growth reports, seasonal calendar for produce, or mail/LINE subscription; "生育レポート配信" is promised to members but no sample is shown. — [Membership](https://kishufarm.com/membership)
- Owner-side plan relevant to site design: onion direct sales start via 産直モール first with an own LP later; TikTok + Instagram as the two platforms; face-and-name person brand; 販売代行 of neighbouring farms' produce so sales are not tied to own harvest. — `/home/user/kishufarm/docs/strategy/maruso-onion-branding.md`
- The owner's operating rules require choices to be presented as at most two options with one recommendation and carried through to execution. — `/home/user/kishufarm/CLAUDE.md`

### Inferences
Ranked by how much they block the stated goals:
1. **No LINE friend-add path** — the cheapest high-conversion capture for Japanese SNS traffic and the natural channel for ongoing delivery; currently replaced by a 6-field email form.
2. **No SNS landing/bridge** — Instagram/TikTok visitors need a mobile-first page with a face, the current offer, and 2–3 buttons (LINE, membership, buy); the home page serves corporate/B2B readers instead. SNS links back out are also absent.
3. **Membership cannot be applied for** — needs finalised plans, application form (or payment link), terms, FAQ, flow, limited count, real photos; and the wine perk must be reconciled with the licence status.
4. **No direct-sales surface** — needs a products/"お取り寄せ" page (even if it only links to a marketplace listing at first, consistent with the "産直モール先行" recommendation), 特商法表記, shipping info, seasonal availability; the onion brand has no presence.
5. **No content stream** — no news/畑だより; no CMS; nothing gives a returning fan a reason to come back.
6. **No measurement** — no analytics, CSP blocks tags; UTM-tagged SNS links and conversion events cannot be evaluated.
7. **Thin trust assets** — stock-like images reused across pages, no producer face, no reviews, no phone.
8. **Information-architecture mix** — B2B wholesale and the farm app share top-level weight with consumer offers; consumer paths (会員権 / 買う / LINE / お知らせ) are not first-class nav items.
- Site-structure facts to design around: brand is Kyoto-Kameoka + 丹波霧 + grapes (not 紀州/ume); existing design tokens and unused FAQ/flow/person CSS can be reused; any embed (Instagram, shop, analytics) requires a CSP change.

### Gaps
- No traffic, lead-count or conversion data was available (no analytics found); the ranking above is reasoned from site structure, not measured.
- Unknown: number of pre-registrations collected so far, whether the membership launch date has slipped, which marketplace (if any) has been chosen for onions, and the relation between the "まる曽" name and the 霧珠ファーム brand on the site.
- Unknown whether wine may legally be included as a membership perk before the licence is granted; needs confirmation with the tax office/licence adviser.
