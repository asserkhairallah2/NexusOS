# **NexusOS – Adaptive Enterprise Management Platform**

# **Section 6 – Core Platform Architecture**

> **"The Core Platform is the foundation upon which every other module is built."**

---

# Introduction

قبل بناء أي Module مثل HR أو CRM أو Projects، يجب أولاً إنشاء البنية الأساسية للنظام (Core Platform).

هذه الطبقة مسؤولة عن تشغيل المنصة بالكامل، وإدارة الشركات، والمستخدمين، والصلاحيات، والإعدادات العامة.

أي Module جديد يتم إضافته في المستقبل سيعتمد على هذه الطبقة.

---

# What is the Core Platform?

الـ Core Platform هو الجزء الذي يحتوي على الخدمات الأساسية المشتركة بين جميع الموديولات.

بدون هذه الطبقة، لن يعمل أي جزء آخر من النظام.

تشمل هذه الطبقة:

* Authentication
* Authorization
* Company Management
* User Management
* Role Management
* Permission Management
* Settings
* Audit Logs
* Notification Infrastructure
* File Management
* Search Infrastructure

---

# Core Platform Architecture

```text
                   NexusOS Platform

-------------------------------------------------------

 Authentication

 Authorization

 Company Service

 User Service

 Role Service

 Permission Service

 Settings Service

 Notification Service

 Audit Service

 Search Service

 File Service

-------------------------------------------------------

          Business Modules

 HR

 CRM

 Projects

 Documents

 Inventory

 Finance

 AI Layer

-------------------------------------------------------
```

---

# Core Principles

تم تصميم الـ Core Platform وفق المبادئ التالية:

### Shared Services

الخدمات الأساسية لا يتم تكرارها داخل كل Module.

مثال:

الـ Login موجود مرة واحدة فقط.

وليس داخل كل Module.

---

### Loose Coupling

كل Module مستقل.

إذا تم تطوير HR.

فلن يؤثر ذلك على CRM.

---

### High Cohesion

كل Service مسؤولة عن وظيفة واحدة فقط.

مثال:

User Service

لا تدير الصلاحيات.

بل تدير المستخدمين فقط.

---

### Reusability

يمكن لأي Module استخدام الخدمات الأساسية.

مثلاً:

HR يحتاج Users.

CRM يحتاج Users.

Projects يحتاج Users.

جميعهم يستخدمون نفس User Service.

---

# Core Services

---

# 1. Authentication Service

المسؤول عن:

* Login
* Logout
* Register
* Password Reset
* Refresh Token
* Session Management

---

## أهدافه

* التحقق من هوية المستخدم.
* إنشاء Access Token.
* إدارة جلسات المستخدم.
* حماية النظام من الدخول غير المصرح به.

---

# 2. Authorization Service

بعد نجاح تسجيل الدخول.

يحدد هذا الجزء:

ماذا يستطيع المستخدم أن يفعل؟

مثال:

Employee

↓

View Tasks

Project Manager

↓

Create Projects

CEO

↓

Manage Company

---

# 3. Company Service

يمثل الشركة داخل النظام.

يشمل:

* Company Profile
* Company Logo
* Company Settings
* Company Status
* Company Plan
* Workspace Information

كل البيانات داخل النظام ترتبط بـ Company_ID.

---

# 4. User Service

المسؤول عن:

* إنشاء المستخدمين.
* تعديل المستخدمين.
* حذف المستخدمين.
* تغيير كلمة المرور.
* إدارة الحسابات.

---

كل User يحتوي على:

* Name
* Email
* Password
* Role
* Department
* Status
* Company_ID

---

# 5. Role Service

يحتوي على جميع Roles.

مثلاً:

* CEO
* HR
* Manager
* Team Leader
* Employee

---

كل Role يحتوي على مجموعة من الصلاحيات.

---

# 6. Permission Service

بدلاً من كتابة الصلاحيات داخل الكود.

يتم حفظها داخل قاعدة البيانات.

مثال:

Employee

↓

Read Tasks

Update Profile

Submit Leave

Manager

↓

Approve Leave

Create Tasks

Generate Reports

---

# 7. Settings Service

كل شركة تمتلك إعداداتها الخاصة.

مثل:

* Language
* Currency
* Timezone
* Working Days
* Theme
* Company Policies

---

# 8. Notification Service

أي Module يستطيع إرسال Notification.

مثلاً:

HR

↓

Leave Approved

Projects

↓

Task Assigned

CRM

↓

Customer Follow-up Reminder

---

لا يهتم الموديول بطريقة الإرسال.

بل يرسل الطلب فقط.

والـ Notification Service تتولى التنفيذ.

---

# 9. Audit Service

من أهم الخدمات داخل النظام.

كل عملية تتم.

يتم تسجيلها.

مثال:

Ahmed

Created Employee

↓

Time

↓

IP Address

↓

Old Value

↓

New Value

---

يساعد ذلك في:

* المراجعة.
* التحقيق.
* الأمان.
* تتبع الأخطاء.

---

# 10. Search Service

بدلاً من أن يبحث كل Module بنفسه.

يوجد Search Engine واحد.

يمكنه البحث في:

* الموظفين.
* المشاريع.
* العملاء.
* المستندات.
* الاجتماعات.
* المهام.

وسيتم لاحقًا ربطه بالـ AI Smart Search.

---

# 11. File Service

جميع الملفات تمر من خلال هذه الخدمة.

مثل:

* الصور.
* PDF.
* العقود.
* الملفات الشخصية.

وتقوم بـ:

* Upload
* Download
* Versioning
* Access Control

---

# Shared Components

كل Module يستطيع استخدام:

* Users
* Roles
* Notifications
* Files
* Search
* Audit Logs

بدون إعادة كتابة الكود.

---

# Company Context

عند تسجيل الدخول.

يقوم النظام بتحميل:

Current Company

Current User

Current Role

Current Permissions

Current Modules

وبالتالي يعرف النظام:

ماذا يعرض لهذا المستخدم.

---

# Core Database Tables

الجداول الأساسية:

* Companies
* Users
* Roles
* Permissions
* RolePermissions
* UserRoles
* CompanySettings
* Sessions
* Notifications
* AuditLogs
* Files

---

# Request Flow Example

مثال عند إنشاء مشروع جديد:

```text
User Login

↓

Authentication

↓

Authorization

↓

Company Validation

↓

Permission Check

↓

Project Service

↓

Audit Log

↓

Notification

↓

Response
```

كل طلب يمر بنفس دورة العمل لضمان الأمان وتسجيل العمليات.

---

# Why Build a Core Platform?

بدون Core Platform.

سيقوم كل Module بإعادة:

* Login
* Permissions
* Notifications
* Search

وهذا يؤدي إلى:

* تكرار الكود.
* صعوبة الصيانة.
* زيادة الأخطاء.

أما بوجود Core Platform.

فتصبح جميع الموديولات تعتمد على نفس الخدمات.

---

# Design Goals

تم تصميم الـ Core Platform لتحقيق:

* إعادة استخدام الخدمات.
* سهولة إضافة Modules جديدة.
* تقليل تكرار الكود.
* تحسين الأداء.
* تسهيل الصيانة.
* دعم التوسع المستقبلي.

---

# Future Enhancements

يمكن مستقبلاً إضافة:

* Single Sign-On (SSO)
* Multi-Factor Authentication (MFA)
* LDAP / Active Directory Integration
* API Keys
* Public API Gateway
* Webhooks
* Event Bus
* Microservices Migration

---

# Section Summary

يمثل الـ Core Platform الأساس الذي يعتمد عليه NexusOS بالكامل. فجميع الموديولات تستخدم نفس خدمات المصادقة، والصلاحيات، وإدارة المستخدمين، والإشعارات، والملفات، والبحث، مما يجعل النظام أكثر تنظيمًا، وأسهل في الصيانة، وقابلًا لإضافة أي Module جديد دون الحاجة إلى إعادة بناء البنية الأساسية.

---

## **Section Status**

✅ **Section 6 Completed**
