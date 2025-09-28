## Лабораторная работа(*) №1  
Выполнила: Просветова Валерия К3241

Задание со звездочкой(*):

Изначально пыталась установить ffuf напрямую, не вышло, я установила через golang:

<img width="694" height="369" alt="Снимок экрана 2025-09-28 в 15 54 56" src="https://github.com/user-attachments/assets/45dbbea0-0d21-4e61-9382-e26162166eab" />

Сайт, который взяла для проверки:
https://apv19.ru/novosti/2023/chempionat-hakasii-po-shashkam-i-shahmatam.html

Проверка на уязвимости:

1)Скрытые административные/управленческие панели (/admin, /panel, /wp-admin и т. п.)  
Файл: common_admins.txt  
Команда: ffuf -u https://apv19.ru/novosti/2023/chempionat-hakasii-po-shashkam-i-shahmatam.html/FUZZ -w ~/common_admins.txt -mc 200,403 -o ~/ffuf_results.txt -of md

Почему это уязвимость: наличие таких эндпоинтов на публичном сервере представляет собой информационную утечку — даже при ограниченном доступе факт существования интерфейса уменьшает неопределённость для атакующего, позволяет идентифицировать используемые платформы и направляет дальнейший анализ (поиск уязвимостей аутентификации, уязвимых плагинов, целенаправленные атаки социальной инженерии).

<img width="720" height="229" alt="Снимок экрана 2025-09-28 в 16 12 18" src="https://github.com/user-attachments/assets/05bab8de-5825-436c-acb0-5823cc24a609" />

Результат показывает, что такого вида уязвимости на сайте нет:

<img width="716" height="364" alt="Снимок экрана 2025-09-28 в 16 15 01" src="https://github.com/user-attachments/assets/21c48182-70f1-4a2b-ba47-9cdec6e3afaa" />

2)Открытые резервные/архивные файлы и конфиги (backup.zip, db.sql, config.php, .env, .git/*)  
Файл: backups.txt  
Команда: ffuf -u https://apv19.ru/novosti/2023/chempionat-hakasii-po-shashkam-i-shahmatam.html/FUZZ -w ~/backups.txt -mc 200,403 -o ~/ffuf_results.txt -of md

<img width="719" height="240" alt="Снимок экрана 2025-09-28 в 16 17 42" src="https://github.com/user-attachments/assets/2ca570f0-4d2f-4a06-a655-338e65f6212a" />

Результат показывает, что такого вида уязвимости на сайте нет:

<img width="719" height="368" alt="Снимок экрана 2025-09-28 в 16 18 34" src="https://github.com/user-attachments/assets/ab56597c-75a8-440d-8071-b0289ac3a3d8" />

3)Открытые каталоги / directory listing (индексация папок) и тестовые/стадинговые окружения (/uploads/, /staging/, /dev/) Что ищешь: uploads, files, staging, dev, test, old, а также пути с / в конце — индексация каталогов.  
Файл: dirs.txt  
Команда:  ffuf -u https://apv19.ru/novosti/2023/chempionat-hakasii-po-shashkam-i-shahmatam.html/FUZZ -w ~/dirs.txt -mc 200,403 -o ~/ffuf_results.txt -of md

<img width="706" height="230" alt="Снимок экрана 2025-09-28 в 16 21 27" src="https://github.com/user-attachments/assets/9489fb81-6739-48ba-b79c-178b129850cd" />

Результат показывает, что такого вида уязвимости на сайте нет:

<img width="716" height="370" alt="Снимок экрана 2025-09-28 в 16 25 24" src="https://github.com/user-attachments/assets/e41fc470-f09d-4a3a-8785-adb479177cfc" />

Насчет статусов:   
200 (OK) — означает, что ресурс доступен: файл/страница реально отдаются — это явный доказуемый риск (утечка данных, открытая админка и т.д.).    
403 (Forbidden) — означает, что ресурс существует, но доступ запрещён; это тоже важная информация — атакующий узнаёт о наличии целевого интерфейса или файла.    

Итого: Взлом не успешен, так как не было выявлено уязвимостей.

Вывод:
В ходе работы я научилась устанавливать и использовать ffuf, разбираться в кодах ответов (200 и 403), а также проверять сайт на типовые уязвимости (админ-панели, резервные копии, открытые каталоги). На выбранном ресурсе таких уязвимостей не выявлено, что подтверждает корректность его базовой конфигурации.

