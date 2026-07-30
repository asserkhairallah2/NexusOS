# **NexusOS – Adaptive Enterprise Management Platform**

# **Section 4 – Stakeholders, User Types & Organizational Structure**

---

# Introduction

بعد تحديد فكرة المشروع والمشكلة التي يحلها، تأتي الخطوة التالية وهي تحديد جميع الأطراف التي ستتعامل مع النظام (Stakeholders)، بالإضافة إلى تعريف أنواع المستخدمين (User Types)، ومسؤوليات كل منهم، والصلاحيات التي يمتلكها.

تم تصميم NexusOS وفق مبدأ **Role-Based Access Control (RBAC)**، أي أن كل مستخدم يرى فقط البيانات والوظائف التي تسمح له صلاحياته بالوصول إليها.

---

# What is a Stakeholder?

الـ Stakeholder هو أي شخص أو جهة تتأثر بالنظام أو تتعامل معه بشكل مباشر أو غير مباشر.

في NexusOS يمكن تقسيمهم إلى:

### Internal Stakeholders

* Company Owner
* Managers
* Employees
* HR Team
* IT Administrators

### External Stakeholders

* Customers
* Vendors
* Investors (اختياري)
* System Administrators (Platform Owners)

---

# User Hierarchy

ينقسم مستخدمو النظام إلى مستويين رئيسيين:

## Platform Level

المستخدمون المسؤولون عن المنصة بالكامل.

يشرفون على جميع الشركات الموجودة داخل NexusOS.

---

## Company Level

المستخدمون الذين يعملون داخل شركة واحدة فقط.

ولا يمكنهم رؤية بيانات أي شركة أخرى.

---

# User Types

---

# 1. Platform Super Admin

هو أعلى مستوى داخل النظام.

يمثل مالك منصة NexusOS.

### Responsibilities

* إنشاء الشركات الجديدة.
* حذف الشركات.
* إدارة الاشتراكات.
* إدارة جميع Modules.
* مراقبة أداء المنصة.
* إدارة النسخ الاحتياطية.
* مراقبة النظام بالكامل.

### Permissions

✔ Full Access

يمكنه الوصول إلى كل شيء داخل المنصة.

---

# 2. Company Owner (CEO)

هو مالك الشركة أو المدير التنفيذي.

### Responsibilities

* إدارة الشركة.
* اختيار Modules.
* إدارة المستخدمين.
* متابعة الأداء.
* مراجعة التقارير.
* مراقبة جميع الأقسام.

### Permissions

* رؤية جميع بيانات شركته فقط.
* لا يستطيع الوصول إلى شركات أخرى.
* يستطيع تعيين المدراء.

---

# 3. Company Administrator

مسؤول تشغيل النظام داخل الشركة.

### Responsibilities

* إنشاء المستخدمين.
* تعيين الصلاحيات.
* إدارة الأقسام.
* إدارة إعدادات الشركة.

---

# 4. HR Manager

مسؤول الموارد البشرية.

### Responsibilities

* إدارة الموظفين.
* الحضور.
* الإجازات.
* العقود.
* تقييم الموظفين.

---

# 5. Department Manager

مدير قسم معين.

مثلاً:

IT Manager

Sales Manager

Marketing Manager

### Responsibilities

* إدارة فريقه.
* توزيع المهام.
* متابعة الأداء.
* الموافقة على الطلبات.

---

# 6. Project Manager

مسؤول المشاريع.

### Responsibilities

* إنشاء المشاريع.
* إدارة الفريق.
* إنشاء Sprint.
* متابعة Milestones.
* متابعة تقدم المشروع.

---

# 7. Team Leader

يقود فريقاً صغيراً داخل المشروع.

### Responsibilities

* توزيع المهام.
* مراجعة التنفيذ.
* متابعة أعضاء الفريق.

---

# 8. Employee

المستخدم العادي.

### يستطيع:

* رؤية مهامه.
* رفع ملفات.
* طلب إجازة.
* تحديث بياناته.
* المشاركة في المشاريع.

ولا يستطيع الوصول إلى بيانات باقي الأقسام إلا إذا كانت لديه صلاحيات بذلك.

---

# 9. Customer (Future)

في الإصدارات المستقبلية.

يمكن منح العميل حساباً.

ليستطيع:

* متابعة المشروع.
* رفع طلبات.
* متابعة التذاكر.
* مراجعة الفواتير.

---

# User Permission Model

يعتمد النظام على ثلاث مستويات:

## Authentication

هل المستخدم مسجل دخول؟

---

## Authorization

هل يمتلك صلاحية؟

---

## Ownership

هل البيانات تخص شركته؟

---

حتى لو كان المستخدم Admin.

لن يستطيع رؤية بيانات شركة أخرى.

---

# Role-Based Access Control (RBAC)

بدلاً من إعطاء صلاحيات لكل مستخدم.

يتم إعطاء الصلاحيات للـ Roles.

مثلاً:

HR Manager

↓

Permissions

↓

Employees

Attendance

Leaves

Contracts

وبالتالي أي مستخدم يحصل على Role HR Manager.

سيحصل تلقائياً على نفس الصلاحيات.

---

# Permission Categories

يمكن تقسيم الصلاحيات إلى:

## Read

عرض البيانات.

---

## Create

إنشاء بيانات جديدة.

---

## Update

تعديل البيانات.

---

## Delete

حذف البيانات.

---

## Approve

الموافقة على الطلبات.

---

## Export

تصدير البيانات.

---

## Configure

تغيير إعدادات النظام.

---

# Example Permission Matrix

| Module            | Employee | Team Leader | Manager | Company Admin | CEO |
| ----------------- | -------- | ----------- | ------- | ------------- | --- |
| View Tasks        | ✔        | ✔           | ✔       | ✔             | ✔   |
| Create Tasks      | ✖        | ✔           | ✔       | ✔             | ✔   |
| Delete Tasks      | ✖        | ✖           | ✔       | ✔             | ✔   |
| Manage Employees  | ✖        | ✖           | ✖       | ✔             | ✔   |
| View Reports      | ✖        | Limited     | ✔       | ✔             | ✔   |
| Configure Modules | ✖        | ✖           | ✖       | ✔             | ✔   |

> **ملاحظة:** الجدول السابق مثال مبدئي، ويمكن توسيعه لاحقًا ليشمل جميع الموديولات.

---

# Organizational Structure

داخل كل شركة يمكن إنشاء الهيكل الإداري.

مثال:

CEO

↓

HR Manager

↓

IT Manager

↓

Backend Team

↓

Frontend Team

↓

Developers

ويستطيع النظام عرض هذا الهيكل في صورة Organizational Chart.

---

# Department Structure

كل شركة تستطيع إنشاء أقسام مثل:

* HR
* IT
* Sales
* Marketing
* Finance
* Operations
* Customer Support

وكل قسم يحتوي على:

* Manager
* Employees
* Projects
* Documents

---

# Multi-Company Isolation

من أهم مبادئ المشروع.

إذا كانت لدينا:

Company A

Company B

Company C

كل شركة ترى فقط:

* موظفيها.
* مشاريعها.
* مستنداتها.
* عملاءها.
* تقاريرها.

ولا يمكن لأي مستخدم الوصول إلى بيانات شركة أخرى مهما كانت صلاحياته، باستثناء Platform Super Admin.

---

# User Journey Example

### أحمد (Backend Developer)

يسجل الدخول.

↓

يرى Dashboard الخاصة به.

↓

يعرض مهامه.

↓

يفتح مشروع ERP.

↓

يرفع ملف.

↓

يكتب تعليق.

↓

يطلب إجازة.

↓

يسجل الخروج.

كل ما يراه أحمد يعتمد على صلاحياته فقط.

---

# Design Principles

تم تصميم نظام المستخدمين وفق المبادئ التالية:

* Least Privilege (كل مستخدم يحصل على أقل صلاحيات يحتاجها).
* Separation of Duties (فصل المسؤوليات بين الأدوار).
* Secure by Default (الإعدادات الافتراضية آمنة).
* Easy Administration (سهولة إدارة المستخدمين والصلاحيات).
* Scalability (إمكانية إضافة أدوار جديدة مستقبلاً).

---

# Section Summary

يعتمد NexusOS على نظام صلاحيات مرن وقابل للتوسع، حيث يتم فصل مسؤوليات إدارة المنصة عن إدارة الشركات، مع تطبيق نموذج RBAC لضمان أمان البيانات وسهولة التحكم في الوصول. كما يسمح النظام بإنشاء هيكل إداري يناسب كل شركة، مع الحفاظ على العزل الكامل بين بيانات الشركات المختلفة داخل المنصة.

---

## **Section Status**

✅ **Section 4 Completed**
