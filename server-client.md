+ شما باید کد هوش مصنوعی خود را در تابع turn که در فایل AI.java (در تمامی کلاینت‌ها فایلی با همین اسم قرار دارد)، پیاده‌سازی کنید.

+ شما می‌توانید کد کلاینت داده شده را تغییر دهید، به آن فایل اضافه کنید یا از آن فایل حذف کنید، به شرط آنکه تغییرات داده شده در کامپایل و اجرای کلاینت و ارتباط آن با سرور اختلالی ایجاد نکند. در مورد هر کلاینت نکاتی ذکر شده که به آن‌ها نیز باید توجه شود. همچنین باید تغییرات احتمالی فایل‌های دیگر کلاینت، یعنی فایل‌هایی غیر از فایلی که در آن کد می‌زنید) را در نظر بگیرید.

+ شما می‌توانید برای به روز بودن کلاینت‌ها یا سرور خود به آخرین نسخه منتشر شده در repository مسابقه مراجعه کنید.
  
  * [کلاینت C++](https://github.com/SharifAIChallenge/AIC20-Client-Cpp)
  * [کلاینت Java](https://github.com/SharifAIChallenge/AIC20-Client-Java)
  * [کلاینت Python](https://github.com/SharifAIChallenge/AIC20-Client-Python)

# کلاینت جاوا

کلاینت‌های جاوا، برای اجرا توسط سرور، باید به فایل jar تبدیل شوند. برای ساخت فایل jar کلاینت جاوا، باید از Intellij استفاده کنید. در Intellij، از مسیر زیر می‌توانید فایل jar رابسازید.  

`File --> Project Structure --> Project Settings --> Artifacts --> green plus sign --> Jar --> From modules with dependencies`

![jar](https://github.com/maghasemzadeh/tmp/blob/main/jar.png)

هر بار که تغییری در کد کلاینت داده شد، برای اجرا باید یک فایل jar تازه ساخته‌شود. مراحل ساخت فایل jar و اطلاعات بیشتر را در [داکیومنتیشن Intellij](https://www.jetbrains.com/help/idea/compiling-applications.html#compile_module) و همچنین [این پست در Stack Overflow](https://stackoverflow.com/questions/1082580/how-to-build-jars-from-intellij-properly) نیز می‌توانید مشاهده کنید.

# کلاینت پایتون

برای اجرای کلاینت‌های پایتون، باید کدها و تمامی dependency ها در یک پکیج تجمیع شود (Binary). این کار با ابزار [Pyinstaller](https://pypi.org/project/pyinstaller/) به راحتی امکان‌پذیر است. برای نصب این پکیج، می‌توانید از دستور pip install pyinstaller استفاده کنید. اگر pip را نصب ندارید، طریقه‌ی نصب آن روی سیستم‌عامل‌های مختلف، از لینک‌های زیر مشاهده کنید:  

  * [Windows](https://phoenixnap.com/kb/install-pip-windows)

  * [Linux](https://www.tecmint.com/install-pip-in-linux/)

  * [Mac OS](https://ahmadawais.com/install-pip-macos-os-x-python/)

دقت کنید که پس از هر بار تغییر در کد، پوشه های build و dist را پاک کنید و مجددا با PyInstaller بیلد بگیرید.
