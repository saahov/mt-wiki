# Нормальные адреса у страниц с тегами

При использовании стандартных шаблонов Movable Type URL тегов выглядят следующим образом:

```
http://example.com/cgi-bin/mt/mt.cgi?mt-search.cgi?blog_id=1&tag=tagname&limit=20
```
Не очень красивый и запоминающийся адрес, поэтому лучше сделать подобное:

```
http://example.com/tag/tagname
```

## Как сделать нормальные URL у тегов

* Для начала нужно выполнить поиск в шаблонах по фразе «TagSearchLink», результат отобразит все шаблоны, в которых есть тег `<mt:TagSearchLink />`.
* Этот тег нужно заменить на следущее: 
```
<mt:BlogURL />tag/<MTTagName encode_url="1" />
```
* После изменения шаблонов, нужно полностью опубликовать сайт. А также добавить в файл [.htaccess](http://ru.wikipedia.org/wiki/.htaccess) следующую строчку:

```apache
RewriteEngine on
RewriteRule ^tag/(.*)$ /cgi-bin/mt/mt-search.cgi?blog_id=1&tag=$1&limit=20
```

## Если блоги на разных доменах

Чтобы использовать такой метод для блогов, которые находятся на домене, отличном от домена, на котором находится Movable Type, необходимо добавить в [httpd.conf](http://httpd.apache.org/docs/2.0/configuring.html), в `VirtualHost` домена следующий параметр:

```apache
ScriptAlias /cgi-bin/ /home/username/example.com/cgi-bin/
```

То есть нужно указать, чтобы на этот домене папка скриптов располагалась в том месте, где располагается Movable Type.

После внесения изменений в httpd.conf, необходимо добавить в .htaccess параметры, аналогичные указанным выше.

**В каком случае это необходимо**

* По адресу `example.com/cgi-bin/mt/` располагается админка.
* Путь на сервере к этой папке для этого домена — `/home/username/example.com/cgi-bin/mt`.
* Второй блог располагается по адресу `example.org`. Для него стандартное расположение папки `cgi-bin` будет вида `/home/username/example.org/cgi-bin`. Поэтому необходимо для домена `example.org` переназначить расположение папки `cgi-bin`, чтобы при запросе `example.org/cgi-bin/mt/` обрабатывались скрипты из каталога `/home/username/example.com/cgi-bin/mt`.

## См. также

* [Модуль Apache mod_rewrite](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html)
