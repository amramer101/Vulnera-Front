# Environment Configuration Guide

## شرح متغيرات البيئة / Environment Variables

هذا المشروع يستخدم متغيرات البيئة لتكوين الإعدادات المختلفة.

### الملفات المتاحة

1. **`.env`** - الإعدادات الحالية (يتم إنشاؤه تلقائياً)
2. **`.env.example`** - مثال للمطورين الآخرين
3. **`.env.production`** - إعدادات الإنتاج (للبناء)

### المتغيرات المتاحة:

```bash
# API Configuration
VITE_API_BASE_URL=http://localhost:3000    # رابط الـ API الأساسي
VITE_API_VERSION=v1                        # إصدار الـ API

# App Information  
VITE_APP_NAME=Vulnera                      # اسم التطبيق
VITE_APP_VERSION=1.0.0                     # إصدار التطبيق
```

### كيفية الاستخدام:

#### 1. التطوير المحلي (Local Development):
```bash
# انسخ الملف المثال
cp .env.example .env

# عدل الإعدادات حسب احتياجك
nano .env

# شغل المشروع
npm run dev
```

#### 2. للشبكة المحلية:
```bash
# استخدم إعدادات الشبكة
cp .env.network .env

# أو اكتب مباشرة
echo "VITE_API_BASE_URL=http://192.168.1.100:3000" > .env
```

#### 3. للخادم البعيد:
```bash
# استخدم إعدادات الخادم البعيد
cp .env.remote .env

# أو اكتب رابط الخادم
echo "VITE_API_BASE_URL=https://api.yourdomain.com" > .env
```

#### 4. للبناء للإنتاج:
```bash
# Vite سيستخدم .env.production تلقائياً
npm run build
```

### أمثلة لـ URLs مختلفة:

```bash
# المطور المحلي
VITE_API_BASE_URL=http://localhost:3000

# الشبكة المحلية 
VITE_API_BASE_URL=http://192.168.1.100:3000

# الخادم البعيد
VITE_API_BASE_URL=https://api.vulnera.dev
VITE_API_BASE_URL=http://18.135.27.89:3000

# مع بورت مختلف
VITE_API_BASE_URL=http://localhost:8080
```

### التحقق من الإعدادات:

عند تشغيل المشروع في وضع التطوير، ستظهر الإعدادات في الـ console:

```javascript
🔧 App Configuration: {
  API_BASE_URL: "http://localhost:3000",
  API_ENDPOINT: "http://localhost:3000/api/v1",
  APP_NAME: "Vulnera",
  APP_VERSION: "1.0.0",
  MODE: "development"
}
```

### ملاحظات مهمة:

1. **يجب أن تبدأ كل متغير بـ `VITE_`** حتى يتم تضمينه في البناء
2. **لا تضع معلومات حساسة** في متغيرات البيئة للـ frontend
3. **ملف `.env`** مُستثنى من Git، لذا كل مطور يمكنه وضع إعداداته الخاصة
4. **التغييرات تحتاج إعادة تشغيل** الخادم (`npm run dev`)

### أسكريبت التبديل السريع

يمكنك استخدام `switch-api.sh` للتبديل السريع بين الإعدادات:

```bash
# للتبديل للـ local
./switch-api.sh local

# للتبديل للـ remote
./switch-api.sh remote

# للتبديل للـ Azure (الموصى به للتجربة الحية)
./switch-api.sh azure

# للتبديل للـ production
./switch-api.sh production

# للشبكة المحلية (سيطلب منك IP)
./switch-api.sh network

# لـ URL مخصص (سيطلب منك الرابط)
./switch-api.sh custom

# سكريبت سريع لـ Azure
./use-azure.sh
```
