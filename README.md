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

1. تمامی import ها باید به صورت نزولی مرتب شوند (از لحاظ طول خط)  
   مثال:  
```javascript 
   import Link from 'next/link';  
   import { useTranslations, } from 'next-intl';  
   import Typography from '@mui/material/Typography';  
   import Panel from '@/modules/general/components/panel';  
   import NewsColoredIcon from '@/modules/general/components/icons/news-colored';  
   import ArrowBackIosRoundedIcon from '@mui/icons-material/ArrowBackIosRounded';
```
     
2. وقتی import ها دویا چند خطی می شوند به انتهای فهرست import منتقل شوند.  
```javascript
   import Link from 'next/link';  
   import { useTranslations, } from 'next-intl';  
   import Typography from '@mui/material/Typography';  
   import Panel from '@/modules/general/components/panel';  
   import {  
     useEffect, useRef, useState,  
   } from 'react';
```
3. وقتی چند متغیر تعریف می کنید، برای همگی یک const یا یک let بگذارید. برای هر متغیر یک const لازم نیست و هر مورد را هم در یک خط جداگانه بنویسید.

```javascript
const  
    t = useTranslations(),  
    screenSize = useMediaQuery('(max-width:1100px)', { noSsr: false, }),  
    categoryId = useSearchParams().get('categoryId');
```

4. اگر یک تایپ داریم که فقط در همین کامپوننت استفاده می شود، لازم نیست آن را جداگانه تعریف کنید و نام جداگانه‌ای برای آن بگذارید. به صورت In Place در همان فایل، جزییات را بیاورید.
5. اگر بیش از یک پارامتر داریم، هر کدام را در یک خط جداگانه بیاورید.
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
6. اگر از ternary operator در jsx استفاده می کنید حتما content را داخل یک پرانتز بگذارید. این مورد برای && هم صدق می کند.

```javascript
   {screenSize && (  
                   <MyComponent  
                     id={1}  
                     title={‘title’}  
                   />  
                 )}
```
7. در یک کامپوننت اگر بیش از یک attribute داریم هنگام استفاده هر کدام در یک خط نوشته شوند (مثال بالا)

8. از نوشتن متن توابع به صورت InPlace خودداری کنید. برای مثال کد زیر استاندارد نیست. یک تابع تعریف کرده و به آن ارجاع دهید.
```javascript
onClick={() => toggleDrawer(false)}
```
9. به هیچ عنوان ternary operator تو در تو استفاده نمی کنیم.
10. محتویات یک Tag یا کامپوننت را در jsx، حتما در یک خط جدید بیاورید.
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
1. نام توابع را خلاصه نکنید. اسم کامل عملکرد را در نام تابع بیاورید. از بلند شدن نام تابع و فایل ها نترسید. (برای مثال از Calc استفاده نکنید از کل کلمه Calculate استفاده شود)  
   
2. اسامی توابع به صورت camelCase نوشته می‌شوند.
   
3.  برای تمامی event ها از کلمه‌ی handle در ابتدای تابع استفاده می کنیم. برای مثال handleUsernameChange

4. اسامی enum ها همگی به صورت UPPER CASE نوشته می‌شوند.
```javascript
const COLOR = {
  Red: "red",
  Blue: "blue",
  Green: "green",
}
```
5.اسامی پارامترها به صورت camelCase نوشته می شوند.

6. اسامی ثابت‌ها به صورت PascalCase است.

7. اسم کامپوننت‌ها PascalCase است.

8. برای ساختن رشته های پیچیده، همیشه از string format استفاده کنید و از + استفاده نکنید.  
   
9.  از Semicolon استفاده کنید. حذف آنها امتیاز ویژه‌ای ندارد. البته linter این مورد را تا حد زیادی کنترل می کند.
    
10.  کامنت فارسی نمی‌نویسیم.
    
11.  همه ی پارامترها باید معنی دار هستند.
    
12.  حتما Spellchecker نصب می کنیم و خطای نوشتاری کلمات انگلیسی پذیرفته نیست.

13.  تا آنجا که می توانید خطاها را هندل کنید. خطا نباید از توابع شما بیرون بیاید مگر اینکه خودتان بخواهید آن را مجددا Raise کنید.

14.  در توابع اگر مقداری برگردانده می شود، یک پارامتر  برای آن در نظر بگیرید و یکبار return شود. تا آنجا که می شود از اینکه چند بار در یک تابع، براساس شرایط return کنید، اجتناب کنید.

15.  از syntax زیر استفاده نکنید. نام مشخصه‌ها و مقدار آنها را بیاورید.  
```javascript
<SomeComponent {...{ someProperty, }} \>
```

16. تا آنجا که می توانید توابع را به صورت arrow functions بنویسید.  


17. تا آنجا که می توانید، تایپی را any تعریف نکنید. (اگر پارامتری از جنس یک تابع است، موردی ندارد)

18. فضای خالی بین کدها نباشد (بیش از یک خط)

19. ترجیحا از single quote  استفاده کنید.
    
20. اگر از کدی استفاده نشده است، آن را حذف کنید. کد hint شده در کد نهاییتان نباشد.  








## قوانین استایل‌ها، CSSها و SCSSها

1. هیچ گونه استایلی در خود فایل jsx به تگ ها و کامپوننت ها داده نمی شود. همگی در فایل sccs مر بوطه نوشته می شوند. در پروژها بدون استثنا از CSS Modules استفاده می کنیم.
   
2. هیچ گونه رنگی به صورت مستقیم استفاده نمی شود. همگی از دیزاین سیستم و از توکن ها و پارامترها باید استفاده شوند.
   
3. تا آنجا که می شود برای padding ها و margin ها از پارامترهای تعریف شده در دیزاین سیستم استفاده کنید.
   
4. حتی الامکان از Grid متریال استفاده نکنید. خودتان Media Query بنویسید. یا از سیستم Grid موجود در CSS استفاده کنید.

5. در فایل های scss اگر Media Query می نویسید حتما از سایز بزرگ به کوچک بنویسید.

6. تا آنجا که می توانید از  important کردن استایل ها خودداری کنید.

7. تا آنجا که می توانید از absolute کردن خودداری کنید. مگر این که چاره ی دیگری نداشته باشید.




## قوانین نامگذاری شاخه‌ها و فایل‌ها

   
نامگذاری فایل ها و شاخه ها دقیقا مانند داکیومنت مربوط به نامگذاری فایل ها باشد.  


