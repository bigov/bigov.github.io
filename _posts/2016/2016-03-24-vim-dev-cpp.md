---
layout: post
categories: site content
date: 2016-03-24 00:31:20
title: Настройка VIM для работы с C++
---

Основная машина для разработки у меня под Archlinux.  На *nix серверах, с которыми я 
работаю, на установку и настройку Вима уходит минимальное время, тут все логично - "жизнь 
диктует". Но недавно я попробовал "причесать" gVim на домашнем буке под Win-8.1 и 
неожиданно столкнулся с трудностями.

Я спросил у ... Гугля и его коллег. В сети дрейфует огромная масса публикаций о знаменитом 
редакторе. Вы без труда найдете избитые шуточки, пространные руководства, советы скопировать 
готовый конфиг (не вникая в суть). Но мне так и не удалось найти ясного и простого руководства, 
как быстро настроить VIM в качестве IDE для разработки.

Представленное ниже содержимое предполагает, что читатель уже знаком с предметом 
обсуждения, знает как пользоваться справкой Вима и где искать пользовательский 
конфигурационный файл.

Стараясь получить от Вима под MS-Win 8.1 функционал, аналогичный основному рабочему 
месту (под Линуксом), я потратил несколько вечеров подряд. На Арче все было просто - установил 
пакеты, по описанию которых решил что они нужны, и все заработало. Под Виндой так гладко не 
случилось - пришлось вникать в связи плагинов, модулей, учитывать особенности строения 
файловых систем и т.д. Что самое интереное, когда я вник и разобрался как чего тут крутится, то в 
результате и на рабочем Арче все было снесено, потом скомпилировал свежий Вим из исходников 
и подключил свой общий конфиг с плагинами в домашней директории.

Хочу сразу отметить,  что об IDE, в общепринятом понимании, речь не идет, хотя Виму вполне 
по силам решать весь набор задач "взрослой" IDE, если на настройку потратить чуть больше 
времени. И так что же делает из текстового редактора "Среду Разработки"? Каков минимально-
необходимый набор возможностей? Для меня на первом месте оказалось наличие следующих 
возможностей:


- подсветка синтаксиса,
- контроль ошибок,
- автодополнение кода,
- быстрый переход по меткам,
- Ну, и возможность настроить "под себя" внешний вид и сочетания клавиш, как же без 
"печенюшек"? Хотя это не главное, так как Вим невероятно гибок.

По обозначенным пунктам и выполним настройки. Насколько такой редактор окажется 
удобным лично для Вас, зависит только от Вашего желания потратить время и силы. Но по своему 
опыту скажу - оно того стоит!

Для начала скачаем свежую версию редактора. Чтобы найти ее, как ни странно, пришлось 
"повозиться". Дело в том, что в свежих сборках Вима добавлены некоторые возможности, которых 
нет в версии трехлетней давности, выложенной на официальном сайте Вима на странице загрузки. 
На сайте vim.wikia.com имеется <a href="http://vim.wikia.com/wiki/Where_to_download_Vim"  
target="_blank">страница со списком ресурсов</a>, где можно найти бинарные сборки Вима. Но 
оказывается, еще есть раздел проекта разработчиков Вима на github.com с <a 
href="https://github.com/vim/vim-win32-installer/releases" target="_blank">бинарными 
сборками</a>. Там лежат свежие сборки для MS-Windows (x86 и x64) как в форме архива, так и в 
виде инсталятора. Я использовал архив, распаковав его в нужную папку - предпочитаю по 
возможности держать все под контролем, привычка сисадмина.

На странице загрузки сайта Вима есть информация, что для поддержки возможности 
перекодировки файлов требуются дополнительные библиотеки из libiconv и libintl. Но в сборке, 
которую я скачал, команды перекодировки при открытии и сохранении файлов (:e ++enc=..., :set 
fileencoding=...) прекрасно работают "из коробки" без дополнительной установки библиотек. 
Может в моей системе они уже и присутствуют, поэтому просто помните, что если у вас 
перекодировка файлов не будет работать, то это попраВимо.

## 1. Подсветка синтаксиса

C этим пунктом проблем нет - работает "из коробки". Для начала конфигурационный файл 
"$HOME/vimfiles/vimrc" я настроил так:


{% highlight VIM %}

set nocompatible
set guifont=DejaVu_Sans_Mono:h9:cRUSSIAN
set lines=80 columns=100
set cursorline
set number
syntax enable
set fileencodings=ucs-bom,utf-8,cp1251,cp866,koi8-r
set fileformat=unix
set hidden
set mouse=a
set showmode
set wildmenu
set showcmd
set allowrevins
set antialias
set noexpandtab
set laststatus=2
set statusline=[%n]\ %<%f\ [%Y%R,%{&ff}%W]%=%m\ %03l/%03L\ [%03v\ %03b]

{% endhighlight %}

Конечно, всегда есть варианты и каждый может настраивать конфиг "под себя". Ключевая 
строка тут всего одна - "syntax enable". Да, еще следует обратить внимание на наличие в системе  
шрифта (DejaVu), указанного во второй строке конфига.

Если какой-то из пунктов приведенного конфигурационного файла непонятен, Вы всегда 
можете спросить про него у своего Вима. Например - ":h hidden". Правда ответ будет на 
английском. Если английский вас утомляет, то для изучения справки на русском языке можно 
скачать файлы справки с проекта <a href="http://ruvim.sourceforge.net/" target="_blank">Russian 
Vim</a>. Там немного устаревшая версия (6.3), но она вполне пригодна для использования, так 
как основной функционал работы Вима за это время практически не изменился. Скопируйте в 
свою домашнюю папку Вима содержимое файлов справки на русском (можно в отдельный 
подкаталог, что не перемешивать) и скажите Виму:

<code>:helptags ~/vimfiles/doc</code>

## 2. Контроль ошибок

Для контроля ошибок в коде я использую пакет (плагин) <a 
href="https://github.com/scrooloose/syntastic" target="_blank">syntastic</a>. Полный функционал и 
его простая установка обеспечивается только в сборках Вима начиная с 7.4.1486. ВНИМАНИЕ: на 
момент написания статьи в официальном репозитории находилась (как я уже отмечал) старая 
версия 7.4.1024, что нас совсем не устраивает. Используйте свежую бинарную сборку с <a 
href="https://github.com/vim/vim-win32-installer/releases" target="_blank">github.com</a>.

Для установки Sytastic в последних сборках Вима уже нет необходимости использовать (что 
лично меня всегда раздражало) дополнительные пакеты плагинов-инсталяторов, достаточно 
просто скопировать пакет в нужную папку. Путь к папке для дополнительных пакетов Вим укажет, 
если у него спросить ":help packages". У меня получилось 
"%HOME%\vimfiles\pack\foo\opt\syntastic", куда я и распаковал архив из репозитория. Если у Вас в 
системе есть "git", то можно прямо в эту папку клонировать репозиторий, что весьма удобно для 
периодического обновления пакета. После этого запускаем редактор и добавляем пакет 
командой ":packadd syntastic".

Функционирование синтастика проверяется командой ":SyntasticInfo". Если редактор открыт 
без редактируемого файла (пустая страница), то по этой команде мы увидим пустой список 
доступных чекеров (утилит проверки синтаксиса). Создадим С++ файл командой ":e tst.cpp" и 
повторим проверку командой ":SyntasticInfo". Если Синтастик найдет в Системе установленные 
компиляторы языка C++, то он автоматически их определит и начнет использовать, что мы и 
увидим. Если нет, то возникает естественный вопрос - а чем собственно Вы собрались 
компилировать свой код?

Все дело в том, что пакет Синтастик ничего сам не проверяет и не компилирует. Это вобще не 
его задача. Но он замечательно умеет использовать существующие в вашей Системе (более 
профессиональные) инструменты работы с кодом и направлять результаты в Вим. Для 
компиляции и проверки кода возмем gcc в составе MinGW-w64. Если кому-то интересно, то  на 
сайте TrickRig  можно посмотреть <a href ="https://www.trickrig.net/gcc_mingw">короткую 
инструкцию</a> о том, как установить свежую сборку GCC. Этот компилятор и будем использовать 
для статического анализа и проверки синтаксиса исходного кода.

Вобще, если вы загляните в Вики на сайте Синтастика, то увидите то он поддерживает 
проверку синтаксиса около двух десятков языков несколькими способами каждый. Так что 
диапазон выбора огромный. А для нашего варианта добавим несколько строк в пользовательский 
конфигурационный файл "$HOME/vimfiles/vimrc":

{% highlight vim %}

filetype on " Включение Vim filetype detection
filetype plugin on " Включение плагинов

" === sytastic plugin ===
let g:syntastic_cpp_compiler="gcc"
let g:syntastic_cpp_compiler_exec="F:/mingw/bin/i686-w64-mingw32-g++.exe"
" ключи статического анализатора для настоящих ниндзя - часть можно убрать:
let g:syntastic_cpp_compiler_options="-std=c++11 -Werror -Wall -Wextra -Wpedantic -Weffc++ -
Woverloaded-virtual -Wctor-dtor-privacy -Wnon-virtual-dtor -Wold-style-cast -Wconversion -Wsign-
conversion -Winit-self -Wunreachable-code"
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*
let g:syntastic_always_populate_loc_list=1
let g:syntastic_auto_loc_list=1
let g:syntastic_check_on_open=1
let g:syntastic_check_on_wq=1

{% endhighlight %}

Тут следует обратить внимание на два момента. Первое - это то что в пути к компилятору 
следует указать обратные слэши для разделения папок. Стандартные для Винды прямые слэши 
Вим, как продукт проросший в среде юникса, у меня не понял. И второе - это настройка опций 
проверки для комилятора. В строке параметров перечислен довольно жесткий набор правил 
статического анализа исходного кода. Некоторым он может показаться излишним.

Для подключения справочного файла модуля Синтастик надо добавить его в папку "doc" в 
пользовательском каталоге Вима и выполнить команду:

<code>:helptags ~/vimfiles/doc</code>

Специально выделил эту команду отдельной строкой - не забывайте обновлять список тегов 
файлов помощи при добавлении любой новой справочной информации.

## 3. Автодополнение кода

Без автодополнения написание кода становится невыносимо долгим и нудным занятием. 
Бывает у вас так, что не заглядывая в документацию используемой библиотеки вы уже "почти" 
угадали имя нужной Вам функции или константы из группы аналогичных, но оно почему-то не 
работает? Без автодополнения начинается подбор окончаний, отдельных букв и заканчивается 
тем, что все-таки обращаешься к документации. И что же мы там видим? Ничего особого, самый 
первый вариант был угадан парвильно. Но в текст закралась маленькая незаметная описка и все -  
полет мысли поломался!

Избавиться от непродуктивных задержек  при написании кода поможет автодополнение. В 
составе Вима уже есть функционал автодополнения "omnicomplete", который работает на основе 
базы тегов создаваемой при помощи утилиты "ctags". В дополнение к нему для написания 
программ на C++ есть плагин <a href="https://github.com/vim-
scripts/OmniCppComplete">OmniCppComplete</a>. Качаем архив и просто распакуем его в 
пользовательский каталог Вима. На этом установка OmniCppComplete заканчивается. Для его  
настройки воспользуемся рекомендациями на <a 
href="http://vim.wikia.com/wiki/C%2B%2B_code_completion" target="_blank">vim.wikia.com</a>.

`продолжение следует: проверяю новые фичи и баги.`

P.S. хотел по-быстрому... Вероятно, Вим не та программа, о которой можно по-быстрому. 
Потому что Вим - это не просто программа, а СТИЛЬ работы.

