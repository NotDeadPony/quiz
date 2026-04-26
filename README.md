# 🎮 IT Квіз — Коледж ІСТ КНЕУ

Інтерактивний квіз для дня спеціальності з real-time лідербордом.

---

## 🚀 Як запустити за 10 хвилин

### Крок 1 — Створи Firebase проєкт (безкоштовно)

1. Перейди на [console.firebase.google.com](https://console.firebase.google.com)
2. Натисни **"Add project"** → введи будь-яку назву (напр. `it-quiz-kneu`)
3. Google Analytics — можна вимкнути, натисни **Continue**
4. Зачекай поки проєкт створюється → **Continue**

### Крок 2 — Підключи Realtime Database

1. В лівому меню: **Build → Realtime Database**
2. Натисни **"Create Database"**
3. Вибери регіон — `europe-west1 (Belgium)` → **Next**
4. Вибери **"Start in test mode"** → **Enable**

### Крок 3 — Отримай Firebase Config

1. В лівому меню зверху натисни шестерню ⚙️ → **Project settings**
2. Прокрути вниз до **"Your apps"**
3. Натисни іконку `</>` (Web)
4. Введи назву додатку (будь-яка) → **Register app**
5. Скопіюй блок `firebaseConfig`:

```js
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "it-quiz-kneu.firebaseapp.com",
  databaseURL: "https://it-quiz-kneu-default-rtdb.europe-west1.firebasedatabase.app",
  projectId: "it-quiz-kneu",
  storageBucket: "it-quiz-kneu.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

### Крок 4 — Встав конфіг в index.html

Відкрий `index.html`, знайди блок `FB_CONFIG` (~рядок 180) і замінь всі `"ЗАМІНИТИ"` на свої значення:

```js
const FB_CONFIG = {
  apiKey:            "AIza...",          // ← вставити
  authDomain:        "it-quiz-kneu.firebaseapp.com",
  databaseURL:       "https://it-quiz-kneu-default-rtdb.europe-west1.firebasedatabase.app",
  projectId:         "it-quiz-kneu",
  storageBucket:     "it-quiz-kneu.appspot.com",
  messagingSenderId: "123456789",
  appId:             "1:123456789:web:abc123"
};
```

### Крок 5 — Розгорни на GitHub Pages

```bash
# 1. Створи новий репозиторій на github.com (публічний)
# 2. Завантаж index.html та README.md

git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/ТВІ_НІКНЕЙМ/it-quiz.git
git push -u origin main

# 3. В налаштуваннях репо: Settings → Pages → Source: main branch → Save
# 4. Через 1-2 хвилини сайт буде доступний за адресою:
#    https://ТВІ_НІКНЕЙМ.github.io/it-quiz/
```

---

## 🖥️ Як використовувати під час презентації

| URL | Для кого |
|-----|---------|
| `https://ТВІ_НІКНЕЙМ.github.io/it-quiz/` | Учасники (по QR-коду) |
| `https://ТВІ_НІКНЕЙМ.github.io/it-quiz/?admin` | Ти (викладач) |

### Сценарій проведення:
1. **Відкрий** `?admin` на своєму екрані/ноутбуці
2. **Покажи QR-код** з посиланням для учасників — вони приєднуються зі своїх телефонів
3. **Натисни "ПОЧАТИ КВІЗ"** — всі учасники одночасно бачать перше питання
4. **Натисни "Закрити питання"** — щоб завершити відповіді та показати правильну відповідь
5. **Натисни "Показати рейтинг / далі"** — рейтинг з'являється кожні 3 питання
6. Повторюй до кінця — фінальний лідерборд з'явиться автоматично

---

## ✏️ Як змінити питання

У файлі `index.html` знайди масив `QUESTIONS` (~рядок 100):

```js
const QUESTIONS = [
  {
    text: "🎨 Малює макети сайтів та додатків...",
    answers: ["Frontend-розробник", "UX/UI дизайнер", "DevOps-інженер", "DBA"],
    correct: 1    // ← індекс правильної відповіді (0, 1, 2 або 3)
  },
  // ... додавай скільки хочеш питань
];
```

**Правила:**
- `answers` — рівно 4 варіанти відповіді
- `correct` — індекс правильного (0 = перший, 1 = другий, 2 = третій, 3 = четвертий)
- Кількість питань необмежена

---

## ⏱️ Час на питання

Знайди рядок `const TIME_PER_Q = 20;` і зміни число (секунди).

---

## 🔄 Скинути між сесіями

В адмін-панелі натисни **"🔄 Скинути все"** — це видалить усіх гравців та перезапустить квіз.

---

## 📱 Генерація QR-коду

Будь-який безкоштовний сервіс:
- [qr-code-generator.com](https://www.qr-code-generator.com)
- [goqr.me](https://goqr.me)

Вставь посилання на свій GitHub Pages сайт.
