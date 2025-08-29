# WealthFlow — Vercel Starter

โครงพร้อมดีพลอยสำหรับเว็บสแตติก + ฟังก์ชัน Cron ส่งอีเมลสรุป (Resend) ที่เชื่อมกับ Supabase

## เตรียมไฟล์ให้ครบ
```
/
├─ index.html
├─ assets/
│  ├─ style.css
│  └─ app.js
├─ api/
│  ├─ monthly-summary.js
│  └─ yearly-tax.js
├─ package.json
└─ vercel.json
```

## ขั้นตอนดีพลอย (ย่อ)
1. อัปทั้งหมดนี้ขึ้น GitHub (repo ใหม่)
2. Vercel → Import Project → เลือก repo → Deploy
3. ตั้ง Environment Variables ใน Vercel (Project → Settings → Env):
   - `SUPABASE_URL` = https://YOUR-PROJECT.supabase.co
   - `SUPABASE_SERVICE_ROLE_KEY` = คีย์ Service Role (ฝั่งเซิร์ฟเวอร์เท่านั้น)
   - `RESEND_API_KEY` = คีย์ Resend
   - (ทางเลือก) `RESEND_FROM` = ที่อยู่อีเมลผู้ส่ง เช่น no-reply@yourdomain.com
4. เปิด Cron: ใช้ไฟล์ `vercel.json` ที่กำหนดไว้แล้ว
5. แก้ **index.html** ใส่ `APP_CONFIG` (URL + ANON KEY) ให้ถูกต้อง จากนั้น redeploy

> หมายเหตุ: ฟังก์ชันใช้ตาราง `profiles(id,email)` และ `transactions(user_id,t_date,amount,type)`
> ถ้า schema ของคุณต่างออกไป ให้แก้ในไฟล์ API ตามต้องการ
