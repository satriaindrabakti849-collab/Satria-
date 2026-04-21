<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PNK - Perlindungan Nusantara Komunitas</title>
    <link rel="stylesheet" href="style.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
</head>
<body>

    <audio id="clickSound" src="https://www.soundjay.com/buttons/sounds/button-16.mp3"></audio>

    <section id="page1" class="hero-section">
        <div class="content" data-aos="fade-up">
            <h1>PNK</h1>
            <p>Perlindungan Nusantara Komunitas</p>
            <button onclick="nextPage(2)">Mulai Registrasi</button>
        </div>
    </section>

    <section id="page2" class="form-section hidden">
        <div class="container" data-aos="zoom-in">
            <h2>Biodata Intro</h2>
            <input type="text" id="nama" placeholder="Nama Lengkap">
            <input type="number" id="umur" placeholder="Umur">
            <input type="date" id="tgl_lahir" placeholder="Tanggal Lahir">
            <input type="text" id="tiktok" placeholder="Username TikTok (@...)">
            <select id="gender">
                <option value="">Jenis Kelamin</option>
                <option value="Laki-laki">Laki-laki</option>
                <option value="Perempuan">Perempuan</option>
            </select>
            <textarea id="alasan" placeholder="Alasan Bergabung"></textarea>
            <button onclick="generateCard()">Buat Kartu & Masuk Grup</button>
        </div>
    </section>

    <section id="page3" class="card-section hidden">
        <div id="introCard" class="card-preview">
            <h3>MEMBER PNK</h3>
            <hr>
            <p><strong>Nama:</strong> <span id="resNama"></span></p>
            <p><strong>TikTok:</strong> <span id="resTikTok"></span></p>
            <p><strong>Status:</strong> <span id="resGender"></span></p>
            <div class="ai-shield">Security Verified by PNK AI 🛡️</div>
        </div>
        <button class="btn-download" onclick="downloadCard()">Download Kartu</button>
        <p class="info-text">Anda akan diarahkan ke WhatsApp dalam 3 detik...</p>
    </section>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script src="script.js"></script>
</body>
</html>



            
