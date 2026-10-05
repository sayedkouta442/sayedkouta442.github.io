# روابط المشاركة — ملفات الاستضافة

الملفات دي بتتحط في مستودع GitHub Pages اسمه `sayedkouta442.github.io`،
مش في المستودع ده. المستودع ده بيحتفظ بيها كمرجع عشان متضيعش.

```
sayedkouta442.github.io/
├── .well-known/
│   └── assetlinks.json
├── book/
│   └── index.html
└── library/
    └── index.html
```

## ⚠️ بصمة الشهادة — أهم خطوة

`assetlinks.json` فيه بصمتين، والاتنين مطلوبين:

1. **بصمة مفتاح الرفع** (موجودة خلاص) — بتخلّي الروابط تشتغل لما تثبّت
   نسخة release من جهازك بـ `flutter install`.

2. **بصمة مفتاح التوقيع بتاع Google Play** — دي **اللي بتهم فعلاً**
   للمستخدمين. لما التطبيق يبقى في Play، جوجل بيعيد توقيعه بمفتاح بتاعه،
   فالنسخة اللي على موبايل المستخدم موقّعة بمفتاح تاني غير بتاعك. من غير
   البصمة دي الروابط هتفتح المتصفّح بدل التطبيق لكل المستخدمين.

   ✅ اتحطّت خلاص (`A9:E6:2C:...`) — متاخدة من Play Console تحت
   **Setup → App integrity → App signing**.

## التأكد إن الربط اشتغل

بعد الرفع، الملف لازم يفتح على:
https://sayedkouta442.github.io/.well-known/assetlinks.json

وبعد تثبيت التطبيق:

```
adb shell pm get-app-links io.bookchange.app
```

لازم تلاقي `verified` جنب الدومين. لو `legacy_failure` يبقى الملف مش
بيتقرا أو البصمة غلط.

التحقق بيحصل وقت التثبيت، فلو غيّرت الملف لازم تعيد تثبيت التطبيق:

```
adb shell pm verify-app-links --re-verify io.bookchange.app
```
