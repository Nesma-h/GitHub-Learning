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


```
Repo -> جزء داخل ال Working Directory
واسمه .git
```
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

## ⚙️ أوامر Git الأساسية

### `git add`
بياخد نسخة من الملف اللي في الـ **Working Directory** ويخزنها (الـ Hash بتاعها) في الـ **Staging Area**، ويبدأ **Tracking** للملف.
> كل حاجة جوه الـ Staging بتبقى دايمًا "متتبَّعة" (Tracked) في الـ `.git`.

### `git commit`
بياخد **Snapshot** للتعديلات اللي في الـ Staging Area ويسجّلها بشكل نهائي في تاريخ المشروع.

```bash
git commit -m "Initial commit"
```

| الأمر | الوظيفة |
|------|---------|
| `git commit -m "..."` | يعمل أول/أي commit برسالة وصفية |
| **ماسح (Clean)** | بعد الـ commit، الـ Staging Area بترجع فاضية تاني |

---

## 📄 حالات الملف (File States)

كل **File** في المشروع بيمر بحالتين أساسيتين:

```
            File
       ┌──────┴──────┐
   Untracked      Tracked
```

| الحالة | المعنى |
|--------|--------|
| **Untracked (U)** | ملف جديد، Git لسه ملاحظه — لم يدخل دائرة التتبع بعد |
| **Tracked** | الملف بقى تحت متابعة Git (دخل الـ Staging مرة على الأقل) |

وتحت **Tracked** بييجي تفصيل أكتر:

| الحالة | المعنى |
|--------|--------|
| **Unmodified** | الملف متتبَّع ومن غير أي تعديل جديد عن آخر Commit |
| **Modified (M)** | الملف متتبَّع وفيه تعديل لسه ملحقش الـ Staging/Commit |
| **Staged** | التعديل دخل الـ Staging Area وجاهز للـ Commit |

---

## 🆕 `git init`
بيحوّل أي فولدر (Project) عادي على جهازك لـ **Repo**، ولازم تكتبه جوه الفولدر بتاعك عشان يبدأ يتتبّع/يبيكرَّب كـ Git Repository.

```bash
git init
```

---


## 🗑️ Undoing Things

### `git rm --cached <file name>`
بيشيل الملف من الـ **Staging Area** بس (مش من الـ Working Directory)، يعني الملف بيرجع **Untracked** تاني.

### `git restore <file name>`
بيرجّع الملف لآخر نسخة محفوظة منه (Discard التعديلات اللي لسه مش متضافة).

### `git restore --staged <file name>`
بيرجّع الملف من الـ **Staging** للـ **Working Directory** من غير ما يمسح التعديلات.

---

## 📜 Version History

### `git commit --amend`
بيعدّل آخر Commit بدل ما يعمل Commit جديد — يفيد لو نسيتي ملف أو غلطتي في الرسالة.

```bash
git commit --amend
```

### `git reset HEAD~1`
بيرجع بالمشروع خطوة لورا (يلغي آخر Commit)، مع خيارات حسب اللي عايزاه يحصل للتعديلات:

| الأمر | الوظيفة |
|------|---------|
| `git reset --soft HEAD~1` | يلغي آخر Commit، والتعديلات بترجع للـ **Staging** |
| `git reset --mixed HEAD~1` *(default)* | يلغي آخر Commit، والتعديلات بترجع للـ **Working Directory** فقط |
| `git reset --hard HEAD~1` | يلغي آخر Commit **ويمسح** التعديلات نهائيًا ⚠️ |

### `git diff`
بيوضّح الفرق (Difference) بين نسختين من الملف — يعني التعديلات اللي حصلت بالظبط، سطر بسطر.

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
