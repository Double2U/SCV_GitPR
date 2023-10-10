![Logo](Git-Logo-2Color.png)
# Работа с Git

## 1.Проверка наличия установленного Git
В терминале выполнить команду `git --version`
Если Git установлен появится сообщение с информацией о версии программы, иначе будет сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию Git с [сайта](https://git-scm.com/downloads).
Устанавливаем с настройками по умолчанию.

## 3. Настройка Git 
При первом использовании Git необходимо представиться.
Для этого нужно ввести в терминале 2 команды:
```
git config --global user.name «Ваше имя английскими буквами»
git config --global user.email ваша почта@example.com
```

## 4. Инициализация репозитория
Чтобы Git начал отслеживать изменения файлов необходимо инициализировать репозиторий. Для этого создаем папку, где будут храниться репозитории и переходим в неё. В терминале вводим команду `git init`. 

## 5. Запись изменений в репозиторий
Запись изменений в репозиторий выполняется при помощи нескольких команд. Для начала необходимо сохранить изменения, это можно сделать с помощью сочетания клавиш *CTRL + S* или автосохранения (Файл -> автосохранение).
### Отображение разницы между текущим файлом и закоммиченным (сохраненным)
Разницу между текущим файлом и закоммиченным можно увидеть с помощью команды 
```
git diff
```

Git выведет примерное сообщение в терминале:

![команда git diff](GitDiff.PNG)

Знак (-) означает удаление строки или изменение строки. Знак (+) означает добавление строки.

### Отображение состояния репозитория

Для того, чтобы посмотреть состояние репозитория необходимо в терминале ввести команду `git status`. Git выведет сообщение в котором указано:
* В какой ветке мы находимся
* Есть ли изменения и добавлены ли они к следующему коммиту(сохранению)
* Какой файл изменён

Выглядит это следующим образом:

![команда git status](GitStatus.PNG)

Красная строка указывает на то, что файл изменен и не добавлены изменения к фиксации или файл не добавлен к следующему коммиту. После того, как будут добавлены изменения к фиксации и заново введена команда `git status` строка с названием файла будет отображаться зеленым цветом.

![команда git status](GitStatus2.PNG)

### Добавление изменений к фиксации (к следующему коммиту)
Добавление изменений к фиксации выполняется с помощью команды:
```
git add <название файла>
```
### Фиксация изменений (создание коммита)


Зафиксировать изменения можно командой:
```
git commit -m "Комментарий"
```
Комментарий может быть любой длины.
 
 ## 6. Просмотр истории коммитов
 Чтобы посмотреть истории всех коммитов необходимо ввести в терминале команду: 
 ```
 git log 
 ```
![команда git log](GitLog.PNG)

Можно посмотреть сокращенный вариант всех коммитов при помощи команды:
```
git log --oneline
```
![команда git log --oneline](GitLogOneline.PNG)

 ## 7. Перемещение между сохранениями (коммитами)
 Перемещение между сохранениями(коммитами) осуществляется командой:
 ```
 git checkout <хэш-код коммита>
 ```
Необязательно указывать весь хеш-код, достаточно первых 4-6 символов.
Чтобы вернуться к актуальному состоянию и продолжить работу необходимо в терминале ввести команду:
```
git checkout master
```
 ## 8. Игнорирование файлов
 Для того, чтобы исключить из отслеживания в репозитории определённые файлы или папки необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны, соответствующие таким файлам или папкам. Для того, чтобы каждый раз не вписывать названия файлов, которые хотим игнорировать, используются шаблоны. Например, **\*.png**. Данная запись означает, что файлы с форматом **png** будут игнорированы.

 ## 9. Создание веток в Git
 По умолчанию имя основной ветки в Git - **master**.
 Создать ветку можно командой:
 ```
 git branch <имя новой ветки>
 ```
 Список веток в репозитории можно посмотреть с помощью команды `git branch`. Текущая ветка будет отмечена звёздочкой: **\* master**.

## 10. Слияние веток и разрешение конфликтов
Чтобы слить ветки необходимо cначала переместиться на основную ветку (*master*) и в терминале ввести команду:
```
git merge <название ветки,которую хотим слить>
```
При слиянии веток может произойти конфликт. Он может возникнуть, когда происходят изменения одних и те же строк. В этом случае Git помечает файл как конфликтующий и останавливает процесс слияния. После этого Visual Code предлагает на выбор три варианта:
1. Принять текущее изменение
2. Принять входящее изменение
3. Принять оба изменения


![solvedConflict](solvedConflict.PNG)
После разрешения конфликта необходимо сделать коммит слияния командой `git commit`.
## 11. Удаление веток
Удалить ветку можно командой:
```
git branch -d <название ветки>
```
Git не позволит удалить ветку, над которой в данный момент выполняется работа. Поэтому необходимо переключиться на ветку, которая не удаляется.
Опция -d удалит ветку, только если она была объединена с другой.
Если необходимо принудительно удалить ветку, можно воспользоваться опцией -D. Полная команда:
```
git branch -D <название ветки>
```
## 12. Работа с удалёнными репозиториями
### Добавление удаленного репозитория к существующему локальному
Чтобы добавить удаленный репозиторий к  локальному репозиторию необходимо ввести команду:
```
git remote add  <название удаленного репозитория> <ссылка на удаленный репозиторий>
``` 
Имя удаленного репозитория в команде git remote add можно придумать самому. Впоследствии, при работе с этим удаленным репозиторием, можно будет обращаться к нему по придуманному имени. Принято называть удаленный репозиторий origin, но строго говоря, никаких ограничений здесь нет.

Со ссылкой на удаленный репозиторий тоже все просто. Ссылку можно взять, нажав на большую зеленую кнопку **Code** на странице репозитория на GitHub.
![urlGithub](urlGithub.PNG)

### Отключение удаленного репозитория от локального
Отключить (забыть) удаленный репозиторий можно командой:
```
git remote remove  <название удаленного репозитория>
```
Данная команда не удаляет удаленный репозиторий с сервера, она удаляет только подключение репозитория к удаленному.
### Изменение имени удаленного репозитория
Чтобы переименовать удаленный репозиторий нужно ввести команду:
```
git remote rename <старое имя удаленного репозитория> <новое имя удаленного репозитория>
```
### Просмотр всех удаленных репозиториев
Просмотреть список всех подключенных удаленных репозиториев и получить информацию о каждом из них позволяет команда:
```
git remote show [имя удаленного репозитория]
``` 
Если передано имя репозитория, то выводит информацию об этом репозитории.

### Клонирование удаленного репозитория
Операция клонирования создаёт на вашем компьютере точную копию удаленного репозитория. 
Необходимость клонировать существующий удаленный репозиторий возникает в ситуациях, когда нужно поработать над уже существующим кодом. Для выполнения этой операции в Git предусмотрена команда:
```
git clone <ссылка на удаленный репозиторий>
``` 
Ссылку на удаленный репозиторий можно получить тем же способом, который разбирался выше. Нужно нажать на зеленую кнопку **Code** на главной странице репозитория на GitHub.

При выполнении команды git сlone [ссылка на репозиторий](https://github.com/Double2U/Test.git) произойдет следующее:

1. В директории, откуда вы запустили команду git clone, создается директория с именем репозитория.
2. В созданную директорию копируется репозиторий, все его ветки и коммиты.
3. В новосозданный локальный репозиторий добавляется удаленный репозиторий с именем origin и ссылкой, которую передалась в git clone. Это избавляет от необходимости вручную писать `git remote add origin https://github.com/Double2U/Test.git`. 

 На этом процесс клонирования заканчивается.

 ### Отправка изменений в удалённый репозиторий
 Когда есть необходимость поделиться своими наработками, необходимо отправить их в удалённый репозиторий. Для этого существует команда: 
 ```
 git push [имя удаленного репозитория] [имя ветки]
 ```

Эта команда срабатывает только в случае, если вы клонировали с сервера, на котором у вас есть права на запись, и если никто другой с тех пор не выполнял команду *push*. Если вы и кто-то ещё одновременно клонируете, затем он выполняет команду *push*, а после него выполнить команду *push* попытаетесь вы, то ваш push точно будет отклонён. Вам придётся сначала получить изменения и объединить их с вашими и только после этого вам можно будет выполнить *push*.

Если команда `git push` была введена впервые, то Git попросит авторизоваться. Для этого необходимо иметь аккаунт на GitHub.

### Получение изменений из удаленного репозитория
Если ветка настроена на отслеживание удалённой ветки, то можно использовать команду:
```
git pull [имя удаленного репозитория]
```  
Выполнение команды `git pull`, как правило, извлекает данные с сервера, с которого изначально клонировался репозиторий, и автоматически пытается слить их с кодом, над которым в данный момент выполняется работа.
### Создание форка репозитория на GitHub. Пулл-реквесты.

**Форк** (от англ. fork – вилка) – точная копия репозитория, но в своём аккаунте. Форки нужны, чтобы вносить свои изменения в проект, к репозиторию которого нет прямого доступа.

**Пулл-реквест** (от англ. pull-request – запрос pull) – функция GitHub, позволяющая попросить владельца репозитория, от которого пользователь сделал форк, загрузить пользовательские изменения обратно в репозиторий владельца.
Если коротко, форки и пулл-реквесты нужны, чтобы любой пользователь мог внести свой вклад в любой открытый проект, репозиторий которого есть на GitHub. Кроме того, перед тем как влить ваши изменения в основной репозиторий, ответственные обязательно проверят ваш код на наличие ошибок и уязвимостей. Таким образом, даже если ваши изменения не примут, вы получите комментарий с указанием всех неточностей.

Рассмотрим пример:

1. Для начала необходимо зайти на страницу репозитория проекта. Нажать на кнопку Fork. После этого Git создаст точную копию этого репозитория в вашем аккаунте.
2. Клонировать репозиторий на локальный компьютер командой `git clone` и создать новую ветку.

3. Добавить файл или внести изменения, и сделать коммит. После этого выполнить команду `git push` , чтобы загрузить изменения в удаленный репозиторий.

4. Нажать на кнопку Compare на подсказке GitHub, либо перейти на вкладку **Pull Requests** и нажать **New pull request**.
5. Откроется страница создания пулл-реквеста.
Здесь можно просмотреть внесенные изменения и выбрать две ветки: одну в исходном репозитории, на нее будут залиты наши изменения, вторую – в нашем репозитории, с нее будут скачаны изменения. Как только мы выбрали ветки и убедились, что не внесли никаких лишних изменений, нажимаем кнопку ***Create pull request***.

6. Откроется страница описания наших изменений. Здесь необходимо описать, что за изменения были внесены и почему они были необходимы. Сообщение, которое будет оставлено, видно на картинке. Оно отражает суть и необходимость внесенных изменений. Как только описание будет закончено, можно нажимать кнопку **Create pull request**.
7. Откроется страница уже созданного пулл-реквеста в изначальном репозитории. На этой странице владелец сможет писать комментарии, указывая на ошибки или задавая вопросы. После того, как владелец репозитория просмотрит наши изменения и убедится, что они не имеют вредоносный характер, он сможет принять наш пулл-реквест. Тогда все изменения, добавленные в этот пулл-реквест нами, будут залиты в исходный репозиторий.