---
id: namespaces
title: فضانام‌ها یا Namespaces
sidebar_label: فضانام‌ها
---


## فضانام‌ها

![Fandogh Network](/img/docs/fandogh-namespaces.png "Fandogh Namespaces")


هر Namespace یک فضای مجازی بر روی ابر فندق است. سرویس‌های شما بر روی Namespaceای که خود شما موقع ثبت نام، نام آن را مشخص کرده‌اید اجرا می‌شوند. سرویس‌های یک Namespace از طریق شبکه داخلی می‌توانند به یک‌دیگر دسترسی داشته باشند.
### شبکه داخلی فضانام‌ها
 هر سرویس درون یک فضانام دارای یک آدرس `IP` و یک `service_name` است.
برای درک بهتر موضوع به تصویر زیر توجه کنید.

![Fandogh Network](/img/docs/service_relation.png "Fandogh Network")

همانگونه که مشاهده می کنید در این Namespace تعداد 4 سرویس ساخته شده است و فندق به هر سرویس ایجاد شده یک IP اختصاص داده است، همینطور هر سرویس دارای مشخصه دیگری به نام `service_name` است.
مشخصه اصلی برای آنکه سرویس‌ها همدیگر را پیدا کنند و با هم تعامل داشته باشند `service_name` است، زیرا که اگر تحت هر شرایطی یکی از سرویس‌ها Redeploy شود، IP جدیدی به آن تخصیص داده خواهد شد.
برای مثال اگر فرض کنیم سرویس SVC1 با SVC2 در تعامل بوده ولی بعد از مدتی
نسخه جدیدی از سرویس SVC2 بر روی فندق deploy شده باشد، سرویس SVC1 با پرس و جو از DNS می‌تواند IP جدید سرویس مورد نظر را پیدا کند و به تعامل ادامه دهد.
### سرویس DNS فضانام‌ها
همانطور که می‌دانیم هر وب‌سایت و یا وب‌‌سرویس در فضای اینترنت دارای یک شناسه با نام IP است، اما از آنجایی که بخاطر سپردن این IP Addressها دشوار است، از سرویسی به نام DNS یا Domain Name System استفاده می‌شود، این سرویس وظیفه ترجمه نام‌ها به IP منتسب شده به آن را بر عهده دارد.
در فندق نیز هر Namespace دارای DNS Server مختص به خود است که وظیفه ترجمه نام سرویس‌ها به IP سرویس را بر عهده دارد.
![Fandogh DNS](/img/docs/dns_namespace.png "Fandogh DNS")
### فضای ذخیره‌سازی فضانام‌ها
همانطور که انتظار می‌رود هر سرویس باید بتواند در فضایی مانا اطلاعات خود را ذخیره و بازیابی کند، به همین جهت هر Namepace به همراه یک Persistent Storage یا فضای ذخیره‌سازی مانا  ساخته می‌شود.
به صورت پیش فرض همه سرویس‌ها به این فضای اطلاعاتی دسترسی دارند و می‌توانند عملیات Read و Write بر روی آن انجام دهند.
![Fandogh Storage](/img/docs/shared_storage.png "Fandogh Storage")