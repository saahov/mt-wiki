RSS-лента уже используется в MT 4.1 в виде [http://ru.wikipedia.org/wiki/Atom Atom]. Следующий код создает обычный RSS-фид.

# Создайте новый Индексный шаблон. Назовите его '''RSS Feed''' и укажите выходной файл как ''rss.xml''. Содержание шаблона: 
<pre>
<$mt:HTTPContentType type="application/rss+xml"$><?xml version="1.0" encoding="<$mt:PublishCharset$>"?>
<rss version="2.0">
<channel>
        <title><$mt:BlogName remove_html="1" encode_xml="1"$></title>
        <link><$mt:BlogURL$></link>
        <description><$mt:BlogDescription remove_html="1" encode_xml="1"$></description>
        <language><$mt:BlogLanguage ietf="1"$></language>
        <copyright><__trans phrase="Copyright [_1]" params="<$mt:Date format="%Y"$>"></copyright>
        <lastBuildDate><mt:Entries lastn="1"><$mt:EntryDate format_name="rfc822"$></mt:Entries></lastBuildDate>
        <generator>http://www.sixapart.com/movabletype/</generator>
        <docs>http://www.rssboard.org/rss-specification</docs>
<mt:Entries lastn="15">
        <item>
            <title><$mt:EntryTitle remove_html="1" encode_xml="1"$></title>
            <description><$mt:EntryBody encode_xml="1"$></description>
            <link><$mt:EntryPermalink encode_xml="1"$></link>
            <guid><$mt:EntryPermalink encode_xml="1"$></guid>
<mt:EntryCategories>
            <category domain="http://www.sixapart.com/ns/types#category"><$mt:CategoryLabel remove_html="1" encode_xml="1"$></category>
</mt:EntryCategories>
<mt:EntryTags>
            <category domain="http://www.sixapart.com/ns/types#tag"><$mt:TagName remove_html="1" encode_xml="1"$></category>
</mt:EntryTags>
            <pubDate><$mt:EntryDate format_name="rfc822"$></pubDate>
        </item>
</mt:Entries>
    </channel>
</rss>
</pre>
# Сохраните шаблон '''RSS Feed'''.
# Опубликуйте шаблон '''RSS Feed'''.
# Добавте следующий код в шаблон содержащий HTML заголовок <head> (это могут быть "Шапка сайта" или "HTML head")
<pre><link rel="alternate" type="application/atom+xml" title="Atom" href="<$mt:Link template="RSS Feed"$>" />
</pre>


[[Категория:Гид дизайнера]]
[[Категория:Примеры шаблонов Movable Type]]
{{NeedEdit}}
[[Категория:Незавершённые статьи]]

