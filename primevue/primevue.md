## Pass Through (pt) 
DOM элементы компонента на стили которых можно повлиять из кода ([приведены на сайте PRIMEVUE](primevue.org) Components->Компонент->PASS THROUGH)

например через атрибут компонента:
```html
<Panel
    header="Header Title"
    :pt="{
        header: {class: 'bg-indigo-500 border-indigo-500'},
        title: {class: 'text-white'},
        content: {class: 'font-bold border-indigo-500'}
    }"
>
    <p>Panel Content Text</p>
</Panel>
```

или через presets:

main.js
```js
app.use(PrimeVue {
    unstyled: true,
    pt: Lara
})
```
Скины (стили) компонентов хранятся в виде js-объектов внутри ./src/presets/lara/...