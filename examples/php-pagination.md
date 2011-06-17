# Пример: Пейджинация на PHP и Smarty

Рассмотрим, как можно при помощи PHP и пары шаблонов сделать динамическую пейджинацию.
Для работы этого примера понадобится создать 2 шаблона: один индексный, один модульный.

## 1. Создание модульного шаблона

Его нужно создать в первую очередь, так как в последствии будет использован ID этого шаблона.
Содержание этого шаблона можно скопировать из стандартного шаблона главной страницы:

```xml
<mt:SetVar name="body_class" value="mt-main-index">
<mt:SetVar name="main_template" value="1">
<mt:SetVar name="main_index" value="1">
<mt:SetVar name="sidebar" value="1">
<mt:SetVarBlock name="title"><mt:BlogName encode_html="1"/></mt:SetVarBlock>

<mt:Include module="Header"/>

<mt:Entries>
	<mt:EntryTrackbackData/>
	<mt:Include module="Entry Summary"/>
</mt:Entries>

<div class="content-nav">
	<a href="<mt:Link template="archive_index"/>">Archives</a>
</div>

<mt:Include module="Footer"/>
```

В этот шаблон необходимо добавить данные для пейджинации:

```xml
<mt:SetVar name="body_class" value="mt-main-index">
<mt:SetVar name="main_template" value="1">
<mt:SetVar name="main_index" value="1">
<mt:SetVar name="sidebar" value="1">
<mt:SetVarBlock name="title"><mt:BlogName encode_html="1"/></mt:SetVarBlock>

<mt:Include module="Header"/>

<mt:Entries lastn="10" offset="`$smarty.request.offset`">
	<mt:EntryTrackbackData/>
	<mt:Include module="Entry Summary"/>
</mt:Entries>

<div class="content-nav">
	{{capture assign="count"}}<mt:BlogEntryCount />{{/capture}}

	{{if $smarty.request.offset < $count-10}}
		<a href="?offset={{$smarty.request.offset+10}}">Следующая страница</a>
	{{/if}}

	{{if $smarty.request.offset > 0}}
		<a href="?offset={{math equation="max(x-10,0)" x=$smarty.request.offset}}">Предыдущая страница</a>
	{{/if}}
</div>

<mt:Include module="Footer"/>
```

## 2. Создание индексного шаблона

После создания модульного шаблона, нужно узнать его ID. Сделать это можно, посмотрев при редактировании адрес: `example.com/cgi-bin/mt/mt.cgi?__mode=view&_type=template&id=123&blog_id=1`. Где значение параметра id и есть ID шаблона (в данном примере 123).

Далее необходимо создать индексный шаблон, опубликовав его под именем `entries.php` (имя может быть и другое, главное — чтобы расширение было `.php`). Содержимое шаблона (не забудьте указать в нём ID своего модульного шаблона):

```php
<?php

// Подключение PHP-библиотеки MT
include('<mt:CGIServerPath/>/php/mt.php');

// Определение ID блога и загрузка конфига
$mt = new MT(<mt:BlogID/>, '<mt:ConfigFile/>'); // Для MT 4
//$mt = MT::get_instance(<mt:BlogID/>, '<mt:ConfigFile/>'); // Для MT 5

// Подкючение шаблона по ID
$mt->display("mt:123");

?>
```

## 3. Ссылка с главной страницы

Теперь, чтобы пользователи могли «листать» записи вашего блога, необходимо разместить ссылку с главной страницы. Для этого откройте шаблон главной страницы, найдите блок 

```html
<div class="content-nav">
	<a href="<mt:Link template="archive_index"/>">Archives</a>
</div>
```

и замените на
```html
<source lang="html4strict">
<div class="content-nav">
	<a href="<mt:BlogURL/>entries.php?offset=10">Предыдущие записи</a>
</div>
```

