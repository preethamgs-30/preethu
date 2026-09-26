<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Phone Home Screen</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background: #000;
            color: white;
            font-family: Arial, sans-serif;
            height: 100vh;
            overflow: hidden;
        }

        .phone {
            width: 100%;
            height: 100vh;
            padding: 25px 25px;
            background: linear-gradient(
                135deg,
                #050505,
                #111,
                #020202
            );
        }

        /* Status bar */
        .status {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 15px;
            margin-bottom: 25px;
        }

        .right-status {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        /* Apps */
        .apps {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 28px 20px;
            text-align: center;
        }

        .app {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
        }

        .icon {
            width: 72px;
            height: 72px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 38px;
            background: white;
        }

        .messages {
            background: #fff;
        }

        .play {
            background: #fff;
        }

        .youtube {
            background: white;
        }

        .photos {
            background: linear-gradient(#00aaff, #2255ff);
        }

        .clock {
            background: white;
            color: #333;
            font-size: 32px;
        }

        .google {
            background: white;
            font-size: 27px;
        }

        .instagram {
            background: linear-gradient(
                45deg,
                #ffcc00,
                #ff0066,
                #8a00ff
            );
        }

        .phone-icon {
            background: #35d06f;
        }

        .whatsapp {
            background: #20d568;
        }

        .chrome {
            background: white;
        }

        .app-name {
            font-size: 16px;
        }

        /* Search bar */
        .search {
            margin: 35px auto;
            width: 90%;
            height: 58px;
            background: #303438;
            border-radius: 35px;
            display: flex;
            align-items: center;
            padding: 0 20px;
            font-size: 25px;
        }

        .search span {
            margin-left: 15px;
            font-size: 18px;
        }

        /* Screen time */
        .screen-time {
            margin-top: 15px;
            width: 280px;
            padding: 15px 20px;
            border-radius: 25px;
            background: #111620;
        }

        .screen-time small {
            font-size: 15px;
        }

        .screen-time h2 {
            margin-top: 5px;
            font-size: 30px;
        }

        /* Date and time */
        .date-time {
            margin-top: 100px;
        }

        .day {
            font-size: 45px;
            font-weight: bold;
        }

        .time {
            font-size: 85px;
            font-weight: bold;
            line-height: 1;
            margin-top: 10px;
        }

        .weather {
            margin-top: 20px;
            font-size: 25px;
        }

        /* Bottom dock */
        .dock {
            position: absolute;
            bottom: 30px;
            left: 25px;
            right: 25px;

            display: flex;
            justify-content: space-between;
        }

        .dock .icon {
            width: 75px;
            height: 75px;
        }

        @media (max-width: 400px) {
            .icon {
                width: 62px;
                height: 62px;
            }

            .app-name {
                font-size: 13px;
            }

            .day {
                font-size: 38px;
            }

            .time {
                font-size: 70px;
            }
        }
    </style>
</head>

<body>

<div class="phone">

    <!-- Status Bar -->
    <div class="status">
        <b id="currentTime">3:51</b>

        <div class="right-status">
            <span>5G</span>
            <span>📶</span>
            <span>🔋 44%</span>
        </div>
    </div>

    <!-- Apps -->
    <div class="apps">

        <div class="app">
            <div class="icon messages">💬</div>
            <div class="app-name">Messages</div>
        </div>

        <div class="app">
            <div class="icon play">▶️</div>
            <div class="app-name">Play Store</div>
        </div>

        <div class="app">
            <div class="icon youtube">▶️</div>
            <div class="app-name">YouTube</div>
        </div>

        <div class="app">
            <div class="icon photos">🌅</div>
            <div class="app-name">Photos</div>
        </div>

        <div class="app">
            <div class="icon clock">🕒</div>
            <div class="app-name">Clock</div>
        </div>

        <div class="app">
            <div class="icon google">G</div>
            <div class="app-name">Google</div>
        </div>

    </div>

    <!-- Google Search -->
    <div class="search">
        🔍 <span>Search</span>
    </div>

    <!-- Screen Time -->
    <div class="screen-time">
        <small>Screen time</small>
        <h2>5h 3m</h2>
    </div>

    <!-- Instagram / PhonePe -->
    <div class="apps" style="margin-top:20px;">

        <div class="app">
            <div class="icon instagram">◎</div>
            <div class="app-name">Instagram</div>
        </div>

        <div></div>

        <div class="app">
            <div class="icon">पे</div>
            <div class="app-name">PhonePe</div>
        </div>

    </div>

    <!-- Date and Time -->
    <div class="date-time">
        <div class="day">Saturday</div>

        <div class="time" id="bigTime">
            3:51
        </div>

        <div class="weather">
            26 Sept ☁️ 26°
        </div>
    </div>

    <!-- Bottom Dock -->
    <div class="dock">

        <div class="icon phone-icon">📞</div>

        <div class="icon">📷</div>

        <div class="icon whatsapp">💬</div>

        <div class="icon chrome">🌐</div>

    </div>

</div>

<script>
    function updateTime() {
        let now = new Date();

        let hours = now.getHours();
        let minutes = now.getMinutes();

        let ampm = hours >= 12 ? "PM" : "AM";

        hours = hours % 12;
        hours = hours ? hours : 12;

        minutes = minutes < 10 ? "0" + minutes : minutes;

        let time = hours + ":" + minutes;

        document.getElementById("currentTime").innerText = time;
        document.getElementById("bigTime").innerText = time;
    }

    updateTime();
    setInterval(updateTime, 1000);
</script>

</body>
</html>
