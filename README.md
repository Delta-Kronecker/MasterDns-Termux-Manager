# MasterDnsVPN Client Termux Manager

**مدیریت حرفه‌ای MasterDnsVpn برای Termux اندروید**

---

⭐ **اگر این برنامه برایتان مفید بوده، لطفاً با زدن دکمه Star در صفحه گیت‌هاب پروژه از توسعه‌دهنده حمایت کنید. زدن یک دکمه از طرف شما انگیزه بزرگی برای ادامه توسعه پروژه‌های متن‌باز است .**

---
 
## 📥 نصب

### مرحله ۱: آماده‌سازی

۱. فایل `MasterDNS.zip` را از بخش Releases و یا [این لینک] دانلود کنید و در پوشه **Download** گوشی خود قرار دهید. مسیر دقیق:

   ```
   /storage/emulated/0/Download/
   ```

۲. برنامه **Termux** را از [F-Droid](https://f-droid.org/packages/com.termux/) و یا [Github](https://github.com/termux/termux-app/releases/tag/v0.118.3) نصب کنید.

### مرحله ۲: اجرای دستور نصب

Termux را باز کنید و این دستور را **دقیقاً به صورت کامل** کپی و اجرا کنید:

```bash
termux-setup-storage && sleep 5 && cd /storage/emulated/0/download/ && unzip MasterDNS.zip && mv MasterDNS /data/data/com.termux/files/home/masterdns && cd /data/data/com.termux/files/home/masterdns && chmod +x masterdns_manager.sh masterdns_resources.sh && echo 'alias master="bash ~/masterdns/masterdns_manager.sh"' >> ~/.bashrc && source ~/.bashrc && exit
```

پس از اجرای این دستور:

- اگر پیام **"Allow Termux to access photos, media and files?"** ظاهر شد، **Allow** را بزنید.
- صبر کنید تا مراحل استخراج و نصب انجام شود.
- **Termux به طور خودکار بسته می‌شود.** این نشانه پایان موفقیت‌آمیز نصب است.

### مرحله ۳: اجرای برنامه

پس از نصب، هر زمان که خواستید برنامه را اجرا کنید:

۱. برنامه **Termux** را باز کنید.
۲. دستور زیر را تایپ کرده و Enter بزنید:

   ```bash
   master
   ```

برنامه اجرا می‌شود. از این به بعد همیشه با زدن `master` می‌توانید برنامه را اجرا کنید.

---

## 🧭 منوی اصلی

تمام گزینه‌ها با یک کلید (بدون Enter) اجرا می‌شوند:

| کلید | عملکرد |
|:----:|--------|
| `1` | Start Client |
| `2` | Stop Client |
| `3` | Edit Current Profile |
| `4` | Resolvers (lists & scanner) |
| `5` | View Log |
| `6` | Manage Profiles |
| `7` | MTU Speed Test |
| `8` | Multi‑Connection |
| `9` | Resolver Health Check |
| `0` | Settings |
| `q` | Exit |
| `h` | Help |

---

## ✨ توضیح بخش‌ها

### ۱. Start Client

اجرای کلاینت. در صورت خالی بودن فایل ریزالور یا load نبودن هیچ پروفایلی هشدار می‌دهد.

### ۲. Stop Client

توقف کلاینت.

### ۳. Edit Current Profile

ویرایش مستقیم `client_config.toml` با nano همراه با آموزش ذخیره و خروج.

### ۴. Resolvers (lists & scanner)

۶ زیرگزینه:

1. **Edit current resolver list**
   ویرایش `client_resolvers.txt` با nano

2. **Switch to a different list**
   انتخاب از لیست‌های ذخیره‌شده در `resolver_lists/`

3. **Import / add a new list**
   پیست کردن از کیبورد یا انتخاب فایل txt از حافظه

4. **Delete a saved list**
   حذف لیست‌های ذخیره‌شده

5. **Scanner: auto‑discover working resolvers**
   اسکن خودکار روی پورت ۱۸۰۰۹ با نوار پیشرفت زنده. توقف خودکار با Q یا آماده شدن پروکسی. ذخیره نتایج به عنوان لیست جدید

### ۵. View Log

نمایش زنده `client.log` . خروج با Q و پاکسازی کامل صفحه.

### ۶. Manage Profiles

۴ زیرگزینه:

1. **Create**
   انتخاب از ۸ قالب تخصصی یا ساخت همه قالب های اماده. دریافت نام، دامنه و کلید.

2. **Load**
   لیست پروفایل‌های ذخیره‌شده، انتخاب شماره، توقف کلاینت فعلی و بارگذاری پروفایل جدید

3. **Delete**
   حدف پروفایل
### ۷. MTU Speed Test

۶ مرحله متوالی با پورت‌های ۱۸۰۰۱ تا ۱۸۰۰۶ و بازه‌های مختلف Upload/Download MTU. دانلود ۲MB از Cloudflare. کنترل‌ها: L لاگ، S رد کردن مرحله، Q لغو کل تست. جدول مقایسه نهایی با هایلایت بهترین.

### ۸. Multi‑Connection

۳ زیرگزینه:

1. **Different Profiles (up to 8)**
   انتخاب پروفایل‌ها با کاما (`0,2,5,7`) یا همه (y). پورت‌های ۱۸۰۰۱+. داشبورد زنده با ۸ ستون. کنترل‌ها: V لاگ نمونه، S توقف همه

2. **Different MTU Ranges (6)**
   ۶ نمونه همزمان با بازه‌های MTU مختلف روی پورت‌های ۱۸۰۰۱ تا ۱۸۰۰۶

### ۹. Resolver Health Check

تست استرس ریزالورها از طریق پروکسی فعال. دو نوع تست:

- **Cloudflare download** – دانلود فایل با سایز دلخواه
- **Telegram ping** – پینگ HTTPS به تلگرام

تنظیم Timeout و Interval (ثانیه). ارسال موازی (حداکثر ۱۰ درخواست همزمان). نمایش لحظه‌ای YES/NO با تغییرات ریزالورها (↑↓=). گزارش نهایی با آمار کامل و تعداد ریزالورهای حذف/اضافه شده.

### ۰. Settings

۷ زیرگزینه:

1. **Change MTU parallelism percentage**
   تنظیم درصد همزمانی تست MTU (۱-۱۰۰) مثلا با 1000 ریزالور و 10 درصد، تست ریزالور ها در گروه هایی 100 تایی انجام می شود، 10 درصد پیشنهاد می شود

3. **Toggle auto‑manage parallelism**
   محاسبه خودکار `MTU_TEST_PARALLELISM` بر اساس تعداد ریزالورها و درصد تنظیم‌شده

4. **Backup all configurations**
   فشرده‌سازی کل پوشه `Configuration/` به فایل tar.gz با timestamp

5. **Restart Client**
   توقف + راه‌اندازی مجدد کلاینت

6. **Show tunnel info**
   نمایش دامنه، کلید رمزنگاری و نام پروفایل فعال

7. **Clear client log**
   خالی کردن فایل `client.log`


## ⚠️ سلب مسئولیت

این برنامه **فقط برای اهداف آموزشی و تحقیقاتی** ارائه شده است.

- **محدودیت مسئولیت:** توسعه‌دهنده هیچ مسئولیتی در قبال آسیب‌های مستقیم، غیرمستقیم، ناشی از استفاده از این نرم‌افزار ندارد.
- **قوانین محلی:** استفاده از این پروژه برای دور زدن قوانین محلی ممکن است عواقب قانونی داشته باشد توسعه‌ده هیچ مسئولیتی در قبال این موضوع ندارد
