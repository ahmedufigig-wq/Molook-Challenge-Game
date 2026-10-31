# ملوك التحدي – الغرف المباشرة

هذه نسخة أولية من كود المستخدم: دخول مجهول، غرف عامة/خاصة، دردشة، أعضاء وإدارة أدوار، مع تكامل ZEGO عند إعداد خادم التوكن.

## النشر
1. فعّل GitHub Pages من Settings → Pages → Deploy from a branch → main → /(root).
2. أضف نطاق Pages إلى Firebase Authentication → Settings → Authorized domains.

## Firebase
1. أنشئ مشروع Firebase وتطبيق Web.
2. فعّل Authentication → Sign-in method → Anonymous.
3. أنشئ Firestore Database.
4. الصق `firestore.rules` في Firestore → Rules ثم Publish.
5. ضع قيم Firebase Web App في كائن `CFG.firebase` داخل `index.html`.

## ZEGO
- ضع رقم AppID في `CFG.zegoAppID`.
- لا تضع ServerSecret في `index.html` أو مستودع عام.
- جهّز خادمًا آمنًا يولّد ZEGO Token04 باستخدام ServerSecret المحفوظ كسر خادمي، ويعيد JSON بالشكل `{"token":"..."}`.
- ضع رابط الخادم في `CFG.zegoTokenEndpoint`.
- توثيق ZEGO: https://www.zegocloud.com/docs/uikit/video-conference-kit-web/authentication-and-kit-token

## حدود النسخة الحالية
- هذه نسخة غرف مباشرة وليست لعبة المسابقات الثلاث المطلوبة سابقًا.
- حد 12 مشاركًا مفروض في واجهة العميل فقط، ويحتاج فرضًا إضافيًا على الخادم لمنع الانضمام المتزامن.
- الصوت والفيديو لا يعملان قبل إعداد ZEGO Token endpoint.
- Firebase وZEGO يحتاجان الإنترنت؛ تخزين ملفات الواجهة مؤقتًا لا يجعل الدردشة أو البث يعملان دون اتصال.
