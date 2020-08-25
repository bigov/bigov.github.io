---
layout: post
title:  "Переезд на GitHub"
date:   2020-08-20 12:59:0 +0900
categories: site content
---

По непонятной причине сайт проекта заглючил, и на восстановление работы пришлось потратить пару часов. Потом, используемая для управления контентом, Очень_Популярная_И_Крутая_CMS в очередной раз потребовала обновиться. Попутно выяснилось, что ее последняя версия опережает используемую у меня уже на два "поколения" (в смысле минорного номера версии). Попытка мигрировать оказалсь неудачной - оказалось, что работа движка завязана на конкретную версию РНР. Но это "пол-беды" - основная проблема оказалась в том, что на сайте используется _sqlite_ база данных, которая не поддерживается в новой версии. Вопрос "встал ребром" - продолжать пользоваться устаревшей версией СМС, рискуя устойчивостью и надежностью, или искать другие варианты.

Несколько попыток мигрировать в "автоматическом" режиме оказались безуспешными. Остался только один вариант - перенос контента "вручную". Не хотелось больше использовать такой капризный в работе инструмент, поэтому начались поиски чего-то более гибкого и простого. А тут еще очень удачно "подвернулся" [GitHub] со своим бесплатным хостингом для репозиториев. Поэтому решение получилось достаточно "радикальное".

## Установка Ruby

На хостинге [GitHub] для "динамического" формирования страниц используется Jekyll. Это софт на платформе Ruby. При работе в MS-Windows его можно установить и настроить из [rubyinstaller2]:

- скачиваем свежий релиз,
- распаковываем в удобном для работы месте,
- открываем окно командной строки в папке `rubyinstaller2_dir\bin`
- выполняем команду `...\bin> ridk install`

С сайта [rubyinstaller2] скачиваем и запускаем инсталятор свежего релиза `rubyinstaller + devkit`. При установке я отключил опцию "установить MSYS2", так как он уже устанвлен в моей системе

Если устанавливать `MSYS2`, предлагаемый в составе `rubyinstaller2`, то его следует обновить. Процесс оказался нетривиальный из-за проблемы с PGP ключами, которые устарели и оказались нерабочими. Чтобы их обновить пришлось выполнять следующее (описание на [msys2.org]) :

```
$ curl -O http://repo.msys2.org/msys/x86_64/msys2-keyring-r21.b39fb11-1-any.pkg.tar.xz
$ curl -O http://repo.msys2.org/msys/x86_64/msys2-keyring-r21.b39fb11-1-any.pkg.tar.xz.sig
$ pacman-key --verify msys2-keyring-r21.b39fb11-1-any.pkg.tar.xz.sig
$ pacman -U --config <(echo) msys2-keyring-r21.b39fb11-1-any.pkg.tar.xz
$ rm -r /etc/pacman.d/gnupg/
$ pacman-key --init
$ pacman-key --populate msys2
$ pacman -Syu
```

После закрытия терминала процесс в памяти зависает и msys2.exe невозможно запустить, пока не будет выполнена команда:

```
С:\> taskkill /f /fi "MODULES eq msys-2.0.dll"

```

После этого повторно запускаем обновление msys2:

```
$ pacman -Syu
```

Устанавливаем `jekyll`:


```
С:\> gem install bundler
С:\> gem install jekyll
С:\> gem update
```

В результате получаем настроенную среду `ruby`. Дальнейший процесс вкратце описан на странице [Quickstart].

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[GitHub]: https://pages.github.com
[rubyinstaller2]: https://github.com/oneclick/rubyinstaller2/releases
[Quickstart]: https://jekyllrb.com/docs/
[msys2.org]: https://www.msys2.org/news/#2020-06-29-new-packagers

