<a href="/README.md">вернуться к оглавлению</a>

<b>Установка Docker Compose</b> <br><br>

Проверяем, установлен или нет Docker
<pre>
user1@ubuntu:~$ docker --version 
Docker version 23.0.4, build f480fb1
</pre>
Примечание: Если я правильно понимаю, от версии Docker зависит  <br>
спецификация YAML файла <br> 
`https://docs.docker.com/compose/compose-file/compose-versioning/` <br>
Если я правильно понимаю, после 19 версии Docker, на данный момент версия YAML 3.8 <br><br>

Проверяем установку Docker Compose <br>
Для этого просто запрашиваем установленную версию в терминале
<pre>
user1@ubuntu:~$ docker-compose --version
Command 'docker-compose' not found, but can be installed with...
</pre>

Для начала посмотрите какие версии доступны на странице релизов <br>
`https://github.com/docker/compose/releases`

Следующая команда загружает свежую версию и сохраняет исполняемый файл в каталоге <br>
`/usr/local/bin/docker-compose` после чего программа будет доступно под именем
`docker-compose`:
<pre>
sudo curl -L "https://github.com/docker/compose/releases/download/v2.18.0/docker-compose-$(uname -s)-$(uname -m)" \
-o /usr/local/bin/docker-compose
</pre>
Примечание: 
- \ - перенос на следующую строку; 
- v2.18.0 - номер версии, можно поменять на свою
- в новых версиях не забываем в ссылке проверить, чтобы версия была с буквой v: v2.18.0: 

Далее работаем с разрешениями, добавляем исполняемость<br>
`sudo chmod +x /usr/local/bin/docker-compose`<br>

Если все получилось проверяем версии<br>
<img src="/01_installation/install.png"/>