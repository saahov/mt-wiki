Для защиты от автоматического спама (рассылаемого при помощи ботов) существует множество инструментов, начиная с привычных картинок с вводов цифр, заканчивая различными сервисами. Но все они, во-первых, неудобны для комментатора (требуют дополнительных действий), а во-вторых — не гарантируют 100% защиты.

'''[http://alogblog.com/movabletype/plugins/ccode_and_tcode_for_mt_40/ CCode]''' — это плагин для надёжной защиты от автоматического спама, не требующий от комментатора дополнительных действий. Принцип работы плагина хорошо [http://www.searchengines.ru/blog/archives/008448.html описал] Сергей Петренко:

<blockquote>
Одна часть спамбота вылавливает установленные на сайтах формы. Затем эта форма вносится в некую базу - на этом этапе форму может посмотреть человек и определить список обязательных полей. После чего спамбот начинает работать - без всяких посещений страниц, зачем? Делается прямой POST (или GET) запрос к обработчику формы, в котором передаются значения всех обязательных и желательных (например, адрес сайта редко бывает обязательным) полей. Все, собственно. Именно поэтому такими эффективными оказываются плагины типа CCode для Movable Type (кстати, спасибо saahov`у за совет), генерящие уникальный ключ для каждой загрузки формы - они просто в три раза удорожают работу спамбота и делают неэффективной достаточно простую операцию по их обходу. Потому что для каждого постинга через форму с CCode требуется загрузить исходную страницу, достать из нее значение определенного поля и отправить его обработчику. Три операции вместо одной. Дешевле просто выкинуть блог из базы.
</blockquote>

== Установка плагина ==

# Скачайте плагин с [http://alogblog.com/movabletype/plugins/ccode_and_tcode_for_mt_40/ официальной страницы] (или [http://movable-type.ru/uploads/2010/03/CTCode-4.0.00.zip с этого сайта]). Далее установите его [[Как устанавливать плагины|стандартным способом]].
# После этого необходимо добавить небольшой Javascript-код в ваш шаблон Javascript. Для этого скопируйте из файла <code>default_templates/obfuscator.js</code> код и вставьте его в конец вашего Javascript-шаблона.
# Теперь нужно добавить тег плагин в ''форму комментирования''. Найдите эту форму в ваших шаблонах, она может выглядеть так:

<source lang="html4strict">
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
</source>

Вам необходимо добавить после поля <code><input type="hidden" name="sid" value="" /></code> тег плагина <code><mt:EntryCCode /></code>. Пример:

<source lang="html4strict">
<form method="post" action="<$mt:CGIPath$><$mt:CommentScript$>" name="comments_form" id="comments-form" onsubmit="return mtCommentOnSubmit(this)">
        <input type="hidden" name="static" value="1" />
        <input type="hidden" name="entry_id" value="<$mt:EntryID$>" />
        <input type="hidden" name="__lang" value="<$mt:BlogLanguage$>" />
        <input type="hidden" name="parent_id" value="<$mt:CommentParentID$>" id="comment-parent-id" />
        <input type="hidden" name="armor" value="1" />
        <input type="hidden" name="preview" value="" />
        <input type="hidden" name="sid" value="" />
        <mt:EntryCCode />
        <div id="comments-open-data">
            <div id="comment-form-name">
                <label for="comment-author">Имя</label>
                <input id="comment-author" name="author" size="30" value="" onfocus="mtCommentFormOnFocus()" />
            </div>
            
<!-- Часть формы вырезана -->
</form>
</source>

После это можно публиковать шаблоны с постами, чтобы изменения отобразились на сайте.


== Плагин TCode ==

В архиве также есть плагин '''TCode''' для защиты от спама в трекбэках. Если вы не используете трекбэки, то плагин можно не устанавливать или деактивировать его после установки. Для использования необходимо лишь добавить код в Javascript-шаблон, как это показано в примере с CCode.



[[Категория:Плагины]]
[[Категория:Защита от спама]]

