<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>sellertopup.id — Digital Gate & Distribution Platform</title>
    <style>
        :root {
            --bg-main: #050811;
            --bg-surface: #0d1527;
            --bg-input: #152038;
            --primary: #1d4ed8;
            --primary-light: #3b82f6;
            --accent: #06b6d4;
            --success: #10b981;
            --text-white: #f8fafc;
            --text-muted: #64748b;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', 'Segoe UI', Roboto, sans-serif;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-white);
            padding: 20px 12px;
        }

        .wrapper {
            max-width: 680px;
            margin: 0 auto;
        }

        /* Header System */
        header {
            text-align: center;
            padding: 35px 0 25px 0;
        }

        .badge-verified {
            background: rgba(6, 182, 212, 0.1);
            color: var(--accent);
            padding: 5px 14px;
            border-radius: 30px;
            font-size: 0.75rem;
            font-weight: 700;
            text-transform: uppercase;
            border: 1px solid rgba(6, 182, 212, 0.2);
            display: inline-block;
            margin-bottom: 12px;
        }

        header h1 {
            font-size: 2.3rem;
            font-weight: 800;
            letter-spacing: -0.03em;
            background: linear-gradient(135deg, #ffffff 50%, var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        header p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 4px;
        }

        /* Melonjong Card Panel */
        .panel-box {
            background-color: var(--bg-surface);
            border: 1px solid rgba(255, 255, 255, 0.03);
            border-radius: 28px; /* Karakter Melonjong */
            padding: 25px;
            margin-bottom: 20px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
        }

        .panel-title {
            font-size: 1.1rem;
            font-weight: 700;
            margin-bottom: 18px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .panel-title .badge-num {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            width: 26px;
            height: 26px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }

        /* Inputs */
        input[type="text"], select {
            width: 100%;
            padding: 16px;
            background-color: var(--bg-input);
            border: 2px solid transparent;
            border-radius: 18px; /* Melonjong */
            color: white;
            font-size: 0.95rem;
            font-weight: 600;
            outline: none;
            transition: all 0.3s;
            margin-bottom: 10px;
        }

        input[type="text"]:focus {
            border-color: var(--primary-light);
        }

        /* Diamond Grid (Modern & Murah) */
        .grid-catalog {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }

        @media(min-width: 480px) {
            .grid-catalog { grid-template-columns: repeat(3, 1fr); }
        }

        .item-card {
            background-color: var(--bg-input);
            border: 2px solid transparent;
            border-radius: 22px; /* Melonjong */
            padding: 18px 12px;
            text-align: center;
            cursor: pointer;
            transition: all 0.25s ease;
            position: relative;
            overflow: hidden;
        }

        .item-card:hover {
            border-color: rgba(6, 182, 212, 0.3);
            transform: translateY(-2px);
        }

        .item-card.selected {
            border-color: var(--primary-light);
            background: linear-gradient(180deg, var(--bg-input), rgba(59, 130, 246, 0.1));
        }

        .dm-name {
            font-size: 1.1rem;
            font-weight: 800;
            display: block;
        }

        .dm-price {
            font-size: 0.85rem;
            color: var(--accent);
            font-weight: 600;
            margin-top: 3px;
            display: block;
        }

        .bonus-tag {
            position: absolute;
            top: 0;
            right: 0;
            background: var(--success);
            color: #000;
            font-size: 0.65rem;
            font-weight: 800;
            padding: 3px 9px;
            border-bottom-left-radius: 12px;
        }

        /* Payment List */
        .grid-pay {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
        }

        .pay-card {
            background-color: var(--bg-input);
            border: 2px solid transparent;
            border-radius: 18px;
            padding: 16px;
            font-weight: 700;
            text-align: center;
            cursor: pointer;
            font-size: 0.9rem;
            transition: 0.2s;
        }

        .pay-card.selected {
            border-color: var(--success);
            background: rgba(16, 185, 129, 0.05);
        }

        /* Action Button */
        .btn-submit {
            width: 100%;
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            color: white;
            border: none;
            padding: 18px;
            font-size: 1.1rem;
            font-weight: 700;
            border-radius: 20px;
            cursor: pointer;
            box-shadow: 0 10px 20px rgba(59, 130, 246, 0.25);
            transition: 0.3s;
        }

        .btn-submit:hover {
            transform: translateY(-1px);
            opacity: 0.95;
        }

        /* MODERN POP-UP INVOICE (GAK LANGSUNG BARCODE / NO WA) */
        .invoice-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(5, 8, 17, 0.85);
            backdrop-filter: blur(8px);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .invoice-modal {
            background-color: var(--bg-surface);
            border: 2px solid var(--primary-light);
            width: 100%;
            max-width: 450px;
            border-radius: 28px;
            padding: 25px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.6);
            animation: slideUp 0.3s ease-out;
        }

        @keyframes slideUp {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .invoice-header {
            text-align: center;
            margin-bottom: 20px;
            border-bottom: 1px dashed rgba(255,255,255,0.1);
            padding-bottom: 15px;
        }

        .invoice-header h3 { color: var(--success); font-size: 1.3rem; }
        .invoice-header p { font-size: 0.8rem; color: var(--text-muted); }

        .invoice-details {
            margin-bottom: 20px;
            font-size: 0.9rem;
        }

        .invoice-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
        }

        .invoice-row span:first-child { color: var(--text-muted); }
        .invoice-row span:last-child { font-weight: 600; }

        .payment-instruction {
            background: #fff;
            color: #000;
            padding: 15px;
            border-radius: 18px;
            text-align: center;
            margin-top: 15px;
        }
        
        .payment-instruction img {
            max-width: 180px;
            width: 100%;
            height: auto;
            margin: 10px auto 0 auto;
            display: block;
            border-radius: 8px;
        }

        .btn-close {
            width: 100%;
            background: var(--bg-input);
            color: var(--text-white);
            border: 1px solid rgba(255,255,255,0.1);
            padding: 12px;
            border-radius: 15px;
            margin-top: 15px;
            cursor: pointer;
            font-weight: 600;
        }

        /* Disclaimer Filter Sistem */
        .legal-text {
            font-size: 0.75rem;
            color: var(--text-muted);
            text-align: center;
            margin-top: 25px;
            line-height: 1.4;
        }

        footer {
            text-align: center;
            color: var(--text-muted);
            font-size: 0.8rem;
            margin: 30px 0 10px 0;
        }
    </style>
</head>
<body>

<div class="wrapper">
    
    <header>
        <span class="badge-verified">Automated Gateway System</span>
        <h1>sellertopup.id</h1>
        <p>Distributor Voucher Elektronik Aman & Terverifikasi</p>
    </header>

    <!-- STEP 1 -->
    <div class="panel-box">
        <div class="panel-title"><div class="badge-num">1</div> Verifikasi Akun</div>
        <input type="text" id="target-id" placeholder="Masukkan Player ID" autocomplete="off">
        <select id="target-zone">
            <option value="ID">Server Indonesia (ID)</option>
        </select>
    </div>

    <!-- STEP 2 -->
    <div class="panel-box">
        <div class="panel-title"><div class="badge-num">2</div> Nominal Layanan</div>
        <div class="grid-catalog">
            <div class="item-card" onclick="selectItem(this, '5 Diamond', 1000)">
                <span class="dm-name">5 DM</span><span class="dm-price">Rp 1.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '12 Diamond', 2000)">
                <span class="dm-name">12 DM</span><span class="dm-price">Rp 2.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '50 Diamond', 8000)">
                <span class="dm-name">50 DM</span><span class="dm-price">Rp 8.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '140 Diamond', 20000)">
                <span class="dm-name">140 DM</span><span class="dm-price">Rp 20.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '355 Diamond', 48000)">
                <span class="dm-name">355 DM</span><span class="dm-price">Rp 48.000</span>
            </div>
            <!-- Bonus Progresif Diatas 50k -->
            <div class="item-card" onclick="selectItem(this, '720 Diamond', 95000)">
                <div class="bonus-tag">+20 DM</div>
                <span class="dm-name">720 DM</span><span class="dm-price">Rp 95.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '1450 Diamond', 190000)">
                <div class="bonus-tag">+40 DM</div>
                <span class="dm-name">1450 DM</span><span class="dm-price">Rp 190.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '2180 Diamond', 280000)">
                <div class="bonus-tag">+60 DM</div>
                <span class="dm-name">2180 DM</span><span class="dm-price">Rp 280.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '3640 Diamond', 450000)">
                <div class="bonus-tag">+80 DM</div>
                <span class="dm-name">3640 DM</span><span class="dm-price">Rp 450.000</span>
            </div>
            <div class="item-card" onclick="selectItem(this, '4000 Diamond', 500000)">
                <div class="bonus-tag">+100 DM</div>
                <span class="dm-name">4000 DM</span><span class="dm-price">Rp 500.000</span>
            </div>
        </div>
    </div>

    <!-- STEP 3 -->
    <div class="panel-box">
        <div class="panel-title"><div class="badge-num">3</div> Metode Pembayaran</div>
        <div class="grid-pay">
            <div class="pay-card" onclick="selectPay(this, 'QRIS')">QRIS Otomatis</div>
            <div class="pay-card" onclick="selectPay(this, 'DANA')">DANA</div>
            <div class="pay-card" onclick="selectPay(this, 'GOPAY')">GoPay</div>
            <div class="pay-card" onclick="selectPay(this, 'OVO')">OVO</div>
        </div>
    </div>

    <button class="btn-submit" onclick="generateInvoice()">Proses Pembelian Instan</button>

    <div class="legal-text">
        <strong>Disclaimer Dagang:</strong> Platform ini bekerja sebagai penyedia voucher independen. Seluruh hak cipta game, logo, dan kekayaan intelektual murni milik developer game terkait. Transaksi diproses secara otomatis oleh sistem interkoneksi e-commerce terenkripsi.
    </div>

    <footer>
        &copy; 2026 sellertopup.id. All Rights Reserved.
    </footer>
</div>

<!-- POP-UP INVOICE OTOMATIS (TERSEMBUNYI DIAWAL) -->
<div class="invoice-overlay" id="invoiceOverlay">
    <div class="invoice-modal">
        <div class="invoice-header">
            <h3>INVOICE GENERATED</h3>
            <p id="inv-date">Sistem Otomatis Berhasil Membuat Tagihan</p>
        </div>
        <div class="invoice-details">
            <div class="invoice-row"><span>ID Tujuan:</span><span id="res-id">-</span></div>
            <div class="invoice-row"><span>Produk:</span><span id="res-prod">-</span></div>
            <div class="invoice-row"><span>Metode:</span><span id="res-method">-</span></div>
            <div class="invoice-row"><span>Biaya Sistem:</span><span>Rp 0</span></div>
            <div class="invoice-row" style="border-top: 1px solid rgba(255,255,255,0.1); padding-top: 8px; margin-top: 8px;">
                <span style="color:#fff; font-weight:bold;">Total Bayar:</span>
                <span id="res-total" style="color:var(--accent); font-weight:bold;">Rp 0</span>
            </div>
        </div>

        <!-- Wadah Instruksi & Gambar Barcode Dinamis -->
        <div class="payment-instruction" id="payInstruct">
            <!-- Tempat Barcode Muncul Otomatis Hanya jika invoice dibuat -->
        </div>

        <button class="btn-close" onclick="closeInvoice()">Tutup & Batalkan</button>
    </div>
</div>

<script>
    let activeProduct = "";
    let activePrice = 0;
    let activeMethod = "";

    function selectItem(el, name, price) {
        document.querySelectorAll('.item-card').forEach(c => c.classList.remove('selected'));
        el.classList.add('selected');
        activeProduct = name;
        activePrice = price;
    }

    function selectPay(el, method) {
        document.querySelectorAll('.pay-card').forEach(p => p.classList.remove('selected'));
        el.classList.add('active', 'selected');
        activeMethod = method;
    }

    function generateInvoice() {
        const uId = document.getElementById('target-id').value;
        if(!uId || uId.length < 4) { alert('Tolong masukkan ID Game secara benar!'); return; }
        if(!activeProduct) { alert('Silakan pilih jumlah Diamond terlebih dahulu!'); return; }
        if(!activeMethod) { alert('Silakan tentukan metode pembayaran!'); return; }

        // Pasang data ke Invoice Pop-up
        document.getElementById('res-id').innerText = uId;
        document.getElementById('res-prod').innerText = activeProduct;
        document.getElementById('res-method').innerText = activeMethod;
        document.getElementById('res-total').innerText = 'Rp ' + activePrice.toLocaleString('id-ID');

        const instructBox = document.getElementById('payInstruct');
        
        // Atur Konten Instruksi Bayar berdasarkan metode (Otomatis & Tersembunyi di awal)
        if(activeMethod === 'QRIS') {
            instructBox.style.background = '#fff';
            instructBox.style.color = '#000';
            instructBox.innerHTML = `
                <p style="font-weight:700; font-size:0.85rem;">Pindai QRIS Resmi di bawah ini:</p>
                <img src="https://images.weserv.nl/?url=ibb.co.com/4g0YgV32" alt="QRIS Code">
            `;
        } else {
            // E-Wallet (DANA/GOPAY/OVO) dibikin otomatis sistem simulasi nomor akun bisnis
            instructBox.style.background = 'var(--bg-input)';
            instructBox.style.color = '#fff';
            instructBox.innerHTML = `
                <p style="font-size:0.85rem; margin-bottom: 5px;">Silakan Transfer Manual / Selesaikan Ke Aplikasi <strong>${activeMethod}</strong> Anda</p>
                <p style="font-size:1.1rem; font-weight:800; color:var(--success);">081234567890</p>
                <p style="font-size:0.7rem; color:var(--text-muted); margin-top:5px;">A/N SELLER TOPUP ID SYSTEM</p>
            `;
        }

        // Tampilkan Pop-up overlay
        document.getElementById('invoiceOverlay').style.display = 'flex';
    }

    function closeInvoice() {
        document.getElementById('invoiceOverlay').style.display = 'none';
    }
</script>

</body>
</html>

