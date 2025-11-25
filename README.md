<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Моя Любовь — Для Тебя 💖</title>
    <style>
        /* === 0. Общие стили и Подгрузка шрифта === */
        @import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Caveat:wght@400;700&display=swap');
        
        body {
            font-family: 'Caveat', cursive; /* Рукописный шрифт для контента */
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px 10px;
            background: linear-gradient(135deg, #fce1e4 0%, #ffc4e2 100%);
            color: #4a4a4a;
            box-sizing: border-box;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* === 1. Заголовок "Я тебя люблю" (Адаптивный) === */
        .header-message {
            font-family: 'Pacifico', cursive;
            font-size: 3rem; /* Чуть меньше для мобильных */
            color: #d1217e;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            animation: pulse 2s infinite;
            text-align: center;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.03); }
            100% { transform: scale(1); }
        }

        /* === 2. Стили для Блокнота с Петельками (Пружиной) === */
        .notebook-container {
            position: relative;
            width: 90%; /* Адаптивная ширина */
            max-width: 350px; /* Максимальная ширина для десктопа */
            margin: 20px 0;
        }

        .book {
            width: 100%;
            height: 450px; /* Увеличили высоту */
            position: relative;
            perspective: 1500px;
            box-shadow: 10px 10px 30px rgba(0, 0, 0, 0.2);
            border-radius: 0 5px 5px 0;
            background-color: transparent; /* Общий фон контейнера */
        }
        
        /* Стилизация Пружины (петелек) */
        .spring {
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 25px; /* Ширина пружины */
            background-color: #6a6a6a; /* Цвет пружины */
            border-radius: 5px 0 0 5px;
            z-index: 15; /* Поверх страниц */
            box-shadow: inset 2px 0 5px rgba(0, 0, 0, 0.3);
        }

        .spring-hole {
            width: 100%;
            height: 20px;
            margin: 15px 0;
            background: linear-gradient(to right, #6a6a6a 0%, #8c8c8c 50%, #6a6a6a 100%);
            border-radius: 50%;
            box-shadow: inset 0 2px 2px rgba(0, 0, 0, 0.4);
        }

        .page {
            position: absolute;
            width: calc(100% - 25px); /* Учитываем ширину пружины */
            height: 100%;
            left: 25px; /* Сдвигаем вправо от пружины */
            padding: 20px 15px 40px 15px; /* Увеличили нижний паддинг */
            box-sizing: border-box;
            background-color: #fffaf0; /* Цвет старой бумаги */
            border: 1px solid #e0d9c4;
            border-left: 1px dashed #d1217e; /* Эффект разметки блокнота */
            border-radius: 0 5px 5px 0;
            transform-origin: left;
            transition: transform 0.8s ease-in-out;
            z-index: 10;
            font-size: 1.3rem; /* Более крупный шрифт для рукописного стиля */
            text-align: left;
            overflow: hidden;
            /* Устранение "отсвечивания" (блика) при 3D-повороте */
            backface-visibility: hidden; 
        }
        
        .page-content {
            white-space: pre-wrap;
        }

        /* Обложка (самая нижняя страница) */
        .page:last-child {
            background-color: #6a0044;
            color: white;
            z-index: 0;
            border: none;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            font-weight: bold;
            box-shadow: -5px 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 0 5px 5px 0;
            left: 25px;
        }
        
        /* Скрытые страницы - они перевернуты */
        .flipped {
            transform: rotateY(-180deg);
            pointer-events: none;
        }
        
        /* Эффект стопки страниц */
        .page[data-page="1"] { z-index: 10; }
        .page[data-page="2"] { z-index: 9; }
        .page[data-page="3"] { z-index: 8; }
        .page[data-page="4"] { z-index: 7; }
        .page[data-page="5"] { z-index: 6; } 
        
        /* Кнопка перелистывания */
        .next-page-btn {
            position: absolute;
            bottom: 10px;
            right: 15px; /* Сдвигаем на 15px от края блокнота */
            padding: 8px 15px;
            background-color: #ff69b4;
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: background-color 0.3s;
            font-weight: bold;
            z-index: 100;
            font-family: sans-serif; /* Не используем рукописный шрифт для кнопки */
            font-size: 0.9rem;
        }

        .next-page-btn:hover {
            background-color: #e04b96;
        }

        /* === 3. Дополнительные милые элементы (Адаптивные) === */
        .extras {
            margin-top: 40px;
            padding: 15px;
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
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        .song-container {
            margin-bottom: 20px;
            border: 4px solid #ff69b4;
            border-radius: 10px;
            overflow: hidden;
            background-color: #fff;
            padding: 5px;
            position: relative;
            /* Адаптивный контейнер для YouTube */
            padding-bottom: 56.25%; /* 16:9 соотношение сторон (высота / ширина) */
            height: 0;
        }
        .song-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        .sweet-words {
            font-style: italic;
            margin-top: 15px;
            color: #884466;
            padding: 10px;
            border: 1px dashed #d1217e;
            border-radius: 8px;
            font-size: 1.2rem;
        }

        /* Медиа-запрос для десктопов (крупных экранов) */
        @media (min-width: 768px) {
            .header-message {
                font-size: 4rem;
            }
            .notebook-container {
                width: 350px;
            }
        }

    </style>
</head>
<body>

    <h1 class="header-message">Я тебя люблю, **[Имя Девушки]**! ❤️</h1>
    
    <div class="notebook-container">
        <div class="spring">
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
            <div class="spring-hole"></div>
        </div>

        <div class="book">
            <button class="next-page-btn" id="nextPageBtn">Листай →</button>

            <div class="page" data-page="1">
                <div class="page-content">
                    **Привет, моя самая лучшая!**
                    
                    Этот маленький блокнот — это попытка уместить все мои чувства к тебе на нескольких листах. 
                    
                    Ты для меня целый мир.
                    
                    Нажимай на кнопку "Листай →" и читай дальше.
                    
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
                    
                    Пусть сегодня с тобой случится что-то очень хорошее.
                    
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
    </div>

    <div class="extras">
        <h3>Твоя любимая мелодия 🎵</h3>
        
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
        // === JavaScript для логики перелистывания (не изменился) ===
        const pages = document.querySelectorAll('.page');
        const nextPageBtn = document.getElementById('nextPageBtn');
        let currentPageIndex = 0;

        const totalFlippablePages = pages.length - 1; 

        nextPageBtn.addEventListener('click', () => {
            if (currentPageIndex < totalFlippablePages) {
                const pageToFlip = pages[currentPageIndex];
                
                // Добавляем класс, который запускает CSS-анимацию переворота
                pageToFlip.classList.add('flipped'); 
                
                // Сдвигаем z-index, чтобы перевернутая страница была под следующей
                // (это делает эффект перелистывания более гладким)
                pageToFlip.style.zIndex = totalFlippablePages - currentPageIndex;
                
                currentPageIndex++;

                if (currentPageIndex === totalFlippablePages) {
                    nextPageBtn.style.display = 'none';
                }
            }
        });
        
        // Добавляем возможность перевернуть обратно для просмотра
        pages.forEach((page, index) => {
            if (index < totalFlippablePages) {
                 page.addEventListener('click', () => {
                    if (page.classList.contains('flipped')) {
                        page.classList.remove('flipped');
                        // Возвращаем z-index
                        page.style.zIndex = 10 - index; 
                        currentPageIndex = index;
                        nextPageBtn.style.display = 'block';
                    }
                });
            }
        });

    </script>
</body>
</html>
