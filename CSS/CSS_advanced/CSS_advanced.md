# **CSS\_advanced**

**Вопрос 1**

Как выбрать все \<span\>, находящиеся внутри элементов с двумя классами одновременно: .f и .g?

1 \<div class="f g"\>  
2   \<span class="x"\>Text\</span\>  
3 \</div\>  
4 \<div class="f"\>  
5   \<span class="g"\>Another\</span\>  
6 \</div\>

1. span.f.g  
2. .f .g span  
3. span\[class\*=".f-g"\]  
4. .f.g span  
5. f+g span

**Вопрос 2**

Как правильно переопределить только text-align для всех дочерних элементов внутри .container, при этом сохранив остальные наследуемые свойства?

1. .container \* { all: inherit; }  
2. .container \* { text-align: initial; }  
3. .container \* { text-align: inherit; }  
4. .container \* { text-align: none; }  
5. .container \> \* { direction: inherit; }

**Вопрос 3**

Как обеспечить, чтобы элемент с заданными width: 100px и padding: 20px занимал ровно 100px по ширине в макете?

1. Установить overflow: hidden;  
2. Применить box-sizing: border-box;  
3. Назначить margin: \-20px;  
4. Прописать width: auto;  
5. Использовать display: inline;

**Вопрос 4**

Когда оптимально использовать встроенные (inline) стили в HTML?

1. Когда проект полностью построен на CSS-модулях и PostCSS  
2. Когда необходимо обеспечить переиспользуемость стилей в рамках всего проекта  
3. Когда нужно задать уникальные стили для одного конкретного элемента без повторного использования  
4. Когда стили должны быть централизованно изменяемы из единого файла  
5. Когда стили должны применяться только после загрузки всех шрифтов

**Вопрос 5**

Как повлиять на vh высоту секции, если на мобильных устройствах часть viewport скрыта (например, адресная строка)?

1. Использовать высоту в px и добавить overflow: auto  
2. Использовать min-height: 100% к \<body\> и \<html\>  
3. Использовать dvh вместо vh  
4. Использовать calc(100vh \- 50px) без учёта видимой области  
5. Использовать max-height: 100vh и padding: 10vh

**Вопрос 6**

Как сделать так, чтобы один из трёх элементов занял всё оставшееся пространство в строке, а остальные были фиксированной ширины?

1. Использовать display: flex и задать нужному элементу flex-grow: 1  
2. Использовать position: absolute для растягиваемого элемента  
3. Применить flex-basis: 100% ко всем элементам  
4. Использовать display: grid с фиксированной шириной колонок  
5. Применить display: flex; justify-content: space-between

**Вопрос 7**

Какая комбинация осей используется Flexbox для размещения элементов?

1. Основная и вспомогательная ось  
2. Только горизонтальная ось  
3. Статическая и абсолютная ось  
4. Левый и правый поток  
5. Верхняя и нижняя ось

**Вопрос 8**

Как с помощью CSS добавить звездочку после обязательного поля формы без изменения HTML?

1. Добавить required:after  
2. Применить :not(optional)  
3. Использовать ::before без content  
4. Использовать ::after c content: "\*"  
5. Задать outline с текстом

**Вопрос 9**

Какой селектор применит стили ко всем кнопкам, кроме тех, у которых установлен класс .primary и которые находятся в фокусе?

1. button:not(.primary):not(:focus)  
2. button:not(:focus).primary  
3. button:is(:not(.primary), :not(:focus))  
4. button:focus:not(.primary)  
5. button:not(.primary:focus)

**Вопрос 10**

Как реализовать плавное изменение фона при наведении на элемент с задержкой запуска эффекта?

1. element:hover { transition: background-color 0.5s ease 0.3s; }  
2. element { transition-delay: background-color 0.3s; }  
3. element:hover { animation: changeBg 0.5s ease 0.3s; }  
4. element:hover { transition: 0.5s ease 0.3s background; }  
5. element { background-transition: delay 0.3s, duration 0.5s; }

**Вопрос 11**

Как реализовать 3D-анимацию переворота карточки по оси X при наведении курсора с сохранением перспективы родительского контейнера?

1. Применить perspective(1000px) и transform: rotateZ(180deg)  
2. Задать transform: scaleZ(2) и backface-visibility: hidden  
3. Использовать transform: skewY(180deg) без дополнительных параметров  
4. Задать transform: rotateX(180deg) и perspective на карточке  
5. Применить transform-style: flat и rotateY(180deg) к карточке

**Вопрос 12**

Какой метод позиционирования наиболее затратный по производительности при прокрутке страницы?

1. position: relative  
2. position: static  
3. display: block  
4. display: flex  
5. position: sticky

**Вопрос 13**

Какой из селекторов имеет наибольшую специфичность?

1 \<div class="item active" id="unique"\>\</div\>

1. div\#unique  
2. div.item  
3. .item.active  
4. .active\#unique  
5. \#unique

**Вопрос 14**

Как сделать так, чтобы изображение внутри контейнера сохраняло пропорции, заполняло весь контейнер по ширине и не выходило за его границы?

1 \<style\>  
2   .container {  
3     width: 100%;  
4     max-width: 600px;  
5     aspect-ratio: 16/9;  
6     overflow: hidden;  
7   }  
8 \</style\>  
9 \<div class="container"\>  
10   \<img src="image.jpg" class="img" /\>  
11 \</div\>

1. .img { height: 100%; width: auto; object-fit: none; }  
2. .img { flex: 1; min-width: 0; }  
3. .img { object-fit: cover; width: 200%; }  
4. .img { position: absolute; top: 0; left: 0; }  
5. .img { width: 100%; height: auto; object-fit: contain; }

**Вопрос 15**

Что произойдет с .card, если ширина экрана уменьшится до 991px?

1 .card {  
2   width: 1000px;  
3   transition: width 0.3s ease;  
4 }  
5 @media (max-width: 992px) {  
6   .card {  
7     width: 100%;  
8   }  
9 }

1. Карточка анимировано сожмется до ширины экрана  
2. Карточка исчезнет  
3. Карточка будет уменьшаться пропорционально  
4. Карточка будет обрезана  
5. Карточка останется шириной 1000px