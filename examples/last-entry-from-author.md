# Пример: Последние записи от автора

Данное решение будет отображать последние 10 статей от каждого автора.

```html
<mt:Authors>
<h1><mt:AuthorName/></h1>
<mt:SetVarBlock name="author"><mt:AuthorName/></mt:SetVarBlock>
<ul>
    <mt:Entries author="$author" lastn="10">
        <li><a href="mt:Permalink"><mt:EntryTitle/></a></li>
    </mt:Entries>
</ul>
</mt:Authors>
```

