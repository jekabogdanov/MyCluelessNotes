[>> tailwindcss.com: Handling Hover, Focus, and Other States](https://tailwindcss.com/docs/hover-focus-and-other-states#file-input-buttons)

Типы модификаторов:
* **Pseudo-classes**: :hover, :focus, :first-child, :required ...
* **Pseudo-elements**: ::before, ::after, ::placeholder, ::selection ...
* **Media and feature queries**: responsive breakpoints, dark mode, prefers-reduced-motion ...
* **Attribute selectors**: [dir="rtl"] and [open]

[>> все модификаторы](https://tailwindcss.com/docs/hover-focus-and-other-states#pseudo-class-reference)

Можно комбинировать:
```html
<button class="dark:md:hover:bg-fuchsia-600 ...">
  Save changes
</button>
```

## Модификаторы для форм
required, invalid, disabled

### Стили на основе состояния родителя (group-{modifier})
Пометить группу классом родителя `group`, в потомке использовать модификаторы `group-*`, например: `group-hover`
```html
<a href="#" class="group block max-w-xs mx-auto rounded-lg p-6 bg-white ring-1 ring-slate-900/5 shadow-lg space-y-3 hover:bg-sky-500 hover:ring-sky-500">
  <div class="flex items-center space-x-3">
    <svg class="h-6 w-6 stroke-sky-500 group-hover:stroke-white" fill="none" viewBox="0 0 24 24"><!-- ... --></svg>
    <h3 class="text-slate-900 group-hover:text-white text-sm font-semibold">New project</h3>
  </div>
  <p class="text-slate-500 group-hover:text-white text-sm">Create a new project from a variety of starting templates.</p>
</a>
```

### Разграничение вложенных групп
Группам можно присваивать имена добавляя класс `group/{name}`, и используя в потомках `group-hover/{name}` 

### Произвольные модификаторы групп
Например: ```group-[.is-published]:block```

```For more control, you can use the '&' character to mark where '.group' should end up in the final selector relative to the selector you are passing in:```

## Стили на основе состояния одноуровневых элементов (sibling) (peer-{modifier})
```html
<form>
  <label class="block">
    <span class="block text-sm font-medium text-slate-700">Email</span>
    <input type="email" class="peer ..."/>
    <p class="mt-2 invisible peer-invalid:visible text-pink-600 text-sm">
      Please provide a valid email address.
    </p>
  </label>
</form>
```
Так же как и для group, для peer работают имена и произвольные модификаторы.

[Youtube: Floating Labels with Tailwind CSS](https://youtu.be/nJzKi6oIvBA)

```For more control, you can use the '&' character to mark where '.peer' should end up in the final selector relative to the selector you are passing in:```

## Стили прямых потомков (*:)

## Стили на основании состояния потомков (has-*)
```html
<label class="has-[:checked]:bg-indigo-50 has-[:checked]:text-indigo-900 has-[:checked]:ring-indigo-200 ..">
  <svg fill="currentColor">
    <!-- ... -->
  </svg>
  Google Pay
  <input type="radio" class="checked:border-indigo-500 ..." />
</label>
```
Можно использовать вместе с псевдоклассами, например `has-[:focus]`, или с селекторами: `has-[img]`, `has-[a]`.
```html
<div class="group ...">
  <img src="..." />
  <h4>Spencer Sharp</h4>
  <svg class="hidden group-has-[a]:block ...">
    <!-- ... -->
  </svg>
  <p>Product Designer at <a href="...">planeteria.tech</a></p>
</div>
```

### Стили на основании состояния потомков одноуровневых элементов (peer-has-{modifier})
```html
<fieldset>
  <legend>Today</legend>

  <div>
    <label class="peer ...">
      <input type="checkbox" name="todo[1]" checked />
      Create a to do list
    </label>
    <svg class="peer-has-[:checked]:hidden ...">
      <!-- ... -->
    </svg>
  </div>

  <!-- ... -->
</fieldset>
```

* `placeholder:`
* `file:` - стили кнопки выбора файла для ```<input type="file">```
* `marker:` - стили маркеров `li` (можно использовать как в `li`, так и в `ul` без `*:`)
* `selection:` - стили выбранного текста (можно вставить в любого родителя текста)
* `first-line`, `first-letter`:
```html
<p class="first-line:uppercase first-line:tracking-widest
  first-letter:text-7xl first-letter:font-bold first-letter:text-slate-900
  first-letter:mr-3 first-letter:float-left
">
  Well, let me tell you something, funny boy. Y'know that little stamp, the one
  that says "New York Public Library"? Well that may not mean anything to you,
  but that means a lot to me. One whole hell of a lot.
</p>
```
