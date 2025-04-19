<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Traffic Light Simulator</title>
  <style>
    body {
      background: #222;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      color: white;
      font-family: Arial, sans-serif;
    }

    .traffic-light {
      background: #333;
      padding: 20px;
      border-radius: 20px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      box-shadow: 0 0 10px #000;
    }

    .light {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      background: #111;
      opacity: 0.3;
      transition: 0.3s;
    }

    .light.red.active {
      background: red;
      opacity: 1;
    }

    .light.yellow.active {
      background: yellow;
      opacity: 1;
    }

    .light.green.active {
      background: limegreen;
      opacity: 1;
    }

    .controls {
      position: absolute;
      bottom: 30px;
    }

    button {
      background: #444;
      color: white;
      border: none;
      padding: 10px 20px;
      margin: 0 5px;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background: #666;
    }
  </style>
</head>
<body>

  <div class="traffic-light" id="trafficLight">
    <div class="light red" id="red"></div>
    <div class="light yellow" id="yellow"></div>
    <div class="light green" id="green"></div>
  </div>

  <div class="controls">
    <button onclick="start()">Start</button>
    <button onclick="stop()">Stop</button>
  </div>

  <script>
    let current = 0;
    let interval;

    const lights = ["red", "yellow", "green"];

    function changeLight() {
      lights.forEach(light => {
        document.getElementById(light).classList.remove("active");
      });

      document.getElementById(lights[current]).classList.add("active");

      current = (current + 1) % lights.length;
    }

    function start() {
      if (!interval) {
        changeLight(); // start immediately
        interval = setInterval(changeLight, 2000); // change every 2 seconds
      }
    }

    function stop() {
      clearInterval(interval);
      interval = null;
      lights.forEach(light => {
        document.getElementById(light).classList.remove("active");
      });
    }
  </script>

</body>
</html>
