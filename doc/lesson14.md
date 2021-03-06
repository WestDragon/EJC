# Lesson 14: Time Complexity

## Введение
В информатике временная сложность (**time complexity**) алгоритма определяет время работы, используемое алгоритмом, как функции от длины строки, представляющей входные данные. Временная сложность алгоритма обычно выражается с использованием нотации «O» большое.
К основным временным сложностям относят:
- Постоянное время: O(1)
- Линейное время O(n)
- Квадратичное время O(n^2)
- Логарифмичное время O(log n)
- Линейно-логарифмическое время O(n log n)

Можно, конечно, запоминать, какая сложность у какого логарифма, но это бесполезная трата ресурсов. Куда интереснее понять, чтобы можно было оценить приблизительно временные затраты на выполнение кода и выбрать правильную реализацию.

## Постоянное время
Постоянное время, указываемое как O(1) не зависит от размера входных данных.
Примером постоянного времени, или же константного, является операция доступа к элементу массива по индексу. Такая операция будет выполняться с одинаковой скоростью вне зависимости от индекса.
**Доступ**, при котором обращение **к любому** элементу последовательности выполняется за равные промежутки времени, которые не зависят от размеров последовательности, называется **произвольным доступом** или **случайным доступом** (**random access**).
В Java даже есть особый интерфейс: **java.util.RandomAccess**. Например, его реализуют ArrayList и Vector, т.к. они являются по сути надстройко над массивом. А массив предоставляет констатное время обращения по индексу.
Важно, что O(1) выполняется любая операция, выполнение которой не зависит от размера входных данных. Например, получение размера массива. Или получение размера коллекций, т.к. он хранится в отдельной переменной и не требует обхода всех элементов.

## Линейное время
Линейное время обозначается как O(n), показывая что временная сложность зависит от n - числа входных данных (кол-ва объектов).
Предположим, у нас есть задача: Найти количество всех положительных чисел в массиве
```java
public static int countPositiveNumbers(int[] array) {
	int summ = 0;
	for (int i = 0; i < array.length; i++) {
		if (array[i] > 0) {
			summ++;
		}
	}
	return summ;
}
```
Как видно, наше решение линейно зависит от количества элементов. При 5 элементах мы 5 раз выполним сравнение с нулём, а при 100 элементах - 100 раз.

## Квадратичное время
Квадратичное время обозначается как O(n), подразумевая, что время возрастает не линейно, а по экспоненте.
Примером могут служить сортировки, например: обменная, вставками, выбором.
Вспоминаем сортировку выбором:
```java
public static void selectionSort(int[] source) {
	System.out.println(Arrays.toString(source));
	for (int i = 0; i < source.length; i++) {
		int minIndex = i;
		for (int min = i+1; min < source.length; min++) {
        	if (source[min] < source[minIndex]) {
				minIndex = min;
			}
		}
		if (i != minIndex) {
			swap(source, i, minIndex);
		}
	}
}
```
Как видно, сначала это было линейная временная сложность, т.к. цикл по каждому элементу. Логично, что такой цикл линейно зависит от количества элементов, т.е. чем больше массив, тем дольше будет по нему идти цикл.
Далее, мы видим цикл внутри цикла, который проходится внутри первого цикла, пробегая по другим элементам. И вот как раз этот цикл и создаёт квадратичную временную сложность.
В статье "[Введение в анализ сложности алгоритмов (часть 2)](https://habrahabr.ru/post/195482/)" можно увидеть такую рекомендацию:
``
Практическая рекомендация: простые программы можно анализировать с помощью подсчёта в них количества вложенных циклов.
``

## Логарифмическое время
Такая временная сложность обозначается как O(log n).
Развёрнутое объяснение хорошо дано в статье "[Введение в анализ сложности алгоритмов (часть 3)](https://habrahabr.ru/post/195996/)".
Первое, что стоит вспомнить, так это то, что же такое логарифм.

Допустим, возьмём число 1024. Если возвести 2 в степень 10, то мы как раз его и получим. И логарифмы призваны для того, чтобы помочь описать это.
В данном случае, 10 является логарифмом 1024 и записывается как log(1024).
Т.е. отвечает на вопрос: В какую степень нужно возвести 2, чтобы получить n.
Примером может служить бинарный поиск. Потому что в нём каждый шаг элементы делятся пополам.
Т.е:
``
1-я итерация: n / 2
2-я итерация: n / 4 (2^2)
3-я итерация: n / 8 (2^3)
``
Получается, что номер итерации соответствует степени двойки.
Поэтому, i-я итерация будет равна: n / 2^i
Алгоритм завершает свою работу, пока после деления не останется 1 элемент.
Тогда, такое записать можно как: ``1 = n / 2^i``, т.е. на некоторой i итерации мы получим при делении 1.
Получается, что 2^i = n, а это ничто иное как i = log(n)
Немного про логорифмы: "[Logarithms... How? (mathbff)](https://www.youtube.com/watch?v=ZIwmZ9m0byI)".

## Линейно-логарифмическое время
Такая временная сложность обозначается как O(n log n).
Такая временная сложность свойственно тем алгоритмам, где происходит рекурсивное деление пополам и при этом для каждой части выполняются какие-то действия.
Например: QuickSort и MergeSort
Подробное описание смотреть, как обычно, в статье: "[Введение в анализ сложности алгоритмов (часть 4)](https://habrahabr.ru/post/196226/)".
