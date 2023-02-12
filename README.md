<h2>pgAdmin для начинающих</h2>

Примечание: ЛКМ, ПКМ - левая, правая кнопка мыши</br>

Разделы: </br>
<a href="#01">01 Установка PostgreSQL и PgAdmin</a></br>
<a href="#02">02 Создание базы данных в правильной кодировке</a></br>
<a href="#03">03 Создание таблиц в pgAdmin</a></br>
<a href="#04">04 Создание столбцов</a></br>
<a href="#05">05 PgAdmin первичный ключ в PostgreSQL</a></br>
<a href="#06">06 Создание базовых колонок</a></br>
<a href="#07">07 Код таблицы DDL в PostgreSQL</a></br>

<a name="01"></a>
**01 Установка PostgreSQL и PgAdmin** - https://www.postgresql.org/download/ </br>
Вместе с PostgreSQL уставливается и PgAdmin </br>
Во время установки задаем пароль суперпользователя (мастер-пароль) базы данных.</br>
Locale - English, United States</br>
Проверить установку PostgreSQL можно так: в Windows находим Службы и в них </br>
проверяем наличие службы PostgreSQL

<details>
<summary>Служба_PostgreSQL.png</summary>
<img src="info/01_Установка_PostgreSQL/Служба_PostgreSQL.png"/> 
</details>

После установки PgAdmin появляется в меню </br> 
Пуск>Все программы>PostgreSQL(N) </br>
При запуске программы нужно указать мастер-пароль, который 
вы указывали при установке. </br>
Также этот пароль понадобится при заходе в базу данных.</br>

Проверка кодировки </br>
Открываем Database > ПКМ на postgres > Properties > Definition</br>
Параметр Encoding = UTF8 </br>
Важно обратить внимание на этот параметр и именно поэтому
мы выбирали локаль <br/> 
Locale - English, United States <br/>
Если у вас кодировка UTF-8, то у вас будет меньше проблем
с экспортом и импортом данных

<details>
<summary>Проверка_кодировки.png</summary>
<img src="info/01_Установка_PostgreSQL/Проверка_кодировки.png"/> 
</details>
<hr/>

<a name="02"></a>
**02 Создание базы данных в правильной кодировке**<br/>
Если кодировка вашей системы отличается от UTF-8
вы все равно сможете создать свою базу c UTF-8
ПКМ На Databases > Create > Database </br>
Во вкладке Definition можно вручную выбрать </br>
Encoding - UTF - 8 </br>
Иногда система может потребовать использовать шаблон template0, 
тогда его вы тоже можете выбрать в этой вкладке
<details>
<summary>База_данных_в_ UTF-8.png</summary>
<img src="info/02_База данных_в_UTF-8/База_данных_в_ UTF-8.png"/> 
</details>
Также вам может потребоваться перенести все ваши таблицы
из старой базы в новую, это вы можете сделать через меню
Tools в верхней части программы - комады Backup и Restore
<hr/>

<a name="03"></a>
**03 Создание таблиц в pgAdmin**<br/>
На примере базы данных postgres находим Tables, <br/>
ПКМ > Create > Table <br/>
<details>
<summary>Создать_таблицу.png</summary>
<img src="info/03_Создание_таблиц_в_pgAdmin/Создать_таблицу.png"/> 
</details>
Задаем название таблицы, эти названия не должны 
пересекаться с ключевыми словами баз данных, иначе могут быть 
неожиданности, Owner - postgres, в комментариях указываем 
назначение таблицы и другую полезную информацию. 
Если после создания таблица не отобразилась в списке Tables, 
можно обновить данные <br/> 
ПКМ на Tables > Refresh <br/>
Для примера создадим несколько таблиц:<br/>
category, priority, task, user_data
<hr/>

<a name="04"></a>
**04 Создание столбцов**<br/>
Создать столбцы можно двумя способами,<br/>
Кликаем на таблицу ПКМ > Properties > Columns<br/>
(можно создать сразу несколько колонок) или <br/>
Кликаем на таблицу ПКМ > Create > Column<br/>
(создаем по одной колонке)<br/>
<details>
<summary>Создать_колонки.png</summary>
<img src="info/04_Создание_столбцов/Создать_колонки.png"/> 
</details>

Добавим следующие колонки в таблицу user_data:<br/>
почта - обязательное значение<br/>
пароль - обязательное значение<br/>
имя - обязательное значение <br/>
<details>
<summary>Колонки_для_userdata.png</summary>
<img src="info/04_Создание_столбцов/Колонки_для_userdata.png"/> 
</details>
После сохранения колонок можно сделать <br/>
ПКМ на таблице > Refresh <br/>
и увидеть наши колонки, развернув таблицу и подраздел 
Columns. <br/>
Для редактирования колонок в дальнейшем 
мы точно также делаем:<br/>
ПКМ на таблице > Properties > Columns<br/>
и в окне, где показаны все столбцы кликаем на значок
редактирования слева от нужного столбца.
<hr/>

<a name="05"></a>
**05 PgAdmin - первичный ключ в PostgreSQL**<br/>
В таблице user_data создаем новое поле id типа bigint<br/>
(аналог long а Джава). Добавляем полю параметр Not Null и
primary key. <br/>
<details>
<summary>id_первичный_ключ.png</summary>
<img src="info/05_Первичный_ключ_в_PostgreSQL/id_первичный_ключ.png"/> 
</details>
Когда мы накладываем ограничение Primary key
в поле id мы можем сохранять только уникальные значния.
Все остальные поля в строке могут быть одинаковыми,
важно, чтобы id был разный. Столбец с Primary key 
чаще всего обозначается PK<br/>
<details>
<summary>id_разный.png</summary>
<img src="info/05_Первичный_ключ_в_PostgreSQL/id_разный.png"/> 
</details>
<hr/>

<a name="06"></a>
**06 Создание базовых колонок**<br/>
Заполните колонками таблицу task:<br/>
title - text - not null<br/>
completed - numeric - not null <br/>
task_date - timestamp without time zone <br/>
id - bigint - not null - Primary key <br/><br/>

Увидеть результат создания можно так:<br/>
Делаем Refresh, через ПКМ на таблице > Refresh <br/>
и разворачиваваем таблицу ЛКМ до колонок <br/>

<details>
<summary>Вид_колонок.png</summary>
<img src="info/06_Создание_базовых_колонок/Вид_колонок.png"/> 
</details>

Заполните столбцами таблицу priority: <br/>
title - text - not null<br/>
color - text - not null<br/>
id - bigint - not null - primary key<br/><br/>

Заполните столбцами таблицу category: <br/>
title - text - not null<br/>
id - bigint - not null - primary key<br/>
<hr/>

<a name="07"></a>
**07 Код таблицы DDL в PostgreSQL**<br/>
Мы создали таблицы в pgAdmin средствами самой программы,
вводя в поля нужные значения и использую переключатели.
Тоже самое можно сделать с помощью <br/>
DDL – Data Definition Language (язык описания данных)<br/>
Это так называемый SQL запрос для создания таблицы.
Мы можем посмотреть этот код (в режиме чтения), выбрав слева 
нужную таблицу, а справа, соотвестствующую вкладку. 
В дальнейшем вам нужно научиться создавать таблицы и тем
и другим способом
<details>
<summary>Код_создания_таблицы.png</summary>
<img src="info/07_Код_таблицы_DDL_в_PostgreSQL/Код_создания_таблицы.png"/> 
</details>
