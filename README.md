# GIT Яндекс Практикум

# Введение

**VCS** (*Version Control System*) — система контроля версий

**SCM** (*Source Control Management)* — система управления исходным кодом

**Ревизией** == **Версия** — содержит что изменидлсь, кто внес изменения, кода было изменение, коментарий к изменению

Основные функции системы контроля версий:

- хранит историю изменений в виде отдельных ревизий;
- позволяет манипулировать историей: например, менять порядок ревизий, полностью удалять версии, возвращаться назад в истории;
- помогает анализировать изменения: например, кто и когда вносит изменения, кто чаще всего вносит изменения в определённый файл и так далее.

> Система контроля версий — общее название ряда продуктов, таких как Git, Mercurial, Subversion и других.
> 

**CLI** (*Command-line Interface*) — командная строка

**Консольные** и **графические интерфейсы** — два способа взаимодействия с программами

**Консоль**, **терминал**, или **командная строка**, — это программа, которая считывает команду пользователя и выполняет её.

![Untitled](GIT_pic/Untitled.png)

Запустите программу **Terminal**

- для Linux — `Ctrl+Alt+T`;
- для macOS — `Cmd+Space`, затем ввести `terminal`

# Команды терминала

**`pwd`** — (*print working directory*) показать рабочую папку

`**cd**` — (*change directory*) сменить директорию

**`~`** — обозначение домашней директории

**`ls`** — (*list directory contents)* отобразить содержимое директории

**`..`** — вернуться на уровень выше

**`.`** — обратиться к текущей директории

**Флаг** **`-a`** пример `ls -a`  — вывести расширенный список (отоброзит все файлы начинающиеся с `.` т.е. файлы конфигурации, а также файл `.` и `..` которые обозначают текущую и родительскую директории)

**`touch`** — (*«коснуться»*) ****создать файл (можно создавать сразу несколько файлов указав их через пробел)

**`mkdir`** — (*«make directory»*) создать директорию (можно создавать сразу несколько папок указав их через пробел)

**Флаг `-p`** пример `mkdir -p dir1/dir-inside/dir-deeper-inside` — создать структуру директорий

**`cp что_копируем куда_копируем`** — (*copy* - «копировать») копирование файлов (можно указать сразу несколько файлов `что_копируем что_копируем что_копируем` )

**`mv`** — (*move - «переместить»*) перемещение файлов и папок

**`cat`** —  (*concatenate and print - «объединить и распечатать»*) чтение файлов

**`rm`** — (*remove - «удалить»*) удалить файл

**`rmdir`** — (*remove directory*) *удалить директорию*

**Флаг `-r`** (*recursive - «рекурсивный»*) пример `rm -r` — удалить папку со всем содержимым (**рекурсивно** удаляет файлы и папки)

---

**`&&`** — разделитель для выполнения нескольких команд 

Пример объединения команд

```bash
$ mkdir second-project && cd second-project && touch index.html style.css
# создаём папку second-project,
# переходим в папку second-project
# и создаём в ней два файла: index.html и style.css
```

**`Tab`** автоматически дописывает не только команды, но и пути (дважды нажать клавишу)

# **Настройка Git**

Для начала работы нужно указать имя пользователя и адрес электронной почты.

**`git config`** (*configuration*) — конфигурация, настройка

**Ключ `--global`** (англ. «глобальный»)

**`user.name`** указать имя или никнейм

**`user.email`** указывают электронную почту

```bash
$ git config --global user.name "User_Name"
# имя или ник нужно написать латиницей и в кавычках

$ git config --global user.email username@yandex.ru
# здесь нужно указать свой настоящий email
```

Все глобальные настройки Git хранит в файле **`.gitconfig`** в домашней директории

Посмотреть файл можно командой

```bash
$ cat ~/.gitconfig
или
$ git config --list 
```

# Инициализация репозитория

**`git init`** — (*repository* - «хранилище», *initialize -* «инициализировать») сделать папку репозиторием (Чтобы Git начал отслеживать изменения)

**`rm -rf .git`** — «разгитить» папку, если что-то пошло не так (удалить скрытую подпапку `.git`)

- **ключ `r`** (*recursive* - «рекурсивно») позволяет удалять папки вместе с их содержимым;
- **ключ `f`** (*force* - «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?»

`**git status**` — (*status* — «статус», «состояние») проверить текущее состояние репозитория

# **Добавляем файлы в репозиторий (`git add`)**

`**git add <file>**` — добавить файл в репозиторий (**не сохраняет файл в репозиторий**)

**Флаг `--all`** — позволяет подготовить к сохранению все файлы в репозитории

`git add .` — добавить всю текущую папку

# Коммит (`git commit`)

Это как если бы вы могли выполнить операцию `Ctrl+Z` для целой папки (репозитория)

`git commit -m <text_message>`  — сохранить все подготовленные файлы в репозиторий с указанным сообщением

**Флаг `-m`** — (***message*** - «сообщение») присвоить коммиту сообщение

> **PS:** в сообщении `root-commit` это самый первый, или «корневой» (*root*), коммит в ветке, у следующих коммитов такой надписи не будет.
`mode 100644` сообщает, что это обычный файл.
>
>
Также возможны варианты `100755` для исполняемых файлов (например, `что-нибудь.exe`) и `120000` для файлов-ссылок в Linux. 
>
>
Файлы-ссылки не содержат данных сами по себе, а только ссылаются на другие файлы — как «ярлыки» в Windows.
> 

# **Историю коммитов**

**`git log`** — (*log* - «журнал [записей]») просмотреть историю коммитов

Последний коммит выводится сверху

# **SSH-ключ**

**Публичный ключ** (*public key*) для **шифрования** данных

**Приватный ключ** (*private key*) для **расшифровки** данных

**`~/.ssh/`** — директория по умолчанию для хранения SSH-ключей

## **Генерация SSH-ключа**

Для генерации SSH-пары можно использовать программу `ssh-keygen`

```bash
$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"
```

`ed25519` — алгоритм шифрования

- Далее будет предложено выбрать место хранения SSH-пары (можно ничего не менять и нажать `Enter` сделав домашний каталог пользователя путём по умолчанию)
- Далее программа запросит **кодовую фразу** (*passphrase*)
- Ключ создан)

`**ls -a ~/.ssh**` — проверить что ключи сгенерированы

## **Привязываем SSH-ключ к GitHub**

Скопируйте содержимое файла с публичным ключом в буфер обмена.

- **GitHub**  
**Settings** → **SSH and GPG keys** → New SSH key → <Заполнить поля> → Add SSH key
    
    ![Untitled](GIT_pic/Untitled%201.png)
    
    ![Untitled](GIT_pic/Untitled%202.png)
    
    ![Untitled](GIT_pic/Untitled%203.png)
    
    ![Untitled](GIT_pic/Untitled%204.png)
    

Проверьте правильность ключа с помощью следующей команды

```bash
$ ssh -T git@github.com 
```

При первом подключении к хосту стоит проверить совпадает ли `fingerprint` в консоли с ним же на сайте

# **Связываем локальный и удалённый репозитории**

**GitHub**

Копировать ссылку на странице удаленного репозитория

![Untitled](GIT_pic/Untitled%205.png)

**В консоли**

1. Прейти в каталог локального репозитория
2. Ввести команду `git remote add` (*remote* - «удалённый», *add* - «добавить»)

```bash
$ cd ~/dev/first-project
$ **git remote add origin URL** 
```

`origin` — имя удалённого репозитория

`URL` — скопированная ссылка со страницы удалённого репозитория

> `origin` (англ. «источник») — стандартный псевдоним, с помощью которого можно обращаться к главному удалённому репозиторию (обычно такой репозиторий один). Это значительно упрощает работу.
> 

**`git remote -v`** — убедиться, что репозитории связаны

**Флаг `-v`** — короткая форма флага `--verbose` - «подробный». Он позволяет показать больше информации в выводе.

```bash
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push) 
```

# **Синхронизируем локальный и удалённый репозитории**

**`main` или `master`**

**`git push`** — (*push* — «толкать») отправить изменения на удалённый репозиторий

В первый раз эту команду нужно вызвать с флагом `-u` и параметрами `origin` (имя удалённого репозитория) и `main` или `master` (название текущей ветки). 

**Флаг `-u`** свяжет локальную ветку с одноимённой удалённой. 

Как вы связывали локальный и удалённый репозитории в предыдущем уроке, так же и здесь нужно дополнительно связать ветки.