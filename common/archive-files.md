Пути публикации архивов

Пути публикации архивов используются при создания архива, они определяют, с какой структурой и с какими именами будут опубликованы архивные шаблоны. Если рассматривать пути публикации со стороны конечного пользователя сайта, то это — адреса страниц (URL).

Один шаблон может иметь несколько путей публикации, например, архив автора и автора по месяцам может быть опубликован с помощью одного шаблона, если в нём задать специальные условия с помощью тегов <code>mt:If, mt:Else, mt:Unless</code>, и др. 

Для создания архива по месяцам подобно этому:
<source lang="html4strict">2008/12/index.html</source>

… используйте <code>%y</code> для обозначения года в четырёхзначном формате и <code>%m</code> для обозначения месяца в двухзначном формате, а также <code>%i</code> для индексного файла. Также не забывайте разделять значения слэшем («/»):
<source lang="html4strict">%y/%m/%i</source>

Для создания архива категории подобно этому:
<source lang="html4strict">категория/под-категория/index.html</source>

… используйте <code>%-c</code> для создания пути категории, слова в которой разделены дефисом, а также <code>%i</code> для индексного файла, не забывая разделять значения слэшем:
<source lang="html4strict">%-c/%i</source>

Чтобы создать архив записи подобно этому:
<source lang="html4strict">2008/12/entry-basename.html</source>

… 4-х значный год, 2-х значный месяц, а также базовое имя записи с расширением, указанным в параметрах блога:
<source lang="html4strict">%y/%m/%-f</source>

Пути архивов используют различные теги Movable Type для создания ссылок (например, <code><mt:EntryPermalink /></code>). Когда путь архива заканчивается индексным файлом (для большинства серверов это <code>index.html</code> или <code>index.php</code>), то Movable Type удаляет этот индексный файл из URL.

Таким образом, если фактическое расположение файлов выглядит так:
<source lang="html4strict">2008/12/entry-basename/index.html
2008/12/index.html</source>

То Movable Type создаёт ссылки без индексного файла (если только вы не создадите собственный путь, в котором индексный файл будет):
<source lang="html4strict"><a href="2008/12/entry-basename/"><!-- запись --></a>
<a href="2008/12/"><!-- ежемесячный архив --></a></source>


== Основные пути архивов ==

Ниже представлены основные пути архивов в Movable Type. Значение по умолчанию для определённого типа архива выделено '''жирным''' шрифтом.

<table> <tr> <th>Тип архива</th> <th>Путь архива</th> <th>Значение в шаблонах</th> </tr> <tr><td><strong>Запись</strong></td><td><code>гггг/мм/базовое-имя-записи.html</code></td><td><code>%y/%m/%-f</code></td></tr> <tr><td>Запись</td><td><code>гггг/мм/базовое_имя_записи.html</code></td><td><code>%y/%m/%f</code></td></tr> <tr><td>Запись</td><td><code>гггг/мм/базовое-имя-записи/index.html</code></td><td><code>%y/%m/%-b/%i</code></td></tr> <tr><td>Запись</td><td><code>гггг/мм/базовое_имя_записи/index.html</code></td><td><code>%y/%m/%b/%i</code></td></tr> <tr><td>Запись</td><td><code>гггг/мм/дд/базовое-имя-записи.html</code></td><td><code>%y/%m/%d/%-f</code></td></tr> <tr><td>Запись</td><td><code>гггг/мм/дд/базовое_имя_записи.html</code></td><td><code>%y/%m/%d/%f</code></td></tr> <tr><td>Запись</td><td><code>гггг/мм/дд/базовое-имя-записи/index.html</code></td><td><code>%y/%m/%d/%-b/%i</code></td></tr> <tr><td>Запись</td><td><code>гггг/мм/дд/базовое_имя_записи/index.html</code></td><td><code>%y/%m/%d/%b/%i</code></td></tr> <tr><td>Запись</td><td><code>категория/под-категория/базовое-имя-записи.html</code></td><td><code>%-c/%-f</code></td></tr> <tr><td>Запись</td><td><code>категория/под-категория/базовое-имя-записи/index.html</code></td><td><code>%-c/%-b/%i</code></td></tr> <tr><td>Запись</td><td><code>категория/под_категория/базовое_имя_записи.html</code></td><td><code>%c/%f</code></td></tr> <tr><td>Запись</td><td><code>категория/под_категория/базовое_имя_записи/index.html</code></td><td><code>%c/%b/%i</code></td></tr> <tr><td><strong>Страница</strong></td><td><code>путь-папки/базовое-имя-страницы.html</code></td><td><code>%-c/%-f</code></td></tr> <tr><td>Страница</td><td><code>путь-папки/базовое-имя-страницы/index.html</code></td><td><code>%-c/%-b/%i</code></td></tr> <tr><td>Страница</td><td><code>путь_папки/базовое_имя_страницы.html</code></td><td><code>%c/%f</code></td></tr> <tr><td>Страница</td><td><code>путь_папки/базовое_имя_страницы/index.html</code></td><td><code>%c/%b/%i</code></td></tr> <tr><td><strong>Ежедневный</strong></td><td><code>гггг/мм/дд/index.html</code></td><td><code>%y/%m/%d/%f</code></td></tr> <tr><td><strong>Еженедельный</strong></td><td><code>гггг/мм/день-недели/index.html</code></td><td><code>%y/%m/%d-week/%i</code></td></tr> <tr><td><strong>Ежемесячный</strong></td><td><code>гггг/мм/index.html</code></td><td><code>%y/%m/%i</code></td></tr> <tr><td><strong>Ежегодный</strong></td><td><code>гггг/index.html</code></td><td><code>%y/%i</code></td></tr> <tr><td><strong>Категория</strong></td><td><code>категория/под-категория/index.html</code></td><td><code>%-c/%i</code></td></tr> <tr><td>Категория</td><td><code>категория/под_категория/index.html</code></td><td><code>%c/%i</code></td></tr> <tr><td><strong>Ежедневный категории</strong></td><td><code>категория/под-категория/гггг/мм/дд/index.html</code></td><td><code>%-c/%y/%m/%d/%i</code></td></tr> <tr><td>Ежедневный категории</td><td><code>категория/под_категория/гггг/мм/дд/index.html</code></td><td><code>%c/%y/%m/%d/%i</code></td></tr> <tr><td><strong>Ежемесячный категории</strong></td><td><code>категория/под-категория/гггг/мм/index.html</code></td><td><code>%-c/%y/%m/%i</code></td></tr> <tr><td>Ежемесячный категории</td><td><code>категория/под_категория/гггг/мм/index.html</code></td><td><code>%c/%y/%m/%i</code></td></tr> <tr><td><strong>Еженедельный категории</strong></td><td><code>категория/под-категория/гггг/мм/день-недели/index.html</code></td><td><code>%-c/%y/%m/%d-week/%i</code></td></tr> <tr><td>Еженедельный категории</td><td><code>категория/под_категория/гггг/мм/день-недели/index.html</code></td><td><code>%c/%y/%m/%d-week/%i</code></td></tr> <tr><td><strong>Ежегодный категории</strong></td><td><code>категория/под-категория/гггг/index.html</code></td><td><code>%-c/%y/%i</code></td></tr> <tr><td>Ежегодный категории</td><td><code>категория/под_категория/гггг/index.html</code></td><td><code>%c/%y/%i</code></td></tr> <tr><td><strong>Автор</strong></td><td><code>автор/отображаемое-имя-автора/index.html</code></td><td><code>author/%-a/%f</code></td></tr> <tr><td>Автор</td><td><code>автор/отображаемое_имя_автора/index.html</code></td><td><code>author/%a/%f</code></td></tr> <tr><td><strong>Ежедневный автора</strong></td><td><code>автор/отображаемое-имя-автора/гггг/мм/дд/index.html</code></td><td><code>author/%-a/%y/%m/%d/%f</code></td></tr> <tr><td>Ежедневный автора</td><td><code>автор/отображаемое_имя_автора/гггг/мм/дд/index.html</code></td><td><code>author/%a/%y/%m/%d/%f</code></td></tr> <tr><td><strong>Ежемесячный автора</strong></td><td><code>автор/отображаемое-имя-автора/гггг/мм/index.html</code></td><td><code>author/%-a/%y/%m/%f</code></td></tr> <tr><td>Ежемесячный автора</td><td><code>автор/отображаемое_имя_автора/гггг/мм/index.html</code></td><td><code>author/%a/%y/%m/%f</code></td></tr> <tr><td><strong>Еженедельный автора</strong></td><td><code>автор/отображаемое-имя-автора/гггг/мм/день-недели/index.html</code></td><td><code>author/%-a/%y/%m/%d-week/%f</code></td></tr> <tr><td>Еженедельный автора</td><td><code>автор/отображаемое_имя_автора/гггг/мм/день-недели/index.html</code></td><td><code>author/%a/%y/%m/%d-week/%f</code></td></tr> <tr><td><strong>Ежегодный автора</strong></td><td><code>автор/отображаемое-имя-автора/гггг/index.html</code></td><td><code>author/%-a/%y/%f</code></td></tr> <tr><td>Ежегодный автора</td><td><code>автор/отображаемое_имя_автора/гггг/index.html</code></td><td><code>author/%a/%y/%f</code></td></tr> </table>

== Редактирование пути архива ==

Путь архива располагается в разделе «Опции шаблона», который находится внизу каждого архивного шаблона.

# Перейдите к Дизайн -> Шаблоны.
# Откройте любой архивный шаблон, например: Запись, Список записей категории, Ежемесячный список записей, и т.д.
# В нижней части экрана найдите ссылку «Опции шаблона», там будет «Путь публикации архивов», где вы можете отредактировать существующий или создать новый путь.


== Использование тегов шаблонов в путях архивов ==

Movable Type позволяет использовать в путях архивов теги шаблонов.

Например, чтобы опубликовать записи с подобным URL:
<source lang="html4strict">2009/September/16/basename.html</source>

Используйте тег mt:EntryDate, в котором можно использовать дополнительные форматы дат. В результате путь архивов будет выглядеть так:
<source lang="html4strict">%y/<mt:EntryDate format="%B" />/%d/%-f</source>

Пример с использованием дат и слэшей:
<source lang="html4strict"><mt:EntryDate format="%Y/%B/%d" />/%-f</source>

'''Обратите внимание:''' необходимо понимать, что использование тегов шаблонов в путях архивов в некоторых ситуациях несёт определённые риски. Нет абсолютной гарантии, что указанные теги, а также их комбинация с модификаторами (например, dirify="1") будет совместима в будущих версиях. Если вы используете теги в этом месте, то не забывайте детально проверять список изменений в новых версиях Movable Type, чтобы избежать возможных ошибок в работе.


== Значения путей архивов ==

'''%a'''

Базовое имя автора <code><mt:AuthorBasename /></code> Пример: <code>melody_nelson</code>.

'''%_a'''

То же самое, что и <code>%a</code>. Может быть использовано для принудительного использования подчёркивания.

'''%-a'''

То же самое, но с использованием дефиса. Пример: <code>melody-nelson</code>.

'''%b'''

Для индивидуального имени записи, равнозначно <code><mt:EntryBasename /></code>. По умолчанию это первые 30 дирифицированных символов с использованием подчёркивания в качестве разделителя. Значение указывается автоматически для записи, но может быть переопределено вручную через поле «Базовое имя» в редакторе записей. Пример: <code>my_summer_vacation</code>

'''%_b'''

Тоже самое, что и <code>%b</code>.

'''%-b'''

То же, что и выше, но используется дефис вместо подчёркивания. Пример: <code>my-summer-vacation</code>.

'''%c'''

Путь категории и подкатегории (если существует) до записи. Используется базовое имя категории. Пример: <code>arts_and_entertainment/tv_and_movies</code>.

'''%_c'''

Равнозначно <code>%c</code>.

'''%-c'''

Тоже, что и выше, но с использованием дефиса. Пример: <code>arts-and-entertainment/tv-and-movies</code>.

'''%C'''

Базовое имя основной категории, равнозначно тегу <code><mt:CategoryBasename /></code> Пример: <code>tv_and_movies</code>.

'''%-C'''

Тоже, что и выше, но с использованием дефиса. Пример: <code>tv-and-movies</code>.

'''%d'''

Двухзначное значение месяца. Равнозначно тегу <code><mt:ArchiveDate format="%d" /></code> Пример: <code>09</code>.

'''%D'''

Трёхзначное название дня недели. Равнозначно тегу <code><mt:ArchiveDate format="%e" trim="1" /></code> Пример: <code>Tue</code>.

'''%e'''

Числовое значение ID записи — шесть цифр. Если значение ID меньше 999999, то первые цифры заменяются нулями. Равнозначно тегу <code><mt:EntryID pad="1" /></code>. Пример: <code>000040</code>.

'''%E'''

Числовое значение ID записи. Равнозначно тегу <code><mt:EntryID pad="0" /></code>. Пример: <code>40</code>.

'''%f'''

Имя публикуемого файла, уже включающее расширение, указанное в параметрах блога. Может быть использовано вместо <code>%b</code> или <code>%i</code> для обеспечения правильного поведения в соответствии с контекстом. Равнозначно тегу <code><mt:ArchiveFile /></code> Пример: <code>entry_basename.html</code> или <code>index.html</code>.

'''%-f'''

Тоже, что и <code>%f</code>, но с использованием дефиса. Пример: <code>entry-basename.html</code>.

'''%F'''

Тоже, что и <code>%f<code>, но без расширения файла. Равнозначно тегу <code><mt:ArchiveFile extension="0" /></code>. Пример: <code>entry_basename</code>.

'''%-F'''

Тоже, что и <code>%f</code>, но без расширения файла и с использованием дефиса. Равнозначно тегу <code><mt:ArchiveFile extension="0" separator="-" /></code>. Пример: <code>entry-basename</code>.

'''%h'''

Час в 24-часовом формате с ведущим нулём. Равнозначно тегу <code><mt:ArchiveDate format="%H" /></code> Пример: <code>09</code> или <code>16</code>.

'''%H'''

Час в 24-часовом формате без ведущего нуля. Равнозначно тегу <code><mt:ArchiveDate format="%k" trim="1" /></code> Пример: <code>9</code> или <code>16</code>.

'''%i'''

Значение конфигурационной директивы [[IndexBasename]] вместе с расширением файла. Равнозначно тегу <code><mt:IndexBasename extension="1" /></code>. Пример: <code>index.html</code>.

'''%I'''

Тоже, что <code>%i<code>, но без расширения файла. Равнозначно тегу <code><mt:IndexBasename /></code> Пример: <code>index</code>.

'''%j'''

Трёхзначный день года, c нулями. Равнозначно тегу <code><mt:ArchiveDate format="%j" /></code> Пример: <code>040</code>.

'''%m'''

Двухзначный месяц, с нулями. Равнозначно тегу <code><mt:ArchiveDate format="%m" /></code> Пример: <code>07</code>.

'''%M'''

Трёхзначное значение месяца. Равнозначно тегу <code><mt:ArchiveDate format="%b" /></code> Пример: <code>Sep<code> или <code>Jan</code>.

'''%n'''

Двухзначные минуты, с нулями. Равнозначно тегу <code><mt:ArchiveDate format="%M" /></code>. Пример: <code>04</code>.

'''%p'''

Номер текущей страницы. Равнозначно <code><mt:PagerBlock><mt:IfCurrentPage><mt:Var name="__value__" /></mt:IfCurrentPage></mt:PagerBlock></code>.

'''%s'''

Двухзначные секунды, с нулями. Равнозначно тегу <code><mt:ArchiveDate format="%S" /></code> Пример: <code>01</code>.

'''%x'''

Расширение файла вместе с точкой (.). Равнозначно тегу <code><mt:BlogFileExtension /></code>. Если расширение файла не указано, то будет возвращено пустое значение. Пример: <code>.html</code>.

'''%y'''

Четырёхзначный год. Равнозначно тегу <code><mt:ArchiveDate format="%Y" /></code> Пример: <code>2005</code>.

'''%Y'''

Двухзначный год, с нулями. Равнозначно тегу <code><mt:ArchiveDate format="%y" /></code> Пример: <code>05</code>.


[[Категория:Шаблоны]]
[[Категория:Избранные статьи]]

