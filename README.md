# Задания из курса СИКП в Массачусетском технологическом институте
Оригинальный курс изучается на языке Scheme, по-русски — Ским.  
Некоторые задания не имеют смысла, если делать их на другом языке программирования,
поэтому такие задания сделаны на нём, остальные – на Пайтоне и С++

## [Задание 1.2](/first_block/1.2/expression.scm)
Перевести выражение в префиксную форму
![equation](/first_block/1.2/expression.png)

**Решение**
```scm
(/ (+ 5 4 (- 2 (- 3 (+ 6 (/ 4 5)))))
   (* 3 (- 6 2) (- 2 7)))
```
> Результат => -0.24666666666666667

## [Задание 1.3](/first_block/1.3)
Написать процедуру, которая принимает три числа и возвращает сумму квадратов двух больших чисел.

**Решение  
Язык: Пайтон**
```py
def sum_of_squares_of_top_two(a, b, c):
    if a < b and a < c:
        return b ** 2 + c ** 2
    elif b < a and b < c:
        return a ** 2 + c ** 2
    else:
        return a ** 2 + b ** 2

```
**Язык: С++**
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
## [1.4](/first_block/1.4/add-with-abs.scm)
Как работает эта процедура
```scm
(define (a-plus-abs-b a b)
  ((if (> b 0) + -) a b))
```

**Решение**  
Если `b` больше нуля, то из `if` вернётся плюс, потом `a` сложится с `b`, `a + b`
Если `b` меньше или равен нулю, то из `if` вернётся минус, потом из `a` вычтится `-b`, `a - (-b) = a + b`
Эта процедура описывает сложение по модулю
