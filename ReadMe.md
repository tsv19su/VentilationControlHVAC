# VentilationControlHVAC

----
#### Назначение
Графические оболочки в виде диалоговых форм (далее по тексту оболочки) управления щитами общеобменных приточно-вытяжных установок **HVAC** (далее по тексту щитами) применяются для дистанционного управления в супервизорном режиме внешних контуров каскадных схем управления аппаратурой **SIEMENS**, **Schneider Electric** с 1999-го года.

Оболочка: 
 - дает команду на автопрогон настроек регулятора внутреннего контура,
 - считывает настройки регуляторов,
 - выдает настройки на регуляторы,
 - выдает задание на регулирование,
 - включает и отключает работу щита.

Регуляторы щитов программные на контроллере щита.
Для управления каждым щитом открывается своя оболочка, на которой вводятся параметры работы.

----
#### Замечания:
 - Сделать на оболочке выбор адреса щита в сети **ModBUS-TCP** (используемых адресов щитов не должно быть в списке доступных),
 - Дописать серверную компоненту (далее по тексту компоненту) опроса щитов по их адресам и раздаче опрошенных данных на формочки по их запросам, индикатор которой вывести например в индикаторы на панели задач,
 - Компонента ведущая (опрашивает), все щиты - ведомые (отвечают на запросы),
 - Вставить на оболочке скрипты-обработчики нажатия кнопок,
 - Внизу подписать на оболочке названия каналов и названия режимов,
 - Сделать из режимов группу, чтобы выбирался только один из них,
 - Делать неактивными виджеты (адрес щита, прочитать/записать настройки щита), которые не могут отдавать команду на щит, когда он в работе,
 - Читать и писать настройки из внешнего **SQL Server**-а по адресу щита в сети **ModBUS-TCP**,
 - Сделать автопрогон настроек регулятора щита, считать их с контроллера в формочку как оптимальных и записать их в базу на внешнем SQL Server-е,
 - Использовать настройки регуляторов щитов, полученные по результатам расчета замкнутой системы регулирования (см. отдельный проект),
 - Переписать расчет переходного процесса замкнутой системы регулирования (см. в отдельный проект) как отдельного клиента с C++ на Python

![IMG_20160928_152215](https://user-images.githubusercontent.com/104857185/169311708-07b7b03a-a0fc-4fd0-a122-0f73b721b21e.jpg)
![IMG_4704](https://user-images.githubusercontent.com/104857185/169308673-81a780ba-8a2d-46db-ab37-a9f41d53fa34.JPG)
![IMG_4486](https://user-images.githubusercontent.com/104857185/169309000-4f485313-a44b-4f15-818e-b0a76adfc1ff.JPG)
![IMG_4547](https://user-images.githubusercontent.com/104857185/169310149-21e65ddf-7baa-45be-a14c-aa3a2d774197.JPG)
![IMG_4778](https://user-images.githubusercontent.com/104857185/169310532-a605a20f-8389-42ef-9c34-928f5b01c33a.JPG)
![IMG_4793](https://user-images.githubusercontent.com/104857185/169310808-5151ae47-95cf-4c17-8756-ea7f3cd65ec5.JPG)
![IMG_3174](https://user-images.githubusercontent.com/104857185/170977221-276454ab-5e53-4747-8108-c8fcff0e6f48.JPG)
![IMG_3176](https://user-images.githubusercontent.com/104857185/170977297-a0bd49e5-281f-4405-9636-5aa8f5c7a8ed.JPG)


#### Примечания:
 - Нужны новые **DDK** и **SDK** фирмы-изготовителя контроллеров HVAC (имеющиеся в наличии работают со старыми моделями аппаратуры), применяемых в щитах.
 - В перспективе переделать с **tk** на **Qt**.
 - В случае использования SCADA-системы фирмы-изготовителя аппаратуры **OPC-сервер** ставится дополнительно поверх нее. Для полноценного функционирования SCADA-систему ставить на **Windows Server** с 4-м **.Net FrameWork**-ом, с **IIS**, с **SQL Express** (после установки зайти в настройки и переподключиться на внешний **SQL Server**). Функционал **OPC-сервер**-а разрешается в USB-вом ключе по дополнительному договору за ежегодную дополнительную оплату фирме-изготовителю.
 - Пользователи работают с программным обеспечением в оригинале с файлового сервера, которое дорабатывается в процессе работы без уведомления его пользователей (в части CI/CD).

Наработки аналогичные SCADA-системе **Desigo Insight** фирмы SIEMENS в том числе:
 * **ИПК Индустрия** (г. Мытищи) см. [статью на facebook-е](https://www.facebook.com/ipkindustriya/)
 * **Симпл-Скада** (г. Краснодар) см. [их сайт](https://simple-scada.com/)
 * **Симп Лайт** (г. Нижний Тагил) см. [их сайт](https://simplight.ru/)
 * **НПФ Круг** (г. Пенза) см. [их сайт](https://www.krug2000.ru/products/ppr/scada-2000.html?utm_medium=cpc&utm_source=mail.yandex.ru&utm_campaign=15353707&utm_term=%D0%BA%D1%83%D0%BF%D0%B8%D1%82%D1%8C%20scada&utm_content=none.0&yclid=2892848951052795745)
 * **IECON** (г. Москва) см. [их сайт](https://www.iecon.ru/about/)
 * **Factory Manager** (г. Омск) см. [их сайт](https://factorymanager.ru/)
 * **АСУ-Технология** (г. Москва) см. [их сайт](https://www.asu-tech.ru/about/dispetcherizaciya.html)
 * **MasterSCADA** (г. Москва) см. [их сайт](https://masterscada.ru/?yclid=2966471923235094160#pos)
 * https://github.com/frangoteam/FUXA

#### Ссылочная литература
Каталоги 1998-го (остался только в печатном виде), 2002-го и 2005-го годов на сервере в папках:
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Synco HVAC`
 - `P:\Техническая информация\Электротехника и КИПиА\Schneider Electric` 

Техническая документация по SCADA-системам фирмы-изготорителя на сервере в папках:
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Desigo Insight`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Desigo CC`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Cerberus Pro`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\DMS8000`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\SCADA Win CC`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\SiPass`
