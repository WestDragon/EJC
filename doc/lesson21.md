# Lesson 21: Exercises

## Рекурсия
Рекурсия - определение части функции (метода) через саму себя, то есть это функция, которая вызывает саму себя, непосредственно (в своём теле) или косвенно (через другую функцию).
Источник: [https://habrahabr.ru/post/275813/](Рекурсия. Тренировочные задачи).
Для написания рекурсивного метода/функции необходимо:
- Определить условие выхода (Recursion termination = exit condition)
- Определить шаг рекурсии (Recursion step)

**Натуральное число** - от лат. "naturalis", которое переводится как "естественный". Т.е. это числа, возникающие естественным образом при счёте (например, 1, 2, 3, 4).
Ноль к таким числам не относится.

**Факториал** - произведение всех натуральных чисел до указанного числа n включительно. Т.к. 0 не натуральное число, то от 1 до n.

**Числа фибоначчи** - последовательность чисел, в которой первые два числа равны либо 1 и 1, либо 0 и 1, а каждое последующее число равно сумме двух предыдущих чисел. Названы в честь средневекового математика Леонардо Пизанского (известного как Фибоначчи).
Материал: "[Практика на Java: Числа Фибоначчи](https://stepik.org/lesson/15831/step/1)".
"[5 способов вычисления чисел Фибоначчи: реализация и сравнение](https://habrahabr.ru/post/261159/)".

**Ханойская башня** - игра, придуманная французским математиком Эдуардом Люком.
Условие:
```Даны три стержня, на один из которых нанизаны восемь колец, причём кольца отличаются размером и лежат меньшее на большем. Задача состоит в том, чтобы перенести пирамиду из восьми колец за наименьшее число ходов на другой стержень. За один раз разрешается переносить только одно кольцо, причём нельзя класть большее кольцо на меньшее.```
[Ханойская башня на пальцах](https://habrahabr.ru/post/200758/)
[ITVDN : Ханойская башня](https://www.youtube.com/watch?v=D1B_2iz8Oi4&app=desktop)

Примеры решений: [Recursion.java](..\workspace\exercises\src\main\java\ru\github\vastap\Recursion.java)