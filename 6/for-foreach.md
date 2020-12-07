В Java существуют две формы цикла for. Первая — традиционная форма, вторая — форма for-each. Мы рассмотрим оба типа цикла for, начиная с традиционной формы.

Общая форма традиционного оператора for выглядит следующим образом:
```java
for (инициализация; условие; повторение) {
  // тело цикла
}
```
Если в цикле будет повторяться только один оператор, фигурные скобки можно опустить.

Цикл for действует следующим образом. При первом запуске цикла программа выполняет инициализационную часть цикла. В общем случае это выражение, устанавливающее значение управляющей переменной цикла, которая действует в качестве счетчика, управляющего циклом. Важно понимать, что выражение инициализации выполняется только один раз.  
Затем программа вычисляет условие, которое должно быть булевским выражением. Как правило, выражение условия сравнивает значение управляющей переменной с целевым значением. Если это значение истинно, программа выполняет тело цикла. Если оно ложно, выполнение цикла прерывается.  
Затем программа выполняет тело цикла и только после этого выполняется часть повторение цикла. Повторение это обычно выражение, которое увеличивает или уменьшает значение управляющей переменной.  
Затем программа повторяет цикл, при каждом прохождении вначале вычисляя условное выражение, затем выполняя тело цикла и выполняя выражение повторения. Процесс повторяется до тех пор, пока значение выражения условия не станет ложным.

Поскольку большинство циклов применяют свои переменные только внутри цикла, цикл for допускает, чтобы выражение инициализации было полным объявлением переменной. Таким образом, переменная ограничена телом цикла и невидима извне.

Приведем пару примеров поясняющих все вышесказанное:
```java
int i;
for (i = 0; i < 10; i++) {
  System.out.println("сейчас i = " + i);
}

System.out.println("i = " + i);
```
В этом примере переменная i объявлена вне цикла, поэтому она так же доступна после его завершения. А вот вывод данного примера:
```txt
сейчас i = 0
сейчас i = 1
сейчас i = 2
сейчас i = 3
сейчас i = 4
i = 5
```
Как видно из вывода приращение переменной i происходит после выполнения последней команды цикла, которая выводит значение i.

А теперь объявим переменную внутри цикла (оператора for):
```java
for (int i = 0; i < 10; i++) {
  System.out.println("сейчас i = " + i);
}

System.out.println("i = " + i); // i недоступна
```
При объявлении переменной внутри цикла for необходимо помнить о следующем важном обстоятельстве: область и время существования этой переменной полностью совпадают с областью и временем существования оператора for.

Синтаксис цикла for не ограничивается циклами с единственной переменной. Как в выражении инициализации, так и в выражении повторения можно использовать запятую для разделения нескольких выражений инициализации и повторения.
```java
int a;
int b;
for (a = 0, b = 4; a < b; a++, b--) {
  System.out.println("a = " + a);
  System.out.println("b = " + b);
}
```
В этом примере в инициализационной части цикла мы устанавливаем начальные значения обеих управляющих переменных a и b.

Цикл for поддерживает несколько разновидностей, которые увеличивают его возможности и повышают применимость. Гибкость этого цикла обусловлена тем, что его три части: инициализацию, проверку условий и итерационную не обязательно использовать только по прямому назначению. Фактически каждый из разделов оператора for можно применять в любых целях.

Стоит, так же, отметить, что любую из частей цикла for (инициализацию, условие и итерационную) или даже все сразу можно пропустить. Например, можно создать таким образом бесконечный цикл:
```java
for (;;) {
  // бесконечный цикл
}
```

## Оператор foreach
Начиная с версии JDK 5 в Java можно использовать вторую форму цикла for, реализующую цикл в стиле foreach ("для каждого"). 

Цикл в стиле foreach предназначен для строго последовательного выполнения повторяющихся действий по отношению к коллекциям объектов, например, таких как массивы. В Java возможность применения цикла foreach реализована за счет усовершенствования цикла for.  Общая форма версии foreach цикла for имеет следующий вид:
```java
for (тип итерационная переменная : коллекция) {
  // тело цикла
}
```
тип - это тип переменной;  
итерационная переменная — имя итерационной переменной, которая последовательно будет принимать значения из коллекции, от первого до последнего.  
коллекция - указывает коллекцию, по которой должен выполняться цикл. С циклом for можно применять различные типы коллекций, но пока мы будем использовать только массивы, кстати которые тоже пока не проходили, поэтому примеры использования foreach будут в теме массивов.

На заметку: оператор foreach применим к массивам и классам, реализующим интерфейс java.lang.Iterable.

На каждой итерации цикла программа извлекает следующий элемент коллекции и сохраняет его в итерационной переменной. Цикл выполняется до тех пор, пока не будут пройдены все элементы коллекции или пока не будет прерван с помощью оператора break;

Поскольку итерационная переменная получает значения из коллекции, ее тип должен совпадать (или быть совместимым) с типом элементов, хранящихся в коллекции. Таким образом, при выполнении цикла по массивам тип должен быть совместим с базовым типом массива.