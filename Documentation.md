# 🔻پیاده‌سازی LB + Failover
## 🔹محیط کار و توپولوژی
![[Topology.png]]
- **GNS3**⬆️



## 🔹هدف
- با **استفاده از** Static Routeها و Mangle و PCC باید کاری کنیم که:
	- روی ترافیک LAN بین WAN1 و WAN2 عمل **Load Balance** انجام شود.
	- اگر WAN1 یا WAN2 قطع شد -> ترافیک به مسیر سالم بره (**Failover**).
	- اگر هر دو Down شدند -> ترافیک خودکار بره روی Backup (همون **Failover**).
	- لینک Backup هنگام Online بودن لینک‌های اصلی **نباید** وارد Load Balance بشه.
	   
- **هدف** این سناریو اینه که اقدامات Load Balancing + Failover رو تمرین کنیم چون در زندگی **روزمره** هم استفادۀ زیادی دارن!



## 🔹اقدامات و کانفیگ‌ها
1. تنظیم IP Address اینترفیس‌ها⬇️
![[MikroTik - IP Addresses.png]]


2. ساخت Routing Tableهای`ISP2`و`ISP1`و نوشتن Route براشون⬇️
![[MikroTik - Routing Tables & Routes.png]]
>این 2 روت تنها مخصوص ترافیکی هستن که از PCC مارک خورده باشن‼️


3. نوشتن Default Routeهای اصلی⬇️
![[MikroTik - Main Routes.png]]
>ترکیب`Distance`و`Check Gateway`باعث بوجود اومدن ساختار Failover میشه‼️


4. تنظیم Mangle برای تقسیم ترافیک⬇️
![[MikroTik - Mangle.png]]
>برای اولین بار از PCC توی عمرم استفاده کردم‼️


5. تنظیم NAT برای هر خروجی⬇️
![[MikroTik - NAT.png]]



## 🔹راستی آزمایی
1. پینگ به آدرس اینترنتی (از کلاینت‌‌‌‌ها) و Counterهای Mangle Ruleها⬇️
![[Tests - Ping & Mangle Counters.png]]
>میبینیم که از هر مقدار پکت Connection خورده دقیقا همون مقدار Route شده✅


2. بررسی کارکردن هردو ISP⬇️
![[Tests -ISP1,ISP2.png]]
>جفتشون همزمان کار میکنن ولی بیشتر`ISP2`پکت‌ها رو میگرفت‼️


3. بررسی Failover با غیرفعال کردن Interfaceها⬇️
![[Tests - No ISP1.png]]
![[Tests - No ISP2.png]]
![[Tests - No ISP1,ISP2.png]]
>همه‌چیز طبق خواسته‌‌مون پیش رفت✅



## 🔹مشکل
>یه سری **مشکل** از سمت GNS3 وجود داشت اما خیلی زود **حل** شد و سناریو به کار افتاد✅



## 🔹نتیجه
>سناریو **موفقیت‌آمیز** بود✅
