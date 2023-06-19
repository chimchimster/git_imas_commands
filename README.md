<h1 align="center">Git и основные команды</h1>

<h3>Оглавление</h3>
<ol>
    <li><a href="#block-1">Создание репозитория</a></li>
    <li><a href="#block-2">Просмотр логов</a></li>
    <li><a href="#block-3">Навигация по веткам</a></li>
    <li><a href="#block-4">Добавление/удаление файлов</a></li>
    <li><a href="#block-5">Отслеживание состояний</a></li>
    <li><a href="#block-6">Запись в репозиторий</a></li>

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
        <code>git switch &lt;name_of_the_branch&gt;</code> или <code>git checkout &lt;name_of_the_branch&gt;</code><br>
    </li>
    <li>
        Создать новую ветку можно с помощью команды <code>git branch -c -r origin/&lt;branch_name&gt;</code>;<br>
    </li>
    <li>
        Удалить remote ветку <code>git branch -d &lt;branch_name&gt;</code>.<br>
        Если вам необходимо удалить также ветку на GitHub/GitLab после удаления remote ветки используйте <code>git push origin :&lt;branch_name&gt;</code>.<br>
        Проверить remote ветки можно с помощью команды <code>git branch -a</code>.
    </li>
</ul>
<br>

<h3 align="center" id="block-4">Добавление/удаление файлов</h3>
<ul>
    <li>
        Добавить файл для отслеживания <code>git add &lt;file_name&gt;</code>;
    </li>
    <li>
        Добавить директорию для отслеживания <code>git add &lt;/dir_name&gt;</code>;
    </li>
    <li>
        Добавить все файлы из директории, в которой вы находитесь <code>git add .</code>;
    </li>
    <li>
        Удалить файлы из отслеживания <code>git reset &lt;file_name&gt;</code>;
    </li>
</ul>
<br>

<h3 align="center" id="block-4">Отслеживание состояний</h3>
<ul>
    <li>
        Текущее состояние <code>git status</code>;
    </li>
    <li>
        Состояние ветки <code>git status -b &lt;branch_name&gt;</code>;
    </li>
</ul>
<br>

<h3 align="center" id="block-4">Запись в репозиторий</h3>
<ul>
    <li>
        Записать все файлы в репозиторий <code>git commit -a -m "commit comment"</code>;
    </li>
    <li>
        
    </li>
</ul>