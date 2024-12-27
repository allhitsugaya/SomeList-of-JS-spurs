## Пример использования таймера в коде

В данном примере показано, как можно использовать таймер для удаления ошибки валидации через определенное время. В случае, если введённый номер телефона не соответствует формату, ошибка отображается, а через 3 секунды она исчезает.

```javascript
if (phone.length < 13 || !/^\+380\d{9}$/.test(phone)) {
    // Отображаем ошибку, если номер телефона некорректен
    document.querySelector(`#phoneerror`).innerText = `Please enter a valid phone number`;
    isValid = false;

    // Убираем ошибку через 3 секунды
    setTimeout(() => {
        document.querySelector(`#phoneerror`).innerText = '';
    }, 3000);
}
```

## Пример использования ReGex
```javascript
/^\+380\d{9}$/ //для телефона.
/^[^\s@]+@[^\s@]+\.[^\s@]+$/ // дял почты
```
# Функция для скрытия номера карты

В этой задаче мы реализуем функцию `getHiddenCard()`, которая скрывает часть номера кредитной карты, заменяя её звездочками, а последние 4 символа оставляет видимыми.

## Описание функции

Функция принимает два параметра:
- **cardNumber** (строка) — номер карты, состоящий из 16 цифр.
- **hiddenCount** (необязательный параметр, по умолчанию 4) — количество символов, которые должны быть заменены на звездочки.

Если параметр `hiddenCount` не передан, то по умолчанию скрывается 4 символа.

## Код функции

```javascript
const getHiddenCard = (cardNumber, hiddenCount = 4) => {
  // Делаем маску звездочками для всех символов, кроме последних visibleCount символов
  const maskedPart = '*'.repeat(hiddenCount); 
  const visiblePart = cardNumber.slice(-4);  // Всегда оставляем последние 4 символа видимыми

  return maskedPart + visiblePart;
};
```
# Методы массивов, строк и объектов в JavaScript

## Методы массивов

### 1. `.push()`
Добавляет один или несколько элементов в конец массива и возвращает новую длину массива.

```javascript
let arr = [1, 2, 3];
arr.push(4);  // [1, 2, 3, 4]

2. .pop()
Удаляет последний элемент массива и возвращает его. Этот метод изменяет длину массива.


let arr = [1, 2, 3, 4];
let last = arr.pop();  // 4
console.log(arr);  // [1, 2, 3]
console.log(last);  // 4
3. .shift()
Удаляет первый элемент массива и возвращает его. Этот метод изменяет длину массива.


let arr = [1, 2, 3, 4];
let first = arr.shift();  // 1
console.log(arr);  // [2, 3, 4]
console.log(first);  // 1
4. .unshift()
Добавляет один или несколько элементов в начало массива и возвращает новую длину массива.


let arr = [2, 3, 4];
arr.unshift(1);  // [1, 2, 3, 4]
console.log(arr);  // [1, 2, 3, 4]
5. .concat()
Соединяет два или более массива и возвращает новый массив, не изменяя исходные.


let arr1 = [1, 2];
let arr2 = [3, 4];
let result = arr1.concat(arr2);  // [1, 2, 3, 4]
console.log(result);  // [1, 2, 3, 4]
6. .indexOf()
Возвращает первый индекс, по которому элемент может быть найден в массиве, или -1, если элемент не найден.


let arr = [1, 2, 3, 4];
let index = arr.indexOf(3);  // 2
console.log(index);  // 2
7. .join()
Объединяет все элементы массива в строку, разделяя их указанным разделителем.


let arr = ['a', 'b', 'c'];
let str = arr.join(', ');  // "a, b, c"
console.log(str);  // "a, b, c"
8. .slice()
Возвращает новый массив, содержащий копию части исходного массива. Не изменяет оригинальный массив.


let arr = [1, 2, 3, 4];
let sliced = arr.slice(1, 3);  // [2, 3]
console.log(sliced);  // [2, 3]
9. .splice()
Изменяет содержимое массива, удаляя или заменяя элементы. Возвращает массив удалённых элементов.


let arr = [1, 2, 3, 4];
let removed = arr.splice(1, 2);  // [2, 3]
console.log(arr);  // [1, 4]
console.log(removed);  // [2, 3]
10. .forEach()
Выполняет функцию для каждого элемента массива.


let arr = [1, 2, 3];
arr.forEach(item => console.log(item));  // 1 2 3
11. .map()
Создаёт новый массив, с результатами вызова функции для каждого элемента массива.


let arr = [1, 2, 3];
let doubled = arr.map(num => num * 2);  // [2, 4, 6]
console.log(doubled);  // [2, 4, 6]
12. .filter()
Создаёт новый массив, содержащий все элементы, которые прошли проверку в переданной функции.

let arr = [1, 2, 3, 4];
let even = arr.filter(num => num % 2 === 0);  // [2, 4]
console.log(even);  // [2, 4]
13. .reduce()
Применяет функцию к каждому элементу массива для получения одного итогового значения.


let arr = [1, 2, 3];
let sum = arr.reduce((acc, curr) => acc + curr, 0);  // 6
console.log(sum);  // 6
```
# Манипуляции с DOM и обработка событий в JavaScript

## 1. Функция создания элемента

```javascript
function createEl({ type = 'div', content, attributes  } = {}) {
    const $el = document.createElement(type);

    if (content) {
        typeof content === 'string' ? $el.textContent = content : $el.append(content)
    }

    if (attributes) Object.entries(attributes).forEach(([key, value]) => {
        $el.setAttribute(key, value)
    })

    return $el;
}

// Пример использования:
const p = createEl({ type: 'p', content: 'Hello World', attributes: { class: 'par', id: 1 } })
const title = createEl({ type: 'h2', content: p, attributes: { class: 'example' } })
document.body.append(title)
```
# Функція `setData`

Функція `setData` використовується для перевірки значення за допомогою регулярного виразу та повернення об'єкта з інформацією про перевірку.
## Сигнатура

```javascript
function setData(regex, value, message) {
    const valid = regex.test(value);
    return {
        value,
        valid,
        errorMessage: !valid ? message : 'Valid'
    };
}
```
# Функція `checkData`

Функція `checkData` використовується для перевірки даних введення в реальному часі, відображаючи повідомлення про помилку або підтвердження і керуючи станом кнопки відправки форми.

## Сигнатура

```javascript
function checkData(e, el) {
    switch (e.target.name) {
        case el.dataset.error: {
            formData[e.target.name] = setData(
                /^\w+$/g,
                e.target.value,
                'Please enter a valid name'
            );
            el.innerText = formData[e.target.name].errorMessage;
            form.elements.submit.disabled = !formData[e.target.name].valid;
        }
    }
}
```
## Їх використання

```javascript
// Об'єкт для збереження стану полів форми
const formData = {};

// Функція `setData` для перевірки значень
function setData(regex, value, message) {
    const valid = regex.test(value);
    return {
        value,
        valid,
        errorMessage: !valid ? message : 'Valid',
    };
}

// Функція `checkData` для обробки перевірок
function checkData(e, el) {
    switch (e.target.name) {
        case el.dataset.error: {
            formData[e.target.name] = setData(
                /^\w+$/g,
                e.target.value,
                'Please enter a valid name'
            );
            el.innerText = formData[e.target.name].errorMessage;
            form.elements.submit.disabled = !formData[e.target.name].valid;
        }
    }
}

// Додаємо обробник подій до форми
const form = document.getElementById('form');
form.addEventListener('input', function (e) {
    const errorElement = form.querySelector(`[data-error="${e.target.name}"]`);
    if (errorElement) {
        checkData(e, errorElement);
    }
});
```