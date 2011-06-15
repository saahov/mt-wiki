Глобальные фильтры могут быть применены практически к любым тегам. В данном примере будет рассмотрено применение фильтра к тегу EntryTitle.

Допустим, у вас есть такой код:
<source lang="xml"><h1><a href="<mt:EntryPermalink />"><mt:EntryTitle /></a></h1></source>

И вы хотите, чтобы из названия записи были вырезаны HTML-теги. Для этого нужно применить глобальный фильтр [[remove_html]]:
<source lang="xml"><h1><a href="<mt:EntryPermalink />"><mt:EntryTitle remove_html="1" /></a></h1></source>

Также возможно применение фильтров к целым блокам:
<source lang="xml"><!-- Сначала необходимо создать блок -->
<mt:SetVarBlock name="markdown_title"># <a href="<mt:EntryPermalink />"><mt:EntryTitle /></a></mt:SetVarBlock>

<!-- А затем в том месте, где необходимо, вывести его. -->
<mt:GetVar name="markdown_title" filters="markdown_with_smartypants" />
</source>


== Си. также ==

* [[Глобальные фильтры]] — список глобальных фильтров.


[[Категория:Шаблоны]]
[[Категория:Избранные статьи]]
[[Категория:Примеры шаблонов Movable Type]]

