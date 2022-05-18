# VentilationControlHVAC
Графическая формочка управления щитом общеобменной приточно-вытяжной установки (далее по тексту щитом)
----
Объемы доработок (вступительная часть):
 - сделать на формочке выбор адреса щита в сети **ModBUS-TCP**,
 - эта формочка ведущая, все щиты - ведомые,
 - вставить скрипты-обработчики нажатия кнопок,
 - написать обработчики,
 - внизу подписать названия каналов и названия режимов,
 - сделать из режимов группу, чтобы выбирался только один из них,
 - делать неактивными виджеты (адрес, прочитать/записать настройки), которые не могут отдавать команду на установку, когда она в работе,
 - читать и писать настройки из внешнего **SQL Server**-а по адресу установки,
 - сделать автопрогон настроек регулятора, чтение их с контроллера в формочку как оптимальных и их запись в базу на SQL Server-е,
 - переписать расчет переходного процесса (см. в отдельный проект) как отдельного клиента с C++ на Python

----
Примечания:
 - Нужны **DDK** и **SDK** фирмы-изготовителя контроллера HVAC
 - **OPC-сервер** ставится поверх **SCADA**, которая ставится на **Windows Server** с 4-м **.Net FrameWork**-ом, с **IIS** и вместе с **SQL Express** (но лучше полноценный внешний **SQL Server**) и которая не приобретается и не применяется
 
