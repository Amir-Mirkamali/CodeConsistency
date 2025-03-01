# داکیومنت Code consistency

* قوانین نیز برای این وضع شده اند که کدها کاملا شبیه هم باشند و کد یکدستی داشته باشیم. بعضی از این قوانین ممکن است با سلیقه‌ی شما یکی نباشند، ولی برای حفظ  Code consistency لازم است.   
* شاید برخی از موارد زیر خیلی ساده و ابتدایی به نظر برسد ولی توجه کنید که همه‌ی برنامه نویسان در یک سطح نیستند.  
* **مسابقه ی نوشتن کد با کمترین خط نداریم\!** خوانایی کد مهترین چیزی است که باید مدنظرتان باشد. اینکه کسی بعدا کد را می‌خواند سریع متوجه شود.
* هیچ متن فارسی ای در کد نباید وجود داشته باشد. همگی به صورت resource در فایل json مربوطه قرار داده می شوند.
* استفاده از  Semicolon الزامی است.


## ابزار مورد استفاده: 

* برای کدنویسی از VSCode استفاده می کنیم. استفاده از هیچ چیز دیگری مجاز نیست.  
* یک فایل eslint تهیه شده است آن را حتما در پروژه ی خود قرار دهید و از این قوانین پیروی کنید.  
* افزونه ی eslint از microsoft را در vscode خود نصب کنید. همین فایل تقریبا اغلب استانداردها را کنترل می کند ولی بعضی کارها را باید خود برنامه نویس دقت کند که در ادامه می آوریم. (فاصله‌ها، آکولاد‌ها، پرانتزها، حلقه‌ها، switchها و استانداردهای نامگذاری اغلب در این فایل قانون‌مند شده اند)  
* تحت هیچ شرایطی از prettier یا هیچ فرمت کننده ی کدی استفاده نکنید. از خود eslint استفاده می کنیم.  
* محتویات فایل ضمیمه را در تنظیمات VSCode خود بیفزایید، VSCode باید فرمت کردن کد شما قبل از ذخیره کردن را به eslint واگذار کند.

## قوانین ظاهری:

۱. تمامی import ها باید به صورت نزولی مرتب شوند (از لحاظ طول خط)  
   مثال:  
```javascript 
   import Link from 'next/link';  
   import { useTranslations, } from 'next-intl';  
   import Typography from '@mui/material/Typography';  
   import Panel from '@/modules/general/components/panel';  
   import NewsColoredIcon from '@/modules/general/components/icons/news-colored';  
   import ArrowBackIosRoundedIcon from '@mui/icons-material/ArrowBackIosRounded';
```
     
۲. وقتی import ها دویا چند خطی می شوند به انتهای فهرست import منتقل شوند.  
```javascript
   import Link from 'next/link';  
   import { useTranslations, } from 'next-intl';  
   import Typography from '@mui/material/Typography';  
   import Panel from '@/modules/general/components/panel';  
   import {  
     useEffect, useRef, useState,  
   } from 'react';
```
۳. وقتی چند متغیر تعریف می کنید، برای همگی یک const یا یک let بگذارید. برای هر متغیر یک const لازم نیست و هر مورد را هم در یک خط جداگانه بنویسید.

```javascript
const  
    t = useTranslations(),  
    screenSize = useMediaQuery('(max-width:1100px)', { noSsr: false, }),  
    categoryId = useSearchParams().get('categoryId');
```

۴. اگر یک تایپ داریم که فقط در همین کامپوننت استفاده می شود، لازم نیست آن را جداگانه تعریف کنید و نام جداگانه‌ای برای آن بگذارید. به صورت In Place در همان فایل، جزییات را بیاورید.
۵. اگر بیش از یک پارامتر داریم، هر کدام را در یک خط جداگانه بیاورید.
```javascript
   export default function MyComponent({  
     title,  
     className,  
   }: {  
     title: string;  
     className?: string;  
   }) {   
     return (  
       <>  
       </>  
     );  
   }
```
۶. اگر از ternary operator در jsx استفاده می کنید حتما content را داخل یک پرانتز بگذارید. این مورد برای && هم صدق می کند.

```javascript
   {screenSize && (  
                   <MyComponent  
                     id={1}  
                     title={‘title’}  
                   />  
                 )}
```
۷. در یک کامپوننت اگر بیش از یک attribute داریم هنگام استفاده هر کدام در یک خط نوشته شوند. مانند مثال بالا.

۸. از نوشتن متن توابع به صورت InPlace خودداری کنید. برای مثال کد زیر استاندارد نیست. یک تابع تعریف کرده و به آن ارجاع دهید.
```javascript
onClick={() => toggleDrawer(false)}
```
۹. به هیچ عنوان ternary operator تو در تو استفاده نمی کنیم.

۱۰. محتویات یک Tag یا کامپوننت را در jsx، حتما در یک خط جدید بیاورید.
```javascript
              <Typography  
                variant='h6'  
                component={'h6'}  
              >  
                Title  
              </Typography>
```



## قوانین نامگذاری
جدول زیر به عنوان کلیات قوانین نامگذاری تعریف می شود:
| Object Name        | Notation   | Plural | Prefix | Suffix | Abbreviation | Char Mask  | Underscores |
|--------------------|------------|--------|--------|--------|--------------|------------|-------------|
| Function name      | camelCase  | Yes    | No     | Yes    | Yes          | [A-z][0-9] | No          |
| Function arguments | camelCase  | Yes    | No     | No     | Yes          | [A-z][0-9] | No          |
| Local variables    | camelCase  | Yes    | No     | No     | Yes          | [A-z][0-9] | No          |
| Constants name     | PascalCase | Yes    | No     | No     | Yes          | [A-z][0-9] | No          |
| Field name         | camelCase  | Yes    | No     | No     | Yes          | [A-z][0-9] | No          |




۱. نام توابع را خلاصه نکنید. اسم کامل عملکرد را در نام تابع بیاورید. از بلند شدن نام تابع و فایل ها نترسید. برای مثال از Calc استفاده نکنید، از کل کلمه Calculate استفاده شود.

۲. اسامی توابع به صورت camelCase نوشته می‌شوند.

۳. برای تمامی event ها از کلمه‌ی handle در ابتدای تابع استفاده می کنیم. برای مثال handleUsernameChange

۴. اسامی enum ها همگی به صورت UPPER CASE نوشته می‌شوند.
```javascript
const COLOR = {
  Red: "red",
  Blue: "blue",
  Green: "green",
}
```
۵. اسامی پارامترها به صورت camelCase نوشته می شوند.

۶. اسامی ثابت‌ها به صورت PascalCase است.

۷. اسم کامپوننت‌ها PascalCase است. سایر فایل ها را با نام کوچک نامگذاری کنید و با dash بخش های آن را از هم تفکیک کنید.

۸. برای ساختن رشته های پیچیده، همیشه از string format استفاده کنید و از + استفاده نکنید.  
   
۹. از Semicolon استفاده کنید. حذف آنها امتیاز ویژه‌ای ندارد. البته linter این مورد را تا حد زیادی کنترل می کند.
    
۱۰. کامنت فارسی ننویسید.
    
۱۱. همه ی پارامترها باید معنی دار باشند.
    
۱۲. حتما Spellchecker نصب می کنیم و خطای نوشتاری کلمات انگلیسی پذیرفته نیست.

۱۳. تا آنجا که می توانید خطاها را هندل کنید. خطا نباید از توابع شما بیرون بیاید مگر اینکه خودتان بخواهید آن را مجددا Raise کنید.

۱۴. در  توابع اگر مقداری برگردانده می شود، یک پارامتر  برای آن در نظر بگیرید و یکبار return شود. تا آنجا که می شود از اینکه چند بار در یک تابع، براساس شرایط return کنید، اجتناب کنید.

۱۵. از syntax زیر استفاده نکنید. نام مشخصه‌ها و مقدار آنها را بیاورید.  
```javascript
<SomeComponent {...{ someProperty, }} \>
```

۱۶. تا آنجا که می توانید توابع را به صورت arrow functions بنویسید.  

۱۷. تا آنجا که می توانید، تایپی را any تعریف نکنید. (اگر پارامتری از جنس یک تابع است، موردی ندارد)

۱۸. فضای خالی بین کدها نباشد (بیش از یک خط)

۱۹. از single quote  استفاده کنید.
    
۲۰. اگر از کدی استفاده نشده است، آن را حذف کنید. کد hint شده در کد نهاییتان نباشد.  

۲۱. اگر تابع دارای return value است. یک پارامتر بگیرید و مقدار آن را تنظیم کنید و در نهایت آن را return کنید. تابع نباید چند عدد return داشته باشد.  









## قوانین استایل‌ها، CSSها و SCSSها

۱. هیچ گونه استایلی در خود فایل jsx به تگ ها و کامپوننت ها داده نمی شود. همگی در فایل sccs مر بوطه نوشته می شوند. در پروژها بدون استثنا از CSS Modules استفاده می کنیم.
   
۲. هیچ گونه رنگی به صورت مستقیم استفاده نمی شود. همگی از دیزاین سیستم و از توکن ها و پارامترها باید استفاده شوند.
   
۳. تا آنجا که می شود برای padding ها و margin ها از پارامترهای تعریف شده در دیزاین سیستم استفاده کنید.
   
۴. حتی الامکان از Grid متریال استفاده نکنید. خودتان Media Query بنویسید. یا از سیستم Grid موجود در CSS استفاده کنید.

۵. در فایل های scss اگر Media Query می نویسید حتما از سایز بزرگ به کوچک بنویسید.

۶. تا آنجا که می توانید از  important کردن استایل ها خودداری کنید.

۷. تا آنجا که می توانید از absolute کردن خودداری کنید. مگر این که چاره ی دیگری نداشته باشید.

۸. استایل عمومی برای یک تگ عمومی تعریف نکنید. حتما استایل دهی محدود شود.




## قوانین نامگذاری شاخه‌ها و فایل‌ها

   
نامگذاری فایل ها و شاخه ها دقیقا مانند داکیومنت مربوط به نامگذاری فایل ها باشد.  


 مواردی که در این داکیومنت نیامده است، در این آدرس قابل دسترسی می باشد:
https://standardjs.com/rules.html


