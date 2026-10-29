<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kafe Senja - Nikmati Kopi dalam Kehangatan Senja</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Poppins -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        coffee: {
                            50: '#fdf8f6',
                            100: '#f2e8e5',
                            200: '#e8d5ce',
                            300: '#cca89a',
                            400: '#b88572',
                            500: '#9e5a42',
                            600: '#84422e',
                            700: '#683323',
                            800: '#4e281b',
                            900: '#341c14',
                            950: '#1e0e0a',
                        },
                        amber: {
                            500: '#f59e0b',
                            600: '#d97706',
                        }
                    },
                    fontFamily: {
                        sans: ['Poppins', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #fdf8f6;
            color: #341c14;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f2e8e5;
        }
        ::-webkit-scrollbar-thumb {
            background: #b88572;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #84422e;
        }

        /* Menu Card Hover Effect */
        .menu-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .menu-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 12px 24px -10px rgba(132, 66, 46, 0.25);
        }

        /* Wheel Pointer Arrow Animation */
        @keyframes pulse-pointer {
            0%, 100% { transform: translateX(-50%) scale(1); }
            50% { transform: translateX(-50%) scale(1.1); }
        }
        .pointer-anim {
            animation: pulse-pointer 1.5s infinite;
        }

        /* Toast Animation */
        .toast-enter {
            transform: translateY(100%);
            opacity: 0;
        }
        .toast-show {
            transform: translateY(0);
            opacity: 1;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between antialiased selection:bg-coffee-500 selection:text-white">

    <!-- ==================== HEADER & NAVBAR ==================== -->
    <header class="sticky top-0 z-40 bg-coffee-900/95 backdrop-blur-md text-white shadow-lg border-b border-coffee-800 transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <!-- Logo -->
                <a href="#beranda" class="flex items-center space-x-3 group">
                    <div class="w-10 h-10 rounded-full bg-amber-500 flex items-center justify-center text-coffee-950 font-bold text-xl shadow-md group-hover:rotate-12 transition-transform">
                        <i class="fa-solid fa-mug-hot"></i>
                    </div>
                    <span class="font-bold text-2xl tracking-wide text-amber-100 group-hover:text-amber-400 transition-colors">Kafe<span class="text-amber-500">Senja</span></span>
                </a>

                <!-- Desktop Navigation -->
                <nav class="hidden md:flex items-center space-x-8 font-medium">
                    <a href="#beranda" class="hover:text-amber-400 transition-colors py-2">Beranda</a>
                    <a href="#menu" class="hover:text-amber-400 transition-colors py-2">Menu</a>
                    <a href="#pesanan-saya" class="hover:text-amber-400 transition-colors py-2 flex items-center gap-1">
                        Pesanan Saya
                    </a>
                    <a href="#tentang" class="hover:text-amber-400 transition-colors py-2">Tentang Kami</a>
                </nav>

                <!-- Actions: Cart Button & Mobile Menu Toggle -->
                <div class="flex items-center space-x-4">
                    <button id="cartBtn" class="relative bg-amber-500 hover:bg-amber-600 text-coffee-950 p-3 rounded-full font-semibold transition-transform active:scale-95 shadow-md flex items-center justify-center">
                        <i class="fa-solid fa-cart-shopping text-lg"></i>
                        <span id="cartCounter" class="absolute -top-1 -right-1 bg-red-600 text-white text-xs w-5 h-5 rounded-full flex items-center justify-center font-bold border-2 border-coffee-900 hidden">0</span>
                    </button>

                    <button id="mobileMenuBtn" class="md:hidden text-2xl text-amber-100 hover:text-amber-400 focus:outline-none">
                        <i class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Navigation Menu -->
        <div id="mobileMenu" class="hidden md:hidden bg-coffee-950 border-b border-coffee-800 px-4 pt-2 pb-4 space-y-2">
            <a href="#beranda" class="block py-2 text-amber-100 hover:text-amber-400 border-b border-coffee-800">Beranda</a>
            <a href="#menu" class="block py-2 text-amber-100 hover:text-amber-400 border-b border-coffee-800">Menu</a>
            <a href="#pesanan-saya" class="block py-2 text-amber-100 hover:text-amber-400 border-b border-coffee-800">Pesanan Saya</a>
            <a href="#tentang" class="block py-2 text-amber-100 hover:text-amber-400">Tentang Kami</a>
        </div>
    </header>

    <!-- ==================== HERO SECTION ==================== -->
    <section id="beranda" class="relative bg-coffee-950 text-white py-24 md:py-32 overflow-hidden flex items-center min-h-[85vh]">
        <div class="absolute inset-0 z-0 opacity-30 bg-cover bg-center" style="background-image: url('https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?q=80&w=1600&auto=format&fit=crop');"></div>
        <div class="absolute inset-0 bg-gradient-to-r from-coffee-950 via-coffee-950/80 to-transparent z-10"></div>
        
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-20 grid md:grid-cols-2 gap-12 items-center">
            <div class="space-y-6 text-center md:text-left">
                <span class="inline-block px-4 py-1.5 rounded-full bg-amber-500/20 text-amber-400 border border-amber-500/30 text-sm font-semibold tracking-wide">
                    ☕ Kehangatan Dalam Setiap Seduhan
                </span>
                <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold leading-tight tracking-tight text-white">
                    Satu Cangkir Kopi, <br><span class="text-amber-500">Sejuta Cerita Senja</span>
                </h1>
                <p class="text-coffee-200 text-base sm:text-lg max-w-xl mx-auto md:mx-0 font-light leading-relaxed">
                    Rasakan perpaduan sempurna biji kopi pilihan nusantara dengan racikan racikan barista terbaik. Tempat terbaik untuk bersantai dan melupakan sejenak penat seharian.
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start pt-4">
                    <a href="#menu" class="bg-amber-500 hover:bg-amber-600 text-coffee-950 font-bold px-8 py-4 rounded-xl shadow-lg transition-all transform hover:-translate-y-1 text-center">
                        Lihat Menu Kami
                    </a>
                    <a href="#tentang" class="border border-coffee-400 hover:border-amber-400 hover:text-amber-400 text-coffee-100 font-semibold px-8 py-4 rounded-xl transition-all text-center">
                        Tentang Kami
                    </a>
                </div>
            </div>
            
            <div class="hidden md:flex justify-center relative">
                <div class="relative w-80 h-80 rounded-full border-4 border-amber-500/30 p-4 animate-pulse">
                    <img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?q=80&w=600&auto=format&fit=crop" alt="Coffee Cup" class="w-full h-full object-cover rounded-full shadow-2xl">
                </div>
            </div>
        </div>
    </section>

    <!-- ==================== MENU SECTION ==================== -->
    <section id="menu" class="py-20 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-2xl mx-auto mb-12">
            <h2 class="text-3xl sm:text-4xl font-bold text-coffee-900 mb-3">Menu Spesial Senja</h2>
            <p class="text-coffee-600">Pilihan hidangan berkualitas yang disiapkan khusus untuk menemani waktu luang Anda.</p>
            
            <!-- Category Filter Buttons -->
            <div class="flex flex-wrap justify-center gap-2 sm:gap-3 mt-8" id="categoryFilters">
                <button data-category="all" class="filter-btn active bg-coffee-800 text-white px-5 py-2 rounded-full font-medium text-sm transition-all shadow-sm">Semua</button>
                <button data-category="kopi" class="filter-btn bg-white text-coffee-800 hover:bg-coffee-100 border border-coffee-200 px-5 py-2 rounded-full font-medium text-sm transition-all">Kopi</button>
                <button data-category="non-kopi" class="filter-btn bg-white text-coffee-800 hover:bg-coffee-100 border border-coffee-200 px-5 py-2 rounded-full font-medium text-sm transition-all">Non-Kopi</button>
                <button data-category="makanan" class="filter-btn bg-white text-coffee-800 hover:bg-coffee-100 border border-coffee-200 px-5 py-2 rounded-full font-medium text-sm transition-all">Makanan</button>
            </div>
        </div>

        <!-- Menu Grid Container -->
        <div id="menuContainer" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
            <!-- Menu items will be dynamically injected via JavaScript -->
        </div>
    </section>

    <!-- ==================== PESANAN SAYA (RIWAYAT) SECTION ==================== -->
    <section id="pesanan-saya" class="py-16 bg-coffee-100/60 border-y border-coffee-200">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row md:items-center justify-between mb-8 gap-4">
                <div>
                    <h2 class="text-3xl font-bold text-coffee-900">Riwayat Pesanan Saya</h2>
                    <p class="text-coffee-600 text-sm mt-1">Daftar transaksi dan status pesanan Anda di Kafe Senja.</p>
                </div>
                <button id="clearHistoryBtn" class="text-xs text-red-600 hover:text-red-800 underline font-medium self-start md:self-auto hidden">
                    <i class="fa-solid fa-trash mr-1"></i> Bersihkan Riwayat
                </button>
            </div>

            <!-- Orders Container -->
            <div id="ordersContainer" class="space-y-4">
                <!-- Orders injected dynamically -->
            </div>
        </div>
    </section>

    <!-- ==================== TENTANG KAMI SECTION ==================== -->
    <section id="tentang" class="py-20 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-2 gap-12 items-center">
            <div class="relative">
                <img src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?q=80&w=800&auto=format&fit=crop" alt="Suasana Kafe Senja" class="rounded-2xl shadow-xl w-full object-cover h-96">
                <div class="absolute -bottom-6 -right-6 bg-amber-500 text-coffee-950 p-6 rounded-2xl shadow-lg hidden sm:block">
                    <p class="text-3xl font-extrabold">4.9/5.0</p>
                    <p class="text-xs font-semibold uppercase tracking-wider mt-1">Rating Pelanggan</p>
                </div>
            </div>
            <div class="space-y-6">
                <span class="text-amber-600 font-bold uppercase tracking-wider text-xs">Cerita Kami</span>
                <h2 class="text-3xl sm:text-4xl font-bold text-coffee-900">Rumah Kedua Bagi Para Pecinta Kopi & Ketenangan</h2>
                <p class="text-coffee-700 leading-relaxed">
                    Didirikan pada tahun 2021, Kafe Senja hadir dari keinginan sederhana: menyediakan tempat nyaman di mana waktu berjalan lebih lambat dan percakapan mengalir lebih dalam.
                </p>
                <p class="text-coffee-700 leading-relaxed">
                    Setiap biji kopi disangrai secara cermat oleh barista berpengalaman kami, dipadukan dengan suasana yang hangat dan musik akustik yang menenangkan.
                </p>
                <div class="grid grid-cols-2 gap-4 pt-4 border-t border-coffee-200">
                    <div>
                        <h4 class="font-bold text-coffee-900 text-lg">100% Nusantara</h4>
                        <p class="text-xs text-coffee-600">Biji kopi asli petani lokal</p>
                    </div>
                    <div>
                        <h4 class="font-bold text-coffee-900 text-lg">Fresh Baked</h4>
                        <p class="text-xs text-coffee-600">Makanan dibuat setiap hari</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ==================== FOOTER ==================== -->
    <footer class="bg-coffee-950 text-coffee-200 border-t border-coffee-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
                <!-- Brand Info -->
                <div class="space-y-4 md:col-span-1">
                    <div class="flex items-center space-x-3">
                        <div class="w-8 h-8 rounded-full bg-amber-500 flex items-center justify-center text-coffee-950 font-bold">
                            <i class="fa-solid fa-mug-hot"></i>
                        </div>
                        <span class="font-bold text-xl text-white">Kafe<span class="text-amber-500">Senja</span></span>
                    </div>
                    <p class="text-xs leading-relaxed text-coffee-400">
                        Menyajikan rasa terbaik dan kehangatan di setiap momen senja Anda.
                    </p>
                </div>

                <!-- Jam Operasional -->
                <div class="space-y-3">
                    <h3 class="text-white font-semibold text-sm tracking-wider uppercase">Jam Operasional</h3>
                    <ul class="text-xs space-y-2 text-coffee-300">
                        <li>Senin - Jumat: 10:00 - 22:00 WIB</li>
                        <li>Sabtu - Minggu: 09:00 - 23:00 WIB</li>
                        <li class="text-amber-400 pt-1">Buka Setiap Hari</li>
                    </ul>
                </div>

                <!-- Alamat & Kontak -->
                <div class="space-y-3">
                    <h3 class="text-white font-semibold text-sm tracking-wider uppercase">Lokasi Kami</h3>
                    <p class="text-xs text-coffee-300 leading-relaxed">
                        Jl. Senopati Senja No. 45, Kebayoran Baru, Jakarta Selatan
                    </p>
                    <p class="text-xs text-coffee-300">
                        <i class="fa-solid fa-phone text-amber-500 mr-2"></i>+62 812-3456-7890
                    </p>
                </div>

                <!-- Sosial Media -->
                <div class="space-y-3">
                    <h3 class="text-white font-semibold text-sm tracking-wider uppercase">Ikuti Kami</h3>
                    <div class="flex space-x-3">
                        <a href="#" class="w-9 h-9 rounded-full bg-coffee-900 border border-coffee-700 flex items-center justify-center hover:bg-amber-500 hover:text-coffee-950 hover:border-amber-500 transition-colors">
                            <i class="fa-brands fa-instagram"></i>
                        </a>
                        <a href="#" class="w-9 h-9 rounded-full bg-coffee-900 border border-coffee-700 flex items-center justify-center hover:bg-amber-500 hover:text-coffee-950 hover:border-amber-500 transition-colors">
                            <i class="fa-brands fa-tiktok"></i>
                        </a>
                        <a href="#" class="w-9 h-9 rounded-full bg-coffee-900 border border-coffee-700 flex items-center justify-center hover:bg-amber-500 hover:text-coffee-950 hover:border-amber-500 transition-colors">
                            <i class="fa-brands fa-whatsapp"></i>
                        </a>
                    </div>
                </div>
            </div>

            <div class="pt-8 border-t border-coffee-900 text-center text-xs text-coffee-500">
                <p>&copy; 2026 Kafe Senja. Seluruh hak cipta dilindungi undang-undang.</p>
            </div>
        </div>
    </footer>

    <!-- ==================== SIDEBAR KERANJANG ==================== -->
    <div id="cartDrawerOverlay" class="fixed inset-0 bg-black/60 z-50 opacity-0 pointer-events-none transition-opacity duration-300"></div>
    <div id="cartDrawer" class="fixed top-0 right-0 h-full w-full sm:w-96 bg-white z-50 shadow-2xl transform translate-x-full transition-transform duration-300 flex flex-col">
        <!-- Drawer Header -->
        <div class="p-5 bg-coffee-900 text-white flex items-center justify-between">
            <div class="flex items-center space-x-2">
                <i class="fa-solid fa-bag-shopping text-amber-500 text-xl"></i>
                <h3 class="font-bold text-lg">Keranjang Belanja</h3>
            </div>
            <button id="closeCartBtn" class="text-coffee-300 hover:text-white text-xl">
                <i class="fa-solid fa-xmark"></i>
            </button>
        </div>

        <!-- Cart Items List -->
        <div id="cartItemsContainer" class="flex-1 overflow-y-auto p-5 space-y-4 divide-y divide-coffee-100">
            <!-- Items injected via JavaScript -->
        </div>

        <!-- Drawer Footer / Summary -->
        <div class="p-5 bg-coffee-50 border-t border-coffee-200 space-y-4">
            <div class="flex justify-between items-center text-base font-bold text-coffee-900">
                <span>Total Belanja:</span>
                <span id="cartSubtotal" class="text-amber-600 text-xl">Rp 0</span>
            </div>
            <p class="text-xs text-coffee-500">Diskon akan dihitung saat memutar Roda Keberuntungan.</p>
            <button id="proceedToSpinBtn" disabled class="w-full bg-amber-500 hover:bg-amber-600 disabled:bg-coffee-200 disabled:text-coffee-400 disabled:cursor-not-allowed text-coffee-950 font-bold py-3 px-4 rounded-xl shadow-md transition-all flex items-center justify-center space-x-2">
                <span>Lanjutkan ke Spin Diskon</span>
                <i class="fa-solid fa-arrow-right"></i>
            </button>
        </div>
    </div>

    <!-- ==================== MODAL GIMMICK: SPIN THE WHEEL ==================== -->
    <div id="spinModal" class="fixed inset-0 bg-black/70 z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
        <div class="bg-white rounded-3xl max-w-md w-full p-6 text-center shadow-2xl relative border-4 border-amber-500 overflow-hidden transform scale-95 transition-transform duration-300" id="spinModalCard">
            <!-- Close Modal Button -->
            <button id="closeSpinModalBtn" class="absolute top-4 right-4 text-coffee-400 hover:text-coffee-900 text-xl z-10">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <span class="inline-block bg-amber-100 text-amber-800 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider mb-2">Gimmick Spesial!</span>
            <h3 class="text-2xl font-extrabold text-coffee-900 mb-1">Spin The Wheel Diskon</h3>
            <p class="text-xs text-coffee-600 mb-6">Putar roda untuk mendapatkan diskon keberuntunganmu!</p>

            <!-- Wheel Container -->
            <div class="relative w-64 h-64 mx-auto mb-6">
                <!-- Wheel Arrow Pointer -->
                <div class="absolute -top-3 left-1/2 -translate-x-1/2 z-20 pointer-anim text-red-600 text-3xl filter drop-shadow">
                    <i class="fa-solid fa-caret-down"></i>
                </div>
                <!-- Canvas Wheel -->
                <canvas id="wheelCanvas" width="300" height="300" class="w-full h-full rounded-full shadow-inner"></canvas>
            </div>

            <!-- Result Display Container -->
            <div id="spinResultContainer" class="mb-4 min-h-[50px] flex items-center justify-center">
                <p id="spinMessage" class="text-sm text-coffee-600 italic">Tekan tombol di bawah untuk memutar!</p>
            </div>

            <!-- Action Buttons -->
            <div class="space-y-2">
                <button id="spinBtn" class="w-full bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-600 hover:to-amber-700 text-coffee-950 font-bold py-3.5 rounded-xl shadow-lg transition-transform active:scale-95 text-base flex items-center justify-center gap-2">
                    <i class="fa-solid fa-arrows-spin"></i> Putar Roda Sekarang!
                </button>
                <button id="checkoutFromSpinBtn" class="w-full bg-coffee-800 hover:bg-coffee-900 text-white font-bold py-3 rounded-xl shadow-md transition-all hidden">
                    Lanjut ke Konfirmasi Pembayaran <i class="fa-solid fa-chevron-right text-xs ml-1"></i>
                </button>
            </div>
        </div>
    </div>

    <!-- ==================== MODAL KONFIRMASI CHECKOUT ==================== -->
    <div id="checkoutModal" class="fixed inset-0 bg-black/70 z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
        <div class="bg-white rounded-2xl max-w-lg w-full p-6 shadow-2xl relative max-h-[90vh] overflow-y-auto">
            <button id="closeCheckoutModalBtn" class="absolute top-4 right-4 text-coffee-400 hover:text-coffee-900 text-xl">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <h3 class="text-2xl font-bold text-coffee-900 mb-4 border-b border-coffee-100 pb-3">Konfirmasi Pesanan</h3>

            <!-- Customer Details Form -->
            <form id="checkoutForm" class="space-y-4 mb-6">
                <div>
                    <label class="block text-xs font-bold text-coffee-700 uppercase tracking-wider mb-1">Nama Pemesan</label>
                    <input type="text" id="custName" required placeholder="Masukkan nama Anda" class="w-full px-4 py-2.5 rounded-xl border border-coffee-200 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm">
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-bold text-coffee-700 uppercase tracking-wider mb-1">Tipe Pesanan</label>
                        <select id="orderType" class="w-full px-4 py-2.5 rounded-xl border border-coffee-200 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm bg-white">
                            <option value="Dine-in">Makan di Tempat (Dine-in)</option>
                            <option value="Takeaway">Bawa Pulang (Takeaway)</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-coffee-700 uppercase tracking-wider mb-1">Nomor Meja</label>
                        <input type="text" id="tableNo" placeholder="Contoh: 05" class="w-full px-4 py-2.5 rounded-xl border border-coffee-200 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm">
                    </div>
                </div>
            </form>

            <!-- Order Summary Details -->
            <div class="bg-coffee-50 p-4 rounded-xl space-y-2 mb-6 border border-coffee-100">
                <h4 class="font-bold text-sm text-coffee-900 mb-2">Rincian Pembayaran</h4>
                <div class="flex justify-between text-xs text-coffee-700">
                    <span>Total Harga Asli:</span>
                    <span id="summaryOriginalTotal" class="font-semibold">Rp 0</span>
                </div>
                <div class="flex justify-between text-xs text-green-700">
                    <span>Diskon Spin (<span id="summaryDiscountPercent">0%</span>):</span>
                    <span id="summaryDiscountAmount" class="font-semibold">- Rp 0</span>
                </div>
                <div class="flex justify-between text-base font-extrabold text-coffee-950 border-t border-coffee-200 pt-2 mt-2">
                    <span>Total Bayar Akhir:</span>
                    <span id="summaryFinalTotal" class="text-amber-600">Rp 0</span>
                </div>
            </div>

            <button id="payNowBtn" class="w-full bg-amber-500 hover:bg-amber-600 text-coffee-950 font-bold py-3.5 rounded-xl shadow-lg transition-transform active:scale-95 text-base flex items-center justify-center gap-2">
                <i class="fa-solid fa-receipt"></i> Bayar Sekarang
            </button>
        </div>
    </div>

    <!-- ==================== MODAL SUKSES RESI ==================== -->
    <div id="successModal" class="fixed inset-0 bg-black/80 z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
        <div class="bg-white rounded-3xl max-w-sm w-full p-6 text-center shadow-2xl relative border-t-8 border-green-500">
            <div class="w-16 h-16 bg-green-100 text-green-500 rounded-full flex items-center justify-center mx-auto text-3xl mb-4">
                <i class="fa-solid fa-check"></i>
            </div>

            <h3 class="text-2xl font-bold text-coffee-900">Pesanan Berhasil!</h3>
            <p class="text-xs text-coffee-600 mt-1 mb-4">Terima kasih telah memesan di Kafe Senja.</p>

            <div class="bg-coffee-50 p-4 rounded-xl border border-dashed border-coffee-300 text-left space-y-2 mb-6 text-xs">
                <div class="flex justify-between border-b border-coffee-200 pb-2">
                    <span class="text-coffee-500">No. Pesanan:</span>
                    <span id="receiptOrderNum" class="font-bold text-coffee-900">#KS-0000</span>
                </div>
                <div class="flex justify-between">
                    <span class="text-coffee-500">Nama:</span>
                    <span id="receiptCustName" class="font-semibold text-coffee-800">-</span>
                </div>
                <div class="flex justify-between">
                    <span class="text-coffee-500">Total Dibayar:</span>
                    <span id="receiptTotalPaid" class="font-bold text-amber-600">Rp 0</span>
                </div>
            </div>

            <p class="text-xs text-coffee-500 mb-6">Tunjukkan nomor pesanan ini ke kasir untuk verifikasi/pembayaran.</p>

            <button id="closeSuccessModalBtn" class="w-full bg-coffee-900 hover:bg-coffee-950 text-white font-bold py-3 rounded-xl shadow-md transition-all">
                Tutup & Kembali
            </button>
        </div>
    </div>

    <!-- ==================== TOAST NOTIFICATION ==================== -->
    <div id="toast" class="fixed bottom-5 right-5 z-50 bg-coffee-900 text-white px-5 py-3.5 rounded-xl shadow-2xl border border-amber-500/30 flex items-center space-x-3 transition-all duration-300 toast-enter pointer-events-none">
        <div class="text-amber-500 text-lg">
            <i class="fa-solid fa-circle-check"></i>
        </div>
        <p id="toastMessage" class="text-sm font-medium">Item berhasil ditambahkan!</p>
    </div>

    <!-- ==================== JAVASCRIPT APP LOGIC ==================== -->
    <script>
        // 1. DATA PRODUK (8 ITEM)
        const PRODUCTS = [
            { id: 1, name: 'Kopi Senja Utama', category: 'kopi', price: 25000, desc: 'Espresso racikan rahasia Senja dengan gula aren murni & susu segar.', image: 'https://images.unsplash.com/photo-1541167760496-1628856ab772?q=80&w=600&auto=format&fit=crop' },
            { id: 2, name: 'Espresso Double', category: 'kopi', price: 20000, desc: 'Ekstraksi ganda biji kopi Arabika pilihan dengan cita rasa mantap.', image: 'https://images.unsplash.com/photo-1510591509098-f4fdc6d0ff04?q=80&w=600&auto=format&fit=crop' },
            { id: 3, name: 'Caramel Macchiato', category: 'kopi', price: 32000, desc: 'Perpaduan espresso, sirup vanila, susu gurih, dan siraman sirup karamel.', image: 'https://images.unsplash.com/photo-1485808191679-5f86510681a2?q=80&w=600&auto=format&fit=crop' },
            { id: 4, name: 'Matcha Latte', category: 'non-kopi', price: 28000, desc: 'Bubuk matcha autentik Uji Jepang dipadu dengan susu hangat lembut.', image: 'https://images.unsplash.com/photo-1536256263959-770b48d82b0a?q=80&w=600&auto=format&fit=crop' },
            { id: 5, name: 'Croissant Butter', category: 'makanan', price: 22000, desc: 'Pastry khas Prancis yang berlapis renyah dengan mentega premium.', image: 'https://images.unsplash.com/photo-1555507036-ab1f4038808a?q=80&w=600&auto=format&fit=crop' },
            { id: 6, name: 'Roti Bakar Bandung', category: 'makanan', price: 24000, desc: 'Roti tebal dengan topping keju melimpah dan cokelat lumer.', image: 'https://images.unsplash.com/photo-1525351484163-7529414344d8?q=80&w=600&auto=format&fit=crop' },
            { id: 7, name: 'French Fries Truffle', category: 'makanan', price: 26000, desc: 'Kentang goreng renyah dengan aroma minyak truffle & taburan keju parmesan.', image: 'https://images.unsplash.com/photo-1576107232684-1279f390859f?q=80&w=600&auto=format&fit=crop' },
            { id: 8, name: 'Red Velvet Cake', category: 'makanan', price: 30000, desc: 'Kue red velvet lembut dengan lapisan cream cheese gurih manis.', image: 'https://images.unsplash.com/photo-1586985289688-ca3cf47d3e6e?q=80&w=600&auto=format&fit=crop' }
        ];

        // 2. SEGMENT DISKON RODA (8 SEGMENT)
        const WHEEL_SLICES = [
            { label: '0%', discount: 0, color: '#683323' },
            { label: '5%', discount: 0.05, color: '#f59e0b' },
            { label: '10%', discount: 0.10, color: '#84422e' },
            { label: '15%', discount: 0.15, color: '#d97706' },
            { label: '20%', discount: 0.20, color: '#9e5a42' },
            { label: '25%', discount: 0.25, color: '#b88572' },
            { label: '30%', discount: 0.30, color: '#4e281b' },
            { label: '50%', discount: 0.50, color: '#ef4444' } // Segmen Diskon Besar
        ];

        // 3. STATE MANAJEMEN APLIKASI
        let state = {
            cart: JSON.parse(localStorage.getItem('kafe_senja_cart')) || [],
            orders: JSON.parse(localStorage.getItem('kafe_senja_orders')) || [],
            appliedDiscount: 0, // Persentase diskon yang didapat
            isSpinning: false
        };

        // Helper: Format Rupiah
        function formatRp(number) {
            return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', maximumFractionDigits: 0 }).format(number);
        }

        // ==================== INITIALIZATION & EVENT LISTENERS ====================
        document.addEventListener('DOMContentLoaded', () => {
            renderMenu('all');
            updateCartUI();
            renderOrdersHistory();
            initWheelCanvas();

            // Mobile menu toggle
            document.getElementById('mobileMenuBtn').addEventListener('click', () => {
                document.getElementById('mobileMenu').classList.toggle('hidden');
            });

            // Category Filter Events
            document.querySelectorAll('#categoryFilters button').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    document.querySelectorAll('#categoryFilters button').forEach(b => {
                        b.classList.remove('bg-coffee-800', 'text-white');
                        b.classList.add('bg-white', 'text-coffee-800');
                    });
                    e.target.classList.remove('bg-white', 'text-coffee-800');
                    e.target.classList.add('bg-coffee-800', 'text-white');
                    
                    const category = e.target.getAttribute('data-category');
                    renderMenu(category);
                });
            });

            // Cart Drawer Controls
            document.getElementById('cartBtn').addEventListener('click', openCart);
            document.getElementById('closeCartBtn').addEventListener('click', closeCart);
            document.getElementById('cartDrawerOverlay').addEventListener('click', closeCart);

            // Spin Wheel Modal Controls
            document.getElementById('proceedToSpinBtn').addEventListener('click', () => {
                closeCart();
                openSpinModal();
            });
            document.getElementById('closeSpinModalBtn').addEventListener('click', closeSpinModal);
            document.getElementById('spinBtn').addEventListener('click', spinWheel);
            document.getElementById('checkoutFromSpinBtn').addEventListener('click', () => {
                closeSpinModal();
                openCheckoutModal();
            });

            // Checkout Modal Controls
            document.getElementById('closeCheckoutModalBtn').addEventListener('click', closeCheckoutModal);
            document.getElementById('payNowBtn').addEventListener('click', handlePayment);

            // Success Modal Controls
            document.getElementById('closeSuccessModalBtn').addEventListener('click', closeSuccessModal);

            // Clear History Control
            document.getElementById('clearHistoryBtn').addEventListener('click', clearOrdersHistory);
        });

        // ==================== MENU RENDERING ====================
        function renderMenu(category = 'all') {
            const container = document.getElementById('menuContainer');
            container.innerHTML = '';

            const filtered = category === 'all' 
                ? PRODUCTS 
                : PRODUCTS.filter(p => p.category === category);

            filtered.forEach(product => {
                const card = document.createElement('div');
                card.className = 'menu-card bg-white rounded-2xl overflow-hidden border border-coffee-100 flex flex-col justify-between shadow-sm';
                card.innerHTML = `
                    <div>
                        <div class="relative h-48 overflow-hidden">
                            <img src="${product.image}" alt="${product.name}" class="w-full h-full object-cover transition-transform duration-500 hover:scale-110">
                            <span class="absolute top-3 right-3 bg-coffee-950/80 text-amber-400 text-xs font-semibold px-2.5 py-1 rounded-full backdrop-blur-md uppercase">
                                ${product.category}
                            </span>
                        </div>
                        <div class="p-5">
                            <h3 class="font-bold text-lg text-coffee-900 mb-1">${product.name}</h3>
                            <p class="text-coffee-600 text-xs leading-relaxed mb-4 line-clamp-2">${product.desc}</p>
                        </div>
                    </div>
                    <div class="px-5 pb-5 pt-0 flex items-center justify-between border-t border-coffee-50 mt-auto">
                        <span class="text-base font-extrabold text-amber-600">${formatRp(product.price)}</span>
                        <button onclick="addToCart(${product.id})" class="bg-coffee-800 hover:bg-coffee-900 text-white p-2.5 rounded-xl shadow transition-all active:scale-90 flex items-center gap-1.5 text-xs font-semibold">
                            <i class="fa-solid fa-plus"></i> Tambah
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        // ==================== CART LOGIC & PERSISTENCE ====================
        function addToCart(productId) {
            const product = PRODUCTS.find(p => p.id === productId);
            const existing = state.cart.find(item => item.id === productId);

            if (existing) {
                existing.qty += 1;
            } else {
                state.cart.push({ ...product, qty: 1 });
            }

            saveCart();
            updateCartUI();
            showToast(`"${product.name}" telah ditambahkan!`);
        }

        function updateQuantity(productId, delta) {
            const item = state.cart.find(i => i.id === productId);
            if (!item) return;

            item.qty += delta;
            if (item.qty <= 0) {
                state.cart = state.cart.filter(i => i.id !== productId);
            }

            saveCart();
            updateCartUI();
        }

        function removeFromCart(productId) {
            state.cart = state.cart.filter(i => i.id !== productId);
            saveCart();
            updateCartUI();
        }

        function saveCart() {
            localStorage.setItem('kafe_senja_cart', JSON.stringify(state.cart));
        }

        function calculateSubtotal() {
            return state.cart.reduce((sum, item) => sum + (item.price * item.qty), 0);
        }

        function updateCartUI() {
            const cartItemsContainer = document.getElementById('cartItemsContainer');
            const cartCounter = document.getElementById('cartCounter');
            const cartSubtotal = document.getElementById('cartSubtotal');
            const proceedBtn = document.getElementById('proceedToSpinBtn');

            // Total count for badge
            const totalItems = state.cart.reduce((sum, i) => sum + i.qty, 0);
            
            if (totalItems > 0) {
                cartCounter.textContent = totalItems;
                cartCounter.classList.remove('hidden');
                proceedBtn.disabled = false;
            } else {
                cartCounter.classList.add('hidden');
                proceedBtn.disabled = true;
            }

            // Render list
            if (state.cart.length === 0) {
                cartItemsContainer.innerHTML = `
                    <div class="text-center py-12 text-coffee-400 space-y-3">
                        <i class="fa-solid fa-basket-shopping text-4xl"></i>
                        <p class="text-sm">Keranjang Anda masih kosong.</p>
                    </div>
                `;
            } else {
                cartItemsContainer.innerHTML = state.cart.map(item => `
                    <div class="flex items-center space-x-4 pt-3 first:pt-0">
                        <img src="${item.image}" alt="${item.name}" class="w-16 h-16 rounded-xl object-cover shadow-sm">
                        <div class="flex-1">
                            <h4 class="font-bold text-sm text-coffee-900">${item.name}</h4>
                            <p class="text-xs text-amber-600 font-semibold">${formatRp(item.price)}</p>
                            <div class="flex items-center space-x-2 mt-2">
                                <button onclick="updateQuantity(${item.id}, -1)" class="w-6 h-6 rounded-md bg-coffee-100 hover:bg-coffee-200 text-coffee-800 flex items-center justify-center text-xs font-bold">-</button>
                                <span class="text-xs font-bold text-coffee-900 px-1">${item.qty}</span>
                                <button onclick="updateQuantity(${item.id}, 1)" class="w-6 h-6 rounded-md bg-coffee-100 hover:bg-coffee-200 text-coffee-800 flex items-center justify-center text-xs font-bold">+</button>
                            </div>
                        </div>
                        <div class="text-right">
                            <p class="text-xs font-bold text-coffee-900 mb-2">${formatRp(item.price * item.qty)}</p>
                            <button onclick="removeFromCart(${item.id})" class="text-red-500 hover:text-red-700 text-xs">
                                <i class="fa-solid fa-trash-can"></i>
                            </button>
                        </div>
                    </div>
                `).join('');
            }

            cartSubtotal.textContent = formatRp(calculateSubtotal());
        }

        function openCart() {
            document.getElementById('cartDrawerOverlay').classList.remove('opacity-0', 'pointer-events-none');
            document.getElementById('cartDrawer').classList.remove('translate-x-full');
        }

        function closeCart() {
            document.getElementById('cartDrawerOverlay').classList.add('opacity-0', 'pointer-events-none');
            document.getElementById('cartDrawer').classList.add('translate-x-full');
        }

        // ==================== GIMMICK: SPIN THE WHEEL ====================
        let currentWheelAngle = 0;

        function initWheelCanvas() {
            const canvas = document.getElementById('wheelCanvas');
            const ctx = canvas.getContext('2d');
            const numSlices = WHEEL_SLICES.length;
            const sliceAngle = (2 * Math.PI) / numSlices;
            const radius = canvas.width / 2;

            ctx.clearRect(0, 0, canvas.width, canvas.height);

            for (let i = 0; i < numSlices; i++) {
                const angle = i * sliceAngle;
                
                // Draw slice segment
                ctx.beginPath();
                ctx.fillStyle = WHEEL_SLICES[i].color;
                ctx.moveTo(radius, radius);
                ctx.arc(radius, radius, radius - 5, angle, angle + sliceAngle);
                ctx.lineTo(radius, radius);
                ctx.fill();
                ctx.lineWidth = 2;
                ctx.strokeStyle = '#ffffff';
                ctx.stroke();

                // Draw Slice Text
                ctx.save();
                ctx.translate(radius, radius);
                ctx.rotate(angle + sliceAngle / 2);
                ctx.textAlign = 'right';
                ctx.fillStyle = '#ffffff';
                ctx.font = 'bold 16px Poppins';
                ctx.fillText(WHEEL_SLICES[i].label, radius - 20, 5);
                ctx.restore();
            }

            // Outer ring border
            ctx.beginPath();
            ctx.arc(radius, radius, radius - 3, 0, 2 * Math.PI);
            ctx.lineWidth = 6;
            ctx.strokeStyle = '#f59e0b';
            ctx.stroke();
        }

        function openSpinModal() {
            if (state.cart.length === 0) return;
            const modal = document.getElementById('spinModal');
            const card = document.getElementById('spinModalCard');
            
            // Reset wheel state for new session
            state.appliedDiscount = 0;
            document.getElementById('spinBtn').classList.remove('hidden');
            document.getElementById('checkoutFromSpinBtn').classList.add('hidden');
            document.getElementById('spinMessage').innerHTML = 'Tekan tombol di bawah untuk memutar!';

            modal.classList.remove('opacity-0', 'pointer-events-none');
            card.classList.remove('scale-95');
        }

        function closeSpinModal() {
            if (state.isSpinning) return; // Prevent closing while wheel spins
            const modal = document.getElementById('spinModal');
            const card = document.getElementById('spinModalCard');
            modal.classList.add('opacity-0', 'pointer-events-none');
            card.classList.add('scale-95');
        }

        function spinWheel() {
            if (state.isSpinning) return;
            state.isSpinning = true;

            const spinBtn = document.getElementById('spinBtn');
            spinBtn.disabled = true;
            spinBtn.classList.add('opacity-50', 'cursor-not-allowed');

            // Select random winning slice index
            const winningIndex = Math.floor(Math.random() * WHEEL_SLICES.length);
            const numSlices = WHEEL_SLICES.length;
            const sliceAngleDeg = 360 / numSlices;

            // Calculate rotation to align winning slice with top pointer (270 degrees position in standard canvas coords)
            // Extra full rotations (e.g. 5 full turns = 1800 deg)
            const extraRotations = 5 * 360; 
            const targetSliceCenterDeg = (winningIndex * sliceAngleDeg) + (sliceAngleDeg / 2);
            
            // Top pointer is at 270 deg on canvas.
            const targetRotation = extraRotations + (270 - targetSliceCenterDeg);

            const canvas = document.getElementById('wheelCanvas');
            canvas.style.transition = 'transform 4s cubic-bezier(0.15, 0.9, 0.25, 1)';
            canvas.style.transform = `rotate(${targetRotation}deg)`;

            setTimeout(() => {
                state.isSpinning = false;
                const wonSlice = WHEEL_SLICES[winningIndex];
                state.appliedDiscount = wonSlice.discount;

                // Update UI Display
                const msg = document.getElementById('spinMessage');
                msg.innerHTML = `
                    <div class="bg-amber-100 border border-amber-300 p-3 rounded-xl">
                        <p class="text-xs text-amber-800 font-semibold">Selamat! Anda Mendapatkan Diskon:</p>
                        <p class="text-3xl font-extrabold text-amber-600 my-1">${wonSlice.label}</p>
                    </div>
                `;

                spinBtn.classList.add('hidden');
                document.getElementById('checkoutFromSpinBtn').classList.remove('hidden');
            }, 4100);
        }

        // ==================== CHECKOUT & PAYMENT ====================
        function openCheckoutModal() {
            const subtotal = calculateSubtotal();
            const discountAmount = subtotal * state.appliedDiscount;
            const finalTotal = subtotal - discountAmount;

            document.getElementById('summaryOriginalTotal').textContent = formatRp(subtotal);
            document.getElementById('summaryDiscountPercent').textContent = `${Math.round(state.appliedDiscount * 100)}%`;
            document.getElementById('summaryDiscountAmount').textContent = `- ${formatRp(discountAmount)}`;
            document.getElementById('summaryFinalTotal').textContent = formatRp(finalTotal);

            const modal = document.getElementById('checkoutModal');
            modal.classList.remove('opacity-0', 'pointer-events-none');
        }

        function closeCheckoutModal() {
            document.getElementById('checkoutModal').classList.add('opacity-0', 'pointer-events-none');
        }

        function handlePayment() {
            const nameInput = document.getElementById('custName');
            const typeInput = document.getElementById('orderType');
            const tableInput = document.getElementById('tableNo');

            if (!nameInput.value.trim()) {
                alert('Silakan masukkan nama pemesan terlebih dahulu!');
                nameInput.focus();
                return;
            }

            const subtotal = calculateSubtotal();
            const discountAmount = subtotal * state.appliedDiscount;
            const finalTotal = subtotal - discountAmount;
            const orderNum = `#KS-${Math.floor(1000 + Math.random() * 9000)}`;

            // Create Order Object
            const newOrder = {
                id: orderNum,
                customer: nameInput.value.trim(),
                type: typeInput.value,
                table: tableInput.value.trim() || '-',
                items: [...state.cart],
                subtotal: subtotal,
                discountPercent: Math.round(state.appliedDiscount * 100),
                discountAmount: discountAmount,
                finalTotal: finalTotal,
                date: new Date().toLocaleString('id-ID', { dateStyle: 'medium', timeStyle: 'short' }),
                status: 'Diproses'
            };

            // Save to Orders state & LocalStorage
            state.orders.unshift(newOrder);
            localStorage.setItem('kafe_senja_orders', JSON.stringify(state.orders));

            // Reset Cart
            state.cart = [];
            saveCart();
            updateCartUI();

            // Populate Success Modal
            document.getElementById('receiptOrderNum').textContent = newOrder.id;
            document.getElementById('receiptCustName').textContent = newOrder.customer;
            document.getElementById('receiptTotalPaid').textContent = formatRp(newOrder.finalTotal);

            closeCheckoutModal();
            renderOrdersHistory();

            // Reset form
            document.getElementById('checkoutForm').reset();

            // Show Success Modal
            document.getElementById('successModal').classList.remove('opacity-0', 'pointer-events-none');
        }

        function closeSuccessModal() {
            document.getElementById('successModal').classList.add('opacity-0', 'pointer-events-none');
        }

        // ==================== PESANAN SAYA (ORDERS HISTORY) ====================
        function renderOrdersHistory() {
            const container = document.getElementById('ordersContainer');
            const clearBtn = document.getElementById('clearHistoryBtn');
            container.innerHTML = '';

            if (state.orders.length === 0) {
                clearBtn.classList.add('hidden');
                container.innerHTML = `
                    <div class="bg-white p-8 rounded-2xl text-center border border-coffee-200 text-coffee-400">
                        <i class="fa-solid fa-receipt text-3xl mb-2"></i>
                        <p class="text-sm">Belum ada riwayat pesanan.</p>
                    </div>
                `;
                return;
            }

            clearBtn.classList.remove('hidden');

            state.orders.forEach(order => {
                const orderCard = document.createElement('div');
                orderCard.className = 'bg-white p-5 rounded-2xl border border-coffee-200 shadow-sm flex flex-col md:flex-row justify-between gap-4';
                
                const itemsList = order.items.map(i => `${i.name} (x${i.qty})`).join(', ');

                orderCard.innerHTML = `
                    <div class="space-y-1">
                        <div class="flex items-center space-x-3">
                            <span class="font-bold text-coffee-900 text-base">${order.id}</span>
                            <span class="bg-amber-100 text-amber-800 text-xs px-2.5 py-0.5 rounded-full font-semibold">${order.status}</span>
                            <span class="text-xs text-coffee-400">${order.date}</span>
                        </div>
                        <p class="text-xs text-coffee-600">Pemesan: <strong class="text-coffee-800">${order.customer}</strong> (${order.type} - Meja ${order.table})</p>
                        <p class="text-xs text-coffee-500 line-clamp-1">Item: ${itemsList}</p>
                    </div>
                    <div class="md:text-right border-t md:border-t-0 pt-2 md:pt-0 border-coffee-100 flex md:flex-col justify-between items-end">
                        <p class="text-xs text-coffee-400">Diskon ${order.discountPercent}% Applied</p>
                        <p class="text-base font-extrabold text-amber-600">${formatRp(order.finalTotal)}</p>
                    </div>
                `;
                container.appendChild(orderCard);
            });
        }

        function clearOrdersHistory() {
            if (confirm('Apakah Anda yakin ingin menghapus seluruh riwayat pesanan?')) {
                state.orders = [];
                localStorage.removeItem('kafe_senja_orders');
                renderOrdersHistory();
            }
        }

        // ==================== TOAST UTILITY ====================
        function showToast(message) {
            const toast = document.getElementById('toast');
            document.getElementById('toastMessage').textContent = message;

            toast.classList.remove('toast-enter', 'pointer-events-none');
            toast.classList.add('toast-show');

            setTimeout(() => {
                toast.classList.remove('toast-show');
                toast.classList.add('toast-enter', 'pointer-events-none');
            }, 3000);
        }
    </script>
</body>
</html>
