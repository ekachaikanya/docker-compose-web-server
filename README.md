# docker-compose-web-server
Week06: ทดลองใช้งาน Docker Compose : สร้าง Web Server

**docker-compose.yml**
```bash
name: my-web-project                      # (เลือกได้) กำหนดชื่อโปรเจกต์หลัก เพื่อใช้เป็นชื่อนำหน้าคอนเทนเนอร์ตัวอื่น
services:
  my-web-server:                          # ชื่อ Service ที่เราตั้งเอง
    image: nginx:latest                   # ใช้ Image ชื่อ nginx รุ่นล่าสุด
    container_name: [username]-myweb      # ใส่ชื่อคอนเทนเนอร์
    ports:
      - "8080:80"          # Map Port: เข้าผ่านเครื่องเราที่ 8080 -> ส่งไปที่ Port 80 ของ Container
```

**index.html**
```bash
<!-- สร้างไฟล์ index.html ไว้ในโฟลเดอร์ html/ -->

<h1>สวัสดีครับ! นี่คือหน้าเว็บของผมผ่าน Docker</h1>
<p>แก้ไขไฟล์นี้ในเครื่อง แล้วกด Refresh ได้เลย!</p>
```


**Docker Compose : เพิ่ม Bind mount**

```bash
# ทำ bind mount เพื่อ map volume กับโฟลเดอร์งาน
name: my-web-project 
services:
  my-web-server:
    image: nginx:latest
    container_name: [username]-myweb
    ports:
      - "8080:80"
    volumes:
      # [โฟลเดอร์ในเครื่องเรา] : [โฟลเดอร์ใน Container]
      - ./html:/usr/share/nginx/html
```

docker compose up -d
หรือ
docker compose up -d my-web-server

docker compose down
