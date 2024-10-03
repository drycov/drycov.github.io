---
layout: default
---


# Запрос на удаление аккаунта

Данная страница позволяет пользователям отправить запрос на удаление своего аккаунта. Форма включает поля для ввода email и причины удаления.

## HTML-код

```html
<h3>Запрос на удаление аккаунта</h3>
<form id="deleteAccountForm">
    <label for="userEmail">Ваш email:</label>
    <input type="email" id="userEmail" name="userEmail" required placeholder="Введите ваш email">

    <label for="subject">Причина:</label>
    <input type="text" id="subject" name="subject" required placeholder="Введите причину для удаления">

    <button type="submit">Отправить запрос</button>
</form>

<p id="responseMessage"></p>

<script type="module">
    // Импортируйте функции, которые вам нужны из SDK
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.14.0/firebase-app.js";
    import { getAnalytics } from "https://www.gstatic.com/firebasejs/10.14.0/firebase-analytics.js";

    // Конфигурация вашего веб-приложения Firebase
    const firebaseConfig = {
        apiKey: "AIzaSyCeMw2MuULJljBV8vSGO2ddfxm9se_EmKM",
        authDomain: "gibapon-f0708.firebaseapp.com",
        databaseURL: "https://gibapon-f0708-default-rtdb.firebaseio.com",
        projectId: "gibapon-f0708",
        storageBucket: "gibapon-f0708.appspot.com",
        messagingSenderId: "878739389133",
        appId: "1:878739389133:web:88c63f21e5ea54560b8784",
        measurementId: "G-MLET020CCP"
    };

    // Инициализация Firebase
    const app = initializeApp(firebaseConfig);
    const analytics = getAnalytics(app);

    document.getElementById('deleteAccountForm').addEventListener('submit', async function(event) {
        event.preventDefault(); // Отменяем стандартное поведение формы

        const email = document.getElementById('userEmail').value;
        const reason = document.getElementById('subject').value;
        const description = 'Прошу вас удалить мою Учетную запись из базы данных приложения Gi-PON по причине: ';
        
        // Создаем экземпляр Task
        const task = new Task({
            id: '', // Установите, если необходимо
            customer: '', 
            type: 999,
            address: "", // Установите, если необходимо
            status: 'pending', // Установите статус по умолчанию
            creationTime: new Date(), // Установите текущее время
            apartment: 'Application', // Установите, если необходимо
            creatorId: email, // Установите ID создателя
            assignedUserId: '', // Установите ID назначенного пользователя
            location: {latitude: 0, longitude: 0}, // Установите, если необходимо
            description: description + reason, // Установите, если необходимо
        });

        // Сохраняем задачу в Firestore
        await task.saveRequest(email, reason);

        document.getElementById('responseMessage').innerText = 
            `Запрос на удаление аккаунта отправлен для ${email}.`;

        // Очистка формы
        this.reset();
    });
</script>
