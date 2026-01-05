<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kasir - Jennaira Group</title>
    
    <style>
        /* RESET */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Arial, sans-serif;
        }
        
        body {
            background: #f5f7fa;
            color: #333;
        }
        
        /* HEADER - FIXED TAPI TIDAK MENUTUP MENU */
        .app-header {
            background: linear-gradient(135deg, #2c3e50 0%, #3498db 100%);
            color: white;
            padding: 20px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        /* NAVIGASI - STICKY (SCROLL BERSAMA TAPI TETAP DI ATAS) */
        .app-nav {
            background: #34495e;
            padding: 15px;
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            position: sticky;
            top: 0;
            z-index: 99;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        /* KONTEN UTAMA */
        .app-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* TAB BUTTON - PERBAIKAN */
        .nav-tab {
            background: #2c3e50;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
            min-width: 120px;
            justify-content: center;
        }
        
        .nav-tab:hover {
            background: #3498db;
            transform: translateY(-2px);
        }
        
        .nav-tab.active {
            background: #27ae60;
            box-shadow: 0 4px 8px rgba(39, 174, 96, 0.3);
        }
        
        /* TAB CONTENT */
        .tab-content {
            display: none;
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 8px 30px rgba(0,0,0,0.08);
            margin-bottom: 30px;
            margin-top: 20px;
            animation: fadeIn 0.5s;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* SEARCH BAR */
        .search-container {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 2px solid #e0e0e0;
        }
        
        .search-box {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        
        .search-input {
            flex: 1;
            padding: 14px 20px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        .search-input:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
        }
        
        /* PRODUCT GRID */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 25px;
            margin-top: 25px;
        }
        
        .product-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            border: 2px solid #e0e0e0;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }
        
        .product-card:hover {
            border-color: #3498db;
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.15);
        }
        
        /* BUTTONS */
        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 15px;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            margin: 5px;
        }
        
        .btn-primary {
            background: #3498db;
            color: white;
        }
        
        .btn-success {
            background: #27ae60;
            color: white;
        }
        
        .btn-csv {
            background: #217346;
            color: white;
        }
        
        /* ALERT */
        .alert {
            padding: 18px 25px;
            border-radius: 10px;
            margin-bottom: 25px;
            display: none;
            animation: slideIn 0.3s;
        }
        
        .alert-success {
            background: #d4edda;
            color: #155724;
            border: 2px solid #c3e6cb;
        }
        
        @keyframes slideIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* RESPONSIVE */
        @media (max-width: 768px) {
            .app-nav {
                flex-direction: column;
                align-items: stretch;
            }
            
            .nav-tab {
                width: 100%;
            }
            
            .products-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }
        }
    </style>
</head>
<body>
    <!-- HEADER -->
    <header class="app-header">
        <h1>💰 KASIR JENNAIRA GROUP</h1>
        <p>Sistem Kasir Lengkap dengan Export Laporan</p>
    </header>
    
    <!-- NAVIGASI -->
    <nav class="app-nav">
        <button class="nav-tab active" onclick="showTab('dashboard')">
            📊 Dashboard
        </button>
        <button class="nav-tab" onclick="showTab('kasir')">
            💼 Kasir
        </button>
        <button class="nav-tab" onclick="showTab('produk')">
            📦 Produk
        </button>
        <button class="nav-tab" onclick="showTab('laporan')">
            📈 Laporan
        </button>
        <button class="nav-tab" onclick="showTab('export')">
            📥 Export
        </button>
    </nav>
    
    <!-- KONTEN UTAMA -->
    <main class="app-content">
        <!-- ALERT -->
        <div id="alert" class="alert"></div>
        
        <!-- DASHBOARD -->
        <div id="dashboard" class="tab-content active">
            <h2>📊 Dashboard</h2>
            <p>Selamat datang di aplikasi kasir Jennaira Group!</p>
        </div>
        
        <!-- KASIR -->
        <div id="kasir" class="tab-content">
            <h2>💼 Kasir</h2>
            
            <!-- SEARCH BAR -->
            <div class="search-container">
                <h3>🔍 Cari Produk</h3>
                <div class="search-box">
                    <input type="text" id="productSearch" class="search-input" placeholder="Ketik nama produk...">
                    <button class="btn btn-primary">
                        🔍 Search
                    </button>
                </div>
            </div>
            
            <!-- PRODUK -->
            <div class="products-grid">
                <div class="product-card">
                    <div style="font-weight: bold; color: #2c3e50;">Beras 5kg</div>
                    <div style="color: #27ae60; font-weight: bold; margin: 10px 0;">Rp 60.000</div>
                    <div style="font-size: 12px; color: #7f8c8d;">Sembako • kg</div>
                </div>
                
                <div class="product-card">
                    <div style="font-weight: bold; color: #2c3e50;">Minyak Goreng 2L</div>
                    <div style="color: #27ae60; font-weight: bold; margin: 10px 0;">Rp 35.000</div>
                    <div style="font-size: 12px; color: #7f8c8d;">Sembako • botol</div>
                </div>
            </div>
        </div>
        
        <!-- PRODUK -->
        <div id="produk" class="tab-content">
            <h2>📦 Manajemen Produk</h2>
            <p>Fitur manajemen produk akan muncul di sini.</p>
        </div>
        
        <!-- LAPORAN -->
        <div id="laporan" class="tab-content">
            <h2>📈 Laporan Penjualan</h2>
            <button class="btn btn-csv">📥 Export CSV</button>
            <button class="btn btn-success">📊 Export Excel</button>
        </div>
        
        <!-- EXPORT -->
        <div id="export" class="tab-content">
            <h2>📥 Export Data</h2>
            <p>Export data dalam format CSV atau Excel.</p>
        </div>
    </main>

    <!-- SCRIPT SEDERHANA -->
    <script>
        // ==================== FUNGSI NAVIGASI ====================
        function showTab(tabId) {
            // Update active button
            document.querySelectorAll('.nav-tab').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // Show selected tab
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            document.getElementById(tabId).classList.add('active');
            
            // Scroll ke atas tab
            document.getElementById(tabId).scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
        
        // ==================== INISIALISASI ====================
        document.addEventListener('DOMContentLoaded', function() {
            console.log('Aplikasi Kasir siap digunakan!');
            showAlert('success', 'Selamat datang di Kasir Jennaira Group!');
        });
        
        function showAlert(type, message) {
            const alertDiv = document.getElementById('alert');
            alertDiv.textContent = message;
            alertDiv.className = `alert alert-${type}`;
            alertDiv.style.display = 'block';
            
            setTimeout(() => {
                alertDiv.style.display = 'none';
            }, 3000);
        }
    </script>
</body>
</html>
