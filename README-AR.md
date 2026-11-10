# Life Organizer — حزمة التطبيق الكاملة

## محتويات المجلد
- `app/` — التطبيق نفسه (index.html + manifest + sw.js للعمل بدون إنترنت + الأيقونات)
- `assets/` — الشعار الأصلي ونسخة مربعة 1024×1024
- `store/` — أيقونة متجر Play (512)، صورة الميزات (1024×500)، ومعلومات التطبيق والوصف

## أسرع طريقة: تثبيته على أندرويد (بدون APK)
1. ارفع مجلد `app/` على استضافة HTTPS مجانية (Netlify Drop أو GitHub Pages أو Cloudflare Pages).
2. افتح الرابط في Chrome على الهاتف ← القائمة ⋮ ← «تثبيت التطبيق» / «إضافة إلى الشاشة الرئيسية».
3. سيعمل كتطبيق كامل الشاشة وبدون إنترنت، وبياناتك تُحفظ على الجهاز.

## تحويله إلى ملف APK / AAB
**الطريقة السهلة:** افتح pwabuilder.com، ألصق رابط الموقع من الخطوة السابقة، اختر Android، ثم نزّل الحزمة.
**الطريقة اليدوية (Capacitor):**
```
npm init -y
npm i @capacitor/core @capacitor/cli @capacitor/android
npx cap init "Life Organizer" com.yourname.lifeorganizer --web-dir app
npx cap add android
npx cap sync
npx cap open android   # ثم Build ← Build APK في Android Studio
```
الأيقونات: استخدم `app/icons/` (أو `assets/logo-square-1024.png` في Android Studio ← Image Asset).

## النشر على Google Play
- حساب مطوّر Play (رسوم لمرة واحدة).
- ارفع ملف AAB، أيقونة `store/play-store-icon-512.png`، وصورة `store/feature-graphic-1024x500.png`.
- أضف لقطات شاشة من هاتفك (2 على الأقل) والنصوص من `store/app-info.txt`.
- سياسة الخصوصية: التطبيق لا يجمع بيانات ويحفظ كل شيء محلياً.

## ملاحظات
- الحفظ عبر localStorage: مسح بيانات المتصفح/التطبيق يحذف التقدم.
- لا تغيّر اسم الملفات `index.html` و`sw.js` و`manifest.webmanifest`.
