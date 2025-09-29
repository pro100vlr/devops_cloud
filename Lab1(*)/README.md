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

https://github.com/pro100vlr/devops_cloud/blob/main/Lab1(*)/common_admins.txt

Команда:

```ffuf -u https://apv19.ru/novosti/2023/chempionat-hakasii-po-shashkam-i-shahmatam.html/FUZZ -w ~/common_admins.txt -mc 200,403 -o ~/ffuf_results.txt -of md```

Почему это уязвимость: наличие таких эндпоинтов на публичном сервере представляет собой информационную утечку, даже при ограниченном доступе факт существования интерфейса уменьшает неопределённость для атакующего, позволяет идентифицировать используемые платформы и направляет дальнейший анализ (поиск уязвимостей аутентификации, уязвимых плагинов, целенаправленные атаки социальной инженерии).

<img width="718" height="230" alt="Снимок экрана 2025-09-29 в 19 36 49" src="https://github.com/user-attachments/assets/382d453f-1653-4fa2-b4b6-56d59dcddb61" />

Результат показывает, что такого вида уязвимости на сайте нет:

<img width="324" height="11" alt="Снимок экрана 2025-09-29 в 19 37 35" src="https://github.com/user-attachments/assets/f6bb94f1-91b1-4b7f-a73f-9d695fcda0f3" />

<img width="713" height="368" alt="Снимок экрана 2025-09-29 в 19 37 51" src="https://github.com/user-attachments/assets/ac5f6096-f48a-4d9a-8343-332309e8538f" />

2)Открытые резервные/архивные файлы и конфиги (backup.zip, db.sql, config.php, .env, .git/*)  

Файл: backups.txt    

https://github.com/pro100vlr/devops_cloud/blob/main/Lab1(*)/backups.txt

Команда: 

```ffuf -u https://apv19.ru/novosti/2023/chempionat-hakasii-po-shashkam-i-shahmatam.html/FUZZ -w ~/backups.txt -mc 200,403 -o ~/ffuf_results.txt -of md```

<img width="717" height="231" alt="Снимок экрана 2025-09-29 в 19 39 24" src="https://github.com/user-attachments/assets/a4ab8bb5-7d94-4036-98c1-c9202d383a2e" />

Результат показывает, что такого вида уязвимости на сайте нет:

<img width="312" height="12" alt="Снимок экрана 2025-09-29 в 19 39 40" src="https://github.com/user-attachments/assets/42317a58-ff84-4820-ad74-6e3799bf5410" />

<img width="716" height="368" alt="Снимок экрана 2025-09-29 в 19 39 56" src="https://github.com/user-attachments/assets/fa9ea0f3-0ffc-4236-ba5a-15fce9888f56" />

3)Открытые каталоги / directory listing (индексация папок) и тестовые/стадинговые окружения (/uploads/, /staging/, /dev/) Что ищешь: uploads, files, staging, dev, test, old, а также пути с / в конце — индексация каталогов.  

Файл: dirs.txt   

https://github.com/pro100vlr/devops_cloud/blob/main/Lab1(*)/dirs.txt

Команда:  

```ffuf -u https://apv19.ru/novosti/2023/chempionat-hakasii-po-shashkam-i-shahmatam.html/FUZZ -w ~/dirs.txt -mc 200,403 -o ~/ffuf_results.txt -of md```

<img width="717" height="222" alt="Снимок экрана 2025-09-29 в 19 40 27" src="https://github.com/user-attachments/assets/e272406b-0e6f-47f6-8e6e-586a4abc38a4" />

Результат показывает, что такого вида уязвимости на сайте нет:

<img width="329" height="10" alt="Снимок экрана 2025-09-29 в 19 41 06" src="https://github.com/user-attachments/assets/d8cfaa8a-9382-4916-9c62-0dd42261e522" />

<img width="719" height="368" alt="Снимок экрана 2025-09-29 в 19 41 18" src="https://github.com/user-attachments/assets/62d79a78-550a-410e-b94d-e2bf956b49bb" />

Насчет статусов:   
200 (OK) — означает, что ресурс доступен: файл/страница реально отдаются — это явный риск (утечка данных, открытая админка и т.д.).    
403 (Forbidden) — означает, что ресурс существует, но доступ запрещён; это тоже важная информация, так как атакующий узнаёт о наличии целевого интерфейса или файла.    

Итого: Взлом не успешен, так как не было выявлено уязвимостей.

Вывод:
В ходе работы я научилась устанавливать и использовать ffuf, разбираться в кодах ответов (200 и 403), а также проверять сайт на типовые уязвимости (админ-панели, резервные копии, открытые каталоги). На выбранном ресурсе таких уязвимостей не выявлено, что подтверждает корректность его базовой конфигурации.

