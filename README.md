# Satria-
satriaindrabakti
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toko Satria - SMM Panel</title>
    <style>
        /* CSS STYLE */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0f0f0f;
            color: white;
            text-align: center;
            margin: 0;
            overflow-x: hidden;
        }

        .hidden { display: none; }

        /* Halaman Animasi Awal */
        #welcome-screen {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: radial-gradient(circle, #1e1e1e 0%, #000 100%);
            cursor: pointer;
        }

        .bounce {
            font-size: 4rem;
            font-weight: bold;
            color: #ff0000;
            text-shadow: 0 0 20px rgba(255, 0, 0, 0.7);
            animation: bounce 1.5s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
            40% {transform: translateY(-40px);}
            60% {transform: translateY(-20px);}
        }

        /* Halaman Utama */
        #main-app {
            padding: 20px;
            animation: fadeIn 1s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .platform-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            max-width: 400px;
            margin: 20px auto;
        }

        .platform-grid button {
            padding: 15px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            border-radius: 12px;
            border: none;
            transition: 0.3s;
            color: white;
        }

        .btn-tiktok { background: #000; border: 2px solid #fff; }
        .btn-fb { background: #1877F2; }
        .btn-ig { background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888); }
        .btn-yt { background: #FF0000; }

        .platform-grid button:hover { transform: scale(1.05); }

        /* Area Order */
        #order-section {
            background: #1e1e1e;
            padding: 20px;
            border-radius: 20px;
            max-width: 500px;
            margin: 20px auto;
            border: 1px solid #333;
        }

        select, button.gacha-btn {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border-radius: 8px;
            border: none;
            font-size: 1rem;
        }

        .gacha-btn {
            background: #f1c40f;
            color: #000;
            font-weight: bold;
            cursor: pointer;
        }

        .price-display {
            background: #222;
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
        }

        .old-price { text-decoration: line-through; color: #888; }
        .new-price { color: #2ecc71; font-size: 1.8rem; font-weight: bold; display: block; }

        .payment-box h4 { margin-bottom: 10px; }
        .btn-payment {
            width: 45%;
            padding: 10px;
            margin: 5px;
            border-radius: 5px;
            border: none;
            font-weight: bold;
            cursor: pointer;
        }
        .dana { background: #008CFF; color: white; }
        .gopay { background: #00AED6; color: white; }

    </style>
</head>
<body>

    <div id="welcome-screen" onclick="startApp()">
        <h1 class="bounce">TOKO SATRIA</h1>
        <p>Klik Layar untuk Masuk</p>
    </div>

    <div id="main-app" class="hidden">
        <header>
            <h1>TOKO SATRIA</h1>
            <p>Pilih Platform Sosial Media:</p>
        </header>

        <div class="platform-grid">
            <button class="btn-tiktok" onclick="selectPlatform('TikTok')">TikTok</button>
            <button class="btn-fb" onclick="selectPlatform('Facebook')">Facebook</button>
            <button class="btn-ig" onclick="selectPlatform('Instagram')">Instagram</button>
            <button class="btn-yt" onclick="selectPlatform('YouTube')">YouTube</button>
        </div>

        <div id="order-section" class="hidden">
            <h3 id="selected-title">Layanan</h3>
            
            <label>Pilih Fitur:</label>
            <select id="service-type">
                <option value="Followers">Followers</option>
                <option value="Like">Like</option>
                <option value="Views">Views</option>
                <option value="Komentar">Komentar</option>
            </select>

            <div class="price-display">
                <span class="old-price">Harga Normal: Rp 200.000</span>
                <button class="gacha-btn" onclick="kocokGacha()">KLIK GACHA DISKON!</button>
                <span id="label-diskon" style="color: yellow; font-weight: bold;"></span>
                <span class="new-price" id="final-price">Rp 200.000</span>
            </div>

            <div class="payment-box">
                <h4>Pilih Metode Pembayaran:</h4>
                <button class="btn-payment dana" onclick="bayar('Dana')">DANA</button>
                <button class="btn-payment gopay" onclick="bayar('Gopay')">GOPAY</button>
            </div>
        </div>
    </div>

    <audio id="click-sound" src="https://www.soundjay.com/buttons/sounds/button-09.mp3"></audio>
    <audio id="gacha-sound" src="https://www.soundjay.com/misc/sounds/bell-ringing-05.mp3"></audio>

    <script>
        /* JAVASCRIPT LOGIC */
        let hargaAwal = 200000;
        let hargaSetelahDiskon = 200000;
        let nomorTujuan = "6287740859655";
        let platformAktif = "";

        function startApp() {
            // Putar suara dan pindah halaman
            document.getElementById('click-sound').play();
            document.getElementById('welcome-screen').classList.add('hidden');
            document.getElementById('main-app').classList.remove('hidden');
        }

        function selectPlatform(name) {
            platformAktif = name;
            document.getElementById('order-section').classList.remove('hidden');
            document.getElementById('selected-title').innerText = "Layanan " + name;
            // Reset harga setiap pilih platform
            hargaSetelahDiskon = 200000;
            document.getElementById('final-price').innerText = "Rp 200.000";
            document.getElementById('label-diskon').innerText = "";
        }

        function kocokGacha() {
            document.getElementById('gacha-sound').play();
            
            // Random diskon 10% sampai 100%
            let diskon = Math.floor(Math.random() * 91) + 10; 
            
            // Hitung harga baru
            let potongan = (diskon / 100) * hargaAwal;
            hargaSetelahDiskon = hargaAwal - potongan;

            // Logika sesuai permintaan: otomatis murah (misal min 5rb atau 100rb)
            if (hargaSetelahDiskon < 5000) {
                hargaSetelahDiskon = 5000;
            }

            // Update Tampilan
            document.getElementById('label-diskon').innerText = "SELAMAT! DISKON " + diskon + "%";
            document.getElementById('final-price').innerText = "Rp " + hargaSetelahDiskon.toLocaleString('id-ID');
            
            alert("Kamu mendapatkan diskon " + diskon + "%! Harga sekarang menjadi Rp " + hargaSetelahDiskon.toLocaleString('id-ID'));
        }

        function bayar(metode) {
            let fitur = document.getElementById('service-type').value;
            let total = document.getElementById('final-price').innerText;
            
            let pesan = `Halo Toko Satria, saya ingin membeli:\n\n` +
                        `- Platform: ${platformAktif}\n` +
                        `- Fitur: ${fitur}\n` +
                        `- Total Bayar: ${total}\n` +
                        `- Metode: ${metode}\n\n` +
                        `Mohon proses ke nomor Dana/Gopay: ${nomorTujuan}`;

            // Link WhatsApp API untuk mengirim data otomatis ke nomor kamu
            let urlWA = `https://api.whatsapp.com/send?phone=${nomorTujuan}&text=${encodeURIComponent(pesan)}`;
            
            window.open(urlWA, '_blank');
        }
    </script>
</body>
</html>
