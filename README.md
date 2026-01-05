<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kasir - Jennaira Group</title>
    
    <!-- SIMPLE STYLE -->
    <style>
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
        
        /* HEADER TETAP DI ATAS */
        .app-header {
            background: linear-gradient(135deg, #2c3e50 0%, #3498db 100%);
            color: white;
            padding: 20px;
            text-align: center;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        /* NAVIGASI TIDAK IKUT SCROLL */
        .app-nav {
            background: #34495e;
            padding: 15px;
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            position: fixed;
            top: 80px; /* Sesuaikan dengan tinggi header */
            left: 0;
            width: 100%;
            z-index: 999;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        /* ISI KONTEN DIMULAI DI BAWAH NAVIGASI */
        .app-content {
            margin-top: 160px; /* Header + Nav height */
            padding: 20px;
            max-width: 1200px;
            margin-left: auto;
            margin-right: auto;
        }
        
        /* TAB BUTTON */
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
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
            margin-bottom: 30px;
            animation: fadeIn 0.5s;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* SEARCH BAR - BARU DITAMBAHKAN */
        .search-container {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 25px;
            border: 2px solid #e0e0e0;
        }
        
        .search-box {
            display: flex;
            gap: 10px;
            align-items: center;
        }
        
        .search-input {
            flex: 1;
            padding: 12px 20px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border 0.3s;
        }
        
        .search-input:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }
        
        .search-btn {
            padding: 12px 30px;
            background: #3498db;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s;
        }
        
        .search-btn:hover {
            background: #2980b9;
        }
        
        /* PRODUCT GRID */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .product-card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            border: 2px solid #e0e0e0;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }
        
        .product-card:hover {
            border-color: #3498db;
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        
        .product-name {
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 10px;
            font-size: 16px;
        }
        
        .product-price {
            color: #27ae60;
            font-weight: bold;
            font-size: 18px;
            margin-bottom: 8px;
        }
        
        .product-category {
            font-size: 12px;
            color: #7f8c8d;
            background: #f8f9fa;
            padding: 3px 8px;
            border-radius: 10px;
            display: inline-block;
        }
        
        /* STATS */
        .stats-grid {
            display:
