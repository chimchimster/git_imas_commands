<h1 align="center">Git и основные команды</h1>

<h3>Оглавление</h3>
<ol>
    <li><a href="#block-1">Создание репозитория</a></li>
    <li><a href="#block-2">Просмотр логов</a></li>
    <li><a href="#block-3">Навигация по веткам</a></li>

</ol>

<h3 align="center" id="block-1">Создание репозитория</h3>

<ul>
    <li>
    Чтобы создать новый репозиторий или переинициализировать существующий выполните команду:
    <code>git init</code>.<br> <i><b>Примечаение:</b> использование команды с уже существующим репозиторием не перезапишет существующие данные.</i> 
    </li>
</ul>
<br>

<h3 align="center" id="block-2">Просмотр логов</h3>

<ul>
    <li>
    Узнать логи по коммитам: <code>git log</code>.
    Используйте <code>space</code>, чтобы перемещаться по уже существующим коммитам.
    Для выхода нажмите <code>q</code>;<br>
    </li>
    <li>
    Узнать логи по коммитам отдельных веток: <code>git log &lt;branch1&gt; &lt;branch2&gt;</code>;<br>
    Исключить логи по ветке branch2: <code>git log &lt;branch1&gt; ^&lt;branch2&gt;</code>.
    </li>
</ul>
<br>

<h3 align="center" id="block-3">Навигация по веткам</h3>

<ul id="block-3">
    <li>
        Узнать текущую ветку можно с помощью команды: <code>git branch</code>;
    </li>
    <li>
        Чтобы сменить текущую ветку используйте команду или 
        <code>git switch &lt;name_of_the_branch&gt;&lt;name_of_the_branch&gt;</code>;<br>
    </li>
    <li>
        Создать новую ветку можно с помощью команды <code>git branch -c &lt;new_branch_name&gt;</code>;<br>
    </li>
    <li>
        <i><b>Примечание:</b> Если вы хотите произвести слияние веток используйте: <code>git branch --merge &lt;branch1&gt; &lt;branch2&gt;</code>
        </i>
    </li>
</ul>


