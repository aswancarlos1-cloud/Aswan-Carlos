[index.html.txt](https://github.com/user-attachments/files/26864948/index.html.txt)
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pekalongan Berbagi - Platform Amal Semi-Konvensional</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Open+Sans:wght@400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        islamic: { DEFAULT: '#1B5E20', light: '#4CAF50', dark: '#0D3B10' },
                        gold: { DEFAULT: '#FFD700', light: '#FFE44D' },
                        cream: '#F5F5DC'
                    },
                    fontFamily: {
                        poppins: ['Poppins', 'sans-serif'],
                        opensans: ['Open Sans', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style>
        body { font-family: 'Open Sans', sans-serif; }
        h1, h2, h3, h4, h5, h6 { font-family: 'Poppins', sans-serif; }
        .glass-effect { background: rgba(255, 255, 255, 0.1); backdrop-filter: blur(10px); }
        .progress-bar { transition: width 1s ease-in-out; }
        .card-hover { transition: all 0.3s ease; }
        .card-hover:hover { transform: translateY(-5px); box-shadow: 0 20px 40px rgba(0,0,0,0.1); }
        @keyframes pulse-gold { 0%, 100% { box-shadow: 0 0 0 0 rgba(255, 215, 0, 0.4); } 50% { box-shadow: 0 0 0 15px rgba(255, 215, 0, 0); } }
        .pulse-gold { animation: pulse-gold 2s infinite; }
        .scroll-hidden::-webkit-scrollbar { display: none; }
        .fade-in { animation: fadeIn 0.5s ease-in; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body class="bg-gray-50">

    <!-- Navigation -->
    <nav class="bg-islamic text-white sticky top-0 z-50 shadow-lg">
        <div class="container mx-auto px-4 py-3">
            <div class="flex justify-between items-center">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 bg-white rounded-full flex items-center justify-center">
                        <span class="text-islamic font-bold text-xl">PB</span>
                    </div>
                    <div>
                        <h1 class="text-xl font-bold">Pekalongan Berbagi</h1>
                        <p class="text-xs text-green-200">Platform Amal Semi-Konvensional</p>
                    </div>
                </div>
                
                <div class="hidden md:flex items-center gap-6">
                    <a href="#" class="hover:text-gold transition" onclick="showPage('home')">Beranda</a>
                    <a href="#" class="hover:text-gold transition" onclick="showPage('programs')">Program</a>
                    <a href="#" class="hover:text-gold transition" onclick="showPage('reports')">Laporan</a>
                    <a href="#" class="hover:text-gold transition" onclick="showPage('about')">Tentang Kami</a>
                </div>

                <div class="flex items-center gap-3">
                    <button onclick="showPage('login')" class="px-4 py-2 rounded-lg border border-white hover:bg-white hover:text-islamic transition">
                        Masuk
                    </button>
                    <button onclick="showPage('register')" class="px-4 py-2 rounded-lg bg-gold text-islamic-dark font-semibold hover:bg-gold-light transition">
                        Daftar
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Toast Container -->
    <div id="toast-container" class="fixed top-20 right-4 z-50 space-y-2"></div>

    <!-- PAGE: HOME -->
    <div id="page-home" class="page">
        <!-- Hero Section -->
        <section class="bg-gradient-to-r from-islamic to-islamic-light text-white py-12">
            <div class="container mx-auto px-4">
                <div class="bg-white/10 backdrop-blur-md rounded-2xl p-6 border border-white/20">
                    <div class="flex justify-between items-start mb-6">
                        <div>
                            <h2 class="text-2xl font-bold mb-2">🕌 Jadwal Amal Hari Ini</h2>
                            <p class="text-green-100" id="current-date"></p>
                        </div>
                        <span class="bg-white/20 px-4 py-2 rounded-full text-sm">
                            <span id="active-programs-count">3</span> Program Aktif
                        </span>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4" id="today-programs">
                        <!-- Programs injected by JS -->
                    </div>
                </div>
            </div>
        </section>

        <!-- Gallery Section -->
        <section class="container mx-auto px-4 py-8">
            <h2 class="text-2xl font-bold text-gray-800 mb-6">📸 Galeri Kegiatan Terbaru</h2>
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4" id="gallery-grid">
                <!-- Gallery items injected by JS -->
            </div>
        </section>

        <!-- Needs Section -->
        <section class="container mx-auto px-4 py-8">
            <div class="bg-white rounded-2xl shadow-lg p-6">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-2xl font-bold text-gray-800">📋 Daftar Kebutuhan Minggu Ini</h2>
                    <button class="text-islamic hover:underline font-medium">Lihat Semua →</button>
                </div>
                <div class="space-y-4" id="needs-list">
                    <!-- Needs injected by JS -->
                </div>
            </div>
        </section>

        <!-- Transparency Section -->
        <section class="container mx-auto px-4 py-8">
            <div class="bg-islamic rounded-2xl p-8 text-white text-center">
                <h2 class="text-2xl font-bold mb-4">Transparansi adalah Kunci Kepercayaan</h2>
                <p class="text-green-100 mb-6 max-w-2xl mx-auto">
                    Lihat laporan keuangan lengkap kapan saja. Setiap rupiah tercatat dan dapat dipertanggungjawabkan.
                </p>
                <button onclick="downloadReport()" class="inline-flex items-center gap-2 px-6 py-3 bg-white text-islamic rounded-xl font-semibold hover:bg-gray-100 transition pulse-gold">
                    <i class="fas fa-download"></i>
                    Download Laporan Keuangan Q1 2026 (PDF)
                </button>
            </div>
        </section>
    </div>

    <!-- PAGE: PROGRAMS -->
    <div id="page-programs" class="page hidden">
        <div class="container mx-auto px-4 py-8">
            <h2 class="text-3xl font-bold text-gray-800 mb-6">Program Amal</h2>
            <div class="flex gap-4 mb-6 overflow-x-auto scroll-hidden">
                <button class="px-4 py-2 bg-islamic text-white rounded-full whitespace-nowrap">Semua</button>
                <button class="px-4 py-2 bg-gray-200 text-gray-700 rounded-full whitespace-nowrap hover:bg-gray-300">Sedekah Jumat</button>
                <button class="px-4 py-2 bg-gray-200 text-gray-700 rounded-full whitespace-nowrap hover:bg-gray-300">Warung Gratis</button>
                <button class="px-4 py-2 bg-gray-200 text-gray-700 rounded-full whitespace-nowrap hover:bg-gray-300">Beasiswa</button>
                <button class="px-4 py-2 bg-gray-200 text-gray-700 rounded-full whitespace-nowrap hover:bg-gray-300">Qurban</button>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="all-programs">
                <!-- All programs injected by JS -->
            </div>
        </div>
    </div>

    <!-- PAGE: DONATE -->
    <div id="page-donate" class="page hidden">
        <div class="container mx-auto px-4 py-8 max-w-2xl">
            <div class="bg-white rounded-2xl shadow-lg p-8">
                <h2 class="text-2xl font-bold text-gray-800 mb-2">Donasi Sekarang</h2>
                <p class="text-gray-500 mb-6" id="donate-program-name">Program: Sedekah Jumat #16</p>

                <form id="donation-form" onsubmit="handleDonation(event)">
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-2">Nominal Donasi</label>
                        <div class="grid grid-cols-3 gap-3 mb-3">
                            <button type="button" onclick="setAmount(50000)" class="py-3 border-2 border-gray-200 rounded-xl hover:border-islamic hover:bg-green-50 transition">Rp 50.000</button>
                            <button type="button" onclick="setAmount(100000)" class="py-3 border-2 border-gray-200 rounded-xl hover:border-islamic hover:bg-green-50 transition">Rp 100.000</button>
                            <button type="button" onclick="setAmount(200000)" class="py-3 border-2 border-gray-200 rounded-xl hover:border-islamic hover:bg-green-50 transition">Rp 200.000</button>
                        </div>
                        <input type="number" id="donation-amount" class="w-full p-4 border-2 border-gray-200 rounded-xl focus:border-islamic focus:outline-none text-lg" placeholder="Atau masukkan nominal lain..." required>
                    </div>

                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-2">Metode Pembayaran</label>
                        <div class="space-y-3">
                            <label class="flex items-center p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-islamic transition">
                                <input type="radio" name="payment" value="qris" class="w-5 h-5 text-islamic" checked>
                                <span class="ml-3 flex-1">QRIS (Scan QR Code)</span>
                                <i class="fas fa-qrcode text-2xl text-gray-400"></i>
                            </label>
                            <label class="flex items-center p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-islamic transition">
                                <input type="radio" name="payment" value="transfer" class="w-5 h-5 text-islamic">
                                <span class="ml-3 flex-1">Transfer Bank</span>
                                <i class="fas fa-university text-2xl text-gray-400"></i>
                            </label>
                            <label class="flex items-center p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-islamic transition">
                                <input type="radio" name="payment" value="ewallet" class="w-5 h-5 text-islamic">
                                <span class="ml-3 flex-1">E-Wallet (GoPay/OVO/DANA)</span>
                                <i class="fas fa-wallet text-2xl text-gray-400"></i>
                            </label>
                        </div>
                    </div>

                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-2">Pesan (Opsional)</label>
                        <textarea class="w-full p-4 border-2 border-gray-200 rounded-xl focus:border-islamic focus:outline-none" rows="3" placeholder="Tulis doa atau pesan motivasi..."></textarea>
                    </div>

                    <label class="flex items-center mb-6">
                        <input type="checkbox" class="w-5 h-5 text-islamic rounded">
                        <span class="ml-3 text-gray-600">Sembunyikan nama saya (Hamba Allah)</span>
                    </label>

                    <button type="submit" class="w-full py-4 bg-islamic text-white rounded-xl font-bold text-lg hover:bg-islamic-dark transition transform hover:scale-[1.02]">
                        Lanjutkan Pembayaran
                    </button>
                </form>
            </div>
        </div>
    </div>

    <!-- PAGE: PAYMENT -->
    <div id="page-payment" class="page hidden">
        <div class="container mx-auto px-4 py-8 max-w-md text-center">
            <div class="bg-white rounded-2xl shadow-lg p-8">
                <div class="w-20 h-20 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-check text-4xl text-islamic"></i>
                </div>
                <h2 class="text-2xl font-bold text-gray-800 mb-2">Donasi Berhasil!</h2>
                <p class="text-gray-500 mb-6">Terima kasih atas kebaikan Anda</p>

                <div class="bg-gray-50 rounded-xl p-4 mb-6 text-left">
                    <div class="flex justify-between mb-2">
                        <span class="text-gray-500">Invoice</span>
                        <span class="font-mono font-bold" id="payment-invoice">INV-20260419-001</span>
                    </div>
                    <div class="flex justify-between mb-2">
                        <span class="text-gray-500">Program</span>
                        <span class="font-medium" id="payment-program">Sedekah Jumat #16</span>
                    </div>
                    <div class="flex justify-between mb-2">
                        <span class="text-gray-500">Nominal</span>
                        <span class="font-bold text-islamic" id="payment-amount">Rp 100.000</span>
                    </div>
                    <div class="flex justify-between">
                        <span class="text-gray-500">Status</span>
                        <span class="px-3 py-1 bg-green-100 text-green-700 rounded-full text-sm">Terverifikasi</span>
                    </div>
                </div>

                <button onclick="showPage('home')" class="w-full py-3 bg-islamic text-white rounded-xl font-semibold hover:bg-islamic-dark transition">
                    Kembali ke Beranda
                </button>
            </div>
        </div>
    </div>

    <!-- PAGE: LOGIN -->
    <div id="page-login" class="page hidden">
        <div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-islamic to-islamic-light">
            <div class="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-md">
                <div class="text-center mb-8">
                    <div class="w-16 h-16 bg-islamic rounded-full flex items-center justify-center mx-auto mb-4">
                        <span class="text-white font-bold text-2xl">PB</span>
                    </div>
                    <h2 class="text-2xl font-bold text-gray-800">Selamat Datang Kembali</h2>
                    <p class="text-gray-500">Masuk untuk melanjutkan amal Anda</p>
                </div>

                <form onsubmit="handleLogin(event)" class="space-y-4">
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Email</label>
                        <input type="email" id="login-email" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-islamic focus:border-transparent" placeholder="nama@email.com" required>
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Password</label>
                        <input type="password" id="login-password" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-islamic focus:border-transparent" placeholder="••••••••" required>
                    </div>
                    <div class="flex justify-between items-center text-sm">
                        <label class="flex items-center">
                            <input type="checkbox" class="rounded text-islamic">
                            <span class="ml-2 text-gray-600">Ingat saya</span>
                        </label>
                        <a href="#" class="text-islamic hover:underline">Lupa password?</a>
                    </div>
                    <button type="submit" class="w-full py-3 bg-islamic text-white rounded-lg font-semibold hover:bg-islamic-dark transition">
                        Masuk
                    </button>
                </form>

                <p class="text-center mt-6 text-gray-500">
                    Belum punya akun? 
                    <a href="#" onclick="showPage('register')" class="text-islamic font-semibold hover:underline">Daftar sekarang</a>
                </p>
            </div>
        </div>
    </div>

    <!-- PAGE: REGISTER -->
    <div id="page-register" class="page hidden">
        <div class="min-h-screen flex items-center justify-center bg-gradient-to-br from-islamic to-islamic-light py-8">
            <div class="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-md">
                <div class="text-center mb-8">
                    <h2 class="text-2xl font-bold text-gray-800">Daftar Akun Baru</h2>
                    <p class="text-gray-500">Bergabung untuk berbagi kebaikan</p>
                </div>

                <form onsubmit="handleRegister(event)" class="space-y-4">
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Nama Lengkap</label>
                        <input type="text" id="reg-name" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-islamic focus:border-transparent" placeholder="Nama lengkap Anda" required>
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Email</label>
                        <input type="email" id="reg-email" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-islamic focus:border-transparent" placeholder="nama@email.com" required>
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Nomor HP (WhatsApp)</label>
                        <input type="tel" id="reg-phone" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-islamic focus:border-transparent" placeholder="08123456789" required>
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Password</label>
                        <input type="password" id="reg-password" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-islamic focus:border-transparent" placeholder="Minimal 8 karakter" required>
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Daftar Sebagai</label>
                        <select id="reg-role" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-islamic focus:border-transparent">
                            <option value="donor">Donatur</option>
                            <option value="volunteer">Relawan</option>
                        </select>
                    </div>
                    <label class="flex items-start">
                        <input type="checkbox" class="mt-1 rounded text-islamic" required>
                        <span class="ml-2 text-sm text-gray-600">Saya setuju dengan <a href="#" class="text-islamic hover:underline">Syarat dan Ketentuan</a> serta <a href="#" class="text-islamic hover:underline">Kebijakan Privasi</a></span>
                    </label>
                    <button type="submit" class="w-full py-3 bg-islamic text-white rounded-lg font-semibold hover:bg-islamic-dark transition">
                        Daftar Sekarang
                    </button>
                </form>

                <p class="text-center mt-6 text-gray-500">
                    Sudah punya akun? 
                    <a href="#" onclick="showPage('login')" class="text-islamic font-semibold hover:underline">Masuk</a>
                </p>
            </div>
        </div>
    </div>

    <!-- PAGE: DASHBOARD DONOR -->
    <div id="page-dashboard" class="page hidden">
        <header class="bg-white shadow-sm border-b">
            <div class="container mx-auto px-4 py-4">
                <div class="flex justify-between items-center">
                    <div>
                        <h1 class="text-2xl font-bold text-gray-800">Assalamu'alaikum, <span id="dashboard-user-name">Ahmad</span></h1>
                        <p class="text-gray-500">Selamat datang di dashboard donatur</p>
                    </div>
                    <div class="flex items-center gap-4">
                        <button class="relative p-2 text-gray-600 hover:bg-gray-100 rounded-full">
                            <i class="fas fa-bell text-xl"></i>
                            <span class="absolute -top-1 -right-1 w-5 h-5 bg-red-500 text-white text-xs rounded-full flex items-center justify-center">3</span>
                        </button>
                        <div class="w-10 h-10 bg-islamic rounded-full flex items-center justify-center text-white font-bold" id="dashboard-avatar">A</div>
                    </div>
                </div>
            </div>
        </header>

        <div class="container mx-auto px-4 py-8">
            <!-- Stats -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-6 mb-8">
                <div class="bg-white rounded-2xl p-6 shadow-lg border-l-4 border-islamic">
                    <div class="flex justify-between items-center">
                        <div>
                            <p class="text-gray-500 text-sm">Total Donasi</p>
                            <h3 class="text-2xl font-bold text-gray-800" id="stat-total">Rp 2.500.000</h3>
                        </div>
                        <div class="w-12 h-12 bg-green-100 rounded-xl flex items-center justify-center">
                            <i class="fas fa-hand-holding-heart text-islamic text-xl"></i>
                        </div>
                    </div>
                </div>
                <div class="bg-white rounded-2xl p-6 shadow-lg border-l-4 border-islamic-light">
                    <div class="flex justify-between items-center">
                        <div>
                            <p class="text-gray-500 text-sm">Program Didukung</p>
                            <h3 class="text-2xl font-bold text-gray-800" id="stat-programs">8</h3>
                        </div>
                        <div class="w-12 h-12 bg-green-100 rounded-xl flex items-center justify-center">
                            <i class="fas fa-list text-islamic-light text-xl"></i>
                        </div>
                    </div>
                </div>
                <div class="bg-white rounded-2xl p-6 shadow-lg border-l-4 border-gold">
                    <div class="flex justify-between items-center">
                        <div>
                            <p class="text-gray-500 text-sm">Sertifikat</p>
                            <h3 class="text-2xl font-bold text-gray-800" id="stat-certificates">12</h3>
                        </div>
                        <div class="w-12 h-12 bg-yellow-100 rounded-xl flex items-center justify-center">
                            <i class="fas fa-award text-gold text-xl"></i>
                        </div>
                    </div>
                </div>
                <div class="bg-white rounded-2xl p-6 shadow-lg border-l-4 border-blue-500">
                    <div class="flex justify-between items-center">
                        <div>
                            <p class="text-gray-500 text-sm">Poin Amal</p>
                            <h3 class="text-2xl font-bold text-gray-800" id="stat-points">250</h3>
                        </div>
                        <div class="w-12 h-12 bg-blue-100 rounded-xl flex items-center justify-center">
                            <i class="fas fa-star text-blue-500 text-xl"></i>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Tabs -->
            <div class="bg-white rounded-2xl shadow-lg overflow-hidden">
                <div class="flex border-b overflow-x-auto">
                    <button onclick="switchDashboardTab('overview')" class="dashboard-tab flex-1 py-4 px-6 text-center font-medium text-islamic border-b-2 border-islamic bg-green-50" data-tab="overview">
                        <i class="fas fa-chart-line mr-2"></i>Ringkasan
                    </button>
                    <button onclick="switchDashboardTab('history')" class="dashboard-tab flex-1 py-4 px-6 text-center font-medium text-gray-500 hover:text-gray-700" data-tab="history">
                        <i class="fas fa-history mr-2"></i>Riwayat
                    </button>
                    <button onclick="switchDashboardTab('programs')" class="dashboard-tab flex-1 py-4 px-6 text-center font-medium text-gray-500 hover:text-gray-700" data-tab="programs">
                        <i class="fas fa-heart mr-2"></i>Program Saya
                    </button>
                </div>

                <div class="p-6" id="dashboard-content">
                    <!-- Content injected by JS -->
                </div>
            </div>
        </div>
    </div>

    <!-- PAGE: ADMIN DASHBOARD -->
    <div id="page-admin" class="page hidden">
        <header class="bg-islamic text-white shadow-lg">
            <div class="container mx-auto px-4 py-4">
                <div class="flex justify-between items-center">
                    <div class="flex items-center gap-4">
                        <h1 class="text-xl font-bold">Admin Dashboard</h1>
                        <span class="bg-white/20 px-3 py-1 rounded-full text-sm">Super Admin</span>
                    </div>
                    <div class="flex items-center gap-4">
                        <button class="p-2 hover:bg-white/10 rounded-full relative">
                            <i class="fas fa-bell text-xl"></i>
                            <span class="absolute -top-1 -right-1 w-5 h-5 bg-red-500 rounded-full text-xs flex items-center justify-center">5</span>
                        </button>
                        <div class="w-8 h-8 bg-white/20 rounded-full flex items-center justify-center">A</div>
                    </div>
                </div>
            </div>
        </header>

        <div class="container mx-auto px-4 py-8">
            <!-- Stats -->
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-4 mb-8">
                <div class="bg-white rounded-xl p-4 shadow-sm">
                    <div class="w-10 h-10 bg-green-100 rounded-lg flex items-center justify-center mb-3">
                        <i class="fas fa-donate text-islamic"></i>
                    </div>
                    <p class="text-2xl font-bold">125.5Jt</p>
                    <p class="text-xs text-gray-500">Total Dana</p>
                </div>
                <div class="bg-white rounded-xl p-4 shadow-sm">
                    <div class="w-10 h-10 bg-blue-100 rounded-lg flex items-center justify-center mb-3">
                        <i class="fas fa-calendar-check text-blue-600"></i>
                    </div>
                    <p class="text-2xl font-bold">12</p>
                    <p class="text-xs text-gray-500">Program Aktif</p>
                </div>
                <div class="bg-white rounded-xl p-4 shadow-sm">
                    <div class="w-10 h-10 bg-purple-100 rounded-lg flex items-center justify-center mb-3">
                        <i class="fas fa-users text-purple-600"></i>
                    </div>
                    <p class="text-2xl font-bold">450</p>
                    <p class="text-xs text-gray-500">Penerima</p>
                </div>
                <div class="bg-white rounded-xl p-4 shadow-sm">
                    <div class="w-10 h-10 bg-yellow-100 rounded-lg flex items-center justify-center mb-3">
                        <i class="fas fa-user-friends text-yellow-600"></i>
                    </div>
                    <p class="text-2xl font-bold">85</p>
                    <p class="text-xs text-gray-500">Relawan</p>
                </div>
                <div class="bg-white rounded-xl p-4 shadow-sm">
                    <div class="w-10 h-10 bg-red-100 rounded-lg flex items-center justify-center mb-3">
                        <i class="fas fa-clock text-red-600"></i>
                    </div>
                    <p class="text-2xl font-bold">12</p>
                    <p class="text-xs text-gray-500">Verifikasi Pending</p>
                </div>
                <div class="bg-white rounded-xl p-4 shadow-sm">
                    <div class="w-10 h-10 bg-indigo-100 rounded-lg flex items-center justify-center mb-3">
                        <i class="fas fa-chart-line text-indigo-600"></i>
                    </div>
                    <p class="text-2xl font-bold">+23%</p>
                    <p class="text-xs text-gray-500">vs Bulan Lalu</p>
                </div>
            </div>

            <!-- Charts & Tables -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <div class="lg:col-span-2 space-y-8">
                    <div class="bg-white rounded-2xl shadow-lg p-6">
                        <h3 class="text-lg font-bold mb-4">Tren Donasi 12 Bulan</h3>
                        <canvas id="donationChart" height="100"></canvas>
                    </div>
                </div>
                <div class="space-y-8">
                    <div class="bg-white rounded-2xl shadow-lg p-6">
                        <h3 class="text-lg font-bold mb-4">Aksi Cepat</h3>
                        <div class="space-y-3">
                            <button class="w-full py-3 bg-islamic text-white rounded-xl hover:bg-islamic-dark transition">
                                <i class="fas fa-plus mr-2"></i>Buat Program Baru
                            </button>
                            <button class="w-full py-3 bg-islamic-light text-white rounded-xl hover:bg-green-600 transition">
                                <i class="fas fa-bullhorn mr-2"></i>Broadcast Pesan
                            </button>
                            <button class="w-full py-3 bg-gold text-islamic-dark rounded-xl hover:bg-gold-light transition">
                                <i class="fas fa-file-alt mr-2"></i>Generate Laporan
                            </button>
                        </div>
                    </div>

                    <div class="bg-white rounded-2xl shadow-lg p-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-bold">Verifikasi Pending</h3>
                            <span class="bg-yellow-100 text-yellow-700 px-2 py-1 rounded-full text-xs">12 menunggu</span>
                        </div>
                        <div class="space-y-3 max-h-96 overflow-y-auto" id="admin-verifications">
                            <!-- Injected by JS -->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-12 mt-12">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                <div>
                    <div class="flex items-center gap-3 mb-4">
                        <div class="w-10 h-10 bg-white rounded-full flex items-center justify-center">
                            <span class="text-islamic font-bold">PB</span>
                        </div>
                        <h3 class="text-xl font-bold">Pekalongan Berbagi</h3>
                    </div>
                    <p class="text-gray-400 text-sm">Platform amal semi-konvensional untuk masyarakat Pekalongan. Transparan, terpercaya, berkelanjutan.</p>
                </div>
                <div>
                    <h4 class="font-bold mb-4">Program</h4>
                    <ul class="space-y-2 text-gray-400 text-sm">
                        <li><a href="#" class="hover:text-white">Sedekah Jumat</a></li>
                        <li><a href="#" class="hover:text-white">Warung Gratis</a></li>
                        <li><a href="#" class="hover:text-white">Beasiswa Yatim</a></li>
                        <li><a href="#" class="hover:text-white">Qurban & Ramadhan</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold mb-4">Tentang</h4>
                    <ul class="space-y-2 text-gray-400 text-sm">
                        <li><a href="#" class="hover:text-white">Visi & Misi</a></li>
                        <li><a href="#" class="hover:text-white">Tim Kami</a></li>
                        <li><a href="#" class="hover:text-white">Laporan Keuangan</a></li>
                        <li><a href="#" class="hover:text-white">Kontak</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold mb-4">Hubungi Kami</h4>
                    <ul class="space-y-2 text-gray-400 text-sm">
                        <li><i class="fas fa-phone mr-2"></i>0812-3456-7890</li>
                        <li><i class="fas fa-envelope mr-2"></i>info@pekalonganberbagi.id</li>
                        <li><i class="fas fa-map-marker-alt mr-2"></i>Pekalongan, Jawa Tengah</li>
                    </ul>
                    <div class="flex gap-4 mt-4">
                        <a href="#" class="w-10 h-10 bg-gray-700 rounded-full flex items-center justify-center hover:bg-islamic transition"><i class="fab fa-whatsapp"></i></a>
                        <a href="#" class="w-10 h-10 bg-gray-700 rounded-full flex items-center justify-center hover:bg-islamic transition"><i class="fab fa-instagram"></i></a>
                        <a href="#" class="w-10 h-10 bg-gray-700 rounded-full flex items-center justify-center hover:bg-islamic transition"><i class="fab fa-facebook"></i></a>
                    </div>
                </div>
            </div>
            <div class="border-t border-gray-700 mt-8 pt-8 text-center text-gray-400 text-sm">
                <p>© 2026 Pekalongan Berbagi. All rights reserved. | Made with ❤️ for Pekalongan</p>
            </div>
        </div>
    </footer>

    <script>
        // ==================== DATA STORE ====================
        const store = {
            currentUser: null,
            programs: [
                { id: 1, code: 'SJ-016', name: 'Sedekah Jumat #16', slug: 'sedekah-jumat-16', type: 'sedekah_jumat', category: 'routine', target: 5000000, collected: 3750000, location: 'Masjid Al-Ikhlas, Pekalongan Timur', time: '11:30 - 13:00', donors: 45, image: '🍱', status: 'active' },
                { id: 2, code: 'WG-009', name: 'Warung Gratis #9', slug: 'warung-gratis-9', type: 'warung_gratis', category: 'routine', target: 3000000, collected: 1500000, location: 'Alun-alun Kota Pekalongan', time: '16:00 - 18:00', donors: 28, image: '🍲', status: 'active' },
                { id: 3, code: 'PS-003', name: 'Posyandu Digital #3', slug: 'posyandu-digital-3', type: 'klinik_sosial', category: 'routine', target: 2000000, collected: 1800000, location: 'Balai RW 02, Kajen', time: '08:00 - 11:00', donors: 15, image: '💊', status: 'active' },
                { id: 4, code: 'BS-012', name: 'Beasiswa Santri Q2 2026', slug: 'beasiswa-santri-q2', type: 'beasiswa', category: 'project', target: 15000000, collected: 9000000, location: 'Multiple Locations', time: 'Bulanan', donors: 120, image: '📚', status: 'active' },
                { id: 5, code: 'QB-1447', name: 'Qurban 1447H', slug: 'qurban-1447h', type: 'qurban', category: 'seasonal', target: 50000000, collected: 35000000, location: 'Seluruh Pekalongan', time: 'Idul Adha', donors: 250, image: '🐄', status: 'active' },
            ],
            needs: [
                { id: 1, item: 'Beras 50kg', fulfilled: 30, total: 50, unit: 'kg', priority: 'high' },
                { id: 2, item: 'Buku Pelajaran SD', fulfilled: 40, total: 100, unit: 'pcs', priority: 'medium' },
                { id: 3, item: 'Vitamin Anak', fulfilled: 80, total: 100, unit: 'botol', priority: 'urgent' },
                { id: 4, item: 'Pakaian Layak Pakai', fulfilled: 20, total: 100, unit: 'pcs', priority: 'low' },
            ],
            galleries: [
                { id: 1, title: 'Renovasi Rumah Pak Budi', date: '15 Apr 2026', image: '🏠' },
                { id: 2, title: 'Santunan Yatim 2025', date: '10 Apr 2026', image: '👶' },
                { id: 3, title: 'Pelatihan Jahit 2025', date: '05 Apr 2026', image: '🧵' },
                { id: 4, title: 'Qurban 1446H', date: '01 Apr 2026', image: '🐄' },
            ],
            donations: [
                { id: 1, program: 'Sedekah Jumat #15', amount: 100000, status: 'verified', date: '15 Apr 2026' },
                { id: 2, program: 'Beasiswa Santri Umar', amount: 500000, status: 'verified', date: '10 Apr 2026' },
                { id: 3, program: 'Warung Gratis #8', amount: 150000, status: 'verified', date: '01 Apr 2026' },
            ],
            verifications: [
                { id: 1, name: 'Budi Santoso', nik: '3375012345678901', category: 'dhuafa', rt: '05', rw: '02', kelurahan: 'Kedungwuni', docs: 3 },
                { id: 2, name: 'Siti Aminah', nik: '3375012345678902', category: 'yatim', rt: '03', rw: '01', kelurahan: 'Kajen', docs: 4 },
                { id: 3, name: 'Ahmad Fauzi', nik: '3375012345678903', category: 'janda', rt: '07', rw: '03', kelurahan: 'Pekalongan Selatan', docs: 3 },
            ]
        };

        // ==================== UTILITIES ====================
        function formatRupiah(amount) {
            return 'Rp ' + amount.toLocaleString('id-ID');
        }

        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            const colors = type === 'success' ? 'bg-green-500' : type === 'error' ? 'bg-red-500' : 'bg-blue-500';
            toast.className = `${colors} text-white px-6 py-3 rounded-xl shadow-lg transform transition-all duration-300 translate-x-full`;
            toast.innerHTML = `<i class="fas ${type === 'success' ? 'fa-check' : type === 'error' ? 'fa-exclamation' : 'fa-info'} mr-2"></i>${message}`;
            container.appendChild(toast);
            
            setTimeout(() => toast.classList.remove('translate-x-full'), 100);
            setTimeout(() => {
                toast.classList.add('translate-x-full');
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        function showPage(pageName) {
            document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'));
            document.getElementById(`page-${pageName}`).classList.remove('hidden');
            window.scrollTo(0, 0);
            
            if (pageName === 'home') renderHome();
            if (pageName === 'programs') renderPrograms();
            if (pageName === 'dashboard') renderDashboard();
            if (pageName === 'admin') renderAdmin();
        }

        // ==================== RENDER FUNCTIONS ====================
        function renderHome() {
            // Set current date
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            document.getElementById('current-date').textContent = new Date().toLocaleDateString('id-ID', options);

            // Render today's programs
            const programsContainer = document.getElementById('today-programs');
            programsContainer.innerHTML = store.programs.slice(0, 3).map(p => `
                <div class="bg-white/10 backdrop-blur-sm rounded-xl p-4 border border-white/20 hover:bg-white/20 transition cursor-pointer" onclick="showDonatePage(${p.id})">
                    <div class="flex items-start gap-3 mb-3">
                        <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center text-2xl">${p.image}</div>
                        <div class="flex-1">
                            <h3 class="font-bold text-white">${p.name}</h3>
                            <p class="text-green-200 text-sm">${p.type === 'sedekah_jumat' ? 'Sedekah Jumat' : p.type === 'warung_gratis' ? 'Warung Gratis' : 'Klinik Sosial'}</p>
                        </div>
                    </div>
                    <div class="mb-3">
                        <div class="flex justify-between text-sm text-green-100 mb-1">
                            <span>Terkumpul</span>
                            <span>${Math.round((p.collected/p.target)*100)}%</span>
                        </div>
                        <div class="h-2 bg-white/20 rounded-full overflow-hidden">
                            <div class="h-full bg-gold transition-all duration-1000" style="width: ${(p.collected/p.target)*100}%"></div>
                        </div>
                        <div class="flex justify-between text-xs text-green-200 mt-1">
                            <span>${formatRupiah(p.collected)}</span>
                            <span>${formatRupiah(p.target)}</span>
                        </div>
                    </div>
                    <div class="flex items-center justify-between text-sm text-green-100">
                        <span><i class="fas fa-map-marker-alt mr-1"></i>${p.location.split(',')[0]}</span>
                        <span><i class="fas fa-users mr-1"></i>${p.donors}</span>
                    </div>
                </div>
            `).join('');

            // Render gallery
            document.getElementById('gallery-grid').innerHTML = store.galleries.map(g => `
                <div class="group relative overflow-hidden rounded-xl shadow-lg cursor-pointer card-hover">
                    <div class="w-full h-48 bg-gradient-to-br from-gray-200 to-gray-300 flex items-center justify-center text-6xl">
                        ${g.image}
                    </div>
                    <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent flex items-end p-4">
                        <div>
                            <h3 class="text-white font-semibold">${g.title}</h3>
                            <p class="text-gray-300 text-sm">${g.date}</p>
                        </div>
                    </div>
                </div>
            `).join('');

            // Render needs
            document.getElementById('needs-list').innerHTML = store.needs.map(n => {
                const percentage = (n.fulfilled / n.total) * 100;
                const priorityColors = {
                    urgent: 'bg-red-100 text-red-700',
                    high: 'bg-orange-100 text-orange-700',
                    medium: 'bg-blue-100 text-blue-700',
                    low: 'bg-gray-100 text-gray-700'
                };
                const priorityLabels = { urgent: 'Segera', high: 'Penting', medium: 'Normal', low: 'Rendah' };
                
                return `
                <div class="flex items-center gap-4 p-4 bg-gray-50 rounded-xl hover:bg-gray-100 transition">
                    <div class="flex-1">
                        <div class="flex justify-between items-start mb-2">
                            <div>
                                <h3 class="font-semibold text-gray-800">${n.item}</h3>
                                <p class="text-sm text-gray-500">Dibutuhkan: ${n.total} ${n.unit}</p>
                            </div>
                            <span class="px-3 py-1 rounded-full text-xs font-medium ${priorityColors[n.priority]}">
                                ${priorityLabels[n.priority]}
                            </span>
                        </div>
                        <div class="h-2 bg-gray-200 rounded-full overflow-hidden">
                            <div class="h-full ${n.priority === 'urgent' ? 'bg-red-500' : 'bg-islamic-light'} transition-all duration-1000" style="width: ${percentage}%"></div>
                        </div>
                        <div class="flex justify-between items-center mt-2">
                            <span class="text-sm text-gray-600">Terkumpul: ${n.fulfilled} / ${n.total} ${n.unit}</span>
                            <button onclick="showDonatePage()" class="px-4 py-2 bg-islamic text-white rounded-lg text-sm hover:bg-islamic-dark transition">
                                Donasi Sekarang
                            </button>
                        </div>
                    </div>
                </div>
                `;
            }).join('');
        }

        function renderPrograms() {
            const container = document.getElementById('all-programs');
            container.innerHTML = store.programs.map(p => `
                <div class="bg-white rounded-2xl shadow-lg overflow-hidden card-hover">
                    <div class="h-48 bg-gradient-to-br from-islamic to-islamic-light flex items-center justify-center text-6xl">
                        ${p.image}
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <span class="px-3 py-1 bg-green-100 text-islamic rounded-full text-xs font-medium">
                                ${p.category === 'routine' ? 'Rutin' : p.category === 'seasonal' ? 'Musiman' : 'Proyek'}
                            </span>
                            <span class="text-sm text-gray-500"><i class="fas fa-users mr-1"></i>${p.donors} donatur</span>
                        </div>
                        <h3 class="text-xl font-bold text-gray-800 mb-2">${p.name}</h3>
                        <p class="text-gray-500 text-sm mb-4"><i class="fas fa-map-marker-alt mr-1"></i>${p.location}</p>
                        
                        <div class="mb-4">
                            <div class="flex justify-between text-sm mb-1">
                                <span class="text-gray-600">Progress</span>
                                <span class="font-bold text-islamic">${Math.round((p.collected/p.target)*100)}%</span>
                            </div>
                            <div class="h-3 bg-gray-200 rounded-full overflow-hidden">
                                <div class="h-full bg-gradient-to-r from-islamic to-islamic-light transition-all duration-1000" style="width: ${(p.collected/p.target)*100}%"></div>
                            </div>
                            <div class="flex justify-between text-xs text-gray-500 mt-1">
                                <span>${formatRupiah(p.collected)}</span>
                                <span>${formatRupiah(p.target)}</span>
                            </div>
                        </div>
                        
                        <button onclick="showDonatePage(${p.id})" class="w-full py-3 bg-islamic text-white rounded-xl font-semibold hover:bg-islamic-dark transition">
                            Donasi Sekarang
                        </button>
                    </div>
                </div>
            `).join('');
        }

        function renderDashboard() {
            document.getElementById('dashboard-user-name').textContent = store.currentUser?.name || 'Pengguna';
            document.getElementById('dashboard-avatar').textContent = (store.currentUser?.name || 'P')[0];
            
            const content = document.getElementById('dashboard-content');
            content.innerHTML = `
                <div class="space-y-6">
                    <div class="bg-gray-50 rounded-xl p-6">
                        <h3 class="text-lg font-bold text-gray-800 mb-4">Tren Donasi 6 Bulan Terakhir</h3>
                        <div class="h-64 flex items-end justify-between gap-2">
                            ${[65, 45, 80, 55, 90, 75].map((h, i) => `
                                <div class="flex-1 flex flex-col items-center gap-2">
                                    <div class="w-full bg-islamic rounded-t-lg transition-all duration-1000" style="height: ${h}%"></div>
                                    <span class="text-xs text-gray-500">${['Nov','Des','Jan','Feb','Mar','Apr'][i]}</span>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                        <button class="p-4 bg-islamic text-white rounded-xl hover:bg-islamic-dark transition text-center">
                            <div class="text-2xl mb-2">💳</div>
                            <div class="font-medium text-sm">Donasi Cepat</div>
                        </button>
                        <button class="p-4 bg-islamic-light text-white rounded-xl hover:bg-green-600 transition text-center">
                            <div class="text-2xl mb-2">🔄</div>
                            <div class="font-medium text-sm">Donasi Rutin</div>
                        </button>
                        <button class="p-4 bg-gold text-islamic-dark rounded-xl hover:bg-gold-light transition text-center">
                            <div class="text-2xl mb-2">🎁</div>
                            <div class="font-medium text-sm">Tukar Poin</div>
                        </button>
                        <button class="p-4 bg-gray-200 text-gray-700 rounded-xl hover:bg-gray-300 transition text-center">
                            <div class="text-2xl mb-2">⚙️</div>
                            <div class="font-medium text-sm">Pengaturan</div>
                        </button>
                    </div>
                </div>
            `;
        }

        function renderAdmin() {
            document.getElementById('admin-verifications').innerHTML = store.verifications.map(v => `
                <div class="p-4 bg-gray-50 rounded-xl cursor-pointer hover:bg-gray-100 transition" onclick="showVerificationDetail(${v.id})">
                    <div class="flex justify-between items-start">
                        <div>
                            <h4 class="font-semibold text-gray-800">${v.name}</h4>
                            <p class="text-sm text-gray-500">NIK: ${v.nik}</p>
                            <p class="text-xs text-gray-400">${v.kelurahan}, RT ${v.rt}/RW ${v.rw}</p>
                        </div>
                        <span class="px-2 py-1 rounded-full text-xs ${v.category === 'yatim' ? 'bg-blue-100 text-blue-700' : v.category === 'dhuafa' ? 'bg-green-100 text-green-700' : 'bg-purple-100 text-purple-700'}">
                            ${v.category}
                        </span>
                    </div>
                    <div class="flex items-center gap-2 mt-2 text-xs text-gray-500">
                        <span>📎 ${v.docs} dokumen</span>
                        <span>•</span>
                        <span>2 jam yang lalu</span>
                    </div>
                </div>
            `).join('');

            // Render chart
            const ctx = document.getElementById('donationChart');
            if (ctx && !ctx.chart) {
                // Simple canvas chart rendering
                const canvas = ctx;
                const c = canvas.getContext('2d');
                canvas.chart = true;
                
                // Draw line chart
                const data = [65, 59, 80, 81, 56, 95, 120, 110, 130, 125, 140, 155];
                const labels = ['Apr','Mei','Jun','Jul','Agu','Sep','Okt','Nov','Des','Jan','Feb','Mar'];
                const max = Math.max(...data);
                const width = canvas.width = canvas.offsetWidth;
                const height = canvas.height = 300;
                const padding = 40;
                
                c.clearRect(0, 0, width, height);
                c.strokeStyle = '#1B5E20';
                c.lineWidth = 3;
                c.beginPath();
                
                data.forEach((val, i) => {
                    const x = padding + (i / (data.length - 1)) * (width - 2 * padding);
                    const y = height - padding - (val / max) * (height - 2 * padding);
                    if (i === 0) c.moveTo(x, y);
                    else c.lineTo(x, y);
                });
                c.stroke();
                
                // Draw labels
                c.fillStyle = '#666';
                c.font = '12px sans-serif';
                labels.forEach((label, i) => {
                    const x = padding + (i / (labels.length - 1)) * (width - 2 * padding);
                    c.fillText(label, x - 10, height - 10);
                });
            }
        }

        // ==================== INTERACTION HANDLERS ====================
        function showDonatePage(programId) {
            const program = store.programs.find(p => p.id === programId) || store.programs[0];
            document.getElementById('donate-program-name').textContent = `Program: ${program.name}`;
            showPage('donate');
        }

        function setAmount(amount) {
            document.getElementById('donation-amount').value = amount;
        }

        function handleDonation(e) {
            e.preventDefault();
            const amount = document.getElementById('donation-amount').value;
            if (!amount || amount < 10000) {
                showToast('Minimal donasi Rp 10.000', 'error');
                return;
            }
            
            // Simulate API call
            setTimeout(() => {
                document.getElementById('payment-amount').textContent = formatRupiah(parseInt(amount));
                document.getElementById('payment-invoice').textContent = 'INV-' + Date.now().toString().slice(-8);
                showPage('payment');
                showToast('Donasi berhasil! Jazakumullah khairan.');
            }, 1000);
        }

        function handleLogin(e) {
            e.preventDefault();
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;
            
            // Simulate auth
            if (email.includes('admin')) {
                store.currentUser = { name: 'Admin', email, role: 'admin' };
                showPage('admin');
            } else {
                store.currentUser = { name: email.split('@')[0], email, role: 'donor' };
                showPage('dashboard');
            }
            showToast('Login berhasil!');
        }

        function handleRegister(e) {
            e.preventDefault();
            showToast('Pendaftaran berhasil! Silakan verifikasi email Anda.');
            showPage('login');
        }

        function switchDashboardTab(tab) {
            document.querySelectorAll('.dashboard-tab').forEach(t => {
                t.classList.remove('text-islamic', 'border-b-2', 'border-islamic', 'bg-green-50');
                t.classList.add('text-gray-500');
            });
            document.querySelector(`[data-tab="${tab}"]`).classList.add('text-islamic', 'border-b-2', 'border-islamic', 'bg-green-50');
            document.querySelector(`[data-tab="${tab}"]`).classList.remove('text-gray-500');
            
            const content = document.getElementById('dashboard-content');
            if (tab === 'history') {
                content.innerHTML = `
                    <div class="space-y-4">
                        ${store.donations.map(d => `
                            <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                                <div class="flex items-center gap-4">
                                    <div class="w-12 h-12 bg-green-100 rounded-full flex items-center justify-center text-green-600">
                                        <i class="fas fa-check"></i>
                                    </div>
                                    <div>
                                        <h4 class="font-semibold text-gray-800">${d.program}</h4>
                                        <p class="text-xs text-gray-400">${d.date}</p>
                                    </div>
                                </div>
                                <div class="text-right">
                                    <p class="font-bold text-gray-800">${formatRupiah(d.amount)}</p>
                                    <span class="text-xs px-2 py-1 bg-green-100 text-green-700 rounded-full">Sukses</span>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                `;
            } else if (tab === 'programs') {
                content.innerHTML = `
                    <div class="space-y-6">
                        ${store.programs.slice(0, 2).map(p => `
                            <div class="bg-gray-50 rounded-xl p-4">
                                <div class="flex justify-between items-start mb-2">
                                    <h4 class="font-bold text-gray-800">${p.name}</h4>
                                    <span class="text-islamic font-bold">${Math.round((p.collected/p.target)*100)}%</span>
                                </div>
                                <div class="h-2 bg-gray-200 rounded-full overflow-hidden mb-2">
                                    <div class="h-full bg-islamic" style="width: ${(p.collected/p.target)*100}%"></div>
                                </div>
                                <p class="text-sm text-gray-600">Anda telah mendonasikan ${formatRupiah(100000)}</p>
                            </div>
                        `).join('')}
                    </div>
                `;
            } else {
                renderDashboard();
            }
        }

        function showVerificationDetail(id) {
            showToast('Membuka detail verifikasi...');
        }

        function downloadReport() {
            showToast('Mengunduh laporan keuangan...');
            setTimeout(() => {
                showToast('Laporan berhasil diunduh!');
            }, 1500);
        }

        // ==================== INITIALIZATION ====================
        document.addEventListener('DOMContentLoaded', () => {
            renderHome();
            
            // Simulate real-time updates
            setInterval(() => {
                const randomProgram = store.programs[Math.floor(Math.random() * 3)];
                randomProgram.collected += Math.floor(Math.random() * 50000);
                if (Math.random() > 0.7) renderHome();
            }, 5000);
        });
    </script>
</body>
</html>
