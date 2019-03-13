# Leanwp; Container

Leanwp; Container คือตัวช่วยสร้าง และติดตั้งแพลตฟอร์ม WordPress ลงบนเซิฟเวอร์จำลอง (ตัวเซิฟเวอร์ถูกสร้างอยู่บน Docker Container)

## ความต้องการของระบบ

#### - Docker Compose

ในการใช้งาน Leanwp; Container นั้น เครื่องคอมพิวเตอร์ที่จะติดตั้ง จำเป็นจะต้องมี Docker Compose ติดตั้งไว้ก่อน  
อ่านรายละเอียดเพิ่มเติม: [วิธีการติดตั้ง Docker Compose](https://docs.docker.com/compose/install).

## เริ่มต้นการใช้งาน

### ดาวน์โหลด Leanwp; Container

ดาวน์โหลด Leanwp; Container [เวอร์ชันล่าสุด](https://github.com/leanwp/container/archive/v0.1.0.zip)  
จากนั้น unzip ไฟล์ที่ดาวน์โหลดมา โดยวางโฟลเดอร์ไว้ที่ใดก็ได้บนเครื่องคอมพิวเตอร์ที่ตั้งการรัน Leanwp; Container

### เริ่มใช้งาน container

หลังจากดาวน์โหลดตัวโปรเจ็ค Leanwp; Container และ unzip ไฟล์แล้ว ให้ใช้โปรแกรม Terminal เปิดเข้าไปที่โฟลเดอร์ Leanwp; Container ที่ได้มาจากขั้นตอนดาวน์โหลด
จากนั้นเพียงแค่รันโค้ดดังต่อไปนี้บนโปรแกรม Terminal

```bash
docker-compose up
```

ตัว Leanwp; Container จะสร้างโฟลเดอร์ขึ้นมาใหม่หนึ่งโฟลเดอร์ บน root โฟลเดอร์, ตัวโฟลเดอร์ที่ถูกสร้างขึ้นมาจะถูกตั้งชื่อไว้ว่า **`html`**  
จากนั้น Leanwp; Container จะดาวน์โหลด และติดตั้ง WordPress ลงบนโฟลเดอร์ `html`

<img width="1552" alt="screen shot 2562-01-12 at 21 10 48" src="https://user-images.githubusercontent.com/2154669/51074195-96b3d800-16ae-11e9-8e52-57c2e0b1a0c3.png">

### ปรับแต่งค่าเริ่มต้น

ผู้ใช้งานสามารถปรับแต่งค่าต่าง ๆ เช่น ชื่อฐานข้อมูล, ชื่อและรหัสผ่านผู้ดูแลระบบ WordPress ได้ที่ไฟล์ [`.env`](https://github.com/leanwp/container/blob/master/.env).
คำอธิบายสำหรับค่าตัวแปรต่าง ๆ สามารถตรวจสอบได้ที่ตารางด้านล่างนี้:

#### Database Credential

| ชื่อตัวแปร             | คำอธิบาย                                                                                              | ค่าเริ่มต้น |
| ------------------- | ---------------------------------------------------------------------------------------------------- | ------------- |
| DB_HOST             | เซิฟเวอร์ของฐานข้อมูล (แนะนำให้คงค่าเริ่มต้นไว้ นอกจากผู้ใช้งานจะมีแผนในการสร้างเซิฟเวอร์ MySQL แยกออกจากตัวเว็บไซต์) | 127.0.0.1     |
| DB_NAME             | ชื่อของฐานข้อมูล (ตัวฐานข้อมูลของแพลตฟอร์ม WordPress จะถูกติดตั้งไว้ที่นี่)                                           | www           |
| DB_USER             | ชื่อบัญชีผู้ใช้งานฐานข้อมูล                                                                                   | wwwadmin      |
| DB_PASSWORD         | รหัสผ่านฐานข้อมูล                                                                                        | wwwpassword   |

#### WordPress Parameters

| ชื่อตัวแปร             | คำอธิบาย                                                                                                 | ค่าเริ่มต้น |
| ------------------- | ------------------------------------------------------------------------------------------------------- | -------------------- |
| WP_VERSION          | เวอร์ชันของ WordPress ที่ต้องการติดตั้ง (หากไม่มีการระบุค่า ตัว Leanwp; Container จะติดตั้ง WordPress เวอร์ชันล่าสุดเสมอ)   |                      |
| WP_DEBUG            | เปิดใช้งานฟีเจอร์ Debug บน WordPress                                                                        | true                 |
| WP_TITLE            | ชื่อเว็บไซต์ WordPress                                                                                      | Leanwp; Container    |
| WP_BASE_URL         | URL ของเว็บไซต์ WordPress (แนะนำให้คงค่าเริ่มต้นไว้ นอกจากว่าผู้ใช้งานมีแผนที่จะตั้งค่า Domain Name เป็นค่าอื่น)              | http://127.0.0.1     |

#### WordPress Admin Account

| ชื่อตัวแปร             | คำอธิบาย                      | ค่าเริ่มต้น              |
| ------------------- | ---------------------------- | -------------------- |
| WP_ADMIN_USER       | บัญชีชื่อผู้ดูแลระบบ (admin)        | admin                |
| WP_ADMIN_PASSWORD   | รหัสผ่านของบัญชีผู้ดูแลระบบ (admin) | password             |
| WP_ADMIN_EMAIL      | อีเมลของบัญชีผู้ดูแลระบบ           | admin@leanwp.dev     |

หากผู้ใช้งานมีการปรับเปลี่ยนค่าใด ๆ แล้ว ผู้ใช้งานจำเป็นจะต้องสร้าง container image ขึ้นมาใหม่อีกรอบ โดยสามารถรันชุดคำสั่งด้านล่างนี้บนโปรแกรม Terminal บนเครื่องคอมพิวเตอร์ที่ติดตั้ง Leanwp; Container
```bash
docker-compose up --build
```

<img width="1008" alt="screen shot 2562-01-12 at 21 15 35" src="https://user-images.githubusercontent.com/2154669/51074240-3a9d8380-16af-11e9-9606-eecdcef87297.png">

## ร่วมพัฒนา

หากใครสนใจร่วมพัฒนา หรือเสนอไอเดียต่าง ๆ สำหรับตัวโปรเจ็ค Leanwp; Container สามารถอ่านขั้นตอนในการส่ง patch, เสนอไอเดีย, รวมถึงแจ้งปัญหาการใช้งานด้านล่างนี้ได้เลยครับ
หมายเหตุ. ขอบคุณที่สนใจร่วมพัฒนาตัวโปรเจ็ค เราอยากเห็นทุกคนช่วยกันพัฒนาตัว Leanwp; Container ให้มันแมส :D

### ส่งโค้ดเพื่อปรับปรุงโปรเจ็ค

หากใครสนใจที่จะส่งโค้ดเพื่อปรับปรุงโปรเจ็ค สามารถทำได้โดย 3 ขั้นตอน ดังนี้

#### 1. สร้าง issue ticket ขึ้นมาใหม่, โดยตั้งชื่อ ticket ว่า "Proposal"

ก่อนที่จะเริ่มปรับปรุงแก้ไขตัวโปรแกรมใด ๆ เราขอแนะนำให้ [สร้าง issue ticket ขึ้นมาใหม่](https://github.com/leanwp/container/issues/new) โดยตั้งชื่อ ticket ว่า: **"[Proposal] หัวข้อข้อเสนอ หรือไอเดียที่ต้องการปรับปรุง"**  

#### 2. รอให้ proposal ticket Wait until the proposal got approved

หลังจากที่ผู้พัฒนานำเสนอ proposal แล้ว จะมีทีมงานตรวจสอบรายละเอียด proposal และติดแท็ก "approved"
กรุณารอให้ proposal นั้น ๆ ถูกติดแท็ก "approved" ก่อนที่จะเริ่มต้นแก้ไขใด ๆ 
ทั้งนี้เพื่อป้องกันเหตุการณ์ที่มีการแก้ไข หรือปรับปรุงตัวโปรเจ็ค แต่ตัวไอเดียนั้น ๆ ไม่ตรงกับทิศทางการพัฒนาโปรเจ็ค

#### 3. สร้าง pull request เพื่อส่งโค้ดเข้าสู่โปรเจ็ค

หลังจากที่ตัว proposal ถูกติดแท็ก "approved" แล้ว ผู้พัฒนาสามารถเริ่มปรับแก้โปรแกรม และส่ง patch เข้ามาที่ตัวโปรเจ็คหลัก, โดยสามารถสร้าง pull request เข้ามาที่ branch `master` โดยตั้งชื่อ pull request ว่า: **"[Proposal #หมายเลขproposal] หัวข้อข้อเสนอ หรือไอเดียที่ต้องการปรับปรุง"**

..  
.  

ศึกษาวิธีการสร้าง pull request เพิ่มเติมได้ที่ลิงก์ดังต่อไปนี้: [https://help.github.com/articles/about-pull-requests](https://help.github.com/articles/about-pull-requests)

### แจ้งปัญหาการใช้งาน

หากพบปัญหาการใช้งานใด ๆ สามารถแจ้งปัญหาเข้ามาได้ โดยสร้าง [GitHub's issue ticket](https://github.com/leanwp/container/issues).

ศึกษาวิธีการแจ้งปัญหาการใช้งานเพิ่มเติมได้ที่ลิงก์ดังต่อไปนี้: [https://guides.github.com/features/issues](https://guides.github.com/features/issues)

## License

Leanwp; Container is open-sourced software released under the [MIT License](https://opensource.org/licenses/MIT).
