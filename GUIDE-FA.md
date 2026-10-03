# 🚀 راهنمای گام‌به‌گام — Azurynth (پنل ادمین + دامنه)

## وضعیت فعلی
- محصولات دیگر داخل کد نیستن؛ از فایل `products.json` خونده میشن.
- پوشه `admin/` پنل مدیریت (Decap CMS) رو داره.

─────────────────────────────
## مسیر A: پنل ادمین واقعی (Netlify — پیشنهادی)
۱. **گیت‌هاب:** به github.com برو → New repository → اسم: `azurynth-site` → Create.
   روی "uploading an existing file" کلیک کن و **کل پوشه پروژه** (index.html، products.json،
   پوشه‌های css / js / assets / admin) رو بکش توی ریپو → Commit changes.
۲. **نتلیفای:** app.netlify.com → Add new site → Import an existing project → GitHub →
   ریپو `azurynth-site` رو انتخاب کن → Build command خالی بذار، Publish directory بذار `/` → Deploy.
۳. **فعال‌سازی ادمین (خیلی مهم):**
   - Site configuration → **Identity** → Enable Identity
   - Registration preferences → **Invite only**
   - Services → **Git Gateway** → Enable
۴. **ورود به پنل:** برو `https://نام‌سایت.netlify.app/admin`
   یک بار از Netlify Identity → Invite users ایمیلت رو دعوت کن، لینک ایمیل رو باز کن،
   رمز بساز — بعدش هر بار با ایمیل+رمز وارد پنل میشی.
۵. **اضافه کردن محصول:** توی پنل → Product Catalog → Products → + →
   اسم، توضیح، قیمت، نوع (Template/Background)، تم پیش‌نمایش → Publish.
   حدود ۱ دقیقه بعد خودکار روی سایت زنده میشه! ✅

─────────────────────────────
## مسیر B: ماندن روی Cloudflare Pages (بدون پنل، ولی راحت)
۱. همون ریپو گیت‌هاب رو بساز (مثل مرحله 1 مسیر A).
۲. Cloudflare → Workers & Pages → Create → Connect to Git → ریپو رو انتخاب کن →
   Build settings: None → Deploy. (از این به بعد هر تغییر روی گیت‌هاب = انتشار خودکار)
۳. برای اضافه کردن محصول: توی گیت‌هاب روی `products.json` → آیکون مداد ✏️ →
   یک بلاک محصول کپی و ویرایش کن → Commit → سایت بعد ~۱ دقیقه آپدیت میشه.

─────────────────────────────
## اتصال دامنه azurynth.com (هیچ‌چیزی رو حذف نکن!)
لندینگ پیج فعلی با تغییر DNS خودکار پاک میشه — فقط کافیه دامنه رو به هاست وصل کنی:

**روش تمیز (Nameserver):**
۱. توی داشبورد Cloudflare (یا Netlify) دامنه رو Add کن.
۲. بهت 2 تا nameserver میده (مثل `lara.ns.cloudflare.com`).
۳. برو پیش جایی که دامنه رو خریدی (رجیسترار) → DNS/Nameservers →
   Nameserver های قبلی رو با این 2 تا عوض کن.
۴. توی پنل هاست → Custom domains / Domain management → `azurynth.com` و `www.azurynth.com` رو Add کن.
   SSL رایگان خودکار فعال میشه. ⏳ انتشار DNS تا 24 ساعت طول میکشه (معمولاً 5 دقیقه).

─────────────────────────────
## ساخت صفحه جدید
یک فایل `page-name.html` توی ریپو بساز (می‌تونی از index.html کپی بگیری و محتواش رو عوض کنی)،
بعد لینکش رو توی منوی ناوبری index.html اضافه کن. با اتصال Git خودکار منتشر میشه.

─────────────────────────────
## نکته امنیتی ⚠️
پنل ادمین رو حتماً روی «Invite only» بذار (فقط خودت دعوت بشی).
