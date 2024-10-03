---
layout: default
---

# Запрос на удаление аккаунта

Данная страница позволяет пользователям отправить запрос на удаление своего аккаунта. Форма включает поля для ввода email и причины удаления.

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
    import { getFirestore, doc, setDoc } from "https://www.gstatic.com/firebasejs/10.14.0/firebase-firestore.js";

    // Модель задачи
    class Task {
        constructor(id, customer, type, address, status, creationTime, apartment, creatorId, assignedUserId, location, description) {
            this.id = id;
            this.customer = customer;
            this.type = type;
            this.address = address;
            this.status = status;
            this.creationTime = creationTime;
            this.apartment = apartment;
            this.creatorId = creatorId;
            this.assignedUserId = assignedUserId;
            this.location = location;
            this.description = description;
        }

        // Метод для сохранения задачи в Firestore
        async saveRequest() {
            const db = getFirestore();
            const taskRef = doc(db, "tasks", this.id); // замените "tasks" на вашу коллекцию

            try {
                await setDoc(taskRef, {
                    customer: this.customer,
                    type: this.type,
                    address: this.address,
                    status: this.status,
                    creationTime: this.creationTime,
                    apartment: this.apartment,
                    creatorId: this.creatorId,
                    assignedUserId: this.assignedUserId,
                    location: this.location,
                    description: this.description
                });
                console.log("Запись успешно добавлена!");
            } catch (error) {
                console.error("Ошибка при добавлении записи:", error);
            }
        }

        static parseType(value) {
            return typeof value === 'number' ? value : parseInt(value, 10) || 0;
        }

        static parseLocation(locationData) {
            return {
                latitude: locationData?.latitude || 0.0,
                longitude: locationData?.longitude || 0.0
            };
        }

        static fromMap(data) {
            return new Task(
                data.id,
                data.customer || '',
                Task.parseType(data.type),
                data.address || {},
                data.status || '',
                data.creationTime || new Date(),
                data.apartment || '',
                data.creatorId || '',
                data.assignedUserId || '',
                Task.parseLocation(data.location || {}),
                data.description || ''
            );
        }
    }

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
        const task = new Task(
            Date.now().toString(), // Генерация уникального ID
            '', // customer
            999, // type
            "", // address
            'pending', // status
            new Date(), // creationTime
            'Application', // apartment
            email, // creatorId
            '', // assignedUserId
            { latitude: 0, longitude: 0 }, // location
            description + reason // description
        );

        // Сохраняем задачу в Firestore
        await task.saveRequest();

        document.getElementById('responseMessage').innerText = 
            `Запрос на удаление аккаунта отправлен для ${email}.`;

        // Очистка формы
        this.reset();
    });
</script>
