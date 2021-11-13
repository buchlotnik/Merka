# Мерка
небольшая надстройка, предназначенная для оценки скорости выполнения запросов PQ в среде MS Excel
## Системные требования
- Excel 2016 и новее (по отзывам работает также и 2013, с точки зрения кода - работать будет и в 2010, но непосредственное тестирование автором не проводилось)
- Разрешённые макросы

## Установка
Приложение поставляется в виде единственного файла **Мерка_версия.xlam**

Надстройку можно добавить одним из способов:
- Использовать стандартный путь **Файл - Параметры - Надстройки - Надстройки Excel - Перейти... - Обзор** - и выбрать расположение файла
- Поместить файл в директорию с надстройками **C:\Users\User\AppData\Roaming\Microsoft\AddIns** - догда Мерка появится в списке доступных надстроек
- Поместить файл (или его ярлык) в папку **C:\Users\Михаил\AppData\Roaming\Microsoft\Excel\XLSTART** - в этом случае надстройка будет запускаться в автоматическом режиме при запуске Excel

После установки вам станут доступны:
- Вкладка **Мерка** на ленте
- Группа и кнопка **Мерка** на вкладке **Данные**
- Макрос **load_merka**, доступный при настройке панели быстрого доступа

## Запуск приложения и настройка
Для запуска нажимаем кнопку **Мерка**, открывается пользовательская форма:
![Диалоговое окно надстройки](https://github.com/buchlotnik/Merka/blob/main/merka_form.png)

### Настраиваемые праметры:
- **необходимое число итераций** - количество циклов измерения скорости выполнения запросов
> **_Важно:_** в реальности итераций производится на одну больше, причем первый результат отбрасывается
- **выгрузка** - по умолчанию выгрузка результатов осуществляется на новый лист, при необходимости можно указать диапазон **на активном листе**, начиная с которого нужно выгружать результаты
- **показывать только выгружаемые запросы** - механика приложения позволяет оценить скорость только тех запросов, которые реально выгружаются на лист, при активации флажка из списка будут исключены запросы со статусом "только подключение" и функции
- **очищать названия запросов** - в списке подключений запросы получают префикс "Запрос - " или "Query - ", что не соответствует отображаемым именам в окне "запросы и подключения", при активации флажка префиксы удаляются из названий
- **создавать таблицу и сводную** - при активации флажка после завершения измерения скорости и выгрузки результатов на лист результаты будут отформатированы как Таблица с именем Мерка_DataX (где X - номер добавленной таблицы, нумерация начинается с нуля, номер изменяется при каждом следующем запуске измерения) и будет сформирована сводная таблица, в которой выводится статистика по проанализированным запросам
- **добавить рисунок сводной** - при активном флажке помимо сводной таблицы будет создаваться её копия в виде рисунка, помещается рядом на листе. опция нужна, если вы собираетесь делиться результатами на форумах или в телеграм-каналах, например https://t.me/PQ_ru
- **показывать вкладку Мерка** - при активном флажке вкладка отображается
- **кнопка на вкладке Данные** - при активном флажке во вкладке данные отображается дополнительная группа **Мерка** 
> **_Важно:_**  настройки вкладки и кнопки вступают в силу после перезапуска приложения или при открытии нового файла
> 
> **_Не менее важно:_**  если вы скрыли обе кнопки, а запустить надстройку всё-таки необходимо - используйте макрос **load_merka** с панели быстрого доступа

### Кнопки:
- **Начать измерение** - запустит процесс узмерения
- **Закрыть** - закроет форму
- **Сохранить настройки** - сохранит текущее состояние флажков и текстовых полей (настройки хранятся в самом файле **Мерка_версия.xlam**)
- **выбрать все** - выберет для анализа все запросы в списке на экране
- **убрать выделение** - снимет выделение со всех запросов на экране

## Общие замечания по использованию
- проанализировать можно только те запросы, которые реально выгружаются на лист
- оценить скорость выполнения отдельных шагов запроса, как в PBI, с текущей механикой приложения невозможно
- на скорость обновления запросов влияет нагруженность вашего процессора в целом, поэтому не следует, запустив процесс анализа, параллельно запускать игрульки или видосики с интернета
- для повышения корректности результатов производится и отбрасывается нулевая итерация обновления, также перед каждым запросом делается секундная задержка

## Автор
![buchlotnik](https://github.com/buchlotnik)
личный сайт пока в разработке, так что сорян

## Лицензия
Приложение бесплатное с открытым кодом, но для порядку см. ![LICENSE.md](https://github.com/buchlotnik/Merka/blob/main/LICENSE)
