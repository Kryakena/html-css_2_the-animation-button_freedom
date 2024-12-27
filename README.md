# Анимированная кнопка "Свобода"

Источник: видео "Анимация кнопки "Свобода" на HTML и CSS3. Эффекты CSS3 // Как это сделать?" 
https://vk.com/im/convo/19460369?entrypoint=list_all&z=video-125918837_456239141%2F2e6b4c91d47840cf0d

1. создаем создаем файлы index.html, style.css, script.js в папке проекта

2. в файле index.html готовим шаблон

```html
<!--сообщаем браузеру, как стоит обрабатывать эту страницу-->
<!DOCTYPE html>
<!--оболочка документа, указываем язык содержимого-->
<html lang="ru">
<!--заголовок страницы, контейнер для других важных данных (не отображается)-->
<head>
    <!--заголовок страницы в браузере-->
    <title></title>
    <!--подключаем CSS-->
    <link rel="stylesheet" href="style.css">
    <!--кодировка страницы-->
    <meta charset="utf-8">
</head>
<!--отображаемое тело страницы-->
<body>
<!--оболочка для демонстрации-->
<div class="wrapper">
    <!--контент-->

</div>
</body>
</html>
```

3. в файле script.js вставляем шаблон

```js
$(document).ready(function () {

});
```

4. в файле style.css вставляем шаблон

```css
/*Обнуление*/
*,*:before,*:after{
    padding: 0;
    margin: 0;
    border: 0;
    box-sizing: border-box;
}
html,body{
    height: 100%;
}
/*Стили для демонстрации*/
.wrapper{
    
}

/*Основные стили*/
```

5. в файле index.html в разделе head пишем название и адаптив

```html
<title>Кнопка с анимацией "Свобода"</title>
```
```html
 <!--адаптив-->
<meta name="viewport" content="width=device-width">
```

6. в файле index.html в разделе body в заранее созданной оболочке wrapper создаем кнопку с названием "Свобода"

```html
<a href="#" class="button">
        <span class="button_text">
            <span>Свобода</span>
        </span>
</a>
```

7. в файле style.css для лучшей демонстрации

```css
.wrapper{
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
}
```

8. в файле style.css стиль самой кнопки

```css
.button {
    font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    text-decoration: none;
    position: relative;
    display: inline-block;
}
```

9. в файле style.css стиль текстовой области самой кнопки

```css
.button_text {
    position: relative;
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0px 50px;
    border-radius: 50px;
    font-size: 24px;
    text-transform: uppercase;
    color: rgba(0,0,0,0.3);
    letter-spacing: 10px;
    transition: all 1s ease 0s; /*анимация*/
    top: 0;
    overflow: hidden;
}
```

10. в файле style.css создаем бэкграунд кнопки с помощью псевдоэлемента before

```css
.button_text:before,
.button_text:after {
    content: '';
    position: absolute;
    width: 50%;
    height: 100%;
    background-color: #eee;
}
.button_text:before {
    left: 0;
    z-index: 2;
}
.button_text:after {
    right: 0;
}
.button_text span {
    position: relative;
    z-index: 2;
}
```

11. в файле style.css создаем движущиеся грани решетки вокруг кнопки.
Создаем псевдоэлементы для всей кнопки

```css
.button:before,
.button:after {
    content: '';
    position: absolute;
    width: 100px;
    height: 100px;
    border: 2px solid red;
    top: -10px;
    left: 50%;
    z-index: 1;
    margin: 0px 0px 0px -40px;
}
```

12. в файле style.css событие при наведении

```css
.button:hover:before,
.button:hover:after {
    left: 100%;
    opacity: 0;
}
```

13. в файле style.css в ".button:before,.button:after" добавляем анимацию плавности анимации при наведении

```css
transition: all 0.8s ease 0s;
```

14. в файле style.css, чтобы элемент выезжая в сторону при наведении не перекрывал собой текст

```css
.button:hover .button_text:before {
    width: 100%;
}
```

15. в файле style.css, чтобы анимация не перекрыла текст

```css
transition: all 0.3s ease 0s;
```
