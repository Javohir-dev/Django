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
9. **`exclude()` - bu Django ORM-da ishlatiladigan metod, ma'lumotlar bazasidan ma'lumotlarni tanlashda qo'llaniladi. Bu metod qo'llanilgan daraja ko'proq ma'lumotlarni tanlashda foydalaniladi va ma'lumotlar bazasidan tanlangan ma'lumotlarni ekskluziv ravishda chiqarish uchun ishlatiladi.**

Masalan, agar siz bir nechta ma'lumotlarni olishni xohlasangiz va ular ichidan qandaydir bir qismini tanlamaslik kerak bo'lsa, `exclude()` metodi juda foydali bo'ladi. Misol uchun:

```python
from myapp.models import MyModel

# MyModel jadvallaridan `some_field` qiymati 'some_value' ga teng bo'lmagan barcha ma'lumotlarni olish
filtered_data = MyModel.objects.exclude(some_field='some_value')
```


# 
# Django ORM
###  1. Telefon raqam ichida 4422 bor bo'lgan barcha userlarni ichiga oladi.**
```python
key = Key.objects.filter(key_id__icontains=6605)
```
###  2. Faqat kerakli fieldlarnigini DB-dan sug'urib oladi.
```python
key = Key.objects.all().values('status', 'key_id') 
```
```bash
>>> key
<QuerySet [{'status': 'CKD', 'key_id': 7998}, {'status': 'CKD', 'key_id': 6605}]>
```
### 3. Faqat kerakli fieldlarnigining qiymatlarini DB-dan sug'urib oladi.
```python
key = Key.objects.all().values_list('status', 'key_id') 
```
```bash
>>> key
<QuerySet [('CKD', 7998), ('CKD', 6605)]>
```
