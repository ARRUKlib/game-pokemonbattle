# ใช้ Node.js image ที่เป็นพื้นฐาน
FROM node:16

# ตั้งค่าโฟลเดอร์ทำงานภายใน container
WORKDIR /usr/src/app

# คัดลอกไฟล์ package.json และ package-lock.json ไปยัง container
COPY package*.json ./

# ติดตั้ง dependencies
RUN npm install

# คัดลอกโค้ดทั้งหมดไปยัง container
COPY . .

# เปิดพอร์ตที่ต้องการ (เช่น 3001)
EXPOSE 3001

# คำสั่งสำหรับรันแอปพลิเคชัน
CMD ["npm", "start"]