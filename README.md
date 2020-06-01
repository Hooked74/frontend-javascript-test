# Тестовое задание на позицию frontend-разработчик
При решении задания нельзя использовать готовые фреймворки и компоненты. Нас интересует как вы умеете решать подобные задачи и создавать что-то с нуля.

## Fizz-buzz задачи

### Задача №1

Написать функцию `dscount`, которая подсчитывает количество идущих подряд символов `s1` и `s2` в строке, без учёта регистра.

```js
function dscount(string, s1, s2) {
  // реализация функции
}

function test(fn, args, expResult, context) {
  const result = fn.apply(context, args);
  console.assert(result === expResult, `Test failed! Result: ${result}`);
}

test(dscount, ['ab___ab__', 'a', 'b'], 2);
test(dscount, ['___cd____', 'c', 'd'], 1);
test(dscount, ['de_______', 'd', 'e'], 1);
test(dscount, ['12_12__12', '1', '2'], 3);
test(dscount, ['_ba______', 'a', 'b'], 0);
test(dscount, ['_a__b____', 'a', 'b'], 0);
test(dscount, ['-ab-аb-ab', 'a', 'b'], 2);
test(dscount, ['aAa', 'a', 'a'], 2);
```

* Решение должно быть простым, умещаться в 1м файле и содержать не более 20 строк кода.
* Идеальное время решения на задачу не более 15 минут.

### Задача №2

Написать функцию `checkSyntax`, которая проверяет на синтаксическую верность последовательность скобок. Задача не сводится к простой проверке сбалансированности скобок. Нужно еще учитывать их последовательность (вложенность).

* Строка может содержать следующий набор скобок: `<,[,{,(`.
* В случае ошибки возвращаем 1.
* В остальных случаех возвращаем 0.

```js
function checkSyntax(string) {
  // реализация функции
}

function test(fn, args, expResult, context) {
  const result = fn.apply(context, args);
  console.assert(result === expResult, `Test failed! Result: ${result}`);
}

test(checkSyntax, ["---(++++)----"], 0);
test(checkSyntax, [""], 0);
test(checkSyntax, ["before ( middle []) after "], 0);
test(checkSyntax, [") ("], 1);
test(checkSyntax, ["} {"], 1);
test(checkSyntax, ["<(   >)"], 1);
test(checkSyntax, ["(  [  <>  ()  ]  <>  )"], 0);
test(checkSyntax, ["   (      [)"], 1);
```

* Решение должно быть простым, умещаться в 1м файле и содержать не более 30 строк кода.
* Идеальное время решения на задачу не более 30 минут.

### Задача №3

Написать функцию `anagram`, которая проверяет, являются ли анаграммами строки `s1` и `s2`. Анаграмма – слово или словосочетание, образованное путём перестановки букв, составляющих другое слово (или словосочетание).

```js
function anagram(s1, s2) {
  // реализация функции
}

function test(fn, args, expResult, context) {
  const result = fn.apply(context, args);
  console.assert(result === expResult, `Test failed! Result: ${result}`);
}

test(anagram, ["Воз", "зов"], true);
test(anagram, ["пила", "липа"], true);
test(anagram, ["Я в мире — сирота.", "Я Ариост в Риме."], true);
test(anagram, ["Аз есмь строка, живу я, мерой остр.", "За семь морей ростка я вижу рост"], true);
test(anagram, ["Чертог", "горечь"], false);
```

* Решение должно быть простым, умещаться в 1м файле и содержать не более 25 строк кода.
* Идеальное время решения на задачу не более 20 минут.

### Задача №4

Написать функцию `treeWalking`, которая делает обход по DOM дереву – начиная с элемента `root`, обходит все его дочерние элементы. Для каждого элемента дерева должен вызываться обработчик `handler`. Ключевое условие – не использовать рекурсию.

```html
<!-- DOM дерево, которое необходимо обойти -->
<div id="root">
  <div><span>1</span><span>2</span><span>3</span></div>
  <div>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
    </ul>
  </div>
</div>
```
Для корректного прохождения тестов в задании, DOM дерево необходимо минимизировать, чтобы избежать лишних текстовых нод.

```js
function treeWalking(node, handler) {
  // реализация функции
}

let counter = 0;

treeWalking(document.getElementById("root"), (node) => {
  // какая-то логика с данной нодой
  // ...
  counter++;
});

console.asset(counter === 16, `Test failed! Result: ${counter}`);
```

* Решение должно быть простым, умещаться в 1м файле и содержать не более 15 строк кода.
* Идеальное время решения на задачу не более 15 минут.

## Алгоритмы

### Задача №1

* Есть 2 сковороды для оладьев, каждая из которых вмещает ровно по 1 блинчику за 1 раз.
* Есть 3 панкейка (блинчика), которые надо пожарить.
* За 1 минуту жарится 1 сторона блинчика.
* Блинчики надо обжарить с 2х сторон.

Итерацией считать процесс жарки 1й стороны 2х блинчиков на 2х сковородах. Сколько нужно времени (итераций) при оптимальном распределении чтобы пожарить 3 панкейка?

Релизуйте ваш алгоритм в виде кода. Это может быть как ООП код, так и функциональный и даже процедурный. Выбор подхода обоснуйте.

Обязательно опишите алгоритм, как бы вы решали эту задачу в физическом мире (в какой момент и как жарили бы эти блинчики).

## Рефакторинг

Задачи на работу с чужим кодом.

### Задача №1

```js
function func(s, a, b) {

	if (s.match(/^$/)) {
		return -1;
	}
	
	var i = s.length -1;
	var aIndex =     -1;
	var bIndex =     -1;
	
	while ((aIndex == -1) && (bIndex == -1) && (i > 0)) {
	    if (s.substring(i, i +1) == a) {
	    	aIndex = i;
    	}
	    if (s.substring(i, i +1) == b) {
	    	bIndex = i;
    	}
	    i = i - 1;
	}
	
	if (aIndex != -1) {
	    if (bIndex == -1) {
	        return aIndex;
	    }
	    else {
	        return Math.max(aIndex, bIndex);
	    }
	}
	
	if (bIndex != -1) {
	    return bIndex;
	}
	else {
	    return -1;
	}
}
```

Что можно улучшить в данном коде? Как бы вы его переписали?

### Задача №2

```js
function drawRating(vote) {
	if (vote >= 0 && vote <= 20) {
    	return '★☆☆☆☆';
	}
	else if (vote > 20 && vote <= 40) {
		return '★★☆☆☆';
	}
	else if (vote > 40 && vote <= 60) {
		return '★★★☆☆';
	}
	else if (vote > 60 && vote <= 80) {
		return '★★★★☆';
	}
	else if (vote > 80 && vote <= 100) {
		return '★★★★★';
	}
}

// Проверка работы результата
console.log(drawRating(0) ); // ★☆☆☆☆
console.log(drawRating(1) ); // ★☆☆☆☆
console.log(drawRating(50)); // ★★★☆☆
console.log(drawRating(99)); // ★★★★★
```

Что можно улучшить? Как бы вы переписали функцию `drawRating`, при условии, что на вход функции должна приходить переменная `vote`, содержащая значение от 0 до 100. Интересует именно логика реализации функции, не визуальное отображение звезд.

## React

Задачи на работу с библиотекой React.

### Задача №1

Slomux — упрощённая, сломанная реализация Flux. Перед вами небольшое приложение, написанное на React + Slomux. Это нерабочий секундомер с настройкой интервала обновления.

Исправьте ошибки и потенциально проблемный код, почините приложение и прокомментируйте своё решение.
Идеальное время решения на задачу не более 25 минут.

```html
<div id="app" />
```

```js
const createStore = (reducer, initialState) => {
  let currentState = initialState;
  const listeners = [];

  const getState = () => currentState;
  const dispatch = action => {
    currentState = reducer(currentState, action);
    listeners.forEach(listener => listener());
  };

  const subscribe = listener => listeners.push(listener);

  return { getState, dispatch, subscribe };
};

const connect = (mapStateToProps, mapDispatchToProps) =>
  Component => {
    class WrappedComponent extends React.Component {
      render() {
        return (
          <Component
            {...this.props}
            {...mapStateToProps(this.context.store.getState(), this.props)}
            {...mapDispatchToProps(this.context.store.dispatch, this.props)}
          />
        );
      }

      componentDidUpdate() {
        this.context.store.subscribe(this.handleChange);
      }

      handleChange = () => {
        this.forceUpdate();
      }
    }

    WrappedComponent.contextTypes = {
      store: PropTypes.object,
    };

    return WrappedComponent;
  };

class Provider extends React.Component {
  getChildContext() {
    return {
      store: this.props.store,
    };
  }
  
  render() {
    return React.Children.only(this.props.children);
  }
}

Provider.childContextTypes = {
  store: PropTypes.object,
};

// APP

// actions

const CHANGE_INTERVAL = 'CHANGE_INTERVAL';

// action creators

const changeInterval = value => ({
  type: CHANGE_INTERVAL,
  payload: value,
});


// reducers

const reducer = (state, action) => {
  switch(action.type) {
    case CHANGE_INTERVAL:
      return state += action.payload;
    default:
      return {};
  }
};

// components

class IntervalComponent extends React.Component {
  render() {
    return (
      <div>
        <span>Интервал обновления секундомера: {this.props.currentInterval} сек.</span>
        <span>
          <button onClick={() => this.props.changeInterval(-1)}>-</button>
          <button onClick={() => this.props.changeInterval(1)}>+</button>
        </span>
      </div>
    );
  }
}

const Interval = connect(dispatch => ({
  changeInterval: value => dispatch(changeInterval(value)),
}),
state => ({
  currentInterval: state,
}))(IntervalComponent);

class TimerComponent extends React.Component {
  state = {
    currentTime: 0
  }

  render() {
    return (
      <div>
        <Interval />
        <div>
          Секундомер: {this.state.currentTime} сек.
        </div>
        <div>
          <button onClick={this.handleStart}>Старт</button>
          <button onClick={this.handleStop}>Стоп</button>
        </div>
      </div>
    );
  }

  handleStart() {
    setTimeout(() => this.setState({
      currentTime: this.state.currentTime + this.props.currentInterval,
    }), this.props.currentInterval);
  }
  
  handleStop() {
    this.setState({ currentTime: 0 });
  }
}

const Timer = connect(state => ({
  currentInterval: state,
}), () => {})(TimerComponent);

// init
ReactDOM.render(
  <Provider store={createStore(reducer)}>
    <Timer />
  </Provider>,
  document.getElementById('app')
);
```

## Typescript

Задачи на работу с типами.

### Задача №1

Необходимо вывести тип параметра `size`(`CustomSize`), находящийся в сигнатуре метода `calculateArea`. На импорт доступен только интерфейс `Rectangle`.
Подсказка: Для решения данной задачи необходимо понимание принципа работы оператора `infer`.

```ts
// lib/index.d.ts

interface CustomSize {
  width: number;
  height: number;
}

export interface Rectangle {
  calculateArea(size: CustomSize): number
}


// main.ts

import { Rectangle } from "lib/index.d.ts"

type Size = ... // вывести тип CustomSize из Rectangle
```

## Дополнительно

Задачи, которые не обязательны, но их решение будет плюсом.

### Задача №1

Написать функцию `getRandomBanner`, которая возвращает рандомный банер в зависимости от его параметра веса. Чем больше вес, тем чаще встречается баннер.

```js
const banners = [
  { weight: 10, id: 1 },
  { weight: 130, id: 2 },
  { weight: 40, id: 3 },
  { weight: 25, id: 4 },
  { weight: 60, id: 5 },
  { weight: 12, id: 6 },
];

function getRandomBanner(banners) {
  // реализация функции
}

getRandomBanner(banners); // рандомный баннер из списка
```

Плюсом будет оптимизация алгоритма с помощью бинарного поиска.

### Задача №2

Написать функцию `map`, которая перебирает массив `array` ассинхронно. Функция должна представлять из себя псевдо concurrency – эмуляцию параллельной обработки нескольких элементов с помощью асинхронного обработчика `handler` и `Promise.all`. Когда обработка одного из нескольких элементов заканчивается, то на его место должна вставать обработка следующего элемента.

Поэтапно выглядит следующим образом:
1. Существует массив с элементами `arr = [1..n]` и ассинхронный обработчик `handler`;
2. Передаем в функцию `map` данный массив, число элементов, которые мы должны одновременно обработать и сам обработчик `map(arr, 4, handler)`;
3. Берем первые 4 элемента и запускаем их обработку `Promise.all([handler(arr[1]), handler(arr[2]), handler(arr[3]), handler(arr[4])])`.
4. Предположим, что обработчик второго элемента завершился раньше, тогда на его место должен встать обработчик со следующим элементом – handler(arr[2]).then(() => handler(arr[5])).
5. И так с каждым элементом, пока не обработаем весь массив.

```js
/**
 * @param {Array} array массив, который нужно обработать
 * @param {number} count число элементов массива, которые будут обрабатываться параллельно
 * @param {() => Promise} handler обработчик, который возвращает промис
 * @return {Promise}
 */
function map(array, count, handler) {
  // реализация функции
  // return Promise.all([...])
}

const random = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;

// вызов функции, каждый четный элемент будет обрабатываться дольше
map(
  Array(random(80, 100))
    .fill()
    .map(() => random(0, 100)),
  4,
  (item) =>
    new Promise((resolve) => {
      setTimeout(resolve, item % 2 === 0 ? 200 : 100);
    })
);
```
