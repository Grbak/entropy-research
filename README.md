# Entropy-Research

# Цель:
Уметь идентифицировать сжатые и зашифрованные файлы

# Техника:
```ShellSession
Использовать несколько алгоритмов для определения типа файла
Использовать статистические данные
Использовать статистические тесты случайности
```

# Алгоритмы:
```ShellSession
Кси-распределение 
Монте-Карло
```

# Методы: 
Энтропия данных может рассказать нам многое о содержании данных

<a href="https://savepice.ru/" target="_blank"><img src="https://cdn1.savepice.ru/uploads/2017/11/19/044a76df2758a2cea0bf24431e2350af-full.png" alt="" title="фотохостинг" border="0"/></a>

Но не все алгоритмы сжатия одинаковы, и некоторые сжатые данные могут быть очень трудно визуально отличить от зашифрованных данных

<a href="https://savepice.ru/" target="_blank"><img src="https://cdn1.savepice.ru/uploads/2017/11/19/31ee39023f830c53f279d6ec44f31e68-full.png" alt="" title="фотохостинг" border="0"/></a>

# Кси-распределение:
Показывает отклонение наблюдаемых результатов от ожидаемых результатов
Существенные отклонения от ожидаемых значений действительно случайных данных указывают на отсутствие случайности


# Монте-Карло:
Используется для аппроксимации значения pi из заданного набора случайных (x, y) координат
Очень точные pi-аппроксимации указывают на очень случайный набор точек данных

# Определение типа файла

Применение этих тестов к образцу файлов с различными алгоритмами сжатия, шифрования показало следующие корреляции:
```ShellSession
# Большие отклонения в распределении хи-квадрат или большие проценты погрешности в приближении Монте-Карло являются уверенными признаками сжатия

# Очень точные вычисления pi (погрешность 0,01%) являются достоверными признаками шифрования

# Нижние значения chi (<300) с более высокой ошибкой pi (> 0,03%) указывают на сжатие

# Более высокие значения chi (> 300) с более низкими ошибками pi (<0,03%) указывают на шифрование
```

Например, здесь приведено сравнение одного и того же файла 24 МБ после ввода алгоритмов AES, 3DES, gzip и lzma:

<a href="https://savepice.ru/" target="_blank"><img src="https://cdn1.savepice.ru/uploads/2017/11/19/88cac030aa7c550aff51c95f1988351f-full.png" alt="" title="фотохостинг" border="0"/></a>

# Демо-расчет
<a href="https://savepice.ru/" target="_blank"><img src="https://cdn1.savepice.ru/uploads/2017/11/19/9a5990e4e1737de4f4bbfd6a16b30f7e-full.png" alt="" title="фотохостинг" border="0"/></a>


# Tutorial 
```ShellSession
$ gcc ent.c chisq.c randtest.c iso8859.c -o ent 
$ ./ent «file»
```
