# Graph_drawer
Проект реализван для отрисовки графиков введённых функций и некоторых стандартных (sin, cos). 
Основными задачами в данном проекте являлись:
  1. Создание парсера строки в мат. выражение
  2. Отрисовка графика функций в заданном диапазоне
  
Для решения первой задачи был создан класс TLexem, полями которого являются символьная строка и тип считываемого выражения (целое число, дробное число, мат. функция и т.д.). Анализ строки позволяет позволяет разбить ее на массив объектов TLexem. Далее мы создаем из этого массива бинарное дерево, опираясь на приоритеты мат. операций, что в конечном итоге позволяет посчитать результат выражения (вместо x подставляется число). В функции parse реализована проверка на правильность выражения, таким образом, при некорректном вводе пользователь увидит сообщение об ошибке и её тип (не закрыта скобка; неверно записано выражение, пример: 1+/х и т.п.), после чего сможет исправить ошибки.

Второй пункт легко решается с помощью класса QPainterPath - реализуем отрисовку линий между вычесленными значениями x и y. Задаем область для отображение графиков, рісуем там оси x y. X вычисляется с учётом заданных границ max min и точности (шаг = 1/точность), Y вычисляется для каждой точки посредством парсинга введённого выражения с x соответствующем каждому шагу. В цикле вычисляем результат, после чего с помощью lineTo строим линии между точками (в случае, если при данном x функция не существует, перемещаем точку с помощью moveTo в следующую позицию без отрисовки линии).
