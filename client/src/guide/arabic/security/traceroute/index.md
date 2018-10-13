---
title: Traceroute
localeTitle: متتبع
---
**جدول المحتويات**

*   [متتبع](#traceroute)
*   [كيف تنتقل البيانات عبر الإنترنت](#how-data-travels-across-the-internet)
*   [بعض الأمثلة على الاستخدام](#some-examples-for-usage)
*   [معلومات اكثر](#more-information)

## متتبع

Traceroute هو أداة تشخيصية لشبكة الكمبيوتر لعرض المسار (المسار) وقياس التأخيرات العابرة للحزم عبر شبكة بروتوكول الإنترنت (IP). يتم تسجيل تاريخ المسار كأوقات ذهاب وإياب للحزم المستلمة من كل مضيف متتابع (عقدة بعيدة) في المسار (المسار) ؛ مجموع المرات الزمنية في كل قفزة هو قياس إجمالي الوقت المستغرق في تأسيس الاتصال. تستمر عملية traceroute ما لم يتم فقدان جميع الحزم المرسلة (ثلاثة) أكثر من مرتين ، ثم يتم فقد الاتصال ولا يمكن تقييم المسار. بينج ، من ناحية أخرى ، فقط يحسب أوقات ذهاب وإياب النهائي من نقطة الوجهة.

#### كيف تنتقل البيانات عبر الإنترنت

يتم تعريف كل جهاز كمبيوتر في traceroute بواسطة عنوان IP الخاص به ، وهو الرقم المكون من تسعة أرقام المفصولة بنقاط يحدد اتصال شبكة الاتصال الفريد للكمبيوتر. فيما يلي بعض التفاصيل المتعلقة بتتبع المسار:

 `- The journey from one computer to another is known as a hop. 
 - The amount of time it takes to make a hop is measured in milliseconds. 
 - The information that travels along the traceroute is known as a packet. 
` 

عادةً ما تعرض قراءات traceroute ثلاثة أعمدة منفصلة لوقت القفزة ، حيث يرسل كل traceroute ثلاثة حزم منفصلة للمعلومات لكل كمبيوتر. في الجزء العلوي من القائمة ، سيعطي traceroute حد عدد خطوط القفزات التي سيعرضها — 30 قفزة هو غالباً العدد الأقصى.

عندما يواجه traceroute صعوبة في الوصول إلى جهاز كمبيوتر ، سيعرض الرسالة "انقضاء مهلة الطلب". سيعرض كل عمود من الأعمدة النجمة بدلاً من عدد الميلي ثانية.

#### بعض الأمثلة على الاستخدام

تتضمن معظم التطبيقات خيارات على الأقل لتحديد عدد الاستعلامات لإرسال كل مرحلة ، ووقت انتظار استجابة ، والحد الأقصى لمنفذ الاستخدام والمنفذ المراد استخدامه. يؤدي استدعاء traceroute بدون خيارات محددة إلى عرض قائمة الخيارات المتاحة ، بينما يعرض traceroute للإنسان المزيد من التفاصيل ، بما في ذلك إشارات الخطأ المعروضة. مثال بسيط على Linux:

 `[root@example ~]#  traceroute -w 3 -q 1 -m 16 www.google.com 
 traceroute to www.google.com (216.58.200.36), 16 hops max, 60 byte packets 
 1  192.168.4.2 (192.168.4.2)  0.136 ms 
 2  * 
 3  * 
 4  * 
 5  * 
 6  * 
 7  * 
 8  * 
 9  * 
 10  * 
 11  * 
 12  * 
 13  * 
 14  * 
 15  * 
 16  * 
` 

في المثال أعلاه ، فإن الخيارات المحددة هي الانتظار لمدة ثلاث ثوانٍ (بدلاً من خمسة) ، وإرسال طلب بحث واحد فقط لكل قفزة (بدلاً من ثلاثة) ، والحد من الحد الأقصى لعدد القفزات إلى 16 قبل الاستسلام (بدلاً من 30) ، مع www.google.com كمضيف نهائي.

يمكن أن يساعد ذلك في تحديد تعريفات جدول التوجيه غير الصحيح أو جدران الحماية التي قد تمنع حركة مرور ICMP أو UDP عالي المنفذ في Unix ping ، إلى موقع. لاحظ أن جدار الحماية قد يسمح بحزم ICMP ولكن لا يسمح بحزم البروتوكولات الأخرى.

كما يتم استخدام traceroute بواسطة مختبري الاختراق لجمع معلومات حول البنية الأساسية للشبكة ونطاقات IP حول مضيف معين.

ويمكن أيضًا استخدامه عند تنزيل البيانات ، وإذا كانت هناك مرايا متعددة متوفرة لنفس قطعة البيانات ، فيمكن للمرء تتبع كل مرآة للحصول على فكرة جيدة عن أي مرآة ستكون الأسرع في الاستخدام.

#### معلومات اكثر

اقرأ على مزيد من المعلومات حول Traceroute:

*   [كيفية استخدام TRACERT في ويندوز](https://support.microsoft.com/en-us/help/314868/how-to-use-tracert-to-troubleshoot-tcp-ip-problems-in-windows) - [كيفية استخدام TRACERT في لينكس](https://www.lifewire.com/traceroute-linux-command-4092586)