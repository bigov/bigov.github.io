---
layout: post
categories: site content
date: 2015-04-20 13:45:27
title: Python и графические движки
---
<p>После моего, сравнительно недавно начавшегося, практического знакомства с OpenGL 
возникло желание посмотреть, как же устроен и работает графический движок в открытой 
мультиплатформенной игрушке <a href="http://www.minetest.net/">minetest</a>. При ее 
установке на свой рабочий Archlinux обратил внимание на то, что менеджер подтянул еще один 
пакет, который оказался графическим движком <a 
href="http://irrlicht.sourceforge.net/">irrlicht</a>.</p>
<p>Движок <a href="http://irrlicht.sourceforge.net/">irrlicht</a> открытый, мультиплатформенный, 
написан на C++. Имеется возможность интеграции с Python через собранный на базе ctypes 
модуль <a href="https://pypi.python.org/pypi/pyirrlicht">pyirrlicht</a>. Все замечательно, если бы 
не одно большое "НО" - последняя версия irrlicht - 1.8.1 выпущена 20 ноября 2013 года. 
Остановилась в 2012 г. и работа над модулем <strong>pyirrlicht</strong>. Похоже на то, что 
проекты больше не развиваются.</p>
<p>Впрочем, есть и хорошие новости. Сравнительно недавно (02/21/15) вышел Alpha 3.1 релиз 
(0.31) графической среды разработки (конструктора игр) <a 
href="http://irrrpgbuilder.sourceforge.net/">irrrpgbuilder</a>, в основе которой все тот-же движок 
irrlicht. Кроме того, <a href="http://www.opennet.ru/opennews/art.shtml?num=39723">появился 
проект</a> нового графического движка <a 
href="http://supertuxkart.sourceforge.net/Antarctica:_Overview">Antarctica</a>, как продолжение 
irrlicht. В нем улучшен рендеринг, появилась поддержка шейдеров, улучшена отрисовка 
растительности, появилась трассировка хода лучей, отрисовка эффектов на основе частиц (soft 
particles) с ускорением на GPU, реализация эффектов глубины поля зрения, улучшенный обсчет 
освещения и ряд иных возможностей, характерных для современных движков 3D: <a 
href="http://www.youtube.com/watch?feature=player_embedded&amp;v=nTmC40hi_FA">демо на 
youtube.com</a>.</p>
<p>Ссылки:</p>
<ul><li><a target="_blank" href="https://code.google.com/p/pyirrlicht/">исходники pyirrlicht</a></li>
<li><a target="_blank" href="https://pypi.python.org/pypi/pyirrlicht">pyirrlicht на pypi</a></li>
<li><a target="_blank" href="http://irrlicht.sourceforge.net/">Сайт irrlicht</a></li>
<li><a target="_blank" href="https://www.ibm.com/developerworks/ru/library/l-
python_details_06/">Статья про cpython на ibm.com</a></li>
<li><a target="_blank" 
href="http://en.wikibooks.org/wiki/Python_Programming/Game_Programming_in_Python">Статья по 
теме в Wiki</a></li>
</ul>


