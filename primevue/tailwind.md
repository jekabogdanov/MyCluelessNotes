## Локальная установка стилей компонента

pt - Pass Through
в атрибуты Panel можно добавить unstyled (зачем?)
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

## Глобальная установка стилей
[Shadcn Skin with Tailwind for PrimeVue Dialog](https://youtu.be/OLv_yeMLPrY?list=PLC9bp-OHi-WkbRc1XMqattI8cE349qok7)

tailwind.config.js
```js
export default {
    content: [
        './node_modules/primevue/**/*.{vue,js,ts,jsx,tsx}',
    ]
}
```

main.js
```js
app.use(PriveVue, {
    unstyled: true,
    pt: {
        dialog: {
            root: 'grid w-full max-w-lg gap-4',
            headerTitle: 'text-lg font-semibold',
            header: 'flex items-center justify-between'
        }
        //можно использовать tailwind transitions
        transition: ({props}) => {
            return props.position === 'top'
            ? {
                enterFromClass: 'opasity-0 scale-75 translate-x-0 -translate-y-full translate-z-0',
                enterActiveClass: 'transition-all duration-200 ease-out',
                leaveActiveClass: 'transition-all duration-200 ease-out',
                leaveToClass: 'opacity-0 scale-75 translate-x-0 -translate-y-full translate-z-0',

              }
            : props.position === 'bottom'
            ? {
                enterFromClass: 'opasity-0 scale-75 translate-y-full',
                enterActiveClass: 'transition-all duration-200 ease-out',
                leaveActiveClass: 'transition-all duration-200 ease-out',
                leaveToClass: 'opacity-0 scale-75 translate-x-0 translate-y-full translate-z-0',
              }
            : props.position === 'left' ||
              props.position === 'topleft' ||
              /*что-то еще ...*/
        }
    }
});
```