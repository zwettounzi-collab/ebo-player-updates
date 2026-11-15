# ebo-player-updates

مصدر التحديث التلقائي لتطبيق **EBO PLAYER** (`com.sahab.tv`).

## البنية

```
version.json                    ← يقرأه التطبيق عند كل إقلاع (رابط يدخل في إعدادات التطبيق)
releases/                       ← APK الموقّع يُرفع إلى GitHub Releases (ليس في المستودع)
```

## صيغة `version.json`

```json
{
  "versionCode": 11,
  "versionName": "1.10",
  "apkUrl": "https://github.com/zwettounzi-collab/ebo-player-updates/releases/download/v1.10/EBO-PLAYER-1.10.apk",
  "notes": "…"
}
```

- `versionCode`: رقم صحيح يُقارن بـ`versionCode` للتطبيق المثبت — التحديث يظهر فقط عندما يكون أكبر.
- `apkUrl`: رابط مباشر للـAPK (GitHub Releases يعطي 302 إلى CDN — التطبيق يتبع التحويلات).
- يمكن استبدال الرابط لاحقًا عند إصدار نسخة جديدة: أنشئ Release باسم `v1.11` وارفع `EBO-PLAYER-1.11.apk` وحدّث الحقول الثلاثة.

## خطوات النشر لكل إصدار

1. بناء APK موقّع (`assembleRelease`) من مشروع `SahabTV`.
2. إعادة تسميته إلى `EBO-PLAYER-<الإصدار>.apk`.
3. إنشاء Release بالوسم `v<الإصدار>` ورفع الـAPK كأصل (asset).
4. تحديث `version.json` في هذا المستودع (versionCode/versionName/apkUrl/notes).
5. `git add version.json && git commit && git push` — التحديث يصل للمستخدمين عند الإقلاع التالي.

## الرابط الذي يُدخل في إعدادات التطبيق

```
https://raw.githubusercontent.com/zwettounzi-collab/ebo-player-updates/main/version.json
```

(أو استخدم رابط `main` الخام أعلاه بعد أول Push.)
