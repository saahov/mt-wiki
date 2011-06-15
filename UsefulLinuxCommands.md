{{TOCright}}
Для некоторых задач Movable Type могут потребоваться навыки работы с командной строкой Linux. Это очень просто, достаточно знать основные команды, которые понимает Linux-сервер.

Взаимодействие с сервером происходит по протоколу [http://ru.wikipedia.org/wiki/SSH SSH], поэтому, если вы работаете в ОС Windows, вам необходимо будет установить программу для работы с SSH (в Linux и Mac OS ничего дополнительно устанавливать не требуется):

* [http://www.chiark.greenend.org.uk/~sgtatham/putty/ PuTTY] ([http://putty.org.ru/ русскоязычный сайт PuTTY]) — бесплатная программа для работы с SSH, не требующая установки.
* [http://www.extraputty.com/ ExtraPuTTY] — расширенная версия PuTTY.
* [http://www.vandyke.com/products/securecrt/ SecureCRT] — мощная программа для работы по SSH (поддерживающая многие другие протоколы).


== Архивация/Разархивация ==

Создание tar.gz-архива:
<source lang="bash">tar czf имя-архива.tar.gz имя-папки</source>

Распаковка tar.gz-архива:
<source lang="bash">tar xzf имя-архива.tar.gz</source>

Создание tar.bz2-архива:
<source lang="bash">tar cjf имя-архива.tar.bz2 имя-папки</source>

Распаковка tar.bz2-архива:
<source lang="bash">tar xjf имя-архива.tar.bz2</source>

Распаковка rar-архива:
<source lang="bash">unrar x имя-архива.rar</source>

== Работа с файлами и папками ==

Список файлов и папок:
<source lang="bash">ls</source>

Полный список файлов и папок, включая скрытые:
<source lang="bash">ls -a</source>

Сменить директорию:
<source lang="bash">cd имя-каталога</source>
Примеры использования:
* <code>cd /</code> — переход в корневую директорию диска;
* <code>cd ..</code> — переход на один уровень выше;
* <code>cd ../..</code> — переход на 2 уровня вверх;
* <code>cd $HOME</code> — переход в домашнюю директорию (достаточно набрать просто <code>cd</code>);
* <code>cd /home/имя-папки/имя-подпапки</code> — переход в указанную папку.

Создание папки:
<source lang="bash">mkdir имя-папки</source>

Удаление файла или папки:
<source lang="bash">rm имя-файла</source>

Удаление файлов и папок рекурсивно (включая все вложенные файлы и папки):
<source lang="bash">rm -r имя-папки</source>

Скопировать файл:
<source lang="bash">cp имя-файла имя-копии-файла</source>

Скопировать папку:
<source lang="bash">cp -r имя-папки имя-копии-папки</source>

Переименовать файл:
<source lang="bash">mv имя-файла новое-имя-файла</source>
Если «новое-имя-файла» — это папка, то файл будет перемещён в эту папку.

Создать символическую ссылку:
<source lang="bash">ln -s имя-файла имя-ссылки</source>

Изменение прав доступа (CHMOD) у файла или папки:
<source lang="bash">chmod 755 имя-папки</source>

Изменение прав доступа (CHMOD) у всех файлов рекурсивно:
<source lang="bash">find . -type f | xargs chmod 644</source>

Изменение прав доступа (CHMOD) у всех файлов с определённым расширением рекурсивно:
<source lang="bash">find . -name '*.cgi' -type f | xargs chmod 755</source>

Изменение прав доступа (CHMOD) у папок рекурсивно:
<source lang="bash">find . -type d | xargs chmod 755</source>

== Бэкап базы данных ==

Бекап базы данных с помощью mysqldump (команда должна быть в одной сроке):

<source lang="bash">mysqldump --user=ПОЛЬЗОВАТЕЛЬ --host=ХОСТ -acnqQ --single-transaction --default-character-set=КОДИРОВКА --password=ПАРОЛЬ -- БАЗА_ДАННЫХ | sed "s#^CREATE TABLE#\0 IF NOT EXISTS# ; s#^INSERT INTO#REPLACE INTO#" | gzip -qf9c > /home/username/путь-где-будут-храниться-бэкапы/имя-базы-данных-`date +%Y-%m-%d`.sql.gz</source>

Пример кодировки: <code>cp1251</code>, <code>utf8</code>.

== Работа с Perl ==

Выполнение Perl-скрипта:
<source lang="bash">perl имя-скрипта.cgi</source>

Установка модулей Perl через CPAN:
<source lang="bash">install ИМЯ::МОДУЛЯ</source>
Перед выполнением этой команды необходимо войти в CPAN, выполнив следующую команду:
<source lang="bash">perl -MCPAN -e "shell"</source>

== Другие полезные команды ==

Закачать файл на сервер:
<source lang="bash">wget http://example.com/filename.zip</source>

Список процессов:
<source lang="bash">top</source>

Список процессов определённого пользователя:
<source lang="bash">top -u имя-пользователя</source>

Текущая дата:
<source lang="bash">date</source>

Сменить пароль:
<source lang="bash">passwd</source>

Сменить пароль у определённого пользователя:
<source lang="bash">passwd имя-пользователя</source>

Показать информацию и ядре:
<source lang="bash">uname -a</source>

Показать информацию о CPU:
<source lang="bash">cat /proc/cpuinfo</source>

Показать информацию о памяти:
<source lang="bash">cat /proc/meminfo</source>

Показать информацию об использовании дисков:
<source lang="bash">df</source>

Перезапустить какой-нибудь сервис:
<source lang="bash">/etc/init.d/имя-сервиса команда</source>
Например: <code>/etc/init.d/apache2 restart</code>

Информация об использовании памяти и swap:
<source lang="bash">free</source>

Возможное расположение приложения:
<source lang="bash">whereis имя-приложения</source>
Например: <code>whereis apache2</code>

Перезагрузить сервер (полная перезагрузка):
<source lang="bash">reboot</source>

== Клавиатурные сочетания ==

* <code>Ctrl+C</code> — завершить текущую команду.
* <code>Ctrl+D</code> — разлогиниться (аналогично exit).
* <code>Ctrl+W</code> — удалить одно слово в текущей строке.
* <code>Ctrl+U</code> — удалить строку.
* <code>!!</code> — повторить последнюю команду.
* <code>exit</code> — разлогиниться.

== Другие списки Linux-команд ==

* [http://gluek.info/wiki/linux/usefulshellcommands Команды на Gluek's Wiki]
* [http://www.linuxsoft.ru/lib/articles/ar1921/index.php Большой список команд на Linux SoftWare Library]
* [http://www.debian-administration.org/articles/438 A couple of tricks with the secure shell] {{ref-en}} — Различные трюки работы с SSH
* [http://commandlinefu.com commandlinefu.com] {{ref-en}} — Сборник команд Linux
* [http://www.shell-fu.org/ shell-fu] {{ref-en}} — Ещё один сборник команд
* [http://ru.wikipedia.org/wiki/Программы_UNIX-подобных_операционных_систем Программы UNIX-подобных операционных систем] — сборник команд в Википедии.

== Авторы этой статьи ==

* [[Служебная:Contributors/Полезные команды Linux]]

[[Категория:Работа с Movable Type]]
[[Категория:Гид администратора]]
[[Категория:Избранные статьи]]

