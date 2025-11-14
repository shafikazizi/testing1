<!doctype html>
<html lang="ms" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sistem Buku Perkhidmatan Kerajaan</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <style>
        body {
            box-sizing: border-box;
        }
        .loading-spinner {
            border: 3px solid #f3f4f6;
            border-top: 3px solid #3b82f6;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
            transition: all 0.3s ease;
        }
        .fade-in {
            animation: fadeIn 0.3s ease-in;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
 </head>
 <body class="h-full bg-gray-50">
  <div class="min-h-full"><!-- Header -->
   <header class="bg-blue-900 shadow-lg">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
     <div class="flex justify-between items-center py-6">
      <div class="flex items-center">
       <div>
        <h1 id="system-title" class="text-2xl font-bold text-white">Sistem Buku Perkhidmatan Kerajaan</h1>
        <p id="department-name" class="text-blue-200">Pejabat Pendidikan Daerah Limbang</p>
       </div>
      </div>
      <div class="flex items-center space-x-4"><span id="record-count" class="text-blue-200 text-sm">0 rekod</span> <button id="add-btn" class="bg-yellow-500 hover:bg-yellow-600 text-blue-900 font-semibold px-4 py-2 rounded-lg transition-colors duration-200"> + Tambah Rekod </button>
      </div>
     </div>
    </div>
   </header><!-- Main Content -->
   <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8"><!-- Search and Filter -->
    <div class="bg-white rounded-lg shadow-md p-6 mb-6">
     <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      <div><label for="search-input" class="block text-sm font-medium text-gray-700 mb-2">Cari Nama/Nombor Jabatan</label> <input type="text" id="search-input" placeholder="Masukkan nama atau nombor jabatan..." class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
      </div>
      <div><label for="status-filter" class="block text-sm font-medium text-gray-700 mb-2">Status Perkhidmatan</label> <select id="status-filter" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"> <option value="">Semua Status</option> <option value="Aktif">Aktif</option> <option value="Bersara">Bersara</option> <option value="Cuti Tanpa Gaji">Cuti Tanpa Gaji</option> <option value="Diberhentikan">Diberhentikan</option> </select>
      </div>
      <div><label for="ministry-filter" class="block text-sm font-medium text-gray-700 mb-2">Sekolah</label> <select id="ministry-filter" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"> <option value="">Semua Sekolah</option> </select>
      </div>
     </div>
    </div><!-- Data Table -->
    <div class="bg-white rounded-lg shadow-md overflow-hidden">
     <div class="overflow-x-auto">
      <table class="min-w-full divide-y divide-gray-200">
       <thead class="bg-gray-50">
        <tr>
         <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Pegawai</th>
         <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nombor Jabatan</th>
         <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jawatan</th>
         <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Gred</th>
         <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
         <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pengemaskinian Sehingga</th>
         <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Catatan</th>
        </tr>
       </thead>
       <tbody id="data-table-body" class="bg-white divide-y divide-gray-200"><!-- Data will be populated here -->
       </tbody>
      </table>
     </div>
     <div id="empty-state" class="text-center py-12 hidden">
      <svg class="mx-auto h-12 w-12 text-gray-400" fill="none" viewbox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
      </svg>
      <h3 class="mt-2 text-sm font-medium text-gray-900">Tiada rekod</h3>
      <p class="mt-1 text-sm text-gray-500">Mulakan dengan menambah rekod perkhidmatan pertama.</p>
     </div>
    </div>
   </main><!-- Footer -->
   <footer class="bg-gray-800 text-white py-6 mt-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
     <p id="footer-text">© 2024 Kerajaan Malaysia</p>
    </div>
   </footer>
  </div><!-- Add/Edit Modal -->
  <div id="modal" class="fixed inset-0 bg-gray-600 bg-opacity-50 hidden z-50">
   <div class="flex items-center justify-center min-h-screen px-4">
    <div class="bg-white rounded-lg shadow-xl max-w-4xl w-full max-h-screen overflow-y-auto">
     <div class="px-6 py-4 border-b border-gray-200">
      <h3 id="modal-title" class="text-lg font-medium text-gray-900">Tambah Rekod Baru</h3>
     </div>
     <form id="record-form" class="px-6 py-4">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
       <div><label for="nama_penuh" class="block text-sm font-medium text-gray-700 mb-2">Nama Pegawai *</label> <input type="text" id="nama_penuh" name="nama_penuh" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div><label for="no_kad_pengenalan" class="block text-sm font-medium text-gray-700 mb-2">No. Kad Pengenalan *</label> <input type="text" id="no_kad_pengenalan" name="no_kad_pengenalan" required placeholder="123456-78-9012" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div><label for="no_perkhidmatan" class="block text-sm font-medium text-gray-700 mb-2">Nombor Jabatan *</label> <input type="text" id="no_perkhidmatan" name="no_perkhidmatan" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div><label for="jawatan" class="block text-sm font-medium text-gray-700 mb-2">Jawatan *</label> <input type="text" id="jawatan" name="jawatan" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div><label for="gred" class="block text-sm font-medium text-gray-700 mb-2">Gred *</label> <select id="gred" name="gred" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"> <option value="">Pilih Gred</option> <option value="1">1</option> <option value="2">2</option> <option value="3">3</option> <option value="4">4</option> <option value="5">5</option> <option value="6">6</option> <option value="7">7</option> <option value="8">8</option> <option value="9">9</option> <option value="10">10</option> <option value="11">11</option> <option value="12">12</option> <option value="13">13</option> <option value="14">14</option> <option value="15">15</option> </select>
       </div>
       <div><label for="kementerian" class="block text-sm font-medium text-gray-700 mb-2">Sekolah *</label> <select id="kementerian" name="kementerian" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"> <option value="">Pilih Sekolah</option> <option value="SK Taman Desa">SK Taman Desa</option> <option value="SK Bandar Utama">SK Bandar Utama</option> <option value="SK Damansara">SK Damansara</option> <option value="SMK Petaling Jaya">SMK Petaling Jaya</option> <option value="SMK Subang Jaya">SMK Subang Jaya</option> <option value="SMK Shah Alam">SMK Shah Alam</option> <option value="SK Seri Kembangan">SK Seri Kembangan</option> <option value="SK Puchong">SK Puchong</option> <option value="SMK Cyberjaya">SMK Cyberjaya</option> <option value="SK Putrajaya">SK Putrajaya</option> <option value="SMK Klang">SMK Klang</option> <option value="SK Kajang">SK Kajang</option> </select>
       </div>
       <div><label for="tarikh_lantikan" class="block text-sm font-medium text-gray-700 mb-2">Tarikh Lantikan *</label> <input type="date" id="tarikh_lantikan" name="tarikh_lantikan" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div><label for="status_perkhidmatan" class="block text-sm font-medium text-gray-700 mb-2">Status Perkhidmatan *</label> <select id="status_perkhidmatan" name="status_perkhidmatan" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"> <option value="">Pilih Status</option> <option value="Aktif">Aktif</option> <option value="Bersara">Bersara</option> <option value="Cuti Tanpa Gaji">Cuti Tanpa Gaji</option> <option value="Diberhentikan">Diberhentikan</option> </select>
       </div>
       <div><label for="pengemaskinian_sehingga" class="block text-sm font-medium text-gray-700 mb-2">Pengemaskinian Sehingga</label> <input type="date" id="pengemaskinian_sehingga" name="pengemaskinian_sehingga" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div class="md:col-span-2"><label for="alamat" class="block text-sm font-medium text-gray-700 mb-2">Alamat</label> <textarea id="alamat" name="alamat" rows="3" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"></textarea>
       </div>
       <div><label for="no_telefon" class="block text-sm font-medium text-gray-700 mb-2">No. Telefon</label> <input type="tel" id="no_telefon" name="no_telefon" placeholder="012-3456789" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
       <div><label for="emel" class="block text-sm font-medium text-gray-700 mb-2">E-mel</label> <input type="email" id="emel" name="emel" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
       </div>
      </div>
      <div class="flex justify-end space-x-3 mt-6 pt-6 border-t border-gray-200"><button type="button" id="cancel-btn" class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50"> Batal </button> <button type="submit" id="save-btn" class="px-4 py-2 text-sm font-medium text-white bg-blue-600 border border-transparent rounded-md hover:bg-blue-700 flex items-center"> <span id="save-text">Simpan</span>
        <div id="save-spinner" class="loading-spinner ml-2 hidden"></div></button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Delete Confirmation Modal -->
  <div id="delete-modal" class="fixed inset-0 bg-gray-600 bg-opacity-50 hidden z-50">
   <div class="flex items-center justify-center min-h-screen px-4">
    <div class="bg-white rounded-lg shadow-xl max-w-md w-full">
     <div class="px-6 py-4">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Padam Rekod</h3>
      <p class="text-sm text-gray-600 mb-6">Adakah anda pasti ingin memadam rekod ini? Tindakan ini tidak boleh dibatalkan.</p>
      <div class="flex justify-end space-x-3"><button id="delete-cancel-btn" class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50"> Batal </button> <button id="delete-confirm-btn" class="px-4 py-2 text-sm font-medium text-white bg-red-600 border border-transparent rounded-md hover:bg-red-700 flex items-center"> <span id="delete-text">Padam</span>
        <div id="delete-spinner" class="loading-spinner ml-2 hidden"></div></button>
      </div>
     </div>
    </div>
   </div>
  </div>
  <script>
        let allRecords = [];
        let filteredRecords = [];
        let editingRecord = null;
        let recordToDelete = null;
        let currentRecordCount = 0;

        const defaultConfig = {
            system_title: "Sistem Buku Perkhidmatan Kerajaan",
            department_name: "Pejabat Pendidikan Daerah Limbang",
            footer_text: "© 2024 Kerajaan Malaysia",
            primary_color: "#1e3a8a",
            secondary_color: "#eab308",
            background_color: "#f9fafb"
        };

        // Data handler for SDK
        const dataHandler = {
            onDataChanged(data) {
                allRecords = data;
                currentRecordCount = data.length;
                updateRecordCount();
                applyFilters();
                updateMinistryFilter();
            }
        };

        // Element SDK functions
        async function render(config) {
            document.getElementById('system-title').textContent = config.system_title || defaultConfig.system_title;
            document.getElementById('department-name').textContent = config.department_name || defaultConfig.department_name;
            document.getElementById('footer-text').textContent = config.footer_text || defaultConfig.footer_text;
        }

        function mapToCapabilities(config) {
            return {
                recolorables: [
                    {
                        get: () => config.primary_color || defaultConfig.primary_color,
                        set: (value) => {
                            config.primary_color = value;
                            window.elementSdk.setConfig({ primary_color: value });
                        }
                    },
                    {
                        get: () => config.secondary_color || defaultConfig.secondary_color,
                        set: (value) => {
                            config.secondary_color = value;
                            window.elementSdk.setConfig({ secondary_color: value });
                        }
                    }
                ],
                borderables: [],
                fontEditable: undefined,
                fontSizeable: undefined
            };
        }

        function mapToEditPanelValues(config) {
            return new Map([
                ["system_title", config.system_title || defaultConfig.system_title],
                ["department_name", config.department_name || defaultConfig.department_name],
                ["footer_text", config.footer_text || defaultConfig.footer_text]
            ]);
        }

        // Initialize SDKs
        async function initializeApp() {
            try {
                if (window.elementSdk) {
                    await window.elementSdk.init({
                        defaultConfig,
                        render,
                        mapToCapabilities,
                        mapToEditPanelValues
                    });
                }

                if (window.dataSdk) {
                    const result = await window.dataSdk.init(dataHandler);
                    if (!result.isOk) {
                        showToast('Ralat memulakan sistem data', 'error');
                    }
                }
            } catch (error) {
                showToast('Ralat memulakan aplikasi', 'error');
            }
        }

        // Utility functions
        function showToast(message, type = 'success') {
            const toast = document.createElement('div');
            toast.className = `toast px-6 py-4 rounded-lg shadow-lg text-white fade-in ${type === 'success' ? 'bg-green-500' : 'bg-red-500'}`;
            toast.textContent = message;
            document.body.appendChild(toast);
            
            setTimeout(() => {
                toast.remove();
            }, 3000);
        }

        function updateRecordCount() {
            const countElement = document.getElementById('record-count');
            countElement.textContent = `${currentRecordCount} rekod`;
        }

        function formatDate(dateString) {
            if (!dateString) return '';
            const date = new Date(dateString);
            return date.toLocaleDateString('ms-MY');
        }

        function updateMinistryFilter() {
            const ministryFilter = document.getElementById('ministry-filter');
            const ministries = [...new Set(allRecords.map(record => record.kementerian).filter(Boolean))];
            
            // Clear existing options except "Semua Sekolah"
            ministryFilter.innerHTML = '<option value="">Semua Sekolah</option>';
            
            ministries.forEach(ministry => {
                const option = document.createElement('option');
                option.value = ministry;
                option.textContent = ministry;
                ministryFilter.appendChild(option);
            });
        }

        function applyFilters() {
            const searchTerm = document.getElementById('search-input').value.toLowerCase();
            const statusFilter = document.getElementById('status-filter').value;
            const ministryFilter = document.getElementById('ministry-filter').value;

            filteredRecords = allRecords.filter(record => {
                const matchesSearch = !searchTerm || 
                    record.nama_penuh.toLowerCase().includes(searchTerm) ||
                    record.no_perkhidmatan.toLowerCase().includes(searchTerm);
                
                const matchesStatus = !statusFilter || record.status_perkhidmatan === statusFilter;
                const matchesSchool = !ministryFilter || record.kementerian === ministryFilter;

                return matchesSearch && matchesStatus && matchesSchool;
            });

            renderTable();
        }

        function renderTable() {
            const tbody = document.getElementById('data-table-body');
            const emptyState = document.getElementById('empty-state');

            if (filteredRecords.length === 0) {
                tbody.innerHTML = '';
                emptyState.classList.remove('hidden');
                return;
            }

            emptyState.classList.add('hidden');
            
            tbody.innerHTML = filteredRecords.map(record => `
                <tr class="hover:bg-gray-50">
                    <td class="px-6 py-4 whitespace-nowrap">
                        <div class="text-sm font-medium text-gray-900">${record.nama_penuh}</div>
                        <div class="text-sm text-gray-500">${record.no_kad_pengenalan}</div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${record.no_perkhidmatan}</td>
                    <td class="px-6 py-4 whitespace-nowrap">
                        <div class="text-sm text-gray-900">${record.jawatan}</div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${record.gred}</td>
                    <td class="px-6 py-4 whitespace-nowrap">
                        <span class="inline-flex px-2 py-1 text-xs font-semibold rounded-full ${getStatusColor(record.status_perkhidmatan)}">
                            ${record.status_perkhidmatan}
                        </span>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                        ${record.pengemaskinian_sehingga ? formatDate(record.pengemaskinian_sehingga) : '-'}
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                        <button onclick="editRecord('${record.__backendId}')" class="text-blue-600 hover:text-blue-900 mr-3">Edit</button>
                        <button onclick="showDeleteModal('${record.__backendId}')" class="text-red-600 hover:text-red-900">Padam</button>
                    </td>
                </tr>
            `).join('');
        }

        function getStatusColor(status) {
            switch (status) {
                case 'Aktif': return 'bg-green-100 text-green-800';
                case 'Bersara': return 'bg-blue-100 text-blue-800';
                case 'Cuti Tanpa Gaji': return 'bg-yellow-100 text-yellow-800';
                case 'Diberhentikan': return 'bg-red-100 text-red-800';
                default: return 'bg-gray-100 text-gray-800';
            }
        }

        function showModal(title = 'Tambah Rekod Baru') {
            document.getElementById('modal-title').textContent = title;
            document.getElementById('modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
        }

        function hideModal() {
            document.getElementById('modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
            document.getElementById('record-form').reset();
            editingRecord = null;
        }

        function showDeleteModal(recordId) {
            recordToDelete = allRecords.find(r => r.__backendId === recordId);
            document.getElementById('delete-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
        }

        function hideDeleteModal() {
            document.getElementById('delete-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
            recordToDelete = null;
        }

        function editRecord(recordId) {
            editingRecord = allRecords.find(r => r.__backendId === recordId);
            if (!editingRecord) return;

            // Populate form
            Object.keys(editingRecord).forEach(key => {
                if (key !== '__backendId') {
                    const element = document.getElementById(key);
                    if (element) {
                        element.value = editingRecord[key] || '';
                    }
                }
            });

            showModal('Edit Rekod');
        }

        async function saveRecord(formData) {
            const saveBtn = document.getElementById('save-btn');
            const saveText = document.getElementById('save-text');
            const saveSpinner = document.getElementById('save-spinner');

            saveBtn.disabled = true;
            saveText.textContent = 'Menyimpan...';
            saveSpinner.classList.remove('hidden');

            try {
                if (currentRecordCount >= 999 && !editingRecord) {
                    showToast('Had maksimum 999 rekod telah dicapai. Sila padam beberapa rekod terlebih dahulu.', 'error');
                    return;
                }

                const recordData = {
                    ...formData,
                    tarikh_masuk: new Date().toISOString()
                };

                let result;
                if (editingRecord) {
                    result = await window.dataSdk.update({ ...editingRecord, ...recordData });
                } else {
                    result = await window.dataSdk.create(recordData);
                }

                if (result.isOk) {
                    showToast(editingRecord ? 'Rekod berjaya dikemaskini' : 'Rekod berjaya disimpan');
                    hideModal();
                } else {
                    showToast('Ralat menyimpan rekod', 'error');
                }
            } catch (error) {
                showToast('Ralat menyimpan rekod', 'error');
            } finally {
                saveBtn.disabled = false;
                saveText.textContent = 'Simpan';
                saveSpinner.classList.add('hidden');
            }
        }

        async function deleteRecord() {
            if (!recordToDelete) return;

            const deleteBtn = document.getElementById('delete-confirm-btn');
            const deleteText = document.getElementById('delete-text');
            const deleteSpinner = document.getElementById('delete-spinner');

            deleteBtn.disabled = true;
            deleteText.textContent = 'Memadam...';
            deleteSpinner.classList.remove('hidden');

            try {
                const result = await window.dataSdk.delete(recordToDelete);
                
                if (result.isOk) {
                    showToast('Rekod berjaya dipadam');
                    hideDeleteModal();
                } else {
                    showToast('Ralat memadam rekod', 'error');
                }
            } catch (error) {
                showToast('Ralat memadam rekod', 'error');
            } finally {
                deleteBtn.disabled = false;
                deleteText.textContent = 'Padam';
                deleteSpinner.classList.add('hidden');
            }
        }

        // Event listeners
        document.addEventListener('DOMContentLoaded', initializeApp);

        document.getElementById('add-btn').addEventListener('click', () => showModal());
        document.getElementById('cancel-btn').addEventListener('click', hideModal);
        document.getElementById('delete-cancel-btn').addEventListener('click', hideDeleteModal);
        document.getElementById('delete-confirm-btn').addEventListener('click', deleteRecord);

        document.getElementById('search-input').addEventListener('input', applyFilters);
        document.getElementById('status-filter').addEventListener('change', applyFilters);
        document.getElementById('ministry-filter').addEventListener('change', applyFilters);

        document.getElementById('record-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const formData = new FormData(e.target);
            const data = Object.fromEntries(formData.entries());
            saveRecord(data);
        });

        // Close modals when clicking outside
        document.getElementById('modal').addEventListener('click', (e) => {
            if (e.target === e.currentTarget) hideModal();
        });

        document.getElementById('delete-modal').addEventListener('click', (e) => {
            if (e.target === e.currentTarget) hideDeleteModal();
        });
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'99e4fe19148264ad',t:'MTc2MzEwNzQwOS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
