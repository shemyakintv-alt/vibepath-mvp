<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VibePath — Учись создавая</title>
    <style>
        /* --- CSS СТИЛИ (Дизайн и Анимации) --- */
        
        :root {
            --primary-color: #2563EB; /* Акцентный синий */
            --bg-color: #F9FAFB;      /* Светлый фон */
            --text-color: #1F2937;    /* Темно-серый текст */
            --card-bg: #FFFFFF;       /* Фон карточек */
            --success-color: #10B981; /* Зеленый для успеха */
            --border-color: #D1D5DB;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            line-height: 1.6;
        }

        /* Шапка сайта */
        header {
            background: var(--card-bg);
            padding: 1rem 2rem;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            max-width: 800px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .logo {
            font-weight: 800;
            font-size: 1.25rem;
            color: var(--primary-color);
            letter-spacing: -0.5px;
        }

        .progress-container {
            flex-grow: 1;
            margin: 0 1rem;
            max-width: 300px;
        }

        .progress-bar-bg {
            background-color: #E5E7EB;
            height: 8px;
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-bar-fill {
            background-color: var(--primary-color);
            height: 100%;
            width: 0%; 
            transition: width 0.5s ease-in-out;
        }

        .lesson-counter {
            font-size: 0.9rem;
            font-weight: 600;
            color: #6B7280;
        }

        /* Основной контент */
        main {
            flex: 1;
            max-width: 800px;
            margin: 2rem auto;
            padding: 0 1.5rem;
            width: 100%;
            box-sizing: border-box;
        }

        .lesson-card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 2rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.6s forwards;
        }

        @keyframes fadeInUp {
            to { opacity: 1; transform: translateY(0); }
        }

        h2 { margin-top: 0; color: #111827; }
        
        .analogy-box {
            background-color: #EFF6FF;
            border-left: 4px solid var(--primary-color);
            padding: 1rem;
            margin: 1.5rem 0;
            border-radius: 0 8px 8px 0;
        }

        .analogy-title {
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
            display: block;
        }

        /* Блок практики и кнопок */
        .action-area {
            margin-top: 2rem;
            padding-top: 2rem;
            border-top: 1px solid #E5E7EB;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        button {
            cursor: pointer;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            transition: all 0.2s;
            font-size: 1rem;
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: white;
            padding: 0.75rem 1.5rem;
            box-shadow: 0 4px 6px rgba(37, 99, 235, 0.2);
        }

        .btn-primary:hover {
            background-color: #1D4ED8;
            transform: translateY(-2px);
        }

        .btn-primary:active {
            transform: translateY(0);
        }

        .btn-secondary {
            background-color: white;
            border: 1px solid #D1D5DB;
            color: #374151;
            padding: 0.75rem 1.5rem;
        }

        .btn-secondary:hover {
            background-color: #F3F4F6;
        }

        .btn-success {
            background-color: var(--success-color);
            color: white;
            padding: 0.75rem 1.5rem;
        }

        .sos-btn {
            align-self: flex-start;
            font-size: 0.85rem;
            color: #6B7280;
            background: transparent;
            text-decoration: underline;
            padding: 0;
            margin-top: 0.5rem;
        }

        .sos-hint {
            display: none;
            margin-top: 0.5rem;
            font-size: 0.9rem;
            color: #4B5563;
            background: #FEF3C7;
            padding: 0.75rem;
            border-radius: 6px;
        }

        /* Стили для формы ввода Email (Урок 4) */
        .email-form {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            margin-top: 1rem;
        }

        .input-field {
            padding: 0.75rem;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.2s;
        }

        .input-field:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        /* Виртуальный сайт (Результат работы ученика) */
        .virtual-site-preview {
            margin-top: 3rem;
            border: 1px dashed #9CA3AF;
            border-radius: 8px;
            padding: 2rem;
            background: white;
            text-align: center;
            min-height: 150px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
        }

        .preview-label {
            position: absolute;
            top: -12px;
            left: 20px;
            background: var(--bg-color);
            padding: 0 10px;
            font-size: 0.8rem;
            color: #6B7280;
            font-weight: 600;
        }

        #site-content {
            font-size: 1.5rem;
            font-weight: bold;
            color: #111827;
            transition: all 0.3s;
        }

        #site-button {
            margin-top: 1rem;
            display: none; 
        }

        /* Подвал */
        footer {
            text-align: center;
            padding: 2rem;
            background: #F3F4F6;
            margin-top: auto;
        }

        .share-btn {
            background: transparent;
            color: var(--primary-color);
            border: 1px solid var(--primary-color);
            padding: 0.5rem 1rem;
            font-size: 0.9rem;
        }

        .share-btn:hover {
            background: #EFF6FF;
        }

        /* Адаптивность для мобильных */
        @media (max-width: 600px) {
            .header-content { flex-direction: column; align-items: flex-start; }
            .progress-container { width: 100%; max-width: none; margin: 0.5rem 0; }
            .lesson-card { padding: 1.5rem; }
        }
    </style>
</head>
<body>

    <!-- ШАПКА -->
    <header>
        <div class="header-content">
            <div class="logo">VibePath 🚀</div>
            <div class="progress-container">
                <div class="progress-bar-bg">
                    <div class="progress-bar-fill" id="progressBar"></div>
                </div>
            </div>
            <div class="lesson-counter" id="lessonCounter">Урок 1 из 4</div>
        </div>
    </header>

    <!-- ОСНОВНОЙ КОНТЕНТ -->
    <main>
        <div class="lesson-card" id="lessonContainer">
            <!-- Сюда JavaScript будет вставлять контент урока -->
        </div>

        <!-- ВИРТУАЛЬНЫЙ САЙТ (Результат) -->
        <div class="virtual-site-preview">
            <span class="preview-label">Твой сайт в разработке</span>
            <div id="site-content">...</div>
            <button id="site-button" class="btn-primary">Нажми меня</button>
        </div>
    </main>

    <!-- ПОДВАЛ -->
    <footer>
        <button class="share-btn" onclick="shareProgress()">📤 Поделиться прогрессом</button>
    </footer>

    <script>
        /* --- JAVASCRIPT ЛОГИКА --- */

        // 1. Данные уроков (Массив объектов)
        const lessons = [
            {
                id: 1,
                title: "Фундамент: Зачем нам структура?",
                theory: "Представь, что ты строишь дом. Нельзя начать с крыши. В веб-разработке фундамент — это HTML. Это скелет твоего сайта.",
                task: "Нажми кнопку, чтобы добавить 'скелет' на твой виртуальный сайт.",
                actionText: "Добавить структуру",
                successMsg: "Отлично! Теперь у твоего сайта есть основа.",
                sosHint: "HTML — это язык разметки. Он говорит браузеру: 'Вот здесь заголовок, а здесь текст'. Без него браузер не поймет, что показывать."
            },
            {
                id: 2,
                title: "Смыслы: Как говорить с пользователем?",
                theory: "Код без смысла — просто набор букв. Вейп-кодинг — это управление смыслом. Мы говорим ИИ, ЧТО написать, а он делает КАК.",
                task: "Измени заголовок своего сайта через кнопку.",
                actionText: "Обновить смысл",
                successMsg: "Супер! Ты только что изменил контент динамически.",
                sosHint: "В обычном программировании мы пишем `document.getElementById...`. В вейп-кодинге ты просто говоришь: 'Сделай текст приветственным', и ИИ меняет его."
            },
            {
                id: 3,
                title: "Действие: Первая кнопка",
                theory: "Сайт должен реагировать на пользователя. Кнопка — это мост между человеком и машиной. Она превращает чтение в действие.",
                task: "Добавь интерактивную кнопку на свой сайт.",
                actionText: "Создать кнопку",
                successMsg: "Поздравляем! Ты создал свой первый интерактивный элемент.",
                sosHint: "Кнопки нужны для конверсии. Без призыва к действию (CTA) пользователь просто уйдет."
            },
            {
                id: 4,
                title: "Следующий шаг: Доступ к клубу",
                theory: "Ты освоил базу! Теперь ты понимаешь логику вейп-кодинга. Чтобы двигаться дальше и создавать сложные приложения, нужна практика и поддержка.",
                task: "Оставь свой email, чтобы получить доступ к закрытому клубу VibePath и следующим модулям бесплатно.",
                isForm: true, // Флаг, что это урок с формой
                successMsg: "Спасибо! Мы свяжемся с тобой и откроем доступ.",
                sosHint: "Мы используем email, чтобы прислать тебе ссылку на следующие уроки и шаблоны промптов."
            }
        ];

        // 2. Управление состоянием (localStorage)
        let currentLessonIndex = parseInt(localStorage.getItem('vibePathProgress')) || 0;
        
        // Элементы DOM
        const lessonContainer = document.getElementById('lessonContainer');
        const progressBar = document.getElementById('progressBar');
        const lessonCounter = document.getElementById('lessonCounter');
        const siteContent = document.getElementById('site-content');
        const siteButton = document.getElementById('site-button');

        // 3. Функция отрисовки урока
        function renderLesson() {
            // Если уроки закончились
            if (currentLessonIndex >= lessons.length) {
                showCompletionScreen();
                return;
            }

            const lesson = lessons[currentLessonIndex];

            // Обновляем счетчик и прогресс-бар
            lessonCounter.textContent = `Урок ${currentLessonIndex + 1} из ${lessons.length}`;
            const progressPercent = ((currentLessonIndex) / lessons.length) * 100;
            progressBar.style.width = `${progressPercent}%`;

            // Генерируем HTML урока
            let actionHtml = '';
            
            if (lesson.isForm) {
                // Если это урок с формой (Урок 4)
                actionHtml = `
                    <p><strong>Задание:</strong> ${lesson.task}</p>
                    <div class="email-form">
                        <input type="email" id="userEmail" class="input-field" placeholder="tvoi@email.com">
                        <button id="actionBtn" class="btn-primary" onclick="submitEmail()">Получить доступ</button>
                    </div>
                    <button id="nextBtn" class="btn-success" style="display:none;" onclick="nextLesson()">Завершить курс →</button>
                    <button class="sos-btn" onclick="toggleSOS()"> SOS: Я не понимаю</button>
                    <div id="sosHintBox" class="sos-hint">${lesson.sosHint}</div>
                `;
            } else {
                // Обычные уроки (1-3)
                actionHtml = `
                    <p><strong>Задание:</strong> ${lesson.task}</p>
                    <button id="actionBtn" class="btn-primary" onclick="completeTask()">
                        ${lesson.actionText}
                    </button>
                    <button id="nextBtn" class="btn-success" style="display:none;" onclick="nextLesson()">
                        Следующий урок →
                    </button>
                    <button class="sos-btn" onclick="toggleSOS()">🆘 SOS: Я не понимаю</button>
                    <div id="sosHintBox" class="sos-hint">${lesson.sosHint}</div>
                `;
            }

            lessonContainer.innerHTML = `
                <h2>${lesson.title}</h2>
                <p>${lesson.theory}</p>
                
                <div class="analogy-box">
                    <span class="analogy-title">💡 Аналогия:</span>
                    ${lesson.sosHint} 
                </div>

                <div class="action-area">
                    ${actionHtml}
                </div>
            `;
            
            // Сброс состояния виртуального сайта для наглядности (если нужно)
            if (currentLessonIndex === 0) {
                siteContent.textContent = "...";
                siteButton.style.display = "none";
            }
        }

        // 4. Логика выполнения задания (Уроки 1-3)
        function completeTask() {
            const actionBtn = document.getElementById('actionBtn');
            const nextBtn = document.getElementById('nextBtn');
            const lesson = lessons[currentLessonIndex];

            // Анимация кнопки
            actionBtn.style.transform = "scale(0.95)";
            setTimeout(() => actionBtn.style.transform = "scale(1)", 100);

            // Изменяем виртуальный сайт в зависимости от урока
            if (currentLessonIndex === 0) {
                siteContent.textContent = "Привет, мир! Это мой первый сайт";
                siteContent.style.color = "#111827";
            } else if (currentLessonIndex === 1) {
                siteContent.textContent = "Я учусь создавать с ИИ 🚀";
                siteContent.style.color = "#2563EB";
            } else if (currentLessonIndex === 2) {
                siteButton.style.display = "block";
            }

            // Показываем сообщение об успехе и кнопку "Далее"
            actionBtn.style.display = "none";
            
            const successMsg = document.createElement('div');
            successMsg.textContent = `✅ ${lesson.successMsg}`;
            successMsg.style.color = "#10B981";
            successMsg.style.fontWeight = "bold";
            successMsg.style.marginBottom = "1rem";
            
            const actionArea = document.querySelector('.action-area');
            actionArea.insertBefore(successMsg, nextBtn);

            nextBtn.style.display = "inline-block";
        }

        // 5. Логика отправки Email (Урок 4)
        function submitEmail() {
            const emailInput = document.getElementById('userEmail');
            const email = emailInput.value;
            const actionBtn = document.getElementById('actionBtn');
            const nextBtn = document.getElementById('nextBtn');
            const lesson = lessons[currentLessonIndex];

            if (!email || !email.includes('@')) {
                alert("Пожалуйста, введите корректный email адрес.");
                return;
            }

            // Сохраняем email в localStorage (для теста)
            localStorage.setItem('vibePathUserEmail', email);
            
            // Имитация отправки
            actionBtn.style.display = "none";
            emailInput.disabled = true;

            const successMsg = document.createElement('div');
            successMsg.textContent = `✅ ${lesson.successMsg}`;
            successMsg.style.color = "#10B981";
            successMsg.style.fontWeight = "bold";
            successMsg.style.marginBottom = "1rem";
            
            const actionArea = document.querySelector('.action-area');
            actionArea.insertBefore(successMsg, nextBtn);

            nextBtn.style.display = "inline-block";
        }

        // 6. Переход к следующему уроку
        function nextLesson() {
            currentLessonIndex++;
            localStorage.setItem('vibePathProgress', currentLessonIndex);
            
            // Анимация исчезновения
            lessonContainer.style.opacity = '0';
            lessonContainer.style.transform = 'translateY(-20px)';
            
            setTimeout(() => {
                lessonContainer.style.transform = 'translateY(20px)'; 
                renderLesson();
            }, 300);
        }

        // 7. Показать SOS подсказку
        function toggleSOS() {
            const hintBox = document.getElementById('sosHintBox');
            hintBox.style.display = hintBox.style.display === 'block' ? 'none' : 'block';
        }

        // 8. Экран завершения
        function showCompletionScreen() {
            progressBar.style.width = "100%";
            lessonCounter.textContent = "Готово!";
            
            lessonContainer.innerHTML = `
                <h2>🎉 Поздравляем!</h2>
                <p>Ты прошел базовый модуль VibePath.</p>
                <p>Ты понял логику: <strong>Структура → Смысл → Действие → Сбор лидов</strong>.</p>
                <div class="analogy-box">
                    <span class="analogy-title">Что дальше?</span>
                    Проверь свою почту (или папку Спам). Мы пришлем туда ссылки на продвинутые модули.
                </div>
                <div class="action-area">
                    <button class="btn-secondary" onclick="resetProgress()">🔄 Начать заново</button>
                </div>
            `;
        }

        // 9. Сброс прогресса
        function resetProgress() {
            localStorage.removeItem('vibePathProgress');
            localStorage.removeItem('vibePathUserEmail');
            currentLessonIndex = 0;
            location.reload();
        }

        // 10. Поделиться
        function shareProgress() {
            const text = `Я прохожу курс VibePath и уже создал свой первый сайт без кода! Присоединяйся: https://shemyakintv-alt.github.io/vibepath-mvp/`;
            navigator.clipboard.writeText(text).then(() => {
                alert("Ссылка скопирована! Отправь её другу.");
            });
        }

        // Запуск при загрузке страницы
        renderLesson();

    </script>
</body>
</html>
