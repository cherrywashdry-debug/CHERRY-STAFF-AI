# CHERRY Staff AI — บอทแปลภาษา (พนักงาน)

บอท Telegram **สำหรับพนักงานเท่านั้น** — แปลข้อความลูกค้าและแปลคำตอบพนักงาน

**Production (ตั้งค่าใหม่):** https://cherry-staff-ai.onrender.com

## แยกจากบอทอื่น

| บอท | Repo | ใช้ที่ไหน |
|-----|------|-----------|
| **Staff AI (ตัวนี้)** | CHERRY-STAFF-AI | กลุ่ม staff `STAFF_GROUP_ID` |
| **FAQ** | [CHERRY-SUPPORT-AI](https://github.com/cherrywashdry-debug/CHERRY-SUPPORT-AI) | แชทส่วนตัวลูกค้า/พนักงาน — กดเมนู FAQ |
| **V3** | cherry-bot-v3-test | ออเดอร์ / บิล / รับ-ส่ง |

**ห้ามใช้ BOT_TOKEN ร่วมกัน** ระหว่าง Staff AI กับ FAQ หรือ V3

## วิธีใช้ (ในกลุ่ม staff)

1. เลือกภาษาพนักงาน (Khmer / Thai / Indonesian)
2. 📩 **Customer Asked** → วางข้อความลูกค้า → บอทสรุปความหมายให้พนักงาน
3. ✍️ **Staff Reply** → พิมพ์คำตอบ → บอทแปลเป็นภาษาลูกค้า → Copy ส่ง

## Environment

| Variable | Required | Description |
|----------|----------|-------------|
| `BOT_TOKEN` | Yes | Token บอท Staff AI (BotFather แยกจาก FAQ) |
| `STAFF_GROUP_ID` | Yes | ID กลุ่ม Telegram ของพนักงาน |
| `OPENAI_API_KEY` | Yes | สำหรับแปล |
| `WEBHOOK_URL` | Yes on Render | `https://cherry-staff-ai.onrender.com/telegram` |
| `ALLOWED_USER_IDS` | Optional | ทดสอบใน DM |

## Setup Render (ครั้งแรก)

1. สร้าง Web Service ใหม่ชื่อ `cherry-staff-ai` (แยกจาก `cherry-support-ai` ที่เป็น FAQ)
2. Connect repo นี้
3. ใส่ env ด้านบน
4. ในกลุ่ม staff ส่ง `/group` → copy `STAFF_GROUP_ID` → redeploy
5. BotFather `/setprivacy` → **Disable** (ให้บอทเห็นข้อความในกลุ่ม)

## Local run

```bash
pip install -r requirements.txt
cp .env.example .env
python app.py
```

## Commands

| Command | Purpose |
|---------|---------|
| `/start` | เมนู + คำแนะนำ |
| `/menu` | เมนูหลัก |
| `/lang` | เปลี่ยนภาษาพนักงาน |
| `/group` | แสดง group ID สำหรับ Render |
| `/health` | ตรวจ OpenAI + bot |
