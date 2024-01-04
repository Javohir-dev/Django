Django ORM (Object-Relational Mapping) ko'p imkoniyatlar bilan ta'minlangan va oddiy vaqt sifatida ishlovchi funksiyalarga ega. Quyidagi eng kerakli funksiyalarni ko'rsatishim mumkin:

1. **Qo'shimcha yaratish (Creating additional entries):**
   ```python
   new_instance = MyModelName(field1='value1', field2='value2')
   new_instance.save()
   ```

2. **Ma'lumotlarni o'qish (Reading data):**
   - Barcha obyektlarni o'qish:
     ```python
     all_objects = MyModelName.objects.all()
     ```
   - Shartni qo'llab-quvvatlash:
     ```python
     filtered_objects = MyModelName.objects.filter(some_field='some_value')
     ```
   - Bitta obyektni o'qish:
     ```python
     single_object = MyModelName.objects.get(id=1)
     ```

3. **Ma'lumotlarni yangilash (Updating data):**
   ```python
   instance = MyModelName.objects.get(id=1)
   instance.field1 = 'new_value'
   instance.save()
   ```

4. **Ma'lumotlarni o'chirish (Deleting data):**
   ```python
   instance = MyModelName.objects.get(id=1)
   instance.delete()
   ```

5. **Join operatsiyalari:**
   ```python
   related_objects = MyModelName.objects.select_related('related_model')
   ```

6. **Aggregatlar (Aggregations):**
   ```python
   from django.db.models import Avg, Max, Min, Sum

   average_value = MyModelName.objects.aggregate(avg_value=Avg('field_name'))
   ```

7. **Ma'lumotlarni tartiblash (Ordering data):**
   ```python
   ordered_objects = MyModelName.objects.order_by('field_name')
   ```

8. **Ma'lumotlarni cheklash va yangilash (Atomicity with `transaction.atomic()`):**
   ```python
   from django.db import transaction

   with transaction.atomic():
       # Ma'lumotlarni yangilash
   ```

Bu funksiyalar bilan Django ORM yordamida ma'lumotlarga kirish, ularga ega bo'lish va ularga o'zgartirishni boshqarish oson bo'ladi. Ushbu funksiyalar yordamida boshqa operatsiyalarni ham bajarishingiz mumkin, shuningdek filtratsiya, ma'lumotlar ustida matematik amallar, aggregatlar va boshqalar.