# อุดมสุขฟิล์มศรีนครินทร์53 — Landing Page (Local SEO)

เว็บไซต์หน้าเดียว (One Page Local SEO Landing Page) สำหรับร้าน **อุดมสุขฟิล์มศรีนครินทร์53**
เป้าหมายเดียว: ให้ลูกค้าค้นเจอจาก Google แล้วกด **โทร / ทัก Line / เปิดแผนที่** มาที่ร้าน

## 🚀 Deploy คลิกเดียว
[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/nustanakritwithai/Udomsukflim)

กดปุ่มด้านบน → ล็อกอิน Render → กด **Apply** (Render จะอ่าน `render.yaml` เอง) ได้ URL `*.onrender.com` พร้อม HTTPS อัตโนมัติ

- **โดเมนจริง (canonical):** `https://udomsuk-film.com/` — schema/canonical/sitemap ทุกจุดชี้มาที่นี่
- **เดโม/สำรอง:** `https://udomsukflim.onrender.com/` — ใช้พรีวิวก่อนเท่านั้น (canonical ชี้กลับโดเมนจริง Google จึงไม่ index ซ้ำ)
- ขั้นต่อไป: ที่ Render → **Settings → Custom Domains** เพิ่ม `udomsuk-film.com` แล้วตั้ง DNS ตามที่ Render บอก เพื่อให้โดเมนจริงออนไลน์

> ⚠️ **ชื่อ repo/URL เดโม "Udomsukflim" / "udomsukflim.onrender.com" เป็นเพียงชื่อภายในสำหรับพรีวิวเท่านั้น
> ไม่ใช่ branding สุดท้ายของร้าน** เมื่อขึ้น production จริงทุกจุด (title, schema, canonical, og:url, sitemap, robots)
> ใช้สะกดที่ถูกต้องคือ **"film"** และโดเมน `udomsuk-film.com` (หรือโดเมนจริงที่เจ้าของร้านเลือก) อยู่แล้ว

## โครงสร้างไฟล์
```
index.html        ← หน้าเว็บทั้งหมด (HTML + CSS + JS เล็กน้อย ในไฟล์เดียว)
404.html          ← หน้าไม่พบ (กัน soft-404)
robots.txt        ← เปิดให้ Google + AI crawler ทั้งหมด + ชี้ไป sitemap
sitemap.xml       ← แผนผังเว็บ + image sitemap
llms.txt          ← สรุปข้อมูลร้านสำหรับ AI (ChatGPT/Claude/Perplexity ดึงไปตอบ)
site.webmanifest  ← PWA/mobile metadata
render.yaml       ← Blueprint สำหรับ deploy เป็น Static Site บน Render
images/           ← รูปจริงของร้าน (ดูคำแนะนำใน images/README.md)
```

## Performance / Core Web Vitals
- รูปทุกภาพมี `loading="lazy"` + `decoding="async"`; รูป hero เป็น `eager` + `fetchpriority="high"` + preload (ดี LCP)
- Google Fonts โหลดแบบไม่ block การ render (preload + `media="print"` swap)
- มี `<main>`, `<nav>` jump links, skip-link, `<address>` semantic → โครงสร้างชัดต่อ crawler/AI

## ปรับแต่งสำหรับ Google + AI Search
- **Structured data หลายชุด:** LocalBusiness/AutoRepair (พร้อม geo, `hasOfferCatalog` แยก 2 หมวดบริการ — ติดฟิล์มรถยนต์ และติดฟิล์มบ้าน/คอนโด/อาคาร/สำนักงาน, `sameAs`, แผนที่), FAQPage, WebSite, WebPage (`speakable` สำหรับ voice/AI), BreadcrumbList — เชื่อมกันด้วย `@id`
- **เปิดทาง AI crawler** ใน `robots.txt`: GPTBot, OAI-SearchBot, ClaudeBot, anthropic-ai, PerplexityBot, Google-Extended, Applebot-Extended, CCBot ฯลฯ
- **`llms.txt`** สรุปข้อเท็จจริงร้านแบบ markdown ให้ AI อ้างอิงได้แม่นยำ ครอบคลุมทั้ง 2 หมวดบริการ
- **Geo meta** (`geo.position`, `ICBM`) + meta keywords + `max-image-preview:large`
- FAQ เขียนแบบถาม–ตอบชัด ครอบคลุมทั้งฟิล์มรถยนต์และฟิล์มบ้าน/คอนโด/อาคาร เพื่อให้ติด AI Overviews / People Also Ask

## สิ่งที่ทำไว้ให้แล้ว (โครงสร้างเว็บพร้อมแล้ว)
- ✅ One page ครบทุก section: Hero (มีปุ่มโทร/Line/Maps ทันที), ข้อมูลร้าน, จุดขาย 6 ข้อ, **บริการติดฟิล์มรถยนต์** (3 บริการ), **บริการติดฟิล์มบ้าน/คอนโด/อาคาร/สำนักงาน/ร้านค้า** (section หลักแยกเฉพาะ พร้อม CTA และ FAQ ของตัวเอง), ตารางราคา 2 แพ็กเกจ (รถยนต์ + อาคาร), พื้นที่บริการ, ผลงาน/รีวิว, FAQ, ติดต่อ + ฝัง Google Maps
- ✅ มี `<h1>` เดียวที่มีคำว่า "ใกล้ฉัน" + `<h2>` ประจำแต่ละ section
- ✅ SEO Title (มีคำว่า "ใกล้ฉัน") + Meta Description + canonical + Open Graph
- ✅ ปุ่มโทร `tel:0863704378` / ปุ่ม Line / ปุ่ม Maps ครบทุก section สำคัญ (hero, บริการรถยนต์, บริการอาคาร, ราคา, ติดต่อ, footer)
- ✅ Sticky bar ปุ่ม โทร/Line/แผนที่ บนมือถือ
- ✅ Responsive 100% มือถือ เดสก์ท็อป
- ✅ LocalBusiness Schema (`AutoRepair`) + `hasOfferCatalog` + FAQPage Schema (JSON-LD ทั้งหมด valid)
- ✅ ข้อมูลร้าน ชื่อ/ที่อยู่/เบอร์/เวลาเปิด เป็น "ตัวหนังสือจริง" (ไม่ฝังในรูป)
- ✅ ทุกรูปมี `alt` text และชื่อไฟล์แบบ SEO
- ✅ robots.txt + sitemap.xml + llms.txt
- ✅ GA4 click-tracking scaffold (`data-ga-event`) พร้อม event: call_click, line_click, maps_click, sticky_call_click, sticky_line_click, sticky_maps_click, car_price_request, glass_photo_request, review_click — ทำงานทันทีที่ใส่ Measurement ID จริง
- ✅ ไม่มีหลังบ้าน ไม่มี framework หนัก โหลดเร็ว

> สรุป: **โครงสร้างเว็บไซต์พร้อมแล้ว เหลือเติมข้อมูลจริงเพื่อใช้งาน Production** (ดูหัวข้อถัดไป)

## ⚠️ ต้องแก้ก่อนปล่อยจริง (ค่า placeholder)
แก้ใน `index.html` (และไฟล์ SEO) ให้ตรงของจริง:

1. **โดเมน** — ปัจจุบันใช้ `https://udomsuk-film.com` ใน canonical, OG, schema, sitemap, robots
   ถ้าใช้โดเมนอื่น ให้แทนที่ทุกจุด
2. **ลิงก์ Line** — ปัจจุบัน `https://line.me/R/ti/p/~@udomsukfilm53`
   เปลี่ยนเป็น Line OA ID / ลิงก์จริงของร้าน
3. **Google Maps** — ปุ่มและ iframe ค้นจากชื่อร้าน ควรเปลี่ยนเป็น
   ลิงก์/`place_id` จริงจาก Google Business Profile เพื่อปักหมุดตรงจุด
4. **ลิงก์ดูรีวิว Google** — ใส่ `placeid` จริง
5. **รูปภาพ** — นำรูปจริงวางใน `images/` ตามชื่อไฟล์ใน `images/README.md`
   (อย่างน้อย 10 รูปตาม Acceptance Criteria)
6. **พิกัด geo** — `index.html` (meta + schema) ใช้พิกัดประมาณ `13.6856, 100.6510`
   ของย่านศรีนครินทร์ 53 ควรเปลี่ยนเป็น **พิกัดจริงจาก Google Business Profile**
   (เปิด Google Maps → คลิกหมุดร้าน → คัดลอก lat,lng) ทั้งใน `geo.position`, `ICBM`
   และ `GeoCoordinates` ใน schema
7. **Social links (`sameAs`)** — แก้ลิงก์ Facebook/Line ในบล็อก LocalBusiness schema
   ให้ตรงเพจจริงของร้าน (ช่วยให้ Google/AI ยืนยันตัวตนธุรกิจ)
8. **Google Search Console** — แทนที่ `REPLACE_WITH_GSC_VERIFICATION_CODE` ใน meta
   `google-site-verification` ด้วยโค้ดจริง (หรือใช้วิธียืนยันแบบ DNS)
9. **Google Analytics 4** — แทน `G-XXXXXXXXXX` ด้วย Measurement ID จริง แล้ว uncomment บล็อก GA4 ก่อน `</head>`
10. **ดาวรีวิวใน SERP** — เมื่อมีรีวิวจริง ให้เติม `aggregateRating`/`review` ใน LocalBusiness
    schema (มี template เป็นคอมเมนต์ใน `index.html` แล้ว) — **ใช้ตัวเลขจริงเท่านั้น**

## ขีดจำกัดที่เหลือ (ต้องใช้ข้อมูลจริง — โค้ดรองรับไว้แล้ว)
ทุกข้อด้านบน (1–10) คือสิ่งที่โค้ดเตรียม placeholder ไว้พร้อม เหลือแค่เติมค่าจริง
เมื่อเติมครบ เว็บจะพร้อมเก็บคะแนน SEO/AI เต็มที่ — โดยเฉพาะ **รูปจริง** และ
**รีวิวจริง (ดาวใน SERP)** คือสองตัวที่ส่งผลต่ออัตราการคลิกมากที่สุด

## การนำขึ้นออนไลน์ (Hosting)
เป็น static site ใช้ที่ไหนก็ได้ เช่น **Cloudflare Pages / Netlify / Vercel** หรือโฮสต์ทั่วไป
- ลากทั้งโฟลเดอร์ขึ้น หรือเชื่อม repo นี้กับ Cloudflare Pages/Netlify/Vercel
- ตั้ง custom domain + เปิด **HTTPS** (ผู้ให้บริการเหล่านี้ออก SSL ให้ฟรีอัตโนมัติ)

## หลังปล่อยเว็บ (Local SEO)
- [ ] เพิ่มเว็บใน **Google Search Console** → ส่ง `sitemap.xml` → ขอ index หน้าแรก
- [ ] ใส่ URL เว็บใน **Google Business Profile** ให้ ชื่อ/ที่อยู่/เบอร์/เวลา ตรงกันทุกที่
- [ ] ติดตั้ง **Google Analytics 4** (วาง snippet ก่อน `</head>`)
- [ ] เพิ่มรูปใน Google Business Profile ≥ 10 รูป + ลงโพสต์สัปดาห์ละ 1 ครั้ง
- [ ] ขอรีวิวลูกค้าหลังจบงานทุกคัน และตอบรีวิว

## ทดสอบก่อนส่งงาน
- กดปุ่มโทร / Line / Maps บน Android และ iPhone ให้ครบ
- เช็กความเร็วด้วย PageSpeed Insights
- ตรวจ schema ด้วย Google Rich Results Test
