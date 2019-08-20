# Задания из курса СИКП в Массачусетском технологическом институте
Оригинальный курс изучается на языке Scheme, по-русски — Ским.  
Некоторые задания не имеют смысла, если делать их на другом языке программирования,
поэтому такие задания сделаны на нём, остальные – на Пайтоне и С++

## [Задание 1.2](/chapter_1/1.2/expression.scm)
Перевести выражение в префиксную форму

![Картинка выражения](/chapter_1/1.2/expression.png)

**Решение**  
**_Язык: Ским_**
```scm
(/ (+ 5 4 (- 2 (- 3 (+ 6 (/ 4 5)))))
   (* 3 (- 6 2) (- 2 7)))
```
> Результат => -0.24666666666666667

## [Задание 1.3](/chapter_1/1.3)
Написать процедуру, которая принимает три числа и возвращает сумму квадратов двух больших чисел.

**Решение  
_Язык: Пайтон_**
```py
def sum_of_squares_of_top_two(a, b, c):
    if a < b and a < c:
        return b ** 2 + c ** 2
    elif b < a and b < c:
        return a ** 2 + c ** 2
    else:
        return a ** 2 + b ** 2

```
**_Язык: С++_**
```c++
int sum_of_squares_of_two_top(int a, int b, int c) {
  if (a < b && a < c) {
    return square(b) + square(c);
  }
  else if (b < c && b < a) {
    return square(a) + square(c);
  }
  else {
    return square(a) + square(b);
  }
}
```
## [Задание 1.4](/chapter_1/1.4/add-with-abs.scm)
Как работает процедура `a-plus-abs-b`
```scm
(define (a-plus-abs-b a b)
  ((if (> b 0) + -) a b))
```

**Решение**  
Может быть только два варианта: `b > 0` и `b <= 0`  
1. `b > 0`.  
Из условия возвращается `+`, тело функции вычисляется в `a + b`  
2. `b <= 0`.  
Из условия возвращается `-`, тело функции вычисляется в `a - (-b) = a + b`  

Эта процедура описывает сложение `a` с модулем `b`, она работает потому что для
скима плюс и минус такие же структуры языка, как переменные.


## [Задание 1.5](/chapter_1/1.5/)
В МИТе придумали тест для интерпретатора. После его выполнения становится понятно с каким порядком
вычислений работает интерпретатор.  
**Решение**  
**_Язык: Пайтон_**  

**_Язык: С++_**  

**_Язык: Ским_**  


Если интерпретатор работает с апликативным порядком вычислений, то он упадет от бесконечной рекурсии.  
Прежде чем выполнять тело функции, он попытается вычислить рекурсивную функцию `p`.  

Если интерпретатор работает с нормальным порядком вычислений, то он вернёт ноль.
Он сразу зайдет в тело функции, вычислит предикат и вернёт ноль.


## [Задание 1.6]()  
Лиза не понимает, почему `if` должна быть особой формой, ведь ее можно реализовать через `cond`. Подруга Лизы Ева пишет реализацию `if` через `cond`
```
(define (new-if predicate then-clause else-clause)
  (cond (predicate then-clause)
        (else else-clause))
)
```

`(new-if (= 2 3) 5 0)` => 0
`(new-if (< 2 3) 5 0)` => 5

Лиза переписывает программу для вычисления квадратного корня через `new-if`.
```
(define (sqrt-iter guess x)
  (new-if (good-enough? guess x)
          guess
          (sqrt-iter (improve guess x) x))
)
```
Что получится при выполнении процедуры?

**Решение**
Интерпретатор упадет от бесконечной рекурсии потому что работает с апликативным порядком вычислений.  
Прежде чем выполнять тело функции `new-if`, он попытается вычислить все аргументы и начнёт бесконечно вызывать функцию `sqrt-iter`

## [Задание 1.7]()


## [Задание 1.8]()
