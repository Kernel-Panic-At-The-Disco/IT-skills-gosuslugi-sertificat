# CSS_advanced

## Вопрос 1
Как выбрать все <span>, находящиеся внутри элементов с двумя классами одновременно: .f и .g?

```html
<div class="f g">
  <span class="x">Text</span>
</div>
<div class="f">
  <span class="g">Another</span>
</div>
```

- span.f.g
- .f .g span
- span[class*=".f-g"]
- .f.g span
- f+g span

---

## Вопрос 2
Как правильно переопределить только text-align для всех дочерних элементов внутри .container, при этом сохранив остальные наследуемые свойства?

- .container * { all: inherit; }
- .container * { text-align: initial; }
- .container * { text-align: inherit; }
- .container * { text-align: none; }
- .container > * { direction: inherit; }

---

## Вопрос 3
Как обеспечить, чтобы элемент с заданными width: 100px и padding: 20px занимал ровно 100px по ширине в макете?

- Установить overflow: hidden;
- Применить box-sizing: border-box;
- Назначить margin: -20px;
- Прописать width: auto;
- Использовать display: inline;

---

## Вопрос 4
Когда оптимально использовать встроенные (inline) стили в HTML?

- Когда проект полностью построен на CSS-модулях и PostCSS
- Когда необходимо обеспечить переиспользуемость стилей в рамках всего проекта
- Когда нужно задать уникальные стили для одного конкретного элемента без повторного использования
- Когда стили должны быть централизованно изменяемы из единого файла
- Когда стили должны применяться только после загрузки всех шрифтов

---

## Вопрос 5
Как повлиять на vh высоту секции, если на мобильных устройствах часть viewport скрыта (например, адресная строка)?

- Использовать высоту в px и добавить overflow: auto
- Использовать min-height: 100% к <body> и <html>
- Использовать dvh вместо vh
- Использовать calc(100vh - 50px) без учёта видимой области
- Использовать max-height: 100vh и padding: 10vh

---

## Вопрос 6
Как сделать так, чтобы один из трёх элементов занял всё оставшееся пространство в строке, а остальные были фиксированной ширины?

- Использовать display: flex и задать нужному элементу flex-grow: 1
- Использовать position: absolute для растягиваемого элемента
- Применить flex-basis: 100% ко всем элементам
- Использовать display: grid с фиксированной шириной колонок
- Применить display: flex; justify-content: space-between

---

## Вопрос 7
Какая комбинация осей используется Flexbox для размещения элементов?

- Основная и вспомогательная ось
- Только горизонтальная ось
- Статическая и абсолютная ось
- Левый и правый поток
- Верхняя и нижняя ось

---

## Вопрос 8
Как с помощью CSS добавить звездочку после обязательного поля формы без изменения HTML?

- Добавить required:after
- Применить :not(optional)
- Использовать ::before без content
- Использовать ::after c content: "*"
- Задать outline с текстом

---

## Вопрос 9
Какой селектор применит стили ко всем кнопкам, кроме тех, у которых установлен класс .primary и которые находятся в фокусе?

- button:not(.primary):not(:focus)
- button:not(:focus).primary
- button:is(:not(.primary), :not(:focus))
- button:focus:not(.primary)
- button:not(.primary:focus)

---

## Вопрос 10
Как реализовать плавное изменение фона при наведении на элемент с задержкой запуска эффекта?

- element:hover { transition: background-color 0.5s ease 0.3s; }
- element { transition-delay: background-color 0.3s; }
- element:hover { animation: changeBg 0.5s ease 0.3s; }
- element:hover { transition: 0.5s ease 0.3s background; }
- element { background-transition: delay 0.3s, duration 0.5s; }

---

## Вопрос 11
Как реализовать 3D-анимацию переворота карточки по оси X при наведении курсора с сохранением перспективы родительского контейнера?

- Применить perspective(1000px) и transform: rotateZ(180deg)
- Задать transform: scaleZ(2) и backface-visibility: hidden
- Использовать transform: skewY(180deg) без дополнительных параметров
- Задать transform: rotateX(180deg) и perspective на карточке
- Применить transform-style: flat и rotateY(180deg) к карточке

---

## Вопрос 12
Какой метод позиционирования наиболее затратный по производительности при прокрутке страницы?

- position: relative
- position: static
- display: block
- display: flex
- position: sticky

---

## Вопрос 13
Какой из селекторов имеет наибольшую специфичность?

```html
<div class="item active" id="unique"></div>
```

- div#unique
- div.item
- .item.active
- .active#unique
- #unique

---

## Вопрос 14
Как сделать так, чтобы изображение внутри контейнера сохраняло пропорции, заполняло весь контейнер по ширине и не выходило за его границы?

```html
<style>
  .container {
    width: 100%;
    max-width: 600px;
    aspect-ratio: 16/9;
    overflow: hidden;
  }
</style>
<div class="container">
  <img src="image.jpg" class="img" />
</div>
```

- .img { height: 100%; width: auto; object-fit: none; }
- .img { flex: 1; min-width: 0; }
- .img { object-fit: cover; width: 200%; }
- .img { position: absolute; top: 0; left: 0; }
- .img { width: 100%; height: auto; object-fit: contain; }

---

## Вопрос 15
Что произойдет с .card, если ширина экрана уменьшится до 991px?

```css
.card {
  width: 1000px;
  transition: width 0.3s ease;
}
@media (max-width: 992px) {
  .card {
    width: 100%;
  }
}
```

- Карточка анимировано сожмется до ширины экрана
- Карточка исчезнет
- Карточка будет уменьшаться пропорционально
- Карточка будет обрезана
- Карточка останется шириной 1000px

---

## Вопрос 16
Как выбрать только те элементы <p>, которые находятся непосредственно внутри <div class="f">?

```html
<div class="a">
  <div class="b">
    <p class="c">Text</p>
  </div>
  <div class="d">
    <p class="e">Text</p>
  </div>
  <div class="f">
    <span class="g">Text</span>
  </div>
</div>
```

- .d p
- .d > p
- div > .e
- div > .e > p
- div.d > .e

---

## Вопрос 17
Как избавиться от лишнего отступа между inline-block элементами, размещенными в одной строке?

- Добавить overflow: hidden родителю блока
- Прописать родителю display: flex с обнулением
- Установить vertical-align: top на блоки
- Применить margin: -x на элементы
- Удалить пробелы между тегами в HTML разметке

---

## Вопрос 18
В каком случае предпочтительно использовать тег <style> внутри секции <head>?

- Когда необходимо обеспечить максимальную производительность за счёт кэширования
- Когда проект использует SCSS и CSS должен быть скомпилирован на лету
- Когда все стили хранятся во внешнем CDN и не требуют локальное хранение
- Когда стили специфичны для данной страницы и не предполагаются их повторное использование
- Когда важна полная изоляция компонентов в SPA приложении

---

## Вопрос 19
Как задать фиксированную ширину поля ввода ровно 30 символов среднего размера?

- Использовать width: 30ex
- Использовать min-width: 30ch
- Использовать max-width: 30em
- Использовать width: 30ch
- Использовать width: 30em

---

## Вопрос 20
Как равномерно распределить три блока по ширине контейнера с отступами между ними в Flexbox?

- Использовать display: flex и gap: auto
- Использовать display: flex; justify-content: center и margin
- Применить display: flex; justify-content: space-between
- Использовать display: align-items: stretch
- Назначить width: 33.3% каждому элементу без flex-контейнера

---

## Вопрос 21
Что произойдёт с Flex-элементами при нехватке места в контейнере с flex-wrap: nowrap ?

- Элементы исчезнут, если не вмещаются полностью
- Элементы автоматически перейдут на новую строку
- Контейнер изменит свой размер, чтобы вместить все элементы
- Элементы выйдут за пределы контейнера и могут наложиться
- Flexbox автоматически уменьшит размеры элементов

---

## Вопрос 22
Как изменить фон инпута при фокусе пользователя?

- Использовать селектор :focus
- Применить :checked к инпуту
- Применить ::before + opacity
- Использовать :visited + bg
- Указать :hover::after

---

## Вопрос 23
Какой селектор применяется, если элемент <h2> — единственный элемент такого типа внутри своего родителя, независимо от других элементов?

- h2:only-child
- h2:only-of-type
- h2:first-of-type
- h2:last-child
- h2:nth-of-type(1)

---

## Вопрос 24
Как реализовать функцию reduce motion для выключения всех анимаций и переходов на странице, используя @keyframes и CSS?

- { transition-delay: 0 !important; animation: none; }
- { transition-timing-function: ease; animation: none; }
- { transition-duration: 0 !important; animation: none !important; }
- { transition-property: none; animation: none !important; }
- { transition-duration: 0 !important; animation: none !important; }

---

## Вопрос 25
Какой селектор будет переопределен при конфликте?

```html
a <a href="#" class="link" id="mainLink"></a>
```

- .link#mainLink
- #mainLink
- a#mainLink
- .link
- a.link

---

## Вопрос 26
Какой способ позволяет задать размер шрифта, который будет адаптироваться в зависимости от ширины экрана без медиа-запросов?

```css
.title {
  font-size: ???;
}
```

- font-size: clamp(1rem, 2vw, 2.5rem)
- font-size: 16px
- font-size: calc(1rem + 1px)
- font-size: 1rem
- font-size: var(--font-lg)

---