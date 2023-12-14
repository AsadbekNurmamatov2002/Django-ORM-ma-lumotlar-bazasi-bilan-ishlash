# Django-ORM-ma-lumotlar-bazasi-bilan-ishlash

## django models.py da ma'lumotlar omborini yaratamiz

#### Post-postlar degan model tuzaylik
>        from django.db import models
>        from django.utils import timezone
>        from django.contrib.auth.models import User
> 
>        class Post(models.Modle):
>            class Status(models.TextChoices):
>               NASHIR_QILINMAGAN = 'NQIL', 'Nashir qilinmagan'
>               NASHER_QILINGAN = 'NQMG', 'Nashir qilingan '
>        title = models.CharField(max_length=250)
>        slug = models.SlugField(max_length=250)
>        author = models.ForeignKey(User, on_delete=models.CASCADE, related_name='blog_posts')
>        body = models.TextField()
>        created = models.DateTimeField(auto_now_add=True)
>        publish = models.DateTimeField(default=timezone.now)
>        updated = models.DateTimeField(auto_now=True)
>        status = models.CharField(max_length=2, choices=Status.choices, default=Status.NASHIR_QILINMAGAN)
>        class Meta:
>            ordering = ['-publish']
>            indexes = [
>                models.Index(fields=['-publish']),
>            ]
>        def __str__(self):
>            return self.title

![image](https://github.com/AsadbekNurmamatov2002/Django-ORM-ma-lumotlar-bazasi-bilan-ishlash/assets/144318530/094ac298-9874-4d9b-93ab-aa9e3f64e72c)

### title-sarlavha CharField() odatda ism, familiya kabi kichik satrlarni saqlash uchun ishlatiladi. Kattaroq matnni saqlash uchun TextField ishlatiladi.
*    __Null__-Agar True bo'lsa , Django bo'sh qiymatlarni ma'lumotlar bazasida NULL sifatida saqlaydi . Birlamchi parametr False .
*    __Blank__-Agar True bo'lsa , maydon bo'sh bo'lishiga ruxsat beriladi. Birlamchi parametr False .
*    __db_column__-Ushbu maydon uchun foydalaniladigan ma'lumotlar bazasi ustunining nomi. Agar bu berilmasa, Django maydon nomidan foydalanadi.
*    __db_index__-	Agar True bo'lsa, bu maydon uchun ma'lumotlar bazasi indeksi yaratiladi
 *   __help_text__-Shakl vidjeti bilan ko'rsatiladigan qo'shimcha "yordam" matni. Bu sizning maydoningiz formada ishlatilmasa ham, hujjatlar uchun foydalidir.
*    __primary_key__-Agar rost bo'lsa, bu maydon model uchun asosiy kalit hisoblanadi.
*    __error_messages__-error_messages argumenti maydon ko'taradigan standart xabarlarni bekor qilish imkonini beradi. Siz bekor qilmoqchi bo'lgan xato xabarlariga mos keladigan kalitlar 
bilan lug'atga o'ting.

*    __verbose_name__-Maydon uchun odam o‘qiy oladigan nom. Agar batafsil nom berilmagan bo'lsa, Django uni avtomatik ravishda maydonning atribut nomidan foydalanib yaratadi va pastki chiziqni bo'sh joylarga aylantiradi.
*    __validators__-Bu maydon uchun ishga tushiriladigan validatorlar roʻyxati. Qo'shimcha ma'lumot uchun validator hujjatlariga qarang .
*    __Unique__-Agar rost bo'lsa, bu maydon butun jadvalda yagona bo'lishi kerak.

  
 ### slug-SlugField asosan ma'lum bir URL manzilidan keyin URL yo'llarini saqlash uchun ishlatiladi. 
*    __Null__-Agar True bo'lsa , Django bo'sh qiymatlarni ma'lumotlar bazasida NULL sifatida saqlaydi . Birlamchi parametr False .
*    __Blank__-Agar True bo'lsa , maydon bo'sh bo'lishiga ruxsat beriladi. Birlamchi parametr False .
*    __db_column__-Ushbu maydon uchun foydalaniladigan ma'lumotlar bazasi ustunining nomi. Agar bu berilmasa, Django maydon nomidan foydalanadi.
*    __Default__-Maydon uchun standart qiymat. Bu qiymat yoki chaqiriladigan ob'ekt bo'lishi mumkin. Agar chaqirish mumkin bo'lsa, u har safar yangi ob'ekt yaratilganda chaqiriladi.
*    __help_text__-Shakl vidjeti bilan ko'rsatiladigan qo'shimcha "yordam" matni. Bu sizning maydoningiz formada ishlatilmasa ham, hujjatlar uchun foydalidir.
*    __primary_key__-Agar rost bo'lsa, bu maydon model uchun asosiy kalit hisoblanadi.
*    __editable__-Agar False bo'lsa , maydon administratorda yoki boshqa ModelFormda ko'rsatilmaydi. Modelni tekshirish vaqtida ular ham o'tkazib yuboriladi. Standart True .
*    __error_messages__-error_messages argumenti maydon ko'taradigan standart xabarlarni bekor qilish imkonini beradi. Siz bekor qilmoqchi bo'lgan xato xabarlariga mos keladigan kalitlar bilan lug'atga o'ting.

*    __verbose_name__-Maydon uchun odam o‘qiy oladigan nom. Agar batafsil nom berilmagan bo'lsa, Django uni avtomatik ravishda maydonning atribut nomidan foydalanib yaratadi va pastki chiziqni bo'sh joylarga aylantiradi.
*    __validators__-Bu maydon uchun ishga tushiriladigan validatorlar roʻyxati. Qo'shimcha ma'lumot uchun validator hujjatlariga qarang .
*    __Unique__-Agar rost bo'lsa, bu maydon butun jadvalda yagona bo'lishi kerak.

  ## Django Field Choices dan qanday foydalanish mumkin?
  * Django dala tanlovlari. Hujjatlarga ko'ra, Field Choices - bu ba'zi maydonlar uchun tanlov sifatida foydalanish uchun aynan ikkita elementning (masalan, [ (A, B), (A, B) …]) takrorlanadiganlaridan iborat ketma-ketlik.

masalan: Har bir kortejdagi birinchi element modelga o'rnatilishi kerak bo'lgan haqiqiy qiymat, ikkinchi element esa odam o'qiy oladigan nomdir.
>       from django.db import models 
>       SEMESTER_CHOICES = ( 
>           ("1", "1"), 
>           ("2", "2"), 
>           ("3", "3"), 
>           ("4", "4"), 
>           ("5", "5"), 
>           ("6", "6"), 
>           ("7", "7"), 
>           ("8", "8"), 
>        ) 
>
>       class Student(models.Model): 
>              semester = models.CharField( max_length = 20, choices = SEMESTER_CHOICES, default = '1' )
![image](https://github.com/AsadbekNurmamatov2002/Django-ORM-ma-lumotlar-bazasi-bilan-ishlash/assets/144318530/a0eaa28a-90b2-4e5f-afe7-65df08546682)
misol:
![image](https://github.com/AsadbekNurmamatov2002/Django-ORM-ma-lumotlar-bazasi-bilan-ishlash/assets/144318530/ecf6a09a-2033-42de-b335-9c9160512fb8)
![image](https://github.com/AsadbekNurmamatov2002/Django-ORM-ma-lumotlar-bazasi-bilan-ishlash/assets/144318530/8e817a07-715d-4b31-840a-bd61ac76bdf6)
misol: __tepadage misolbiln birxil_
![image](https://github.com/AsadbekNurmamatov2002/Django-ORM-ma-lumotlar-bazasi-bilan-ishlash/assets/144318530/d7d20e5c-6254-4dd1-ab98-ace7b8977312)

![image](https://github.com/AsadbekNurmamatov2002/Django-ORM-ma-lumotlar-bazasi-bilan-ishlash/assets/144318530/207881e7-acd0-45d8-882c-c20f0ea33ab7)


# Django-orqali yangiliklar web-site qilamiz 
* py -m venv myenv
* myenv\Scripts\activate.bat 
* py -m pip install django
* django-admin --version
* django-admin startproject now_project
* cd now_project
* py manage.py runserver
* CTRL+C
* py manage.py startapp nowapp
* mkdir templates
* mkdir static
* mkdir media
* dir
* code .
* 
  

