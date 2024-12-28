# 🐣 Анимированная кнопка "Свобода" 🐣

Источник: видео "Анимация кнопки "Свобода" на HTML и CSS3. Эффекты CSS3 // Как это сделать?" 
https://vk.com/im/convo/19460369?entrypoint=list_all&z=video-125918837_456239141%2F2e6b4c91d47840cf0d

![2024-12-28_14-14-06](https://github.com/user-attachments/assets/21fe6e4d-73b7-49fd-9959-3f32877ec31d) ![2024-12-28_14-14-18](https://github.com/user-attachments/assets/a553f952-2642-411f-8674-9b6e303c371f)


https://github.com/user-attachments/assets/31c500c7-4151-4eb4-bb8f-1e326a23fb06


1. создаем создаем файлы index.html, style.css в папке проекта

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

3. в файле style.css вставляем шаблон

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

4. в файле index.html в разделе head пишем название и адаптив

```html
<title>Кнопка с анимацией "Свобода"</title>
```
```html
 <!--адаптив-->
<meta name="viewport" content="width=device-width">
```

5. в файле index.html в разделе body в заранее созданной оболочке wrapper создаем кнопку с названием "Свобода"

```html
<a href="#" class="button">
        <span class="button_text">
            <span>Свобода</span>
        </span>
</a>
```

6. в файле style.css для лучшей демонстрации

```css
.wrapper{
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
}
```

7. в файле style.css стиль самой кнопки

```css
.button {
    font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    text-decoration: none;
    position: relative;
    display: inline-block;
}
```

8. в файле style.css стиль текстовой области самой кнопки

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

9. в файле style.css создаем бэкграунд кнопки с помощью псевдоэлемента before

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

10. в файле style.css создаем движущиеся грани решетки вокруг кнопки.
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

11. в файле style.css событие при наведении

```css
.button:hover:before,
.button:hover:after {
    left: 100%;
    opacity: 0;
}
```

12. в файле style.css в ".button:before,.button:after" добавляем анимацию плавности анимации при наведении

```css
transition: all 0.8s ease 0s;
```

13. в файле style.css, чтобы элемент выезжая в сторону при наведении не перекрывал собой текст

```css
.button:hover .button_text:before {
    width: 100%;
}
```

14. в файле style.css в ".button_text:before, .button_text:after", чтобы анимация не перекрыла текст

```css
transition: all 0.8s ease 0s;
```

15. в файле style.css меняем цвет кнопки, который меняется при наведении

```css
.button:hover .button_text:before, /*цвет кнопки меняется при наведении*/
.button:hover .button_text:after{
    background-color: #18b5a4;
}
```

16. в файле style.css когда рамочка отъезжает вправо, то кнопка анимацией показывает,что она готова для нажатия
Кнопка поднимается вверх, становится объемной.

```css
.button:hover .button_text{
    top: -10px; /*кнопка при наведении становится объемной, приподнимается*/
    color: #fff;
    transition: all 0.5s ease 0s; /*задержка 0.5 меньше 0.8 стандартной, чтобы основная анимация сработала быстрее*/
    box-shadow: 0 5px 0px 0 #0c5b52;
}
```

17. в файле style.css чтобы была реакция на нажатие кнопки

```css
.button:active .button_text { /*видим анимацию нажатия кнопки*/
    top: -7px;
    transition: all 0.1s ease 0s;
    box-shadow: 0 2px 0px 0 #0c5b52;
}
```

18. в файле style.css заставляем наши линии вокруг кнопки вращаться.
     Создаем ключевые фреймы

```css
@keyframes rotate { /*крутим элементы вокруг кнопки*/
    0%{
        transition: rotate(0deg);
    }
    100%{
        transform: rotate(360deg);
    }
}
```

19. в файле style.css заставляем наши линии вокруг кнопки вращаться с разной скоростью.

```css
/*элементы вращаются вокруг кнопки с разной скоростью*/
.button:before{
    animation: rotate 20s linear infinite;
}
.button:after{
    animation: rotate 25s linear infinite;
}
```

# Итог

1. в файле style.css

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
     height: 200px;
     display: flex;
     justify-content: center;
     align-items: center;
}

/*Основные стили*/

.button {
     font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
     text-decoration: none;
     position: relative;
     display: inline-block;
}
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
     transition: all 0.8s ease 0s;
     margin: 0px 0px 0px -40px;
}

/*элементы вращаются вокруг кнопки с разной скоростью*/
.button:before{
     animation: rotate 20s linear infinite;
}
.button:after{
     animation: rotate 25s linear infinite;
}

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
.button_text:before,
.button_text:after {
     content: '';
     position: absolute;
     width: 50%;
     height: 100%;
     background-color: #eee;
     transition: all 0.8s ease 0s;
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

.button:hover:before,
.button:hover:after {
     left: 100%;
     opacity: 0;
}

.button:hover .button_text{
     top: -10px; /*кнопка при наведении становится объемной, приподнимается*/
     color: #fff;
     transition: all 0.5s ease 0s; /*задержка 0.5 меньше 0.8 стандартной, чтобы основная анимация сработала быстрее*/
     box-shadow: 0 5px 0px 0 #0c5b52;
}

.button:hover .button_text:before, /*цвет кнопки меняется при наведении*/
.button:hover .button_text:after{
     background-color: #18b5a4;
}

.button:hover .button_text:before {
     width: 100%;
}

.button:active .button_text { /*видим анимацию нажатия кнопки*/
     top: -7px;
     transition: all 0.1s ease 0s;
     box-shadow: 0 2px 0px 0 #0c5b52;
}

@keyframes rotate { /*крутим элементы вокруг кнопки*/
     0%{
          transition: rotate(0deg);
     }
     100%{
          transform: rotate(360deg);
     }
}
```

![2024-12-28_14-11-48](https://github.com/user-attachments/assets/6275e407-f808-47a1-a19b-60ed9b5e3d3f)
![2024-12-28_14-12-07](https://github.com/user-attachments/assets/0b908006-2763-49b9-8b1f-3a3baba7fd27)
![2024-12-28_14-12-21](https://github.com/user-attachments/assets/93b4fb9b-6c25-4d71-a76f-2dd094fd376e)


2. в файле index.html

```html
<!--сообщаем браузеру, как стоит обрабатывать эту страницу-->
<!DOCTYPE html>
<!--оболочка документа, указываем язык содержимого-->
<html lang="ru">
<!--заголовок страницы, контейнер для других важных данных (не отображается)-->
<head>
     <!--заголовок страницы в браузере-->
     <title>Кнопка с анимацией "Свобода"</title>
     <!--подключаем CSS-->
     <link rel="stylesheet" href="style.css">
     <!--кодировка страницы-->
     <meta charset="utf-8">
     <!--адаптив-->
     <meta name="viewport" content="width=device-width">
</head>
<!--отображаемое тело страницы-->
<body>
<!--оболочка для демонстрации-->
<div class="wrapper">
     <!--контент-->
     <a href="#" class="button">
        <span class="button_text">
            <span>Свобода</span>
        </span>
     </a>
</div>
</body>
</html>
```

![2024-12-28_14-11-27](https://github.com/user-attachments/assets/ca2a7276-4969-492e-a144-6b789b4d3fa2)
