# Тема: Функции

Тайминг: 1 час 30 минут.

## Дорожная карта занятия

* [Что такое функции и для чего они нужны?](#what_is_functions)
* [Способы объявления функций](#variants)
* [Копирование функций](#copy)
* [Нейминг функций](#naming)
* [Итого](#result)
* [Тренировка](#trains)
* [Домашнее задание](#homework)

## <a id="what_is_functions">Что такое функции и для чего они нужны?</a>

Представьте, что вам нужно выполнять одну и ту же логику несколько раз в разных участках вашего приложения.
Как быть? Копировать? Писать заново?
Так ведь можно и с ума сойти, прежде чем запомнишь откуда и что копировать раз за разом.

Сейчас мы рассмотрим инструмент, позволяющий заготовить определенную логику
и переиспользовать ее в любом месте нашего приложения.

Встречайте - Функции!
Функции работают как **мини-программы**.
Сначала объявляем функцию, указываем какие входные данные хотим получить,
затем пишем логику, которую должна выполнить функция, когда мы ее вызовем,
после чего мы можем вернуть или не возвращать какое-либо значение (строку/число/объект - что угодно)
в то место программы, где эта функция была вызвана.

Примеры:

```javascript
function sayHello /* function name */(message /* args */) {
    // function body
    alert(`Hello! ${message}`);
}

function sum /* function name */(a, b /* args */) {
    // function body
    return a + b
}

function multiply /* function name */(a, b /* args */) {
    // function body
    return a * b
}
```

В данном примере мы объявили 3 функции: `sayHello`, `sum`, `multiply`.
Объявили - означает что мы создали, но еще не вызывали эту функции.
Они просто зарегистрировались в оперативной памяти и при необходимости, мы сможем обратиться
к нужной нам функции по ее имени, например: `sayHello`.

Разберемся в коде:

- `/* args */` - места, где мы принимаем аргументы функции. Аргументы - это входные данные,
  которые мы передадим в функцию, в момент ее вызова. Аргументы указываются в круглых скобках
  и именуются произвольно, за некоторыми исключениями. О них поговорим позже.
  Если нам нужно принимать несколько аргументов, например 2 числа, то аргументы перечисляются через запятую.
  В функциях `sum` и `multiply` мы реализовали такой случай. Указав что мы хотим принять 2 аргумента - `a` и `b`.
- `/* function name */` - В этом месте указывается имя функции, по которому в будущем, к ней можно будет обратиться.
- `// function body ` - В этом месте пишется тело функции. Тот самый набор инструкций,
  который будет выполнен, когда мы запустим нашу функцию. Например: `return a + b` - это означает, что функция вернет
  результат сложения чисел `a` и `b` в то место, где мы вызвали функцию.

**Важно понимать**, что `return` прерывает выполнение функции и любой код, который стоит после(ниже) `return` (в теле
функции) выполнен не будет.

Рассмотрим последовательно, что будет происходить с момента объявления функции, до момента сохранения значения в
переменную:

```javascript
// Этап 1. Мы объявили функцию sum.
// В момент вызова функции, в нее нужно будет передать 2 аргумента - a, b.
// a, b - в данной функции, мы будем воспринимать как числа
// над которыми будем производить математическую операцию сложения.
function sum(a, b) {
    return a + b
}

//Этап 2. Создание переменной и присвоение ей значения.
const result = sum(3, 5)
/**
 * В данном случае в аргумент "a" - будет присвоено значение 3, а в "b" - 5.
 * Так как значение аргументам передаются ровно в том порядке,
 * в котором они объявлены - a, b = 3, 5 соответственно.
 * В переменную result присвоится значение 8.
 * Так как мы вызываем функцию sum, внутри нее выполняется сложение 3 + 5
 * Результат сложения возвращается в то место, где мы вызвали функцию, с помощью return
 * Соответственно вместо sum(3,5) в переменную result будет присвоено значение 8
 * Далее, ниже по коду мы можем работать с result как со значением 8
 * Например, выведем это число в консоль
 */

console.log(result) //будет выведено 8
```

--- **!!!Нарисовать схему, как работает вызов функции и присвоение аргументов!!!**

Используя функции, мы можем оборачивать повторяющуюся логику в них и переиспользовать функции там,
где нам это нужно, чтобы не дублировать код, сводя риски допустит ошибку лишь к одному месту - телу функции.

## <a id="variants">Способы объявления функций</a>

На данный момент - существует 3 способа объявить функцию:

### - Function Declaration (Объявление функции)

Это способ объявления функции, когда мы явно указываем название функции сразу после ключевого слова `function`.
Такой способ объявления функции имеет ряд отличий от остальных,
рассмотрим их в главе “Области видимости”.

Пример:

```javascript
function sayHello( /* args */) {
    // functions body
    alert('Hello!')
}
```

### - Function Expression (Функциональное выражение)

Данный синтаксис позволяет нам создавать новую функцию в середине любого выражения.
Это выглядит следующим образом:

```javascript
const sayHello = function ( /* args */) {
    // function body
    alert('Hello!');
}
```

В JavaScript, функция - это значение. Поэтому мы можем свободно присваивать, в виде значения переменной - функцию.
Если выполнить следующий код, то в консоль будет выведен код функции текстом:

```javascript
console.log(sayHello)
```

Обратите внимание, что в этом примере мы не вызываем функцию `sayHello`, поскольку нет круглых скобок после имени
функции.
Соответственно мы не получим результат выполнения функции, а лишь передаем ссылку на ячейку оперативной памяти,
в которую записалась наша функция при ее объявлении.

**Важный момент**, поскольку `function expression` - это выражение, то рекомендуется ставить после закрывающей фигурной
скобки `;`.

### - Arrow Function (Стрелочная функция)

Это самый короткий способ объявления функций, с рядом ограничений и отличий от других способов объявления.
Выглядит следующим образом:

```javascript
const myFunc = (/* args */) => {
    // function body
}
```

Стрелочные функции, также позволяет писать "однострочный код", т.е. возвращать значение сразу, без
использования `return`.
Перепишем функцию `sum` используя стрелочную функцию:

```javascript
const sum = (a, b) => a + b
```

Если мы хотим сразу вернуть значение, то мы не указываем фигурные скобки и возвращаем результат вычислений сразу же
после `=>` символов.
Это будет аналогично записи:

```javascript
function sum(a, b) {
    return a + b
}
```

Если же нам нужно, чтобы стрелочная функция была "многострочной", то используем `{` `}` фигурные скобки сразу
после `=>`:

```javascript
const sum = (a, b) => {
    //какая-то дополнительная логика, может быть тут
    return a + b
}
```

## <a id="naming">Как правильно называть функции (Нейминг функций)</a>

В языках программирования, функции создаются для того, чтобы выполнить какое-то действие.
Поэтому зачастую, в названиях функций можно встретить глаголы.
Название функции должно отображать суть того, что делает эта функция, при этом желательно,
чтобы название было коротким, емким и понятным программисту, который будет читать код.
Как правило, в начале функций, указывается какой-либо глагольный префикс, после которого идет уточнение.
Например, функции, начинающиеся с `is...` обычно проверяют, является ли переданное значение чем-либо,
а функции начинающиеся с `get` возвращают результат вычислений.

Вот наиболее распространенные примеры:

- `get...` - такие функции возвращают значение
- `show...` - такие функции показывают что-либо
- `is...` - такие функции проверяют, является ли значение чем-либо, например строкой.
- `check...` - такие функции проверяют что-то и возвращают логическое значение.
- `create...` - такие функции создают что-либо
- `remove...` - такие функции удаляют что-либо
- `calc...`  - такие функции вычисляют значение и возвращают его путем математических операций.
- и т.д.

Благодаря префиксам, при первом взгляде на имя функции становится понятным, что делает её код, и какое значение она
может возвращать.

> ### Одна функция - одно действие
> Функция должна делать только то, что явно подразумевается её названием. И это должно быть одним действием.
> Об этом нам говорит один из принципов [SOLID](https://ru.wikipedia.org/wiki/SOLID_(программирование)). Это первая
> буква S (Single Responsibility),
> что в переводе означает - принцип единственной ответственности. Согласно этому принципу,
> каждая функция должна выполнять лишь то, что указано в ее названии и ничего более.
>
> Два независимых действия обычно подразумевают две функции, даже если предполагается, что они будут вызываться вместе (
> в этом случае мы можем создать третью функцию, которая будет их вызывать).
>
> #### Правила хорошего и плохого тона (примеры):
> - `getAge` - такая функция должна вычислять возраст и возвращать его.
    Если в функции будет `alert()` или какие-либо другие не относящиеся к вычислениям и возврату значения действие -
    это будет плохая функция.
> - `showModal` - такая функция должна отобразить модальное окно для пользователя.
    Если в функции будет какая-либо лишняя логика, например обращение к серверу, чтобы узнать погоду то, это будет
    плохая функция.
> - `isEqual` - такая функция должна проверить, что ее входные аргументы точно совпадают друг с другом.
    Например, будет плохим выбором - реализовать в функции дополнительные вычисления по загрузке этих значений с сервера.
    Но хорошей реализацией будет вот такой пример: 
> ```javascript
> const isEqualString = (str1, str2) => {
>   //Функция проверят, что str1 и str2 полностью равны
>   //и возвращает boolean значение.
>   return str1 === str2
> }
> ```

## <a id="result">Итого</a>

Из того, что мы сегодня узнали, можно подвести следующие итоги:

- Функции являются неотъемлемой частью разработки.
- Функции позволяют переиспользовать ту или иную логику, которая была заложена в них.
- Передаваемые в функцию значения через запятую, становятся локальными переменными в теле функции.
- Функции могут возвращать значение в то место, где она была вызвана, с помощью ключевого слова `return`
- Название функции должно быть емким и информативным одновременно. Увидев название функции,
программист, должен понять, что делает эта функция.
- Одна функция = одно действие. Single Responsibility - говорит нам о том, что каждая функция,
должна соответствовать принципу единственной ответственности и выполнять одну, конкретную задачу.

На данном занятии мы лишь поверхностно рассмотрели основной инструментов написания кода - функции.
Это лишь начало пути.
Позже, мы будем углубляться в тонкости работы с функциями, например:
- Область видимости
- Hoisting
- Рекурсии
- Замыкания
- и т.д.

Но уже сейчас, мы научились создавать и работать с функциями, чтобы начать писать код с использованием этого инструмента

## <a id="trains">Тренировка</a>

- Как назвать функцию, которая вычисляет скорость и принимает 2 аргумента: время и расстояние?
- Как назвать функцию, которая проверит что ее аргумент `value` является числом и вернет `boolean` значение?
- С помощью какого ключевого слова мы можем вернуть значение из функции наружу, в то место, где была вызвана функция?
- Как передать аргументы в функцию?
- Как принимать аргументы в функции?
- Что выведет этот код:
    ```javascript
    const sayMyName = (name) => {
        alert(name)
    } 
        
    console.log(sayMyName)
    ```
- Что не так с этой функцией?
    ```javascript
    const sayHello = () => {
        alert('Hello!')
        alert('Занятие окончено, переходим к обсуждению домашнего задания!')
    } 
    ```
  
## <a id="homework">Домашнее задание</a>

1. Обязательное задание:
   - Выполнить задачи 1 - 3 по [ссылке](https://github.com/Mistrade/mistrade_js_tasks/blob/main/functions/easy.level.js)
   - Написать функцию и правильно назвать ее, которая принимает 2 аргумента (числа) - `a` и `b` и возвращает минимальное из них.
   - Написать функцию и правильно назвать ее, которая принимает 2 аргумента (числа) - `a` и `b` и возвращает максимальное из них.
2. Дополнительное задание:
   - Изучить базовые операторы и математические операции. Статья [тут](https://learn.javascript.ru/operators)
   - Изучить логические операторы. Статья [тут](https://learn.javascript.ru/logical-operators)

Код задания прислать в `.zip` архиве в [telegram](https://telegram.me/andreimistrade)





