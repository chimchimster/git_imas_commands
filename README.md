<h1 align="center">Git и основные команды</h1>

<h3>Оглавление</h3>

<h4>Настройки</h4>
<ol>
    <li><a href="#settings-1">Настройка SSH-подключения к GitLab</a></li>
</ol>

<h4>Базовые команды</h4>
<ol>
    <li><a href="#block-1">Создание репозитория</a></li>
    <li><a href="#block-2">Просмотр логов</a></li>
    <li><a href="#block-3">Навигация по веткам</a></li>
    <li><a href="#block-4">Добавление/удаление файлов</a></li>
    <li><a href="#block-5">Отслеживание состояний</a></li>
    <li><a href="#block-6">Запись в репозиторий</a></li>
    <li><a href="#block-7">Восстановление состояний</a></li>
    <li><a href="#block-8">Слияние веток</a></li>
    <li><a href="#block-9">Архивация изменений</a></li>
    <li><a href="#block-10">Система тегов</a></li>
    <li><a href="#block-11">Клонирование репозитория</a></li>
    <li><a href="#block-12">Синхронизация изменений с удаленным сервером</a></li>
</ol>

<h4>Практики внедрения</h4>
<ol>
    <li><a href="#practice-1">Правила ветвления для компании iMAS</a></li>
</ol>


<h3 align="center" id="settings-1">Настройка SSH-подключения к GitLab</h3>
<ul>
    <li>
        Откройте терминал и выполните команду <code>ssh-keygen -t ed25519 -C &lt;your_email&gt;</code>;
    </li>
    <li>
        Пройдите все стадии генерации ключа. Для сохранения ключей используйте директорию по умолчанию <code>/home/user/.ssh/id_ed25519</code>;
    </li>
    <li>
        Перейдите в директорию <code>~/.ssh</code>
    </li>
    <li>
        Выполните команду <code>nano config</code>;
    </li>
    <li>
        Сохраните строки в файл:<br>
        <code>Host gitlab.imas.kz<br>
        &nbsp;&nbsp;&nbsp;&nbsp;PreferredAuthentications publickey<br>
        &nbsp;&nbsp;&nbsp;&nbsp;IdentityFile ~/.ssh/id_ed25519.pub</code>
    </li>
    <li>
        Находясь в дириктории <code>~/.ssh</code> измените права доступа к файлам:<br>
        <code>sudo chmod 600 config</code>;<br>
        <code>sudo chmod 600 id_ed25519</code>;<br>
        <code>sudo chmod 600 id_ed25519.pub</code>;<br>
        <code>sudo chmod 700 known_hosts</code>.
    </li>
    <li>
        Перейдите и авторизуйтесь на <code>gitlab.imas.kz</code>.<br> 
        <code>Ваш профиль</code> -> <code>Edit profile</code> -> в поле <code>SSH Keys</code> вставьте ваш публичный ключ.
        Настройте параметры ключа (title, usage type, expiration date) -> нажмите <code>Add key</code>;
    </li>
    <li>
        Проверьте правильность настройки, выполнив команду:<br>
        <code>ssh -T git@gitlab.imas.kz</code>;
    </li>
    <li>
        Введите фразу, которую вы указывали при генерации ключа.<br>
        Вы должны будете увидеть следующий вывод:<br>
        <code>Welcome to GitLab, @&lt;yourname&gt;</code>
    </li>
    <li>
        Теперь чтобы выполнять команды вам достаточно выполнить команду <code>git remote set-url origin git@gitlab.com:&lt;your_repo&gt;.git</code>;
    </li>
    <li>
        <b>NB!</b> После перезагрузки системы вам необходимо выполнить опреацию <code>ssh-add</code>, чтобы добавить свой ключ. 
        Теперь вы можете вносить изменения в удаленный репозиторий (push, pull и т.д.).
    </li>
</ul>




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
        Удалить файлы из отслеживания <code>git reset HEAD &lt;file_name&gt;</code>;
    </li>
</ul>
<br>

<h3 align="center" id="block-5">Отслеживание состояний</h3>
<ul>
    <li>
        Текущее состояние <code>git status</code>;
    </li>
    <li>
        Состояние ветки <code>git status -b &lt;branch_name&gt;</code>;
    </li>
    <li>
        Отмена изменений в файле (вернуть к состоянию последнего коммита) <code>git checkout -- &lt;filename&gt;</code>. Использовать эту команду с <i><b>осторожностью</b></i>.
    </li>
</ul>
<br>

<h3 align="center" id="block-6">Запись в репозиторий</h3>
<ul>
    <li>
        Записать все файлы в репозиторий с комментарием <code>git commit -am "commit comment"</code>;
    </li>
    <li>
        Наиболее простой способ отменить последний коммит использовать команду <code>git commit --amend</code>;
    </li>
    <li>
        Записать все файлы в репозиторий без комментария <code>git commit -a</code>;<br>
        <i><b>Примечание:</b> система так или иначе предложит оставить комментарий вашего коммита. Предпочтительно использовать первый способ.</i>
    </li>
</ul>
<br>

<h3 align="center" id="block-7">Восстановление состояний</h3>
<ul>
    <li>
        Предположим вы воспользовались командой <code>git rm &lt;file.txt&gt;</code>.<br>
        Вы удалили из дерева файл, но хотите его восстановить. По-хорошему, перед удалением файлов вам необходимо закомититься.<br>
        Состояние возможно восстановить из рабочего дерева коммитов.<br>
        Выполните следующие команды:
        <ol>
            <li><code>git log -p</code> - просмотрите логи и найдите тот коммит к которому вы хотите вернуться. Скопируйте hash вашего коммита.</li>
            <li><code>git restore --source=&lt;commit hash&gt; &lt;filename&gt;</code></li>
        </ol>
    </li>
</ul>
<br>

<h3 align="center" id="block-8">Слияние веток</h3>
<ul>
    <li>
        Предположим у вас имеется дерево:<br>
        &nbsp; &nbsp; &nbsp; &nbsp; A - B - C topic<br>
        &nbsp; &nbsp; &nbsp; &nbsp; /<br>
        D - E - F - G master
    </li>
    <li>
        Если вы выполните команду <code>git merge topic</code>. Результат будет следующий:<br>
        &nbsp; &nbsp; &nbsp; &nbsp; A - B - C topic<br>
        &nbsp; &nbsp; &nbsp; &nbsp; / &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;\<br>
        D - E - F - G - H master
    </li>
    <li>
        <i><b>Примечание:</b> если вы хотите вернуть прежнее состояние используйте команду <code>git merge --abort</code></i>
    </li>
</ul>

<h4 align=center>Пример слияния</h2>
<p>Предположим мы находимся в ветке main нашего репозитория.</p>
<p>Проверим это используя команду <code>git branch -l</code>.</p>
<p><img src="https://github.com/chimchimster/git_imas_commands/blob/main/media/git_branch1.png" alt="git branch -l"></p>
<p>Внутри репозитория находится файл <a href="https://github.com/chimchimster/git_imas_commands/blob/main/text.txt">text.txt</a>. В котором содержится следующая информация:</p>
<p><img src="https://github.com/chimchimster/git_imas_commands/blob/main/media/git_branch2.png" alt="New Bourne! Shell -> THIS IS MAIN"></p>
<p>Теперь сменим ветку на new_branch с помощью команды <code>git checkout new_branch</code>.</p>
<p><img src="https://github.com/chimchimster/git_imas_commands/blob/main/media/git_branch3.png" alt="git checkout new_branch"></p>
<p>Как видите в том же файле text.txt содержится иная информация. Это приведет к возникновению <b>конфликта</b> во время слияния.</p>
<p><img src="https://github.com/chimchimster/git_imas_commands/blob/main/media/git_branch4.png" alt="New Bourne! Shell -> THIS IS NEW_BRANCH"></p>
<p>Давайте попробуем использовать команду, которая соеденит наши репозитории main и new_branch.</p>
<p>Выполним команду <code>git merge main</code>.</p>
<p><img src="https://github.com/chimchimster/git_imas_commands/blob/main/media/git_branch5.png" alt="git checkout new_branch"></p>
<p>Как видите мы получили ожидаемую ошибку слияния веток. Дело в том, что файлы text.txt перед слиянием различались.</p>
<p>Теперь система контроля версий предлагает нам вручную разрешить конфликты:</p>
<p><img src="https://github.com/chimchimster/git_imas_commands/blob/main/media/git_branch6.png" alt="конфликты в файле text.txt"></p>
<p>Git сгенерировал новые данные. Символы <<<<<<< указывают на ветку, а разделители ======== отделяют код одной ветки от другой.</p>
<p>Удалите ненужный код и выполните коммит <code>git commit -am "your comment"</code>.</p>
<p>Поздравляю! Вы только что выполнили слияние веток.</p>

<br>

<h3 align="center" id="block-9">Архивация изменений</h3>
<ul>
    <li>
        Если вы хотите заархивировать изменения в рабочей ветке и пока что не готовы делать коммиты воспользуйтесь командой <code>git stash</code>.
    </li>
    <li>
        Теперь вы можете использовать все доступные команды git: делать коммиты, перемещаться по веткам и т.д.
    </li>
    <li>
        Как только вы готовы применить архивные изменения используйте команду <code>git stash pop</code>, если вы хотите очистить архив, в противном случае воспользуйтесь <code>git stash apply</code>.
    </li>
</ul>
<br>

<h3 align="center" id="block-10">Система тегов</h3>
<ul>
    <li>
        Система тегов позволяет сохранять состояние определенных версий.
        Всего существует два вида тегов - <i>аннотированные</i> и <i>легковесные</i>;
    </li>
    <li>
        Легковесный тег - это обычный указатель на коммит. 
        Аннотированные теги - это полноценный объект хранящийся в базе данных.
    </li>
    <li>
        Выполните команду <code>git tag -a v1.0 -m "version 1.0"</code>, чтобы создать <i>аннотировнный</i> тег;
    </li>
    <li>
        Выполните команду <code>git tag v1.0-lw</code>, чтобы создать <i>легковесный</i> тег.
    </li>
    <li>
        Чтобы посмотреть все существующие теги выполните команду <code>git tag</code>;
    </li>
    <li>
        Чтобы посмотреть данные по определенному тегу используйте <code>git show v1.0</code>;
    </li>
    <li>
        По умолчанию теги не отправляются в репозиторий вместе с командой git push.
        Поэтому их нужно отправлять явно: <code>git push origin v1.0</code>.
        Если тегов много то воспользуйтесь командой <code>git push origin --tags</code>.
    </li>
    <li>
        Удалить тег можно с помощью команды <code>git tag -d v1.0</code>. 
        При этом тег не удаляется из внешнего репозитория. 
        Чтобы удалить тег из внешнего репозитория используйте команду <code>git push origin --delete v1.0</code>
    </li>
    <li>
        Перейти на нужный вам тег можно с помощью команды <code>git checkout v1.0</code>.
    </li>
    <li>
        При переходе на тег лучше всего сразу создавать новую ветку <code>git checkout -b version1 v1.0</code>
    </li>
</ul>
<br>

<h3 align="center" id="block-11">Клонирование репозитория</h3>
<ul>
    <li>
        Команда <code>git clone git@gitlab.imas.kz:&lt;your_account&gt;/&lt;some_project&gt;.git</code>
        склонирует <code>remote (удаленный)</code> репозиторий в дерикторию из которой вы выполняете команду;
    </li>
    <li>Склонировать репозиторий так, чтобы HEAD указывала на новую ветку 
    <code>git clone -b &lt;branch_name&gt; git@gitlab.imas.kz:&lt;your_account&gt;/&lt;some_project&gt;.git</code>.</li>
</ul>
<br>

<h3 align="center" id="block-12">Синхронизация изменений с удаленным сервером</h3>
<ul>
    <li>
        Чтобы синхронизировать изменения с удаленным сервером (origin, remote) используйте команду <code>git fetch origin или remote</code>.
    </li>
    <li>
        После выполнения данной команды те ветки, которые по каким бы то ни было причинам не были добавлены в ваш репозиторий, 
        будут добавлены в ваш локальный репозиторий.
    </li>
</ul>
<br>

<h3 align="center" id="practice-1">Правила ветвления для компании iMAS.</h3>
<ol>
    <li>
        Стабильный код должен находится в ветке <code>master</code>; 
    </li>
    <li>
        Параллельные ветки должны называться &lt;feature_name&gt;_&lt;developer_name&gt;;
    </li>
    <li>
        Прежде чем произвести слияние параллельных веток в основную, создается ветка &lt;project_name&gt;_&lt;test&gt;;
        Все изменения в порядке очереди сливаются в тестовую ветку. На данном этапе проект тестируется.
    </li>
    <li>
        Если все благополучно протестировано, тестовая ветка сливается с <code>master</code> и код деплоится.
    </li>
</ol>