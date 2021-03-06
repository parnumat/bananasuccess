﻿# bananasuccess
/* อธิบาย -e -d -p อ่านเพิ่มเติมได้โดยการพิม "docker run --help" */

/*-it คือ mode interactive terminal*/
/*คำสั่ง ใช้เข้าไปในไฟล์ image*/
docker run -it (repository image)
/*คำสั่ง ใช้เข้าไปในไฟล์ contrainer*/
docker exec -it (name contrainer) bash

/*check ข้อมูลทั้งหมดของ contrainer*/
docker inspect [contrainer name]

/*tag ใช้สร้าง image จาก image commit ใช้สร้าง image จาก contrainer*/
docker tag|commit [name] [name]
/*pull ดึง image จาก docker hub, push นำ image ขึ้น docker hub*/
docker pull|push [name]
/*คำสั่ง commit ทำให้ contrainer ที่เราเซตแล้ว เก็บเป็น image ใหม่*/
docker commit (name or ID contrainer) (newname image)



/* ลง MYSQL version 5.7 REPOSITORY ก็คือ 5.7 */
docker pull mysql:5.7 

/* ลง PHPmyadmin บน docker ที่มี REPOSITORY ก็คือ phpmyadmin/phpmyadmin */
docker pull phpmyadmin/phpmyadmin

/* docker run --name "ชื่อ_container_mysql" -e MYSQL_ROOT_PASSWORD =
 "user จะเท่ากับ root อัตโนมัต ตามด้วย PASSWORD" -d mysql:5.7 */
 /*mount volume คืการ back up ไฟล์ ไว้ใน folder ของเราด้วยเวลา rm contrainer ข้อมูลจะไม่หาย*/
docker run --name icemysql -d -e MYSQL_ROOT_PASSWORD=ice -v ./sql:/var/lib/mysql -p 3306:3306 mysql:5.7

/* docker run --name "ชื่อ_container_phpmyadmin" -d --link icemysql:db "บอกว่าเชื่อมต่อไปที่ DB ของเรา 
 :db บอกว่าเป็น database "  -p 8080:80 "กำหนด port คือ 8080 " phpmyadmin/phpmyadmin */ 
docker run --name phpmy -d --link icemysql:db -p 8080:80 phpmyadmin/phpmyadmin
/*docker-compose.yml ใช้หลักการเดียวกัน*/



/* Dockerfile*/
/*สำสั่ง สร้าง images ที่กำหนดไว้ใน Dockerfile*/
docker build -t [image name] .
/*  EX..
    FROM centos
    RUN yum update -y
    RUN yum install httpd -y

    EXPOSE 80

    command ที่จะส่งตอนเรียก docker run
    CMD["httpd","-DFOREGROUND"]
*/
