# Пример: Навигационная цепочка

Навигационная цепочка вида *Категория » Подкатегория*. Данное решение нужно вставлять в шаблон страниц.

```xml
<mt:HasParentCategory>
    <mt:ParentCategories exclude_current="1">
        <a href="<mt:CategoryArchiveLink/>"><mt:CategoryLabel/></a>
    </mt:ParentCategories>  »
</mt:HasParentCategory>
<mt:ArchiveTitle /> 
```

