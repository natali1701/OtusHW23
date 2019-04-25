# **Web сервера**

## **Homework**

Написать конфигурацию nginx, которая даёт доступ клиенту только с определенной cookie.

Если у клиента её нет, нужно выполнить редирект на location, в котором кука будет добавлена, после чего клиент будет обратно отправлен (редирект) на запрашиваемый ресурс.

Смысл: умные боты попадаются редко, тупые боты по редиректам с куками два раза не пойдут

Для выполнения ДЗ понадобятся

https://nginx.org/ru/docs/http/ngx_http_rewrite_module.html

https://nginx.org/ru/docs/http/ngx_http_headers_module.html 


**Запускаем Vagrantfile, устанавливаем epel-release и nginx. Далее правим файл /etc/nginx/nginx.conf.**

Vagrantfile и nginx.conf приложены.

В итоге получаем:

[root@localhost ~]# curl -b none -L -I 127.0.0.1

HTTP/1.1 302 Moved Temporarily

Server: nginx/1.12.2

Date: Thu, 25 Apr 2019 12:29:27 GMT

Content-Type: text/html

Content-Length: 161

Connection: keep-alive

Location: http://127.0.0.1/cookie

HTTP/1.1 302 Moved Temporarily

Server: nginx/1.12.2

Date: Thu, 25 Apr 2019 12:29:27 GMT

Content-Type: text/html

Content-Length: 161

Connection: keep-alive

Location: http://127.0.0.1/

Set-Cookie: id=302

HTTP/1.1 404 Not Found

Server: nginx/1.12.2

Date: Thu, 25 Apr 2019 12:29:27 GMT

Content-Type: text/html

Content-Length: 169

Connection: keep-alive

