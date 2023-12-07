# Django-ORM-ma-lumotlar-bazasi-bilan-ishlash

django models.py da ma'lumotlar omborini yaratamiz

Post-postlar degan model tuzaylik
>        from django.db import models
>        from django.utils import timezone
>        from django.contrib.auth.models import User
> 
>        class Post(models.Modle):
>        class Status(models.TextChoices):
>            DRAFT = 'DF', 'Draft'
>            PUBLISHED = 'PB', 'Published'
>        title = models.CharField(max_length=250)
>        slug = models.SlugField(max_length=250)
>        author = models.ForeignKey(User, on_delete=models.CASCADE, related_name='blog_posts')
>        body = models.TextField()
>        created = models.DateTimeField(auto_now_add=True)
>        publish = models.DateTimeField(default=timezone.now)
>        updated = models.DateTimeField(auto_now=True)
>        status = models.CharField(max_length=2, choices=Status.choices, default=Status.DRAFT)
>        class Meta:
>            ordering = ['-publish']
>            indexes = [
>                models.Index(fields=['-publish']),
>            ]
>        def __str__(self):
>            return self.title

![image](https://github.com/AsadbekNurmamatov2002/Django-ORM-ma-lumotlar-bazasi-bilan-ishlash/assets/144318530/094ac298-9874-4d9b-93ab-aa9e3f64e72c)

title-sarlavha CharField() odatda ism, familiya kabi kichik satrlarni saqlash uchun ishlatiladi. Kattaroq matnni saqlash uchun TextField ishlatiladi.
*    Null-Agar True bo'lsa , Django bo'sh qiymatlarni ma'lumotlar bazasida NULL sifatida saqlaydi . Birlamchi parametr False .
*    Blank-Agar True bo'lsa , maydon bo'sh bo'lishiga ruxsat beriladi. Birlamchi parametr False .
*    db_column-Ushbu maydon uchun foydalaniladigan ma'lumotlar bazasi ustunining nomi. Agar bu berilmasa, Django maydon nomidan foydalanadi.
*    db_index-	Agar True bo'lsa, bu maydon uchun ma'lumotlar bazasi indeksi yaratiladi
 *   help_text-Shakl vidjeti bilan ko'rsatiladigan qo'shimcha "yordam" matni. Bu sizning maydoningiz formada ishlatilmasa ham, hujjatlar uchun foydalidir.
*    primary_key-Agar rost bo'lsa, bu maydon model uchun asosiy kalit hisoblanadi.
*    error_messages-error_messages argumenti maydon ko'taradigan standart xabarlarni bekor qilish imkonini beradi. Siz bekor qilmoqchi bo'lgan xato xabarlariga mos keladigan kalitlar 
bilan lug'atga o'ting.

*    verbose_name-Maydon uchun odam o‘qiy oladigan nom. Agar batafsil nom berilmagan bo'lsa, Django uni avtomatik ravishda maydonning atribut nomidan foydalanib yaratadi va pastki chiziqni bo'sh joylarga aylantiradi.
*    validators-Bu maydon uchun ishga tushiriladigan validatorlar roʻyxati. Qo'shimcha ma'lumot uchun validator hujjatlariga qarang .
*    Unique-Agar rost bo'lsa, bu maydon butun jadvalda yagona bo'lishi kerak.

  
slug-SlugField asosan ma'lum bir URL manzilidan keyin URL yo'llarini saqlash uchun ishlatiladi. 
*    Null-Agar True bo'lsa , Django bo'sh qiymatlarni ma'lumotlar bazasida NULL sifatida saqlaydi . Birlamchi parametr False .
*    Blank-Agar True bo'lsa , maydon bo'sh bo'lishiga ruxsat beriladi. Birlamchi parametr False .
*    db_column-Ushbu maydon uchun foydalaniladigan ma'lumotlar bazasi ustunining nomi. Agar bu berilmasa, Django maydon nomidan foydalanadi.
*    Default-Maydon uchun standart qiymat. Bu qiymat yoki chaqiriladigan ob'ekt bo'lishi mumkin. Agar chaqirish mumkin bo'lsa, u har safar yangi ob'ekt yaratilganda chaqiriladi.
*    help_text-Shakl vidjeti bilan ko'rsatiladigan qo'shimcha "yordam" matni. Bu sizning maydoningiz formada ishlatilmasa ham, hujjatlar uchun foydalidir.
*    primary_key-Agar rost bo'lsa, bu maydon model uchun asosiy kalit hisoblanadi.
*    editable-Agar False bo'lsa , maydon administratorda yoki boshqa ModelFormda ko'rsatilmaydi. Modelni tekshirish vaqtida ular ham o'tkazib yuboriladi. Standart True .
*    error_messages-error_messages argumenti maydon ko'taradigan standart xabarlarni bekor qilish imkonini beradi. Siz bekor qilmoqchi bo'lgan xato xabarlariga mos keladigan kalitlar bilan lug'atga o'ting.

*    verbose_name-Maydon uchun odam o‘qiy oladigan nom. Agar batafsil nom berilmagan bo'lsa, Django uni avtomatik ravishda maydonning atribut nomidan foydalanib yaratadi va pastki chiziqni bo'sh joylarga aylantiradi.
*    validators-Bu maydon uchun ishga tushiriladigan validatorlar roʻyxati. Qo'shimcha ma'lumot uchun validator hujjatlariga qarang .
*    Unique-Agar rost bo'lsa, bu maydon butun jadvalda yagona bo'lishi kerak.
  
