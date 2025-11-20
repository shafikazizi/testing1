
<html lang="ms">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>eKenderaan - Sistem Pengurusan Kenderaan</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
        body {
            box-sizing: border-box;
        }
        
        /* Custom responsive utilities */
        @media (max-width: 640px) {
            .mobile-stack {
                flex-direction: column;
            }
            .mobile-full {
                width: 100%;
            }
            .mobile-text-sm {
                font-size: 0.875rem;
            }
        }
        
        /* Animation utilities */
        .fade-in {
            animation: fadeIn 0.3s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Chart container responsive */
        .chart-container {
            position: relative;
            width: 100%;
            height: 400px;
        }
        
        @media (max-width: 768px) {
            .chart-container {
                height: 300px;
            }
        }
        
        /* Table responsive wrapper */
        .table-responsive {
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
        }
        
        /* Mobile navigation improvements */
        .mobile-nav-item {
            transition: all 0.2s ease;
        }
        
        .mobile-nav-item:hover {
            background-color: #f3f4f6;
            padding-left: 1.5rem;
        }
        
        /* Form responsive improvements */
        .form-grid {
            display: grid;
            gap: 1rem;
            grid-template-columns: 1fr;
        }
        
        @media (min-width: 640px) {
            .form-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        @media (min-width: 1024px) {
            .form-grid-lg {
                grid-template-columns: repeat(4, 1fr);
            }
            
            .form-grid-xl {
                grid-template-columns: repeat(5, 1fr);
            }
        }
        
        /* Card responsive improvements */
        .card-grid {
            display: grid;
            gap: 1rem;
            grid-template-columns: 1fr;
        }
        
        @media (min-width: 640px) {
            .card-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        @media (min-width: 1024px) {
            .card-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }
        
        /* Button responsive improvements */
        .btn-responsive {
            padding: 0.5rem 1rem;
            font-size: 0.875rem;
        }
        
        @media (min-width: 768px) {
            .btn-responsive {
                padding: 0.75rem 1.5rem;
                font-size: 1rem;
            }
        }
        
        /* Status badge improvements */
        .status-badge {
            display: inline-flex;
            align-items: center;
            padding: 0.25rem 0.75rem;
            border-radius: 9999px;
            font-size: 0.75rem;
            font-weight: 500;
        }
        
        .status-active {
            background-color: #d1fae5;
            color: #065f46;
        }
        
        .status-inactive {
            background-color: #fee2e2;
            color: #991b1b;
        }
        
        .status-pending {
            background-color: #fef3c7;
            color: #92400e;
        }
        
        .status-approved {
            background-color: #d1fae5;
            color: #065f46;
        }
        
        .status-rejected {
            background-color: #fee2e2;
            color: #991b1b;
        }
        
        .status-in-use {
            background-color: #dbeafe;
            color: #1e40af;
        }
        
        /* Loading spinner */
        .spinner {
            border: 2px solid #f3f3f3;
            border-top: 2px solid #3498db;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Modal improvements */
        .modal-backdrop {
            backdrop-filter: blur(4px);
        }
        
        /* Print styles */
        @media print {
            .no-print {
                display: none !important;
            }
            
            .print-full-width {
                width: 100% !important;
            }
        }
        
        /* Accessibility improvements */
        .focus-visible:focus {
            outline: 2px solid #3b82f6;
            outline-offset: 2px;
        }
        
        /* High contrast mode support */
        @media (prefers-contrast: high) {
            .bg-gray-50 {
                background-color: #ffffff;
            }
            
            .text-gray-600 {
                color: #000000;
            }
        }
        
        /* Reduced motion support */
        @media (prefers-reduced-motion: reduce) {
            .fade-in {
                animation: none;
            }
            
            .spinner {
                animation: none;
            }
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="/_sdk/element_sdk.js" type="text/javascript"></script>
 </head>
 <body class="bg-gradient-to-br from-blue-50 to-indigo-100 min-h-screen"><!-- Login Section -->
  <div id="login-section" class="min-h-screen flex items-center justify-center px-4">
   <div class="bg-white rounded-xl shadow-lg p-6 sm:p-8 w-full max-w-md fade-in">
    <div class="text-center mb-6 sm:mb-8">
     <h1 class="text-2xl sm:text-3xl font-bold text-gray-800 mb-2">🚗 eKenderaan</h1>
     <p class="text-gray-600 text-sm sm:text-base">Sistem Pengurusan Kenderaan</p>
     <p class="text-gray-600 text-xs sm:text-sm">Pejabat Pendidikan Daerah Limbang</p>
    </div><!-- Login/Register Toggle -->
    <div class="flex mb-6 bg-gray-100 rounded-lg p-1"><button id="login-tab" class="flex-1 py-2 px-4 rounded-md font-medium transition-all bg-blue-600 text-white text-sm sm:text-base"> Log Masuk </button> <button id="register-tab" class="flex-1 py-2 px-4 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm sm:text-base"> Daftar Akaun </button>
    </div><!-- Login Form -->
    <div id="login-form-container">
     <form id="login-form" class="space-y-4 sm:space-y-6">
      <div><label for="username" class="block text-sm font-medium text-gray-700 mb-2">Email Rasmi</label> <input type="email" id="username" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" placeholder="Masukkan email rasmi" required>
      </div>
      <div><label for="password" class="block text-sm font-medium text-gray-700 mb-2">Kata Laluan</label> <input type="password" id="password" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" placeholder="Masukkan kata laluan" required>
      </div><button type="submit" class="w-full bg-blue-600 text-white py-2 sm:py-3 px-4 sm:px-6 rounded-lg font-medium hover:bg-blue-700 transition-colors text-sm sm:text-base"> 🔐 Log Masuk </button>
     </form><!-- Demo Credentials -->
     <div class="mt-4 sm:mt-6 p-3 sm:p-4 bg-gray-50 rounded-lg">
      <p class="text-xs sm:text-sm text-gray-600 font-medium mb-2 sm:mb-3">Demo Login Credentials:</p>
      <div class="space-y-2">
       <div class="bg-white p-2 rounded border-l-4 border-red-500">
        <p class="text-xs font-medium text-gray-700">Admin:</p>
        <p class="text-xs text-gray-600">admin@moe.gov.my / admin123</p>
       </div>
       <div class="bg-white p-2 rounded border-l-4 border-blue-500">
        <p class="text-xs font-medium text-gray-700">Staff:</p>
        <p class="text-xs text-gray-600">pegawai@moe.gov.my / pegawai123</p>
       </div>
       <div class="bg-white p-2 rounded border-l-4 border-green-500">
        <p class="text-xs font-medium text-gray-700">Manager:</p>
        <p class="text-xs text-gray-600">manager@moe.gov.my / manager123</p>
       </div>
      </div>
     </div>
    </div><!-- Registration Form -->
    <div id="register-form-container" class="hidden">
     <form id="register-form" class="space-y-4 sm:space-y-6">
      <div><label for="reg-fullname" class="block text-sm font-medium text-gray-700 mb-2">Nama Penuh</label> <input type="text" id="reg-fullname" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" placeholder="Masukkan nama penuh" required>
      </div>
      <div><label for="reg-email" class="block text-sm font-medium text-gray-700 mb-2">Email Rasmi</label> <input type="email" id="reg-email" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" placeholder="contoh@moe.gov.my" required>
      </div>
      <div><label for="reg-sector" class="block text-sm font-medium text-gray-700 mb-2">Sektor/Unit</label> <select id="reg-sector" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" required> <option value="">Pilih sektor/unit...</option> <option value="Sektor Perancangan">Sektor Perancangan</option> <option value="Sektor Pembelajaran">Sektor Pembelajaran</option> <option value="Sektor Pengurusan Sekolah">Sektor Pengurusan Sekolah</option> <option value="Sektor Pengurusan">Sektor Pengurusan</option> <option value="Sektor Pentaksiran dan Peperiksaan">Sektor Pentaksiran dan Peperiksaan</option> <option value="PTIS">PTIS</option> </select>
      </div>
      <div><label for="reg-password" class="block text-sm font-medium text-gray-700 mb-2">Kata Laluan</label> <input type="password" id="reg-password" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" placeholder="Cipta kata laluan" required>
      </div>
      <div><label for="reg-confirm-password" class="block text-sm font-medium text-gray-700 mb-2">Sahkan Kata Laluan</label> <input type="password" id="reg-confirm-password" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" placeholder="Sahkan kata laluan" required>
      </div><button type="submit" class="w-full bg-green-600 text-white py-2 sm:py-3 px-4 sm:px-6 rounded-lg font-medium hover:bg-green-700 transition-colors text-sm sm:text-base"> ✅ Daftar Akaun </button>
     </form>
    </div><!-- Messages -->
    <div id="login-error" class="hidden mt-4 p-3 bg-red-100 border border-red-400 text-red-700 rounded-lg text-sm">
     Nama pengguna atau kata laluan tidak sah!
    </div>
    <div id="register-success" class="hidden mt-4 p-3 bg-green-100 border border-green-400 text-green-700 rounded-lg text-sm">
     ✅ Akaun berjaya didaftar! Sila log masuk.
    </div>
    <div id="register-error" class="hidden mt-4 p-3 bg-red-100 border border-red-400 text-red-700 rounded-lg text-sm"><!-- Error message will be inserted here -->
    </div>
   </div>
  </div><!-- Main Application -->
  <div id="main-app" class="hidden container mx-auto px-4 py-4 sm:py-8 max-w-7xl"><!-- Header -->
   <header class="mb-6 sm:mb-8"><!-- Mobile Header -->
    <div class="lg:hidden">
     <div class="flex justify-between items-center mb-4">
      <div id="user-info-mobile" class="text-left">
       <p class="text-xs text-gray-600">Selamat datang,</p>
       <p id="current-user-display-mobile" class="text-sm font-semibold text-gray-800"></p>
       <p id="current-role-display-mobile" class="text-xs text-blue-600"></p>
      </div><button id="logout-btn-mobile" class="px-3 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 transition-colors text-xs no-print"> 🚪 Keluar </button>
     </div>
     <div class="text-center mb-4">
      <h1 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">🚗 eKenderaan</h1>
      <p class="text-sm text-gray-600">Sistem Pengurusan Kenderaan</p>
      <p class="text-xs text-gray-600">PPD Limbang</p>
     </div>
    </div><!-- Desktop Header -->
    <div class="hidden lg:block text-center">
     <div class="flex justify-between items-center mb-4">
      <div id="user-info" class="text-left">
       <p class="text-sm text-gray-600">Selamat datang,</p>
       <p id="current-user-display" class="font-semibold text-gray-800"></p>
       <p id="current-role-display" class="text-xs text-blue-600"></p>
      </div>
      <div class="text-center">
       <h1 class="text-3xl sm:text-4xl font-bold text-gray-800 mb-2">🚗 eKenderaan</h1>
       <p class="text-gray-600">Sistem Pengurusan Kenderaan</p>
       <p class="text-gray-600">Pejabat Pendidikan Daerah Limbang</p>
      </div><button id="logout-btn" class="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 transition-colors text-sm no-print"> 🚪 Log Keluar </button>
     </div>
    </div>
   </header><!-- Navigation Tabs -->
   <div class="mb-6 sm:mb-8 no-print"><!-- Mobile Navigation (Hamburger Menu) -->
    <div class="lg:hidden">
     <div class="bg-white rounded-lg shadow-md"><button id="mobile-menu-toggle" class="w-full px-4 py-3 text-left font-medium text-gray-800 flex items-center justify-between focus-visible:focus"> <span id="mobile-menu-title">📝 Tempahan Baru</span>
       <svg class="w-5 h-5 transition-transform" id="mobile-menu-arrow" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
       </svg></button>
      <div id="mobile-menu-items" class="hidden border-t border-gray-200"><button id="mobile-tab-booking" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> 📝 Tempahan Baru </button> <button id="mobile-tab-tracking" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> 📍 Tracking Kenderaan </button> <button id="mobile-tab-schedule" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> 📅 Jadual Pinjaman </button> <button id="mobile-tab-history" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> 📋 Sejarah Pinjaman </button> <button id="mobile-tab-approval" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> ✅ Kelulusan Tempahan </button> <button id="mobile-tab-users" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> 👥 Pengurusan Pengguna </button> <button id="mobile-tab-drivers" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> 🚗 Pengurusan Pemandu </button> <button id="mobile-tab-vehicles" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all border-b border-gray-100"> 🚙 Pengurusan Kenderaan </button> <button id="mobile-tab-analytics" class="mobile-nav-item w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all"> 📊 Analitik Penggunaan </button>
      </div>
     </div>
    </div><!-- Desktop Navigation -->
    <div class="hidden lg:flex justify-center">
     <div class="bg-white rounded-lg shadow-md p-1">
      <div class="flex flex-wrap justify-center gap-1"><button id="tab-booking" class="btn-responsive rounded-md font-medium transition-all bg-blue-600 text-white focus-visible:focus"> Tempahan Baru </button> <button id="tab-tracking" class="btn-responsive rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 focus-visible:focus"> Tracking Kenderaan </button> <button id="tab-schedule" class="btn-responsive rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 focus-visible:focus"> Jadual Pinjaman </button> <button id="tab-history" class="btn-responsive rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 focus-visible:focus"> Sejarah Pinjaman </button> <button id="tab-approval" class="btn-responsive rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 focus-visible:focus"> Kelulusan Tempahan </button> <!-- Management Dropdown -->
       <div class="relative" id="management-dropdown"><button id="management-dropdown-btn" class="btn-responsive rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 flex items-center focus-visible:focus"> Pengurusan 
         <svg class="w-3 h-3 ml-1 transition-transform" id="dropdown-arrow" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
         </svg></button>
        <div id="management-dropdown-menu" class="hidden absolute top-full left-0 mt-1 bg-white rounded-lg shadow-lg border border-gray-200 min-w-48 z-50 max-h-60 overflow-y-auto"><button id="tab-users" class="w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all rounded-t-lg text-sm focus-visible:focus"> 👥 Pengurusan Pengguna </button> <button id="tab-drivers" class="w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all text-sm focus-visible:focus"> 🚗 Pengurusan Pemandu </button> <button id="tab-vehicles" class="w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all rounded-b-lg text-sm focus-visible:focus"> 🚙 Pengurusan Kenderaan </button>
        </div>
       </div><button id="tab-analytics" class="btn-responsive rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 focus-visible:focus"> Analitik Penggunaan </button>
      </div>
     </div>
    </div>
   </div><!-- Booking Form Section -->
   <div id="booking-section" class="max-w-4xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">📝 Borang Tempahan Kenderaan</h2>
     <form id="booking-form" class="space-y-4 sm:space-y-6">
      <div class="form-grid">
       <div><label for="employee-name" class="block text-sm font-medium text-gray-700 mb-2">Nama Pegawai</label> <input type="text" id="employee-name" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg bg-gray-50 text-gray-700 text-sm sm:text-base" readonly>
       </div>
       <div><label for="employee-sector" class="block text-sm font-medium text-gray-700 mb-2">Sektor/Unit</label> <input type="text" id="employee-sector" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg bg-gray-50 text-gray-700 text-sm sm:text-base" readonly>
       </div>
      </div>
      <div class="hidden"><label class="block text-sm font-medium text-gray-700 mb-2">Kenderaan</label>
       <div class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg bg-gray-50 text-gray-600 text-sm sm:text-base">
        Kenderaan akan ditentukan oleh admin semasa kelulusan
       </div><input type="hidden" id="car-select" value="Akan ditentukan oleh admin">
      </div>
      <div class="form-grid">
       <div><label for="start-date" class="block text-sm font-medium text-gray-700 mb-2">Tarikh Mula</label> <input type="date" id="start-date" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" required>
       </div>
       <div><label for="start-time" class="block text-sm font-medium text-gray-700 mb-2">Masa Mula</label> <select id="start-time" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" required> <option value="">Pilih masa...</option> <option value="07:00">07:00 AM</option> <option value="07:30">07:30 AM</option> <option value="08:00">08:00 AM</option> <option value="08:30">08:30 AM</option> <option value="09:00">09:00 AM</option> <option value="09:30">09:30 AM</option> <option value="10:00">10:00 AM</option> <option value="10:30">10:30 AM</option> <option value="11:00">11:00 AM</option> <option value="11:30">11:30 AM</option> <option value="12:00">12:00 PM</option> <option value="12:30">12:30 PM</option> <option value="13:00">01:00 PM</option> <option value="13:30">01:30 PM</option> <option value="14:00">02:00 PM</option> <option value="14:30">02:30 PM</option> <option value="15:00">03:00 PM</option> <option value="15:30">03:30 PM</option> <option value="16:00">04:00 PM</option> <option value="16:30">04:30 PM</option> <option value="17:00">05:00 PM</option> <option value="17:30">05:30 PM</option> <option value="18:00">06:00 PM</option> </select>
       </div>
      </div>
      <div class="form-grid">
       <div><label for="end-date" class="block text-sm font-medium text-gray-700 mb-2">Tarikh Tamat</label> <input type="date" id="end-date" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" required>
       </div>
       <div><label for="end-time" class="block text-sm font-medium text-gray-700 mb-2">Masa Tamat</label> <select id="end-time" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" required> <option value="">Pilih masa...</option> <option value="07:00">07:00 AM</option> <option value="07:30">07:30 AM</option> <option value="08:00">08:00 AM</option> <option value="08:30">08:30 AM</option> <option value="09:00">09:00 AM</option> <option value="09:30">09:30 AM</option> <option value="10:00">10:00 AM</option> <option value="10:30">10:30 AM</option> <option value="11:00">11:00 AM</option> <option value="11:30">11:30 AM</option> <option value="12:00">12:00 PM</option> <option value="12:30">12:30 PM</option> <option value="13:00">01:00 PM</option> <option value="13:30">01:30 PM</option> <option value="14:00">02:00 PM</option> <option value="14:30">02:30 PM</option> <option value="15:00">03:00 PM</option> <option value="15:30">03:30 PM</option> <option value="16:00">04:00 PM</option> <option value="16:30">04:30 PM</option> <option value="17:00">05:00 PM</option> <option value="17:30">05:30 PM</option> <option value="18:00">06:00 PM</option> </select>
       </div>
      </div>
      <div><label for="purpose" class="block text-sm font-medium text-gray-700 mb-2">Tujuan Penggunaan</label> <textarea id="purpose" rows="3" class="w-full px-3 sm:px-4 py-2 sm:py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm sm:text-base" placeholder="Nyatakan tujuan penggunaan kereta..." required></textarea>
      </div><button type="submit" class="w-full bg-blue-600 text-white py-2 sm:py-3 px-4 sm:px-6 rounded-lg font-medium hover:bg-blue-700 transition-colors text-sm sm:text-base"> 🚗 Hantar Tempahan Kenderaan </button>
     </form>
    </div>
   </div><!-- Tracking Section -->
   <div id="tracking-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">📍 Status Kenderaan Masa Kini</h2>
     <div class="card-grid" id="car-status-grid"><!-- Car status cards will be populated here -->
     </div>
    </div>
   </div><!-- Schedule Section -->
   <div id="schedule-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">📅 Jadual Pinjaman Kenderaan</h2><!-- Date Navigation -->
     <div class="flex flex-col sm:flex-row items-center justify-between mb-4 sm:mb-6 gap-4"><button id="prev-week" class="btn-responsive bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors order-1 sm:order-none"> ← Minggu Sebelum </button>
      <h3 id="current-week" class="text-base sm:text-lg font-semibold text-gray-800 order-2 sm:order-none"></h3><button id="next-week" class="btn-responsive bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors order-3 sm:order-none"> Minggu Seterusnya → </button>
     </div><!-- Calendar Grid -->
     <div class="table-responsive">
      <div class="min-w-full"><!-- Days Header -->
       <div class="grid grid-cols-8 gap-1 sm:gap-2 mb-4">
        <div class="font-semibold text-gray-700 p-2 sm:p-3 text-xs sm:text-sm">
         Kenderaan
        </div>
        <div id="day-headers" class="col-span-7 grid grid-cols-7 gap-1 sm:gap-2"><!-- Day headers will be populated here -->
        </div>
       </div><!-- Car Schedule Grid -->
       <div id="schedule-grid" class="space-y-1 sm:space-y-2"><!-- Schedule rows will be populated here -->
       </div>
      </div>
     </div><!-- Legend -->
     <div class="mt-4 sm:mt-6 flex flex-wrap gap-2 sm:gap-4 text-xs sm:text-sm">
      <div class="flex items-center">
       <div class="w-3 h-3 sm:w-4 sm:h-4 bg-green-200 rounded mr-2"></div><span>Tersedia</span>
      </div>
      <div class="flex items-center">
       <div class="w-3 h-3 sm:w-4 sm:h-4 bg-blue-200 rounded mr-2"></div><span>Ditempah</span>
      </div>
      <div class="flex items-center">
       <div class="w-3 h-3 sm:w-4 sm:h-4 bg-red-200 rounded mr-2"></div><span>Sedang Digunakan</span>
      </div>
     </div>
    </div>
   </div><!-- History Section -->
   <div id="history-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">📋 Sejarah Pinjaman</h2>
     <div class="table-responsive">
      <table class="w-full table-auto min-w-full">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Nama</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Sektor/Unit</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Kenderaan</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Pemandu</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tarikh</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Status</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tujuan</th>
        </tr>
       </thead>
       <tbody id="history-table-body"><!-- History entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Approval Section -->
   <div id="approval-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">✅ Kelulusan Tempahan</h2><!-- Pending Approvals -->
     <div class="mb-6 sm:mb-8">
      <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">⏳ Tempahan Menunggu Kelulusan</h3>
      <div class="table-responsive">
       <table class="w-full table-auto min-w-full">
        <thead>
         <tr class="bg-yellow-50">
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Nama</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Sektor/Unit</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Kenderaan</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tarikh &amp; Masa</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tujuan</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700 no-print">Tindakan</th>
         </tr>
        </thead>
        <tbody id="pending-approvals-body"><!-- Pending approvals will be populated here -->
        </tbody>
       </table>
      </div>
     </div><!-- Recent Decisions -->
     <div>
      <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">📋 Keputusan Terkini</h3>
      <div class="table-responsive">
       <table class="w-full table-auto min-w-full">
        <thead>
         <tr class="bg-gray-50">
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Nama</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Kenderaan</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tarikh</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Status</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Diluluskan Oleh</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Masa Keputusan</th>
         </tr>
        </thead>
        <tbody id="recent-decisions-body"><!-- Recent decisions will be populated here -->
        </tbody>
       </table>
      </div>
     </div>
    </div>
   </div><!-- Driver Management Section -->
   <div id="drivers-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">🚗 Pengurusan Pemandu</h2><!-- Add New Driver Form -->
     <div class="bg-gray-50 rounded-lg p-4 sm:p-6 mb-6 sm:mb-8 no-print">
      <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">➕ Tambah Pemandu Baru</h3>
      <form id="add-driver-form" class="form-grid form-grid-lg">
       <div><label for="new-driver-name" class="block text-sm font-medium text-gray-700 mb-2">Nama Penuh Pemandu</label> <input type="text" id="new-driver-name" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" placeholder="Encik Ahmad bin Ali" required>
       </div>
       <div><label for="new-driver-ic" class="block text-sm font-medium text-gray-700 mb-2">No. Kad Pengenalan</label> <input type="text" id="new-driver-ic" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" placeholder="123456-12-1234" required>
       </div>
       <div><label for="new-driver-license" class="block text-sm font-medium text-gray-700 mb-2">No. Lesen Memandu</label> <input type="text" id="new-driver-license" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" placeholder="D1234567" required>
       </div>
       <div class="flex items-end"><button type="submit" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors text-sm"> ➕ Tambah Pemandu </button>
       </div>
      </form>
     </div><!-- Drivers List -->
     <div class="table-responsive">
      <table class="w-full table-auto min-w-full print-full-width">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Nama Pemandu</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">No. Kad Pengenalan</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">No. Lesen</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Status</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tarikh Daftar</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700 no-print">Tindakan</th>
        </tr>
       </thead>
       <tbody id="drivers-table-body"><!-- Driver entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Vehicle Management Section -->
   <div id="vehicles-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">🚗 Pengurusan Kenderaan</h2><!-- Add New Vehicle Form -->
     <div class="bg-gray-50 rounded-lg p-4 sm:p-6 mb-6 sm:mb-8 no-print">
      <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">➕ Tambah Kenderaan Baru</h3>
      <form id="add-vehicle-form" class="form-grid form-grid-xl">
       <div><label for="new-vehicle-brand" class="block text-sm font-medium text-gray-700 mb-2">Jenama</label> <select id="new-vehicle-brand" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" required> <option value="">Pilih jenama...</option> <option value="Toyota">Toyota</option> <option value="Honda">Honda</option> <option value="Perodua">Perodua</option> <option value="Proton">Proton</option> <option value="Nissan">Nissan</option> <option value="Mazda">Mazda</option> <option value="Mitsubishi">Mitsubishi</option> </select>
       </div>
       <div><label for="new-vehicle-model" class="block text-sm font-medium text-gray-700 mb-2">Model</label> <input type="text" id="new-vehicle-model" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" placeholder="Contoh: Vios, City, Axia" required>
       </div>
       <div><label for="new-vehicle-plate" class="block text-sm font-medium text-gray-700 mb-2">No. Plat</label> <input type="text" id="new-vehicle-plate" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" placeholder="ABC1234" required>
       </div>
       <div><label for="new-vehicle-year" class="block text-sm font-medium text-gray-700 mb-2">Tahun</label> <select id="new-vehicle-year" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" required> <option value="">Pilih tahun...</option> <option value="2024">2024</option> <option value="2023">2023</option> <option value="2022">2022</option> <option value="2021">2021</option> <option value="2020">2020</option> <option value="2019">2019</option> <option value="2018">2018</option> <option value="2017">2017</option> <option value="2016">2016</option> <option value="2015">2015</option> </select>
       </div>
       <div class="flex items-end"><button type="submit" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors text-sm"> ➕ Tambah Kenderaan </button>
       </div>
      </form>
     </div><!-- Vehicles List -->
     <div class="table-responsive">
      <table class="w-full table-auto min-w-full print-full-width">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Jenama &amp; Model</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">No. Plat</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tahun</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Status</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tarikh Daftar</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700 no-print">Tindakan</th>
        </tr>
       </thead>
       <tbody id="vehicles-table-body"><!-- Vehicle entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Analytics Section -->
   <div id="analytics-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">📊 Analitik Penggunaan Kenderaan</h2><!-- Filter Controls -->
     <div class="bg-gray-50 rounded-lg p-4 sm:p-6 mb-6 sm:mb-8 no-print">
      <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">🔍 Penapis Data</h3>
      <div class="form-grid lg:grid-cols-3">
       <div><label for="analytics-year" class="block text-sm font-medium text-gray-700 mb-2">Tahun</label> <select id="analytics-year" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm"> <option value="2024">2024</option> <option value="2023">2023</option> <option value="2022">2022</option> </select>
       </div>
       <div><label for="analytics-vehicle" class="block text-sm font-medium text-gray-700 mb-2">Kenderaan</label> <select id="analytics-vehicle" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm"> <option value="all">Semua Kenderaan</option> </select>
       </div>
       <div class="flex items-end"><button id="update-analytics" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors text-sm"> 📊 Kemas Kini Graf </button>
       </div>
      </div>
     </div><!-- Summary Cards -->
     <div class="card-grid mb-6 sm:mb-8">
      <div class="bg-gradient-to-r from-blue-500 to-blue-600 rounded-lg p-4 sm:p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-blue-100 text-xs sm:text-sm">Jumlah Tempahan</p>
         <p id="total-bookings" class="text-xl sm:text-2xl font-bold">0</p>
        </div>
        <div class="text-2xl sm:text-3xl">
         📋
        </div>
       </div>
      </div>
      <div class="bg-gradient-to-r from-green-500 to-green-600 rounded-lg p-4 sm:p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-green-100 text-xs sm:text-sm">Tempahan Selesai</p>
         <p id="completed-bookings" class="text-xl sm:text-2xl font-bold">0</p>
        </div>
        <div class="text-2xl sm:text-3xl">
         ✅
        </div>
       </div>
      </div>
      <div class="bg-gradient-to-r from-purple-500 to-purple-600 rounded-lg p-4 sm:p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-purple-100 text-xs sm:text-sm">Kenderaan Paling Popular</p>
         <p id="most-popular-vehicle" class="text-sm sm:text-lg font-bold">-</p>
        </div>
        <div class="text-2xl sm:text-3xl">
         🏆
        </div>
       </div>
      </div>
      <div class="bg-gradient-to-r from-orange-500 to-orange-600 rounded-lg p-4 sm:p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-orange-100 text-xs sm:text-sm">Purata Penggunaan/Bulan</p>
         <p id="average-usage" class="text-xl sm:text-2xl font-bold">0</p>
        </div>
        <div class="text-2xl sm:text-3xl">
         📈
        </div>
       </div>
      </div>
     </div><!-- Charts Container -->
     <div class="space-y-6 sm:space-y-8"><!-- Monthly Usage Chart -->
      <div class="bg-gray-50 rounded-lg p-4 sm:p-6">
       <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">📈 Penggunaan Bulanan</h3>
       <div class="chart-container">
        <canvas id="monthly-usage-chart" class="w-full h-full"></canvas>
       </div>
      </div><!-- Vehicle Comparison Chart -->
      <div class="bg-gray-50 rounded-lg p-4 sm:p-6">
       <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">🚗 Perbandingan Penggunaan Kenderaan</h3>
       <div class="chart-container">
        <canvas id="vehicle-comparison-chart" class="w-full h-full"></canvas>
       </div>
      </div><!-- Usage by Sector Chart -->
      <div class="bg-gray-50 rounded-lg p-4 sm:p-6">
       <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">🏢 Penggunaan Mengikut Sektor</h3>
       <div class="chart-container">
        <canvas id="sector-usage-chart" class="w-full h-full"></canvas>
       </div>
      </div>
     </div><!-- Detailed Statistics Table -->
     <div class="mt-6 sm:mt-8">
      <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">📋 Statistik Terperinci</h3>
      <div class="table-responsive">
       <table class="w-full table-auto min-w-full print-full-width">
        <thead>
         <tr class="bg-gray-50">
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Kenderaan</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Jumlah Tempahan</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Jam Penggunaan</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Sektor Terbanyak</th>
          <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Kadar Penggunaan</th>
         </tr>
        </thead>
        <tbody id="analytics-table-body"><!-- Analytics data will be populated here -->
        </tbody>
       </table>
      </div>
     </div>
    </div>
   </div><!-- User Management Section -->
   <div id="users-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 lg:p-8 fade-in">
     <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-4 sm:mb-6">👥 Pengurusan Pengguna</h2><!-- Add New User Form -->
     <div class="bg-gray-50 rounded-lg p-4 sm:p-6 mb-6 sm:mb-8 no-print">
      <h3 class="text-base sm:text-lg font-semibold text-gray-800 mb-4">➕ Tambah Pengguna Baru</h3>
      <form id="add-user-form" class="form-grid form-grid-xl">
       <div><label for="new-user-name" class="block text-sm font-medium text-gray-700 mb-2">Nama Penuh</label> <input type="text" id="new-user-name" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" placeholder="Nama pengguna" required>
       </div>
       <div><label for="new-user-email" class="block text-sm font-medium text-gray-700 mb-2">Email Rasmi</label> <input type="email" id="new-user-email" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" placeholder="contoh@moe.gov.my" required>
       </div>
       <div><label for="new-user-sector" class="block text-sm font-medium text-gray-700 mb-2">Sektor/Unit</label> <select id="new-user-sector" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" required> <option value="">Pilih sektor...</option> <option value="Sektor Perancangan">Sektor Perancangan</option> <option value="Sektor Pembelajaran">Sektor Pembelajaran</option> <option value="Sektor Pengurusan Sekolah">Sektor Pengurusan Sekolah</option> <option value="Sektor Pengurusan">Sektor Pengurusan</option> <option value="Sektor Pentaksiran dan Peperiksaan">Sektor Pentaksiran dan Peperiksaan</option> <option value="PTIS">PTIS</option> </select>
       </div>
       <div id="role-field"><label for="new-user-role" class="block text-sm font-medium text-gray-700 mb-2">Peranan</label> <select id="new-user-role" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-sm" required> <option value="">Pilih peranan...</option> <option value="Pegawai">Pegawai</option> <option value="Penyelia">Penyelia</option> <option value="Pengurus">Pengurus</option> <option value="Admin">Admin</option> </select>
       </div>
       <div class="flex items-end"><button type="submit" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors text-sm"> ➕ Tambah Pengguna </button>
       </div>
      </form>
     </div><!-- Users List -->
     <div class="table-responsive">
      <table class="w-full table-auto min-w-full print-full-width">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Nama</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Sektor/Unit</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Peranan</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Status</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700">Tarikh Daftar</th>
         <th class="px-2 sm:px-4 py-3 text-left text-xs sm:text-sm font-medium text-gray-700 no-print">Tindakan</th>
        </tr>
       </thead>
       <tbody id="users-table-body"><!-- User entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Success Messages -->
   <div id="success-message" class="hidden fixed top-4 right-4 bg-green-500 text-white px-4 sm:px-6 py-3 sm:py-4 rounded-lg shadow-lg z-50 text-sm sm:text-base">
    ✅ Tempahan berjaya dihantar!
   </div>
   <div id="user-success-message" class="hidden fixed top-4 right-4 bg-green-500 text-white px-4 sm:px-6 py-3 sm:py-4 rounded-lg shadow-lg z-50 text-sm sm:text-base">
    ✅ Pengguna berjaya ditambah!
   </div><!-- Loading Overlay -->
   <div id="loading-overlay" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
    <div class="bg-white rounded-lg p-6 flex items-center space-x-3">
     <div class="spinner"></div><span class="text-gray-700">Memproses...</span>
    </div>
   </div>
  </div><!-- JavaScript -->
  <script src="js/app.js"></script>
  <script src="js/auth.js"></script>
  <script src="js/booking.js"></script>
  <script src="js/management.js"></script>
  <script src="js/analytics.js"></script>
  <script src="js/utils.js"></script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'99e535bb63b7f004',t:'MTc2MzEwOTY4Ny4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
