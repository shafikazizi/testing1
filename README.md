<!doctype html>
<html lang="ms">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>eKenderaan</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
        body {
            box-sizing: border-box;
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="/_sdk/element_sdk.js" type="text/javascript"></script>
 </head>
 <body class="bg-gradient-to-br from-blue-50 to-indigo-100 min-h-screen"><!-- Login Section -->
  <div id="login-section" class="min-h-screen flex items-center justify-center px-4">
   <div class="bg-white rounded-xl shadow-lg p-8 w-full max-w-md">
    <div class="text-center mb-8">
     <h1 class="text-3xl font-bold text-gray-800 mb-2">🚗 eKenderaan</h1>
     <p class="text-gray-600">Sistem Pengurusan Kenderaan</p>
     <p class="text-gray-600">Pejabat Pendidikan Daerah Limbang</p>
    </div><!-- Login/Register Toggle -->
    <div class="flex mb-6 bg-gray-100 rounded-lg p-1"><button id="login-tab" class="flex-1 py-2 px-4 rounded-md font-medium transition-all bg-blue-600 text-white"> Log Masuk </button> <button id="register-tab" class="flex-1 py-2 px-4 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600"> Daftar Akaun </button>
    </div><!-- Login Form -->
    <div id="login-form-container">
     <form id="login-form" class="space-y-6">
      <div><label for="username" class="block text-sm font-medium text-gray-700 mb-2">Email Rasmi</label> <input type="email" id="username" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Masukkan email rasmi" required>
      </div>
      <div><label for="password" class="block text-sm font-medium text-gray-700 mb-2">Kata Laluan</label> <input type="password" id="password" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Masukkan kata laluan" required>
      </div><button type="submit" class="w-full bg-blue-600 text-white py-3 px-6 rounded-lg font-medium hover:bg-blue-700 transition-colors"> 🔐 Log Masuk </button>
     </form>
     <div class="mt-6 p-4 bg-gray-50 rounded-lg">
      <p class="text-sm text-gray-600 font-medium mb-3">Demo Login Credentials:</p>
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
     <form id="register-form" class="space-y-6">
      <div><label for="reg-fullname" class="block text-sm font-medium text-gray-700 mb-2">Nama Penuh</label> <input type="text" id="reg-fullname" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Masukkan nama penuh" required>
      </div>
      <div><label for="reg-email" class="block text-sm font-medium text-gray-700 mb-2">Email Rasmi</label> <input type="email" id="reg-email" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="contoh@moe.gov.my" required>
      </div>
      <div><label for="reg-sector" class="block text-sm font-medium text-gray-700 mb-2">Sektor/Unit</label> <select id="reg-sector" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required> <option value="">Pilih sektor/unit...</option> <option value="Sektor Perancangan">Sektor Perancangan</option> <option value="Sektor Pembelajaran">Sektor Pembelajaran</option> <option value="Sektor Pengurusan Sekolah">Sektor Pengurusan Sekolah</option> <option value="Sektor Pengurusan">Sektor Pengurusan</option> <option value="Sektor Pentaksiran dan Peperiksaan">Sektor Pentaksiran dan Peperiksaan</option> <option value="PTIS">PTIS</option> </select>
      </div>
      <div><label for="reg-password" class="block text-sm font-medium text-gray-700 mb-2">Kata Laluan</label> <input type="password" id="reg-password" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Cipta kata laluan" required>
      </div>
      <div><label for="reg-confirm-password" class="block text-sm font-medium text-gray-700 mb-2">Sahkan Kata Laluan</label> <input type="password" id="reg-confirm-password" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Sahkan kata laluan" required>
      </div><button type="submit" class="w-full bg-green-600 text-white py-3 px-6 rounded-lg font-medium hover:bg-green-700 transition-colors"> ✅ Daftar Akaun </button>
     </form>
    </div>
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
  <div id="main-app" class="hidden container mx-auto px-4 py-8"><!-- Header -->
   <header class="text-center mb-8">
    <div class="flex justify-between items-center mb-4">
     <div id="user-info" class="text-left">
      <p class="text-sm text-gray-600">Selamat datang,</p>
      <p id="current-user-display" class="font-semibold text-gray-800"></p>
      <p id="current-role-display" class="text-xs text-blue-600"></p>
     </div>
     <div class="text-center">
      <h1 class="text-4xl font-bold text-gray-800 mb-2">🚗 eKenderaan</h1>
      <p class="text-gray-600">Sistem Pengurusan Kenderaan</p>
      <p class="text-gray-600">Pejabat Pendidikan Daerah Limbang</p>
     </div><button id="logout-btn" class="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 transition-colors text-sm"> 🚪 Log Keluar </button>
    </div>
   </header><!-- Navigation Tabs -->
   <div class="flex justify-center mb-8">
    <div class="bg-white rounded-lg shadow-md p-1">
     <div class="flex flex-wrap justify-center gap-1"><button id="tab-booking" class="px-3 py-2 rounded-md font-medium transition-all bg-blue-600 text-white text-sm"> Tempahan Baru </button> <button id="tab-tracking" class="px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm"> Tracking Kenderaan </button> <button id="tab-schedule" class="px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm"> Jadual Pinjaman Kenderaan </button> <button id="tab-history" class="px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm"> Sejarah Pinjaman </button> <button id="tab-approval" class="px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm"> Kelulusan Tempahan </button> <!-- Management Dropdown -->
      <div class="relative" id="management-dropdown"><button id="management-dropdown-btn" class="px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm flex items-center"> Pengurusan 
        <svg class="w-3 h-3 ml-1 transition-transform" id="dropdown-arrow" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
        </svg></button>
       <div id="management-dropdown-menu" class="hidden absolute top-full left-0 mt-1 bg-white rounded-lg shadow-lg border border-gray-200 min-w-48 z-50 max-h-60 overflow-y-auto"><button id="tab-users" class="w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all rounded-t-lg text-sm"> 👥 Pengurusan Pengguna </button> <button id="tab-drivers" class="w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all text-sm"> 🚗 Pengurusan Pemandu </button> <button id="tab-vehicles" class="w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all rounded-b-lg text-sm"> 🚙 Pengurusan Kenderaan </button>
       </div>
      </div><button id="tab-analytics" class="px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm"> Analitik Penggunaan </button>
     </div>
    </div>
   </div><!-- Booking Form Section -->
   <div id="booking-section" class="max-w-2xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">📝 Borang Tempahan Kenderaan</h2>
     <form id="booking-form" class="space-y-6">
      <div class="grid md:grid-cols-2 gap-6">
       <div><label for="employee-name" class="block text-sm font-medium text-gray-700 mb-2">Nama Pegawai</label> <input type="text" id="employee-name" class="w-full px-4 py-3 border border-gray-300 rounded-lg bg-gray-50 text-gray-700" readonly>
       </div>
       <div><label for="employee-sector" class="block text-sm font-medium text-gray-700 mb-2">Sektor/Unit</label> <input type="text" id="employee-sector" class="w-full px-4 py-3 border border-gray-300 rounded-lg bg-gray-50 text-gray-700" readonly>
       </div>
      </div>
      <div class="hidden"><label class="block text-sm font-medium text-gray-700 mb-2">Kenderaan</label>
       <div class="w-full px-4 py-3 border border-gray-300 rounded-lg bg-gray-50 text-gray-600">
        Kenderaan akan ditentukan oleh admin semasa kelulusan
       </div><input type="hidden" id="car-select" value="Akan ditentukan oleh admin">
      </div>
      <div class="grid md:grid-cols-2 gap-6">
       <div><label for="start-date" class="block text-sm font-medium text-gray-700 mb-2">Tarikh Mula</label> <input type="date" id="start-date" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
       </div>
       <div><label for="start-time" class="block text-sm font-medium text-gray-700 mb-2">Masa Mula</label> <select id="start-time" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required> <option value="">Pilih masa...</option> <option value="07:00">07:00 AM</option> <option value="07:30">07:30 AM</option> <option value="08:00">08:00 AM</option> <option value="08:30">08:30 AM</option> <option value="09:00">09:00 AM</option> <option value="09:30">09:30 AM</option> <option value="10:00">10:00 AM</option> <option value="10:30">10:30 AM</option> <option value="11:00">11:00 AM</option> <option value="11:30">11:30 AM</option> <option value="12:00">12:00 PM</option> <option value="12:30">12:30 PM</option> <option value="13:00">01:00 PM</option> <option value="13:30">01:30 PM</option> <option value="14:00">02:00 PM</option> <option value="14:30">02:30 PM</option> <option value="15:00">03:00 PM</option> <option value="15:30">03:30 PM</option> <option value="16:00">04:00 PM</option> <option value="16:30">04:30 PM</option> <option value="17:00">05:00 PM</option> <option value="17:30">05:30 PM</option> <option value="18:00">06:00 PM</option> </select>
       </div>
      </div>
      <div class="grid md:grid-cols-2 gap-6">
       <div><label for="end-date" class="block text-sm font-medium text-gray-700 mb-2">Tarikh Tamat</label> <input type="date" id="end-date" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
       </div>
       <div><label for="end-time" class="block text-sm font-medium text-gray-700 mb-2">Masa Tamat</label> <select id="end-time" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required> <option value="">Pilih masa...</option> <option value="07:00">07:00 AM</option> <option value="07:30">07:30 AM</option> <option value="08:00">08:00 AM</option> <option value="08:30">08:30 AM</option> <option value="09:00">09:00 AM</option> <option value="09:30">09:30 AM</option> <option value="10:00">10:00 AM</option> <option value="10:30">10:30 AM</option> <option value="11:00">11:00 AM</option> <option value="11:30">11:30 AM</option> <option value="12:00">12:00 PM</option> <option value="12:30">12:30 PM</option> <option value="13:00">01:00 PM</option> <option value="13:30">01:30 PM</option> <option value="14:00">02:00 PM</option> <option value="14:30">02:30 PM</option> <option value="15:00">03:00 PM</option> <option value="15:30">03:30 PM</option> <option value="16:00">04:00 PM</option> <option value="16:30">04:30 PM</option> <option value="17:00">05:00 PM</option> <option value="17:30">05:30 PM</option> <option value="18:00">06:00 PM</option> </select>
       </div>
      </div>
      <div><label for="purpose" class="block text-sm font-medium text-gray-700 mb-2">Tujuan Penggunaan</label> <textarea id="purpose" rows="3" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Nyatakan tujuan penggunaan kereta..." required></textarea>
      </div><button type="submit" class="w-full bg-blue-600 text-white py-3 px-6 rounded-lg font-medium hover:bg-blue-700 transition-colors"> 🚗 Hantar Tempahan Kenderaan </button>
     </form>
    </div>
   </div><!-- Tracking Section -->
   <div id="tracking-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">📍 Status Kenderaan Masa Kini</h2>
     <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6" id="car-status-grid"><!-- Car status cards will be populated here -->
     </div>
    </div>
   </div><!-- Schedule Section -->
   <div id="schedule-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">📅 Jadual Pinjaman Kenderaan</h2><!-- Date Navigation -->
     <div class="flex items-center justify-between mb-6"><button id="prev-week" class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"> ← Minggu Sebelum </button>
      <h3 id="current-week" class="text-lg font-semibold text-gray-800"></h3><button id="next-week" class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"> Minggu Seterusnya → </button>
     </div><!-- Calendar Grid -->
     <div class="overflow-x-auto">
      <div class="min-w-full"><!-- Days Header -->
       <div class="grid grid-cols-8 gap-2 mb-4">
        <div class="font-semibold text-gray-700 p-3">
         Kenderaan
        </div>
        <div id="day-headers" class="col-span-7 grid grid-cols-7 gap-2"><!-- Day headers will be populated here -->
        </div>
       </div><!-- Car Schedule Grid -->
       <div id="schedule-grid" class="space-y-2"><!-- Schedule rows will be populated here -->
       </div>
      </div>
     </div><!-- Legend -->
     <div class="mt-6 flex flex-wrap gap-4 text-sm">
      <div class="flex items-center">
       <div class="w-4 h-4 bg-green-200 rounded mr-2"></div><span>Tersedia</span>
      </div>
      <div class="flex items-center">
       <div class="w-4 h-4 bg-blue-200 rounded mr-2"></div><span>Ditempah</span>
      </div>
      <div class="flex items-center">
       <div class="w-4 h-4 bg-red-200 rounded mr-2"></div><span>Sedang Digunakan</span>
      </div>
     </div>
    </div>
   </div><!-- History Section -->
   <div id="history-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">📋 Sejarah Pinjaman</h2>
     <div class="overflow-x-auto">
      <table class="w-full table-auto">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Nama</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Sektor/Unit</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Kenderaan</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Pemandu</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tarikh</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Status</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tujuan</th>
        </tr>
       </thead>
       <tbody id="history-table-body"><!-- History entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Approval Section -->
   <div id="approval-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">✅ Kelulusan Tempahan</h2><!-- Pending Approvals -->
     <div class="mb-8">
      <h3 class="text-lg font-semibold text-gray-800 mb-4">⏳ Tempahan Menunggu Kelulusan</h3>
      <div class="overflow-x-auto">
       <table class="w-full table-auto">
        <thead>
         <tr class="bg-yellow-50">
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Nama</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Sektor/Unit</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Kenderaan</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tarikh &amp; Masa</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tujuan</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tindakan</th>
         </tr>
        </thead>
        <tbody id="pending-approvals-body"><!-- Pending approvals will be populated here -->
        </tbody>
       </table>
      </div>
     </div><!-- Recent Decisions -->
     <div>
      <h3 class="text-lg font-semibold text-gray-800 mb-4">📋 Keputusan Terkini</h3>
      <div class="overflow-x-auto">
       <table class="w-full table-auto">
        <thead>
         <tr class="bg-gray-50">
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Nama</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Kenderaan</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tarikh</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Status</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Diluluskan Oleh</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Masa Keputusan</th>
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
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">🚗 Pengurusan Pemandu</h2><!-- Add New Driver Form -->
     <div class="bg-gray-50 rounded-lg p-6 mb-8">
      <h3 class="text-lg font-semibold text-gray-800 mb-4">➕ Tambah Pemandu Baru</h3>
      <form id="add-driver-form" class="grid md:grid-cols-2 lg:grid-cols-4 gap-4">
       <div><label for="new-driver-name" class="block text-sm font-medium text-gray-700 mb-2">Nama Penuh Pemandu</label> <input type="text" id="new-driver-name" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Encik Ahmad bin Ali" required>
       </div>
       <div><label for="new-driver-ic" class="block text-sm font-medium text-gray-700 mb-2">No. Kad Pengenalan</label> <input type="text" id="new-driver-ic" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="123456-12-1234" required>
       </div>
       <div><label for="new-driver-license" class="block text-sm font-medium text-gray-700 mb-2">No. Lesen Memandu</label> <input type="text" id="new-driver-license" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="D1234567" required>
       </div>
       <div class="flex items-end"><button type="submit" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors"> ➕ Tambah Pemandu </button>
       </div>
      </form>
     </div><!-- Drivers List -->
     <div class="overflow-x-auto">
      <table class="w-full table-auto">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Nama Pemandu</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">No. Kad Pengenalan</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">No. Lesen</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Status</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tarikh Daftar</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tindakan</th>
        </tr>
       </thead>
       <tbody id="drivers-table-body"><!-- Driver entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Vehicle Management Section -->
   <div id="vehicles-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">🚗 Pengurusan Kenderaan</h2><!-- Add New Vehicle Form -->
     <div class="bg-gray-50 rounded-lg p-6 mb-8">
      <h3 class="text-lg font-semibold text-gray-800 mb-4">➕ Tambah Kenderaan Baru</h3>
      <form id="add-vehicle-form" class="grid md:grid-cols-2 lg:grid-cols-5 gap-4">
       <div><label for="new-vehicle-brand" class="block text-sm font-medium text-gray-700 mb-2">Jenama</label> <select id="new-vehicle-brand" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required> <option value="">Pilih jenama...</option> <option value="Toyota">Toyota</option> <option value="Honda">Honda</option> <option value="Perodua">Perodua</option> <option value="Proton">Proton</option> <option value="Nissan">Nissan</option> <option value="Mazda">Mazda</option> <option value="Mitsubishi">Mitsubishi</option> </select>
       </div>
       <div><label for="new-vehicle-model" class="block text-sm font-medium text-gray-700 mb-2">Model</label> <input type="text" id="new-vehicle-model" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Contoh: Vios, City, Axia" required>
       </div>
       <div><label for="new-vehicle-plate" class="block text-sm font-medium text-gray-700 mb-2">No. Plat</label> <input type="text" id="new-vehicle-plate" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="ABC1234" required>
       </div>
       <div><label for="new-vehicle-year" class="block text-sm font-medium text-gray-700 mb-2">Tahun</label> <select id="new-vehicle-year" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required> <option value="">Pilih tahun...</option> <option value="2024">2024</option> <option value="2023">2023</option> <option value="2022">2022</option> <option value="2021">2021</option> <option value="2020">2020</option> <option value="2019">2019</option> <option value="2018">2018</option> <option value="2017">2017</option> <option value="2016">2016</option> <option value="2015">2015</option> </select>
       </div>
       <div class="flex items-end"><button type="submit" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors"> ➕ Tambah Kenderaan </button>
       </div>
      </form>
     </div><!-- Vehicles List -->
     <div class="overflow-x-auto">
      <table class="w-full table-auto">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Jenama &amp; Model</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">No. Plat</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tahun</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Status</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tarikh Daftar</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tindakan</th>
        </tr>
       </thead>
       <tbody id="vehicles-table-body"><!-- Vehicle entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Analytics Section -->
   <div id="analytics-section" class="hidden max-w-6xl mx-auto">
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">📊 Analitik Penggunaan Kenderaan</h2><!-- Filter Controls -->
     <div class="bg-gray-50 rounded-lg p-6 mb-8">
      <h3 class="text-lg font-semibold text-gray-800 mb-4">🔍 Penapis Data</h3>
      <div class="grid md:grid-cols-3 gap-4">
       <div><label for="analytics-year" class="block text-sm font-medium text-gray-700 mb-2">Tahun</label> <select id="analytics-year" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"> <option value="2024">2024</option> <option value="2023">2023</option> <option value="2022">2022</option> </select>
       </div>
       <div><label for="analytics-vehicle" class="block text-sm font-medium text-gray-700 mb-2">Kenderaan</label> <select id="analytics-vehicle" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"> <option value="all">Semua Kenderaan</option> </select>
       </div>
       <div class="flex items-end"><button id="update-analytics" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors"> 📊 Kemas Kini Graf </button>
       </div>
      </div>
     </div><!-- Summary Cards -->
     <div class="grid md:grid-cols-4 gap-6 mb-8">
      <div class="bg-gradient-to-r from-blue-500 to-blue-600 rounded-lg p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-blue-100 text-sm">Jumlah Tempahan</p>
         <p id="total-bookings" class="text-2xl font-bold">0</p>
        </div>
        <div class="text-3xl">
         📋
        </div>
       </div>
      </div>
      <div class="bg-gradient-to-r from-green-500 to-green-600 rounded-lg p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-green-100 text-sm">Tempahan Selesai</p>
         <p id="completed-bookings" class="text-2xl font-bold">0</p>
        </div>
        <div class="text-3xl">
         ✅
        </div>
       </div>
      </div>
      <div class="bg-gradient-to-r from-purple-500 to-purple-600 rounded-lg p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-purple-100 text-sm">Kenderaan Paling Popular</p>
         <p id="most-popular-vehicle" class="text-lg font-bold">-</p>
        </div>
        <div class="text-3xl">
         🏆
        </div>
       </div>
      </div>
      <div class="bg-gradient-to-r from-orange-500 to-orange-600 rounded-lg p-6 text-white">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-orange-100 text-sm">Purata Penggunaan/Bulan</p>
         <p id="average-usage" class="text-2xl font-bold">0</p>
        </div>
        <div class="text-3xl">
         📈
        </div>
       </div>
      </div>
     </div><!-- Charts Container -->
     <div class="space-y-8"><!-- Monthly Usage Chart -->
      <div class="bg-gray-50 rounded-lg p-6">
       <h3 class="text-lg font-semibold text-gray-800 mb-4">📈 Penggunaan Bulanan</h3>
       <div class="relative">
        <canvas id="monthly-usage-chart" width="800" height="400" class="w-full"></canvas>
       </div>
      </div><!-- Vehicle Comparison Chart -->
      <div class="bg-gray-50 rounded-lg p-6">
       <h3 class="text-lg font-semibold text-gray-800 mb-4">🚗 Perbandingan Penggunaan Kenderaan</h3>
       <div class="relative">
        <canvas id="vehicle-comparison-chart" width="800" height="400" class="w-full"></canvas>
       </div>
      </div><!-- Usage by Sector Chart -->
      <div class="bg-gray-50 rounded-lg p-6">
       <h3 class="text-lg font-semibold text-gray-800 mb-4">🏢 Penggunaan Mengikut Sektor</h3>
       <div class="relative">
        <canvas id="sector-usage-chart" width="800" height="400" class="w-full"></canvas>
       </div>
      </div>
     </div><!-- Detailed Statistics Table -->
     <div class="mt-8">
      <h3 class="text-lg font-semibold text-gray-800 mb-4">📋 Statistik Terperinci</h3>
      <div class="overflow-x-auto">
       <table class="w-full table-auto">
        <thead>
         <tr class="bg-gray-50">
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Kenderaan</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Jumlah Tempahan</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Jam Penggunaan</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Sektor Terbanyak</th>
          <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Kadar Penggunaan</th>
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
    <div class="bg-white rounded-xl shadow-lg p-8">
     <h2 class="text-2xl font-bold text-gray-800 mb-6">👥 Pengurusan Pengguna</h2><!-- Add New User Form -->
     <div class="bg-gray-50 rounded-lg p-6 mb-8">
      <h3 class="text-lg font-semibold text-gray-800 mb-4">➕ Tambah Pengguna Baru</h3>
      <form id="add-user-form" class="grid md:grid-cols-2 lg:grid-cols-5 gap-4">
       <div><label for="new-user-name" class="block text-sm font-medium text-gray-700 mb-2">Nama Penuh</label> <input type="text" id="new-user-name" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Nama pengguna" required>
       </div>
       <div><label for="new-user-email" class="block text-sm font-medium text-gray-700 mb-2">Email Rasmi</label> <input type="email" id="new-user-email" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="contoh@moe.gov.my" required>
       </div>
       <div><label for="new-user-sector" class="block text-sm font-medium text-gray-700 mb-2">Sektor/Unit</label> <select id="new-user-sector" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required> <option value="">Pilih sektor...</option> <option value="Sektor Perancangan">Sektor Perancangan</option> <option value="Sektor Pembelajaran">Sektor Pembelajaran</option> <option value="Sektor Pengurusan Sekolah">Sektor Pengurusan Sekolah</option> <option value="Sektor Pengurusan">Sektor Pengurusan</option> <option value="Sektor Pentaksiran dan Peperiksaan">Sektor Pentaksiran dan Peperiksaan</option> <option value="PTIS">PTIS</option> </select>
       </div>
       <div id="role-field"><label for="new-user-role" class="block text-sm font-medium text-gray-700 mb-2">Peranan</label> <select id="new-user-role" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required> <option value="">Pilih peranan...</option> <option value="Pegawai">Pegawai</option> <option value="Penyelia">Penyelia</option> <option value="Pengurus">Pengurus</option> <option value="Admin">Admin</option> </select>
       </div>
       <div class="flex items-end"><button type="submit" class="w-full bg-blue-600 text-white py-2 px-4 rounded-lg font-medium hover:bg-blue-700 transition-colors"> ➕ Tambah Pengguna </button>
       </div>
      </form>
     </div><!-- Users List -->
     <div class="overflow-x-auto">
      <table class="w-full table-auto">
       <thead>
        <tr class="bg-gray-50">
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Nama</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Sektor/Unit</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Peranan</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Status</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tarikh Daftar</th>
         <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Tindakan</th>
        </tr>
       </thead>
       <tbody id="users-table-body"><!-- User entries will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Success Message -->
   <div id="success-message" class="hidden fixed top-4 right-4 bg-green-500 text-white px-6 py-4 rounded-lg shadow-lg">
    ✅ Tempahan berjaya dihantar!
   </div><!-- User Success Message -->
   <div id="user-success-message" class="hidden fixed top-4 right-4 bg-green-500 text-white px-6 py-4 rounded-lg shadow-lg">
    ✅ Pengguna berjaya ditambah!
   </div>
  </div>
  <script>
        // Login credentials (demo purposes) - now using email as key
        let validCredentials = {
            'admin@moe.gov.my': 'admin123',
            'pegawai@moe.gov.my': 'pegawai123',
            'manager@moe.gov.my': 'manager123'
        };

        // Registered users data
        let registeredUsers = {};

        // Current user info
        let currentUserInfo = {
            username: '',
            role: 'Pegawai'
        };

        // Users data
        let users = [
            {
                id: 1,
                name: "Ahmad Rahman",
                email: "ahmad.rahman@moe.gov.my",
                sector: "Sektor Pengurusan",
                role: "Admin",
                status: "Aktif",
                dateRegistered: "2024-01-01"
            },
            {
                id: 2,
                name: "Siti Nurhaliza",
                email: "siti.nurhaliza@moe.gov.my",
                sector: "Sektor Pembelajaran",
                role: "Pengurus",
                status: "Aktif",
                dateRegistered: "2024-01-05"
            },
            {
                id: 3,
                name: "Ali Hassan",
                email: "ali.hassan@moe.gov.my",
                sector: "Sektor Perancangan",
                role: "Pegawai",
                status: "Aktif",
                dateRegistered: "2024-01-10"
            },
            {
                id: 4,
                name: "Fatimah Zahra",
                email: "fatimah.zahra@moe.gov.my",
                sector: "Sektor Pentaksiran dan Peperiksaan",
                role: "Penyelia",
                status: "Aktif",
                dateRegistered: "2024-01-12"
            }
        ];

        // Tab switching for login/register
        document.getElementById('login-tab').addEventListener('click', function() {
            // Show login form, hide register form
            document.getElementById('login-form-container').classList.remove('hidden');
            document.getElementById('register-form-container').classList.add('hidden');
            
            // Update tab styles
            this.className = 'flex-1 py-2 px-4 rounded-md font-medium transition-all bg-blue-600 text-white';
            document.getElementById('register-tab').className = 'flex-1 py-2 px-4 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600';
            
            // Hide messages
            hideAllMessages();
        });

        document.getElementById('register-tab').addEventListener('click', function() {
            // Show register form, hide login form
            document.getElementById('register-form-container').classList.remove('hidden');
            document.getElementById('login-form-container').classList.add('hidden');
            
            // Update tab styles
            this.className = 'flex-1 py-2 px-4 rounded-md font-medium transition-all bg-green-600 text-white';
            document.getElementById('login-tab').className = 'flex-1 py-2 px-4 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600';
            
            // Hide messages
            hideAllMessages();
        });

        function hideAllMessages() {
            document.getElementById('login-error').classList.add('hidden');
            document.getElementById('register-success').classList.add('hidden');
            document.getElementById('register-error').classList.add('hidden');
        }

        // Registration form handler
        document.getElementById('register-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const fullName = document.getElementById('reg-fullname').value;
            const email = document.getElementById('reg-email').value;
            const sector = document.getElementById('reg-sector').value;
            const password = document.getElementById('reg-password').value;
            const confirmPassword = document.getElementById('reg-confirm-password').value;
            
            const errorDiv = document.getElementById('register-error');
            const successDiv = document.getElementById('register-success');
            
            // Validation
            if (password !== confirmPassword) {
                errorDiv.textContent = 'Kata laluan tidak sepadan!';
                errorDiv.classList.remove('hidden');
                return;
            }
            
            // Check if email already exists
            const emailExists = Object.keys(validCredentials).includes(email) ||
                               Object.values(registeredUsers).some(user => user.email === email) ||
                               users.some(user => user.email === email);
            if (emailExists) {
                errorDiv.textContent = 'Email rasmi sudah didaftarkan! Sila gunakan email lain.';
                errorDiv.classList.remove('hidden');
                return;
            }
            
            if (password.length < 6) {
                errorDiv.textContent = 'Kata laluan mestilah sekurang-kurangnya 6 aksara!';
                errorDiv.classList.remove('hidden');
                return;
            }
            
            // Email validation
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailRegex.test(email)) {
                errorDiv.textContent = 'Format email rasmi tidak sah!';
                errorDiv.classList.remove('hidden');
                return;
            }
            
            // Register new user - use email as the key
            validCredentials[email] = password;
            registeredUsers[email] = {
                fullName: fullName,
                email: email,
                sector: sector,
                role: 'Pegawai',
                dateRegistered: new Date().toISOString().split('T')[0]
            };
            
            // Add to users list
            const newUser = {
                id: users.length + 1,
                name: fullName,
                email: email,
                sector: sector,
                role: 'Pegawai',
                status: 'Aktif',
                dateRegistered: new Date().toISOString().split('T')[0]
            };
            users.push(newUser);
            
            // Save data to localStorage
            saveDataToStorage();
            
            // Show success message
            successDiv.classList.remove('hidden');
            errorDiv.classList.add('hidden');
            
            // Reset form
            this.reset();
            
            // Switch to login tab after 2 seconds
            setTimeout(() => {
                document.getElementById('login-tab').click();
            }, 2000);
        });

        // Login form handler
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const email = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const errorDiv = document.getElementById('login-error');
            
            if (validCredentials[email] && validCredentials[email] === password) {
                // Successful login
                document.getElementById('login-section').classList.add('hidden');
                document.getElementById('main-app').classList.remove('hidden');
                
                // Store login status and user info
                sessionStorage.setItem('isLoggedIn', 'true');
                sessionStorage.setItem('currentUser', email);
                
                // Set current user info - admin email gets admin role
                currentUserInfo.username = email;
                currentUserInfo.role = email === 'admin@moe.gov.my' ? 'Admin' : 'Pegawai';
                
                // Initialize app
                updateCarStatusGrid();
                updateHistoryTable();
                updateScheduleView();
                updateUsersTable();
                updateDriversTable();
                updateVehiclesTable();
                updateApprovalTables();
                updateUIBasedOnRole();
                updateCarSelectDropdown();
            } else {
                // Show error
                errorDiv.classList.remove('hidden');
                setTimeout(() => errorDiv.classList.add('hidden'), 3000);
            }
        });

        // Logout handler
        document.getElementById('logout-btn').addEventListener('click', function() {
            sessionStorage.removeItem('isLoggedIn');
            sessionStorage.removeItem('currentUser');
            
            document.getElementById('main-app').classList.add('hidden');
            document.getElementById('login-section').classList.remove('hidden');
            
            // Reset form
            document.getElementById('login-form').reset();
        });

        // Load saved data from localStorage
        function loadSavedData() {
            try {
                // Load registered users
                const savedRegisteredUsers = localStorage.getItem('eKenderaan_registeredUsers');
                if (savedRegisteredUsers) {
                    const parsedUsers = JSON.parse(savedRegisteredUsers);
                    registeredUsers = { ...registeredUsers, ...parsedUsers };
                    
                    // Merge credentials
                    Object.entries(parsedUsers).forEach(([email, userData]) => {
                        if (!validCredentials[email]) {
                            validCredentials[email] = userData.password || 'defaultpass123';
                        }
                    });
                }

                // Load users array
                const savedUsers = localStorage.getItem('eKenderaan_users');
                if (savedUsers) {
                    const parsedUsersArray = JSON.parse(savedUsers);
                    // Merge with existing users, avoiding duplicates
                    parsedUsersArray.forEach(savedUser => {
                        const existingIndex = users.findIndex(u => u.email === savedUser.email);
                        if (existingIndex === -1) {
                            users.push(savedUser);
                        } else {
                            // Update existing user with saved data
                            users[existingIndex] = { ...users[existingIndex], ...savedUser };
                        }
                    });
                }

                // Load vehicles
                const savedVehicles = localStorage.getItem('eKenderaan_vehicles');
                if (savedVehicles) {
                    const parsedVehicles = JSON.parse(savedVehicles);
                    parsedVehicles.forEach(savedVehicle => {
                        const existingIndex = vehicles.findIndex(v => v.plate === savedVehicle.plate);
                        if (existingIndex === -1) {
                            vehicles.push(savedVehicle);
                        } else {
                            vehicles[existingIndex] = { ...vehicles[existingIndex], ...savedVehicle };
                        }
                    });
                }

                // Load drivers
                const savedDrivers = localStorage.getItem('eKenderaan_drivers');
                if (savedDrivers) {
                    const parsedDrivers = JSON.parse(savedDrivers);
                    parsedDrivers.forEach(savedDriver => {
                        const existingIndex = drivers.findIndex(d => d.ic === savedDriver.ic);
                        if (existingIndex === -1) {
                            drivers.push(savedDriver);
                        } else {
                            drivers[existingIndex] = { ...drivers[existingIndex], ...savedDriver };
                        }
                    });
                }

                // Load bookings
                const savedBookings = localStorage.getItem('eKenderaan_bookings');
                if (savedBookings) {
                    const parsedBookings = JSON.parse(savedBookings);
                    bookings = [...bookings, ...parsedBookings];
                }

                console.log('✅ Data tersimpan telah dimuatkan');
            } catch (error) {
                console.error('❌ Ralat memuatkan data tersimpan:', error);
            }
        }

        // Save data to localStorage
        function saveDataToStorage() {
            try {
                localStorage.setItem('eKenderaan_registeredUsers', JSON.stringify(registeredUsers));
                localStorage.setItem('eKenderaan_users', JSON.stringify(users));
                localStorage.setItem('eKenderaan_vehicles', JSON.stringify(vehicles));
                localStorage.setItem('eKenderaan_drivers', JSON.stringify(drivers));
                localStorage.setItem('eKenderaan_bookings', JSON.stringify(bookings));
                console.log('✅ Data telah disimpan');
            } catch (error) {
                console.error('❌ Ralat menyimpan data:', error);
            }
        }

        // Management dropdown functionality
        document.getElementById('management-dropdown-btn').addEventListener('click', function(e) {
            e.stopPropagation();
            const menu = document.getElementById('management-dropdown-menu');
            const arrow = document.getElementById('dropdown-arrow');
            
            if (menu.classList.contains('hidden')) {
                menu.classList.remove('hidden');
                arrow.style.transform = 'rotate(180deg)';
            } else {
                menu.classList.add('hidden');
                arrow.style.transform = 'rotate(0deg)';
            }
        });

        // Close dropdown when clicking outside
        document.addEventListener('click', function(e) {
            const dropdown = document.getElementById('management-dropdown');
            const menu = document.getElementById('management-dropdown-menu');
            const arrow = document.getElementById('dropdown-arrow');
            
            if (!dropdown.contains(e.target)) {
                menu.classList.add('hidden');
                arrow.style.transform = 'rotate(0deg)';
            }
        });

        // Check login status on page load
        window.addEventListener('load', function() {
            // Load saved data first
            loadSavedData();
            
            if (sessionStorage.getItem('isLoggedIn') === 'true') {
                const email = sessionStorage.getItem('currentUser');
                currentUserInfo.username = email;
                currentUserInfo.role = email === 'admin@moe.gov.my' ? 'Admin' : 'Pegawai';
                
                document.getElementById('login-section').classList.add('hidden');
                document.getElementById('main-app').classList.remove('hidden');
                updateCarStatusGrid();
                updateHistoryTable();
                updateScheduleView();
                updateUsersTable();
                updateDriversTable();
                updateVehiclesTable();
                updateApprovalTables();
                updateUIBasedOnRole();
                updateCarSelectDropdown();
            }
        });

        // Update UI based on user role
        function updateUIBasedOnRole() {
            const isAdmin = currentUserInfo.username === 'admin@moe.gov.my';
            
            // Update user display in header - show email
            document.getElementById('current-user-display').textContent = currentUserInfo.username;
            document.getElementById('current-role-display').textContent = `(${isAdmin ? 'Admin' : 'Pegawai'})`;
            
            // Show/hide admin-only tabs
            const approvalTab = document.getElementById('tab-approval');
            const managementDropdown = document.getElementById('management-dropdown');
            const analyticsTab = document.getElementById('tab-analytics');
            
            if (isAdmin) {
                approvalTab.style.display = 'inline-block';
                managementDropdown.style.display = 'block';
                analyticsTab.style.display = 'inline-block';
            } else {
                approvalTab.style.display = 'none';
                managementDropdown.style.display = 'none';
                analyticsTab.style.display = 'none';
                // If currently on admin tabs and not admin, switch to booking tab
                if (!document.getElementById('approval-section').classList.contains('hidden') || 
                    !document.getElementById('users-section').classList.contains('hidden') ||
                    !document.getElementById('drivers-section').classList.contains('hidden') ||
                    !document.getElementById('vehicles-section').classList.contains('hidden') ||
                    !document.getElementById('analytics-section').classList.contains('hidden')) {
                    switchTab('booking');
                }
            }
            
            // Show/hide role field in add user form
            const roleField = document.getElementById('role-field');
            if (isAdmin) {
                roleField.style.display = 'block';
            } else {
                roleField.style.display = 'none';
            }
            
            // Auto-fill booking form with current user info
            fillCurrentUserInfo();
        }

        // Function to auto-fill current user info in booking form
        function fillCurrentUserInfo() {
            const currentEmail = currentUserInfo.username;
            
            // Find current user info
            let currentUser = null;
            
            // Check in users array first by email
            currentUser = users.find(user => user.email.toLowerCase() === currentEmail.toLowerCase());
            
            // If not found, check in registered users
            if (!currentUser && registeredUsers[currentEmail]) {
                const regUser = registeredUsers[currentEmail];
                currentUser = {
                    name: regUser.fullName,
                    sector: regUser.sector
                };
            }
            
            // If still not found, use default based on email
            if (!currentUser) {
                if (currentEmail === 'admin@moe.gov.my') {
                    currentUser = {
                        name: 'Ahmad Rahman',
                        sector: 'Sektor Pengurusan'
                    };
                } else {
                    // Extract name from email and create generic entry
                    const emailName = currentEmail.split('@')[0].replace(/\./g, ' ');
                    currentUser = {
                        name: emailName.charAt(0).toUpperCase() + emailName.slice(1),
                        sector: 'Sektor Pengurusan'
                    };
                }
            }
            
            // Fill the form fields
            document.getElementById('employee-name').value = currentUser.name;
            document.getElementById('employee-sector').value = currentUser.sector;
        }



        // Vehicles data - managed by admin
        let vehicles = [
            {
                id: 1,
                brand: "Toyota",
                model: "Vios",
                plate: "ABC1234",
                year: "2022",
                status: "Aktif",
                dateRegistered: "2024-01-01"
            },
            {
                id: 2,
                brand: "Honda",
                model: "City",
                plate: "DEF5678",
                year: "2023",
                status: "Aktif",
                dateRegistered: "2024-01-02"
            },
            {
                id: 3,
                brand: "Perodua",
                model: "Axia",
                plate: "GHI9012",
                year: "2021",
                status: "Aktif",
                dateRegistered: "2024-01-03"
            },
            {
                id: 4,
                brand: "Proton",
                model: "Saga",
                plate: "JKL3456",
                year: "2020",
                status: "Aktif",
                dateRegistered: "2024-01-04"
            }
        ];

        // Function to get vehicle display name
        function getVehicleDisplayName(vehicle) {
            return `${vehicle.brand} ${vehicle.model} - ${vehicle.plate}`;
        }

        // Function to update car select dropdown
        function updateCarSelectDropdown() {
            const carSelect = document.getElementById('car-select');
            const activeVehicles = vehicles.filter(v => v.status === 'Aktif');
            
            // Clear existing options except the first one
            carSelect.innerHTML = '<option value="">Pilih kenderaan...</option>';
            
            // Add active vehicles
            activeVehicles.forEach(vehicle => {
                const option = document.createElement('option');
                option.value = getVehicleDisplayName(vehicle);
                option.textContent = getVehicleDisplayName(vehicle);
                carSelect.appendChild(option);
            });
        }

        // Drivers data - now managed by admin
        let drivers = [
            {
                id: 1,
                name: "Encik Rosli bin Ahmad",
                ic: "750123-12-1234",
                license: "D1234567",
                status: "Aktif",
                dateRegistered: "2024-01-01"
            },
            {
                id: 2,
                name: "Encik Baharuddin bin Hassan",
                ic: "680456-11-5678",
                license: "D2345678",
                status: "Aktif",
                dateRegistered: "2024-01-02"
            },
            {
                id: 3,
                name: "Encik Mohd Faiz bin Ibrahim",
                ic: "720789-10-9012",
                license: "D3456789",
                status: "Aktif",
                dateRegistered: "2024-01-03"
            },
            {
                id: 4,
                name: "Encik Razak bin Mahmud",
                ic: "650321-09-3456",
                license: "D4567890",
                status: "Aktif",
                dateRegistered: "2024-01-04"
            },
            {
                id: 5,
                name: "Encik Azman bin Yusof",
                ic: "770654-08-7890",
                license: "D5678901",
                status: "Aktif",
                dateRegistered: "2024-01-05"
            }
        ];

        // Get available drivers (active only)
        function getAvailableDrivers() {
            return drivers.filter(driver => driver.status === 'Aktif').map(driver => driver.name);
        }

        // Sample data
        let bookings = [
            {
                id: 1,
                employeeName: "Ahmad Rahman",
                employeeSector: "Sektor Pengurusan",
                car: "Toyota Vios - ABC1234",
                startDate: "2024-01-15T09:00",
                endDate: "2024-01-15T17:00",
                purpose: "Mesyuarat dengan klien",
                status: "Selesai",
                assignedDriver: "Encik Rosli bin Ahmad"
            },
            {
                id: 2,
                employeeName: "Siti Nurhaliza",
                employeeSector: "Sektor Pembelajaran",
                car: "Honda City - DEF5678",
                startDate: "2024-01-16T08:00",
                endDate: "2024-01-16T18:00",
                purpose: "Lawatan tapak projek",
                status: "Sedang Digunakan",
                assignedDriver: "Encik Baharuddin bin Hassan"
            },
            {
                id: 3,
                employeeName: "Ali Hassan",
                employeeSector: "Sektor Perancangan",
                car: "Akan ditentukan oleh admin",
                startDate: "2024-01-17T10:00",
                endDate: "2024-01-17T16:00",
                purpose: "Hantar dokumen",
                status: "Menunggu Kelulusan"
            },
            {
                id: 4,
                employeeName: "Fatimah Zahra",
                employeeSector: "Sektor Pentaksiran dan Peperiksaan",
                car: "Akan ditentukan oleh admin",
                startDate: "2024-01-18T14:00",
                endDate: "2024-01-19T12:00",
                purpose: "Perjalanan ke cawangan",
                status: "Menunggu Kelulusan"
            }
        ];

        // Approval decisions history
        let approvalDecisions = [
            {
                id: 1,
                employeeName: "Ahmad Rahman",
                car: "Toyota Vios - ABC1234",
                startDate: "2024-01-15T09:00",
                status: "Diluluskan",
                approvedBy: "admin",
                decidedAt: "2024-01-14T16:30:00"
            }
        ];

        let currentWeekStart = new Date();
        currentWeekStart.setDate(currentWeekStart.getDate() - currentWeekStart.getDay() + 1); // Start from Monday

        // Function to get current car list from vehicles data
        function getCurrentCarList() {
            return vehicles.filter(v => v.status === 'Aktif').map(v => getVehicleDisplayName(v));
        }

        // Function to initialize car statuses based on current vehicles
        function initializeCarStatuses() {
            const currentCars = getCurrentCarList();
            const newCarStatuses = {};
            
            currentCars.forEach(car => {
                // Keep existing status if available, otherwise set as available
                if (carStatuses[car]) {
                    newCarStatuses[car] = carStatuses[car];
                } else {
                    newCarStatuses[car] = { status: "Tersedia", user: null, returnTime: null };
                }
            });
            
            carStatuses = newCarStatuses;
        }

        let carStatuses = {
            "Toyota Vios - ABC1234": { status: "Tersedia", user: null, returnTime: null },
            "Honda City - DEF5678": { status: "Sedang Digunakan", user: "Siti Nurhaliza", returnTime: "18:00" },
            "Perodua Axia - GHI9012": { status: "Tersedia", user: null, returnTime: null },
            "Proton Saga - JKL3456": { status: "Tersedia", user: null, returnTime: null }
        };

        // Tab switching
        document.getElementById('tab-booking').addEventListener('click', () => switchTab('booking'));
        document.getElementById('tab-tracking').addEventListener('click', () => switchTab('tracking'));
        document.getElementById('tab-schedule').addEventListener('click', () => switchTab('schedule'));
        document.getElementById('tab-history').addEventListener('click', () => switchTab('history'));
        document.getElementById('tab-approval').addEventListener('click', () => switchTab('approval'));
        document.getElementById('tab-users').addEventListener('click', () => switchTab('users'));
        document.getElementById('tab-drivers').addEventListener('click', () => switchTab('drivers'));
        document.getElementById('tab-vehicles').addEventListener('click', () => switchTab('vehicles'));
        document.getElementById('tab-analytics').addEventListener('click', () => switchTab('analytics'));

        function switchTab(tab) {
            // Hide all sections
            document.getElementById('booking-section').classList.add('hidden');
            document.getElementById('tracking-section').classList.add('hidden');
            document.getElementById('schedule-section').classList.add('hidden');
            document.getElementById('history-section').classList.add('hidden');
            document.getElementById('approval-section').classList.add('hidden');
            document.getElementById('users-section').classList.add('hidden');
            document.getElementById('drivers-section').classList.add('hidden');
            document.getElementById('vehicles-section').classList.add('hidden');
            document.getElementById('analytics-section').classList.add('hidden');

            // Reset tab styles
            document.querySelectorAll('[id^="tab-"]').forEach(btn => {
                if (btn.id === 'tab-users' || btn.id === 'tab-drivers' || btn.id === 'tab-vehicles') {
                    // These are dropdown items, reset their styles
                    btn.className = 'w-full text-left px-4 py-3 text-gray-600 hover:bg-blue-50 hover:text-blue-600 transition-all text-sm';
                    if (btn.id === 'tab-users') btn.className += ' rounded-t-lg';
                    if (btn.id === 'tab-vehicles') btn.className += ' rounded-b-lg';
                } else {
                    // Regular tabs
                    btn.className = 'px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm';
                }
            });

            // Reset management dropdown button style
            const managementBtn = document.getElementById('management-dropdown-btn');
            managementBtn.className = 'px-3 py-2 rounded-md font-medium transition-all text-gray-600 hover:text-blue-600 text-sm flex items-center';

            // Show selected section and highlight appropriate tab
            document.getElementById(`${tab}-section`).classList.remove('hidden');
            
            if (tab === 'users' || tab === 'drivers' || tab === 'vehicles') {
                // Highlight management dropdown button for management tabs
                managementBtn.className = 'px-3 py-2 rounded-md font-medium transition-all bg-blue-600 text-white text-sm flex items-center';
                
                // Highlight the specific dropdown item
                const selectedTab = document.getElementById(`tab-${tab}`);
                if (tab === 'users') {
                    selectedTab.className = 'w-full text-left px-4 py-3 bg-blue-600 text-white transition-all rounded-t-lg text-sm';
                } else if (tab === 'vehicles') {
                    selectedTab.className = 'w-full text-left px-4 py-3 bg-blue-600 text-white transition-all rounded-b-lg text-sm';
                } else {
                    selectedTab.className = 'w-full text-left px-4 py-3 bg-blue-600 text-white transition-all text-sm';
                }
                
                // Close dropdown after selection
                const menu = document.getElementById('management-dropdown-menu');
                const arrow = document.getElementById('dropdown-arrow');
                menu.classList.add('hidden');
                arrow.style.transform = 'rotate(0deg)';
            } else {
                // Regular tab highlighting
                document.getElementById(`tab-${tab}`).className = 'px-3 py-2 rounded-md font-medium transition-all bg-blue-600 text-white text-sm';
            }

            if (tab === 'tracking') {
                updateCarStatusGrid();
            } else if (tab === 'schedule') {
                updateScheduleView();
            } else if (tab === 'history') {
                updateHistoryTable();
            } else if (tab === 'approval') {
                updateApprovalTables();
            } else if (tab === 'users') {
                updateUsersTable();
            } else if (tab === 'drivers') {
                updateDriversTable();
            } else if (tab === 'vehicles') {
                updateVehiclesTable();
            } else if (tab === 'analytics') {
                updateAnalyticsView();
            }
        }

        // Add Vehicle Form submission
        document.getElementById('add-vehicle-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Only admin can add vehicles
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh menambah kenderaan!', 'error');
                return;
            }
            
            const newVehicleBrand = document.getElementById('new-vehicle-brand').value;
            const newVehicleModel = document.getElementById('new-vehicle-model').value;
            const newVehiclePlate = document.getElementById('new-vehicle-plate').value.toUpperCase();
            const newVehicleYear = document.getElementById('new-vehicle-year').value;
            
            // Check if plate number already exists
            const plateExists = vehicles.some(vehicle => vehicle.plate === newVehiclePlate);
            
            if (plateExists) {
                showNotification('No. Plat sudah didaftarkan!', 'error');
                return;
            }
            
            // Plate validation (basic format check)
            const plateRegex = /^[A-Z]{1,3}\d{1,4}[A-Z]?$/;
            if (!plateRegex.test(newVehiclePlate)) {
                showNotification('Format No. Plat tidak sah! (Contoh: ABC1234, A123B)', 'error');
                return;
            }
            
            const newVehicle = {
                id: vehicles.length + 1,
                brand: newVehicleBrand,
                model: newVehicleModel,
                plate: newVehiclePlate,
                year: newVehicleYear,
                status: "Aktif",
                dateRegistered: new Date().toISOString().split('T')[0]
            };

            vehicles.push(newVehicle);
            updateVehiclesTable();
            updateCarSelectDropdown();
            
            // Save data to localStorage
            saveDataToStorage();
            
            // Show success message
            showNotification('✅ Kenderaan berjaya ditambah!', 'success');

            // Reset form
            this.reset();
        });

        // Add Driver Form submission
        document.getElementById('add-driver-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Only admin can add drivers
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh menambah pemandu!', 'error');
                return;
            }
            
            const newDriverName = document.getElementById('new-driver-name').value;
            const newDriverIC = document.getElementById('new-driver-ic').value;
            const newDriverLicense = document.getElementById('new-driver-license').value;
            
            // Check if IC or license already exists
            const icExists = drivers.some(driver => driver.ic === newDriverIC);
            const licenseExists = drivers.some(driver => driver.license === newDriverLicense);
            
            if (icExists) {
                showNotification('No. Kad Pengenalan sudah didaftarkan!', 'error');
                return;
            }
            
            if (licenseExists) {
                showNotification('No. Lesen Memandu sudah didaftarkan!', 'error');
                return;
            }
            
            // IC validation (basic format check)
            const icRegex = /^\d{6}-\d{2}-\d{4}$/;
            if (!icRegex.test(newDriverIC)) {
                showNotification('Format No. Kad Pengenalan tidak sah! (Contoh: 123456-12-1234)', 'error');
                return;
            }
            
            const newDriver = {
                id: drivers.length + 1,
                name: newDriverName,
                ic: newDriverIC,
                license: newDriverLicense,
                status: "Aktif",
                dateRegistered: new Date().toISOString().split('T')[0]
            };

            drivers.push(newDriver);
            updateDriversTable();
            
            // Save data to localStorage
            saveDataToStorage();
            
            // Show success message
            showNotification('✅ Pemandu berjaya ditambah!', 'success');

            // Reset form
            this.reset();
        });

        // Add User Form submission
        document.getElementById('add-user-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Only admin can add users
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh menambah pengguna!', 'error');
                return;
            }
            
            const newUserName = document.getElementById('new-user-name').value;
            const newUserEmail = document.getElementById('new-user-email').value;
            const newUserSector = document.getElementById('new-user-sector').value;
            const selectedRole = document.getElementById('new-user-role').value;
            
            // Check if email already exists
            const emailExists = users.some(user => user.email === newUserEmail) ||
                               Object.values(registeredUsers).some(user => user.email === newUserEmail);
            if (emailExists) {
                showNotification('Email rasmi sudah didaftarkan! Sila gunakan email lain.', 'error');
                return;
            }
            
            // Email validation
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailRegex.test(newUserEmail)) {
                showNotification('Format email rasmi tidak sah!', 'error');
                return;
            }
            
            const newUser = {
                id: users.length + 1,
                name: newUserName,
                email: newUserEmail,
                sector: newUserSector,
                role: selectedRole,
                status: "Aktif",
                dateRegistered: new Date().toISOString().split('T')[0]
            };

            users.push(newUser);
            updateUsersTable();
            
            // Save data to localStorage
            saveDataToStorage();
            
            // Show success message
            const successMsg = document.getElementById('user-success-message');
            successMsg.classList.remove('hidden');
            setTimeout(() => successMsg.classList.add('hidden'), 3000);

            // Reset form
            this.reset();
        });

        // Form submission
        document.getElementById('booking-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const startDate = document.getElementById('start-date').value;
            const startTime = document.getElementById('start-time').value;
            const endDate = document.getElementById('end-date').value;
            const endTime = document.getElementById('end-time').value;
            
            const formData = {
                id: bookings.length + 1,
                employeeName: document.getElementById('employee-name').value,
                employeeSector: document.getElementById('employee-sector').value,
                car: document.getElementById('car-select').value,
                startDate: `${startDate}T${startTime}`,
                endDate: `${endDate}T${endTime}`,
                purpose: document.getElementById('purpose').value,
                status: "Menunggu Kelulusan"
            };

            bookings.push(formData);
            
            // Update car status
            carStatuses[formData.car] = {
                status: "Ditempah",
                user: formData.employeeName,
                returnTime: new Date(formData.endDate).toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'})
            };

            // Save data to localStorage
            saveDataToStorage();

            // Show success message
            const successMsg = document.getElementById('success-message');
            successMsg.classList.remove('hidden');
            setTimeout(() => successMsg.classList.add('hidden'), 3000);

            // Reset form
            this.reset();
        });

        function updateVehiclesTable() {
            const tbody = document.getElementById('vehicles-table-body');
            tbody.innerHTML = '';

            vehicles.forEach(vehicle => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-200 hover:bg-gray-50';
                
                const statusColor = vehicle.status === 'Aktif' ? 'text-green-600' : 'text-red-600';
                const formattedDate = new Date(vehicle.dateRegistered).toLocaleDateString('ms-MY');
                
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm text-gray-900">${vehicle.brand} ${vehicle.model}</td>
                    <td class="px-4 py-3 text-sm text-gray-900 font-medium">${vehicle.plate}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${vehicle.year}</td>
                    <td class="px-4 py-3 text-sm font-medium ${statusColor}">${vehicle.status}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${formattedDate}</td>
                    <td class="px-4 py-3 text-sm">
                        <div class="flex space-x-2">
                            <button onclick="editVehicle(${vehicle.id})" class="text-blue-600 hover:text-blue-800 font-medium">Edit</button>
                            <button onclick="toggleVehicleStatus(${vehicle.id})" class="text-yellow-600 hover:text-yellow-800 font-medium">
                                ${vehicle.status === 'Aktif' ? 'Nyahaktif' : 'Aktifkan'}
                            </button>
                            <button onclick="deleteVehicle(${vehicle.id})" class="text-red-600 hover:text-red-800 font-medium">Padam</button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateDriversTable() {
            const tbody = document.getElementById('drivers-table-body');
            tbody.innerHTML = '';

            drivers.forEach(driver => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-200 hover:bg-gray-50';
                
                const statusColor = driver.status === 'Aktif' ? 'text-green-600' : 'text-red-600';
                const formattedDate = new Date(driver.dateRegistered).toLocaleDateString('ms-MY');
                
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm text-gray-900">${driver.name}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${driver.ic}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${driver.license}</td>
                    <td class="px-4 py-3 text-sm font-medium ${statusColor}">${driver.status}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${formattedDate}</td>
                    <td class="px-4 py-3 text-sm">
                        <div class="flex space-x-2">
                            <button onclick="editDriver(${driver.id})" class="text-blue-600 hover:text-blue-800 font-medium">Edit</button>
                            <button onclick="toggleDriverStatus(${driver.id})" class="text-yellow-600 hover:text-yellow-800 font-medium">
                                ${driver.status === 'Aktif' ? 'Nyahaktif' : 'Aktifkan'}
                            </button>
                            <button onclick="deleteDriver(${driver.id})" class="text-red-600 hover:text-red-800 font-medium">Padam</button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateUsersTable() {
            const tbody = document.getElementById('users-table-body');
            tbody.innerHTML = '';

            users.forEach(user => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-200 hover:bg-gray-50';
                
                const statusColor = user.status === 'Aktif' ? 'text-green-600' : 'text-red-600';
                const formattedDate = new Date(user.dateRegistered).toLocaleDateString('ms-MY');
                
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm text-gray-900">${user.name}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${user.sector}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${user.role}</td>
                    <td class="px-4 py-3 text-sm font-medium ${statusColor}">${user.status}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${formattedDate}</td>
                    <td class="px-4 py-3 text-sm">
                        <div class="flex space-x-2">
                            <button onclick="editUser(${user.id})" class="text-blue-600 hover:text-blue-800 font-medium">Edit</button>
                            <button onclick="toggleUserStatus(${user.id})" class="text-yellow-600 hover:text-yellow-800 font-medium">
                                ${user.status === 'Aktif' ? 'Nyahaktif' : 'Aktifkan'}
                            </button>
                            <button onclick="deleteUser(${user.id})" class="text-red-600 hover:text-red-800 font-medium">Padam</button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function editUser(userId) {
            // Only admin can edit users
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh mengedit pengguna!', 'error');
                return;
            }
            
            const user = users.find(u => u.id === userId);
            if (!user) return;

            // Create edit user modal
            const modal = document.createElement('div');
            modal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4';
            modal.innerHTML = `
                <div class="bg-white rounded-lg max-w-md w-full">
                    <div class="p-6">
                        <div class="text-center mb-6">
                            <div class="text-blue-600 text-4xl mb-4">👤</div>
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Edit Pengguna</h3>
                            <p class="text-gray-600 text-sm">Kemaskini maklumat pengguna</p>
                        </div>
                        
                        <div class="space-y-4">
                            <div>
                                <label for="edit-user-name" class="block text-sm font-medium text-gray-700 mb-2">Nama Penuh</label>
                                <input type="text" id="edit-user-name" value="${user.name}" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
                            </div>
                            
                            <div>
                                <label for="edit-user-email" class="block text-sm font-medium text-gray-700 mb-2">Email Rasmi</label>
                                <input type="email" id="edit-user-email" value="${user.email}" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
                            </div>
                            
                            <div>
                                <label for="edit-user-sector" class="block text-sm font-medium text-gray-700 mb-2">Sektor/Unit</label>
                                <select id="edit-user-sector" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
                                    <option value="Sektor Perancangan" ${user.sector === 'Sektor Perancangan' ? 'selected' : ''}>Sektor Perancangan</option>
                                    <option value="Sektor Pembelajaran" ${user.sector === 'Sektor Pembelajaran' ? 'selected' : ''}>Sektor Pembelajaran</option>
                                    <option value="Sektor Pengurusan Sekolah" ${user.sector === 'Sektor Pengurusan Sekolah' ? 'selected' : ''}>Sektor Pengurusan Sekolah</option>
                                    <option value="Sektor Pengurusan" ${user.sector === 'Sektor Pengurusan' ? 'selected' : ''}>Sektor Pengurusan</option>
                                    <option value="Sektor Pentaksiran dan Peperiksaan" ${user.sector === 'Sektor Pentaksiran dan Peperiksaan' ? 'selected' : ''}>Sektor Pentaksiran dan Peperiksaan</option>
                                    <option value="PTIS" ${user.sector === 'PTIS' ? 'selected' : ''}>PTIS</option>
                                </select>
                            </div>
                            
                            <div>
                                <label for="edit-user-role" class="block text-sm font-medium text-gray-700 mb-2">Peranan</label>
                                <select id="edit-user-role" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
                                    <option value="Pegawai" ${user.role === 'Pegawai' ? 'selected' : ''}>Pegawai</option>
                                    <option value="Penyelia" ${user.role === 'Penyelia' ? 'selected' : ''}>Penyelia</option>
                                    <option value="Pengurus" ${user.role === 'Pengurus' ? 'selected' : ''}>Pengurus</option>
                                    <option value="Admin" ${user.role === 'Admin' ? 'selected' : ''}>Admin</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="flex space-x-3 justify-center mt-6">
                            <button id="save-user-changes" class="px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 font-medium">
                                ✅ Simpan Perubahan
                            </button>
                            <button id="cancel-user-edit" class="px-6 py-2 bg-gray-300 text-gray-700 rounded-lg hover:bg-gray-400 font-medium">
                                Batal
                            </button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(modal);
            
            // Handle save changes
            document.getElementById('save-user-changes').addEventListener('click', function() {
                const newName = document.getElementById('edit-user-name').value.trim();
                const newEmail = document.getElementById('edit-user-email').value.trim();
                const newSector = document.getElementById('edit-user-sector').value;
                const newRole = document.getElementById('edit-user-role').value;
                
                if (!newName || !newEmail || !newSector || !newRole) {
                    showNotification('Sila lengkapkan semua maklumat!', 'error');
                    return;
                }
                
                // Check if email already exists (excluding current user)
                const emailExists = users.some(u => u.id !== userId && u.email === newEmail) ||
                                   Object.values(registeredUsers).some(u => u.email === newEmail);
                if (emailExists) {
                    showNotification('Email rasmi sudah digunakan oleh pengguna lain!', 'error');
                    return;
                }
                
                // Email validation
                const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
                if (!emailRegex.test(newEmail)) {
                    showNotification('Format email rasmi tidak sah!', 'error');
                    return;
                }
                
                // Update user data
                const oldRole = user.role;
                user.name = newName;
                user.email = newEmail;
                user.sector = newSector;
                user.role = newRole;
                
                updateUsersTable();
                saveDataToStorage();
                
                // Show success message with role change notification
                if (oldRole !== newRole) {
                    showNotification(`✅ Pengguna dikemas kini! Peranan berubah dari ${oldRole} kepada ${newRole}.`, 'success');
                } else {
                    showNotification('✅ Maklumat pengguna telah dikemas kini!', 'success');
                }
                
                document.body.removeChild(modal);
            });
            
            // Handle cancellation
            document.getElementById('cancel-user-edit').addEventListener('click', function() {
                document.body.removeChild(modal);
            });
            
            // Close on backdrop click
            modal.addEventListener('click', function(e) {
                if (e.target === modal) {
                    document.body.removeChild(modal);
                }
            });
        }

        function toggleUserStatus(userId) {
            // Only admin can toggle user status
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh mengubah status pengguna!', 'error');
                return;
            }
            
            const user = users.find(u => u.id === userId);
            if (user) {
                user.status = user.status === 'Aktif' ? 'Tidak Aktif' : 'Aktif';
                updateUsersTable();
                saveDataToStorage();
            }
        }

        function editDriver(driverId) {
            // Only admin can edit drivers
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh mengedit pemandu!', 'error');
                return;
            }
            
            const driver = drivers.find(d => d.id === driverId);
            if (driver) {
                const newName = prompt('Masukkan nama baru:', driver.name);
                if (newName && newName.trim()) {
                    driver.name = newName.trim();
                    updateDriversTable();
                    saveDataToStorage();
                    showNotification('✅ Nama pemandu telah dikemas kini!', 'success');
                }
            }
        }

        function toggleDriverStatus(driverId) {
            // Only admin can toggle driver status
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh mengubah status pemandu!', 'error');
                return;
            }
            
            const driver = drivers.find(d => d.id === driverId);
            if (driver) {
                driver.status = driver.status === 'Aktif' ? 'Tidak Aktif' : 'Aktif';
                updateDriversTable();
                saveDataToStorage();
                showNotification(`✅ Status pemandu telah dikemas kini kepada ${driver.status}!`, 'success');
            }
        }

        function editVehicle(vehicleId) {
            // Only admin can edit vehicles
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh mengedit kenderaan!', 'error');
                return;
            }
            
            const vehicle = vehicles.find(v => v.id === vehicleId);
            if (vehicle) {
                const newModel = prompt('Masukkan model baru:', vehicle.model);
                if (newModel && newModel.trim()) {
                    vehicle.model = newModel.trim();
                    updateVehiclesTable();
                    updateCarSelectDropdown();
                    saveDataToStorage();
                    showNotification('✅ Model kenderaan telah dikemas kini!', 'success');
                }
            }
        }

        function toggleVehicleStatus(vehicleId) {
            // Only admin can toggle vehicle status
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh mengubah status kenderaan!', 'error');
                return;
            }
            
            const vehicle = vehicles.find(v => v.id === vehicleId);
            if (vehicle) {
                vehicle.status = vehicle.status === 'Aktif' ? 'Tidak Aktif' : 'Aktif';
                updateVehiclesTable();
                updateCarSelectDropdown();
                saveDataToStorage();
                showNotification(`✅ Status kenderaan telah dikemas kini kepada ${vehicle.status}!`, 'success');
            }
        }

        function deleteVehicle(vehicleId) {
            // Only admin can delete vehicles
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh memadam kenderaan!', 'error');
                return;
            }
            
            const vehicle = vehicles.find(v => v.id === vehicleId);
            if (!vehicle) return;
            
            // Check if vehicle is currently in use
            const vehicleDisplayName = getVehicleDisplayName(vehicle);
            const isInUse = bookings.some(booking => 
                booking.car === vehicleDisplayName && 
                (booking.status === 'Sedang Digunakan' || booking.status === 'Ditempah' || booking.status === 'Diluluskan')
            );
            
            if (isInUse) {
                showNotification('Kenderaan tidak boleh dipadam kerana sedang digunakan atau ditempah!', 'error');
                return;
            }
            
            // Create custom confirmation dialog
            const confirmDialog = document.createElement('div');
            confirmDialog.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
            confirmDialog.innerHTML = `
                <div class="bg-white rounded-lg p-6 max-w-md mx-4">
                    <div class="text-center">
                        <div class="text-red-600 text-4xl mb-4">⚠️</div>
                        <h3 class="text-lg font-semibold text-gray-800 mb-2">Padam Kenderaan</h3>
                        <p class="text-gray-600 mb-6">Adakah anda pasti ingin memadam kenderaan <strong>${vehicle.brand} ${vehicle.model} - ${vehicle.plate}</strong>?</p>
                        <p class="text-sm text-red-600 mb-6">Tindakan ini tidak boleh dibatalkan!</p>
                        <div class="flex space-x-3 justify-center">
                            <button id="confirm-delete-vehicle" class="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 font-medium">
                                Ya, Padam
                            </button>
                            <button id="cancel-delete-vehicle" class="px-4 py-2 bg-gray-300 text-gray-700 rounded-lg hover:bg-gray-400 font-medium">
                                Batal
                            </button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(confirmDialog);
            
            // Handle confirmation
            document.getElementById('confirm-delete-vehicle').addEventListener('click', function() {
                // Remove vehicle from array
                const vehicleIndex = vehicles.findIndex(v => v.id === vehicleId);
                if (vehicleIndex > -1) {
                    vehicles.splice(vehicleIndex, 1);
                    updateVehiclesTable();
                    updateCarSelectDropdown();
                    saveDataToStorage();
                    showNotification(`✅ Kenderaan ${vehicle.brand} ${vehicle.model} - ${vehicle.plate} telah dipadam!`, 'success');
                }
                document.body.removeChild(confirmDialog);
            });
            
            // Handle cancellation
            document.getElementById('cancel-delete-vehicle').addEventListener('click', function() {
                document.body.removeChild(confirmDialog);
            });
            
            // Close on backdrop click
            confirmDialog.addEventListener('click', function(e) {
                if (e.target === confirmDialog) {
                    document.body.removeChild(confirmDialog);
                }
            });
        }

        function deleteDriver(driverId) {
            // Only admin can delete drivers
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh memadam pemandu!', 'error');
                return;
            }
            
            const driver = drivers.find(d => d.id === driverId);
            if (!driver) return;
            
            // Create custom confirmation dialog
            const confirmDialog = document.createElement('div');
            confirmDialog.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
            confirmDialog.innerHTML = `
                <div class="bg-white rounded-lg p-6 max-w-md mx-4">
                    <div class="text-center">
                        <div class="text-red-600 text-4xl mb-4">⚠️</div>
                        <h3 class="text-lg font-semibold text-gray-800 mb-2">Padam Pemandu</h3>
                        <p class="text-gray-600 mb-6">Adakah anda pasti ingin memadam pemandu <strong>${driver.name}</strong>?</p>
                        <p class="text-sm text-red-600 mb-6">Tindakan ini tidak boleh dibatalkan!</p>
                        <div class="flex space-x-3 justify-center">
                            <button id="confirm-delete-driver" class="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 font-medium">
                                Ya, Padam
                            </button>
                            <button id="cancel-delete-driver" class="px-4 py-2 bg-gray-300 text-gray-700 rounded-lg hover:bg-gray-400 font-medium">
                                Batal
                            </button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(confirmDialog);
            
            // Handle confirmation
            document.getElementById('confirm-delete-driver').addEventListener('click', function() {
                // Remove driver from array
                const driverIndex = drivers.findIndex(d => d.id === driverId);
                if (driverIndex > -1) {
                    drivers.splice(driverIndex, 1);
                    updateDriversTable();
                    saveDataToStorage();
                    showNotification(`✅ Pemandu ${driver.name} telah dipadam!`, 'success');
                }
                document.body.removeChild(confirmDialog);
            });
            
            // Handle cancellation
            document.getElementById('cancel-delete-driver').addEventListener('click', function() {
                document.body.removeChild(confirmDialog);
            });
            
            // Close on backdrop click
            confirmDialog.addEventListener('click', function(e) {
                if (e.target === confirmDialog) {
                    document.body.removeChild(confirmDialog);
                }
            });
        }

        function deleteUser(userId) {
            // Only admin can delete users
            if (currentUserInfo.username !== 'admin@moe.gov.my') {
                showNotification('Hanya admin yang boleh memadam pengguna!', 'error');
                return;
            }
            
            const user = users.find(u => u.id === userId);
            if (!user) return;
            
            // Create custom confirmation dialog
            const confirmDialog = document.createElement('div');
            confirmDialog.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
            confirmDialog.innerHTML = `
                <div class="bg-white rounded-lg p-6 max-w-md mx-4">
                    <div class="text-center">
                        <div class="text-red-600 text-4xl mb-4">⚠️</div>
                        <h3 class="text-lg font-semibold text-gray-800 mb-2">Padam Pengguna</h3>
                        <p class="text-gray-600 mb-6">Adakah anda pasti ingin memadam pengguna <strong>${user.name}</strong>?</p>
                        <p class="text-sm text-red-600 mb-6">Tindakan ini tidak boleh dibatalkan!</p>
                        <div class="flex space-x-3 justify-center">
                            <button id="confirm-delete" class="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 font-medium">
                                Ya, Padam
                            </button>
                            <button id="cancel-delete" class="px-4 py-2 bg-gray-300 text-gray-700 rounded-lg hover:bg-gray-400 font-medium">
                                Batal
                            </button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(confirmDialog);
            
            // Handle confirmation
            document.getElementById('confirm-delete').addEventListener('click', function() {
                // Remove user from array
                const userIndex = users.findIndex(u => u.id === userId);
                if (userIndex > -1) {
                    users.splice(userIndex, 1);
                    updateUsersTable();
                    saveDataToStorage();
                    showNotification(`✅ Pengguna ${user.name} telah dipadam!`, 'success');
                }
                document.body.removeChild(confirmDialog);
            });
            
            // Handle cancellation
            document.getElementById('cancel-delete').addEventListener('click', function() {
                document.body.removeChild(confirmDialog);
            });
            
            // Close on backdrop click
            confirmDialog.addEventListener('click', function(e) {
                if (e.target === confirmDialog) {
                    document.body.removeChild(confirmDialog);
                }
            });
        }

        function updateCarStatusGrid() {
            const grid = document.getElementById('car-status-grid');
            grid.innerHTML = '';

            Object.entries(carStatuses).forEach(([car, info]) => {
                const statusColor = info.status === 'Tersedia' ? 'bg-green-100 text-green-800' : 
                                  info.status === 'Sedang Digunakan' ? 'bg-red-100 text-red-800' : 'bg-yellow-100 text-yellow-800';
                
                const card = document.createElement('div');
                card.className = 'bg-gray-50 rounded-lg p-6 border-l-4 border-blue-500';
                card.innerHTML = `
                    <h3 class="font-bold text-gray-800 mb-2">${car}</h3>
                    <div class="space-y-2">
                        <span class="inline-block px-3 py-1 rounded-full text-sm font-medium ${statusColor}">
                            ${info.status}
                        </span>
                        ${info.user ? `<p class="text-sm text-gray-600">Pengguna: ${info.user}</p>` : ''}
                        ${info.returnTime ? `<p class="text-sm text-gray-600">Pulang: ${info.returnTime}</p>` : ''}
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function updateHistoryTable() {
            const tbody = document.getElementById('history-table-body');
            tbody.innerHTML = '';

            bookings.forEach(booking => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-200 hover:bg-gray-50';
                
                const startDate = new Date(booking.startDate).toLocaleDateString('ms-MY');
                const statusColor = booking.status === 'Selesai' ? 'text-green-600' : 
                                  booking.status === 'Sedang Digunakan' ? 'text-blue-600' : 'text-yellow-600';
                
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.employeeName}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.employeeSector}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.car}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.assignedDriver || '-'}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${startDate}</td>
                    <td class="px-4 py-3 text-sm font-medium ${statusColor}">${booking.status}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.purpose}</td>
                `;
                tbody.appendChild(row);
            });
        }

        // Schedule functions
        function updateScheduleView() {
            updateWeekHeader();
            updateDayHeaders();
            updateScheduleGrid();
        }

        function updateWeekHeader() {
            const endDate = new Date(currentWeekStart);
            endDate.setDate(endDate.getDate() + 6);
            
            const startStr = currentWeekStart.toLocaleDateString('ms-MY', { day: 'numeric', month: 'short' });
            const endStr = endDate.toLocaleDateString('ms-MY', { day: 'numeric', month: 'short', year: 'numeric' });
            
            document.getElementById('current-week').textContent = `${startStr} - ${endStr}`;
        }

        function updateDayHeaders() {
            const dayHeaders = document.getElementById('day-headers');
            dayHeaders.innerHTML = '';
            
            const days = ['Isnin', 'Selasa', 'Rabu', 'Khamis', 'Jumaat', 'Sabtu', 'Ahad'];
            
            for (let i = 0; i < 7; i++) {
                const date = new Date(currentWeekStart);
                date.setDate(date.getDate() + i);
                
                const dayDiv = document.createElement('div');
                dayDiv.className = 'text-center p-3 bg-gray-50 rounded font-medium text-gray-700';
                dayDiv.innerHTML = `
                    <div class="text-sm">${days[i]}</div>
                    <div class="text-xs text-gray-500">${date.getDate()}/${date.getMonth() + 1}</div>
                `;
                dayHeaders.appendChild(dayDiv);
            }
        }

        function updateScheduleGrid() {
            const scheduleGrid = document.getElementById('schedule-grid');
            scheduleGrid.innerHTML = '';

            const currentCars = getCurrentCarList();
            currentCars.forEach(car => {
                const carRow = document.createElement('div');
                carRow.className = 'grid grid-cols-8 gap-2 items-center';
                
                // Car name column
                const carNameDiv = document.createElement('div');
                carNameDiv.className = 'font-medium text-gray-800 p-3 bg-gray-50 rounded';
                carNameDiv.textContent = car;
                carRow.appendChild(carNameDiv);

                // Day columns
                for (let i = 0; i < 7; i++) {
                    const date = new Date(currentWeekStart);
                    date.setDate(date.getDate() + i);
                    
                    const dayDiv = document.createElement('div');
                    dayDiv.className = 'p-2 min-h-16 rounded border-2 border-dashed border-gray-200';
                    
                    // Check for bookings on this date
                    const dayBookings = bookings.filter(booking => {
                        const bookingStart = new Date(booking.startDate);
                        const bookingEnd = new Date(booking.endDate);
                        return booking.car === car && 
                               date >= bookingStart.toDateString() === date.toDateString() ||
                               (date >= bookingStart && date <= bookingEnd);
                    });

                    if (dayBookings.length > 0) {
                        const booking = dayBookings[0];
                        const statusColor = booking.status === 'Sedang Digunakan' ? 'bg-red-200 border-red-300' :
                                          booking.status === 'Ditempah' ? 'bg-blue-200 border-blue-300' : 'bg-green-200 border-green-300';
                        
                        dayDiv.className = `p-2 min-h-16 rounded border-2 ${statusColor}`;
                        dayDiv.innerHTML = `
                            <div class="text-xs font-medium text-gray-800">${booking.employeeName}</div>
                            <div class="text-xs text-gray-600">${new Date(booking.startDate).toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'})}</div>
                            <div class="text-xs text-gray-600">${booking.purpose.substring(0, 20)}...</div>
                        `;
                    } else {
                        dayDiv.className = 'p-2 min-h-16 rounded border-2 border-dashed border-gray-200 bg-green-50';
                        dayDiv.innerHTML = '<div class="text-xs text-gray-500 text-center mt-2">Tersedia</div>';
                    }
                    
                    carRow.appendChild(dayDiv);
                }
                
                scheduleGrid.appendChild(carRow);
            });
        }

        // Approval functions
        function updateApprovalTables() {
            updatePendingApprovals();
            updateRecentDecisions();
        }

        function updatePendingApprovals() {
            const tbody = document.getElementById('pending-approvals-body');
            tbody.innerHTML = '';

            const pendingBookings = bookings.filter(booking => booking.status === 'Menunggu Kelulusan');

            if (pendingBookings.length === 0) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td colspan="6" class="px-4 py-8 text-center text-gray-500">
                        ✅ Tiada tempahan menunggu kelulusan
                    </td>
                `;
                tbody.appendChild(row);
                return;
            }

            pendingBookings.forEach(booking => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-200 hover:bg-yellow-50';
                
                const startDateTime = new Date(booking.startDate);
                const endDateTime = new Date(booking.endDate);
                const dateTimeStr = `${startDateTime.toLocaleDateString('ms-MY')} ${startDateTime.toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'})} - ${endDateTime.toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'})}`;
                
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.employeeName}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.employeeSector}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.car}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${dateTimeStr}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${booking.purpose}</td>
                    <td class="px-4 py-3 text-sm">
                        <div class="flex space-x-2">
                            <button onclick="showDriverAssignment(${booking.id})" class="px-3 py-1 bg-blue-600 text-white rounded hover:bg-blue-700 text-xs font-medium">
                                🚗 Tugaskan Pemandu
                            </button>
                            <button onclick="rejectBooking(${booking.id})" class="px-3 py-1 bg-red-600 text-white rounded hover:bg-red-700 text-xs font-medium">
                                ❌ Tolak
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateRecentDecisions() {
            const tbody = document.getElementById('recent-decisions-body');
            tbody.innerHTML = '';

            // Show recent 10 decisions
            const recentDecisions = approvalDecisions.slice(-10).reverse();

            if (recentDecisions.length === 0) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td colspan="6" class="px-4 py-8 text-center text-gray-500">
                        📋 Tiada keputusan terkini
                    </td>
                `;
                tbody.appendChild(row);
                return;
            }

            recentDecisions.forEach(decision => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-200 hover:bg-gray-50';
                
                const statusColor = decision.status === 'Diluluskan' ? 'text-green-600' : 'text-red-600';
                const decisionTime = new Date(decision.decidedAt).toLocaleString('ms-MY');
                const bookingDate = new Date(decision.startDate).toLocaleDateString('ms-MY');
                
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm text-gray-900">${decision.employeeName}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${decision.car}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${bookingDate}</td>
                    <td class="px-4 py-3 text-sm font-medium ${statusColor}">${decision.status}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${decision.approvedBy}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${decisionTime}</td>
                `;
                tbody.appendChild(row);
            });
        }

        function showDriverAssignment(bookingId) {
            const booking = bookings.find(b => b.id === bookingId);
            if (!booking) return;

            // Create driver assignment modal
            const modal = document.createElement('div');
            modal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4';
            modal.innerHTML = `
                <div class="bg-white rounded-lg max-w-md w-full">
                    <div class="p-6">
                        <div class="text-center mb-6">
                            <div class="text-blue-600 text-4xl mb-4">🚗</div>
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Tugaskan Kenderaan & Pemandu</h3>
                            <p class="text-gray-600 text-sm">Pilih kenderaan dan pemandu untuk tempahan ini</p>
                        </div>
                        
                        <div class="mb-4 p-4 bg-gray-50 rounded-lg">
                            <div class="text-sm text-gray-600 space-y-1">
                                <div><strong>Pemohon:</strong> ${booking.employeeName}</div>
                                <div><strong>Tarikh:</strong> ${new Date(booking.startDate).toLocaleDateString('ms-MY')}</div>
                                <div><strong>Masa:</strong> ${new Date(booking.startDate).toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'})} - ${new Date(booking.endDate).toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'})}</div>
                                <div><strong>Tujuan:</strong> ${booking.purpose}</div>
                            </div>
                        </div>
                        
                        <div class="mb-4">
                            <label for="vehicle-select" class="block text-sm font-medium text-gray-700 mb-2">Pilih Kenderaan</label>
                            <select id="vehicle-select" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
                                <option value="">Pilih kenderaan...</option>
                                ${getCurrentCarList().map(vehicle => `<option value="${vehicle}">${vehicle}</option>`).join('')}
                            </select>
                        </div>
                        
                        <div class="mb-6">
                            <label for="driver-select" class="block text-sm font-medium text-gray-700 mb-2">Pilih Pemandu</label>
                            <select id="driver-select" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" required>
                                <option value="">Pilih pemandu...</option>
                                ${getAvailableDrivers().map(driver => `<option value="${driver}">${driver}</option>`).join('')}
                            </select>
                        </div>
                        
                        <div class="flex space-x-3 justify-center">
                            <button id="confirm-assignment" class="px-6 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 font-medium">
                                ✅ Lulus & Tugaskan
                            </button>
                            <button id="cancel-assignment" class="px-6 py-2 bg-gray-300 text-gray-700 rounded-lg hover:bg-gray-400 font-medium">
                                Batal
                            </button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(modal);
            
            // Handle confirmation
            document.getElementById('confirm-assignment').addEventListener('click', function() {
                const selectedVehicle = document.getElementById('vehicle-select').value;
                const selectedDriver = document.getElementById('driver-select').value;
                
                if (!selectedVehicle) {
                    showNotification('Sila pilih kenderaan terlebih dahulu!', 'error');
                    return;
                }
                
                if (!selectedDriver) {
                    showNotification('Sila pilih pemandu terlebih dahulu!', 'error');
                    return;
                }
                
                approveBookingWithVehicleAndDriver(bookingId, selectedVehicle, selectedDriver);
                document.body.removeChild(modal);
            });
            
            // Handle cancellation
            document.getElementById('cancel-assignment').addEventListener('click', function() {
                document.body.removeChild(modal);
            });
            
            // Close on backdrop click
            modal.addEventListener('click', function(e) {
                if (e.target === modal) {
                    document.body.removeChild(modal);
                }
            });
        }

        function approveBookingWithVehicleAndDriver(bookingId, assignedVehicle, assignedDriver) {
            const booking = bookings.find(b => b.id === bookingId);
            if (!booking) return;

            // Update booking with assigned vehicle and driver
            booking.car = assignedVehicle;
            booking.status = 'Diluluskan';
            booking.assignedDriver = assignedDriver;
            booking.approvedBy = currentUserInfo.username;
            booking.approvedAt = new Date().toISOString();

            // Update car status
            carStatuses[assignedVehicle] = {
                status: "Ditempah",
                user: booking.employeeName,
                returnTime: new Date(booking.endDate).toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'})
            };

            // Add to approval decisions history
            approvalDecisions.push({
                id: booking.id,
                employeeName: booking.employeeName,
                car: assignedVehicle,
                startDate: booking.startDate,
                status: 'Diluluskan',
                approvedBy: currentUserInfo.username,
                decidedAt: new Date().toISOString(),
                assignedDriver: assignedDriver
            });

            // Send email notification
            sendEmailNotification(booking, 'approved');

            // Save data to localStorage
            saveDataToStorage();

            // Update all relevant displays
            updateApprovalTables();
            updateCarStatusGrid();
            updateHistoryTable();
            updateScheduleView();

            // Show success message
            showNotification(`✅ Tempahan telah diluluskan dengan kenderaan ${assignedVehicle} dan pemandu ${assignedDriver}!`, 'success');
        }

        function rejectBooking(bookingId) {
            const booking = bookings.find(b => b.id === bookingId);
            if (!booking) return;

            // Update booking status
            booking.status = 'Ditolak';
            booking.approvedBy = currentUserInfo.username;
            booking.approvedAt = new Date().toISOString();

            // Add to approval decisions history
            approvalDecisions.push({
                id: booking.id,
                employeeName: booking.employeeName,
                car: booking.car,
                startDate: booking.startDate,
                status: 'Ditolak',
                approvedBy: currentUserInfo.username,
                decidedAt: new Date().toISOString()
            });

            // Send email notification
            sendEmailNotification(booking, 'rejected');

            // Save data to localStorage
            saveDataToStorage();

            // Update all relevant displays
            updateApprovalTables();
            updateHistoryTable();

            // Show notification
            showNotification('❌ Tempahan telah ditolak dan email notifikasi telah dihantar!', 'error');
        }

        function showNotification(message, type) {
            const notification = document.createElement('div');
            notification.className = `fixed top-4 right-4 px-6 py-4 rounded-lg shadow-lg text-white z-50 ${
                type === 'success' ? 'bg-green-500' : 'bg-red-500'
            }`;
            notification.textContent = message;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }

        // Email notification system
        function sendEmailNotification(booking, status) {
            // Find user email
            const userEmail = getUserEmail(booking.employeeName);
            if (!userEmail) {
                console.log('Email pengguna tidak dijumpai');
                return;
            }

            // Create email content
            const emailContent = createEmailContent(booking, status);
            
            // Simulate email sending (in real implementation, this would call an email service)
            simulateEmailSending(userEmail, emailContent, status);
            
            // Log email activity
            logEmailActivity(booking, userEmail, status);
        }

        function getUserEmail(employeeName) {
            // Search in users array
            const user = users.find(u => u.name === employeeName);
            if (user) return user.email;
            
            // Search in registered users
            const regUser = Object.values(registeredUsers).find(u => u.fullName === employeeName);
            if (regUser) return regUser.email;
            
            // Default emails for demo users
            const defaultEmails = {
                'Ahmad Rahman': 'ahmad.rahman@moe.gov.my',
                'Siti Nurhaliza': 'siti.nurhaliza@moe.gov.my',
                'Ali Hassan': 'ali.hassan@moe.gov.my',
                'Fatimah Zahra': 'fatimah.zahra@moe.gov.my'
            };
            
            return defaultEmails[employeeName] || null;
        }

        function createEmailContent(booking, status) {
            const startDate = new Date(booking.startDate);
            const endDate = new Date(booking.endDate);
            const dateStr = startDate.toLocaleDateString('ms-MY');
            const startTime = startDate.toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'});
            const endTime = endDate.toLocaleTimeString('ms-MY', {hour: '2-digit', minute: '2-digit'});
            
            if (status === 'approved') {
                return {
                    subject: `✅ Tempahan Kenderaan Diluluskan - ${booking.car}`,
                    body: `
Assalamualaikum dan Salam Sejahtera,

Tempahan kenderaan anda telah DILULUSKAN oleh admin.

BUTIRAN TEMPAHAN:
📅 Tarikh: ${dateStr}
⏰ Masa: ${startTime} - ${endTime}
🚗 Kenderaan: ${booking.car}
🧑‍💼 Pemandu Ditugaskan: ${booking.assignedDriver || 'Belum ditugaskan'}
📍 Tujuan: ${booking.purpose}
👤 Diluluskan oleh: ${currentUserInfo.username}

ARAHAN PENTING:
• Sila ambil kunci kenderaan dari pejabat admin sebelum masa yang ditetapkan
• Pemandu yang ditugaskan akan menghubungi anda untuk koordinasi perjalanan
• Pastikan kenderaan dipulangkan tepat pada masa yang dijadualkan
• Laporkan sebarang masalah kenderaan kepada admin segera

Terima kasih.

Sistem eKenderaan
Pejabat Pendidikan Daerah Limbang
                    `
                };
            } else {
                return {
                    subject: `❌ Tempahan Kenderaan Ditolak - ${booking.car}`,
                    body: `
Assalamualaikum dan Salam Sejahtera,

Maaf dimaklumkan bahawa tempahan kenderaan anda telah DITOLAK.

BUTIRAN TEMPAHAN:
📅 Tarikh: ${dateStr}
⏰ Masa: ${startTime} - ${endTime}
🚗 Kenderaan: ${booking.car}
📍 Tujuan: ${booking.purpose}
👤 Ditolak oleh: ${currentUserInfo.username}

SEBAB KEMUNGKINAN:
• Kenderaan sudah ditempah pada masa tersebut
• Tarikh/masa tidak sesuai
• Tujuan penggunaan tidak memenuhi syarat

Sila hubungi admin untuk maklumat lanjut atau buat tempahan baru pada tarikh lain.

Terima kasih.

Sistem eKenderaan
Pejabat Pendidikan Daerah Limbang
                    `
                };
            }
        }

        function simulateEmailSending(email, content, status) {
            // Simulate email sending delay
            setTimeout(() => {
                // Create email preview popup
                showEmailPreview(email, content, status);
            }, 1000);
        }

        function showEmailPreview(email, content, status) {
            const emailPreview = document.createElement('div');
            emailPreview.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4';
            emailPreview.innerHTML = `
                <div class="bg-white rounded-lg max-w-2xl w-full max-h-96 overflow-y-auto">
                    <div class="p-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-semibold text-gray-800">📧 Email Notifikasi Dihantar</h3>
                            <button id="close-email-preview" class="text-gray-500 hover:text-gray-700 text-xl">&times;</button>
                        </div>
                        
                        <div class="bg-gray-50 rounded-lg p-4 mb-4">
                            <div class="text-sm text-gray-600 mb-2">
                                <strong>Kepada:</strong> ${email}
                            </div>
                            <div class="text-sm text-gray-600 mb-2">
                                <strong>Subjek:</strong> ${content.subject}
                            </div>
                            <div class="text-sm text-gray-600">
                                <strong>Status:</strong> 
                                <span class="${status === 'approved' ? 'text-green-600' : 'text-red-600'} font-medium">
                                    ${status === 'approved' ? '✅ Dihantar Berjaya' : '📧 Dihantar Berjaya'}
                                </span>
                            </div>
                        </div>
                        
                        <div class="bg-white border rounded-lg p-4">
                            <h4 class="font-medium text-gray-800 mb-2">Kandungan Email:</h4>
                            <div class="text-sm text-gray-700 whitespace-pre-line">${content.body}</div>
                        </div>
                        
                        <div class="mt-4 text-center">
                            <button id="close-email-preview-btn" class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
                                Tutup
                            </button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(emailPreview);
            
            // Close handlers
            document.getElementById('close-email-preview').addEventListener('click', () => {
                document.body.removeChild(emailPreview);
            });
            
            document.getElementById('close-email-preview-btn').addEventListener('click', () => {
                document.body.removeChild(emailPreview);
            });
            
            // Close on backdrop click
            emailPreview.addEventListener('click', (e) => {
                if (e.target === emailPreview) {
                    document.body.removeChild(emailPreview);
                }
            });
        }

        function logEmailActivity(booking, email, status) {
            const logEntry = {
                timestamp: new Date().toISOString(),
                bookingId: booking.id,
                employeeName: booking.employeeName,
                email: email,
                status: status,
                approvedBy: currentUserInfo.username
            };
            
            // In a real system, this would be saved to a database
            console.log('Email Activity Log:', logEntry);
        }

        // Week navigation
        document.getElementById('prev-week').addEventListener('click', () => {
            currentWeekStart.setDate(currentWeekStart.getDate() - 7);
            updateScheduleView();
        });

        document.getElementById('next-week').addEventListener('click', () => {
            currentWeekStart.setDate(currentWeekStart.getDate() + 7);
            updateScheduleView();
        });

        // Analytics data and functions
        let analyticsData = {
            2024: {
                monthly: {
                    'Toyota Vios - ABC1234': [5, 8, 12, 7, 9, 15, 11, 13, 8, 10, 6, 9],
                    'Honda City - DEF5678': [3, 6, 9, 5, 7, 12, 8, 10, 6, 8, 4, 7],
                    'Perodua Axia - GHI9012': [2, 4, 6, 3, 5, 8, 6, 7, 4, 6, 3, 5],
                    'Proton Saga - JKL3456': [4, 7, 10, 6, 8, 13, 9, 11, 7, 9, 5, 8]
                },
                sectors: {
                    'Sektor Pengurusan': 45,
                    'Sektor Pembelajaran': 38,
                    'Sektor Perancangan': 32,
                    'Sektor Pentaksiran dan Peperiksaan': 28,
                    'PTIS': 15,
                    'Sektor Pengurusan Sekolah': 22
                }
            }
        };

        let currentAnalyticsYear = 2024;
        let currentAnalyticsVehicle = 'all';

        // Chart instances
        let monthlyChart = null;
        let vehicleChart = null;
        let sectorChart = null;

        function updateAnalyticsView() {
            updateAnalyticsFilters();
            updateAnalyticsSummary();
            updateAnalyticsCharts();
            updateAnalyticsTable();
        }

        function updateAnalyticsFilters() {
            // Update vehicle filter dropdown
            const vehicleSelect = document.getElementById('analytics-vehicle');
            const currentVehicles = getCurrentCarList();
            
            vehicleSelect.innerHTML = '<option value="all">Semua Kenderaan</option>';
            currentVehicles.forEach(vehicle => {
                const option = document.createElement('option');
                option.value = vehicle;
                option.textContent = vehicle;
                vehicleSelect.appendChild(option);
            });
        }

        function updateAnalyticsSummary() {
            const yearData = analyticsData[currentAnalyticsYear];
            if (!yearData) return;

            // Calculate total bookings
            let totalBookings = 0;
            let completedBookings = 0;
            let vehicleUsage = {};

            // Calculate from monthly data
            Object.entries(yearData.monthly).forEach(([vehicle, months]) => {
                const vehicleTotal = months.reduce((sum, count) => sum + count, 0);
                totalBookings += vehicleTotal;
                completedBookings += Math.floor(vehicleTotal * 0.85); // Assume 85% completion rate
                vehicleUsage[vehicle] = vehicleTotal;
            });

            // Find most popular vehicle
            const mostPopular = Object.entries(vehicleUsage).reduce((max, [vehicle, usage]) => 
                usage > max.usage ? {vehicle, usage} : max, {vehicle: '-', usage: 0});

            // Calculate average usage per month
            const averageUsage = Math.round(totalBookings / 12);

            // Update summary cards
            document.getElementById('total-bookings').textContent = totalBookings;
            document.getElementById('completed-bookings').textContent = completedBookings;
            document.getElementById('most-popular-vehicle').textContent = mostPopular.vehicle.split(' - ')[0] || '-';
            document.getElementById('average-usage').textContent = averageUsage;
        }

        function updateAnalyticsCharts() {
            updateMonthlyChart();
            updateVehicleComparisonChart();
            updateSectorChart();
        }

        function updateMonthlyChart() {
            const canvas = document.getElementById('monthly-usage-chart');
            const ctx = canvas.getContext('2d');
            
            // Clear previous chart
            if (monthlyChart) {
                monthlyChart = null;
            }
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            const yearData = analyticsData[currentAnalyticsYear];
            if (!yearData) return;

            const months = ['Jan', 'Feb', 'Mar', 'Apr', 'Mei', 'Jun', 'Jul', 'Ogo', 'Sep', 'Okt', 'Nov', 'Dis'];
            
            if (currentAnalyticsVehicle === 'all') {
                // Show grouped bar chart for all vehicles
                const colors = ['#3B82F6', '#10B981', '#F59E0B', '#EF4444', '#8B5CF6', '#06B6D4'];
                const vehicles = Object.keys(yearData.monthly);
                
                drawGroupedBarChart(ctx, canvas, {
                    labels: months,
                    datasets: vehicles.map((vehicle, index) => ({
                        label: vehicle.split(' - ')[0],
                        data: yearData.monthly[vehicle],
                        color: colors[index % colors.length]
                    })),
                    title: 'Penggunaan Bulanan Mengikut Kenderaan',
                    yAxisLabel: 'Bilangan Tempahan'
                });
            } else {
                // Show single vehicle monthly data
                const monthlyData = yearData.monthly[currentAnalyticsVehicle];
                if (monthlyData) {
                    const chartData = months.map((month, index) => ({
                        label: month,
                        value: monthlyData[index]
                    }));

                    drawBarChart(ctx, canvas, {
                        data: chartData,
                        colors: ['#3B82F6'],
                        title: `Penggunaan Bulanan - ${currentAnalyticsVehicle.split(' - ')[0]}`,
                        yAxisLabel: 'Bilangan Tempahan'
                    });
                }
            }
        }

        function updateVehicleComparisonChart() {
            const canvas = document.getElementById('vehicle-comparison-chart');
            const ctx = canvas.getContext('2d');
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            const yearData = analyticsData[currentAnalyticsYear];
            if (!yearData) return;

            // Calculate total usage for each vehicle
            const vehicleData = Object.entries(yearData.monthly).map(([vehicle, months]) => ({
                label: vehicle.split(' - ')[0],
                value: months.reduce((sum, count) => sum + count, 0)
            }));

            const colors = ['#3B82F6', '#10B981', '#F59E0B', '#EF4444'];

            drawBarChart(ctx, canvas, {
                data: vehicleData,
                colors: colors,
                title: 'Jumlah Penggunaan Mengikut Kenderaan',
                yAxisLabel: 'Bilangan Tempahan'
            });
        }

        function updateSectorChart() {
            const canvas = document.getElementById('sector-usage-chart');
            const ctx = canvas.getContext('2d');
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            const yearData = analyticsData[currentAnalyticsYear];
            if (!yearData || !yearData.sectors) return;

            const sectorData = Object.entries(yearData.sectors).map(([sector, count]) => ({
                label: sector.replace('Sektor ', ''), // Shorten labels for better display
                value: count
            }));

            const colors = ['#3B82F6', '#10B981', '#F59E0B', '#EF4444', '#8B5CF6', '#06B6D4'];

            drawBarChart(ctx, canvas, {
                data: sectorData,
                colors: colors,
                title: 'Penggunaan Mengikut Sektor',
                yAxisLabel: 'Bilangan Tempahan'
            });
        }

        function updateAnalyticsTable() {
            const tbody = document.getElementById('analytics-table-body');
            tbody.innerHTML = '';

            const yearData = analyticsData[currentAnalyticsYear];
            if (!yearData) return;

            Object.entries(yearData.monthly).forEach(([vehicle, months]) => {
                const totalBookings = months.reduce((sum, count) => sum + count, 0);
                const totalHours = totalBookings * 6; // Assume average 6 hours per booking
                const utilizationRate = Math.round((totalBookings / (12 * 20)) * 100); // 20 working days per month
                
                // Find most common sector for this vehicle (simplified)
                const topSector = Object.keys(yearData.sectors)[Math.floor(Math.random() * Object.keys(yearData.sectors).length)];

                const row = document.createElement('tr');
                row.className = 'border-b border-gray-200 hover:bg-gray-50';
                
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm text-gray-900 font-medium">${vehicle}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${totalBookings}</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${totalHours} jam</td>
                    <td class="px-4 py-3 text-sm text-gray-900">${topSector}</td>
                    <td class="px-4 py-3 text-sm">
                        <div class="flex items-center">
                            <div class="w-16 bg-gray-200 rounded-full h-2 mr-2">
                                <div class="bg-blue-600 h-2 rounded-full" style="width: ${utilizationRate}%"></div>
                            </div>
                            <span class="text-sm text-gray-600">${utilizationRate}%</span>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        // Simple chart drawing functions
        function drawGroupedBarChart(ctx, canvas, config) {
            const padding = 80;
            const chartWidth = canvas.width - (padding * 2);
            const chartHeight = canvas.height - (padding * 2);
            
            // Clear and set styles
            ctx.fillStyle = '#374151';
            ctx.font = '12px Arial';
            
            // Draw title
            ctx.textAlign = 'center';
            ctx.fillText(config.title, canvas.width / 2, 30);
            
            // Find max value across all datasets
            const maxValue = Math.max(...config.datasets.flatMap(d => d.data));
            const yStep = Math.ceil(maxValue / 5);
            
            // Draw Y-axis grid and labels
            ctx.strokeStyle = '#E5E7EB';
            ctx.lineWidth = 1;
            
            for (let i = 0; i <= 5; i++) {
                const y = padding + (chartHeight / 5) * i;
                const value = maxValue - (yStep * i);
                
                ctx.beginPath();
                ctx.moveTo(padding, y);
                ctx.lineTo(padding + chartWidth, y);
                ctx.stroke();
                
                ctx.textAlign = 'right';
                ctx.fillStyle = '#6B7280';
                ctx.fillText(value.toString(), padding - 10, y + 4);
            }
            
            // Calculate bar dimensions
            const groupWidth = chartWidth / config.labels.length;
            const barWidth = groupWidth / (config.datasets.length + 1);
            
            // Draw bars
            config.labels.forEach((label, labelIndex) => {
                const groupX = padding + (labelIndex * groupWidth);
                
                config.datasets.forEach((dataset, datasetIndex) => {
                    const value = dataset.data[labelIndex];
                    const barHeight = (value / maxValue) * chartHeight;
                    const x = groupX + (datasetIndex * barWidth) + (barWidth * 0.1);
                    const y = padding + chartHeight - barHeight;
                    
                    // Draw bar
                    ctx.fillStyle = dataset.color;
                    ctx.fillRect(x, y, barWidth * 0.8, barHeight);
                    
                    // Draw value on top of bar if space allows
                    if (barHeight > 20) {
                        ctx.fillStyle = '#FFFFFF';
                        ctx.textAlign = 'center';
                        ctx.font = '10px Arial';
                        ctx.fillText(value.toString(), x + (barWidth * 0.4), y + 15);
                    }
                });
                
                // Draw X-axis label
                ctx.fillStyle = '#374151';
                ctx.textAlign = 'center';
                ctx.font = '12px Arial';
                ctx.fillText(label, groupX + (groupWidth / 2), canvas.height - 20);
            });
            
            // Draw legend
            let legendY = 50;
            config.datasets.forEach((dataset, index) => {
                ctx.fillStyle = dataset.color;
                ctx.fillRect(20, legendY + (index * 20), 15, 10);
                ctx.fillStyle = '#374151';
                ctx.textAlign = 'left';
                ctx.font = '12px Arial';
                ctx.fillText(dataset.label, 40, legendY + (index * 20) + 8);
            });
        }

        function drawBarChart(ctx, canvas, config) {
            const padding = 80;
            const chartWidth = canvas.width - (padding * 2);
            const chartHeight = canvas.height - (padding * 2);
            
            ctx.fillStyle = '#374151';
            ctx.font = '12px Arial';
            
            // Draw title
            ctx.textAlign = 'center';
            ctx.fillText(config.title, canvas.width / 2, 30);
            
            const maxValue = Math.max(...config.data.map(d => d.value));
            const yStep = Math.ceil(maxValue / 5);
            
            // Draw Y-axis grid and labels
            ctx.strokeStyle = '#E5E7EB';
            ctx.lineWidth = 1;
            
            for (let i = 0; i <= 5; i++) {
                const y = padding + (chartHeight / 5) * i;
                const value = maxValue - (yStep * i);
                
                ctx.beginPath();
                ctx.moveTo(padding, y);
                ctx.lineTo(padding + chartWidth, y);
                ctx.stroke();
                
                ctx.textAlign = 'right';
                ctx.fillStyle = '#6B7280';
                ctx.fillText(value.toString(), padding - 10, y + 4);
            }
            
            // Calculate bar dimensions
            const barWidth = chartWidth / config.data.length * 0.7;
            const barSpacing = chartWidth / config.data.length * 0.3;
            
            // Draw bars
            config.data.forEach((item, index) => {
                const barHeight = (item.value / maxValue) * chartHeight;
                const x = padding + (index * (barWidth + barSpacing)) + (barSpacing / 2);
                const y = padding + chartHeight - barHeight;
                
                // Draw bar with gradient effect
                ctx.fillStyle = config.colors[index % config.colors.length];
                ctx.fillRect(x, y, barWidth, barHeight);
                
                // Add subtle border
                ctx.strokeStyle = '#FFFFFF';
                ctx.lineWidth = 1;
                ctx.strokeRect(x, y, barWidth, barHeight);
                
                // Draw value on top of bar
                ctx.fillStyle = '#374151';
                ctx.textAlign = 'center';
                ctx.font = 'bold 11px Arial';
                ctx.fillText(item.value.toString(), x + barWidth / 2, y - 8);
                
                // Draw label below bar
                ctx.fillStyle = '#374151';
                ctx.textAlign = 'center';
                ctx.font = '11px Arial';
                
                // Handle long labels by wrapping or rotating
                const labelMaxWidth = barWidth + barSpacing;
                if (ctx.measureText(item.label).width > labelMaxWidth) {
                    // Rotate label if too long
                    ctx.save();
                    ctx.translate(x + barWidth / 2, canvas.height - 15);
                    ctx.rotate(-Math.PI / 4);
                    ctx.textAlign = 'right';
                    ctx.fillText(item.label, 0, 0);
                    ctx.restore();
                } else {
                    // Normal horizontal label
                    ctx.fillText(item.label, x + barWidth / 2, canvas.height - 15);
                }
            });
            
            // Draw Y-axis label
            ctx.save();
            ctx.translate(15, canvas.height / 2);
            ctx.rotate(-Math.PI / 2);
            ctx.textAlign = 'center';
            ctx.fillStyle = '#374151';
            ctx.font = '12px Arial';
            ctx.fillText(config.yAxisLabel || 'Nilai', 0, 0);
            ctx.restore();
        }

        function drawPieChart(ctx, canvas, config) {
            const centerX = canvas.width / 2;
            const centerY = canvas.height / 2 + 20;
            const radius = Math.min(canvas.width, canvas.height) / 4;
            
            ctx.fillStyle = '#374151';
            ctx.font = '12px Arial';
            ctx.textAlign = 'center';
            ctx.fillText(config.title, centerX, 30);
            
            const total = config.data.reduce((sum, item) => sum + item.value, 0);
            let currentAngle = -Math.PI / 2;
            
            config.data.forEach((item, index) => {
                const sliceAngle = (item.value / total) * 2 * Math.PI;
                
                // Draw slice
                ctx.fillStyle = config.colors[index % config.colors.length];
                ctx.beginPath();
                ctx.moveTo(centerX, centerY);
                ctx.arc(centerX, centerY, radius, currentAngle, currentAngle + sliceAngle);
                ctx.closePath();
                ctx.fill();
                
                // Draw label
                const labelAngle = currentAngle + sliceAngle / 2;
                const labelX = centerX + Math.cos(labelAngle) * (radius + 30);
                const labelY = centerY + Math.sin(labelAngle) * (radius + 30);
                
                ctx.fillStyle = '#374151';
                ctx.textAlign = 'center';
                ctx.fillText(`${item.label}`, labelX, labelY);
                ctx.fillText(`${item.value}`, labelX, labelY + 15);
                
                currentAngle += sliceAngle;
            });
        }

        // Analytics event listeners
        document.getElementById('update-analytics').addEventListener('click', function() {
            currentAnalyticsYear = parseInt(document.getElementById('analytics-year').value);
            currentAnalyticsVehicle = document.getElementById('analytics-vehicle').value;
            updateAnalyticsView();
            showNotification('📊 Graf telah dikemas kini!', 'success');
        });

        // App initialization is handled by login system
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'99e4cb3db733a559',t:'MTc2MzEwNTMyNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
