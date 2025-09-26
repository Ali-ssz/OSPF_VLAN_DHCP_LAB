# OSPF_VLAN_DHCP_LAB
r
# لاب عملي: VLANs مع Inter-VLAN Routing، DHCP وOSPF

## وصف المشروع
هذا اللاب يعرض كيفية تصميم شبكة متعددة VLANs (10 VLANs) وربطها باستخدام Router-on-a-Stick، مع خادم DHCP لكل VLAN، وربط الراوترات الثلاثة باستخدام بروتوكول OSPF للتوجيه الديناميكي.  
الهدف: تطوير مهارات إعداد VLANs، التوجيه بين VLANs، إدارة DHCP، وفهم التوجيه الديناميكي باستخدام OSPF.

---

## 1 تصميم الشبكة (Topology)
- 9 أجهزة موزعة على 9 VLANs مختلفة.  
- راوتر مركزي يربط VLANs (Router-on-a-Stick).  
- سيرفر DHCP في VLAN 100.  
- ثلاثة راوترات متصلة ببعضها باستخدام OSPF.

("Topology")  
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

(Router CLI)  
*صورة تبين إعدادات Subinterfaces على الراوتر*

---

## 4️ اختبار الاتصال (Connectivity Tests)
### 4.1 Ping بين VLANs
![Ping VLANs Screenshot](images/ping_vlans.png)  
*تأكيد أن الأجهزة في VLAN مختلفة تتواصل بنجاح*

### 4.2 Ping إلى السيرفر
![Ping Server Screenshot](images/ping_server.png)  
*تأكيد أن DHCP يعمل والأجهزة تستطيع الوصول للسيرفر*

### 4.3 Tracert
![Tracert Screenshot](images/tracert.png)  
*توضيح مسار الحزم من جهاز في VLAN إلى السيرفر*

---

## 5️ إعداد DHCP على السيرفر
- DHCP Pool لكل VLAN لتعطي IP تلقائي للأجهزة.  
- مثال: VLAN10 Pool: 192.168.10.10 - 192.168.10.50

![DHCP Screenshot](images/dhcp.png)  
*صورة توضح إعداد DHCP لكل VLAN*

---

## 6️ OSPF Routing
- تم ربط الراوترات الثلاثة باستخدام بروتوكول OSPF لتبادل معلومات التوجيه ديناميكيًا.  
- تم تعريف الشبكات مباشرة على الواجهات (Interface-based).

**Router1 مثال:**
```plaintext
interface Gig0/0.10
ip address 192.168.10.1 255.255.255.0
ip ospf 1 area 0
