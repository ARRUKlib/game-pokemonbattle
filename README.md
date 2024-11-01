# Pokemon Battle Game
เกมต่อสู้โปเกมอนที่จำลองการต่อสู้แบบเทิร์นเบส พัฒนาด้วย React TypeScript, Python Backend และ PostgreSQL


## หลักการพัฒนา
  ### โปรเจกต์นี้เป็นเกมต่อสู้โปเกมอนที่พัฒนาโดยใช้หลักการออกแบบเชิงวัตถุ (Object-Oriented Design) เพื่อจำลองการต่อสู้ระหว่างโปเกมอน โครงสร้างหลักของโปรเจกต์ประกอบด้วย:
    1. คลาส Pokemon: กำหนดคุณลักษณะและความสามารถพื้นฐานของโปเกมอน เช่น ชื่อ, พลังชีวิต, และท่าโจมตี
    2. คลาส Battle: จัดการกลไกการต่อสู้ระหว่างโปเกมอนสองตัว รวมถึงการโจมตีและการคำนวณความเสียหาย โดยฝั่งที่มีสปีดเยอะกว่าจะได้โจมตีก่อน แต่หากสปีดเท่ากัน ผู้เล่นจะได้โจมตีก่อน
    3. คลาส EXP: กำหนดการได้รับ EXP สำหรับผู้เล่น เมื่อผู้เล่นเล่นไปเรื่อยๆ จะมีโอกาสเพิ่ม level และหาก level สูงขึ้น ก็ยิ่งมีโอกาสได้การ์ดประเภท rare ที่มีพลังการโจมตีสูงขึ้นด้วย
  ### โปรเจคถูกออกแบบมาประกอบด้วย 3 ส่วนหลัก:
    1. Frontend: พัฒนาด้วย React TypeScript เพื่อสร้าง UI ที่ตอบสนองและมีประสิทธิภาพ
    2. Backend: พัฒนาด้วย Python ใช้ FastAPI เพื่อสร้าง RESTful API ที่รวดเร็วและมีประสิทธิภาพ
    3. Database: ใช้ PostgreSQL เพื่อจัดเก็บข้อมูลผู้เล่น, โปเกมอน, และสถิติการเล่น


## API ที่สำคัญ
  1. GET /api/pokemon: ดึงรายการโปเกมอนทั้งหมดที่มีในเกม
  2. POST /api/battle/start: เริ่มการต่อสู้ระหว่างโปเกมอนสองตัว
  3. POST /api/battle/attack: ส่งคำสั่งโจมตีในการต่อสู้
  4. GET /api/player/{player_id}/exp: ดึงข้อมูล EXP และ Level ของผู้เล่น
  5. POST /api/player/{player_id}/level-up: อัพเดท Level ของผู้เล่นเมื่อได้รับ EXP เพียงพอ


## วิธี Deploy
  ### ข้อกำหนดเบื้องต้น
    - Node.js (v14 หรือสูงกว่า)
    - Python (v3.8 หรือสูงกว่า)
    - PostgreSQL
    - Bun (สำหรับ Frontend)


## ขั้นตอนการ Deploy
### 1. Clone โปรเจกต์:
```
bash
git clone https://github.com/your-username/pokemon-battle-game.git
cd pokemon-battle-game
```

### 2. ติดตั้ง Dependencies:
สำหรับ Frontend:
```
bash
cd frontend
bun install
```

สำหรับ Backend:
bash
cd backend
pip install -r requirements.txt

ตั้งค่า Environment Variables:
สร้างไฟล์ .env ในโฟลเดอร์ backend และกำหนดค่าต่างๆ เช่น:
text
DATABASE_URL=postgresql://username:password@localhost/dbname
SECRET_KEY=your_secret_key

สร้างฐานข้อมูล:
bash
psql -c "CREATE DATABASE pokemon_battle"

รัน Database Migrations:
bash
cd backend
python manage.py db upgrade

Build Frontend:
bash
cd frontend
bun run build

รัน Backend Server:
bash
cd backend
python main.py

รัน Frontend Server (สำหรับ Development):
bash
cd frontend
bun run dev

การ Deploy บน Production
สำหรับการ Deploy บน Production environment คุณอาจต้องใช้ services เพิ่มเติม เช่น:
ใช้ Nginx เป็น reverse proxy
ใช้ Gunicorn เป็น WSGI server สำหรับ Python backend
ใช้ PM2 หรือ systemd เพื่อจัดการ process
ตัวอย่าง Dockerfile สำหรับ Frontend:
text
FROM oven/bun
WORKDIR /app
COPY package.json bun.lockb ./
RUN bun install
COPY . .
RUN bun run build
CMD ["bunx", "--bun", "vite", "preview", "--host"]

ตัวอย่าง Dockerfile สำหรับ Backend:
text
FROM python:3.9
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "main.py"]

การรัน Local Development
รัน Backend:
bash
cd backend
python main.py

รัน Frontend:
bash
cd frontend
bun run dev

เปิดเบราว์เซอร์และไปที่ http://localhost:5173
