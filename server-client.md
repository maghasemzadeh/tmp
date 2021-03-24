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

# اجرای سرور

برای اجرای سرور آخرین نسخه ریلیز سرور را از این ریپو دانلود کنید (فایل server.jar). سپس سرور را به این شکل اجرا کنید:  
`java -jar server.jar --first-team=/path/to/first/client --second-team=/path/to/second/client`
  
در بالا دو آرگومان اول محل قرار گیری فایل کلاینت برای تیم اول و تیم دوم را مشخص می کنند. این فایل برای کلاینت جاوا همان فایل jar تولید شده است ، برای کلاینت پایتون خروجی باینری و برای کلاینت cpp همان خروجی حاصل از بیلد گرفتن کلاینت است.  
  
دقت کنید که اگر فایل کلاینت شما در پوشه سرور قرار دارد (مثلا نام آن client است) از ./ در ابتدای آن استفاده کنید:  
`--first-team=./client`

برای نمایش لاگ بیشتر از سرور جهت دیباگ کردن (و همچنین نمایش خروجی کلاینت ها در لاگ سرور) از آرگومان `--show-log` نیز  می‌توانید استفاده کنید.  
مثال:   
`java -jar server.jar --first-team=/path/to/first/client --second-team=/path/to/second/client --show-log`
  
با استفاده از آرگومان `--max-agent` می توانید یک کران بالا برای تعداد نیرو های ساخته شد (instance های اجرایی از کلاینت) تعیین کنید تا سیستم شما دچار مشکل در اجرا نشود (پیشنهاد ما حداکثر ۵۰ است)

مثال:  
 `java -jar server.jar --first-team=/path/to/first/client --second-team=/path/to/second/client --max-agent=20`  
 این مقدار به طور پیش فرض 200 در نظر گرفته می شود.
در صورت تمایل به اجرای کلاینت ها بصورت دستی، می توانید از آرگومان `--run-manually` استفاده کنید. در این صورت هر موقع سرور منتظر وصل شدن کلاینت جدید ماند، باید یک instance از کلاینت خود را دستی اجرا کنید. در این صورت می توانید به طور کامل لاگ کلاینت را در کنسول مشاهده کنید. (در این صورت توصیه می شود از اعداد کوچک برای `inital_ant_num` در `map.config` استفاده کنید.)

+ برای تست کردن کد، با تعداد کم نیرو این روش بسیار مفید خواهد بود. ضمن این که برای اجرا در این روش نیازی به خروجی گرفتن از کلاینت نیست.  

+ دقت کنید که هرموقع نیاز به کلاینت جدید بود، سرور در خروجی ای رشته را چاپ می کند:  
`Run a new instance of your client, waiting...`
