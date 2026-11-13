# MIH Connect · Prototype (เว็บ static สำหรับ Vercel)

ต้นแบบระบบ MIH Connect v4 ครบทุกหน้า (บริษัทยา / หน่วยงาน / นักวิจัย) ข้อมูลทั้งหมดเป็นข้อมูลสมมุติ
ไม่มีฐานข้อมูลหรือ backend · กดรีเฟรชแล้วข้อมูลที่กรอกจะกลับเป็นค่าเริ่มต้น

## Deploy ขึ้น Vercel (เลือก 1 วิธี)

**วิธีที่ 1 · ผ่าน GitHub (แนะนำ ถ้าจะอัปเดตบ่อย)**
1. สร้าง repo ใหม่ใน GitHub แล้วอัปโหลดไฟล์ทั้งหมดในโฟลเดอร์นี้ (ให้ `index.html` อยู่ชั้นนอกสุดของ repo)
2. เข้า https://vercel.com/new → Import repo นั้น
3. Framework Preset: **Other** · Build Command: เว้นว่าง · Output Directory: เว้นว่าง → กด **Deploy**
4. ครั้งต่อไปแค่ push ไฟล์ใหม่ Vercel จะ deploy ให้อัตโนมัติ

**วิธีที่ 2 · Vercel CLI**
```bash
cd mih-connect-prototype
npx vercel          # ครั้งแรก: login + ตั้งชื่อโปรเจกต์ (ได้ลิงก์ preview)
npx vercel --prod   # ขึ้น production
```

## โครงสร้างไฟล์
| ไฟล์ | หน้าที่ |
|---|---|
| `index.html` | ตัว prototype ทั้งหมด (สร้างจากแคนวาส v4) |
| `support.js` | runtime ที่แสดงผล prototype |
| `vendor/` | React 18.3.1, ReactDOM, Babel — เก็บไว้ในเว็บเอง ไม่พึ่ง CDN |
| `assets/` | โลโก้ ตรา สธ. ภาพประกอบ 3 กลุ่ม และไฟล์ตัวอย่างนำเข้า (.xlsx) |
| `vercel.json` | ตั้งค่า noindex, cache, และให้ทุก URL เปิดหน้า prototype |

## หมายเหตุ
- ตั้ง `noindex` ไว้ทั้งเว็บ (Google ไม่เก็บ) และมีป้าย "Prototype · ข้อมูลสมมุติ" ที่ขอบล่าง เพื่อไม่ให้ถูกเข้าใจว่าเป็นระบบจริงของกระทรวง
- ฟอนต์ Inter + IBM Plex Sans Thai โหลดจาก Google Fonts
- ถ้าต้องการจำกัดคนเข้าดู: Vercel → Project → Settings → **Deployment Protection** (Vercel Authentication หรือ Password Protection)
- มุมล่างซ้ายของ sidebar มี "สลับมุมมอง (เดโม)" ใช้สลับบทบาทระหว่างนำเสนอ
