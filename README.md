# อุดมสุขฟิล์มศรีนครินทร์53 — Landing Page (Local SEO)

เว็บไซต์หน้าเดียว (One Page Local SEO Landing Page) สำหรับร้าน **อุดมสุขฟิล์มศรีนครินทร์53**
เป้าหมายเดียว: ให้ลูกค้าค้นเจอจาก Google แล้วกด **โทร / ทัก Line / เปิดแผนที่** มาที่ร้าน

## โครงสร้างไฟล์
```
index.html      ← หน้าเว็บทั้งหมด (HTML + CSS + JS เล็กน้อย ในไฟล์เดียว)
robots.txt      ← เปิดให้ Google + AI crawler ทั้งหมด + ชี้ไป sitemap
sitemap.xml     ← แผนผังเว็บ
llms.txt        ← สรุปข้อมูลร้านสำหรับ AI (ChatGPT/Claude/Perplexity ดึงไปตอบ)
render.yaml     ← Blueprint สำหรับ deploy เป็น Static Site บน Render
images/         ← รูปจริงของร้าน (ดูคำแนะนำใน images/README.md)
```

## ปรับแต่งสำหรับ Google + AI Search
- **Structured data หลายชุด:** LocalBusiness/AutoRepair (พร้อม geo, รายการบริการ `makesOffer`, `sameAs`, แผนที่), FAQPage, WebSite, WebPage (`speakable` สำหรับ voice/AI), BreadcrumbList — เชื่อมกันด้วย `@id`
- **เปิดทาง AI crawler** ใน `robots.txt`: GPTBot, OAI-SearchBot, ClaudeBot, anthropic-ai, PerplexityBot, Google-Extended, Applebot-Extended, CCBot ฯลฯ
- **`llms.txt`** สรุปข้อเท็จจริงร้านแบบ markdown ให้ AI อ้างอิงได้แม่นยำ
- **Geo meta** (`geo.position`, `ICBM`) + meta keywords + `max-image-preview:large`
- FAQ เขียนแบบถาม–ตอบชัด เพื่อให้ติด AI Overviews / People Also Ask

## สิ่งที่ทำไว้ให้แล้ว (ตาม Acceptance Criteria)
- ✅ One page ครบทุก section: Hero, ข้อมูลร้าน, จุดขาย 6 ข้อ, บริการ 4 อย่าง, ตารางราคา, พื้นที่บริการ, ผลงาน/รีวิว, FAQ, ติดต่อ + ฝัง Google Maps
- ✅ มี `<h1>` เดียว และ `<h2>` ประจำแต่ละ section
- ✅ SEO Title + Meta Description + canonical + Open Graph
- ✅ ปุ่มโทร `tel:0863704378` / ปุ่ม Line / ปุ่ม Maps — วาง CTA 4 จุด (บนสุด, หลังบริการ, หลังราคา, ล่างสุด)
- ✅ Sticky bar ปุ่ม โทร/Line/แผนที่ บนมือถือ
- ✅ Responsive 100% มือถือ เดสก์ท็อป
- ✅ LocalBusiness Schema (`AutoRepair`) + FAQPage Schema (JSON-LD)
- ✅ ข้อมูลร้าน ชื่อ/ที่อยู่/เบอร์/เวลาเปิด เป็น "ตัวหนังสือจริง" (ไม่ฝังในรูป)
- ✅ ทุกรูปมี `alt` text และชื่อไฟล์แบบ SEO
- ✅ robots.txt + sitemap.xml
- ✅ ไม่มีหลังบ้าน ไม่มี framework หนัก โหลดเร็ว

## ⚠️ ต้องแก้ก่อนปล่อยจริง (ค่า placeholder)
แก้ใน `index.html` (และไฟล์ SEO) ให้ตรงของจริง:

1. **โดเมน** — ปัจจุบันใช้ `https://udomsukfilm53.com` ใน canonical, OG, schema, sitemap, robots
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
