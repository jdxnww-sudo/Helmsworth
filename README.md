<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Моя Любовь — Для Тебя 💖</title>
    <style>
        /* === 1. Общие стили и фон === */
        body {
            font-family: 'Georgia', serif; /* Базовый шрифт */
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            background: linear-gradient(135deg, #fce1e4 0%, #ffc4e2 100%); /* Нежный розово-фиолетовый градиент */
            color: #4a4a4a;
            box-sizing: border-box;
            overflow-x: hidden;
        }

        /* === 2. Заголовок "Я тебя люблю" с красивым шрифтом === */
        .header-message {
            font-family: 'Pacifico', cursive; /* Использование красивого рукописного шрифта, который будет подгружен */
            font-size: 4rem; /* Очень крупный */
            color: #d1217e; /* Ярко-розовый */
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
            animation: pulse 2s infinite; /* Анимация пульсации */
            text-align: center;
        }
        
        /* Подгрузка шрифта Pacifico (для красивого рукописного стиля) */
        @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        /* === 3. Стили для Блокнота/Книги === */
        .book {
            width: 300px;
            height: 400px;
            position: relative;
            perspective: 1500px; /* Для 3D-эффекта перелистывания */
            margin: 30px 0;
            box-shadow: 10px 10px 30px rgba(0, 0, 0, 0.2);
            border-radius: 5px;
        }

        .page {
            position: absolute;
            width: 100%;
            height: 100%;
            padding: 20px;
            box-sizing: border-box;
            background-color: #fffaf0; /* Цвет старой бумаги */
            border: 1px solid #e0d9c4;
            border-radius: 0 5px 5px 0;
            transform-origin: left;
            transition: transform 0.8s ease-in-out;
            z-index: 10;
            line-height: 1.6;
            font-size: 1rem;
            text-align: left;
            overflow: hidden; /* Скрываем излишек текста */
        }
        
        .page-content {
            white-space: pre-wrap; /* Сохраняет переносы строк и пробелы из HTML */
        }

        /* Стиль для обложки (самая нижняя страница) */
        .page:last-child {
            background-color: #6a0044; /* Темно-бордовая обложка */
            color: white;
            z-index: 0;
            border: none;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
            box-shadow: -5px 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 5px;
        }
        
        /* Скрытые страницы - они перевернуты */
        .flipped {
            transform: rotateY(-180deg);
            pointer-events: none; /* Отключаем события для перевернутых страниц */
        }
        
        /* Эффект стопки страниц для тех, что еще не перевернуты */
        .page[data-page="1"] { z-index: 10; }
        .page[data-page="2"] { z-index: 9; }
        .page[data-page="3"] { z-index: 8; }
        .page[data-page="4"] { z-index: 7; }
        .page[data-page="5"] { z-index: 6; } /* Это предпоследняя страница перед обложкой */
        
        /* Кнопка перелистывания */
        .next-page-btn {
            position: absolute;
            bottom: 10px;
            right: 10px;
            padding: 8px 15px;
            background-color: #ff69b4; /* Ярко-розовый */
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: background-color 0.3s;
            font-weight: bold;
            z-index: 100; /* Всегда поверх страниц */
        }

        .next-page-btn:hover {
            background-color: #e04b96;
        }

        /* === 4. Дополнительные милые элементы === */
        .extras {
            margin-top: 40px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.6);
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
            width: 90%;
            max-width: 600px;
            text-align: center;
        }

        .extras h3 {
            color: #d1217e;
            font-family: 'Pacifico', cursive;
            font-size: 2rem;
            margin-bottom: 15px;
        }

        /* Стиль для песен (встроенное видео YouTube) */
        .song-container {
            margin-bottom: 20px;
            border: 4px solid #ff69b4;
            border-radius: 10px;
            overflow: hidden;
            background-color: #fff;
            padding: 5px;
        }
        .song-container iframe {
            display: block;
            width: 100%;
            height: 315px; /* Стандартная высота для YouTube */
            border: none;
        }

        /* Стиль для милых картинок (если загрузите свои) */
        .image-container img {
            max-width: 100%;
            height: auto;
            border-radius: 10px;
            margin-top: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .sweet-words {
            font-style: italic;
            margin-top: 20px;
            color: #884466;
            padding: 10px;
            border: 1px dashed #d1217e;
            border-radius: 8px;
        }

    </style>
</head>
<body>

    <h1 class="header-message">Я тебя люблю, **[Имя Девушки]**! ❤️</h1>
    
    <div class="book">
        
        <button class="next-page-btn" id="nextPageBtn">Вперёд →</button>

        <div class="page" data-page="1">
            <div class="page-content">
                **Привет, моя самая лучшая!**
                
                Этот маленький блокнот — это попытка уместить все мои чувства к тебе на нескольких листах. 
                
                Надеюсь, тебе понравится!
                
                Нажимай на кнопку "Вперёд →" и листай дальше.
                
                Твой,
                [Твое Имя]
            </div>
        </div>

        <div class="page" data-page="2">
            <div class="page-content">
                **⭐ Мои любимые моменты с тобой**
                
                1. Твоя улыбка по утрам.
                2. Наши долгие разговоры до полуночи.
                3. Как мы вместе готовили тот самый ужин.
                4. Наша первая поездка к морю/в горы.
                
                [Добавь сюда свои личные воспоминания!]
            </div>
        </div>

        <div class="page" data-page="3">
            <div class="page-content">
                **Пожелание на сегодня**
                
                Желаю тебе самого чудесного дня, моя радость! Пусть он будет таким же светлым и прекрасным, как ты. 
                
                Помни: даже если что-то не получается, я всегда рядом, чтобы поддержать.
                
                Ты — мое вдохновение.
            </div>
        </div>

        <div class="page" data-page="4">
            <div class="page-content">
                **Почему ты такая особенная?**
                
                Ты обладаешь невероятным талантом видеть красоту в мелочах. Твоя доброта делает мир лучше. Твоя целеустремленность восхищает.
                
                Спасибо, что ты есть.
            </div>
        </div>

        <div class="page" data-page="5">
            <div class="page-content">
                **Планы на будущее**
                
                Я хочу...
                
                ...увидеть с тобой мир.
                ...построить уютный дом.
                ...встречать каждое утро с тобой.
                ...[Тут твоя личная мечта!]
                
                Продолжение следует... (Листай на обложку!)
            </div>
        </div>

        <div class="page" data-page="6">
            **С любовью, твой [Твое Имя]**
        </div>
        
    </div>

    <div class="extras">
        <h3>Для поднятия настроения! 🎶</h3>
        
        <div class="song-container">
             <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ?autoplay=1&mute=1" title="Любимая Песня" allow="autoplay; encrypted-media; picture-in-picture" allowfullscreen></iframe>
        </div>
        
        <div class="sweet-words">
            **P.S. Если бы любовь была музыкой, то ты была бы моей самой любимой мелодией, которую я готов слушать вечно.**
        </div>

        <div class="image-container">
            </div>

    </div>

    <script>
        // === JavaScript для логики перелистывания ===
        
        const pages = document.querySelectorAll('.page');
        const nextPageBtn = document.getElementById('nextPageBtn');
        let currentPageIndex = 0;

        // Определяем количество страниц, которые можно листать (все, кроме последней - обложки)
        const totalFlippablePages = pages.length - 1; 

        nextPageBtn.addEventListener('click', () => {
            if (currentPageIndex < totalFlippablePages) {
                // Находим текущую активную (верхнюю) страницу для переворачивания
                const pageToFlip = pages[currentPageIndex];
                
                // Добавляем класс, который запускает CSS-анимацию переворота
                pageToFlip.classList.add('flipped'); 
                
                // Переходим к следующей странице
                currentPageIndex++;

                // Если это была предпоследняя страница, скрываем кнопку
                if (currentPageIndex === totalFlippablePages) {
                    nextPageBtn.style.display = 'none';
                }
            }
        });
        
        // Добавляем возможность перевернуть обратно для просмотра (бонус)
        // Если кликнуть по перевернутой странице, она вернется.
        pages.forEach((page, index) => {
             // Исключаем последнюю (обложку)
            if (index < totalFlippablePages) {
                 page.addEventListener('click', () => {
                     // Если страница перевернута (т.е. мы листали вперед)
                    if (page.classList.contains('flipped')) {
                        page.classList.remove('flipped');
                        currentPageIndex = index; // Возвращаемся к этой странице
                        nextPageBtn.style.display = 'block'; // Показываем кнопку снова
                    }
                });
            }
        });

    </script>
</body>
</html>
