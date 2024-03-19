### Flow การทำงานของระบบ Captive Portal
![Image](https://user-images.githubusercontent.com/20470718/108593826-b0a16800-73a8-11eb-991e-201b8a92b249.png)
### ขั้นตอนการทำงานของระบบ
- ผู้ใช้ออก Internet แต่ Firewall ไม่มี User Mapping
- Firewall redirect traffic ไปที่ External Captive Portal (Ext-CP)
- ผู้ใช้ Authentication ผ่านหน้า Ext-CP เพื่อเช็ค User และ Password กับ Active Directory
- Ext-CP ส่ง XMLAPI ไปที่ Firewall เพื่อทำ User Mapping (IPv4 และ IPv6)
- ผู้ใช้ออก Internet ได้ปกติ

## คู่มือการใช้งานระบบ ฝั่งAdminใช้งาน
### เมื่อเข้ามาระบบผ่านการloginในครั้งแรก

        - ให้ไปEdit servers ให้ไปดูวิธีการที่ข้อ(6.2 Servers)
        - จัดกลุ่มusers ให้ไปดูวิธีการที่ข้อ(5.Group users)
        - จัดการConfig ต่างๆ ให้ไปดูวิธีการที่ข้อ(6.Setting)
        - Connection Test ให้ไปดูวิธีการที่ข้อ(3.Configuration and Connection Test)
        - ทำการSynchronize users ให้ไปดูวิธีการที่ข้อ(4.Users)

1.Login/logout 

  1.1 Login 
  
        - เข้าไปที่ http://[domain.com:8000]/login
        - เมื่อAdmin เข้าระบบมาครั้งแรก 
<img width="965" alt="1" src="https://user-images.githubusercontent.com/40853593/122517499-4b017780-d03a-11eb-96a1-f6257c3c4cfa.png">

        - ระบบจะพาAdminไปเปลี่ยนPassword
  ![screencapture-localhost-8000-login-set-password-for-admin-page-parinpond-baree-io-2021-06-22-14_02_39](https://user-images.githubusercontent.com/40853593/122880663-72bb4d00-d364-11eb-99ba-c3f7403bbc74.png)

        - จากนั้นจะกลับมาในหน้าlogin อีกครั้ง ให้ทำการlogin กรอก usernameและpassword เพื่อเข้าไปในระบบ
  
<img width="964" alt="3" src="https://user-images.githubusercontent.com/40853593/122517594-69677300-d03a-11eb-8926-a3a4c760d64f.png">

  1.2 การLogout ออกจากระบบ
  
        - คลิกที่มุมบนได้ขวามือที่ชื่อEmailของAdmin และเลือกLogout
  
<img width="1260" alt="5" src="https://user-images.githubusercontent.com/40853593/122524052-e5b18480-d041-11eb-919d-0c5eff47729a.png">

        - มีPopupให้ยืนยันการออกจากระบบ
  
<img width="592" alt="6" src="https://user-images.githubusercontent.com/40853593/122524072-ea763880-d041-11eb-87b5-26d422c4ea38.png">
  
2.Dashboard

**มีfucntionการทำงานดังนี้**

          - Report Login success/failed  แสดงข้อมูลdefault เป็นAD ระยะเวลา1เดือน เป็นรูปแบบpie chart สามารถค้นหาโดยเลือกประเภท<img width="150" alt="6" src="https://user-images.githubusercontent.com/40853593/122872171-400c5700-d35a-11eb-8d2e-94dc568ee2c4.png">
          - Servers แสดงข้อมูลเกี่ยวกับServers ADที่ต้องการดึงข้อมูล
          - Group users แสดงข้อมูลเกี่ยวกับประเภทของกลุ่มUsers
          - Firewall แสดงข้อมูลเกี่ยวกับFirewall จะออกเป็นสองประเภท syslog users id agent และ syslog external
          - Email แสดงข้อมูลเกี่ยวกับServers email ที่เป็นตัวใช้ส่งemailไปยังusers
          - Authen Login/Logout แสดงlogระยะเวลา5วัน
![1](https://user-images.githubusercontent.com/40853593/124434083-a901bf00-dd9d-11eb-9e19-3f06764e709c.png)
3.Configuration and Connection Test 

**มีfucntionการทำงานดังนี้**

        - กดเลือกที่ เมนูชื่อ Test 
        - ทางซ้ายมือจะแสดง functionการtest 4 function ได้แก่ - User id agent,Syslog external,AD,LDAP Login,Google Authenticator 
        - ทางขวามือจะแสดง การดูLogหลังจากทดสอบfunctionต่างๆ
        
![2](https://user-images.githubusercontent.com/40853593/124434740-6f7d8380-dd9e-11eb-855f-b5e98461020d.png)

        - ตัวอย่างการทดสอบ LDAP Login กรอก username และpassword ที่ต้องการทดสอบ
![2](https://user-images.githubusercontent.com/40853593/124434971-b4091f00-dd9e-11eb-8cfc-d33946ebceb7.png)

        - ตัวอย่างการทดสอบ Google Authenticator 
<p align="center"><img width="400" alt="" src="https://user-images.githubusercontent.com/40853593/124435544-4d383580-dd9f-11eb-92a5-666182ec8d8a.png"></p>

        - ตัวอย่างการทดสอบ Google Authenticator เมื่อscan QR code ในApp Google Authenticator นำpasscode มากรอกที่ระบบ
<p align="center"><img width="250" alt="" src="https://user-images.githubusercontent.com/40853593/122528013-14c9f500-d046-11eb-8a61-cd5f41416f9b.PNG"></p>

4.Users 

![u1](https://user-images.githubusercontent.com/40853593/122864439-daff3400-d34e-11eb-9546-7d7bfa162de8.png)

**มีfucntionการทำงานดังนี้**

4.1 Add admin list 

        - เพิ่มAdmin กรอกE-mailระบบจะทำการส่งPasswordไปยังE-mail

<img width="400" alt="" src="https://user-images.githubusercontent.com/40853593/122890042-8919d680-d36d-11eb-95d9-49251005b4ce.png">

4.2 Search ค้นหาด้วย E-mail และUsername

4.3 Edit 

        - เมื่อedit Group users เป็นTwo-factor authenticator หรือ Admin ระบบจะส่งEmail ไปแจ้งQR code หรือPassword

![u2](https://user-images.githubusercontent.com/40853593/122901216-89b76a80-d377-11eb-8055-41034c82176b.png)

        - ตัวอย่างระบบส่ง ไปแจ้งQR code

<img width="500" alt="" src="https://user-images.githubusercontent.com/40853593/122906177-1106dd00-d37c-11eb-9709-01da49996578.png">

        - เมื่อUsers ได้อยู่ในGroup Two-factor authenticator แล้วจะมีปุ่มReset token เมื่อกดปุ่มนี้ระบบจะทำการGennerate QR codeใหม่และส่งEmailไปหาUsersนั้น

<img width="1104" alt="" src="https://user-images.githubusercontent.com/40853593/122906249-2976f780-d37c-11eb-963d-0fdb5b54a033.png">

4.4 Synchronize users แบบManual เมื่อกดปุ่มlogicจะทำงานดังนี้

        1.Connect to AD ดึงข้อมูลจากAD
        
        2.Insert ข้อมูลจากAD ลงqueue (ใช้tableในdatabaseเป็นqueue)
        
        3.เช็คข้อมูลที่Synchronizeไม่สำเร็จโดยเช็คจากflag ที่เราทำการmarkไว้ก่อน จากนั้นทำการรันซ่อม
        
        4.Update flag เพื่อจะเริ่มการ synchronization
        
        5.Select queue และนำค่าobjectguid (เป็นPrimary key)ไปเช็คกับข้อมูลUsersในระบบว่าเคยมีหรือไม่?
          - ถ้า[มี]ให้Update data
          - ถ้า[ไม่มี]ให้ Create data
          - ระหว่างการ Update/Create ทำการจัดกลุ่ม group users ว่าอยู่กลุ่มไหน โดยอิงจากการconfigในระบบหลังบ้านว่าเลือกgroup dn 
          อยู่ใน group usersไหน ถ้าทางADไม่มีการจัดgroup dnมาให้default จะอยู่Users
          - เมื่อทำoperationข้างตันเสร็จ จะทำการลบqueue by row id และ update flag synchronization ที่users ว่าprocess เสร็จแล้ว
          
        6.Check tb users อีกครั้ง ด้วยflag ที่ยังไม่ได้ทำการprocess 
          - ยกเว้นtype ที่เป็นadmin และobjectguidเป็นค่าว่าง ความหมายคือเป็นusers admin ที่ระบบสร้างขึ้นมาโดยไม่มีข้อมูลในAD
          จึงไม่ได้ทำการปรับปรุงข้อมูล
          - เมื่อทำการCheck ข้อมูลอีกรอบจะดูrowที่flagยังไม่ได้ทำการprocess ส่งข้อมูลไปcheck ที่ADถ้าไม่เจอข้อมูล ทำการลบข้อมูลนั้นออกจากระบบ 
          ถ้าเจอให้ปรับปรุงข้อมูล
          
        7.สรุปผล เขียนlog  Usera AD total ,created, updated, deleted, disable, repair
        
4.5 วิธีตั้งเวลาcronjob ตั้งที่path ดังต่อไปนี้

``
http://[domain.com:8000]/synchronize_users/process
``         

5.Group users

![g1](https://user-images.githubusercontent.com/40853593/122864466-e3f00580-d34e-11eb-8264-337dfddacec5.png)

5.1 Add Group users 

        - เพิ่มประเภทGroup users ใหม่โดยผูกกับThemeของระบบ
![g3](https://user-images.githubusercontent.com/40853593/122864471-e5b9c900-d34e-11eb-8ffb-71443301d6c9.png)

5.2 Add Group DN

    - ทางด้านซ้ายสามารถกดเลือกGroup DN ให้อยู่ภายในใต้Group users เพื่อเวลาSynchronize usersจะได้นำข้อมูลConfigเหล่านี้ไปจัดกลุ่ม 
    
![g5](https://user-images.githubusercontent.com/40853593/123030160-8621f300-d40c-11eb-9ab0-5695c1dbaa8c.png)

    - กรณีไม่มีข้อมูลทางด้านซ้ายสามารถกดเลือก ให้ไปEdit Serversก่อนเพื่อดึงข้อมูลGroup DNมา
    
![g4](https://user-images.githubusercontent.com/40853593/123030170-8ae6a700-d40c-11eb-8e1e-a7a21e57fcc6.png)

6.Setting   

6.1 Firewall

**มีfucntionการทำงานดังนี้**

        - แสดงconfigของFirewall โดยการส่งผ่านแบบSyslog แบบออกเป็น2ประเภท Syslog และ Syslog external
        - Syslogเป็นตัวหลักที่ใช้ส่งdataไปที่Firewall 
        - Syslog external มีเครื่องอื่นอยากดูlog สามารถยิงไปไปได้ ตอนนี้ได้แค่1เครื่อง
        - ปุ่มVerify users id agent & connectionและVerify users id agent & connection[external] 
        ใช้เพื่อทำการทดสอบconnection เมื่อกดปุ่มจะพาไปดูlogที่หน้า test connection
        
![F1](https://user-images.githubusercontent.com/40853593/123032912-0d716580-d411-11eb-88f8-c9c947e82862.png)

        - หน้าจอEdit ข้อมูลSyslog
![F2](https://user-images.githubusercontent.com/40853593/123032927-13674680-d411-11eb-855b-2d1a0e67a4b4.png)

6.2 Servers

**มีfucntionการทำงานดังนี้**
แสดงรายการ config servers 
<img width="50" alt="" src="https://user-images.githubusercontent.com/40853593/124442030-845e1500-dda6-11eb-89ac-2ad9cf4cb18b.png"> View ดูข้อมูล

<img width="50" alt="" src="https://user-images.githubusercontent.com/40853593/124442207-b1aac300-dda6-11eb-8851-7e530e34b87f.png"> Edit ข้อมูล

<img width="50" alt="" src="https://user-images.githubusercontent.com/40853593/124442217-b2dbf000-dda6-11eb-943e-0b56f83acccd.png"> ปุ่มVerify AD authentication & connection ใช้เพื่อทำการทดสอบconnection เมื่อกดปุ่มจะพาไปดูlogที่หน้า test connection

<img width="50" alt="" src="https://user-images.githubusercontent.com/40853593/124442220-b3748680-dda6-11eb-84e5-c7c3b2544425.png"> ลบข้อมูล
        

        
![1](https://user-images.githubusercontent.com/40853593/124440192-917a0480-dda4-11eb-88af-41299e812827.png)

6.3 Theme

**มีfucntionการทำงานดังนี้**

        - แสดงรายการThemeต่างๆ
![t1](https://user-images.githubusercontent.com/40853593/122540312-b5bead00-d052-11eb-809b-cd430eb0aa51.png)

        - สามารถทำการEdit theme ชื่อของบริษัท,สีเมนูด้านซ้าย,เมนูด้านบน รวมไปถึงlogo
![t2](https://user-images.githubusercontent.com/40853593/122540324-b9523400-d052-11eb-9de3-418f649747e3.png)

        - หน้าจอAdd Theme
![t3](https://user-images.githubusercontent.com/40853593/122540337-bb1bf780-d052-11eb-8e83-494d0e225ae7.png)

6.4 Backup

**มีfucntionการทำงานดังนี้**

        - Import config การนำfile sql ที่เคยExport configไปimportเข้าไปยังเดิม
        - Export config ระบบทำการดึงข้อมูลจากdatabase ณ ขณะนั้น ออกมาเป็นfile sqlให้
        - Log synchronize users ระบบทำการดึงข้อมูลจากdatabase เฉพาะข้อมูลsynchronize users เป็นfile csvออกมาให้
        - Log authentication ระบบทำการดึงข้อมูลจากdatabase เฉพาะข้อมูลauthentication เป็นfile csvออกมาให้
        - Log email ระบบทำการดึงข้อมูลจากdatabase เฉพาะข้อมูลการส่งemail เป็นfile csvออกมาให้
        
![b1](https://user-images.githubusercontent.com/40853593/122540388-ccfd9a80-d052-11eb-8053-3e397f2f7e4b.png)

6.5 Email

**มีfucntionการทำงานดังนี้**

        - ด้านซ้ายแสดงรายละเอียดconfig email ด้านขวาแสดงlogการส่งemail
![e4](https://user-images.githubusercontent.com/40853593/122540432-d71f9900-d052-11eb-8065-96ed11f6a6ce.png)

        - เมื่อกดปุ่มEdit email servers จะขึ้นรายละเอียดให้แก้ไขข้อมูล
![e2](https://user-images.githubusercontent.com/40853593/122540451-dbe44d00-d052-11eb-9390-468e6e50900b.png)

        - เมื่อกดปุ่ม Verify email servers จะขึ้นpop up ให้กรอกemailที่ต้องการทดสอบ ผลการทดสอบจะแสดงด้านขวาlogการส่งemail
![e3](https://user-images.githubusercontent.com/40853593/122540447-dab32000-d052-11eb-87d2-a080d0a0dd81.png)

        - ตัวอย่าง ระบบส่งEmailไปทดสอบ
![e1](https://user-images.githubusercontent.com/40853593/122540454-dc7ce380-d052-11eb-98bc-f15c9b5db0af.png)

7.Log

**มีfucntionการทำงานดังนี้**

7.1 Authentication

        - แสดงlog การauthentication จะdefault 3วัน สามารถเลือกวัน,คำค้นหา และexport เป็นfile csvได้

![l1](https://user-images.githubusercontent.com/40853593/122710600-d709de00-d28a-11eb-993a-8a741fef976b.png)

7.2 Synchronize users

        - แสดงlog การsynchronize users จะdefault 3วัน สามารถเลือกวัน,คำค้นหา และexport เป็นfile csvได้
        
![l2](https://user-images.githubusercontent.com/40853593/122710614-de30ec00-d28a-11eb-85a2-18fe6664d1e0.png)

7.3 Email

        - แสดงlog การส่งemail จะdefault 3วัน สามารถเลือกวัน,คำค้นหา และexport เป็นfile csvได้
        
![l3](https://user-images.githubusercontent.com/40853593/122710631-e38e3680-d28a-11eb-81a5-d3d8384bbc1d.png)

## คู่มือการใช้งานระบบ ฝั่งUsersใช้งาน

เข้าไปที่ http://[domain.com:8000]/

แบ่งออกเป็น 2ประเภท ในการlogin
1. Users 

        - กรอก username และpassword  
    
![1](https://user-images.githubusercontent.com/40853593/123050848-56361800-d42b-11eb-9120-04f50bf0aab2.png)

        - ผลลัพธ์แสดงการเข้าใช้งานอินเตอร์เน็ตและปุ่มlogout
        
![2](https://user-images.githubusercontent.com/40853593/123050868-59310880-d42b-11eb-829a-f410409fd201.png)

2. Two-factor Google Authenticator

        - กรอก username และpassword
        
![3](https://user-images.githubusercontent.com/40853593/123050872-5a623580-d42b-11eb-9331-7f1b17ff55c7.png)

        - ระบบตรวจสอบว่าอยู่ในกลุ่มTwo-factorsหรือไม่? ถ้าอยู่ผ่านไปหน้ายืนยันตัวตน
        
![4](https://user-images.githubusercontent.com/40853593/123050876-5afacc00-d42b-11eb-954b-8bf5ca10fcae.png)

        - Users ทำการเปิดEmail ที่ระบบได้ส่งQR codeไปให้และทำการสแกน QR code ถ้าไม่มีApplication Google Authenticator ให้ไปดาวน์โหลดก่อน

<img width="600" alt="" src="https://user-images.githubusercontent.com/40853593/123050879-5b936280-d42b-11eb-97eb-5bd243ad9d10.png">

        - ทำCode ที่ได้นำไปกรอกที่ระบบและกดตรวจสอบ
        
<img width="400" alt="" src="https://user-images.githubusercontent.com/40853593/123050882-5c2bf900-d42b-11eb-9857-09ba10ed001d.jpg">


        
        
        
        
# CaptivePortal-SAML
