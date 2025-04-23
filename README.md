## 💣 Скрипт «Не нажимай» — Шутливый Обратный Отсчёт

Этот мини-скрипт добавляет на страницу кнопку с надписью «Не нажимай». При клике запускается 5-секундный обратный отсчёт, после чего появляется надпись «Boom!» и затем страница плавно исчезает. Подойдёт для шутки или демонстрации работы с DOM и анимацией на чистом JavaScript.

### 📦 Использование

Просто вставь этот код в консоль браузера или добавь в конец HTML-файла внутри тега `<script>...</script>`.

### 🧠 Что делает скрипт:

- Добавляет на страницу стилизованную кнопку.
- При клике запускается обратный отсчёт.
- Показывается анимированный баннер с таймером.
- Через 5 секунд появляется «💥 Boom!» и страница исчезает.

### 📋 Код (нажми, чтобы скопировать):

<details>
<summary>Показать/Скрыть JavaScript</summary>

```js
(function () {
  const style = document.createElement('style');
  style.textContent = `
    #start-countdown {
      position: fixed;
      bottom: 40px;
      right: 40px;
      background: crimson;
      color: white;
      font-size: 20px;
      padding: 12px 24px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      z-index: 9999;
      box-shadow: 0 0 15px rgba(0,0,0,0.5);
      font-family: monospace;
    }
    #countdown-banner {
      position: fixed;
      top: 20px;
      right: 20px;
      background: black;
      color: lime;
      font-size: 24px;
      padding: 10px 20px;
      border-radius: 8px;
      z-index: 9999;
      font-family: monospace;
      box-shadow: 0 0 10px lime;
    }
  `;
  document.head.appendChild(style);

  const button = document.createElement('button');
  button.id = 'start-countdown';
  button.textContent = 'Не нажимай';
  document.body.appendChild(button);

  function countdownAndFade() {
    const countdownSeconds = 5;
    let counter = countdownSeconds;

    const banner = document.createElement('div');
    banner.id = 'countdown-banner';
    banner.textContent = `💣 ${counter}`;
    document.body.appendChild(banner);

    const interval = setInterval(() => {
      counter--;
      if (counter <= 0) {
        clearInterval(interval);
        banner.textContent = '💥 Boom!';
        setTimeout(() => {
          document.body.style.transition = 'opacity 1s';
          document.body.style.opacity = '0';
        }, 1000);
      } else {
        banner.textContent = `💣 ${counter}`;
      }
    }, 1000);
  }

  button.addEventListener('click', countdownAndFade);
})();
```

</details>

### ⚠️ Внимание

Скрипт влияет на всю страницу: по завершении обратного отсчёта она исчезает.
