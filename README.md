<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PNK - Perlindungan Nusantara Komunitas</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <style>
        .glass { background: rgba(255, 255, 255, 0.1); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.2); }
        .page { display: none; }
        .active { display: flex; }
    </style>
</head>
<body class="bg-slate-900 text-white overflow-hidden">

    <audio id="clickSound" src="https://www.soundjay.com/buttons/sounds/button-3.mp3"></audio>

    <section id="page1" class="page active min-h-screen flex-col items-center justify-center p-6 text-center">
        <h1 class="text-4xl font-bold mb-4 tracking-widest text-blue-400">PNK</h1>
        <p class="text-lg opacity-80 mb-8">Perlindungan Nusantara Komunitas</p>
        <div class="animate-pulse mb-6 text-sm text-green-400 font-mono">[ SECURITY SYSTEM: ACTIVE ]</div>
        <button onclick="nextPage(2)" class="glass px-8 py-3 rounded-full hover:bg-blue-600 transition">Mulai Perkenalan</button>
    </section>

    <section id="page2" class="page min-h-screen flex-col items-center justify-center p-6">
        <div class="glass p-8 rounded-2xl w-full max-w-md">
            <h2 class="text-2xl font-bold mb-6 text-center">Data Diri Anggota</h2>
            <div class="space-y-4">
                <input type="text" id="nama" placeholder="Nama Lengkap" class="w-full bg-transparent border-b border-gray-500 p-2 outline-none focus:border-blue-400">
                <div class="flex gap-2">
                    <input type="number" id="umur" placeholder="Umur" class="w-1/3 bg-transparent border-b border-gray-500 p-2 outline-none">
                    <input type="date" id="tglLahir" class="w-2/3 bg-transparent border-b border-gray-500 p-2 outline-none text-gray-400">
                </div>
                <input type="text" id="tiktok" placeholder="Username TikTok" class="w-full bg-transparent border-b border-gray-500 p-2 outline-none">
                <input type="text" id="asal" placeholder="Asal Daerah" class="w-full bg-transparent border-b border-gray-500 p-2 outline-none">
                <select id="gender" class="w-full bg-transparent border-b border-gray-500 p-2 outline-none text-gray-400">
                    <option value="" class="bg-slate-900">Jenis Kelamin</option>
                    <option value="Laki-laki" class="bg-slate-900">Laki-laki</option>
                    <option value="Perempuan" class="bg-slate-900">Perempuan</option>
                </select>
                <textarea id="alasan" placeholder="Alasan Bergabung" class="w-full bg-transparent border-b border-gray-500 p-2 outline-none"></textarea>
            </div>
            <button onclick="generateCard()" class="w-full mt-8
            
            
