<h3> Подключение и пример работы с Docker Compose</h3>
В данном примере создадим страничку в html <br> 
и запустим её через nginx в Ubuntu, используя Docker Compose<br>
Жми ★ если понравилось. <br><br>

<b>Примечание</b> <br>
Все работы будут проводится на Ubuntu 22.04 <br>

<a href="/01_installation/INSTALLATION.md">Установка Docker Compose</a> <br>
Проверяем наличие программы и, если её нет, устанавливаем.<br><br>

<a href="/02_tuning/TUNING.md">Подготовка и настройка</a> <br>
Создание рабочего каталога, работа с docker-compose.yml и др.<br><br>

<b>Запуск Docker Compose</b> <br>
После установки и настройки всех частей приложения можно попробовать запустить<br>
получившуюся систему. <br>
Для запуска используем следующую команду: <br>
`user1@ubuntu:~/compose-demo$ docker-compose up -d`

<details>
<summary>Результат выполнения команды docker-compose up (скрин)</summary>
<img alt="" src="/03_run/docker_compose_up.png">
</details>

Docker Compose сначала попробует найти заданные образы в локальной системе, <br>
и если не найдет, загрузит его из Docker Hub <br>

Проверяем результат запуска образа, в браузере переходим по адресу, <br>
`http://localhost:8000/` <br>
указанному в настройках и наблюдаем нужную страницу.<br>

<details>
<summary>Результат выполнения localhost:8000 (скрин)</summary>
<img alt="" src="/03_run/localhost_8000.png">
</details>

Для остановки docker-compose и удаления контейнера, сети и тома,<br>
связанные с контейнерной средой используем docker-compose down
<pre>
user1@ubuntu:~/compose-demo$ docker-compose down
[+] Running 2/2
 ✔ Container compose-demo-web-1  Removed                       0.6s 
 ✔ Network compose-demo_default  Removed                       0.4s 
user1@ubuntu:~/compose-demo$ 
</pre>
