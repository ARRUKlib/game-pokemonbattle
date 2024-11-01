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

# สร้างแอปพลิเคชัน React สำหรับ production
RUN npm run build

# ใช้ Nginx เพื่อเสิร์ฟแอปพลิเคชัน React ที่ถูก build แล้ว
FROM nginx:alpine
COPY --from=0 /usr/src/app/build /usr/share/nginx/html

# เปิดพอร์ตที่ต้องการ (เช่น 80)
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]