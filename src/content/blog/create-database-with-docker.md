---
title: สร้าง database local ตัวไหนก็ได้ด้วย docker
author: your name
pubDatetime: 2023-02-13 19:50:00+07
postSlug: create-database-with-docker
featured: true
draft: false
tags:
  - docker
  - database
ogImage: ""
description: This is the example description of the example post.
---

# สร้าง database local ตัวไหนก็ได้ด้วย docker

![image](/assets/create-database-with-docker/1.jpeg)
เป็นวิธีส่วนตัวที่เราอยากจะใช้ database สักตัว แต่ไม่อยากติดตั้งให้มันวุ่นวาย พอได้มารู้จัก docker รู้สึกว่าช่วยได้มากกกก

ในกรณีนี้ขอยกตัวอย่างเป็น postgres

โดยเรามาที่หน้าของ docker image ที่เราต้องการจะใช้
![image2](/assets/create-database-with-docker/2.jpg)

```bash
docker run --rm -d -e POSTGRES_PASSWORD=1234 -p 5432:5432 postgres
```

จากนั้นก็ใช้ docker command ด้านบน โดยทำการ expose port ออกมานอก container ทำให้ local สามารถใช้ database ได้ โดยที่ไม่จำเป็นต้องติดตั้ง database เลย

ด้วยวิธีนี้ทำให้ผมสามารถเลือก database ตัวไหนก็ได้ตามที่อยากใช้เลยครับ โดยหากเราขี้เกียจเขียน command ทุกครั้งที่จะทำ project ก็สามารถเขียนเป็น docker compose ได้อีกด้วย

แต่เราก็ต้องศึกษา database ที่เราจะใช้ให้ดีด้วยว่าต้องตั้งค่าอย่างไรบ้าง โดยสามารถอ่านได้จาก docker hub ของ database ที่เรานำมาใช้

อย่างในตัวอย่าง เราใช้ port 5432 เนื่องจากเป็น default ของ postgres แต่ถ้าเป็น mariadb จะใช้ port 3306 และ environment variable ก็จะไม่เหมือนกันอีก ก็ต้องดูดีๆนะครับ หวังว่าจะเป็นประโยชน์ครับ
