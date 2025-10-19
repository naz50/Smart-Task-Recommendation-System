# 🧠 Smart Task Recommendation System  
### نظام التوصية الذكي للمهام (Automation + Machine Learning)
---

## 🚀 Overview | نظرة عامة
This project is an **intelligent task recommendation system** that integrates **Automation + Machine Learning (ML)** to assist managers in assigning tasks fairly, efficiently, and transparently.  

يهدف المشروع إلى بناء **نظام ذكي لتوصية المهام** يعتمد على الأتمتة (Power Automate) وخوارزميات تعلم الآلة (ML) لتوزيع المهام بشكل **عادل واحترافي** وتحقيق **الشفافية والتوثيق** في أداء الموظفين.



## 🎯 Objectives | الأهداف
- ⚖️ ضمان **توزيع المهام بشكل عادل وموضوعي**.  
- 🤖 **تقليل الجهد الإداري** عبر التوصية التلقائية بالموظف الأنسب.  
- 🧾 **توثيق الأعمال وحفظ الحقوق** لكل موظف.  
- 📊 **عرض تحليلات Power BI تفاعلية** للمديرين والموظفين.  
- 💎 **تحفيز الأداء** عبر نظام المكافآت (Bonus).



## 🏗️ System Architecture | هيكل النظام

## 🧾 Smart Task Recommendation System Architecture | مخطط هيكل النظام الذكي لتوصية المهام
<img width="3515" height="1020" alt="Smart Task Recommendation System Architecture" src="https://github.com/user-attachments/assets/d4c7066e-c31f-40aa-b068-e868cd4bc552" />


## 🧾 End-to-End Task Automation & Recommendation Flow | مخطط سير عمل نظام التوصية الذكي للمهام
<img width="556" height="977" alt="image" src="https://github.com/user-attachments/assets/d7fe80cd-f8e1-4da8-9f13-d21aa47121c1" />

## 👥 ERP Employees Database |  قاعدة بيانات موظفين (ERP)
<img width="1571" height="635" alt="SQL_EMP_DB" src="https://github.com/user-attachments/assets/e6875d93-f603-4cea-ae90-e08812f4997c" />


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


## 📊 Power BI Dashboard URL
 
[![View Power BI Dashboard](https://img.shields.io/badge/Power%20BI-View%20Dashboard-yellow)](https://app.powerbi.com/view?r=eyJrIjoiY2FmYTYxYWMtNGMzNi00NTY1LWI5OTItZTRhZDE5NWZhMDQyIiwidCI6IjMzYTllMjJjLTUwOWUtNDYyNC05NmNjLTc2OWFjNzk2OGNhNSIsImMiOjl9)
---

## ⚙️ Power Automate Flow | سير العمل


<img width="1268" height="603" alt="DW4_PIPLINE_2" src="https://github.com/user-attachments/assets/937f1c3a-58ee-4266-9d37-d86ffd891d07" />



### 🔸 Trigger:
- **Recurrence Trigger ⏰** – يعمل **4 مرات يوميًا**.

### 🔸 Logic:
- إذا كانت المهمة **غير مسندة** → تُضاف إلى `Task_Assignment`  
- إذا كانت المهمة **مسندة أو مكتملة** → تُضاف إلى `Task_Assigned_To`



## 💰 Bonus Logic | منطق المكافآت

```text
if TaskType = 'Machine Learning' → +20  
if TaskType = 'SPSS' → +15  
if TaskType = 'Power BI' → +10  
else → +5

