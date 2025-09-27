# OSPF_VLAN_DHCP_LAB
r
# لاب عملي : OSPF,Inter-VLAN Routing,VLANs and DHCP

## وصف المشروع
هذا اللاب يعرض كيفية تصميم شبكة متعددة VLANs (10 VLANs) وربطها باستخدام Router-on-a-Stick، مع خادم DHCP لكل VLAN، وربط الراوترات الثلاثة باستخدام بروتوكول OSPF للتوجيه الديناميكي.  
الهدف: تطوير مهارات إعداد VLANs، التوجيه بين VLANs، إدارة DHCP، وفهم التوجيه الديناميكي باستخدام OSPF.

---

## 1 تصميم الشبكة (Topology)
- 9 أجهزة موزعة على 9 VLANs مختلفة.  
- راوتر مركزي يربط VLANs (Router-on-a-Stick).  
- سيرفر DHCP في VLAN 100.  
- ثلاث راوترات متصلة ببعضها باستخدام OSPF.

<img width="1920" height="1080" alt="Topology" src="https://github.com/user-attachments/assets/cb2f4984-1887-4b74-8864-e6c52f1d5ee9" />
  
*صورة توضح التصميم الكامل للشبكة*

---

## 2 إعداد VLANs
| VLAN | اسم VLAN    | Subnet            | Default Gateway |
|------|------------|-----------------|----------------|
| 10   | HR         | 192.168.10.0/24 | 192.168.10.1   |
| 20   | IT      | 192.168.20.0/24 | 192.168.20.1   |
| 30   | Finance    | 192.168.30.0/24 | 192.168.30.1   |
| 40   | SALES         | 192.168.40.0/24 | 192.168.40.1   |
| 50   | ADMIN  | 192.168.50.0/24 | 192.168.50.1   |
| 60   | GUEST    | 192.168.60.0/24 | 192.168.60.1   |
| 70   | RND      | 192.168.70.0/24 | 192.168.70.1   |
| 80   | ENG        | 192.168.80.0/24 | 192.168.80.1   |
| 90   | SUPPORT      | 192.168.90.0/24 | 192.168.90.1   |
| 100  | Server     | 192.168.100.0/24| 192.168.100.1  |

---

## 3️ إعداد الراوتر (Subinterfaces)
- كل VLAN له Subinterface على الراوتر مع IP خاص.  
- تم تفعيل Inter-VLAN Routing.

<img width="1920" height="1080" alt="Router" src="https://github.com/user-attachments/assets/1bce6d81-a16e-4e45-83a3-36f79ed728ee" />
  
*صورة تبين إعدادات Subinterfaces على الراوتر*

---

## 4️ اختبار الاتصال (Connectivity Tests)
### 4.1 اختبار PING بين VLANS
<img width="1920" height="1080" alt="Ping_Vlans" src="https://github.com/user-attachments/assets/28e9051f-e0b6-40d8-9a07-d10a6ef4b463" />

  
*تأكيد أن الأجهزة في VLAN مختلفة تتواصل بنجاح*

### 4.2 اختبار PING إلى السيرفر
<img width="1920" height="1080" alt="Png_Server" src="https://github.com/user-attachments/assets/119ec1b7-d770-4504-a42c-9477a8dd3050" />

  
*تأكيد أن DHCP يعمل والأجهزة تستطيع الوصول للسيرفر*

### 4.3 Tracert
<img width="1920" height="1080" alt="Tracert" src="https://github.com/user-attachments/assets/8582791e-d9ff-43b5-8c2c-988901b62023" />

 
*توضيح مسار الحزم من جهاز في VLAN إلى السيرفر*

---

## 5️ إعداد DHCP على السيرفر
- تم عمل DHCP POOL لكل VLAN لإعطاء IP تلقائي للأجهزة     
- مثال: DHCP POOL10 يبدأ التوزيع من IP : 192.168.10.11

<img width="1920" height="1080" alt="DHCP" src="https://github.com/user-attachments/assets/d54987de-f72b-43d0-a173-effd74aadc8a" />
  
*صورة توضح إعداد DHCP لكل VLAN*

---

## 6️ OSPF Routing
- تم ربط الراوترات الثلاثة باستخدام بروتوكول OSPF لتبادل معلومات التوجيه ديناميكيًا.  
- تم تعريف الشبكات مباشرة على الواجهات (Interface-based).

**مثال Router1:**

<img width="852" height="638" alt="OSPF_Routing_Table" src="https://github.com/user-attachments/assets/5b8ac4d3-5f99-48c1-970b-cfcc151af725" />
<img width="852" height="182" alt="OSPF_Neighbors" src="https://github.com/user-attachments/assets/1e018e5d-4222-474a-a984-fbacb3044b4e" />

---


LinkedIn : https://www.linkedin.com/in/ali-alzahrani-b8a7a3347/

Email : assz1419@hotmail.com
