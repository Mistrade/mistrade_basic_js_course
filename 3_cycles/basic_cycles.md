# Тема: Базовые циклы

Тайминг: 1 час 30 минут.

## Дорожная карта занятия

* [Что такое цикл и зачем оно нам надо?](#what_is)
* [Цикл `for`](#for)
    * [Как работает цикл `for`?](#how_work_for)
    * [Как создать бесконечный цикл, используя `for`?](#infinity_for)
* [Цикл `while`](#while)
    * [Как работает цикл `while`?](#how_work_while)
    * [Как создать бесконечный цикл, используя `while`?](#infinity_while)
* [Цикл `do...while`](#do_while)
    * [Как работает цикл `do...while`?](#how_work_do_while)
* [Директивы `break` и `continue`](#break_continue)
* [В каких задачах могут использоваться циклы?](#when_use_it)
* [Как определить, какой цикл использовать?](#what_use)
* [Итого](#result)
* [Тренировка](#trains)
* [Домашнее задание](#homework)

## <a id="what_is">Что такое цикл?</a>

> **Цикл** - это механизм, позволяющий выполнять определенный набор инструкций `n` раз.
> Пример из жизни: Сделать 50 приседаний.
> Каждое повторение приседания - это итерация. А в совокупности - цикл,
> т.к. мы выполняем одно и то же действие 50 раз.

Как это реализовать в коде?

```javascript
//Объявляем функцию, которая будет выполнять 1 приседание.
function sitDown() {
    // набор инструкций, который надо сделать чтобы присесть
}

//Запускаем цикл на 50 итераций
for (let i = 1; i <= 50; i++) {
    //На каждой итерации, выполняем 1 приседание
    sitDown()
}
```

## <a id="for">Цикл `for`</a>

В данном примере мы использовали цикл `for` - он удобен, когда у нас есть количество итераций,
которое необходимо сделать.
В круглых скобках после слова `for`, мы указываем стартовое значение счетчика цикла (`let i = 1`),
условие выхода из цикла (`i <= 50`) и шаг цикла, который будет увеличивать наш счетчик после каждой выполненной
итерации (`i++`).

Формула:

```javascript
for (/* начальное значение счетчика итераций */; /* условие выхода из цикла */; /*; шаг цикла */) {
    //Тело цикла
}
```

В отличие от функций, в круглых скобках цикла, аргументы передаются через точку с запятой - `;`.

**Важная особенность**, любую из частей, заключенную в круглые скобки цикла `for` можно пропустить:

```javascript
for (let i = 0; ; i++) {
    console.log(i)
}
```

В данном примере мы не стали указывать условие выхода из цикла и этот цикл будет крутиться бесконечно.
Ровно такое же поведение будет и у цикла `for`, если вообще не указывать параметры, однако `;` обязательно должны
присутствовать, иначе будет ошибка синтаксиса.

### <a id="how_work_for">Как работает цикл `for`?</a>

Чтобы понять, как он работает, разберем дословно что написано в конструкции цикла `for`:

Запусти цикл, стартовое значение счетчика итераций которого = `1` (т.к. мы объявили там переменную `let i = 1`),
выполняй блок кода, который помещен в фигурные скобки `{` `}` столько раз,
пока условие выхода из цикла `i <= 50` не будет `false` (то есть пока `i <= 50` - цикл будет выполняться, когда
значение `i`
будет 51, код внутри фигурных скобок перестанет выполняться), и после каждого успешного выполнения кода,
заключенного в фигурные скобки, увеличь значение счетчика на единицу `i++` (подробнее
про [инкременты и декременты](https://learn.javascript.ru/operators#inkrement-dekrement)).

Разберем пример работы цикла построчно:

```javascript
//Цикл, выводящий в консоль 3, 2, 1, 0
for (let i = 3; i >= 0; i--) {
    console.log(i)
}
```

- Когда код начнет выполняться, JS увидит, что стартовое значение счетчика цикла `= 3`
- Затем JS проверит `3 >= 0` в данном случае это правда, поэтому выполнится `console.log(i)` и будет выведено `3`
- Выполнится декремент `i--`, значение счетчика уменьшится на единицу и станет `2`
- Проверка условия `2 >= 0`, снова `true`, в консоль выводится `2`.
- Выполнится декремент `i--`, значение счетчика уменьшится на единицу и станет `1`
- Проверка условия `1 >= 0`, снова `true`, в консоль выводится `1`.
- Выполнится декремент `i--`, значение счетчика уменьшится на единицу и станет `0`
- Проверка условия `0 >= 0`, снова `true`, в консоль выводится `0`.
- Выполнится декремент `i--`, значение счетчика уменьшится на единицу и станет `-1`
- Проверка условия `-1 >= 0`, теперь условие вернет `false` так как -1 не больше, чем 0 и не равен 0.
- Код `console.log(i)` более выполнен не будет, цикл остановится.

> Если коротко, то суть работы конструкции цикла, заключается в том, чтобы выполнять одно и то же действие
> до тех пор, пока условие выхода из цикла не станет `false`.

### <a id="infinity_for">Как создать бесконечный цикл, используя `for`?</a>

На самом деле, создать бесконечный цикл очень просто, но делать так лучше не стоит.
Также, бывают ситуации, когда программист по невнимательности допускает ошибку и создает бесконечный цикл.

Рассмотрим пример:

```javascript
for (let i = 0; i >= 0; i++) {
    console.log(i)
}
```

Данный пример будет выполняться бесконечно, пока мы принудительно не остановим его, например - закрыв вкладку браузера.

Почему?
Потому что мы задаем стартовое значение `= 0`, условие выхода из цикла `>= 0`, а после каждой итерации счетчик будет
увеличиваться на `1`. Таким образом `i` всегда будет `>= 0` и цикл никогда не закончится, т.к. условие выхода из цикла
никогда не вернет `false`.

## <a id="while">Цикл `while`</a>

Еще одной из базовых конструкций циклов - цикл `while`. Данный цикл удобен, в тех случаях, когда нужно выполнять
одно и то же действие до тех пор, пока условие выхода из цикла не станет `false`, но стоит быть аккуратными с
использованием

Если перевести конструкцию while на наш, человеческий язык, то будет звучать примерно так:
**Пока (условие выхода из цикла == true) делай { то, что написано тут }.**

```javascript
let condition = true;

while (condition) {
    //делай это
}
```

Любое выражение или переменная может быть условием цикла, а не только сравнение: условие `while` вычисляется и
преобразуется в логическое значение.

Например, `while (i)` – более краткий вариант `while (i != 0)`:

```javascript
let i = 3;
while (i) { // когда i будет равно 0, условие станет ложным, и цикл остановится
    alert(i);
    i--;
}
```

### <a id="how_work_while">Как работает цикл `while`?</a>

Цикл `while` работает следующим образом:
Проверяется условие выхода из цикла, помещенное в **круглые скобки** после ключевого слова `while`. Если
выражение/переменную удалось конвертировать в `true`, то выполнится блок кода, а иначе - цикл остановится.

Таким образом, цикл `while` может не выполнить ни одной итерации, если при первой же итерации условие будет приравнено
к `false`.

### <a id="infinity_while">Как создать бесконечный цикл, используя `while`?</a>

```javascript
while (true) {
    //do something...
}
```

Очень легко, пока результат выражения в круглых скобках может быть приравнен к `true`, цикл будет крутиться.
**Делать так, конечно же, не стоит!**

## <a id="do_while">Цикл `do...while`</a>

Цикл `do...while` работает похожим образом, как и `while` с одним существенным отличием.
Если цикл `while` - сначала проверяет условие выхода из цикла, а затем выполняет код, то `do...while` работает
наоборот - сначала выполняет код в блоке `do`,
затем проверяет условие из круглых скобок блока `while`, рассмотрим пример:

```javascript
let i = 0
do {
    console.log('Hello, world!')
    i++
} while (i < 3)
```

По правде говоря, в реальной разработке, достаточно редко можно встретить ситуации, когда использование
цикла `do...while` будет оправданным.

### <a id="how_work_do_while">Как работает цикл `do...while`?</a>

Цикл `do...while` работает следующим образом:
Сначала выполняется блок кода, находящийся между фигурными скобками `do`.
После того как весь этот код будет выполнен, произойдет проверка условия выхода из цикла, которое указывается в круглых
скобках блока `while`. Если условие вернуло `true`, то выполнится еще одна итерация блока `do`, иначе - цикл
остановится.

Таким образом, вне зависимости от того, каким будет результат выражения условия выхода из цикла, цикл `do...while`
выполнит
как минимум 1 итерацию.

## <a id="break_continue">Директивы `break` и `continue`</a>

Бывают случаи, когда нам нужно остановить цикл до того, как выполнится условие выхода из цикла.

Например: Нам нужно прозвонить всю телефонную книгу, чтобы продать 10 книг, которые лежат на нашей полке в
шкафу и пылятся. В телефонной книге 1.000 номеров.
Однако, 10 продаж мы можем сделать еще до того, как прозвоним всю телефонную книгу и звонить дальше смысла уже не
будет - книг не осталось.
В таких случаях к нам на помощь придет директива `break`.

Данная директива позволяет нам остановить работу цикла. Выглядит это следующим образом, рассмотрим тот же пример:

```javascript
let soldBooksCount = 0; //До того, как мы начали звонить - мы не продали ни одной книги.
const phoneNumbersCount = 1000; //Количество номеров в телефонной книге

for (let i = 0; i < phoneNumbersCount; i++) { //Запускаем цикл на 1000 итераций
    const randomValue = !!Math.random(); //Создаем рандомное boolean значение (продано или нет)

    if (randomValue) { //Если книга была продана по данному номеру телефона
        soldBooksCount++; // то увеличиваем количество проданных книг на единицу
    }

    if (soldBooksCount === 10) { //Как только количество проданных книг станет 10
        //Дальше звонить не имеет смысла, поэтому мы останавливаем цикл
        break;
    }
}
```

Или же наоборот, представим ситуацию, когда необходимо актуализировать номера в телефонной книге. Те же 1.000 номеров.
Если абонент взял трубку - то мы оставляем его в телефонной книге, а иначе - удаляем. В данной задаче, нам поможет
директива `continue`,
которая пропустит выполнение кода текущей итерации, расположенного ниже директивы,
чтобы перейти на следующую итерацию.

Реализация в коде:

```javascript
let removedCount = 0; //До начала цикла, мы еще никого не удалили, поэтому 0.
const phoneNumbersCount = 1000; //Кол-во контактов в телефонной книге.

//Запускаем цикл на те же 1000 итераций, чтобы пройтись по всей телефонной книге
for (let i = 0; i < phoneNumbersCount; i++) {
    // Создаем рандомное значение - взял пользователь трубку или нет (boolean)
    const isConnected = !!Math.random()

    //Если абонент взял трубку, то мы ничего с ним не делаем, поболтали и пошли звонить дальше
    //то есть - пропустили итерацию удаления
    if (isConnected) {
        continue;
    }

    //Иначе удаляем абонента из телефонной книги
    removedCount++
}
```

## <a id="when_use_it">В каких задачах могут использоваться циклы?</a>

В данном вопросе стоит отталкиваться от того, что такое цикл. Как мы ранее выяснили - цикл, это механизм позволяющий
выполнять
один и тот же код `n`-ое количество раз.
Соответственно, если задача требует перебора каких-либо значений, то в данной ситуации в решении задачи стоит обратить
внимание на циклы.
Но, не всегда.

## <a id="what_use">Как определить, какой цикл использовать?</a>

В большинстве случаев, цикл `for` может быть использован для решения задачи, требующей циклической логики,
но бывают более частные случаи, когда нам может понадобиться цикл `while`:

- Нам неизвестно количество итераций и нет переменной, в которой может быть сохранено это значение.
- Отсутствие счетчика цикла, например нужно что-то делать, пока не произойдет какое-либо событие.
- Вам просто нравится конструкция `while`.

Это лишь приблизительный список тех ситуаций, когда `while` может быть приоритетнее, чем `for`, однако в большинстве
случаев,
эти же задачи можно решить через `for`, просто это будет более сложный и громоздкий код.

## <a id="result">Итого</a>

Ключевые моменты, о которых мы узнали на сегодняшнем занятии:

- Существует 3 базовых вида цикла: `for`, `while`, `do...while`.
- Цикл `while` - сначала проверяет условие, потом выполняет код.
- Цикл `do...while` - сначала выполняет код, затем проверяет условие.
- Цикл `for` - сначала проверяет условие, затем выполняет код, есть возможно задавать дополнительные настройки.
- Следует быть внимательнее к условиям выхода из цикла, так как неверное условие может привести к бесконечному циклу.
- Чтобы остановить цикл, мы можем использовать директиву `break`.
- Чтобы пропустить итерацию цикла, мы можем использовать директиву `continue`.

## <a id="trains">Тренировка</a>

- Для чего нужны циклы?
- Почему бесконечный цикл - это зло?
- Каким разделительным знаком отделяются параметры в цикле `for`?
- До каких пор цикл `while` будет выполнять код?
- В чем основная разница между `do...while` и `while`?
- Что выведет код ниже?
  ```javascript
  let i = 0;
  while (i < 3){
    console.log(i)
    i++
  }
  ```
- Что не так с этим циклом?
  ```javascript
  for(let i = 0; i >= 0;){
    console.log(i)
  }
  ```
- Что выведет код ниже?
  ```javascript
  let i = 0;
  do{
    console.log(i)
    i++
  } while(false)
  ```

## <a id="homework">Домашнее задание</a>

В качестве **обязательной** части домашнего задания, необходимо решить задачи 1 - 3
из [этого репозитория](https://github.com/Mistrade/mistrade_js_tasks/blob/main/cycles/easy.level.js).

В качестве **дополнительной** части домашнего задания, решить задачу:
Напишите функцию, которая возвращает массив нечетных чисел в диапазоне от `min` до `max`, где `min` - минимальное число,
а `max` - максимальное. При этом, если значение `min` больше, чем значение `max` - то возвращать пустой массив не
выполняя ни одной итерации цикла. 















