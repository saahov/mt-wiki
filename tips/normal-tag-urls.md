При использовании стандартных шаблонов Movable Type URL тегов выглядят следующим образом:
<source lang="apache">http://example.com/cgi-bin/mt/mt.cgi?mt-search.cgi?blog_id=1&tag=tagname&limit=20</source>
Не очень красивый и запоминающийся адрес, поэтому лучше сделать подобное:
<source lang="apache">http://example.com/tag/tagname</source>

== Как сделать нормальные URL у тегов ==

* Для начала нужно выполнить поиск в шаблонах по фразе «TagSearchLink», результат отобразит все шаблоны, в которых есть тег <code><mt:TagSearchLink /></code>.
* Этот тег нужно заменить на следущее: 
<source lang="apache"><mt:BlogURL />tag/<MTTagName encode_url="1" /></source>
* После изменения шаблонов, нужно полностью опубликовать сайт. А также добавить в файл [http://ru.wikipedia.org/wiki/.htaccess .htaccess] следующую строчку:
<source lang="apache">
RewriteEngine on
RewriteRule ^tag/(.*)$ /cgi-bin/mt/mt-search.cgi?blog_id=1&tag=$1&limit=20
</source>

== Если блоги на разных доменах ==

Чтобы использовать такой метод для блогов, которые находятся на домене, отличном от домена, на котором находится Movable Type, необходимо добавить в [http://httpd.apache.org/docs/2.0/configuring.html httpd.conf], в <code>VirtualHost</code> домена следующий параметр:
<source lang="apache">ScriptAlias /cgi-bin/ /home/username/example.com/cgi-bin/</source>
То есть нужно указать, чтобы на этот домене папка скриптов располагалась в том месте, где располагается Movable Type.

После внесения изменений в httpd.conf, необходимо добавить в .htaccess параметры, аналогичные указанным выше.

''В каком случае это необходимо:''

* По адресу <code>example.'''com'''/cgi-bin/mt/</code> располагается админка.
* Путь на сервере к этой папке для этого домена — <code>/home/username/example.'''com'''/cgi-bin/mt</code>.
* Второй блог располагается по адресу <code>example.'''org'''</code>. Для него стандартное расположение папки <code>cgi-bin</code> будет вида <code>/home/username/example.'''org'''/cgi-bin</code>. Поэтому необходимо для домена example.org переназначить расположение папки cgi-bin, чтобы при запросе example.'''org'''/cgi-bin/mt/ обрабатывались скрипты из каталога /home/username/example.'''com'''/cgi-bin/mt.

== См. также ==

* [http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html Модуль Apache mod_rewrite] {{ref-en}}


[[Категория:Шаблоны]]
[[Категория:Избранные статьи]]

