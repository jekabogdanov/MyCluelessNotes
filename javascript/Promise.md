Функция-исполнитель запускается при вызове new Promise.
    
Исполнитель получает два аргумента: resolve и reject — это функции, 
встроенные в JavaScript, исполнитель должен вызвать одну из них по готовности.

```javascript
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve("done!"), 1000);
});
```
Объект promise, возвращаемый конструктором new Promise, имеет внутренние свойства:
* state («состояние»):
  * "pending" («ожидание»)
  * "fulfilled" («выполнено успешно») при вызове resolve
  * "rejected" («выполнено с ошибкой») при вызове reject
* result («результат») 
  * undefined, 
  * value из resolve(value) или error из reject(error).
 
Первый аргумент метода .then – функция, которая выполняется, когда промис 
переходит в состояние «выполнен успешно», и получает результат.

Второй аргумент .then – функция, которая выполняется, когда промис переходит 
в состояние «выполнен с ошибкой», и получает ошибку.
```javascript
promise
  .then(
    result => alert(result), // выведет "done!" через одну секунду
    error => alert(error) // не будет запущена
  )
  .catch(alert) //обработка ошибки, аналог второго параметра в .then
  .finally(()=>alert('that is all')); //может возвращать ошибку, которая будет обработана в следующем .catch
```

### Обработка непойманных ошибок:
```javascript
  window.addEventListener('unhandledrejection', function(event) {
    // объект события имеет два специальных свойства:
    alert(event.promise); // [object Promise] - промис, который сгенерировал ошибку
    alert(event.reason); // Error: Ошибка! - объект ошибки, которая не была обработана
  });
  
  new Promise(function() {
    throw new Error("Ошибка!");
  }); // нет обработчика ошибок
```  