Привет🙌, меня зовут Алексей.

Я начинающий QA-инженер с горящими глазами. Ищу удаленную работу!

__Обо мне:__

Я прохожу обучуние и осваиваю профессию инженера по тестированию на платформе SkyPro. Особый интерес проявляю к тестированию API и работе с SQL. Я активно посещаю онлайн-курсы, читаю профессиональные книги и форумы, где могу учиться у опытных профессионалов, постоянно общаюсь и коллегами по курсу, а так же с кураторами. Также ищу разные возможности и участвую в профессиональных конференциях и встречах, чтобы делиться знаниями. Всё это помогает мне развиваться в области тестирования и достигать высоких результатов в обучении и освоении новой профессии.

Связаться со мной:
https://t.me/alekseykazantsev

Языки и инструменты:
- функциональное тестирование;
- тестирование API;
- SQL.

Проект тестирования функциональной возможность добавления, редактирования и удаления личного события в личном кабинете учителя Skyeng.

Раздел 1. Функциональное тестирование
На тестирование нового элемента - “Личные события” потрачено 85 минут. 
Применены следующие виды тестироватия:

- Smoke тест
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/1.jpeg)




- Функциональное тестирование
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/2.jpeg)
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/3.jpeg)






- Приемочное тестирование
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/4.jpeg)




- Регрессионное тестрирование (старый функционал)
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/5.jpeg)




По результатам тестирования найдено 4 бага, все баги с низким приоритетом (P3) - Low, серьезность S4 - незначительная. 
Все баги заведены в баг-трекинговую систему Jira. Три бага связаны с визуальным отражением в календаре уроков и личных событий в момент, 
когда они совпадают по времени, согласно требованию урок всегда должен отображаться выше личных событий. Один баг связан с полем “Описание“,
согласно документации проекта поле не имеет ограничение по количеству символов, в проекте реализовано ограничение в 500 символов.
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/6.jpeg)






Работа по тестированию проводилась ПК VivobookAsus_Laptop X1502ZA, ОС Windows 11 Домашняя для одного языка Версия 22H2, 
Браузер Microsoft Edge Версия 111.0.1661.62 (Официальная сборка) (64-разрядная версия).



Раздел 2. Тестирование API
При тестировании функционала “Личные события” через API проведены следующие мероприятия:
- Созданы функциональные тест-кейсы, на основе которых определены методы для тестирования API
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/7.jpeg)


- Создана Postman-коллекция (ссылка) и проведен тест-ран. При запуске колеекции ошибок не выявлено;
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/8.jpeg)


- Дополнительно написан тест-кейс “Повторное удаление личного события“, данный тест-кейс нельзя проверить через UI через один клиент (браузер). Также API позволяет при редактировании личного события устанавливать любую дату нового события как в прошлом так и в будущем, в отличие от UI (диапазон дат, редактируемого личного события, равен понедельнику недели в котором находится редактируемое личное событие плюс 3 месяца)
- Выявлен баг отображения времени урока, созданного через API на UI. При последовательном прогоне запросов в Postman (создание, редактирование) часовой пояс указанный в теле запроса на 1 час больше чем часовой пояс который фиксируется в UI. Связано с тем, что тестовая версия личного кабинета не учитывает часовой пояс пользователя, по умолчанию стоит часовой пояс МСК +3, а в Postman используются данные из инструментов разработчика пользователя (часовой пояс пользователя).
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/9.jpeg)
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/10.jpeg)






Заключение. 

Раздел 1. Найденые баги являются низкими по приоритету, так как не влияют на новую функциональность, и можно исправить в последнюю очередь. Основные операции с “Личными событиями“: добавление, удаление, редактирование, совмещение личного события и урока работают согласно документации к проекту. Так же было проведено регресс-тестирование старого функционала перенос и отмена “Урока”, данные функции работают без замечаний.

Раздел 2. Благодаря тестированию API появилась возможность протестировать более широкий диапазон переноса дат события, особенно это касаестся даты в прошлом. Так же мы убедились в том, что при первом удалении личного события оно гарантировано удаляется из системы, что подтверждает запрос на повторное удаление личного события. Выявили баг несоответствия часового пояса польвателя с данными в личном кабинете.

Вывод: 
- новый функционал (личные события) системы готов к выпуску;
- остальной функционал (уроки - перенос, отмена) системы работает в прежнем режиме;
- проведенное тестирование API, подтверждает ранее сделанные выводы о работе функционала “Личные собития“, функционал работает согласно документации к проекту;
- необходимо к следующему релизу рассмотреть возможность изменения технологии корректировки даты в UI (выбор не из выпадающего списка, а через календарь);
- автоматический учет часового пояса пользователя на основании данных из ОС


