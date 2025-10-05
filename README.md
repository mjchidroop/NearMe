# Ex04 Places Around Me
## Date: 06/10/2025
## Devoloped by: CHIDROOP M J
### Reference number: 25018548
## AIM
To develop a website to display details about the places around my house.

## DESIGN STEPS

### STEP 1
Create a Django admin interface.

### STEP 2
Download your city map from Google.

### STEP 3
Using ```<map>``` tag name the map.

### STEP 4
Create clickable regions in the image using ```<area>``` tag.

### STEP 5
Write HTML programs for all the regions identified.

### STEP 6
Execute the programs and publish them.

## CODE
```html
INDEX.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Welcome | MySurroundings</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      background: linear-gradient(to right, #0f2027, #203a43, #2c5364);
      color: white;
      font-family: 'Orbitron', sans-serif;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      overflow: hidden;
    }

    h1 {
      font-size: 4rem;
      animation: fadeIn 2s ease-out;
    }

    p {
      font-size: 1.5rem;
      opacity: 0.7;
      animation: fadeIn 3s ease-out;
    }

    .enter-btn {
      margin-top: 30px;
      padding: 15px 30px;
      font-size: 1.2rem;
      background-color: #00c6ff;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: transform 0.3s ease;
    }

    .enter-btn:hover {
      transform: scale(1.1);
      background-color: #0072ff;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>
  <h1>CHIDROOP M J</h1>
  <h2>25018548</h2>
  <p>Click here to EXPLORE my Surroundings</p>
  <button class="enter-btn" onclick="location.href='map.html'">EXPLORE</button>
</body>
</html>

MAP.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Explore | MySurroundings Interface</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/tsparticles@2.11.1/tsparticles.bundle.min.js"></script>
  <style>
    body {
      margin: 0;
      background: radial-gradient(circle at center, #0f2027, #203a43, #2c5364);
      font-family: 'Orbitron', sans-serif;
      color: #00ffe0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }

    h1 {
      font-size: 2.5rem;
      text-shadow: 0 0 10px #00ffe0;
      margin-top: 80px; /* Push down below nav bar */
      margin-bottom: 10px;
    }

    .map-container {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-top: 20px;
    }

    .map-container img {
      max-width: 90vw;
      height: auto;
      border: 2px solid #00ffe0;
      box-shadow: 0 0 20px #00ffe0;
    }

    .marker {
      position: absolute;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      background-color: gold;
      box-shadow: 0 0 10px gold;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
    }

    .marker:hover {
      transform: scale(1.5);
      box-shadow: 0 0 20px #fff;
    }

    .heart {
      background-color: red;
      box-shadow: 0 0 10px red;
    }

    .info-panel {
      position: absolute;
      background: #000;
      color: #00ffe0;
      padding: 10px;
      border: 2px solid #00ffe0;
      border-radius: 8px;
      font-size: 0.9rem;
      display: none;
      z-index: 10;
      box-shadow: 0 0 15px #00ffe0;
    }

    .back-btn {
      margin-top: 40px;
      padding: 12px 24px;
      border: 2px solid #00ffe0;
      color: #00ffe0;
      background: transparent;
      border-radius: 10px;
      font-size: 1rem;
      text-decoration: none;
      transition: all 0.3s ease;
    }

    .back-btn:hover {
      background-color: #00ffe0;
      color: #000;
      box-shadow: 0 0 15px #00ffe0;
    }

    .top-nav {
      position: fixed;
      top: 0;
      width: 100%;
      background: rgba(0, 0, 0, 0.6);
      display: flex;
      justify-content: center;
      gap: 20px;
      padding: 12px 0;
      z-index: 1000;
      box-shadow: 0 0 15px #00ffe0;
      border-bottom: 2px solid #00ffe0;
    }

    .top-nav a {
      color: #00ffe0;
      text-decoration: none;
      font-weight: bold;
      font-size: 1rem;
      padding: 8px 16px;
      border-radius: 6px;
      transition: all 0.3s ease;
    }

    .top-nav a:hover {
      background-color: #00ffe0;
      color: #000;
      box-shadow: 0 0 10px #00ffe0;
    }

    #tsparticles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
    }
  </style>
</head>
<body>
  <nav class="top-nav">
  <a href="map.html"> Map</a>
  <a href="home.html"> Home</a>
  <a href="walknjog.html"> Walk</a>
  <a href="busstand.html"> Busstand</a>
  <a href="cybernaut.html"> Cybernaut</a>
  <a href="college.html"> College</a>
  <a href="temple.html"> Temple</a>
</nav>
  <div id="tsparticles"></div>
  <h1>MAP INTERFACE</h1>

  <div class="map-container">
    <img src="my_map.jpg" alt="My Map">

    <!-- Markers -->
    <div class="marker" style="top: 33px; left: 608px;" onclick="showInfo('walknjog')"></div>
    <div class="marker" style="top: 453px; left: 550px;" onclick="showInfo('busstand')"></div>
    <div class="marker" style="top: 685px; left: 690px;" onclick="showInfo('cybernaut')"></div>
    <div class="marker" style="top: 258px; left: 1372px;" onclick="showInfo('college')"></div>
    <div class="marker" style="top: 792px; left: 915px;" onclick="showInfo('temple')"></div>
    <div class="marker heart" style="top: 650px; left: 758px;" onclick="showInfo('home')"></div>

    <!-- Info Panels -->
    <div id="walknjog" class="info-panel" style="top: 60px; left: 640px;" onclick="window.location.href='walknjog.html'">
  <strong>Walk 'n' Jog Karur</strong><br>Open park for walking and jogging.
</div>

<div id="busstand" class="info-panel" style="top: 480px; left: 580px;" onclick="window.location.href='busstand.html'">
  <strong>Karur New Central Busstand</strong><br>Major transport hub.
</div>

<div id="cybernaut" class="info-panel" style="top: 710px; left: 720px;" onclick="window.location.href='cybernaut.html'">
  <strong>CybernatEdTech</strong><br>Tech learning center.
</div>

<div id="college" class="info-panel" style="top: 280px; left: 1400px;" onclick="window.location.href='college.html'">
  <strong>Karur Govt. Medical College</strong><br>Medical education and research.
</div>

<div id="temple" class="info-panel" style="top: 820px; left: 945px;" onclick="window.location.href='temple.html'">
  <strong>Temple</strong><br>Spiritual center and heritage site.
</div>

<div id="home" class="info-panel" style="top: 670px; left: 790px;" onclick="window.location.href='home.html'">
  <strong> MY HOME</strong><br>Sweetest place on Earth.
</div>
  </div>

  <a class="back-btn" href="index.html">← Return to Boot Interface</a>

  <script>
    function showInfo(id) {
      const panels = document.querySelectorAll('.info-panel');
      panels.forEach(p => p.style.display = 'none');
      document.getElementById(id).style.display = 'block';
    }
  </script>
  <script>
  tsParticles.load("tsparticles", {
    fullScreen: { enable: false },
    background: { color: { value: "transparent" } },
    particles: {
      number: { value: 60 },
      color: { value: "#00ffe0" },
      shape: { type: "circle" },
      opacity: { value: 0.5 },
      size: { value: 3 },
      move: {
        enable: true,
        speed: 1,
        direction: "none",
        outModes: { default: "bounce" }
      }
    }
  });
  </script>
</body>
</html>

WALK'N'JOG.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Walk 'n' Jog | MySurroundings</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: radial-gradient(circle at center, #0f2027, #203a43, #2c5364);
      color: #00ffe0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }
    .content {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 40px;
      margin-top: 40px;
    }
    .image-box {
      max-width: 500px;
      border: 4px solid #00ffe0;
      box-shadow: 0 0 25px #00ffe0;
      border-radius: 10px;
      overflow: hidden;
    }
    .image-box img {
      width: 100%;
      height: auto;
      display: block;
    }
    .text-box {
      max-width: 500px;
    }
    h1 {
      font-size: 2.5rem;
      text-shadow: 0 0 15px #00ffe0;
    }
    p {
      font-size: 1.1rem;
      text-shadow: 0 0 10px #000;
    }
    .back-btn {
      margin-top: 40px;
      padding: 12px 24px;
      border: 2px solid #00ffe0;
      color: #00ffe0;
      background: transparent;
      border-radius: 10px;
      font-size: 1rem;
      text-decoration: none;
      transition: all 0.3s ease;
    }
    .back-btn:hover {
      background-color: #00ffe0;
      color: #000;
      box-shadow: 0 0 15px #00ffe0;
    }
  </style>
</head>
<body>
  <h1>🏃 Walk 'n' Jog Karur</h1>
  <div class="content">
    <div class="image-box">
      <img src="walknjog.jpg" alt="Walk 'n' Jog Image">
    </div>
    <div class="text-box">
      <p>A peaceful green zone for fitness and relaxation. Whether you're walking under the pergola or jogging past the fountain, this space keeps Karur moving.</p>
    </div>
  </div>
  <a class="back-btn" href="map.html">← Back to Map Interface</a>
</body>
</html>

BUSSTAND.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Busstand | MySurroundings</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: radial-gradient(circle at center, #0f2027, #203a43, #2c5364);
      color: #00ffe0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }
    .content {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 40px;
      margin-top: 40px;
    }
    .image-box {
      max-width: 500px;
      border: 4px solid #00ffe0;
      box-shadow: 0 0 25px #00ffe0;
      border-radius: 10px;
      overflow: hidden;
    }
    .image-box img {
      width: 100%;
      height: auto;
      display: block;
    }
    .text-box {
      max-width: 500px;
    }
    h1 {
      font-size: 2.5rem;
      text-shadow: 0 0 15px #00ffe0;
    }
    p {
      font-size: 1.1rem;
      text-shadow: 0 0 10px #000;
    }
    .back-btn {
      margin-top: 40px;
      padding: 12px 24px;
      border: 2px solid #00ffe0;
      color: #00ffe0;
      background: transparent;
      border-radius: 10px;
      font-size: 1rem;
      text-decoration: none;
      transition: all 0.3s ease;
    }
    .back-btn:hover {
      background-color: #00ffe0;
      color: #000;
      box-shadow: 0 0 15px #00ffe0;
    }
  </style>
</head>
<body>
  <h1>🚌 Karur New Central Busstand</h1>
  <div class="content">
    <div class="image-box">
      <img src="busstand.jpg" alt="Busstand Image">
    </div>
    <div class="text-box">
      <p>The pulse of the city’s transport. Buses to every corner of Tamil Nadu and beyond. Always buzzing, always moving.</p>
    </div>
  </div>
  <a class="back-btn" href="map.html">← Back to Map Interface</a>
</body>
</html>

COLLEGE.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Medical College | MySurroundings</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: radial-gradient(circle at center, #0f2027, #203a43, #2c5364);
      color: #00ffe0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }
    .content {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 40px;
      margin-top: 40px;
    }
    .image-box {
      max-width: 500px;
      border: 4px solid #00ffe0;
      box-shadow: 0 0 25px #00ffe0;
      border-radius: 10px;
      overflow: hidden;
    }
    .image-box img {
      width: 100%;
      height: auto;
      display: block;
    }
    .text-box {
      max-width: 500px;
    }
    h1 {
      font-size: 2.5rem;
      text-shadow: 0 0 15px #00ffe0;
    }
    p {
      font-size: 1.1rem;
      text-shadow: 0 0 10px #000;
    }
    .back-btn {
      margin-top: 40px;
      padding: 12px 24px;
      border: 2px solid #00ffe0;
      color: #00ffe0;
      background: transparent;
      border-radius: 10px;
      font-size: 1rem;
      text-decoration: none;
      transition: all 0.3s ease;
    }
    .back-btn:hover {
      background-color: #00ffe0;
      color: #000;
      box-shadow: 0 0 15px #00ffe0;
    }
  </style>
</head>
<body>
  <h1>🏥 Karur Govt. Medical College</h1>
  <div class="content">
    <div class="image-box">
      <img src="college.jpg" alt="Medical College Image">
    </div>
    <div class="text-box">
      <p>Training the healers of tomorrow. A center of excellence in medical education and community care.</p>
    </div>
  </div>
  <a class="back-btn" href="map.html">← Back to Map Interface</a>
</body>
</html>

TEMPLE.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Temple | MySurroundings</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: radial-gradient(circle at center, #0f2027, #203a43, #2c5364);
      color: #00ffe0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }

    .content {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      gap: 40px;
      flex-wrap: wrap;
      max-width: 1200px;
      margin-top: 40px;
    }

    .image-box {
      flex: 1;
      max-width: 500px;
      border: 4px solid #00ffe0;
      box-shadow: 0 0 25px #00ffe0;
      border-radius: 10px;
      overflow: hidden;
    }

    .image-box img {
      width: 100%;
      height: auto;
      display: block;
    }

    .text-box {
      flex: 1;
      max-width: 500px;
    }

    h1 {
      font-size: 2.5rem;
      text-shadow: 0 0 15px #00ffe0;
      margin-bottom: 20px;
    }

    p {
      font-size: 1.1rem;
      text-shadow: 0 0 10px #000;
    }

    .back-btn {
      margin-top: 40px;
      padding: 12px 24px;
      border: 2px solid #00ffe0;
      color: #00ffe0;
      background: transparent;
      border-radius: 10px;
      font-size: 1rem;
      text-decoration: none;
      transition: all 0.3s ease;
    }

    .back-btn:hover {
      background-color: #00ffe0;
      color: #000;
      box-shadow: 0 0 15px #00ffe0;
    }
  </style>
</head>
<body>
  <h1>🛕 Temple</h1>

  <div class="content">
    <div class="image-box">
      <img src="temple.jpg" alt="Temple Image">
    </div>
    <div class="text-box">
      <p>A place of peace, prayer, and tradition. This sacred site is where Karur’s spiritual heartbeat echoes through generations. Whether you seek blessings or quiet reflection, this temple welcomes all.</p>
    </div>
  </div>

  <a class="back-btn" href="map.html">← Back to Map Interface</a>
</body>
</html>

CYBERNAUT.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Temple | MySurroundings</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: radial-gradient(circle at center, #0f2027, #203a43, #2c5364);
      color: #00ffe0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }

    .content {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      gap: 40px;
      flex-wrap: wrap;
      max-width: 1200px;
      margin-top: 40px;
    }

    .image-box {
      flex: 1;
      max-width: 500px;
      border: 4px solid #00ffe0;
      box-shadow: 0 0 25px #00ffe0;
      border-radius: 10px;
      overflow: hidden;
    }

    .image-box img {
      width: 100%;
      height: auto;
      display: block;
    }

    .text-box {
      flex: 1;
      max-width: 500px;
    }

    h1 {
      font-size: 2.5rem;
      text-shadow: 0 0 15px #00ffe0;
      margin-bottom: 20px;
    }

    p {
      font-size: 1.1rem;
      text-shadow: 0 0 10px #000;
    }

    .back-btn {
      margin-top: 40px;
      padding: 12px 24px;
      border: 2px solid #00ffe0;
      color: #00ffe0;
      background: transparent;
      border-radius: 10px;
      font-size: 1rem;
      text-decoration: none;
      transition: all 0.3s ease;
    }

    .back-btn:hover {
      background-color: #00ffe0;
      color: #000;
      box-shadow: 0 0 15px #00ffe0;
    }
  </style>
</head>
<body>
  <h1>🛕 Temple</h1>

  <div class="content">
    <div class="image-box">
      <img src="temple.jpg" alt="Temple Image">
    </div>
    <div class="text-box">
      <p>A place of peace, prayer, and tradition. This sacred site is where Karur’s spiritual heartbeat echoes through generations. Whether you seek blessings or quiet reflection, this temple welcomes all.</p>
    </div>
  </div>

  <a class="back-btn" href="map.html">← Back to Map Interface</a>
</body>
</html>

HOME.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>MY HOME | MySurroundings</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Orbitron', sans-serif;
      background: linear-gradient(135deg, #ff6ec4, #7873f5, #00ffe0);
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }

    h1 {
      font-size: 3rem;
      text-shadow: 0 0 20px #fff;
      margin-bottom: 20px;
    }

    p {
      font-size: 1.2rem;
      max-width: 600px;
      text-shadow: 0 0 10px #000;
    }

    .image-box {
      max-width: 500px;
      border: 4px solid #00ffe0;
      box-shadow: 0 0 25px #00ffe0, 0 0 50px #00ffe0 inset;
      border-radius: 12px;
      overflow: hidden;
      margin-bottom: 30px;
      animation: pulseGlow 2s infinite;
    }

    .image-box img {
      width: 100%;
      height: auto;
      display: block;
    }

    @keyframes pulseGlow {
      0% {
        box-shadow: 0 0 25px #00ffe0, 0 0 50px #00ffe0 inset;
      }
      50% {
        box-shadow: 0 0 40px #00ffe0, 0 0 80px #00ffe0 inset;
      }
      100% {
        box-shadow: 0 0 25px #00ffe0, 0 0 50px #00ffe0 inset;
      }
    }

    .back-btn {
      margin-top: 40px;
      padding: 12px 24px;
      border: 2px solid white;
      color: white;
      background: transparent;
      border-radius: 10px;
      font-size: 1rem;
      text-decoration: none;
      transition: all 0.3s ease;
    }

    .back-btn:hover {
      background-color: white;
      color: #000;
      box-shadow: 0 0 15px white;
    }
  </style>
</head>
<body>
  <h1> Welcome to MY HOME</h1>

  <div class="image-box">
    <img src="home.jpg" alt="My Home Image">
  </div>

  <p>This is the heart of your surroundings. A place of comfort, memories, and vibrant energy. You’ve arrived at the most special spot on your map.</p>

  <a class="back-btn" href="map.html">← Back to Map Interface</a>
</body>
</html>

```


## OUTPUT
![alt text](<Screenshot (29).png>)

![alt text](<Screenshot (30).png>)

![alt text](<Screenshot (31).png>)

![alt text](<Screenshot (32).png>)

![alt text](<Screenshot (33).png>)

![alt text](<Screenshot (34).png>)

![alt text](<Screenshot (35).png>)

![alt text](<Screenshot (36).png>)

![alt text](<Screenshot (37).png>)

![alt text](<Screenshot (38).png>)

![alt text](<Screenshot (39).png>)

![alt text](<Screenshot (40).png>)

![alt text](<Screenshot (41).png>)

![alt text](<Screenshot (42).png>)


## RESULT
The program for implementing image maps using HTML is executed successfully.
