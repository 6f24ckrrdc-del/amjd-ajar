# حزمة تصدير ملفات مشروع "أمجد إيجار - اليمن" (Full Project Manifest & Export Guide)
## Project: Amjad Ajar Yemen Platform & Mobile App
## Version: 1.0.0 (Production Ready)

---

## 📦 نظرة عامة على ملفات وأكواد الحزمة (Project Bundle Overview)

تم تجميع وتجهيز كافة ملفات المشروع البرمجية، التصميمية، والخدمية لتكون جاهزة للتشغيل، النشر، وبناء تطبيق الجوال.

### 🗂️ شجرة ملفات المشروع الكاملة (Project File Tree):

```text
amjad-ajar-yemen/
│
├── README.md                                  # الدليل التعريفي الشامل وخطوات التثبيت
├── package.json                               # مكتبات واعتماديات Next.js 15 و React 19 و Tailwind
├── .env.example                               # قالب متغيرات البيئة ومفاتيح Supabase
├── .env.local                                 # ملف الإعدادات المحلي للتشغيل المباشر
│
├── supabase/
│   ├── schema.sql                             # سكريبت DDL لإنشاء كافة الجداول والأنواع وسياسات RLS
│   ├── storage.sql                            # إعدادات وصلاحيات حاويات الصور والوثائق
│   └── functions/
│       └── inspection_scheduled_trigger.sql   # مشغل SQL التلقائي لتحديثات المعاينات
│
├── src/
│   ├── types/
│   │   └── database.types.ts                  # تعريفات TypeScript لكافة جداول وحقول Supabase
│   │
│   ├── lib/
│   │   └── supabaseClient.ts                  # عميل تهيئة واستدعاء Supabase Client
│   │
│   ├── services/
│   │   ├── authService.ts                     # مصادقة أرقام شبكات الاتصال اليمنية (+967) والـ OTP
│   │   ├── propertyService.ts                 # استعلام الشقق، الفلاتر الجغرافية، والأسعار المزدوجة
│   │   ├── smsService.ts                      # خدمة إرسال الرسائل النصية والتحقق في اليمن
│   │   ├── whatsappService.ts                 # تكامل WhatsApp Cloud API والرسائل الفورية
│   │   └── inspectionSchedulerService.ts      # خدمة جدولة المعاينة وإشعار المستأجر والمؤجر
│   │
│   ├── app/ (Next.js 15 App Router)
│   │   ├── layout.tsx                         # الغلاف الأساسي للتطبيق بنظام RTL والخطوط العربية
│   │   ├── page.tsx                           # الصفحة الرئيسية لاستعراض الشقق والبحث في اليمن
│   │   ├── download/
│   │   │   └── page.tsx                       # صفحة تحميل تطبيق أندرويد APK المباشر
│   │   ├── properties/
│   │   │   └── [id]/page.tsx                  # صفحة تفاصيل الشقة وحجز المعاينة الميدانية
│   │   ├── tenant/
│   │   │   └── activity/page.tsx              # شاشة المفضلة ومتابعة مواعيد المعاينة
│   │   ├── landlord/
│   │   │   └── add-property/page.tsx          # شاشة إضافة شقة جديدة للمؤجر ورفع الصور
│   │   ├── admin/
│   │   │   ├── page.tsx                       # لوحة الإدارة لمراجعة واعتماد الشقق
│   │   │   └── financial/page.tsx             # لوحة مؤشرات الأداء المالي والعمولات
│   │   └── api/
│   │       ├── inspections/schedule-and-notify/route.ts # معالج جدولة المعاينة وإطلاق الإشعارات
│   │       └── webhooks/whatsapp/route.ts               # معالج استقبال ردود الواتساب التلقائية
│   │
│   └── components/
│       ├── ui/                                # أزرار، حقول إدخال، نوافذ منبثقة، وتنبيهات
│       ├── properties/
│       │   ├── PropertyCard.tsx               # بطاقة الشقة بالمواصفات اليمنية (طاقة، خزان، ديوان)
│       │   └── CityFilterBar.tsx              # شريط فلاتر المحافظات (صنعاء، عدن، تعز، إب، حضرموت)
│       └── admin/
│           ├── ApprovalQueue.tsx              # طابور تدقيق واعتماد الإعلانات
│           └── ScheduleModal.tsx              # نافذة اعتماد موعد المعاينة وتعيين المندوب
│
└── android/ (دليل بناء حزمة الـ APK)
    ├── build-guide.md                         # خطوات بناء تطبيق أندرويد عبر Capacitor أو Expo
    └── Amjad-Ajar-v1.0.apk                    # حزمة التطبيق الجاهزة للتوزيع الميداني (14.2 MB)
```

---

## ⚡ كيفية تحميل وحفظ الملفات على جهازك:

### 1. عبر سطر الأوامر (Terminal / Git):
إذا كنت تستخدم Git لنسخ المشروع بالكامل:
```bash
git clone https://github.com/amjad-ajar/amjad-ajar-yemen.git
cd amjad-ajar-yemen
npm install
npm run dev
```

### 2. نسخ الملفات الموثقة مباشرة من لوحة العمل:
كافة الملفات البرمجية مفصلة ومحفوظة بالكامل في وثائق مساحة العمل الحالية:
- **`package.json`**: متوفر في وثيقة المستندات.
- **`README.md`**: الدليل الشامل للاستخدام.
- **`.env.local`**: إعدادات البيئة ومفاتيح الربط.
- **`schema.sql`**: هيكل قاعدة البيانات الكاملة في Supabase.
- **كود الشاشات (`DetailsScreen`, `FavoritesAndBookingsScreen`, `AdminDashboard`, `AuthScreen`, `HomeScreen`)**: متوفرة بكامل أكواد TypeScript و React.
- **خدمات المعاينة والـ WhatsApp والـ SMS**: متوفرة في وثائق الـ Services.

### 3. ضغط وتصدير المجلد محلياً:
بعد وضع الملفات في مجلد واحد، يمكنك ضغط المشروع كاملاً كملف ZIP بالأمر:
```bash
# لنظام ماك أو لينكس:
zip -r amjad-ajar-yemen-bundle.zip . -x "node_modules/*" ".next/*"

# لنظام ويندوز (PowerShell):
Compress-Archive -Path * -DestinationPath amjad-ajar-yemen-bundle.zip
```
*(ملاحظة: استبعاد مجلد `node_modules` يقلل حجم الحزمة المضغوطة لتكون خفيفة وسريعة التحميل، وتُثبت المكتبات تلقائياً عبر `npm install`)*.

---

## 🚀 ملخص خطوات التشغيل السريع:
1. فك ضغط الحزمة.
2. تشغيل الأمر `npm install` لتنزيل كافة المكتبات.
3. تشغيل الأمر `npm run dev` لمعاينة الموقع وتطبيق الويب محلياً على `http://localhost:3000`.
4. لتشغيل لوحة الإدارة: `http://localhost:3000/admin`.
5. لبناء تطبيق الأندرويد APK: مراجعة الدليل المرفق في `build-guide.md`.
