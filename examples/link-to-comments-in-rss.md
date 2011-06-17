# Пример: Ссылка на комментарии в RSS-потоке

Чтобы вставить в RSS-поток (или Atom) ссылку на комментарии, необходимо проделать следующее (на примере Atom-потока):

* Найти в шаблоне «Лента последних сообщений» (или «Feed - Recent Entries» в английском варианте) код:

```xml
<content type="html" xml:lang="<$MTBlogLanguage ietf="1"$>" xml:base="<$MTBlogURL encode_xml="1"$>">
    <$MTEntryBody encode_xml="1"$>
    <$MTEntryMore encode_xml="1"$>
</content>
```

* И заменить его на вот этот:

```xml
<content type="html" xml:lang="<mt:BlogLanguage ietf="1"/>" xml:base="<mt:BlogURL encode_xml="1"/>">
    <![CDATA[
    <mt:EntryBody/>
    <mt:EntryMore/>
    <p>
        <mt:IfCommentsActive>
        <a href="<mt:EntryPermalink />#comments">
            <mt:EntryCommentCount singular="1 Комментарий" plural="# Комментария" none="Оставить комментарий"/>
        </a>
        </mt:IfCommentsActive>
    </p>
    ]]>
</content>
```

В результате в конце каждого сообщения будет ссылка на комментарии к записи с указанием их количества. Если комментариев нет, то будет выведена ссылка «Оставить комментарий».

