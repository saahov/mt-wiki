# Фильтры тегов

Фильтры тегов — это специальные атрибуты для тегов Movable Type, которые изменяют поведение тех или иных тегов.
Глобальные фильтры могут быть применены практически к любым тегам.

### Пример применения фильтра к тегу `<mt:EntryTitle/>`.

Допустим, у вас есть такой код:
```html
<h1><a href="<mt:EntryPermalink />"><mt:EntryTitle /></a></h1>
```

И вы хотите, чтобы из названия записи были вырезаны HTML-теги. Для этого нужно применить глобальный фильтр [[remove_html]]:
```html
<h1><a href="<mt:EntryPermalink />"><mt:EntryTitle remove_html="1" /></a></h1>
```

Также возможно применение фильтров к целым блокам:
```html
<!-- Сначала необходимо создать блок -->
<mt:SetVarBlock name="markdown_title"># <a href="<mt:EntryPermalink />"><mt:EntryTitle /></a></mt:SetVarBlock>

<!-- А затем в том месте, где необходимо, вывести его. -->
<mt:GetVar name="markdown_title" filters="markdown_with_smartypants" />
```


## Список глобальных фильтров

