Чтобы вставить в RSS-поток (или Atom) ссылку на комментарии, необходимо проделать следующее (на примере Atom-потока):

* Найти в шаблоне «Лента последних сообщений» (или «Feed - Recent Entries» в английском варианте) код:

<source lang="xml">
<content type="html" xml:lang="<$MTBlogLanguage ietf="1"$>" xml:base="<$MTBlogURL encode_xml="1"$>">
    <$MTEntryBody encode_xml="1"$>
    <$MTEntryMore encode_xml="1"$>
</content>
</source>

* И заменить его на вот этот:

<source lang="xml">
<content type="html" xml:lang="<mt:BlogLanguage ietf="1" />" xml:base="<mt:BlogURL encode_xml="1" />">
    <![CDATA[
    <mt:EntryBody />
    <mt:EntryMore />
    <p>
        <mt:IfCommentsActive>
        <a href="<mt:EntryPermalink />#comments">
            <mt:EntryCommentCount singular="1 Комментарий" plural="# Комментария" none="Оставить комментарий" />
        </a>
        </mt:IfCommentsActive>
    </p>
    ]]>
</content>
</source>

В результате в конце каждого сообщения будет ссылка на комментарии к записи с указанием их количества. Если комментариев нет, то будет выведена ссылка «Оставить комментарий».

[[Категория:Шаблоны]]
[[Категория:Избранные статьи]]
[[Категория:Примеры шаблонов Movable Type]]

