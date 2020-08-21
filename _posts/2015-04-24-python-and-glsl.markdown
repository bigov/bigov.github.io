---
layout: post
categories: site content
date: 2015-04-24 14:02:44
title: Python + GLSL
---
<p>На сегодняшний день для создания качественной графики в OpenGL необходимым условием 
является использование шейдеров. Через поиск в Сети можно найти несколько нитересных 
сайтов, на которых есть описание модулей для работы с GLSL и шейдерами. В их числе <a 
target="_blank" href="https://swiftcoder.wordpress.com/2008/12/19/simple-glsl-wrapper-for-
pyglet/">glsl-wrapper</a>, <a target="_blank" href="http://www.pythonstuff.org/glsl/index-
2.html">GLSL experiments</a>, <a target="_blank" 
href="http://codeflow.org/entries/2009/jul/31/gletools-advanced-pyglet-utilities/">gletools</a>, <a 
target="_blank" href="https://code.google.com/p/pyglet-shaders/">pyglet-shaders</a> и несколько 
других. Но все они под Python2, и попытки "по быстрому" это все запустить и проверить под 
Python3 для меня (с поверхностными знаниями C++) оказались провальными.</p>

<p>Но не все плохо. Для работы с OpenGL в среде Python3 можно использовать библиотеку <a 
target="_blank" href="http://www.libsdl.org/index.php">SDL</a>. Это кросс-платформенная 
библиотека, обеспечивающая низкоуровневый доступ к звуковой подсистеме, клавиатуре, мыши, 
джойстику и графическому оборудованию через OpenGL и Direct3D. SDL официально 
поддерживает Windows, Mac OS X, Linux, iOS, и Android. На платформе Linux библиотека входит в 
число стандартных пакетов с именем sdl2_*. Для Windows и Mac OS X с <a target="_blank" 
href="http://www.libsdl.org/index.php">сайта разработчика SDL</a> можно скачать бинарники. 
Там-же в <a target="_blank" href="http://wiki.libsdl.org/Tutorials">Wiki</a> есть необходимая для 
работы документация и довольно обширный раздел ссылок на обучающие материалы. В среде 
Python3 для работы с SDL есть <a target="_blank" 
href="http://pysdl2.readthedocs.org/en/latest/index.html">модуль PySDL2</a> (на момент 
написания статьи - версия 0.9.3). К сожалению, в документации на модуль PySDL2 нет примеров 
работы с шейдерами, а мне непременно надо как-то их "пощупать", что понять как приручить.</p>

<p>Поиск какого-нибудь "quick-start" по теме работы с шейдерами в PySDL2 привел меня в блог 
hivestream.de, где обнаружилось довольно подробное начальное <a target="_blank" 
href="http://www.hivestream.de/python-3-and-opengl-woes.html">руководство (на английском)</a> 
по его использованию, но... Снова извечное "НО"! Приведенный в этом куроводстве пример у 
меня вываливается с ошибкой на функцию запуска шейдера. Не могу пока точно назвать причину, 
вероятнее всего дело в различии версий OpenGL на моем компьютере и использованной в уроке. 
Хотя все демо-примеры из состава модуля PySDL2 (его код размещен на <a target="_blank" 
href="https://bitbucket.org/marcusva/py-sdl2/">bitbucket.org</a>) работают на моей рабочей 
станции без ошибок.</p>


