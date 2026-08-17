WOOD POP ADVENTURE — دليل التغليف للنشر (Capacitor)
====================================================

هذي الخطوات تشتغل على جهازك (Windows/Mac/Linux) وتحتاج Node.js مثبت.

1) ثبّت الأدوات:
   npm install

2) أضف منصة أندرويد:
   npx cap add android

   (لو تريد iOS، على جهاز Mac فقط:)
   npx cap add ios

3) زامن ملفات الويب داخل المشروع:
   npx cap sync

4) افتح مشروع أندرويد بـ Android Studio:
   npx cap open android

   بالداخل: Build > Generate Signed Bundle / APK
   - أنشئ Keystore جديد (احتفظ فيه بمكان آمن، تحتاجه لكل تحديث مستقبلي)
   - اختر Android App Bundle (.aab) وهذا المطلوب لمتجر Google Play

5) الأيقونة وشاشة البداية (Splash):
   - استخدم أداة @capacitor/assets لتوليدها تلقائيًا من icon.svg:
     npm install @capacitor/assets --save-dev
     npx capacitor-assets generate

6) النشر على Google Play:
   - أنشئ حساب مطوّر (رسوم لمرة وحدة 25$): play.google.com/console
   - أنشئ تطبيق جديد، ارفع ملف .aab
   - عبّي معلومات المتجر (وصف، صور، سياسة خصوصية — مطلوبة حتى لو التطبيق أوفلاين بالكامل)
   - عبّي استمارة تصنيف المحتوى (Content Rating)
   - أرسل للمراجعة

7) النشر على App Store (iOS، يحتاج جهاز Mac + حساب مطوّر أبل 99$/سنة):
   - افتح المشروع بـ Xcode: npx cap open ios
   - Product > Archive، ثم ارفعه عبر App Store Connect

ملاحظات مهمة:
- عدّل appId بملف capacitor.config.json لمعرّف حزمة فريد يخصك قبل النشر (مثال: com.iraqstudio.woodpop)
- التطبيق أوفلاين بالكامل فما يحتاج أي صلاحيات إنترنت — احذف صلاحية INTERNET من AndroidManifest.xml إذا ظهرت تلقائيًا، لتقليل الصلاحيات المطلوبة أمام المستخدم
- لأي تحديث مستقبلي: عدّل ملفات www/ ثم أعد npx cap sync وابني نسخة جديدة برقم إصدار أعلى
