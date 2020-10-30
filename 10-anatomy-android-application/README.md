Независимо от вашего предыдущего опыта программирования, будь то Windows, macOS, Linux или даже iOS, велики шансы, что разработка под Android будет совершенно непохожа на все, с чем вы сталкивались раньше. Поэтому цель этой главы - дать краткое понимание высокоуровневых концепций, лежащих в основе архитектуры приложений Android. При этом мы рассмотрим как различные компоненты, которые можно использовать для создания приложения, так и механизмы, которые позволяют им работать вместе для создания связного приложения.

## Activities (Активности)
Те, кто знаком с объектно-ориентированными языками программирования, такими как Java, Kotlin, C++ или C #, будут знакомы с концепцией инкапсуляции элементов функциональности приложения в классы, которые затем создаются как объекты и управляются для создания приложения. Поскольку приложения для Android написаны на Java и Kotlin, это по-прежнему актуально. Android также поднимает концепцию повторно используемых компонентов на более высокий уровень. 

Приложения Android создаются путем объединения одного или нескольких компонентов, известных как *Activities*. Активность - это отдельный автономный модуль функциональности приложения, который обычно напрямую связан с одним экраном пользовательского интерфейса и его соответствующими функциями. Например, приложение для учета встреч, может иметь экран активности, на котором отображаются встречи, назначенные на текущий день. Приложение также может использовать вторую активность, состоящую из экрана, на котором пользователь может вводить новые встречи. 

Активности задумывались как полностью повторно используемые и взаимозаменяемые строительные блоки, которые могут использоваться разными приложениями. Например, приложение электронной почты, может содержать активность, специально предназначенную для составления и отправки сообщения электронной почты. Разработчик может писать другое приложение, которое также требует отправки сообщения электронной почты. Вместо того, чтобы разрабатывать активность по составлению сообщения электронной почты специально для нового приложения, разработчик может просто использовать активность из существующего приложения электронной почты.

Активности создаются как подклассы класса *Activity* из Android и должны быть реализованы так, чтобы быть полностью независимыми от других активностей в приложении. Другими словами, совместно используемая активность не может полагаться на то, что её вызывают в известной точке потока программы (поскольку другие приложения могут использовать активность непредвиденным образом), и одна активность не может напрямую вызывать методы или получать доступ к данным экземпляра другой активности. Вместо этого, это достигается с помощью *Intents* (намерений) и *Content Providers*. 

По умолчанию активность не может возвращать результаты той активности, из которой она была вызвана. Если такая функциональность требуется, активность должна быть специально запущена как под-активность исходной активности.

## Fragments (Фрагменты)
Активности, как описано выше, обычно представляют собой отдельный экран пользовательского интерфейса в приложении. Один из вариантов - создавать активность с использованием одного макета пользовательского интерфейса и одного соответствующего файла класса активности. Однако лучшая альтернатива - разбить активность на разные разделы. 

Каждый из таких разделов называется фрагментом, и состоит из части макета пользовательского интерфейса и соответствующего файла класса (объявленного как подкласс класса *Fragment*). В этом сценарии активность просто становится контейнером, в который встроены один или несколько фрагментов. Фактически, фрагменты представляют собой эффективную альтернативу тому, что каждый экран пользовательского интерфейса представлен отдельной активностью. Вместо этого приложение может состоять из одной активности, которая переключается между разными фрагментами, каждый из которых представляет отдельный экран приложения.

## Intents (Намерения | Интенты)
Intents - это механизм, с помощью которого одна активность может запускать другую. Интенты состоят из описания операции, которая должна быть выполнена и данных, над которыми она должна быть выполнена (данные необязательны). 

Интенты могут быть явными, в том смысле, что они запрашивают запуск определенной активности, ссылаясь на нее по имени класса, или неявными, указывая либо тип действия, которое должно быть выполнено, либо предоставляя данные определенного типа, для которых должно быть выполнено действие. В случае неявных интентов, среда Android выберет для запуска ту активность, которая наиболее точно соответствует критериям, указанным в намерении. Этот процесс называется *Intent Resolution*.

## Broadcast Intents (Широковещательные интенты)
Другой тип интентов, широковещательный, является общесистемным интентом, который рассылается всем приложениям, зарегистрировавшим интересующий *Broadcast Receiver* (Broadcast-приемник). Например, система Android, обычно отправляет широковещательные интенты, чтобы указать изменения в состоянии устройства, такие как завершение запуска системы, подключение внешнего источника питания к устройству или включение или выключение экрана. 

## Broadcast Receiver (Широковещательный приемник)
*Broadcast Receiver* - это механизм, с помощью которого приложения могут отвечать на Broadcast-интенты. Broadcast-приемник должен быть зарегистрирован приложением и настроен с помощью *Intent Filter* (фильтра намерений), чтобы указать типы широковещательной передачи, в которых он заинтересован. При совпадающем Broadcast-интенте, приемник будет вызван средой выполнения Android независимо от того, запущено ли приложение, зарегистрировавшее приемник. Затем у получателя есть 5 секунд для выполнения любых требуемых от него задач (таких как запуск службы, обновление данных или отправка уведомления пользователю) перед возвратом. Broadcast-приемники работают в фоновом режиме и не имеют пользовательского интерфейса.

## Services (Сервисы | Службы)
Services - это процессы, которые выполняются в фоновом режиме и не имеют пользовательского интерфейса. Их можно запускать и впоследствии управлять из активностей, Broadcast-приемников или других сервисов. Службы Android идеально подходят для ситуаций, когда приложение должно продолжать выполнять задачи, но не обязательно, чтобы пользовательский интерфейс был видимым для пользователя. Хотя в сервисах отсутствует пользовательский интерфейс, они по-прежнему могут уведомлять пользователя о событиях с помощью уведомлений и всплывающих окон *toasts* (небольшие сообщения, которые появляются на экране, не прерывая видимой в данный момент активности), а также могут выдавать интенты.

Android дает сервисам более высокий приоритет, чем многим другим процессам, и они будут прекращены системой только в крайнем случае, чтобы освободить ресурсы. Однако в случае, если среде выполнения действительно необходимо убить сервис, он будет автоматически перезапущен, как только снова станут доступны соответствующие ресурсы. Сервис может снизить риск завершения, заявив, что он должн работать *foreground*. Это достигается вызовом ```startForeground()```. Это рекомендуется только в ситуациях, когда завершение может нанести ущерб пользовательскому опыту (например, если пользователь слушает аудио, передаваемое сервисом). 

## Content Providers (Поставщик контента)
Content Providers реализуют механизм обмена данными между приложениями. Любое приложение может предоставить другим приложениям доступ к своим базовым данным посредством реализации Content Provider, включая возможность добавлять, удалять и запрашивать данные (при наличии разрешений). Доступ к данным предоставляется через универсальный идентификатор ресурса (URI), определенный поставщиком контента. Данные могут быть переданы в виде файла или всей базы данных SQLite. Собственные приложения Android включают ряд стандартных поставщиков контента, позволяющих приложениям получать доступ к таким данным, как контакты и мультимедийные файлы. Поставщики контента, доступные в настоящее время в системе Android, могут быть обнаружены с помощью *Content Resolver*.

## Application Manifest (Манифест приложения)
Клей, что соединяет вместе различные элементы приложения, является файл манифеста. Именно в этом файле на основе XML, приложение описывает активности, службы, Broadcast-приемники, поставщики данных и *permissions* (разрешения), составляющие полное приложение.

## Application resources (Ресурсы приложения)
Помимо файла манифеста и файлов Dex, содержащих байтовый код, пакет приложения Android также содержит набор файлов ресурсов. Эти файлы содержат ресурсы, такие как: строки, изображения, шрифты и цвета, которые появляются в пользовательском интерфейсе вместе с XML-представлением макетов пользовательского интерфейса. По умолчанию эти файлы хранятся в подкаталоге */res*.

## Application Context (Контекст приложения)
Когда приложение компилируется, создается класс с именем R, содержащий ссылки на ресурсы приложения. Файл манифеста и эти ресурсы объединяются, чтобы создать то, что известно как контекст приложения. Этот контекст, представленный классом Android *Context*, может использоваться в коде приложения для получения доступа к ресурсам приложения во время выполнения. Кроме того, в контексте приложения может быть вызван широкий спектр методов для сбора информации и внесения изменений в среду приложения во время выполнения.