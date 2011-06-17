# Плагины CCode и TCode

Для защиты от автоматического спама (рассылаемого при помощи ботов) существует множество инструментов, начиная с привычных картинок с вводов цифр, заканчивая различными сервисами. Но все они, во-первых, неудобны для комментатора (требуют дополнительных действий), а во-вторых — не гарантируют 100% защиты.

[CCode](http://alogblog.com/movabletype/plugins/ccode_and_tcode_for_mt_40/)— это плагин для надёжной защиты от автоматического спама, не требующий от комментатора дополнительных действий. Принцип работы плагина хорошо [описал](http://www.searchengines.ru/blog/archives/008448.html) Сергей Петренко:

> Одна часть спамбота вылавливает установленные на сайтах формы. Затем эта форма вносится в некую базу - на этом этапе форму может посмотреть человек и определить список обязательных полей. После чего спамбот начинает работать - без всяких посещений страниц, зачем? Делается прямой POST (или GET) запрос к обработчику формы, в котором передаются значения всех обязательных и желательных (например, адрес сайта редко бывает обязательным) полей. Все, собственно. Именно поэтому такими эффективными оказываются плагины типа CCode для Movable Type (кстати, спасибо saahov`у за совет), генерящие уникальный ключ для каждой загрузки формы - они просто в три раза удорожают работу спамбота и делают неэффективной достаточно простую операцию по их обходу. Потому что для каждого постинга через форму с CCode требуется загрузить исходную страницу, достать из нее значение определенного поля и отправить его обработчику. Три операции вместо одной. Дешевле просто выкинуть блог из базы.

TCode работает аналогичным образом, но для трекбэков. Их рекомендуется выключить на системном уровне, а также удалить или переименовать скрипт трекбэков, так как кроме спамеров трекбэками никто не пользуется. 

## Установка плагина

* Скачайте плагин с [официальной страницы](http://alogblog.com/movabletype/plugins/ccode_and_tcode_for_mt_40/) (или с сайта [MT.ru](http://movable-type.ru/uploads/2010/03/CTCode-4.0.00.zip)\). Далее установите его [[стандартным способом|install-plugins]].
* После этого необходимо добавить небольшой Javascript-код в ваш шаблон Javascript. Для этого скопируйте из файла `default_templates/obfuscator.js` код и вставьте его в конец вашего Javascript-шаблона.
* Теперь нужно добавить тег плагин в форму комментирования. Найдите эту форму в ваших шаблонах, она может выглядеть так:

```html
<form method="post" action="<$mt:CGIPath$><$mt:CommentScript$>" name="comments_form" id="comments-form" onsubmit="return mtCommentOnSubmit(this)">
    <input type="hidden" name="static" value="1" />
    <input type="hidden" name="entry_id" value="<$mt:EntryID$>" />
    <input type="hidden" name="__lang" value="<$mt:BlogLanguage$>" />
    <input type="hidden" name="parent_id" value="<$mt:CommentParentID$>" id="comment-parent-id" />
    <input type="hidden" name="armor" value="1" />
    <input type="hidden" name="preview" value="" />
    <input type="hidden" name="sid" value="" />
    <div id="comments-open-data">
        <div id="comment-form-name">
            <label for="comment-author">Имя</label>
            <input id="comment-author" name="author" size="30" value="" onfocus="mtCommentFormOnFocus()" />
        </div>
        
<!-- Часть формы вырезана -->
</form>
```

Вам необходимо добавить после поля `<input type="hidden" name="sid" value="" />` тег плагина `<mt:EntryCCode/>`. Пример:

```html
<form method="post" action="<$mt:CGIPath$><$mt:CommentScript$>" name="comments_form" id="comments-form" onsubmit="return mtCommentOnSubmit(this)">
        <input type="hidden" name="static" value="1" />
        <input type="hidden" name="entry_id" value="<$mt:EntryID$>" />
        <input type="hidden" name="__lang" value="<$mt:BlogLanguage$>" />
        <input type="hidden" name="parent_id" value="<$mt:CommentParentID$>" id="comment-parent-id" />
        <input type="hidden" name="armor" value="1" />
        <input type="hidden" name="preview" value="" />
        <input type="hidden" name="sid" value="" />
        <mt:EntryCCode/> <!-- Тег плагина -->
        <div id="comments-open-data">
            <div id="comment-form-name">
                <label for="comment-author">Имя</label>
                <input id="comment-author" name="author" size="30" value="" onfocus="mtCommentFormOnFocus()" />
            </div>
            
<!-- Часть формы вырезана -->
</form>
```

После это можно публиковать шаблоны с постами, чтобы изменения отобразились на сайте.
