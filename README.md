## Laboratory work II

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab02** и с лиценцией **MIT**
- [ ] 2. Сгенирировать токен для доступа к сервису **GitHub** с правами **repo**
- [ ] 3. Ознакомиться со ссылками учебного материала
- [ ] 4. Выполнить инструкцию учебного материала
- [ ] 5. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

Установка переменных
```ShellSession
$ export GITHUB_USERNAME=FalaleevDanila                               # Экспорт переменной GITHUB_USERNAME
$ export GITHUB_EMAIL=falaleevdanila@gmail.ru                         # Экспорт переменной GITHUB_EMAIL
$ export GITHUB_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx        # Экспорт переменной GITHUB_TOKEN
$ alias edit=nano                                                     # Экспорт синонима команды edit
```
Переход в папку workspace и активация начального скрипта:
```ShellSession
$ cd ${GITHUB_USERNAME}/workspace         # Переход в папку workspace             
$ source scripts/activate                 # Выполнение скрипта подготовки
```
Конфигурация hub:
```ShellSession
$ mkdir ~/.config                                   # Создание папки с config
mkdir: невозможно создать каталог «/home/danila/.config»: Файл существует
$ cat > ~/.config/hub <<EOF                         # Создание файла hub и запись в него
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF
$ git config --global hub.protocol https            # Установка переменной config git
```
Работа с git:
```ShellSession
$ mkdir projects/lab02 && cd projects/lab02                               # Создание папки и переход в нее
mkdir: невозможно создать каталог «projects/lab02»: Файл существует
$ git init                                                                # Создание пустого репозиторий
Переинициализирован существующий репозиторий Git в /home/danila/FalaleevDanila/workspace/.git/
$ git config --global user.name ${GITHUB_USERNAME}                        # Установка переменной user.name для git
$ git config --global user.email ${GITHUB_EMAIL}                          # Установка переменной user.email для git
# check your git global settings                                          
$ git config -e --global                                                  # Вывод config из git
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git   # Добавление ссылки репозитория на Github
fatal: внешний репозиторий origin уже существует
$ git pull origin master                                                  # Перенос изменения с Github
warning: не общих коммитов
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (3/3), готово.
Из https://github.com/FalaleevDanila/lab02
 * branch            master     -> FETCH_HEAD
 + 5427082...4ec904d master     -> origin/master  (принудительное обновление)
fatal: отказ слияния несвязанных историй изменений
$ touch README.md                                                         # Создание README.md
$ git status                                                              # Посмотр статуса репозитория
На ветке master
нечего коммитить, нет изменений в рабочем каталоге
$ git add README.md                                                       # Добавление README.md в список фиксированных
$ git commit -m"added README.md"                                          # Закоммитить фиксированные изменения
На ветке master
нечего коммитить, нет изменений в рабочем каталоге
$ git push origin master                                                  # Отправить изменения на гитхаб
 ! [rejected]        master -> master (non-fast-forward)
error: не удалось отправить некоторые ссылки в «https://github.com/FalaleevDanila/lab02.git»
```

Добавить на сервисе **GitHub** в репозитории **lab02** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
.idea/
```
Перенос изменений с github:
```ShellSession
$ git pull origin master   # Перенос изменений с Github
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (3/3), готово.
Из https://github.com/FalaleevDanila/lab02
 * branch            master     -> FETCH_HEAD
   4ec904d..43b84f2  master     -> origin/master
fatal: отказ слияния несвязанных историй изменений
$ git log                  ## Просмотр commits
commit 28dc2e0170eba6997b9c22167a4289d9b9d91d23 (HEAD -> master)
Author: FalaleevDanila <falaleevdanila@gmai.ru>
Date:   Mon Mar 25 01:20:26 2019 +0300

    added sources

commit 727a167b31c240a5df869c229b4c1778d53cc58e
Merge: 46af5e8 0250a08
Author: FalaleevDanila <falaleevdanila@gmai.ru>
Date:   Mon Mar 25 01:08:22 2019 +0300

    Merge branch 'master' of https://github.com/FalaleevDanila/lab02

commit 46af5e8c8661bd97a5f8c8a1a70af1436af67440
Author: FalaleevDanila <falaleevdanila@gmai.ru>
Date:   Mon Mar 25 01:05:53 2019 +0300

    added README.md

commit 0250a0817b5f188a051f4440320adc58fe48e0ca
Author: FalaleevDanila <47750074+FalaleevDanila@users.noreply.github.com>
Date:   Sun Mar 24 22:08:02 2019 +0300

    Create .gitignore

commit bfa3e848fb1ffdee6b252bcfe09e1200e50e56de
Author: FalaleevDanila <47750074+FalaleevDanila@users.noreply.github.com>
Date:   Mon Mar 18 18:35:24 2019 +0300

    Initial commit
``` 
Создание папок и файла с кодом:
```ShellSession
$ mkdir sources                   # Создание папки sources
mkdir: невозможно создать каталог «sources»: Файл существует
$ mkdir include                   # Создание папки include
mkdir: невозможно создать каталог «include»: Файл существует
$ mkdir examples                  # Создание папки examples
mkdir: невозможно создать каталог «examples»: Файл существует
$ cat > sources/print.cpp <<EOF   # Запись кода в файл
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
```
Создание файла с кодом:
```ShellSession
$ cat > include/print.hpp <<EOF  # Запись кода в файл
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
```
Создание файла с кодом:
```ShellSession
$ cat > examples/example1.cpp <<EOF   # Запись кода в файл
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
```
Создание файла с кодом:
```ShellSession
$ cat > examples/example2.cpp <<EOF   # Запись кода в файл
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```
Редактирование README.md:
```ShellSession         
$ edit README.md    # Редактировать README.md
```
Просмотр состояния репозитория и отправка изменений на github:
```ShellSession
$ git status                          # Просмотр статуса репозитория
На ветке master
Изменения, которые не в индексе для коммита:
  (используйте «git add <файл>…», чтобы добавить файл в индекс)
  (используйте «git checkout -- <файл>…», чтобы отменить изменения
   в рабочем каталоге)

        изменено:      include/print.hpp

нет изменений добавленных для коммита
(используйте «git add» и/или «git commit -a»)
$ git add .                           # Фиксация всех изменений
$ git commit -m"added sources"        # Commit зафиксированных изменений
[master 87d961c] added sources
 1 file changed, 8 deletions(-)
$ git push origin master              # Отправка изменений на Github
``` 

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=02
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Homework

### Part I

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
3. Создайте файл `hello_world.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.
4. Добавьте этот файл в локальную копию репозитория.
5. Закоммитьте изменения с *осмысленным* сообщением.
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно `git add`?
8. Запуште изменения в удалёный репозиторий.
9. Проверьте, что история коммитов доступна в удалёный репозитории.

### Part II

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. В локальной копии репозитория создайте локальную ветку `patch1`.
2. Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.
3. **commit**, **push** локальную ветку в удалённый репозиторий.
4. Проверьте, что ветка `patch1` доступна в удалёный репозитории.
5. Создайте pull-request `patch1 -> master`.
6. В локальной копии в ветке `patch1` добавьте в исходный код комментарии.
7. **commit**, **push**.
8. Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request
9. В удалённый репозитории выполните  слияние PR `patch1 -> master` и удалите ветку `patch1` в удаленном репозитории.
10. Локально выполните **pull**.
11. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.
12. Удалите локальную ветку `patch1`.

### Part III

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. Создайте новую локальную ветку `patch2`.
2. Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.
3. **commit**, **push**, создайте pull-request `patch2 -> master`.
4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
5. Убедитесь, что в pull-request появились *конфликтны*.
6. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.
7. Сделайте *force push* в ветку `patch2`
8. Убедитель, что в pull-request пропали конфликтны. 
9. Вмержите pull-request `patch2 -> master`.

## Links

- [hub](https://hub.github.com/)
- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2015-2019 The ISC Authors
```
