# react-phonebook
Телефонный справочник на Node.js + React

##Сервер
В корневой папке реализован сервер на node.js.

Для запуска следует открыть папку в терминале и выполнить команду `npm run start`.

В ответ вернётся сообщение: Server listening on 3001. Сервер запускается на порту 3001.
Логика работы сервера реализована в файле server/server.js. Сервер обрабатывает запросы на получение полного списка контактов, получение данных конкретного контакта по его порядковому номеру, редактирование существующей или добавление новой записи.

Данные номеров телефонов хранятся в файле data/usersData.json в формате json и возвращаются по запросу.

##Клиент

Клиентская часть реализована на React и находится в папке client.

Для запуска следует открыть папку client в терминале и выполнить команду `npm run start`.

После этого по адресу http://localhost:8080/ будет доступна главная страница приложения.

Клиентская часть реализована в файле client/src/App.js. На главной странице данные выводятся в виде таблицы, отсортированной по порядковому номеру контакта. Чтобы отредактировать контакт следует кликнуть по иконке "Редактировать" во втором столбце справа, либо зайти непосредственно по ссылке вида /edit/id, где id - номер контакта.

Для удаления контакта следует кликнуть по иконке "Удалить" в правом столбце. Добавить новый контакт можно по ссылке "Добавить новый контакт", либо перейдя непосдерственно по ссылке вида /add.

При удалении приложение затребует подтверждение в виде всплывающего окна. Если удаляется запись из середины таблицы, то порядковые номера будут пересчитаны с учётом удалённой записи.

При редактировании существующей записи, или добавлении новой, открывается отдельная страница с формой редактирования с текстовыми полями "Имя", "Город", "Адрес", "Телефон", а также тремя выпадающими списками select "День", "Месяц" и "Год", формирующих дату рождения. Списки формируются с помощью массивов в App.js, выбор доступного числа дня зависит от месяца (количество дней в месяце) и года (високосный, или нет).

При добавлении новой записи введённые данные сохраняются в localStorage браузера и подставляются автоматически при обновлении страницы.

При работе с формой предусмотрены ограничения на ввод в поле "Имя" - строка должна иметь длину не более 100 символов. Телефон вводится по специальной маске ввода в формате +79999999999.

При отправке данных предусмотрена валидация длины и заполненности полей "Имя" и всех полей даты рождения. Ввод телефона не обязателен, но если он вводится, то должен иметь указанный формат. Все сообщения об ошибках выводятся в виде всплывающих информационных блоков у полей, соответствующие поля выделяются красными рамками.

Дополнительная валидация, аналогичная клиентской, предусмотрена на стороне сервера. Если сервер по каким-то причинам получит не валидные данные, будет возвращена ошибка. Сообщение о ней отображается под кнопкой отправки.

Предусмотрены отображения страницы 404, сообщений при ошибках в запросах, loader-ов при обработке запросов.

Все страницы являются адаптивными и открываются по ширине любого экрана. 
