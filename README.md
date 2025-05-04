DIGITAL CLOCK

# PROGRAM
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Digital Clock & Stopwatch</title>
  <style>
    body {
      background-color: #0f172a;
      color: #f8fafc;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      height: 100vh;
      padding-top: 50px;
      gap: 60px;
    }

    .container {
      text-align: center;
      background-color: #1060e1;
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(176, 242, 8, 0.3);
      width: 250px;
    }

    .time-display {
      font-size: 3rem;
      margin-bottom: 20px;
    }

    .buttons button {
      margin: 5px;
      padding: 10px 20px;
      font-size: 1rem;
      border: none;
      border-radius: 10px;
      background-color: #3b82f6;
      color: white;
      cursor: pointer;
      transition: background-color 0.2s;
    }

    .buttons button:hover {
      background-color: #2563eb;
    }
  </style>
</head>
<body>
  <!-- Digital Clock -->
  <div class="container">
    <h2>Digital Clock</h2>
    <div class="time-display" id="digitalClock">00:00:00</div>
  </div>

  <!-- Stopwatch -->
  <div class="container">
    <h2>Stopwatch</h2>
    <div class="time-display" id="stopwatch">00:00:00</div>
    <div class="buttons">
      <button onclick="startStopwatch()">Start</button>
      <button onclick="stopStopwatch()">Stop</button>
      <button onclick="resetStopwatch()">Reset</button>
    </div>
  </div>

  <script>
    // Digital Clock
    function updateDigitalClock() {
      const now = new Date();
      const h = String(now.getHours()).padStart(2, '0');
      const m = String(now.getMinutes()).padStart(2, '0');
      const s = String(now.getSeconds()).padStart(2, '0');
      document.getElementById('digitalClock').textContent = `${h}:${m}:${s}`;
    }
    setInterval(updateDigitalClock, 1000);
    updateDigitalClock();

    // Stopwatch
    let stopwatchInterval;
    let stopwatchTime = 0;

    function formatTime(ms) {
      const totalSeconds = Math.floor(ms / 1000);
      const h = String(Math.floor(totalSeconds / 3600)).padStart(2, '0');
      const m = String(Math.floor((totalSeconds % 3600) / 60)).padStart(2, '0');
      const s = String(totalSeconds % 60).padStart(2, '0');
      return `${h}:${m}:${s}`;
    }

    function updateStopwatch() {
      stopwatchTime += 1000;
      document.getElementById('stopwatch').textContent = formatTime(stopwatchTime);
    }

    function startStopwatch() {
      if (!stopwatchInterval) {
        stopwatchInterval = setInterval(updateStopwatch, 1000);
      }
    }

    function stopStopwatch() {
      clearInterval(stopwatchInterval);
      stopwatchInterval = null;
    }

    function resetStopwatch() {
      stopStopwatch();
      stopwatchTime = 0;
      document.getElementById('stopwatch').textContent = '00:00:00';
    }
  </script>
</body>
</html>
```

# OUTPUT
![image](https://github.com/user-attachments/assets/6f7c8f03-7007-45c8-9294-883d089368e0)
