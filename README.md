##Счетчики покрытия JaCoCo
**INSTRUCTION**

Наименьшая единица отсчета JaCoCo - это инструкции одиночного байтового кода Java. Покрытие инструкций предоставляет информацию об объеме кода, который был выполнен или пропущен. Эта метрика полностью независима от исходного форматирования и всегда доступна, даже при отсутствии отладочной информации в файлах классов.

**BRANCHES**

JaCoCo также рассчитывает покрытие ветвей для всех операторов if и switch. Эта метрика подсчитывает общее количество таких ветвей в методе и определяет количество выполненных или пропущенных ветвей. Покрытие веток всегда доступно, даже при отсутствии отладочной информации в файлах классов. Обратите внимание, что обработка исключений не рассматривается как ветки в контексте этого определения счетчика.

Если файлы классов были скомпилированы с отладочной информацией, точки принятия решения могут быть сопоставлены с исходными строками и выделены соответствующим образом:

* Нет покрытия: нет ответвлений в линии (красный ромб)
* Частичное покрытие: выполнена только часть ветвей в линии (желтый ромб)
* Полное покрытие: все ответвления в линии выполнены (зеленый ромб)

**LINES**

Для всех файлов классов, которые были скомпилированы с отладочной информацией, можно рассчитать информацию о покрытии для отдельных строк. Исходная строка считается выполненной, когда была выполнена хотя бы одна инструкция, назначенная этой строке.

В связи с тем, что одна строка обычно компилируется в инструкции с несколькими байтами, выделение исходного кода показывает три разных состояния для каждой строки, содержащей исходный код:

* Нет покрытия: ни одна инструкция в строке не была выполнена (красный фон)
* Частичное покрытие: выполнена только часть инструкции в строке (желтый фон)
* Полное покрытие: все инструкции в строке выполнены (зеленый фон)

В зависимости от форматирования исходного кода одна строка исходного кода может относиться к нескольким методам или нескольким классам. Следовательно, количество строк методов нельзя просто сложить, чтобы получить общее количество для содержащего класса. То же самое верно и для строк нескольких классов в одном исходном файле. JaCoCo рассчитывает покрытие строк для классов и исходного файла на основе фактически охваченных строк исходного кода.

**CYCLOMATIC COMPLEXITY**

JaCoCo также вычисляет цикломатическую сложность для каждого неабстрактного метода и суммирует сложность для классов, пакетов и групп. Согласно определению МакКабе 1996, цикломатическая сложность - это минимальное количество путей, которые могут в (линейной) комбинации генерировать все возможные пути с помощью метода. Таким образом, значение сложности может служить индикатором количества примеров модульного тестирования, которые полностью охватывают определенную часть программного обеспечения. Показатели сложности всегда можно рассчитать, даже при отсутствии отладочной информации в файлах классов.

Формальное определение цикломатической сложности v (G) основано на представлении графа потока управления метода в виде ориентированного графа:

v (G) = E - N + 2

Где E - количество ребер, а N - количество узлов. JaCoCo рассчитывает цикломатическую сложность метода с помощью следующего эквивалентного уравнения на основе количества ветвей (B) и количества точек принятия решения (D):

v (G) = B - D + 1

На основании статуса покрытия каждого филиала JaCoCo также рассчитывает покрываемую и пропущенную сложность для каждого метода. Пропущенная сложность снова указывает на количество тестовых примеров, которые отсутствуют для полного покрытия модуля. Обратите внимание, что поскольку JaCoCo не учитывает обработку исключений, блоки try / catch веток также не увеличивают сложность.