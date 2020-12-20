# ScreenshotSender: как один из вариантов победить прокторинг
 

**Идея:**
> Утилита периодически делает снимок экрана и отправляет его на email другу.
> Друг находит ответы на вопросы и отправляет их в каком-нибудь мессенджере на телефон сдающего.
> А телефон сдающего на протяжении тестирования закреплён на малоактивной области экрана.
 
![Terminal](https://github.com/Orlodox/ScreenshotSender/blob/master/Screenshot%20at%20Dec%2015%2018-22-31.png) 
![Email client](https://github.com/Orlodox/ScreenshotSender/blob/master/Screenshot%20at%20Dec%2015%2018-25-06.png)
![Smatrphone](https://github.com/Orlodox/ScreenshotSender/blob/master/Screenshot%20at%20Dec%2015%2018-41-54.png)


**Преимущества:**
> 1. Беспроблемный показ комнаты, если потребуется
> 2. Не надо переживать за качество камеры в телефоне и за стабильность соединения
> 3. Смотреть в ответы можно на протяжении всего тестирования, не вызывая подозрений
> 4. Можно сдать без личного присутствия друга


**Сложности:**
> На ноутбуке должна быть установлена Java 1.8 и
> нужно будет потыкать в настройках почтового аккаунта (своего или созданного), чтобы пропускались POP-сообщения

**Развёртка:**
> 1. Загрузить и установить Java 1.8. Убедиться, что консоль (терминал) понимает команду java.
> 2. Скачать файл [ScreenshotSender.jar](https://github.com/Orlodox/ScreenshotSender/raw/master/ScreenshotSender.jar/) из корня репозитория и положить его в папку, доступную сторонним приложениям для чтения и записи (в папку пользователя, например).
> 3. Подготовить аккаунт-отправитель на gmail. Можно создать новый или использовать свой – jar-ник никому не расскажет пароль. Управление аккаунтом Google -> Безопасность -> Ненадежные приложения, у которых есть доступ к аккаунту -> Разблокировать.
> 4. Убедиться, что не подключены дополнительные мониторы (с ними программный скриншот не делается).

**Запуск:**

> Открываем в консоли папку с jar-ником и пишем команду
> 
> `java -jar ScreenshotSender.jar fromEmail fromPassword toEmail directoryPath period` 
> 
> - `fromEmail` – подготовленная gmail-почта отправителя
> - `fromPassword` – пароль от этой почты
> - `toEmail` – почта друга, на которую будут отправляться скриншоты (часто попадают в спам!)
> - `directoryPath` – полный(!) путь в папку, доступную сторонним приложениям для чтения и записи, где будет лежать перезаписываемый скриншот
> - `period` – периодичность отправки в секундах. Лучше не отправлять чаще, чем раз в 20 секунд – этот период протестирован на протяжении 80 минут. У более частых запросов могут возникнуть проблемы на любой из сторон.

**Возможные проблемы:**
> Ошибка «could not convert socket to TSL». Решение – выключение антивирусника, перезагрузка компьютера, перезапуск jar-ника с выключенным антивирусником.
> Скриншот захватывает не весь экран. Решение – вместо обычного ScreenshotSender.jar скачать [dimFix.jar](https://github.com/Orlodox/ScreenshotSender/raw/master/dimFix.jar/) и запустить его аналогичным образом: `java -jar dimFix.jar fromEmail fromPassword toEmail directoryPath period`.

_Вопросы и всё остальное в [телеграм](https://t.me/orlodox) или в [ВК](https://vk.com/orlodox) : @orlodox_
