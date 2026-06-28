# Git and GitHub | شخبط وانت متطمن

---

## 🔄 Version Control Systems

### 1. Local Version Control
لوكال على الجهاز بتاعك. التتبع والنسخ بيحصل محلي فقط، من غير أي سيرفر خارجي.

### 2. Central Version Control (CVCS)
- الـ Source Code بيكون في مكان واحد (الـ **Center / Server**)
- كل المطورين عندهم **access** على هذا السيرفر
- التعديلات بتكون **Live** على السيرفر المركزي طول الوقت

### 3. Distributed Version Control (DVCS)
- كل حد بياخد **Clone** كامل من البروجكت على جهازه
- بيعمل التعديلات اللي يحتاجها محليًا
- وبعدين بيرفعها (push) للريبو المشترك

> **💡 الفرق ** اللي بيميز Git عن باقي أنظمة الـ Version Control:
> Git هو **Distributed Version Control System**، وبيحتفظ بـ **Snapshot** عن كل تعديل — حتى لو كان مجرد تغيير حرف أو سطر واحد — مش مرجع واحد بياخد سناب شوت من الملفات كلها.

```
Git → Distributed Version Control System
```

---

## 🏗️ Git Architecture (3 Layers)

| # | الجزء | الوظيفة |
|---|-------|---------|
| 1 | **Working Directory** | المجلد اللي بتشتغل فيه وبتعدل في الملفات بشكل مباشر |
| 2 | **Repository (Repo)** | المكان اللي بيتخزن فيه تاريخ المشروع بالكامل (الـ commits والتاريخ) |
| 3 | **Staging Area** | منطقة وسيطة بتجمع فيها التعديلات اللي عايز تضمها للـ commit الجاي |

### متطلبات Git (Git Requirements)
لإدارة أي مشروع، Git محتاج يحقق 3 أساسيات:

1. ✅ **Track everything** — يتابع كل تغيير بيحصل
2. ✅ **OS Independent** — يشتغل على أي نظام تشغيل من غير فروقات
3. ✅ **Unique ID** — كل تعديل أو commit له **ID فريد** يميزه عن غيره

### History
Git بيحتفظ بتاريخ كامل لكل التعديلات اللي حصلت، يقدر يرجعلها في أي وقت.

---

## 🧩 Git Objects

Git بيخزن البيانات في صورة 3 أنواع أساسية من الـ Objects:

### 🔹 Blob (Binary Large Object)
- يمثل **File** واحد
- المحتوى (**Content**) فقط — من غير اسم أو معلومات تانية

### 🔹 Tree
- يمثل **Folder**
- بيحتوي على:
  - **Content** → إشارة لمحتوى الملفات/المجلدات الفرعية
  - **Metadata** → بيانات زي الاسم، الصلاحيات، النوع... إلخ

### 🔹 Commit
- اللقطة (**Snapshot**) النهائية اللي بتجمع كل حاجة مع بعض
- بتحتوي على إشارة لـ Tree معين + معلومات الـ commit (الرسالة، الكاتب، التاريخ)

---

## 🗂️ Summary Diagram

```
Working Directory  →  Staging Area  →  Repository (Repo)
       (edit)             (add)            (commit)
```

```
Commit
  └── Tree (folder)
        ├── Blob (file)
        ├── Blob (file)
        └── Tree (sub-folder)
              └── Blob (file)
```

---

> 📝 *ملاحظات شخصية من أول جزء في كورس Git & GitHub.*
