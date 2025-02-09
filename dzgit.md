# Введение в контроль версий. Git.
***(Конспект)***

# Введение

**Система контроля версий** — это система, записывающая изменения в файл или набор файлов в течение времени и позволяющая вернуться позже к версии версии. Можно использовать контроль версий практически для любых типов файлов.

***Системы контроля версий сохраняют  только отличия от изначальной версии***, а не разные версии файла целиком. Данный способ хранения позволяет экономиgiть огромное количество памяти.

*Существует возможность отслеживания всех изменений, их фиксации и возврата к любой из зафиксированных точек.*

Использование какой-либо системы контроля версий позволяет взаимодействовать с другими участниками проекта, редакторами и пр., параллельно продолжая работу над проектом.
Можно вести работу над проектами, требующими участия большого количества участников.

# История 

Наиболее популярная система контроля версий - Git.

**Git** (произносится «гит») — распределённая система управления версиями.

Проект был создан Линусом Торвальдсом - создателем операционной системы Linux для управления разработкой ядра. В этом проекте учавствовало огромное количество программистов-энтузиастов со всего мира и для структурирования их работы был создан Git.

![Линус и Linux стараются](linuzandlinux.jpg)

Первая версия Git выпущена 7 апреля 2005 года.

# Первые шаги в Git

Необходимо установить Git на свой компьютер.

Его можно скачать по ссылке:
<https://git-scm.com/book/en/v2/Getting-Started-Installing-Git>

В терминале VSCode можно посмотреть установленную версию Git командой:

git --version

***При первой установке и запуске Git необходимо пройти регистрацию.*** 

Это можно сделать всего один раз в системе, используя опцию --global

Если предполагается использовать разные имена и почту для разных проектов, то можно в каталоге с проектом не указывать функцию --global.

Необходимо ввести имя пользователя и почту:

git config --global user.name "________"

git config --global user.email ________

**ПОМНИТЕ!** 

*В дальнейшем все следы вашей жизнедеятельности в Git будут помечены указанными данными.*

Если предполагается взаимодействие с другими пользователями, работодателями и пр. лучше выбрать что-то благозвучное или, минимум, нейтральное. С этим жить.

Например, PrettyGirl_1964, Leha_Tankist_Taxi и прочие MegatronDestroer9000, возможно, не лучшие варианты для социальных взаимодействий в сфере IT.

***

Затем необходимо создать папку на своем компьютере для работы с вашим проектом и превратить ее в **репозиторий** - место, где Git будет отслеживать все изменения.

Для этого **папку** нужно **открыть в VSCode** и **использовать в терминале команду _git init_**

Git создаст в этой папке скрытую папку .git, в которой и будет сохранять изменения.

***

**ВАЖНО!**

Можно случайно сделать репозиторием весь рабочий стол, диск C и другие крупные/системные папки. В таком случае Git будет пытаться отслеживать изменения в них.

Чтобы устранить подобную ошибку требуется сделать видимыми **скрытые папки** (Через **Панель управления** в меню **Пуск**), а затем **удалить папку .git**

***

# Команды Git

## Основные термины:

**Индекс** в Git — это специальная промежуточная область, в которой хранятся изменения файлов на пути от рабочей директории до репозитория. При выполнении коммита в него попадают только те изменения, которые были добавлены в индекс.

Стандартный способ работы с индексом — это добавление или изменение файлов и последующий **коммит** - создание новой точки фиксации.

## Основные команды

**git init** инициирует работу git в заданной папке (можно выбрать в правой части экрана VSCode). ***Необходимая первая комманда для работы с папкой любого проекта.***

***

**git status** показывает состояния файлов в рабочей директории и индексе: какие файлы изменены, но не добавлены в индекс, а какие ожидают коммита в индексе. Вдобавок к этому выводятся подсказки о том, как изменить состояние файлов.

***

**Важно!** _Перед использованием команды git add необходимо провести сохранение файла. (Ctrl+S)_ Белая точка в названии файла (VSCode) сообщает, что изменения не сохранены.

**git add название файла.расширение** добавляет содержимое рабочей директории в индекс (staging area) для последующего создания коммита. Происходит включение файла в фиксацию get-а, позволяет отслеживать изменения, **используется каждый раз при создании новых точек фиксации - коммитов**. 

*При работе с несколькими файлами в папке -  при создании точек фисации (коммитов) необходимо использовать данную команду для каждого файла.*

Для ускорения работы можно вводить только первые буквы названия файла и использовать клавишу Tab - автоматическое заполнение.

***

**git commit** берёт все данные, добавленные в индекс с помощью git add, и сохраняет их слепок во внутренней базе данных, а затем сдвигает указатель текущей ветки на этот слепок. 

Каждый **коммит** имеет свой **уникальный цифровой код**, используемый **для возврата к конкретной точке фиксации** - состоянию рабочего  файла.

**Важно!** _Команда git commit -m"text" позволяет создавать комментарии для каждой точки фиксации._ **Написание комментариев обязательно!**

Коммиты можно редактировать. Для этого существует ряд команд, например:

**git commit --amend -m "Новое описание"** позволяет редактировать текст последнего коммента.

Более подробно о редактировании комментов можно узнать, например, [Здесь](https://webhamster.ru/mytetrashare/index/mtb0/1436643644058rbwdv4h)

***

**git diff** используется для вычисления разницы между любыми двумя Git деревьями. Это может быть разница между вашей рабочей копией и индексом (собственно **git diff**), разница между индексом и последним коммитом (**git diff --staged**), или между любыми двумя коммитами (**git diff master branchB**). 

***

**git log** По умолчанию git log перечисляет коммиты, сделанные в репозитории в обратном к хронологическому порядке — последние коммиты находятся вверху (между ними можно перемещаться стреками).

git log имеет очень большое количество опций для поиска коммитов по разным критериям.

*Более подробно ознакомиться с доп. опциями можно* [ТУТ](https://git-scm.com/book/ru/v2/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git-%D0%9F%D1%80%D0%BE%D1%81%D0%BC%D0%BE%D1%82%D1%80-%D0%B8%D1%81%D1%82%D0%BE%D1%80%D0%B8%D0%B8-%D0%BA%D0%BE%D0%BC%D0%BC%D0%B8%D1%82%D0%BE%D0%B2#:~:text=%D0%9E%D0%B4%D0%BD%D0%B8%D0%BC%20%D0%B8%D0%B7%20%D0%BE%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D1%85%20%D0%B8%20%D0%BD%D0%B0%D0%B8%D0%B1%D0%BE%D0%BB%D0%B5%D0%B5,%D1%8D%D1%82%D0%BE%D0%B3%D0%BE%20%D1%8F%D0%B2%D0%BB%D1%8F%D0%B5%D1%82%D1%81%D1%8F%20%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D0%B0%20git%20log%20.&text=%D0%9F%D0%BE%20%D1%83%D0%BC%D0%BE%D0%BB%D1%87%D0%B0%D0%BD%D0%B8%D1%8E%20(%D0%B1%D0%B5%D0%B7%20%D0%B0%D1%80%D0%B3%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2)%20git,%D0%BF%D0%BE%D1%80%D1%8F%D0%B4%D0%BA%D0%B5%20%E2%80%94%20%D0%BF%D0%BE%D1%81%D0%BB%D0%B5%D0%B4%D0%BD%D0%B8%D0%B5%20%D0%BA%D0%BE%D0%BC%D0%BC%D0%B8%D1%82%D1%8B%20%D0%BD%D0%B0%D1%85%D0%BE%D0%B4%D1%8F%D1%82%D1%81%D1%8F%20%D0%B2%D0%B2%D0%B5%D1%80%D1%85%D1%83.)

***

**git checkout** _номер коммита_
(Обычно достаточно ввести 4 первых символа). Позволяет загружать определенные **коммиты**, т.е. возвращать состояние файла к каким-либо сохраненным точкам фиксации.

***

# Работа с ветками в Git

При использовании ветвления,  происходит отклонение от основной линии разработки. Работа продолжается независимо от неё, без вмешательства в основную линию. 

Ветвление позволяет создавать отдельные блоки внутри своего проекта, а также взаимодействовать между различными участниками проекта (в том числе удаленно), каждый из которых проводит свою часть работы в отдельной ветке. Затем ветки с помощью специальных комманд сливаются в один проект.

Новые ветки создают дополнительные указатели для перемещения между коммитами.

*Названия веток в Git - это указатели на коммиты.*

**Ветка являющаяся основной**, изначальной, имеет имя **master**.

*При этом из основной ветки master не видна информация, содержащаяся в отдельных ветвях, и наоборот, отдельные ветви отображают информацию,изначально содержащуюся в ветке master.*

**Текущая ветка и ее последний коммит**, в которой сейчас работаем имеет указатель **HEAD**. Указатель HEAD по существу указывает на тот коммит, после которого будет сделан следующий коммит. 

**HEAD всегда должен указывать на вершину какой-либо ветки.** Когда название ветки и положение HEAD совпадают, то имя ветки, допустим master, указывает на последний коммит в ветке master.

### !Состояние detached HEAD - отсоединенная голова!

Если загрузить какой-либо из предыдущих коммитов, то HEAD сместится туда.
При этом в рабочем каталоге состояние файлов возвращается к состоянию файлов этого коммита.
*Созданные коммиты ветки более поздних состояний, чем загружаемый коммит, никуда не исчезают.*

**Возникает состояние detached HEAD.**

Команда **git reflog** - просмотр истории перемещения головы.

Вызванный **git status показывает данное состояние красным цветом**, тк оно требует внимания.

**Внимание!** 
**Если в состоянии detached HEAD начать работать и создавать новые коммиты, есть большой риск их не то, чтобы совсем потерять, но ооочень долго искать с помощью различных команд и потерять при этом массу времени.**

Проблему возникают потому, что **в состоянии detached HEAD, _голова привязана к конкретному коммиту,_ а не к названию ветки.** Получается, что при создании новых коммитов фактически начинается ветвление, но без создания ветки. И **забыв идентификатор конкретного коммита**, первого в такой псевдоветке, **переключиться на него и все последующие коммиты, в последствии не получится**.

Если не можешь управлять - возглавь!
**"Лечение" подобных состояний - это самостоятельное создание новых веток** при работе из "старого" коммита. 

При перемещении по ветке в состоянии detached HEAD Git сам предложит создать новую ветку.

***

**После перемещения HEAD в созданную для этого ветку обязательно создать новый коммит.**

***

[Понятное, хотя и старенькое пособие по Git, в котором объясняются достаточно сложные моменты](https://webhamster.ru/mytetrashare/index/mtb0/1088)

## Просмотр коммитов при ветвлении

**По умолчанию команда git log - показывает коммиты текущей ветки!**

Для показа истории конкретной ветки необходимо использовать команду **git log Название ветки**

А чтобы посмотреть все существующие коммиты можно воспользоваться командой **git log --all**

**git log --graph** команда показывает цветную шкалу веток и их связей слева от их названий.


## Команды для работы с ветками

**git branch** показывает **существующие ветки**. При этом *текущая ветка*, в которой находимся сейчас *отмечена зеленым цветом и знаком \*.*

***

**git branch название** позволяет создать новую ветку.

**Помните!** *Данная команда создает ветку, но не переходит на нее автоматически.*

***

**git checkout название** команда переключения между ветками.

**git checkout master** - переход в основную ветку.

Можно использовать git branch, чтобы удостовериться в переходе.

***

**git merge название** команда для слияния веток. 

**Для ее осуществления необходимо сначала использовать git checkout master**, а уже **потом git merge название ветки**, которую будем сливать/соединять с основной.

После слияния веток, можно удалить побочную ветвь, используя **git checkout -d Название ветки**

**Важно!** _Комманда **git checkout -d** удаляет только уже слитые ветки, а команда **git checkout -D** удаляет ветки независимо от совершенных над ними действий. Таким образом можно полностью удалить и потерять не слитые ветки._

***

**При работе с ветками нельзя забывать о создании соответствующих коммитов.**

**ИНТЕРЕСНО:** что при команде git merge <ветка>, Git автоматически создаст "коммит слияния". То есть, Git не только изменит содержимое рабочего каталога, применяя вливаемые изменения, но и создаст "завершающий" коммит слияния. Таким образом, после слияния не нужно делать коммит, чтобы "зафиксировать" слияние. Однако следует помнить, что закоммичевание произойдет только в том случае, если при слиянии не было конфликтов.

## Конфликты при слиянии веток

**Слияние и конфликты являются неотъемлемой частью работы с Git.** В других инструментах управления версиями, например SVN, работа с конфликтами может быть дорогой и времязатратной.

 Git позволяет выполнять слияния очень просто. В большинстве случаев Git самостоятельно решает, как автоматически интегрировать новые изменения.

Обычно конфликты возникают, когда два человека изменяют одни и те же строки в файле или один разработчик удаляет файл, который в это время изменяет другой разработчик. В таких случаях Git не может автоматически определить, какое изменение является правильным. Конфликты затрагивают только того разработчика, который выполняет слияние, остальная часть команды о конфликте не знает. Git помечает файл как конфликтующий и останавливает процесс слияния. В этом случае ответственность за разрешение конфликта несут разработчики.

Если при сливании веток информация конфликтует, то в общем окне отображаются оба варианта
Heads и "название ветки".

Конфликт выглядит следующим образом:

Accept Current Change|Accept Incoming Change|Accept Both Chenge

* \<<<<<<<HEAD
* \=======
* \>>>>>>> название ветки

Где \====== - центр конфликта.  
Все содержимое между этим центром и строкой \<<<<<<< HEAD находится в текущей ветке, на которую ссылается указатель HEAD. 

Все содержимое между центром и строкой \>>>>>>> *название ветки* является содержимым ветки для слияния.

Можно выбрать самостоятельно подходящий итоговый вариант. Для этого в верху этого блока есть меню, либо можно отредактировать вручную и устранить конфликт, а потом закоммитить изменения.

# Работа с удаленными репозиториями

Коммит, созданный нами, хранится в репозитарии, привязанном к конкретной папке на нашем компьютере, т.е. является локальным. Это полезно, если мы работаем над проектом самостоятельно. Однако в большинстве случаев возникает необходимость обеспечить доступ к результатам работы или доставить код на сервер, где он будет выполняться.

**Удалённые репозитории** представляют собой версии вашего проекта, сохранённые в интернете или ещё где-то в сети (на сервере).

**GitHab** - это крупнейший веб-сервис для хостинга (размещения в сети) и совместной разработки различных проектов. Githab основан на системе контроля версий Git, является бесплатным для проектов с открытым исходным кодом и небольших частных разработчиков.

Для того, чтобы иметь возможность работы с удаленными репозиториями через GitHab необходимо создать аккаунт (зарегистрироватья). 

Затем, в своем аккаунте, можно создавать репозитории для хранения информации, загружать информацию на githab, и пр.

[GitHab](https://github.com)

# Команды Git для работы с удаленными репозиториями

## **Выгрузка проекта из GitHab на свой компьютер** 
***

**git clone _ссылка из GitHab_** - позволяет скопировать чей-либо репозиторий в свою текущую папку, в которой **нет репозитория**.

*Cсылки на рапозитории в GitHab - вкладка Code на GitHab*

Затем его можно редактировать и изменять уже на своем компьютере.
Git log - позволяет посмотреть коммиты, сделанные предыдущими исполнителями, а git branch - ветки данного проекта.

***

## **Загрузка проекта на GitHab** 

**git branch -M main или master** - указывает основную ветку.

**git remote add origin Ссылка на удаленный репозиторий** - соединяет с данным репозиторием.

**git push -u origin main или master**, где main или master - название ветки. - отправляет данную ветку в удаленный репозиторий.

*После этого можно отправлять репозиторий кому-либо в виде ссылки на данный репозиторий, просто скопировав ее из вкладки Code.*

**Дальнейшая ваша работа над проектом будет проводиться на вашем же компьютере. И для отправки изменений в удаленный репозиторий необходимо использовать команду _Git push_, не указывая отдельную ветку.**

***

**git pull** - позволяет загрузить изменения из удаленного репозитория на свой компьютер. Эта команда автоматически сливает ветки и создает коммент слияния.

***

**Интересно!**

В GitHab есть возможность изменять загруженные файлы - вкладка, на которой изображен **карандаш** (в правой части окна) и **оставлять коммиты** (в нижней части окна, нужен скроллинг).
Кнопка **History** -позволяет посмотреть существующие коммиты.

# GitHab и сторонние проекты.

Для того, чтобы попробовать принять участие над сторонним проектом необходимо воспользоваться кнопкой **Fork** в правом верхнем углу - она **позволяет скопировать чужой репозиторий на свой аккаунт**.

Затем ссылка на этот репозиторий отправляется в VSCode командой **git clone ссылка**.
Работу с такими репозиториями лучше вести в новой ветке. Для этого создается новая ветка.

**В папке с проектом создается файл READMI.md** (капсом -так принято) - в нем описываются сделанные изменения.

Затем требуется отправить изменения в удаленный репозиторий в своем аккаунте (тот самый репозиторий, который был скопирован командой Fork) - **git push**

Теперь **можно предложить данные изменения хозяину проекта**.
Для этого на гитхаб в правом верхнем углу **кнопка Сompare@Pull  request** - сравнить и отправить/предложить хозяину репозитория. Можно добавить описание сделанного.
Появится также окно диалога для общения с хозяином проекта.


### Это всего лишь основы работы с таким мощным инструментом, как Git

[Подробный учебник Git](https://git-scm.com/book/en/v2)


# Спасибо за внимание!