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

<img width="1920" height="1019" alt="Topology" src="https://github.com/user-attachments/assets/3936bb38-c57c-4e56-b51b-746b31bde02b" />

  
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

<img width="873" height="210" alt="Router-Subinterfaces" src="https://github.com/user-attachments/assets/1cf691fc-f632-4c5d-8600-57dabe09c46a" />


  
*صورة تبين إعدادات Subinterfaces على الراوتر*

---

## 4️ اختبار الاتصال (Connectivity Tests)
### 4.1 اختبار PING بين VLANS
<img width="1920" height="1017" alt="Ping_Vlans" src="https://github.com/user-attachments/assets/b4d8fd15-5768-4950-a189-399efca8530c" />


  
*تأكيد أن الأجهزة في VLAN مختلفة تتواصل بنجاح*

### 4.2 اختبار PING إلى السيرفر
<img width="1920" height="1017" alt="Png_Server" src="https://github.com/user-attachments/assets/43727804-b936-472f-8b8c-21eedb654ac1" />


  
*تأكيد أن DHCP يعمل والأجهزة تستطيع الوصول للسيرفر*

### 4.3 Tracert
<img width="1920" height="1019" alt="Tracert" src="https://github.com/user-attachments/assets/300b21e7-4d85-468f-9252-45c484645c8c" />


 
*توضيح مسار الحزم من جهاز في VLAN إلى السيرفر*

---

## 5️ إعداد DHCP على السيرفر
- تم عمل DHCP POOL لكل VLAN لإعطاء IP تلقائي للأجهزة     
- مثال: DHCP POOL10 يبدأ التوزيع من IP : 192.168.10.11

<img width="1920" height="1017" alt="DHCP-POOL" src="https://github.com/user-attachments/assets/700cb454-05b3-4eda-829d-596223e1730d" />


  
*صورة توضح إعداد DHCP لكل VLAN*

---

## 6️ OSPF Routing
- تم ربط الراوترات الثلاثة باستخدام بروتوكول OSPF لتبادل معلومات التوجيه ديناميكيًا.  
- تم تعريف الشبكات مباشرة على الواجهات (Interface-based).

**مثال Router1:**

## <img width="876" height="98" alt="OSPF_Neighbors" src="https://github.com/user-attachments/assets/b985d443-63f3-4266-82c1-20bd4983857a" /> 
## <img width="871" height="558" alt="OSPF_Routing_Table" src="https://github.com/user-attachments/assets/898fa54b-e10c-4b49-97ed-45694c16674b" />
<img width="869" height="145" alt="OSPF-Details" src="https://github.com/user-attachments/assets/62b41c89-c652-4904-b282-4eb33e16b0f1" />



---


LinkedIn : https://www.linkedin.com/in/ali-alzahrani-b8a7a3347/

Email : assz1419@hotmail.com
