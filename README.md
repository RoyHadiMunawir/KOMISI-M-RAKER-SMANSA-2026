# KOMISI-M-RAKER-SMANSA-2026
silahkan memberikan saran dan solusi
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikasi Formulir & Inventaris Data OSIS</title>
    <style>
        /* Desain Modern Klasik (Monokrom Pilihan) */
        :root {
            --bg-color: #f4f5f7;
            --card-bg: #ffffff;
            --text-main: #222222;
            --text-muted: #666666;
            --border-color: #dddddd;
            --accent-black: #1a1a1a;
            --accent-hover: #444444;
            --accent-light: #f8f9fa;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
            margin: 0;
            padding: 30px 15px;
        }

        .container {
            max-width: 850px;
            margin: 0 auto;
            background: var(--card-bg);
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
            border: 1px solid rgba(0, 0, 0, 0.05);
        }

        /* Navigasi Tab Modern */
        .nav-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 10px;
        }

        .tab-btn {
            background: none;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 15px;
            font-weight: 600;
            color: var(--text-muted);
            transition: all 0.2s ease;
            border-radius: 4px;
        }

        .tab-btn:hover {
            color: var(--accent-black);
            background-color: var(--accent-light);
        }

        .tab-btn.active {
            background-color: var(--accent-black);
            color: #fff;
        }

        /* Konten */
        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .header-section {
            position: relative;
            margin-bottom: 30px;
        }

        h2 {
            font-size: 22px;
            font-weight: 700;
            color: var(--accent-black);
            margin: 0 0 8px 0;
            letter-spacing: -0.5px;
        }

        .desc-text {
            font-size: 14px;
            color: var(--text-muted);
            margin: 0;
        }

        /* Tombol Pengaturan */
        .settings-btn {
            position: absolute;
            right: 0;
            top: 0;
            background: var(--accent-light);
            border: 1px solid var(--border-color);
            padding: 6px 12px;
            font-size: 12px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 4px;
            transition: all 0.2s;
        }

        .settings-btn:hover {
            background: #eee;
            border-color: #bbb;
        }

        /* Form & Input */
        .form-group {
            margin-bottom: 25px;
        }

        label {
            display: block;
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 14px;
            color: var(--accent-black);
        }

        input[type="text"], textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            background-color: #fff;
            box-sizing: border-box;
            font-size: 14px;
            font-family: inherit;
            transition: all 0.2s ease;
        }

        textarea {
            resize: vertical;
            height: 110px;
        }

        input:focus, textarea:focus {
            border-color: var(--accent-black);
            box-shadow: 0 0 0 3px rgba(0, 0, 0, 0.05);
            outline: none;
        }

        /* Tombol Utama */
        .btn {
            background: var(--accent-black);
            color: #fff;
            border: none;
            padding: 12px 24px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            font-size: 14px;
            transition: background 0.2s;
        }

        .btn:hover {
            background: var(--accent-hover);
        }

        /* Modal / Panel Edit Pertanyaan */
        .edit-panel {
            display: none;
            background: var(--accent-light);
            border: 1px solid var(--border-color);
            padding: 20px;
            border-radius: 6px;
            margin-bottom: 30px;
        }

        /* Tabel Inventaris Data */
        .table-container {
            overflow-x: auto;
            margin-top: 20px;
            border-radius: 6px;
            border: 1px solid var(--border-color);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
            background: #fff;
        }

        th, td {
            padding: 14px 16px;
            text-align: left;
            vertical-align: top;
            border-bottom: 1px solid var(--border-color);
        }

        th {
            background-color: var(--accent-light);
            font-weight: 600;
            color: var(--accent-black);
            border-bottom: 2px solid var(--border-color);
        }

        tr:last-child td {
            border-bottom: none;
        }

        tr:hover td {
            background-color: rgba(0,0,0,0.01);
        }

        .no-data {
            text-align: center;
            color: var(--text-muted);
            font-style: italic;
            padding: 30px;
        }

        .clear-btn {
            background: transparent;
            color: #cc0000;
            border: 1px solid #cc0000;
            padding: 8px 16px;
            font-size: 13px;
            font-weight: 600;
            border-radius: 6px;
            margin-top: 20px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .clear-btn:hover {
            background: #fee;
        }
    </style>
</head>
<body>

<div class="container">
    <!-- Menu Navigasi -->
    <div class="nav-tabs">
        <button class="tab-btn active" onclick="switchTab('form-tab')">Formulir Pengisian</button>
        <button class="tab-btn" onclick="switchTab('data-tab')">Inventaris Data Tanggapan</button>
    </div>

    <!-- TAB 1: FORMULIR -->
    <div id="form-tab" class="tab-content active">
        <div class="header-section">
            <h2 id="lbl-title">Formulir Evaluasi & Tanggapan</h2>
            <p id="lbl-desc" class="desc-text">Silakan isi evaluasi pengelolaan ekstrakurikuler majelis pembimbing OSIS di bawah ini.</p>
            <button class="settings-btn" onclick="toggleEditPanel()">⚙️ Edit Teks Pertanyaan</button>
        </div>

        <!-- PANEL EDIT TEKS PERTANYAAN (TERSEMBUNYI SECARA DEFAULT) -->
        <div id="editPanel" class="edit-panel">
            <h3 style="margin-top:0; font-size:16px;">Pengaturan Teks Formulir</h3>
            <div class="form-group">
                <label>Judul Formulir:</label>
                <input type="text" id="edit-title">
            </div>
            <div class="form-group">
                <label>Deskripsi/Petunjuk:</label>
                <input type="text" id="edit-desc">
            </div>
            <div class="form-group">
                <label>Pertanyaan 1:</label>
                <input type="text" id="edit-q1">
            </div>
            <div class="form-group">
                <label>Pertanyaan 2:</label>
                <input type="text" id="edit-q2">
            </div>
            <button class="btn" onclick="simpanKonfigurasiTeks()">Terapkan Perubahan</button>
            <button class="btn" style="background:#ccc; color:#333;" onclick="toggleEditPanel()">Batal</button>
        </div>
        
        <!-- FORM UTAMA -->
        <form id="osisForm" onsubmit="simpanData(event)">
            <div class="form-group">
                <label for="nama">Nama Pengisi / Jabatan:</label>
                <input type="text" id="nama" required placeholder="Contoh: Ahmad Fauzi - Pembina Pramuka">
            </div>

            <div class="form-group">
                <label id="lbl-q1" for="perbaikan">1. Apa hal yang perlu diperbaiki dalam pengelolaan ekstrakurikuler majelis pembimbing OSIS?</label>
                <textarea id="perbaikan" required placeholder="Tuliskan kendala atau kekurangan manajemen..."></textarea>
            </div>

            <div class="form-group">
                <label id="lbl-q2" for="solusi">2. Apa solusi yang bisa dikemukakan?</label>
                <textarea id="solusi" required placeholder="Tuliskan saran rekomendasi atau jalan keluar konkret..."></textarea>
            </div>

            <button type="submit" class="btn">Simpan Tanggapan</button>
        </form>
    </div>

    <!-- TAB 2: INVENTARISASI DATA -->
    <div id="data-tab" class="tab-content">
        <div class="header-section">
            <h2>Inventaris Data Tanggapan</h2>
            <p class="desc-text">Berikut adalah daftar tanggapan terkumpul yang disimpan di database lokal browser Anda.</p>
        </div>

        <div class="table-container">
            <table id="dataTable">
                <thead>
                    <tr>
                        <th style="width: 5%;">No</th>
                        <th style="width: 25%;">Nama / Jabatan</th>
                        <th id="th-q1" style="width: 35%;">Hal yang Perlu Diperbaiki</th>
                        <th id="th-q2" style="width: 35%;">Solusi yang Dikemukakan</th>
                    </tr>
                </thead>
                <tbody id="dataBody">
                    <!-- Data otomatis diisi JS -->
                </tbody>
            </table>
        </div>
        
        <button class="clear-btn" onclick="hapusSemuaData()">Hapus Semua Inventaris Data</button>
    </div>
</div>

<script>
    // Konfigurasi Default Teks Formulir
    const defaultText = {
        title: "Formulir Evaluasi & Tanggapan",
        desc: "Silakan isi evaluasi pengelolaan ekstrakurikuler majelis pembimbing OSIS di bawah ini.",
        q1: "1. Apa hal yang perlu diperbaiki dalam pengelolaan ekstrakurikuler majelis pembimbing OSIS?",
        q2: "2. Apa solusi yang bisa dikemukakan?"
    };

    // Load konfigurasi teks saat aplikasi dibuka
    function loadTeksFormulir() {
        const customText = JSON.parse(localStorage.getItem('customFormText')) || defaultText;
        
        document.getElementById('lbl-title').innerText = customText.title;
        document.getElementById('lbl-desc').innerText = customText.desc;
        document.getElementById('lbl-q1').innerText = customText.q1;
        document.getElementById('lbl-q2').innerText = customText.q2;
        
        // Update juga header tabel di halaman data
        document.getElementById('th-q1').innerText = customText.q1.replace(/^\d+\.\s*/, '');
        document.getElementById('th-q2').innerText = customText.q2.replace(/^\d+\.\s*/, '');

        // Isi nilai ke panel editor teks
        document.getElementById('edit-title').value = customText.title;
        document.getElementById('edit-desc').value = customText.desc;
        document.getElementById('edit-q1').value = customText.q1;
        document.getElementById('edit-q2').value = customText.q2;
    }

    // Fungsi buka/tutup panel edit pertanyaan
    function toggleEditPanel() {
        const panel = document.getElementById('editPanel');
        panel.style.display = (panel.style.display === 'block') ? 'none' : 'block';
    }

    // Fungsi menyimpan teks baru yang diedit
    function simpanKonfigurasiTeks() {
        const teksBaru = {
            title: document.getElementById('edit-title').value,
            desc: document.getElementById('edit-desc').value,
            q1: document.getElementById('edit-q1').value,
            q2: document.getElementById('edit-q2').value
        };
        localStorage.setItem('customFormText', JSON.stringify(teksBaru));
        loadTeksFormulir();
        toggleEditPanel();
        alert('Teks pertanyaan berhasil diperbarui!');
    }

    // Fungsi navigasi halaman/tab
    function switchTab(tabId) {
        document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));
        document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
        
        document.getElementById(tabId).classList.add('active');
        event.target.classList.add('active');
        
        if(tabId === 'data-tab') {
            tampilkanData();
        }
    }

    // Fungsi simpan data tanggapan
    function simpanData(event) {
        event.preventDefault();
        
        const nama = document.getElementById('nama').value;
        const perbaikan = document.getElementById('perbaikan').value;
        const solusi = document.getElementById('solusi').value;
        
        const dataBaru = { nama, perbaikan, solusi };
        let inventarisOSIS = JSON.parse(localStorage.getItem('inventarisOSIS')) || [];
        inventarisOSIS.push(dataBaru);
        localStorage.setItem('inventarisOSIS', JSON.stringify(inventarisOSIS));
        
        document.getElementById('osisForm').reset();
        alert('Tanggapan berhasil disimpan!');
        
        // Alihkan ke halaman inventaris data
        switchTab('data-tab');
        const btns = document.querySelectorAll('.tab-btn');
        btns[0].classList.remove('active');
        btns[1].classList.add('active');
    }

    // Tampilkan data di tabel
    function tampilkanData() {
        loadTeksFormulir(); // Pastikan judul kolom tabel sesuai teks terbaru
        const dataBody = document.getElementById('dataBody');
        dataBody.innerHTML = '';
        
        let inventarisOSIS = JSON.parse(localStorage.getItem('inventarisOSIS')) || [];
        
        if (inventarisOSIS.length === 0) {
            dataBody.innerHTML = `<tr><td colspan="4" class="no-data">Belum ada data tanggapan yang disimpan.</td></tr>`;
            return;
        }
        
        inventarisOSIS.forEach((item, index) => {
            const row = `<tr>
                <td>${index + 1}</td>
                <td><strong>${escapeHtml(item.nama)}</strong></td>
                <td>${escapeHtml(item.perbaikan).replace(/\n/g, '<br>')}</td>
                <td>${escapeHtml(item.solusi).replace(/\n/g, '<br>')}</td>
            </tr>`;
            dataBody.innerHTML += row;
        });
    }

    function escapeHtml(text) {
        return text.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/"/g, "&quot;").replace(/'/g, "&#039;");
    }

    function hapusSemuaData() {
        if(confirm('Hapus seluruh data inventaris? Tindakan ini tidak bisa dibatalkan.')) {
            localStorage.removeItem('inventarisOSIS');
            tampilkanData();
        }
    }

    // Inisialisasi awal saat file dibuka
    window.onload = loadTeksFormulir;
</script>

</body>
</html>
