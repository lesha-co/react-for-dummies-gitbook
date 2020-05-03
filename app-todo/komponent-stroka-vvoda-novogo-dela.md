# Компонент: Строка ввода нового дела

Рядом с `TodoApp.jsx`, в папке `todo`, создадим файл `field.jsx`.

В созданном файле объявим функцию `Field`, которая будет являться нашим компонентом. Сделаем так, что бы она возвращала хоть что-то:

```jsx
function Field() {
  return <p>Hello, world!</p>
}
```

В прошлом уроке мы научились пользоваться `useState`, давай применим его тут для хранения содержимого поля ввода.

Для ввода текстовых данных есть тег `<input>`, у которого есть свойство `value` для текста и `onChange` для обработки _изменений_, сродни `onClick` для нажатий. Следовательно, наш компонент будет выглядеть как-то так:

```jsx
export function Field() {
  const [text, setText] = useState('');

  function onInputChange() {
    // что-то тут будет ???
  }
  
  return (
    <div>
      <input type="text" value={text} onChange={onInputChange} />
    </div>
  );
}
```

Обрати внимание на `useState`: теперь изначальное значение — пустая строка.

Осталось понять, что делать в `onInputChange`.  Нам надо получить новое значение из поля ввода и сохранить его в  `text`. 

## События

В прошлом уроке мы узнали о том, что существуют события, и их обработчики. В данном случае, у нас есть поле ввода, на котором висит обработчик события `change`.  

Обработчик события получает первым аргументом \(обычно, его называют `e`\) само событие — всю информацию, которую браузер знает о том, что произошло. В частности, какой элемент на странице породил это событие. Этот элемент доступен нам в объекте `e.target` . Его новое значение — в `e.target.value` . Это значение нам и предстоит сохранить в `text`:

```jsx
function onInputChange(e) {
  setText(e.target.value);
}
```

Вуаля! Теперь мы можем редактировать значение поля ввода! Строго говоря, если бы мы ничего не писали, а оставили голый `<input type="text"/>` , мы бы тоже смогли редактировать его с клавиатуры, однако теперь мы можем его редактировать из кода нашего компонента!

## Кнопка

Осталось совсем немного: создать кнопку, которая будет добавлять дело в список:

```jsx
return (
  <div >
    <input className="left" type="text" value={text} onChange={onInputChange} />
    <button>New</button>
  </div>
);
```


