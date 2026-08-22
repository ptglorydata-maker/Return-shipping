# สินค้าตีกลับ กรกฎาคม — แดชบอร์ด

หน้าเว็บสถิตย์ (static) หน้าเดียว (`index.html`) ไม่มีขั้นตอน build สรุปข้อมูลสินค้าตีกลับเดือน ก.ค. 2569 ของ PT Glory จาก Google Sheet (แท็บ Discuse, Total_Order on Sell, config)

## Deploy ขึ้น Vercel

1. เข้า https://vercel.com/new แล้วเลือก **Import** repo นี้ (`Return-shipping`)
2. ตั้งค่า Framework Preset เป็น **Other** (ไม่ต้อง build command / output directory ใด ๆ เพราะเป็น static `index.html`)
3. กด **Deploy**

## จำกัดสิทธิ์ผู้เข้าดูเฉพาะทีมภายใน (Vercel Authentication)

เมื่อ deploy เสร็จแล้ว:

1. ไปที่ **Project → Settings → Deployment Protection**
2. เปิด **Vercel Authentication**
3. ระบบจะให้เข้าถึงได้เฉพาะคนที่เป็นสมาชิกใน Vercel Team เดียวกันเท่านั้น — ถ้าผู้บริหารคนไหนยังไม่อยู่ในทีม ต้องเชิญเข้า Team ก่อนที่ **Team Settings → Members**
4. บันทึกการตั้งค่า — คนนอกทีมที่เปิดลิงก์จะถูกเด้งไปหน้า login ของ Vercel ก่อนเสมอ

## อัปเดตข้อมูล

ข้อมูลในหน้านี้ฝังเป็นค่าคงที่ (static) ไว้ใน `index.html` ไม่ได้ดึงสดจาก Google Sheet — เมื่อมีข้อมูลเดือนใหม่หรือแก้ไขตัวเลข ต้องแก้ในไฟล์ `index.html` แล้ว push ขึ้น Vercel จะ deploy ให้อัตโนมัติ
