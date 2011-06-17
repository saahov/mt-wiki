# Пример: «Пейджинация» на статических страницах

Пейджинация — это разбивка содержимого на отдельные страницы. 

Существуют 3 способа сделать пейджинацию:

* Пейджинация по датам (рекомендуется)
* Пейджинация с помощью плагинов
* [Пейджинация при помощи PHP и Smarty|php-pagination]

## Пейджинация по датам

Пейджинация по датам — это когда контент отображается за определённый период, но вместо ссылок «предыдущая/следущая страницы выводятся ссылки на предыдущий/следующий период.

### Как это сделать

По умолчанию в Movable Type уже создано подобие такой пейджинации. Но, поскольку она не удовлетворяет требованиям некоторых пользователей, на форуме [родилось другое решение](http://movable-type.ru/forums/viewtopic.php?id=42).

(На примере стандартных шаблонов.)

Откройте файл «Список записей» (Entry Listing), найдите в нём код:

```xml
<div class="content-nav">
    <MTArchivePrevious>
    <a href="<$MTArchiveLink$>">&laquo; <$MTArchiveTitle$></a> |
    </MTArchivePrevious>
    <a href="<$MTLink template="main_index"$>">Main Index</a> |
    <a href="<$MTLink template="archive_index"$>">Archives</a>
    <MTArchiveNext>
    | <a href="<$MTArchiveLink$>"><$MTArchiveTitle$> &raquo;</a>
    </MTArchiveNext>
</div>
```

Замените его вот на этот:

```xml
<mt:IfArchiveType type="Author">
    <div class="content-nav">
        <mt:ArchiveList archive_type="Author-Monthly" lastn="1">
        <a href="<mt:ArchiveLink/>" id="last-link" title="Сообщения за <mt:ArchiveTitle/>">&laquo; За весь месяц</a>
        </mt:ArchiveList>
    </div>
</mt:IfArchiveType>
<mt:IfArchiveType type="Category">
    <div class="content-nav">
        <mt:ArchiveList archive_type="Category-Monthly" lastn="1">
        <a href="<mt:ArchiveLink/>" id="last-link" title="Сообщения за <mt:ArchiveTitle/>">&laquo; За весь месяц</a>
        </mt:ArchiveList>
    </div>
<mt:Else>
    <div class="content-nav">
        <mt:ArchivePrevious><a href="<mt:ArchiveLink/>">&laquo; <mt:ArchiveTitle/></a> | </mt:ArchivePrevious>
        <a href="<mt:Link template="main_index"/>">Главная страница</a> |
        <a href="<mt:Link template="archive_index"/>">Архивы</a>
        <mt:ArchiveNext> | <a href="<mt:ArchiveLink/>"><mt:ArchiveTitle/> &raquo;</a></mt:ArchiveNext>
    </div>
</mt:IfArchiveType>
```

Обратите внимание на первые 2 условия: Author и Category. Код сделан таким образом, что будут публиковаться (если эти архивы активны) ссылки на архивы категорий и авторов по месяцам. Если у вас не публикуются архивы категорий и авторов по месяцам, но, к примеру, публикуются архивы авторов и категорий по дням/неделям/годам, то необходимо изменить атрибут тега ArchiveList — archive_type.

В шаблоне главной страницы найдите код:

```xml
<div class="content-nav">
    <a href="<$MTLink template="archive_index"$>">Archives</a>
</div>
```
И замените его на этот:

```xml
<mt:IfArchiveTypeEnabled archive_type="Monthly">
    <div class="content-nav">
    <mt:ArchiveList archive_type="Monthly" lastn="1">
        <a href="<mt:ArchiveLink/>" id="last-link" title="Сообщения за <mt:ArchiveTitle/>">&laquo; За весь месяц</a>
    </mt:ArchiveList>
    </div>
</mt:IfArchiveTypeEnabled>
```

После этих действий опубликуйте блог полностью.
[Ещё один вариант пейджинации по датам](http://movable-type.ru/forums/viewtopic.php?pid=506#p506 ), предложенный участником форума liketts.

## Пейджинация с помощью плагинов

На данный момент самым актуальным плагином для пейджинации является разработка от Марка Кэри — [Pagination](http://mt-hacks.com/pagination.html). Плагин делаёт пейджинацию следующего вида: `index.html?page=1`, `index.html?page=2`, `index.html?page=3`, и т.д. Минус плагина: для страниц пейджинации используется динамическая публикация через Perl.

