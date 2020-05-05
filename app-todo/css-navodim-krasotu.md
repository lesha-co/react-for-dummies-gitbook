# CSS: Наводим красоту

Ответ для прошлой главы

{% code title="Field.jsx" %}
```jsx
function onButtonClick() {
  
  if(text !== ''){ // работаем, только если строка не пустая!
    props.onAdd(text);
    setText('') // просто делаем текст пустой строчкой!
  }
  
}
```
{% endcode %}

