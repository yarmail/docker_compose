<a href="/README.md">вернуться к оглавлению</a>

<b>Подготовка и настройка</b> <br><br>

В домашнем каталоге создаем рабочую директорию и переходим в неё.<br>
В ней создаем папку app для файлов. 
<pre> 
user1@ubuntu:~$ mkdir ~/compose-demo
user1@ubuntu:~$ cd compose-demo
user1@ubuntu:~/compose-demo$
user1@ubuntu:~/compose-demo$ mkdir app
</pre>

В папке app создаем файл index.html со следующим содержимым:

``` html
user1@ubuntu:~/compose-demo$ nano app/index.html

<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Docker Compose Demo</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/kognise/water.css@latest/dist/dark.min.css">
</head>
<body>

	<h1>This is a Docker Compose Demo Page.</h1>
	<p>This content is being served by an Nginx container.</p>

</body>
</html>
```
Примечание: если вы использовали nano для редактирования, <br>
используйте CTRL+X, а затем Y и ENTER для подтверждения. <br><br>

Создаем docker-compose.yml <br>
`user1@ubuntu:~/compose-demo$ nano docker-compose.yml` <br><br>

со следующим содержимым
```yaml
version: '3.8'
services:
  web:
    image: nginx:alpine
    ports:
      - "8000:80"
    volumes:
      - ./app:/usr/share/nginx/html
```

Пояснения к файлу <br>
Файл docker-compose обычно начинается с определения версии. Версия показывает, <br>
какую спецификацию мы используем (надо ещё уточнить этот вопрос). <br><br>

Далее идет блок services, где настраиваются службы, являющиеся частью этой среды. <br>
В нашем случае у нас есть одна служба **web**.  Эта служба использует образ **nginx:alpine** <br>
и настраивает переадресацию портов с помощью директивы **ports**. Все запросы порта 8000 <br>
на компьютере **host** (система, где вызапускаете Docker Compose) будут перенаправляться в <br>
контейнер web на порту 80, где будет работать Nginx.<br><br>

Директива **volumes** создаст общий том для хоста и контейнера. Контейнеру будет предоставлен <br>
доступ к локальной папке **app**, а том будет располагаться в каталоге **/usr/share/nginx/html** <br>
внутри контейнера, который заменит корневой каталог документов Nginx по умолчанию.<br>
После настройки можно попробовать запустить docker-compose.