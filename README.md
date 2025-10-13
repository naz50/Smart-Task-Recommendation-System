# 🧠 Smart Task Recommendation System  
### نظام التوصية الذكي للمهام (Automation + Machine Learning)

---

## 🚀 Overview | نظرة عامة
This project is an **intelligent task recommendation system** that integrates **Automation + Machine Learning (ML)** to assist managers in assigning tasks fairly, efficiently, and transparently.  

يهدف المشروع إلى بناء **نظام ذكي لتوصية المهام** يعتمد على الأتمتة (Power Automate) وخوارزميات تعلم الآلة (ML) لتوزيع المهام بشكل **عادل واحترافي** وتحقيق **الشفافية والتوثيق** في أداء الموظفين.

---

## 🎯 Objectives | الأهداف
- ضمان **توزيع المهام بشكل عادل وموضوعي**.
- **تقليل الجهد الإداري** عبر التوصية التلقائية بالموظف الأنسب.
- **توثيق الأعمال وحفظ الحقوق** لكل موظف.
- **عرض تحليلات Power BI تفاعلية** للمديرين والموظفين.
- **تحفيز الأداء** عبر نظام المكافآت (Bonus).

---

## 🏗️ System Architecture | هيكل النظام

### 🔹 Main Components:
1. **Microsoft Planner** – مصدر المهام (المسندة وغير المسندة).  
2. **Power Automate (Flow)** – يسحب البيانات من Planner ويصنفها.  
3. **SharePoint Lists**
   - `Task_Assignment`: المهام **غير المسندة**.
   - `Task_Assigned_To`: المهام **المسندة أو المكتملة**.
4. **Dataflow & Pipeline (Microsoft Fabric)** – لجلب وتحديث البيانات من SharePoint.
5. **Fabric Lakehouse** – لتخزين ومعالجة البيانات (Bronze → Silver → Gold).
6. **Notebook (Python + Spark)** – لتنفيذ خوارزميات التوصية (ML).
7. **Power BI Dashboard** – لعرض النتائج بصريًا.
8. **Teams / Outlook Alerts** – لإرسال التنبيهات الدورية.

---

## ⚙️ Power Automate Flow | سير العمل
- **Trigger:** Recurrence Trigger ⏰ runs **4 times per day**.
- **Logic:**
  - إذا كانت المهمة **غير مسندة** → `Task_Assignment`
  - إذا كانت المهمة **مسندة أو مكتملة** → `Task_Assigned_To`

### 💰 Bonus Logic:
```text
if TaskType = 'Machine Learning' → +20  
if TaskType = 'SPSS' → +15

# 🧠 Smart Task Recommendation System  
### نظام التوصية الذكي للمهام (Automation + Machine Learning)

---

🎯 **الهدف من البونس:**  
تحفيز الموظفين على تنفيذ المهام التقنية والمعقدة.

---

## 🧩 Data Preparation | تجهيز البيانات

### **Data Sources:**
- `EmployeesTable` ← من نظام ERP.  
- `Task_Assignment` ← من SharePoint (Power Automate).

### **ETL Steps:**
- تنظيف البيانات وتوحيد التنسيق.  
- التعامل مع القيم الفارغة.  
- تحديث تلقائي عبر **Pipeline Schedule**.

---

## 🧠 Machine Learning Model | نموذج الذكاء الاصطناعي

### 🔸 Translation Layer
يستخدم **Deep Translator** لترجمة النصوص العربية إلى الإنجليزية:

```python
GoogleTranslator(source='auto', target='en').translate(text)





if TaskType = 'Power BI' → +10  
else → +5
