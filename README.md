<h2>pgAdmin базовые возможности</h2>

Примечание: ПКМ, ЛКМ - правая и левая кнопка мыши

**01 Установка PostgreSQL и PgAdmin** - https://www.postgresql.org/download/ </br>
Вместе с PostgreSQL уставливается и PgAdmin </br>
Во время установки задаем пароль суперпользователя (мастер-пароль) базы данных.</br>
Locale - English, United States</br>
Проверить установку PostgreSQL можно так: в Windows находим Службы и в них </br>
проверяем наличие службы PostgreSQL

<details>
<summary>01_Служба_PostgreSQL.png</summary>
<img src="01_Установка_PostgreSQL/01_Служба_PostgreSQL.png"/> 
</details>

После установки PgAdmin появляется в меню </br> 
Пуск>Все программы>PostgreSQL(N) </br>
При запуске программы нужно указать мастер пароль, который вы укзывали
при установке. </br>
Также этот пароль понадобится при заходе в базу данных.</br>

Проверка кодировки </br>
Открываем Database > ПКМ на postgres > Properties > Definition
Параметр Encoding = UTF8
Важно обратить внимание на этот параметр и именно поэтому
мы выбирали локаль Locale - English, United States

<details>
<summary>01_Служба_PostgreSQL.png</summary>
<img src="01_Установка_PostgreSQL/02_Проверка_кодировки.png"/> 
</details>
<hr/>