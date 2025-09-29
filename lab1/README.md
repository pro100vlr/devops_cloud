## Лабораторная работа №1  
Выполнила: Просветова Валерия К3241
## Ход работы: 

1.Обновляю список доступных пакетов и устанавливаю nginx  

<img width="477" height="368" alt="Снимок экрана 2025-09-28 в 14 11 11" src="https://github.com/user-attachments/assets/235ad81b-1223-4208-bb99-b704bb022241" />

<img width="591" height="370" alt="Снимок экрана 2025-09-28 в 14 13 08" src="https://github.com/user-attachments/assets/e9fac0f1-994f-4d8d-84ef-9502004689b3" />

2.Создаю папки для сайтов, где в файлы записываю содержимое сайтов. Создаю самоподписанный SSL сертификат и делаю настройку nginx        
<p>
<img width="394" height="12" alt="Снимок экрана 2025-09-28 в 14 40 55" src="https://github.com/user-attachments/assets/982e7a16-6962-4338-a200-848df3ff0fb1" />        
</p>
<p>
<img width="378" height="27" alt="Снимок экрана 2025-09-28 в 14 41 30" src="https://github.com/user-attachments/assets/d51e317f-c64b-4f03-aca6-534f708a99a0" />       
</p>
<p>
<img width="413" height="12" alt="Снимок экрана 2025-09-28 в 14 41 51" src="https://github.com/user-attachments/assets/3ad16c7d-2ce1-4f15-a7c8-71958eb368b0" />         
</p>         

Содержимое файлов index.html для project1 и project2:

<img width="303" height="433" alt="Снимок экрана 2025-09-28 в 14 46 25" src="https://github.com/user-attachments/assets/3b348d65-3c63-4545-ae65-b967168e5235" />

<img width="292" height="445" alt="Снимок экрана 2025-09-28 в 14 46 49" src="https://github.com/user-attachments/assets/70a3e76c-e48b-4eac-88bc-ee26229efbc6" />

Теперь перхожу к созданию сертификата:

<img width="397" height="107" alt="Снимок экрана 2025-09-28 в 14 54 24" src="https://github.com/user-attachments/assets/ca99008b-1e6a-408a-8bc7-b40c2b508929" />

Настройка nginx:

<img width="535" height="57" alt="Снимок экрана 2025-09-28 в 14 57 10" src="https://github.com/user-attachments/assets/e91e520f-47b8-4c76-a70a-a0f2606a0ba0" />

Сначало создаю конфигурацию виртуальных хостов, потом символьную ссылку. Проверяю синтаксис конфигов nginx, затем перезапускаю его без полной остановки, только обновление настроек.

Конфигурация виртуальных хостов:

Здесь настраиваю редирект и alias для сайтов 

<img width="408" height="652" alt="Снимок экрана 2025-09-28 в 15 03 07" src="https://github.com/user-attachments/assets/3ea043d7-39cc-4f1f-868c-940de670df75" />

3.Проверка работы(редиректа и работы HTTPS)
<p>
<img width="427" height="83" alt="Снимок экрана 2025-09-28 в 15 21 45" src="https://github.com/user-attachments/assets/f4d9a93b-2981-474c-b321-b3c9d1b1166f" />
</p>

<img width="431" height="180" alt="Снимок экрана 2025-09-28 в 15 22 52" src="https://github.com/user-attachments/assets/334b737d-6fcb-4633-89d4-33493a38718f" />

Открываю сайты в браузере:     
Пытаюсь перейти на сайт первого проекта http://project1.local

<img width="718" height="389" alt="Снимок экрана 2025-09-28 в 15 26 33" src="https://github.com/user-attachments/assets/c860466d-ce3d-4b52-906b-53f9e0d1eb8e" />

Наблюдаю редирект на https://project1.local

<img width="720" height="393" alt="Снимок экрана 2025-09-28 в 15 26 52" src="https://github.com/user-attachments/assets/34022ba2-d6cc-4b12-a400-db9e3e443515" />

Пытаюсь перейти на сайт второго проекта http://project2.local
<img width="716" height="390" alt="Снимок экрана 2025-09-28 в 15 28 08" src="https://github.com/user-attachments/assets/b981abaa-1dfd-4647-b2f9-7a15ea424cf7" />

Наблюдаю редирект на https://project2.local

<img width="719" height="393" alt="Снимок экрана 2025-09-28 в 15 27 20" src="https://github.com/user-attachments/assets/e51424c7-c7fc-41d3-b9e7-1db05eee90ba" />

Вывод:   
В ходе работы я научилась устанавливать и настраивать веб-сервер nginx (создавать директории сайтов, конфиги, включать сайты через sites-enabled), генерировать самоподписанный SSL-сертификат (openssl) и настраивать перенаправление HTTP→HTTPS, добавлять alias для создания псевдонимов путей к катологам на сервере, проверять работу сайта и редиректы с помощью curl.

