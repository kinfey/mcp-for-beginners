<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "c69f9df7f3215dac8d056020539bac36",
  "translation_date": "2025-07-13T16:34:20+00:00",
  "source_file": "02-Security/README.md",
  "language_code": "ar"
}
-->
# أفضل ممارسات الأمان

اعتماد بروتوكول سياق النموذج (MCP) يضيف قدرات قوية لتطبيقات الذكاء الاصطناعي، لكنه يطرح تحديات أمنية فريدة تتجاوز مخاطر البرمجيات التقليدية. بالإضافة إلى المخاوف المعروفة مثل الترميز الآمن، مبدأ أقل الامتيازات، وأمان سلسلة التوريد، يواجه MCP وأعباء العمل الخاصة بالذكاء الاصطناعي تهديدات جديدة مثل حقن المطالبات، تسميم الأدوات، وتعديل الأدوات الديناميكي. هذه المخاطر قد تؤدي إلى تسريب البيانات، انتهاكات الخصوصية، وسلوك غير مقصود للنظام إذا لم تُدار بشكل صحيح.

تستعرض هذه الدرس أهم المخاطر الأمنية المرتبطة بـ MCP — بما في ذلك المصادقة، التفويض، الأذونات المفرطة، حقن المطالبات غير المباشر، وثغرات سلسلة التوريد — وتقدم ضوابط عملية وأفضل الممارسات للتخفيف منها. ستتعلم أيضًا كيفية الاستفادة من حلول مايكروسوفت مثل Prompt Shields، Azure Content Safety، وGitHub Advanced Security لتعزيز تنفيذ MCP الخاص بك. من خلال فهم وتطبيق هذه الضوابط، يمكنك تقليل احتمالية حدوث خرق أمني بشكل كبير وضمان بقاء أنظمة الذكاء الاصطناعي الخاصة بك قوية وموثوقة.

# أهداف التعلم

بنهاية هذا الدرس، ستكون قادرًا على:

- تحديد وشرح المخاطر الأمنية الفريدة التي يطرحها بروتوكول سياق النموذج (MCP)، بما في ذلك حقن المطالبات، تسميم الأدوات، الأذونات المفرطة، وثغرات سلسلة التوريد.
- وصف وتطبيق ضوابط فعالة للتخفيف من مخاطر أمان MCP، مثل المصادقة القوية، مبدأ أقل الامتيازات، إدارة الرموز الآمنة، والتحقق من سلسلة التوريد.
- فهم والاستفادة من حلول مايكروسوفت مثل Prompt Shields، Azure Content Safety، وGitHub Advanced Security لحماية MCP وأعباء عمل الذكاء الاصطناعي.
- التعرف على أهمية التحقق من بيانات تعريف الأدوات، مراقبة التغييرات الديناميكية، والدفاع ضد هجمات حقن المطالبات غير المباشر.
- دمج أفضل ممارسات الأمان المعروفة — مثل الترميز الآمن، تقوية الخوادم، وهندسة الثقة الصفرية — في تنفيذ MCP الخاص بك لتقليل احتمالية وتأثير الخروقات الأمنية.

# ضوابط أمان MCP

أي نظام لديه وصول إلى موارد مهمة يواجه تحديات أمنية ضمنية. يمكن معالجة هذه التحديات عادةً من خلال التطبيق الصحيح للضوابط والمفاهيم الأمنية الأساسية. نظرًا لأن MCP تم تعريفه حديثًا، فإن المواصفات تتغير بسرعة مع تطور البروتوكول. مع مرور الوقت، ستنضج الضوابط الأمنية داخله، مما يتيح تكاملًا أفضل مع البنى الأمنية المؤسسية والممارسات المثلى المعتمدة.

تشير الأبحاث المنشورة في [تقرير الدفاع الرقمي لمايكروسوفت](https://aka.ms/mddr) إلى أن 98% من الخروقات المبلغ عنها يمكن منعها من خلال ممارسات نظافة أمنية قوية، وأفضل حماية ضد أي نوع من الخروقات هي الحصول على نظافة أمنية أساسية صحيحة، ممارسات الترميز الآمن، وأمان سلسلة التوريد — تلك الممارسات المجربة والمختبرة التي نعرفها لا تزال الأكثر تأثيرًا في تقليل المخاطر الأمنية.

لنلق نظرة على بعض الطرق التي يمكنك من خلالها البدء في معالجة مخاطر الأمان عند اعتماد MCP.

> **ملاحظة:** المعلومات التالية صحيحة حتى **29 مايو 2025**. بروتوكول MCP في تطور مستمر، وقد تقدم الإصدارات المستقبلية أنماط مصادقة وضوابط جديدة. للحصول على أحدث التحديثات والإرشادات، يرجى الرجوع دائمًا إلى [مواصفات MCP](https://spec.modelcontextprotocol.io/) ومستودع [MCP الرسمي على GitHub](https://github.com/modelcontextprotocol) وصفحة [أفضل ممارسات الأمان](https://modelcontextprotocol.io/specification/draft/basic/security_best_practices).

### بيان المشكلة  
افترضت المواصفة الأصلية لـ MCP أن المطورين سيكتبون خادم المصادقة الخاص بهم. هذا تطلب معرفة بـ OAuth والقيود الأمنية المرتبطة به. عملت خوادم MCP كخوادم تفويض OAuth 2.0، تدير المصادقة المطلوبة للمستخدم مباشرةً بدلاً من تفويضها إلى خدمة خارجية مثل Microsoft Entra ID. اعتبارًا من **26 أبريل 2025**، يسمح تحديث لمواصفات MCP لخوادم MCP بتفويض مصادقة المستخدم إلى خدمة خارجية.

### المخاطر
- قد يؤدي منطق التفويض غير المهيأ بشكل صحيح في خادم MCP إلى كشف بيانات حساسة وتطبيق ضوابط وصول خاطئة.
- سرقة رمز OAuth على خادم MCP المحلي. إذا سُرق الرمز، يمكن استخدامه لانتحال هوية خادم MCP والوصول إلى الموارد والبيانات من الخدمة التي ينتمي إليها رمز OAuth.

#### تمرير الرموز
يُحظر تمرير الرموز صراحةً في مواصفات التفويض لأنه يسبب عدة مخاطر أمنية، منها:

#### التهرب من ضوابط الأمان
قد ينفذ خادم MCP أو واجهات برمجة التطبيقات التابعة له ضوابط أمان مهمة مثل تحديد المعدل، التحقق من الطلبات، أو مراقبة الحركة، والتي تعتمد على جمهور الرمز أو قيود الاعتماد الأخرى. إذا تمكن العملاء من الحصول على الرموز واستخدامها مباشرة مع واجهات برمجة التطبيقات التابعة دون تحقق صحيح من خادم MCP أو التأكد من أن الرموز صادرة للخدمة الصحيحة، فإنهم يتجاوزون هذه الضوابط.

#### مشاكل المساءلة ومسار التدقيق
لن يتمكن خادم MCP من التعرف على أو التمييز بين عملاء MCP عندما يتصل العملاء برمز وصول صادر من جهة عليا قد يكون غير واضح لخادم MCP.
قد تظهر سجلات خادم الموارد التابع طلبات تبدو وكأنها صادرة من مصدر مختلف بهوية مختلفة، بدلاً من خادم MCP الذي يقوم فعليًا بتمرير الرموز.
كلا العاملين يجعل التحقيق في الحوادث، الضوابط، والتدقيق أكثر صعوبة.
إذا مرر خادم MCP الرموز دون التحقق من مطالباتها (مثل الأدوار، الامتيازات، أو الجمهور) أو بيانات التعريف الأخرى، يمكن لمهاجم يمتلك رمزًا مسروقًا استخدام الخادم كوكيل لتسريب البيانات.

#### مشاكل حدود الثقة
يمنح خادم الموارد التابع الثقة لكيانات محددة. قد تشمل هذه الثقة افتراضات حول الأصل أو أنماط سلوك العميل. كسر هذه الحدود قد يؤدي إلى مشاكل غير متوقعة.
إذا تم قبول الرمز من قبل خدمات متعددة دون تحقق صحيح، يمكن لمهاجم يخترق خدمة واحدة استخدام الرمز للوصول إلى خدمات أخرى متصلة.

#### مخاطر التوافق المستقبلي
حتى إذا بدأ خادم MCP كـ "وكيل نقي" اليوم، قد يحتاج لاحقًا إلى إضافة ضوابط أمان. البدء بفصل جمهور الرموز بشكل صحيح يسهل تطوير نموذج الأمان.

### ضوابط التخفيف

**يجب ألا تقبل خوادم MCP أي رموز لم تصدر صراحةً لخادم MCP**

- **مراجعة وتقوية منطق التفويض:** قم بتدقيق تنفيذ التفويض في خادم MCP بعناية لضمان وصول المستخدمين والعملاء المقصودين فقط إلى الموارد الحساسة. للإرشادات العملية، راجع [Azure API Management Your Auth Gateway For MCP Servers | Microsoft Community Hub](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690) و[Using Microsoft Entra ID To Authenticate With MCP Servers Via Sessions - Den Delimarsky](https://den.dev/blog/mcp-server-auth-entra-id-session/).
- **فرض ممارسات آمنة للرموز:** اتبع [أفضل ممارسات مايكروسوفت للتحقق من صحة الرموز وعمرها](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens) لمنع سوء استخدام رموز الوصول وتقليل خطر إعادة تشغيل أو سرقة الرموز.
- **حماية تخزين الرموز:** قم دائمًا بتخزين الرموز بأمان واستخدم التشفير لحمايتها أثناء التخزين والنقل. لنصائح التنفيذ، راجع [Use secure token storage and encrypt tokens](https://youtu.be/uRdX37EcCwg?si=6fSChs1G4glwXRy2).

# الأذونات المفرطة لخوادم MCP

### بيان المشكلة
قد تكون خوادم MCP قد مُنحت أذونات مفرطة على الخدمة/المورد الذي تصل إليه. على سبيل المثال، يجب أن يكون لخادم MCP الذي هو جزء من تطبيق مبيعات ذكاء اصطناعي يتصل بمخزن بيانات مؤسسي وصول مقيد ببيانات المبيعات فقط، وليس السماح له بالوصول إلى جميع الملفات في المخزن. بالعودة إلى مبدأ أقل الامتيازات (أحد أقدم مبادئ الأمان)، لا يجب أن يمتلك أي مورد أذونات تتجاوز ما هو مطلوب لتنفيذ المهام المخصصة له. يشكل الذكاء الاصطناعي تحديًا متزايدًا في هذا المجال لأنه من الصعب تحديد الأذونات الدقيقة المطلوبة لتمكينه من المرونة.

### المخاطر  
- منح أذونات مفرطة قد يسمح بتسريب أو تعديل بيانات لم يكن من المفترض أن يصل إليها خادم MCP. قد يكون هذا أيضًا مشكلة خصوصية إذا كانت البيانات معلومات تعريف شخصية (PII).

### ضوابط التخفيف
- **تطبيق مبدأ أقل الامتيازات:** امنح خادم MCP الحد الأدنى فقط من الأذونات اللازمة لأداء مهامه المطلوبة. راجع هذه الأذونات بانتظام وقم بتحديثها لضمان عدم تجاوزها لما هو مطلوب. للإرشادات التفصيلية، راجع [Secure least-privileged access](https://learn.microsoft.com/entra/identity-platform/secure-least-privileged-access).
- **استخدام التحكم في الوصول بناءً على الأدوار (RBAC):** قم بتعيين أدوار لخادم MCP تكون محددة بدقة للموارد والإجراءات المعينة، مع تجنب الأذونات الواسعة أو غير الضرورية.
- **مراقبة وتدقيق الأذونات:** راقب استخدام الأذونات باستمرار وراجع سجلات الوصول لاكتشاف ومعالجة الامتيازات المفرطة أو غير المستخدمة بسرعة.

# هجمات حقن المطالبات غير المباشر

### بيان المشكلة

يمكن لخوادم MCP الخبيثة أو المخترقة أن تسبب مخاطر كبيرة من خلال كشف بيانات العملاء أو تمكين إجراءات غير مقصودة. هذه المخاطر ذات صلة خاصة في أعباء عمل الذكاء الاصطناعي وMCP، حيث:

- **هجمات حقن المطالبات:** يقوم المهاجمون بإدخال تعليمات خبيثة في المطالبات أو المحتوى الخارجي، مما يدفع نظام الذكاء الاصطناعي لأداء إجراءات غير مقصودة أو تسريب بيانات حساسة. للمزيد: [Prompt Injection](https://simonwillison.net/2025/Apr/9/mcp-prompt-injection/)
- **تسميم الأدوات:** يقوم المهاجمون بالتلاعب ببيانات تعريف الأدوات (مثل الأوصاف أو المعلمات) للتأثير على سلوك الذكاء الاصطناعي، مما قد يتجاوز ضوابط الأمان أو يؤدي إلى تسريب البيانات. التفاصيل: [Tool Poisoning](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks)
- **حقن المطالبات عبر المجالات:** يتم تضمين تعليمات خبيثة في مستندات، صفحات ويب، أو رسائل بريد إلكتروني، والتي تتم معالجتها بعد ذلك بواسطة الذكاء الاصطناعي، مما يؤدي إلى تسريب أو تلاعب بالبيانات.
- **تعديل الأدوات الديناميكي (Rug Pulls):** يمكن تغيير تعريفات الأدوات بعد موافقة المستخدم، مما يضيف سلوكيات خبيثة جديدة دون علم المستخدم.

تسلط هذه الثغرات الضوء على الحاجة إلى التحقق الصارم، المراقبة، وضوابط الأمان عند دمج خوادم وأدوات MCP في بيئتك. لمزيد من التفاصيل، راجع المراجع المرتبطة أعلاه.

![prompt-injection-lg-2048x1034](../../../translated_images/prompt-injection.ed9fbfde297ca877c15bc6daa808681cd3c3dc7bf27bbbda342ef1ba5fc4f52d.ar.png)

**حقن المطالبات غير المباشر** (المعروف أيضًا بحقن المطالبات عبر المجالات أو XPIA) هو ثغرة حرجة في أنظمة الذكاء الاصطناعي التوليدية، بما في ذلك تلك التي تستخدم بروتوكول سياق النموذج (MCP). في هذا الهجوم، تُخفى تعليمات خبيثة داخل محتوى خارجي — مثل مستندات، صفحات ويب، أو رسائل بريد إلكتروني. عندما يعالج نظام الذكاء الاصطناعي هذا المحتوى، قد يفسر التعليمات المضمنة كأوامر شرعية من المستخدم، مما يؤدي إلى إجراءات غير مقصودة مثل تسريب البيانات، توليد محتوى ضار، أو التلاعب بتفاعلات المستخدم. لشرح مفصل وأمثلة من الواقع، راجع [Prompt Injection](https://simonwillison.net/2025/Apr/9/mcp-prompt-injection/).

شكل خطير بشكل خاص من هذا الهجوم هو **تسميم الأدوات**. هنا، يقوم المهاجمون بحقن تعليمات خبيثة في بيانات تعريف أدوات MCP (مثل أوصاف الأدوات أو معلماتها). نظرًا لأن نماذج اللغة الكبيرة (LLMs) تعتمد على هذه البيانات لتحديد الأدوات التي يجب استدعاؤها، يمكن للأوصاف المخترقة خداع النموذج لتنفيذ استدعاءات أدوات غير مصرح بها أو تجاوز ضوابط الأمان. غالبًا ما تكون هذه التلاعبات غير مرئية للمستخدمين النهائيين لكنها تُفسر وتُنفذ بواسطة نظام الذكاء الاصطناعي. يزداد هذا الخطر في بيئات خوادم MCP المستضافة، حيث يمكن تحديث تعريفات الأدوات بعد موافقة المستخدم — وهو سيناريو يُعرف أحيانًا بـ "[rug pull](https://www.wiz.io/blog/mcp-security-research-briefing#remote-servers-22)". في مثل هذه الحالات، قد يتم تعديل أداة كانت آمنة سابقًا لأداء أفعال خبيثة، مثل تسريب البيانات أو تغيير سلوك النظام، دون علم المستخدم. للمزيد عن هذا النوع من الهجمات، راجع [Tool Poisoning](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks).

![tool-injection-lg-2048x1239 (1)](../../../translated_images/tool-injection.3b0b4a6b24de6befe7d3afdeae44138ef005881aebcfc84c6f61369ce31e3640.ar.png)

## المخاطر
تقدم الإجراءات غير المقصودة للذكاء الاصطناعي مجموعة متنوعة من المخاطر الأمنية التي تشمل تسريب البيانات وانتهاكات الخصوصية.

### ضوابط التخفيف
### استخدام دروع المطالبات للحماية من هجمات حقن المطالبات غير المباشر
-----------------------------------------------------------------------------

**دروع مطالبات الذكاء الاصطناعي** هي حل طورته مايكروسوفت للدفاع ضد هجمات حقن المطالبات المباشرة وغير المباشرة. تساعد من خلال:

1.  **الكشف والتصفية:** تستخدم دروع المطالبات خوارزميات تعلم آلي متقدمة ومعالجة اللغة الطبيعية لاكتشاف وتصنيف التعليمات الخبيثة المضمنة في المحتوى الخارجي، مثل المستندات، صفحات الويب، أو رسائل البريد الإلكتروني.
    
2.  **التسليط الضوئي:** تساعد هذه التقنية نظام الذكاء الاصطناعي على التمييز بين التعليمات النظامية الصحيحة والمدخلات الخارجية التي قد تكون غير موثوقة. من خلال تحويل نص الإدخال بطريقة تجعله أكثر صلة بالنموذج، يضمن التسليط الضوئي قدرة الذكاء الاصطناعي على التعرف بشكل أفضل على التعليمات الخبيثة وتجاهلها.
    
3.  **الفواصل وعلامات البيانات:** تضمين فواصل في رسالة النظام يحدد بوضوح موقع نص الإدخال، مما يساعد نظام الذكاء الاصطناعي على التعرف وفصل مدخلات المستخدم عن المحتوى الخارجي المحتمل أن يكون ضارًا. تمتد علامات البيانات هذا المفهوم باستخدام علامات خاصة لتسليط الضوء على حدود البيانات الموثوقة وغير الموثوقة.
    
4.  **المراقبة والتحديث المستمر:** تراقب مايكروسوفت باستمرار وتحدث دروع المطالبات لمواجهة التهديدات الجديدة والمتطورة. يضمن هذا النهج الاستباقي بقاء الدفاعات فعالة ضد أحدث تقنيات الهجوم.
    
5. **التكامل مع Azure Content Safety:** تعد دروع المطالبات جزءًا من مجموعة أمان محتوى Azure AI الأوسع، التي توفر أدوات إضافية لاكتشاف محاولات كسر الحماية، المحتوى الضار، ومخاطر الأمان الأخرى في تطبيقات الذكاء الاصطناعي.

يمكنك قراءة المزيد عن دروع مطالبات الذكاء الاصطناعي في [توثيق Prompt Shields](https://learn.microsoft.com/azure/ai-services/content-safety/concepts/jailbreak-detection).

![prompt-shield-lg-2048x1328](../../../translated_images/prompt-shield.ff5b95be76e9c78c6ec0888206a4a6a0a5ab4bb787832a9eceef7a62fe0138d1.ar.png)

### أمان سلسلة التوريد
تظل أمان سلسلة التوريد أمرًا أساسيًا في عصر الذكاء الاصطناعي، لكن نطاق ما يُعتبر جزءًا من سلسلة التوريد الخاصة بك قد توسع. بالإضافة إلى حزم الكود التقليدية، يجب عليك الآن التحقق بدقة ومراقبة جميع المكونات المتعلقة بالذكاء الاصطناعي، بما في ذلك النماذج الأساسية، وخدمات التضمين، ومزودي السياق، وواجهات برمجة التطبيقات الخارجية. كل واحد من هذه يمكن أن يُدخل ثغرات أو مخاطر إذا لم يُدار بشكل صحيح.

**ممارسات أمان سلسلة التوريد الرئيسية للذكاء الاصطناعي وMCP:**
- **التحقق من جميع المكونات قبل الدمج:** يشمل ذلك ليس فقط المكتبات مفتوحة المصدر، بل أيضًا نماذج الذكاء الاصطناعي، ومصادر البيانات، وواجهات برمجة التطبيقات الخارجية. تحقق دائمًا من المصدر، والترخيص، والثغرات المعروفة.
- **الحفاظ على خطوط نشر آمنة:** استخدم خطوط CI/CD مؤتمتة مع فحص أمني مدمج لاكتشاف المشكلات مبكرًا. تأكد من نشر القطع الموثوقة فقط في بيئة الإنتاج.
- **المراقبة والتدقيق المستمر:** نفذ مراقبة مستمرة لجميع التبعيات، بما في ذلك النماذج وخدمات البيانات، لاكتشاف الثغرات الجديدة أو هجمات سلسلة التوريد.
- **تطبيق مبدأ أقل الامتيازات وضوابط الوصول:** قيد الوصول إلى النماذج والبيانات والخدمات فقط لما هو ضروري لعمل خادم MCP الخاص بك.
- **الاستجابة السريعة للتهديدات:** ضع عملية لتصحيح أو استبدال المكونات المخترقة، ولتدوير الأسرار أو بيانات الاعتماد في حال اكتشاف خرق.

يوفر [GitHub Advanced Security](https://github.com/security/advanced-security) ميزات مثل فحص الأسرار، وفحص التبعيات، وتحليل CodeQL. تتكامل هذه الأدوات مع [Azure DevOps](https://azure.microsoft.com/en-us/products/devops) و[Azure Repos](https://azure.microsoft.com/en-us/products/devops/repos/) لمساعدة الفرق على تحديد وتخفيف الثغرات عبر كل من الكود ومكونات سلسلة توريد الذكاء الاصطناعي.

تطبق مايكروسوفت أيضًا ممارسات أمان شاملة لسلسلة التوريد داخليًا لجميع المنتجات. تعرف على المزيد في [الرحلة نحو تأمين سلسلة توريد البرمجيات في مايكروسوفت](https://devblogs.microsoft.com/engineering-at-microsoft/the-journey-to-secure-the-software-supply-chain-at-microsoft/).


# أفضل ممارسات الأمان المعتمدة التي سترتقي بمستوى أمان تنفيذ MCP الخاص بك

يرث أي تنفيذ لـ MCP الوضع الأمني الحالي لبيئة مؤسستك التي بُني عليها، لذا عند النظر في أمان MCP كجزء من أنظمة الذكاء الاصطناعي الشاملة لديك، يُنصح بالعمل على رفع مستوى الوضع الأمني العام القائم. الضوابط الأمنية المعتمدة التالية ذات صلة خاصة:

-   أفضل ممارسات البرمجة الآمنة في تطبيق الذكاء الاصطناعي الخاص بك - الحماية من [OWASP Top 10](https://owasp.org/www-project-top-ten/)، و[OWASP Top 10 للنماذج اللغوية الكبيرة](https://genai.owasp.org/download/43299/?tmstv=1731900559)، استخدام خزائن آمنة للأسرار والرموز، تنفيذ اتصالات آمنة من النهاية إلى النهاية بين جميع مكونات التطبيق، وغيرها.
-   تقوية الخادم - استخدم المصادقة متعددة العوامل حيثما أمكن، حافظ على تحديث التصحيحات، دمج الخادم مع مزود هوية خارجي للوصول، وهكذا.
-   حافظ على تحديث الأجهزة والبنية التحتية والتطبيقات بالتصحيحات.
-   مراقبة الأمان - تنفيذ تسجيل ومراقبة لتطبيق الذكاء الاصطناعي (بما في ذلك عميل/خوادم MCP) وإرسال هذه السجلات إلى نظام SIEM مركزي لاكتشاف الأنشطة الشاذة.
-   بنية الثقة الصفرية - عزل المكونات عبر ضوابط الشبكة والهوية بطريقة منطقية لتقليل الحركة الجانبية في حال تم اختراق تطبيق الذكاء الاصطناعي.

# النقاط الرئيسية

- تظل أساسيات الأمان حاسمة: البرمجة الآمنة، مبدأ أقل الامتيازات، التحقق من سلسلة التوريد، والمراقبة المستمرة ضرورية لأعباء عمل MCP والذكاء الاصطناعي.
- يقدم MCP مخاطر جديدة مثل حقن المطالبات، تسميم الأدوات، والصلاحيات المفرطة التي تتطلب ضوابط تقليدية وخاصة بالذكاء الاصطناعي.
- استخدم ممارسات قوية للمصادقة، والتفويض، وإدارة الرموز، مستفيدًا من مزودي الهوية الخارجيين مثل Microsoft Entra ID حيثما أمكن.
- احمِ نفسك من حقن المطالبات غير المباشر وتسميم الأدوات من خلال التحقق من بيانات تعريف الأدوات، والمراقبة للتغييرات الديناميكية، واستخدام حلول مثل Microsoft Prompt Shields.
- عامل جميع مكونات سلسلة توريد الذكاء الاصطناعي الخاصة بك — بما في ذلك النماذج، والتضمينات، ومزودي السياق — بنفس الصرامة التي تعامل بها تبعيات الكود.
- تابع تحديثات مواصفات MCP وشارك في المجتمع للمساعدة في تشكيل معايير أمان قوية.

# موارد إضافية

- [Microsoft Digital Defense Report](https://aka.ms/mddr)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [حقن المطالبات في MCP (Simon Willison)](https://simonwillison.net/2025/Apr/9/mcp-prompt-injection/)
- [هجمات تسميم الأدوات (Invariant Labs)](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks)
- [عمليات الاحتيال في MCP (Wiz Security)](https://www.wiz.io/blog/mcp-security-research-briefing#remote-servers-22)
- [توثيق Prompt Shields (مايكروسوفت)](https://learn.microsoft.com/azure/ai-services/content-safety/concepts/jailbreak-detection)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Top 10 للنماذج اللغوية الكبيرة](https://genai.owasp.org/download/43299/?tmstv=1731900559)
- [GitHub Advanced Security](https://github.com/security/advanced-security)
- [Azure DevOps](https://azure.microsoft.com/products/devops)
- [Azure Repos](https://azure.microsoft.com/products/devops/repos/)
- [الرحلة نحو تأمين سلسلة توريد البرمجيات في مايكروسوفت](https://devblogs.microsoft.com/engineering-at-microsoft/the-journey-to-secure-the-software-supply-chain-at-microsoft/)
- [الوصول الآمن بأقل امتيازات (مايكروسوفت)](https://learn.microsoft.com/entra/identity-platform/secure-least-privileged-access)
- [أفضل الممارسات للتحقق من صحة الرموز وفترة صلاحيتها](https://learn.microsoft.com/entra/identity-platform/access-tokens)
- [استخدام تخزين رموز آمن وتشفير الرموز (يوتيوب)](https://youtu.be/uRdX37EcCwg?si=6fSChs1G4glwXRy2)
- [إدارة واجهات برمجة التطبيقات في Azure كبوابة مصادقة لـ MCP](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)
- [أفضل ممارسات أمان MCP](https://modelcontextprotocol.io/specification/draft/basic/security_best_practices)
- [استخدام Microsoft Entra ID للمصادقة مع خوادم MCP](https://den.dev/blog/mcp-server-auth-entra-id-session/)

### التالي

التالي: [الفصل 3: البدء](../03-GettingStarted/README.md)

**إخلاء المسؤولية**:  
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الموثوق به. للمعلومات الهامة، يُنصح بالترجمة البشرية المهنية. نحن غير مسؤولين عن أي سوء فهم أو تفسير ناتج عن استخدام هذه الترجمة.