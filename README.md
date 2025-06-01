<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pengumuman Kelulusan SDN Sundawenang</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', Arial, sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            color: #333;
        }
        
        .container {
            width: 90%;
            max-width: 800px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            padding: 30px;
            margin: 30px 0;
            text-align: center;
        }
        
        h1 {
            color: #6a3093;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #777;
            margin-bottom: 30px;
            font-weight: 500;
        }
        
        .teaser {
            font-size: 1.2rem;
            margin: 40px 0;
            color: #6a3093;
            font-weight: 600;
        }
        
        .input-container {
            margin: 30px 0;
        }
        
        input {
            padding: 12px 20px;
            width: 70%;
            border: 2px solid #ddd;
            border-radius: 30px;
            font-size: 1rem;
            outline: none;
            transition: border 0.3s;
        }
        
        input:focus {
            border-color: #6a3093;
        }
        
        button {
            background-color: #6a3093;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 30px;
            font-size: 1rem;
            cursor: pointer;
            margin-top: 10px;
            transition: background-color 0.3s;
        }
        
        button:hover {
            background-color: #5a2580;
        }
        
        .result-container {
            display: none;
            margin-top: 30px;
            animation: fadeIn 0.5s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .congrats {
            font-size: 1.5rem;
            color: #6a3093;
            margin: 20px 0;
            font-weight: 600;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        
        th, td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        th {
            background-color: #f8f8f8;
        }
        
        .status {
            color: #28a745;
            font-weight: 600;
        }
        
        .action-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 30px;
            flex-wrap: wrap;
        }
        
        .action-btn {
            padding: 10px 20px;
            border-radius: 30px;
            font-size: 0.9rem;
            cursor: pointer;
            transition: transform 0.2s;
        }
        
        .action-btn:hover {
            transform: translateY(-3px);
        }
        
        .celebrate {
            background-color: #ffc107;
            color: #333;
        }
        
        .motivation {
            background-color: #17a2b8;
            color: white;
        }
        
        .surprise {
            background-color: #dc3545;
            color: white;
        }
        
        .message {
            margin-top: 20px;
            padding: 15px;
            border-radius: 10px;
            display: none;
            animation: fadeIn 0.3s;
        }
        
        .celebrate-message {
            background-color: #fff3cd;
            color: #856404;
        }
        
        .motivation-message {
            background-color: #d1ecf1;
            color: #0c5460;
        }
        
        .surprise-message {
            background-color: #f8d7da;
            color: #721c24;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Hasil Kelulusan</h1>
        <div class="subtitle">SDN Sundawenang, Tahun Ajaran 2024/2025</div>
        
        <div id="teaser-section">
            <div class="teaser">🎉 Siap-siap deg-degan, tulis namamu di sini ya! 🎉</div>
            <div class="input-container">
                <input type="text" id="name-input" placeholder="Masukkan nama lengkapmu">
                <button onclick="checkResult()">Lihat Hasil</button>
            </div>
        </div>
        
        <div id="result-section" class="result-container">
            <div class="congrats">Selamat Atas Kelulusanmu! Kamu Luar Biasa!</div>
            
            <table>
                <thead>
                    <tr>
                        <th>Nama</th>
                        <th>NISN</th>
                        <th>Status</th>
                    </tr>
                </thead>
                <tbody id="result-table">
                    <!-- Data akan diisi oleh JavaScript -->
                </tbody>
            </table>
            
            <div class="action-buttons">
                <button class="action-btn celebrate" onclick="showCelebrate()">Rayakan!</button>
                <button class="action-btn motivation" onclick="showMotivation()">Kata Motivasi</button>
                <button class="action-btn surprise" onclick="showSurprise()">Kejutan!</button>
            </div>
            
            <div id="celebrate-message" class="message celebrate-message"></div>
            <div id="motivation-message" class="message motivation-message"></div>
            <div id="surprise-message" class="message surprise-message"></div>
        </div>
    </div>

    <script>
        // Data siswa dari Excel (disederhanakan)
        const students = [
            { nama: "ADE LENI", nisn: "3132157300" },
            { nama: "ADELIA PARANISA", nisn: "3179596063" },
            { nama: "ADITYA NAUFAL FEBRIAN", nisn: "3158218648" },
            { nama: "ADITYA RAMDHAN", nisn: "3168634805" },
            { nama: "ADVA HARDIYANTO", nisn: "3169591903" },
            { nama: "AGUNG MUHAMAD RAMDANI", nisn: "3162671534" },
            { nama: "Ahmad Fadillah", nisn: "3121672046" },
            { nama: "Ai Santi Nuraeni", nisn: "3121488222" },
            { nama: "Ai Tantri", nisn: "3124853118" },
            { nama: "Albian Nur Cahya", nisn: "3123782715" },
            { nama: "ALIFAH AZZAHRA", nisn: "3158109080" },
            { nama: "Amelia Siti Salam", nisn: "3137523668" },
            { nama: "Andita Izmi Azkia", nisn: "3131068853" },
            { nama: "Angga Jenal", nisn: "3127939682" },
            { nama: "ANGGA SAPUTRA", nisn: "3162687772" },
            { nama: "ANGGI PERMANA", nisn: "3145856681" },
            { nama: "ANISA GUSTIANI", nisn: "3178033778" },
            { nama: "Aqila Khairul Azmi", nisn: "0136653860" },
            { nama: "ARFIANI MAULIDA", nisn: "3163759451" },
            { nama: "Ariski", nisn: "3132758720" },
            { nama: "AYANG SULISTIANI", nisn: "3168706546" },
            { nama: "AYU YULIANINGSIH", nisn: "3159613419" },
            { nama: "Caca Setiawan", nisn: "3137547756" },
            { nama: "CAHRIYAL NUGRAHA", nisn: "3168364532" },
            { nama: "Cahyani Destriyanti", nisn: "3137983364" },
            { nama: "CAHYATI", nisn: "3179007280" },
            { nama: "Cica Sri Ayu", nisn: "3127552078" },
            { nama: "Citra", nisn: "3138688429" },
            { nama: "DADAN LESMANA", nisn: "3141958154" },
            { nama: "DAFA AIDIL NUGRAHA", nisn: "3170275947" },
            { nama: "DAFA PEBRIAN", nisn: "3145977860" },
            { nama: "Dais Aulia Nopianti", nisn: "3121846421" },
            { nama: "Dais Rahmawati", nisn: "3133676751" },
            { nama: "DE NAILA ALMIRA", nisn: "3121261132" },
            { nama: "DERIS ANDIKA WIJAYA", nisn: "3141829492" },
            { nama: "DERIS FAUZIATUL AN NUR", nisn: "3169098472" },
            { nama: "DETI KUSMIA", nisn: "3175359334" },
            { nama: "DEWI LESTARI", nisn: "3147899348" },
            { nama: "Dewi Sinta Anggraeni", nisn: "3134210004" },
            { nama: "DIANA ALYA FAJRIN", nisn: "3183822923" },
            { nama: "DIMAS MUHAMMAD", nisn: "3147396388" },
            { nama: "DISTI UMAIZA NURFALAH", nisn: "3172280690" },
            { nama: "DITA JULIANI", nisn: "3185288703" },
            { nama: "DZAKIA HAURA ZAHRINA", nisn: "3174300483" },
            { nama: "Elwiki Alfaeyza", nisn: "3122462552" },
            { nama: "Fahmi Ramdhani", nisn: "3124667022" },
            { nama: "GANJAR HABIBURRAHMAN", nisn: "3153879237" },
            { nama: "GILANG RAMDHAN", nisn: "3160013744" },
            { nama: "HANA KHOIRUN NISA", nisn: "3144729699" },
            { nama: "Harlina Apriani", nisn: "3134699912" },
            { nama: "HIKAM NUR RAMDAN", nisn: "3160111578" },
            { nama: "HIKMAT SOFIYAN", nisn: "3162057167" },
            { nama: "HILMA MALIKA NUR SABILA", nisn: "3173499822" },
            { nama: "IFAN IRPINSYAH", nisn: "3137452653" },
            { nama: "KAILA FITRI NURSANI", nisn: "3148570958" },
            { nama: "KAISYA NUR LAILA", nisn: "3171148659" },
            { nama: "KAMILAH NURIPAH", nisn: "3151947398" },
            { nama: "KHARLA ANASTASHYA", nisn: "3165189370" },
            { nama: "LESTI MAULIDA", nisn: "3157957867" },
            { nama: "Lia Agustin", nisn: "3139688808" },
            { nama: "MEYDA SEFIRA SUTIAWAN", nisn: "3145152763" },
            { nama: "MUHAMAD ALVIN", nisn: "3156632019" },
            { nama: "MUHAMAD RAFA", nisn: "3144442588" },
            { nama: "Muhamad Rif'al Putra", nisn: "3125047434" },
            { nama: "MUHAMAD SIDIQ", nisn: "3168494531" },
            { nama: "MUHAMMAD DENI RAMDANI", nisn: "3131400672" },
            { nama: "Muhammad Miftah Al Ansori", nisn: "3122266580" },
            { nama: "Muhammad Nayaka Rabbani", nisn: "0166327424" },
            { nama: "Muhammad Pirmansah", nisn: "3128168400" },
            { nama: "MUHAMMAD RAI REJEKI", nisn: "3162252368" },
            { nama: "MUTIA LESTARI", nisn: "3150690902" },
            { nama: "Nabila Nurlaila", nisn: "3139478162" },
            { nama: "Nadhira Azalea Ihsaniah", nisn: "3168937119" },
            { nama: "NADIA AULIA", nisn: "3155013961" },
            { nama: "NAJWA QURROTU A'INUN", nisn: "3164546653" },
            { nama: "Naura Hasna Annida", nisn: "3138886078" },
            { nama: "NENG ARUM KHASANAH", nisn: "3167136580" },
            { nama: "NENG RISMA HERMAWATI", nisn: "3148696128" },
            { nama: "NINDIA FAUZIYYAH", nisn: "3159438198" },
            { nama: "NOVI IRAWATI", nisn: "3160920367" },
            { nama: "Nuri Apriyani Dewi", nisn: "3126342330" },
            { nama: "NURI ASANTI", nisn: "3180719666" },
            { nama: "RADINKA ANINDYA PUTRI", nisn: "3144313129" },
            { nama: "RADIT PANDILAH", nisn: "3150873427" },
            { nama: "RADIT YUDISTIRA", nisn: "3140301885" },
            { nama: "Rahmani", nisn: "3125318796" },
            { nama: "RAIHAN NUGRAHA", nisn: "3143306081" },
            { nama: "Raina Safira", nisn: "3132058481" },
            { nama: "RAISYA AULIA ZAHRA", nisn: "3168758722" },
            { nama: "RAISYA NURAINI", nisn: "3155774239" },
            { nama: "RAMADHAN SUTIOSO SAPUTRA", nisn: "0149924270" },
            { nama: "RAMDHAN RAMADHANISH", nisn: "3148763287" },
            { nama: "Rania", nisn: "3125934176" },
            { nama: "RANINDIA TIARA", nisn: "3163550222" },
            { nama: "RAPIF ALDZUKWAN RIZKI", nisn: "3154831981" },
            { nama: "REFALDI ARGA NURJAMAN", nisn: "3179012185" },
            { nama: "Reiza Ahmad Firdaus", nisn: "3130794017" },
            { nama: "Resti Ailia", nisn: "3137352543" },
            { nama: "RESYA APRILIA", nisn: "3143301658" },
            { nama: "RHAN SAPUTRA", nisn: "3174258053" },
            { nama: "Rihaadatul 'Aisy", nisn: "3136643530" },
            { nama: "RINRIN INDRIYANI", nisn: "3148351137" },
            { nama: "Ripki Septiadi", nisn: "3135229838" },
            { nama: "Risha Aqila Melati", nisn: "3135517004" },
            { nama: "Riski Maulana", nisn: "3123165218" },
            { nama: "RIZKY ARDIANSYAH PURNAMA", nisn: "3166240165" },
            { nama: "RIZKY SILVIA", nisn: "3144893260" },
            { nama: "Rosahani", nisn: "3137551355" },
            { nama: "SAFWAN AQILA PRANAJA", nisn: "3169007612" },
            { nama: "San San Aditya", nisn: "3121436571" },
            { nama: "SANDI RADITYA SANJAYA", nisn: "3140521161" },
            { nama: "SASKIA NABILA", nisn: "3157902122" },
            { nama: "Septiana", nisn: "3123700736" },
            { nama: "SHIDIQ PASYA", nisn: "3155401328" },
            { nama: "Shofa Widayanti", nisn: "3128753535" },
            { nama: "SINDI AGISTIN", nisn: "3135845041" },
            { nama: "Sinta Cahya Purnama", nisn: "3139323225" },
            { nama: "SINTYA WAFFA", nisn: "3174501501" },
            { nama: "Siti Nuraeni", nisn: "3144371754" },
            { nama: "Siti Saidah Ramadhani", nisn: "3127699756" },
            { nama: "SONY KURNIAWAN", nisn: "3158559945" },
            { nama: "SULTHAN ASYAM NURFADILAH", nisn: "3186123976" },
            { nama: "SURYA SAPUTRA", nisn: "3179890681" },
            { nama: "SYAFIQA ARSYILA GAUTSI", nisn: "3161830250" },
            { nama: "Syakila Nur Rahma", nisn: "3139302127" },
            { nama: "Syiffa Nuralipah", nisn: "3134563872" },
            { nama: "TEGUH HIMAWAN", nisn: "3149976783" },
            { nama: "Tendi Nurpalah", nisn: "3135345904" },
            { nama: "Tesa Rosita", nisn: "3139439213" },
            { nama: "TIA HERMAWAN", nisn: "3142850959" },
            { nama: "Tiyara Syifa Hilmaya", nisn: "3136734539" },
            { nama: "VIONA NISSA", nisn: "3176798950" },
            { nama: "Wafi Khoerulmuna", nisn: "3154571742" },
            { nama: "WENDI", nisn: "3146542746" },
            { nama: "WISHA SAVANA ZAHRA", nisn: "3123704132" },
            { nama: "Wisnu Ramdhani", nisn: "3123548419" },
            { nama: "YOGA MAULANA", nisn: "3142502020" },
            { nama: "YUNDA NUROHMAH", nisn: "3151272637" }
        ];

        // Fungsi untuk memeriksa hasil
        function checkResult() {
            const inputName = document.getElementById('name-input').value.trim().toUpperCase();
            const resultSection = document.getElementById('result-section');
            const teaserSection = document.getElementById('teaser-section');
            const resultTable = document.getElementById('result-table');
            
            // Cari siswa berdasarkan nama
            const student = students.find(s => s.nama.toUpperCase() === inputName);
            
            if (student) {
                // Tampilkan hasil
                resultTable.innerHTML = `
                    <tr>
                        <td>${student.nama}</td>
                        <td>${student.nisn}</td>
                        <td class="status">LULUS</td>
                    </tr>
                `;
                
                teaserSection.style.display = 'none';
                resultSection.style.display = 'block';
            } else {
                alert('Nama tidak ditemukan. Pastikan Anda memasukkan nama lengkap dengan benar.');
            }
        }
        
        // Fungsi untuk tombol-tombol aksi
        function showCelebrate() {
            hideAllMessages();
            const messages = [
                "🎉 Yeay! Kamu lulus! 🎉",
                "🎊 Selamat! Kamu berhasil! 🎊",
                "🥳 Horeee! Lulus dengan gemilang! 🥳"
            ];
            const randomMessage = messages[Math.floor(Math.random() * messages.length)];
            document.getElementById('celebrate-message').textContent = randomMessage;
            document.getElementById('celebrate-message').style.display = 'block';
        }
        
        function showMotivation() {
            hideAllMessages();
            const messages = [
                "Terus semangat dan capai cita-citamu!",
                "Langkah pertama telah berhasil, teruskan perjuanganmu!",
                "Kamu hebat! Teruslah belajar dan berkembang!",
                "Kelulusan ini adalah awal dari petualangan baru!"
            ];
            const randomMessage = messages[Math.floor(Math.random() * messages.length)];
            document.getElementById('motivation-message').textContent = randomMessage;
            document.getElementById('motivation-message').style.display = 'block';
        }
        
        function showSurprise() {
            hideAllMessages();
            const messages = [
                "Dapat hadiah es krim digital! 🍦🎉",
                "Kamu dapat 1 tiket gratis ke dunia impian! ✨",
                "Selamat! Kamu mendapatkan bintang penghargaan! ⭐",
                "Hadiah virtual: 1 pelukan hangat dari kami! 🤗"
            ];
            const randomMessage = messages[Math.floor(Math.random() * messages.length)];
            document.getElementById('surprise-message').textContent = randomMessage;
            document.getElementById('surprise-message').style.display = 'block';
        }
        
        function hideAllMessages() {
            document.getElementById('celebrate-message').style.display = 'none';
            document.getElementById('motivation-message').style.display = 'none';
            document.getElementById('surprise-message').style.display = 'none';
        }
        
        // Tambahkan event listener untuk input (bisa tekan Enter)
        document.getElementById('name-input').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                checkResult();
            }
        });
    </script>
</body>
</html>
