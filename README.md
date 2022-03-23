# -
وب سرویس لحظه ای بورس - API JSON - جهت استفاده برنامه نویسان

مستندات استفاده از وب سرویس لحظه ای آژیر365

مستندات API زیر تنها برای Version 1 وب سرویس آژیر365 صدق می کند.

کاربران با خرید سرویس، باید از استانداردهای این بخش اقدام به بهره برداری سرویس در پروژه های خود نمایند.
API لحظه ای بورس چه چیزی را در اختیار برنامه نویس قرار می دهد؟

در این سرویس 11 فاکتور حین معاملاتی در تابلوی عمومی بورس به همراه تغییرات شاخص کل، بدون هیچگونه تجزیه و تحلیل های اضافه، بصورت زنده و کاملأ خام از طریق JSON API به کاربران ارائه می شود.
ثابت های API لحظه ای بورس آژیر365:
نام 	ویژگی 	فراخوانی
case 	فراخوانی متد case 	اختیاری
type 	تعیین نوع صفت 	اختیاری
token 	توکن خصوصی دریافتی 	الزامی
name 	نام نماد به فارسی 	الزامی

نکته 1: حداقل یکی از ثابت های case یا type باید به همراه token و name فراخوانی شوند.

نکته 2: نمادها باید به زبان فارسی در متد name فراخوانی شوند. به عنوان مثال برای نماد فملی، به صورت زیر است:

&name=یلمف

لیست تمام صفات type:
ثابت ها نام 	متعلق به ثابت 	ویژگی 	نوع 	مثال 	ورژن API
all 	type 	نمایش تمام عناصر نماد 	صفت 	?type=all 	version 1
buy_price 	type 	قیمت خرید 	صفت 	?type=buy_price 	version 1
sell_price 	type 	قیمت فروش 	صفت 	?type=sell_price 	version 1
close_price 	type 	قیمت پایانی 	صفت 	?type=close_price 	version 1
first_price 	type 	اولین قیمت معامله 	صفت 	?type=first_price 	version 1
yesterday_price 	type 	قیمت دیروز 	صفت 	?type=yesterday_price 	version 1
low_price 	type 	کمترین قیمت معامله شده روز 	صفت 	?type=low_price 	version 1
high_price 	type 	بیشترین قیمت معامله شده روز 	صفت 	?type=high_price 	version 1
number_taders 	type 	تعداد معاملات 	صفت 	?type=number_taders 	version 1
volume_taders 	type 	حجم معاملات 	صفت 	?type=volume_taders 	version 1
value_taders 	type 	ارزش معاملات 	صفت 	?type=value_taders 	version 1
last_day_trade_gregorian 	type 	آخرین روز معاملاتی (میلادی) 	صفت 	?type=last_day_trade_gregorian 	version 1
last_azhir365_update 	type 	آخرین بروزرسانی API 	صفت 	?type=last_azhir365_update 	version 1
last_tse_update 	type 	آخرین بروزرسانی در تابلو عمومی 	صفت 	?type=last_tse_update 	version 1
متد y :

گاهی لازم است ما هر صفت را بصورت یک Json مجزا داشته باشیم. با کمک متد Y این کار میسر است. در متد y شیوه معکوسی دنبال میشود.نحوه کار این متد به این صورت است که صفت های اصلی را به عنوان عنصر در نظر گرفته و به آنها صفت ثابت y را می دهیم. همچنین این متد در روشی دیگر که در ادامه ذکر خواهد شد، می تواند به کمک متد case بیاید.
نام 	صفت 	ویژگی 	نوع 	مثال 	ورژن API
buy_price 	y 	قیمت خرید 	عنصر 	?buy_price=y 	version 1
sell_price 	y 	قیمت فروش 	عنصر 	?sell_price=y 	version 1
close_price 	y 	قیمت پایانی 	عنصر 	?close_price=y 	version 1
first_price 	y 	اولین قیمت معامله 	عنصر 	?first_price=y 	version 1
yesterday_price 	y 	قیمت دیروز 	عنصر 	?yesterday_price=y 	version 1
low_price 	y 	کمترین قیمت معامله شده روز 	عنصر 	?low_price=y 	version 1
high_price 	y 	بیشترین قیمت معامله شده روز 	عنصر 	?high_price=y 	version 1
number_taders 	y 	تعداد معاملات 	عنصر 	?number_taders=y 	version 1
volume_taders 	y 	حجم معاملات 	عنصر 	?volume_taders=y 	version 1
value_taders 	y 	ارزش معاملات 	عنصر 	?value_taders=y 	version 1
last_day_trade_gregorian 	y 	آخرین روز معاملاتی (میلادی) 	عنصر 	?last_day_trade_gregorian=y 	version 1
last_azhir365_update 	y 	آخرین بروزرسانی API 	عنصر 	?last_azhir365_update=y 	version 1
last_tse_update 	y 	آخرین بروزرسانی در تابلو عمومی 	عنصر 	?last_tse_update=y 	version 1
متد case :

از متد case صرفأ برای انتخاب موردی هر کدام از صفات نماد استفاده می شود. متد case به تنهایی پاسخی نمی دهد و نیاز به حداقل یک عنصر از متد y دارد. پاسخ سرور به این درخواست، یک json می باشد. یعنی به عنوان مثال اگر درخواست کننده در طی یک درخواست، تقاضای حجم معاملات، ارزش معاملات را باهم دارد. و بنا دارد خروجی در یک json قرار بگیرد (دقیقأ برعکس متد y) متد case را با صفت ثابت w فراخوانی می کند.
نام 	صفت 	توضیح 	نوع 	مثال 	ورژن API
case 	w 	صفات انتخابی در یک json 	ثابت 	?case=w 	version 1

اطلاعات زیر در خصوص هر نماد، به صورت JSON از API لحظه ای بورس قابل درخواست است: قیمت خرید، قیمت فروش، قیمت پایانی، حجم معاملات، تعداد معاملات ، ارزش معاملات ، قیمت روز قبل ، کمترین قیمت روز ، بیشترین قیمت روز ، آخرین روز معامله سهم ، آخرین ساعت معامله سهم و وضعیت سهم.
تمامی مثال ها:	

در اینجا به عنوان مثال درخواست تمام عناصر تابلوی نماد آ س پ را کرده ایم.
درخواست:

https://api.azhir365.com/v1/bourse/?token=e193b1613082a46116b95f4e12b6cedd&type=all&name=پ س آ

مثال خروجی:

{
"symbol":"\u0622 \u0633 \u067e",
"buy_price":"4377",
"sell_price":"5288",
"close_price":"5491",
"first_price":"5844",
"low_price":"5844",
"high_price":"5288",
"yesterday_price":"5566",
"number_trades":"1356",
"volume_trades":"23456652",
"value_trades":"128802196116",
"last_day_trade_gregorian":"20220316",
"last_azhir365_update":"05:00:02",
"last_tse_update":"12:29:56",
"time":"2022\/3\/17 - 05\/00\/54",
"copyright":"www.azhir365.com"
}

در اینجا به عنوان مثال درخواست (فقط) قیمت پایانی نماد ثشاهد را کرده ایم.
درخواست:

https://api.azhir365.com/v1/bourse/?token=e193b1613082a46116b95f4e12b6cedd&type=close_price&name=دهاشث

مثال خروجی:

{
"close_price":"7260"
}

مثال برای متد y :

گاهی لازم است فقط چند عنصر خاص را در یک درخواست خروجی بگیریم. به طوری که هر صفت از سهم در یک json مجزا قرار بگیرد. در مثال زیر به عنوان مثال 2 خروجی را در نظر می گیریم.

در اینجا به عنوان مثال درخواست قیمت خرید و قیمت فروش نماد ثشاهد را با کمک متد y کرده ایم. همانگونه که می بینید خروجی دو json مجزاست.
درخواست:

https://api.azhir365.com/v1/bourse/?token=e193b1613082a46116b95f4e12b6cedd&buy_price=y&sell_price=y&name=دهاشث

مثال خروجی:

{"buy_price":"7240"}{"close_price":"7260"}

مثال برای متد case :

متد case تمام عناصر انتخابی متد y را در یک json تجمیع می کند. به عنوان مثال در اینجا می خواهیم  قیمت پایانی ، قیمت فروش و حجم خرید سهم های وب را باهم در یک json قرار بدهیم.
درخواست:

https://api.azhir365.com/v1/bourse/?token=e193b1613082a46116b95f4e12b6cedd&case=w&close_price=y&sell_price=y&volume_trades=y&name=بو یاه

مثال خروجی:

{
"sell_price":"6590",
"close_price":"6550",
"volume_trades":"7907722"
}
