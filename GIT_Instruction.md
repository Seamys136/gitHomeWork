# Инструкция работы с Git

## Что такое Git?
**Git** - это специальная программа, которая позволяет отслеживать любые изменения в файлах, хранить их версии и оперативно возвращаться в любое сохранённое состояние.

Git может быть **локальным**, **централизованным** или **распределённым**:

* __Локальный__ установлен на одном компьютере и хранит файлы только в одном экземпляре в рамках настроенного окружения — подходит, если программист пишет код в одиночку.
* __Централизованный__ находится на общем севере и хранит все файлы на нем.
* __Распределённый__ хранит данные и в общем облачном хранилище, и в устройствах участников команды.

## Основные команды Git

#### Создание нового репозитория
Создать новый репозиторий поможет команда:
>**git init**

В рамках нового проекта эта команда выполняется обычно первой, потому что большинство остальных команд Git невозможно использовать без инициализации репозитория.

#### Текущее состояние
Получить информацию от **git** о его текущем состоянии можнол с помощью команды:

>**git status**

Эта команда отображает состояние рабочего каталога и раздела проиндексированных файлов. С ее помощью можно проверить изменения и увидеть файлы, которые не отслеживаются. Используй эту команду чаще.

#### Добавление файла
Если нам нужно, чтобы шёл контроль версий файлов и программа **Git** их контролировала, то нужно добавить эти файлы как отслеживаемые.
Для этого существует команда:

>**git add** <Имя_файла>

Она сообщает **Git**, что вы хотите включить изменения в конкретном файле в следующий коммит. Однако на самом деле эта команда не оказывает существенного влияния на репозиторий: изменения регистрируются в нем только после выполнения команды __*git commit*__, информация о которой см. ниже.

#### Создание коммита

Чтобы зафиксировать изменения, используй команду:
>**git commit**

Чтобы понимать, какое именно изменение было внесено, нужно добавить комментарий. Делается это так:

>**git commit -m** 'Информация/комментарий о внесенном изменении'

**Примечание:**
У нас есть какой-то файл, в который мы вносим изменения. Чтобы зафиксировать их, нужно сначала использовать команду __*git add*__, а потом команду __*git commit*__.
Однако, если файл уже отслеживается, то можно использовать команду, которая совмещает эти две команды:
>**git commit -am** 'Информация/комментарий о внесенном изменении' 

Выполни команду __*git status*__, чтобы удедиться, что изменения сохранены.
О том, что новых изменений пока нет, нам оговорит сообщение:
 >**On branch master
nothing to commit, working tree clean**

#### Просмотр истории коммитов
Для вывода на экран истории всех коммитов с их хеш-кодами испольуется команда:
>**git log**

После выполнения команды на экран вывоятся все произведенные коммиты с комментариями. Последнее изменение будет показано первым. 
Используй стрелки **"вверх"/"вниз"** для перемещения по журналу.
Чтобы выйти из журнала, нажми **"q"**.

#### Переход от одного коммита к другому
Для переключения между сохранениями используется команда:
>**git checkout**

**Например:**
Нам нужно перейти к определенному коммиту, для этого с помощью команды __*git log*__ переходим в журнал всех изменений. Находим тот коммит, который нам нужен и копируем первые 4-6 символов его хеш-кода, чтобы **Git** смог понять, какой
коммит имеется в виду.
Выходим из журнала (**"q"**) и выполняем команду:

>**git checkout** 213c // _номер - это пример_

**Примечание:**
Если в текущей версии есть несохраненные изменения, то **Git** не позволит перейти на другое сохранение, пока текущее не будет зафиксированно. Это происходит для того, чтобы мы не потеряли информацию.
#### Возврат к текущей версии

Чтобы вернуться к текущей версии, используй команду:
>**git checkout master**

После выполнения этой команды мы вернемся к текущей версии из сохранения, которое мы просматривали.

#### Разница между версиями

Мы можем посмотреть разницу между
текущей и уже зафиксированной версией
файла. Для этого используется команда:
>**git diff**

**Например:**
Мы начали вносить в файл изменения и хотим узнать, какие именно изменения мы уже успели внести.
После выполнения команды __*git diff*__мы увидим эту разницу в терминале.
Используй стрелки **"вверх"/"вниз"** для перемещения.
Для выхода нажми **"q"**.

**Примечание:**
Если изменения еще не внесены, то команда выполнится, не показав никакой информации.

#### Посмотреть список веток в репозитории

Для работы не следует использовать одну ветку, их должно быть несколько. Посмотреть список существующих веток поможет команда:

>**git branch**

Выглядеть это будет так:
![branch.PNG](branch.PNG)
**Примечание:**
Рисунок показывает, что ветка на данный момент у нас только одна и мы находимся в ней (знак **"*"** перед ее названием).

#### Создание новой ветки

Новая ветка создается с помощью команды:
>**git branch** <название ветки>

**Примечание:**
После выполнения этой команды следует выполнить команду __*git branch*__, чтобы убедиться, что в списке веток присутствует наша, только что созданная. 

#### Переход к другой ветке

Когда мы создали несколько веток, мы можем между ними перемещаться. Делается это с помощью команды:

>**git checkout** <название ветки>

**Примечание:**
После выполнения этой команды следует выполнить команду __*git branch*__, чтобы убедиться, что мы перешли на нужную ветку.
Символ **"*"** должен находиться напротив нужной нам ветки, а сама ветка будет подсвечена зеленым:

![checkout.PNG](checkout.PNG)
#### Слияние веток

Так как не рекомендуется все изменения вносить сразу в ветке **master**, мы создаем другие ветки. Однако, если мы уверены во внесенных изменениях, то их можно перенести в основную ветку (или в любую другую), используя команду:
>**git merge**<название ветки>

**Примечание:**
Например, если мы находимся в ветке **master**, а последние изменения были внесены в ветку **add_new_branch** (тут имеется в виду название ветки, оно может быть любым), то пишем:

>**git merge add_new_branch**

Однако, если изменения зафиксированы в разных ветках, на тех же строчках, то случится __*конфликт*__, который необходимо разрешить.

Выглядит это следующим образом:
![CONFLICT.PNG](CONFLICT.PNG)


__*Что мы видим?*__
На бирюзовом поле мы видим текущее изменение, а на синем - входящее.
Мы можем сравнить их и принять решение.

__*Что делать?*__
Мы видим четыре варианта (кнопки над бирюзовым полем), это:
* **Accept Current Change**  - Принять текущее изменение. То есть оставить только то, что содержит бирюзовое поле;
* **Accept Incomming Ghange** - Принять входящее изменение. То есть оставить только то, что содержит синее поле;
* **Accept Both Changes** - Принять  оба изменения;
* **Compare Changes** - Сравнить изменения.

Если конфликт не возник, то мы увидим:
![NO_CONFLICT.PNG](NO_CONFLICT.PNG)

#### Удаление ненужных веток
Если ветка больше не используется, то ее можно удалить. Команда для этого:
>**git branch -d** <название ветки>

**Примечание:**
Если изменения из удаляемой ветки были внесены не полностью (не слиты), то появится сообщение:

![delete_branch.PNG](delete_branch.PNG)

В случае, если мы уверены, что ветку можно удалить, используем (как просит **Git**) команду:

>**git branch -D** <название ветки>

То есть теперь вместо маленькой **d** будет большая.

#### Визуализация всех веток
Чтобы отобразить коммиты в виде дерева (увидеть, какие ветки были слиты), используем команду:

>**git log --graph**

#### Очистка выдачи терминала

При необходимости выдачу терминала можно очистить. Для этого используем команду:

>**clear**

## Работа с удаленными репозиториями
## Что такое GitHub?

**GitHub** - это сервис компании Майкрософт для
организации работы удаленных репозиториев. Самый популярный сервис **Git**.

**Удаленный репозиторий** – это репозиторий, размещенный в локальной или интернет сети. Удаленный репозиторий используется для того, чтобы делиться и обмениваться кодом между разработчиками в рамках сети. Его также можно использовать, если вы разрабатываете проект на нескольких устройствах.

#### Работа с готовым репозиторием (создание локальной версии)

__*Что нужно сделать?*__

1. Перейти на https://github.com/
2. Зарегистрироваться / Авторизоваться
3. Найти готовый репозиторий
    **Примечание:**
Какие файлы содержит репозиторий, мы можем посмотреть здесь же, открыв их.
4. Скопировать ссылку на репозиторий. Делается это следущим образом:
    
    4.1. Нажать на кнопку "Code"(1)
    4.1. Нажать на кнопку "Копировать"(2)
![clone.PNG](clone.PNG)
5. Создать/Открыть папку, не содержащую репозиторий.
        **Примечание:**
Чтобы убедиться, данная папка не является репозиторием, используем команду _**git status**_.
6. Создать локальную версию репозитория. Это команда:

>**git clone**<Строка, скопированная с GitHub>

После выполнения этой команды в нашей папке появляется локальная версия репозитория, взятого с https://github.com/.

Чтобы начать работу с **Git**, в эту папку нужно перейти с помощью команды:

>**cd**<Имя появившейся папки>

#### Создание репозитория на GitHub

Создавать репозиторий мы уже уже умеем, а теперь нужно сделать так, чтобы он отправился на https://github.com/.
Для этого первое, что нужно сделать - это создать свой аккаунт или зайти в существующий.

Теперь создадим репозиторий:

1. Находясь в своем аккаунте, ищем в правом верхнем углу плюсик (**"+"**) и нажимаем его.
2. В выпадающем меню выбираем **"New repository"**.

Выглядит это вот так:
![new_rep.PNG](new_rep.PNG)

3. Теперь дадим ему имя. Оставив все остальное по умолчанию, нажимаем **"Create repository"**:

![rep_create_and_name.PNG](rep_create_and_name.PNG)

Дальше мы видим подсказки, что мы можем сделать:

* создать новый репозиторий в командной строке;
* отправить существующий репозиторий из командной строки;
* импортировать код из другого репозитория;

    **Примечание:**
Под каждой подсказкой мы видим и команды, которые нужно будет использовать для каждого из вариантов:
![com.PNG](com.PNG)

Нам нужно выбрать второй вариант.
Копируем и выполняем поочередно команды:

>**git remote add origin** https://github.com/Seamys136/My_First_Repository.git *//связываем свой локальный репозиторий  с удаленным*

>**git branch -M main** *//указываем, какая ветка будет являться основной*

>**git push -u origin main** *//отправляем все, что содержит локальный репозиторий в интернет*

**Примечание:**
После выполнения третьей команды (если она выполняется впервые), нужно пройти авторизацию. Необходимо следовать подсказкам **VS Code**.
После того, как мы "подружили" **Git** и **GitHub**, в терминале увидим следующее:

![success.PNG](success.PNG)

#### Добавление информации в существующий удаленный репозиторий
После того, как мы связалаи локальный репозиторий с удаленным, мы снова можем внести изменения, зафиксировать их и опять отправить на удаленный репозитоий. Для этого достаточно использовать команду:

>**git push**

#### Добавление информации с удаленного репозитория в локальный

Например, мы внесли изменения с другого компьютера или на удаленном репозитории. Теперь мы хотим, чтобы эти изменения оказались на локальной версии.
Используем команду: 
>**git pull**

**Примечание:**
Эта команда позволяет скачать все из текущего репозитория и автоматически сделать merge с нашей версией.

#### Участие в другом проекте

К примеру, мы увидели чей-то проект и хотим в нем поучаствовать или помочь в его развитии автору. У нас нет доступа к таким репозиториям, но тем не менее, предложить свои идеи мы можем.     
Для этого, находясь винтересующем нас репозитории нужно нажать кнопку **"Fork"**:
![fork.PNG](fork.PNG)
После этого на следующей странице нажимаем кнопку **Сreate fork"**.
Теперь этот репозиторий находится на нашем аккаунте и мы можем его клонировать его копию на свой компьютер
(Раздел **"Работа с готовым репозиторием (создание локальной версии"**)).

Добавляем в репозиторий новую ветку, в которую вносим свои изменения. Теперь их нужно оправить на удаленный репозиторий. Это команда **_git push_**.

Так как все изменения вносились не в основную ветку, **Git** нам подскажет, какую команду нужно выполнить, чтобы отправить изменения. Это будет команда:
>**git push --set-upstream origin master** //где **master** - это название ветки, с которой мы работали.

После этого на **GitHub** появится кнопка **"Compare & pull request"**. 

![pull_request.PNG](pull_request.PNG)
Нажимаем на нее.
Далее мы можем добавить какое-то описание и нажать кнопку **"Create pull request"**.

Теперь наши изменения ушли к хозяину репозитория.