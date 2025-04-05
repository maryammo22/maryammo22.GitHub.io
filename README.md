import random
import pandas as pd

# قائمة أسماء أولية
first_names = ["أحمد", "محمد", "سارة", "نورا", "خالد", "فيصل", "رنا", "ليلى", "سلمان", "جواهر", "عبدالله", "ريم", "فهد", "مها", "تركي", "هدى", "بندر", "منال", "ياسر", "دلال"]
last_names = ["العنزي", "السبيعي", "القحطاني", "الشمري", "الغامدي", "العتيبي", "الدوسري", "الشمراني", "الهزاع", "الحربي"]

# إنشاء البيانات
employees = []
for _ in range(40):
    name = f"{random.choice(first_names)} {random.choice(last_names)}"
    extension = random.randint(1000, 9999)
    employees.append({"الاسم": name, "التحويلة": extension})

# تحويلها إلى جدول
df = pd.DataFrame(employees)

# عرض الجدول
print(df)
