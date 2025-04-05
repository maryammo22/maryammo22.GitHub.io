from faker import Faker
import pandas as pd
import random

# إنشاء مولد بيانات باللغة العربية
fake = Faker('ar_EG')

# قائمة وظائف وأقسام
job_titles = [
    "مدير مشروع", "محاسب", "أخصائي تسويق", "مطور برمجيات",
    "مصمم جرافيك", "مدير موارد بشرية", "مهندس شبكات",
    "فني دعم", "كاتب محتوى", "محلل نظم", "مساعد إداري", "مندوب مبيعات"
]

departments = [
    "تقنية المعلومات", "المالية", "الموارد البشرية",
    "المبيعات", "التسويق", "التصميم", "الدعم الفني"
]

status_options = ["نشط", "غير نشط"]

# إنشاء البيانات
employees = []
for i in range(40):
    name = fake.name()
    extension = random.randint(1000, 9999)
    job = random.choice(job_titles)
    dept = random.choice(departments)
    email = f"{name.split()[0].lower()}.{name.split()[-1].lower()}@company.com"
    hire_date = fake.date_between(start_date='-10y', end_date='today')
    salary = random.randint(5000, 20000)
    status = random.choice(status_options)

    employees.append({
        "الرقم": i + 1,
        "الاسم": name,
        "المسمى الوظيفي": job,
        "القسم": dept,
        "التحويلة": extension,
        "البريد الإلكتروني": email,
        "تاريخ التوظيف": hire_date.strftime('%Y-%m-%d'),
        "الراتب الشهري": f"{salary} ريال",
        "الحالة": status
    })

# تحويل إلى جدول
df = pd.DataFrame(employees)

# عرض الجدول
print(df)

# حفظ إلى Excel
df.to_excel("جدول_تفصيلي_للموظفين.xlsx", index=False)
