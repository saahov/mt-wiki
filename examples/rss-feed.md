# Пример: Создание RSS-потока

Лента с последними сообщениями уже используется в MT 4.1, но в [Atom](http://ru.wikipedia.org/wiki/Atom)-формате. Используя следующий пример, вы можете создать ленту с последними сообщениями в формате RSS.

### Создание шаблона

1. Создайте новый Индексный шаблон.
2. Назовите его `RSS Feed` и укажите имя публикуемого файла `rss.xml`.
3. Содержание шаблона:

```xml
<mt:HTTPContentType type="application/rss+xml"/>
<?xml version="1.0" encoding="<mt:PublishCharset/>"?>
<rss version="2.0">
    <channel>
        <title><mt:BlogName remove_html="1" encode_xml="1"/></title>
        <link><mt:BlogURL/></link>
        <description><mt:BlogDescription remove_html="1" encode_xml="1"/></description>
        <language><mt:BlogLanguage ietf="1"/></language>
        <copyright>Copyright <mt:Date format="%Y"/></copyright>
        <lastBuildDate><mt:Entries lastn="1"><mt:EntryDate format_name="rfc822"/></mt:Entries></lastBuildDate>
        <generator>Movable Type <mt:Version/></generator>
        <mt:Entries lastn="15">
            <item>
                <title><mt:EntryTitle remove_html="1" encode_xml="1"/></title>
                <description><mt:EntryBody encode_xml="1"/></description>
                <link><mt:EntryPermalink encode_xml="1"/></link>
                <guid><mt:EntryPermalink encode_xml="1"/></guid>
                <mt:EntryCategories>
                    <category domain="<mt:BlogURL/>"><mt:CategoryLabel remove_html="1" encode_xml="1"/></category>
                </mt:EntryCategories>
                <mt:EntryTags>
                    <category domain="<mt:BlogURL/>"><mt:TagName remove_html="1" encode_xml="1"/></category>
                </mt:EntryTags>
                <pubDate><mt:EntryDate format_name="rfc822"/></pubDate>
            </item>
        </mt:Entries>
    </channel>
</rss>
```
Теперь осталось опубликовать шаблон и добавить (или заменить, если подобный тег присутствует) ссылку на RSS в шаблон. Приведённый пример добавляется между тегами `head`, чтобы браузеры могли самостоятельно обнаруживать поток. В стандартных шаблонах теги `head` находятся либо в шаблоне «Шапка сайта», либо в «HTML head»

```html
<link rel="alternate" type="application/rss+xml" title="RSS" href="<mt:Link template="RSS Feed"/>" />
```

