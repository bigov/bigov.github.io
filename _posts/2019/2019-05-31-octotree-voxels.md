---
layout: post
categories: site content
date: 2019-05-31 01:05:10
title: Октодерево и воксели
---
В разрабатываемом графическом движке одной из базовых возможностей должна стать техника 
"Level of Detail" (LOD) - изменение детализации  3D-объектов при изменении расстояния до 
наблюдателя. Без этого невозможно обеспечить онлайн-прорисовку открытого пространства c 
сохранением приемлемого  FPS.

Сейчас основные модули формирования графического интерфейса и 3D сцены построены, и 
настала очередь заняться разработкой LOD. К сожалению, попытки "заточить" под работу с LOD 
текущую модель  построения элементов пространства (на свободно трансформируемых боксах) 
привели к полному разочарованию - сложность реализации не выдерживает никакой критики. 
Стала очевидной необходимость ее менять.

В схему работы LOD идеально ложится модель октодерева. Поэтому было решено не "изобретать 
велосипед", а перейти на использование технологий построения октодерева. Пришлось снова все 
переписывать. Теперь базовым элементом пространства станет масштабируемый воксель. Точнее, 
не "масштабируемый", а разделяемый - в соответствии с принципами построения октодерева 
каждый воксель можно рекурсивно делить на восемь частей. Это дает возможность просто и 
эффективно просчитывать необходимый уровень детализации для объектов, расположенных на 
разном расстоянии от камеры наблюдателя.

