<!DOCTYPE html>
<html lang="ru">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Последние и интересные новости из мира искусственного интеллекта">
    <title>Новости ИИ 🤖</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="style.css">
</head>
# comment one
<body>
    <header>
        <div class="container">
            <h1>Новости Искусственного Интеллекта 🤖📰</h1>
            <nav>
                <ul>
                    <li><a href="#">🏠 Главная</a></li>
                    <li><a href="#">📰 Новости</a></li>
                    <li><a href="#">📞 Контакты</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <section class="hero">
        <div class="container">
            <h2>Будущее уже рядом 🚀: всё о последних трендах в мире ИИ</h2>
            <p>Узнайте, как искусственный интеллект 🤖 меняет наш мир и что нас ждёт впереди! 🌍</p>
        </div>
    </section>

    <section class="sort-buttons">
        <div class="container">
            <button id="sort-asc">Сортировать по дате: сначала старые</button>
            <button id="sort-desc">Сортировать по дате: сначала новые</button>
        </div>
    </section>

    <section class="news">
        <div class="container" id="news-container">
            <!-- Динамический контент будет добавлен сюда -->
        </div>
    </section>

    <footer>
        <div class="container">
            <p>&copy; 2024 Новости ИИ 🤖. Все права защищены.</p>
        </div>
    </footer>

    <script>
        // Функция для создания HTML-кода новости с датой
        function createNewsItem(newsItem) {
            return `
                <article class="news-item">
                    <h3>${newsItem.title}</h3>
                    <p>${newsItem.description}</p>
                    <p><small>Дата публикации: ${newsItem.date}</small></p>
                    <a href="${newsItem.link}" class="read-more">Читать подробнее ➡️</a>
                </article>
            `;
        }

        // Функция для отображения новостей
        function displayNews(newsArray) {
            const newsContainer = document.getElementById('news-container');
            newsContainer.innerHTML = ''; // Очищаем контейнер
            newsArray.forEach(item => {
                newsContainer.innerHTML += createNewsItem(item);
            });
        }

        // Сортировка по возрастанию даты
        function sortByDateAsc(newsArray) {
            return newsArray.slice().sort((a, b) => new Date(a.date) - new Date(b.date));
        }

        // Сортировка по убыванию даты
        function sortByDateDesc(newsArray) {
            return newsArray.slice().sort((a, b) => new Date(b.date) - new Date(a.date));
        }

        // Функция для симуляции загрузки данных с API
        function fetchNews() {
            // Моделируем задержку, как будто данные загружаются с бэкенда
            return new Promise((resolve) => {
                setTimeout(() => {
                    // Эмуляция данных, которые могли бы прийти с бэкенда
                    const news = [
                        {
                            title: "ИИ в искусстве 🎨: новые горизонты",
                            description: "Искусственный интеллект помогает создавать произведения искусства, которые вызывают восхищение у миллионов людей. Художники и разработчики объединяют усилия, чтобы создать нечто уникальное.",
                            link: "#",
                            date: "2024-10-01"
                        },
                        {
                            title: "Роботы в здравоохранении 🏥: новый взгляд",
                            description: "Новые роботы с искусственным интеллектом могут выполнять операции с невероятной точностью и помогать врачам диагностировать сложные заболевания.",
                            link: "#",
                            date: "2024-09-29"
                        },
                        {
                            title: "Будущее транспорта 🚗 с ИИ",
                            description: "Автономные автомобили с каждым годом становятся всё более распространёнными. Водители могут расслабиться и доверить управление искусственному интеллекту.",
                            link: "#",
                            date: "2024-09-25"
                        },
                        {
                            title: "Искусственный интеллект на службе человечества",
                            description: "ИИ продолжает развиваться, помогая людям с ограниченными возможностями, а также повышая эффективность производства в различных отраслях.",
                            link: "#",
                            date: "2024-10-03"
                        }
                    ];
                    resolve(news);
                }, 1000); // Моделируем задержку 1 секунда
            });
        }

        // Изначальная загрузка данных и отображение новостей
        let currentNews = [];

        // Загрузка данных и сортировка по убыванию
        fetchNews().then(news => {
            currentNews = news;
            displayNews(sortByDateDesc(currentNews)); // Отображаем новости по убыванию даты
        });

        // Добавляем события на кнопки для сортировки
        document.getElementById('sort-asc').addEventListener('click', () => {
            displayNews(sortByDateAsc(currentNews)); // Сортировка по возрастанию
        });

        document.getElementById('sort-desc').addEventListener('click', () => {
            displayNews(sortByDateDesc(currentNews)); // Сортировка по убыванию
        });
    </script>

</body>

</html>
