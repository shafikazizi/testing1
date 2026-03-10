import React, { useState, useEffect } from 'react';
import { 
  Inbox, 
  Send, 
  LayoutDashboard, 
  PlusCircle, 
  Search, 
  FileText, 
  CheckCircle, 
  Clock, 
  AlertCircle,
  MoreVertical,
  LogOut,
  User,
  Filter
} from 'lucide-react';

// Komponen Utama
export default function App() {
  const [activeTab, setActiveTab] = useState('dashboard');
  const [letters, setLetters] = useState([
    { id: 1, refNo: 'KPM/100/1/1(01)', title: 'Mesyuarat Penyelarasan ICT', type: 'Masuk', sender: 'Kementerian Pendidikan', date: '2024-05-20', status: 'Selesai', priority: 'Tinggi' },
    { id: 2, refNo: 'JPN/200/2/5(12)', title: 'Laporan Suku Tahun Kedua', type: 'Keluar', sender: 'Unit Kewangan', date: '2024-05-22', status: 'Menunggu', priority: 'Sederhana' },
    { id: 3, refNo: 'PPD/300/1/2(05)', title: 'Permohonan Cuti Peristiwa', type: 'Masuk', sender: 'SK Taman Maju', date: '2024-05-23', status: 'Proses', priority: 'Rendah' },
  ]);

  const [searchTerm, setSearchTerm] = useState('');
  const [showModal, setShowModal] = useState(false);
  const [newLetter, setNewLetter] = useState({
    refNo: '', title: '', type: 'Masuk', sender: '', date: '', priority: 'Sederhana', status: 'Menunggu'
  });

  // Fungsi tambah surat baru
  const handleAddLetter = (e) => {
    e.preventDefault();
    const letterToAdd = {
      ...newLetter,
      id: letters.length + 1
    };
    setLetters([letterToAdd, ...letters]);
    setShowModal(false);
    setNewLetter({ refNo: '', title: '', type: 'Masuk', sender: '', date: '', priority: 'Sederhana', status: 'Menunggu' });
  };

  // Statistik
  const stats = {
    total: letters.length,
    inbound: letters.filter(l => l.type === 'Masuk').length,
    outbound: letters.filter(l => l.type === 'Keluar').length,
    pending: letters.filter(l => l.status === 'Menunggu').length
  };

  const filteredLetters = letters.filter(l => 
    l.title.toLowerCase().includes(searchTerm.toLowerCase()) || 
    l.refNo.toLowerCase().includes(searchTerm.toLowerCase())
  );

  return (
    <div className="flex h-screen bg-gray-50 font-sans">
      {/* Sidebar */}
      <aside className="w-64 bg-slate-900 text-white flex flex-col">
        <div className="p-6 flex items-center gap-3 border-b border-slate-800">
          <div className="bg-blue-600 p-2 rounded-lg">
            <FileText size={24} />
          </div>
          <h1 className="text-xl font-bold tracking-tight">eSurat Pro</h1>
        </div>
        
        <nav className="flex-1 p-4 space-y-2">
          <NavItem 
            icon={<LayoutDashboard size={20} />} 
            label="Papan Pemuka" 
            active={activeTab === 'dashboard'} 
            onClick={() => setActiveTab('dashboard')} 
          />
          <NavItem 
            icon={<Inbox size={20} />} 
            label="Surat Masuk" 
            active={activeTab === 'masuk'} 
            onClick={() => setActiveTab('masuk')} 
          />
          <NavItem 
            icon={<Send size={20} />} 
            label="Surat Keluar" 
            active={activeTab === 'keluar'} 
            onClick={() => setActiveTab('keluar')} 
          />
        </nav>

        <div className="p-4 border-t border-slate-800">
          <div className="flex items-center gap-3 p-2 rounded-lg hover:bg-slate-800 cursor-pointer transition-colors">
            <div className="w-8 h-8 rounded-full bg-slate-700 flex items-center justify-center">
              <User size={16} />
            </div>
            <div className="flex-1 overflow-hidden">
              <p className="text-sm font-medium truncate">Admin Sistem</p>
              <p className="text-xs text-slate-400">admin@esurat.gov.my</p>
            </div>
            <LogOut size={16} className="text-slate-500" />
          </div>
        </div>
      </aside>

      {/* Main Content */}
      <main className="flex-1 overflow-y-auto">
        {/* Header */}
        <header className="bg-white border-b sticky top-0 z-10 p-4 flex justify-between items-center">
          <h2 className="text-xl font-semibold text-gray-800">
            {activeTab === 'dashboard' ? 'Papan Pemuka' : 
             activeTab === 'masuk' ? 'Pengurusan Surat Masuk' : 'Pengurusan Surat Keluar'}
          </h2>
          <div className="flex items-center gap-4">
            <div className="relative">
              <Search className="absolute left-3 top-1/2 -translate-y-1/2 text-gray-400" size={18} />
              <input 
                type="text" 
                placeholder="Cari no. rujukan atau tajuk..."
                className="pl-10 pr-4 py-2 border rounded-full text-sm bg-gray-50 focus:outline-none focus:ring-2 focus:ring-blue-500 w-64 transition-all"
                value={searchTerm}
                onChange={(e) => setSearchTerm(e.target.value)}
              />
            </div>
            <button 
              onClick={() => setShowModal(true)}
              className="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg flex items-center gap-2 text-sm font-medium transition-colors"
            >
              <PlusCircle size={18} /> Daftar Surat
            </button>
          </div>
        </header>

        <div className="p-6">
          {activeTab === 'dashboard' && (
            <>
              {/* Stats Cards */}
              <div className="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
                <StatCard label="Jumlah Surat" value={stats.total} icon={<FileText className="text-blue-600" />} color="blue" />
                <StatCard label="Surat Masuk" value={stats.inbound} icon={<Inbox className="text-emerald-600" />} color="emerald" />
                <StatCard label="Surat Keluar" value={stats.outbound} icon={<Send className="text-indigo-600" />} color="indigo" />
                <StatCard label="Menunggu Tindakan" value={stats.pending} icon={<Clock className="text-amber-600" />} color="amber" />
              </div>

              {/* Recent Activity / Table */}
              <div className="bg-white rounded-xl shadow-sm border overflow-hidden">
                <div className="p-4 border-b bg-gray-50 flex justify-between items-center">
                  <h3 className="font-semibold text-gray-700">Senarai Surat Terkini</h3>
                  <button className="text-sm text-blue-600 font-medium hover:underline flex items-center gap-1">
                    <Filter size={14} /> Tapis Data
                  </button>
                </div>
                <div className="overflow-x-auto">
                  <table className="w-full text-left">
                    <thead>
                      <tr className="bg-gray-50 text-gray-500 text-xs uppercase tracking-wider">
                        <th className="px-6 py-3 font-medium">No. Rujukan / Tajuk</th>
                        <th className="px-6 py-3 font-medium">Jenis</th>
                        <th className="px-6 py-3 font-medium">Pengirim/Penerima</th>
                        <th className="px-6 py-3 font-medium">Tarikh</th>
                        <th className="px-6 py-3 font-medium">Status</th>
                        <th className="px-6 py-3 font-medium text-right">Tindakan</th>
                      </tr>
                    </thead>
                    <tbody className="divide-y">
                      {filteredLetters.map((letter) => (
                        <tr key={letter.id} className="hover:bg-gray-50 transition-colors">
                          <td className="px-6 py-4">
                            <div className="text-sm font-semibold text-gray-900">{letter.refNo}</div>
                            <div className="text-xs text-gray-500">{letter.title}</div>
                          </td>
                          <td className="px-6 py-4 text-sm capitalize">
                            <span className={`px-2 py-1 rounded-full text-xs font-medium ${
                              letter.type === 'Masuk' ? 'bg-emerald-100 text-emerald-700' : 'bg-indigo-100 text-indigo-700'
                            }`}>
                              {letter.type}
                            </span>
                          </td>
                          <td className="px-6 py-4 text-sm text-gray-600">{letter.sender}</td>
                          <td className="px-6 py-4 text-sm text-gray-600">{letter.date}</td>
                          <td className="px-6 py-4">
                            <StatusBadge status={letter.status} />
                          </td>
                          <td className="px-6 py-4 text-right">
                            <button className="text-gray-400 hover:text-gray-600">
                              <MoreVertical size={18} />
                            </button>
                          </td>
                        </tr>
                      ))}
                    </tbody>
                  </table>
                </div>
              </div>
            </>
          )}

          {activeTab !== 'dashboard' && (
            <div className="bg-white p-8 rounded-xl shadow-sm border text-center">
              <FileText size={48} className="mx-auto text-gray-300 mb-4" />
              <h3 className="text-lg font-medium text-gray-900">Modul {activeTab === 'masuk' ? 'Surat Masuk' : 'Surat Keluar'}</h3>
              <p className="text-gray-500">Kandungan spesifik untuk {activeTab} akan dipaparkan di sini mengikut keperluan sistem anda.</p>
            </div>
          )}
        </div>
      </main>

      {/* Modal Daftar Surat */}
      {showModal && (
        <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50 p-4">
          <div className="bg-white rounded-xl shadow-xl w-full max-w-lg overflow-hidden animate-in fade-in zoom-in duration-200">
            <div className="p-6 border-b flex justify-between items-center bg-gray-50">
              <h3 className="text-lg font-bold text-gray-800">Daftar Surat Baru</h3>
              <button onClick={() => setShowModal(false)} className="text-gray-500 hover:text-gray-700">&times;</button>
            </div>
            <form onSubmit={handleAddLetter} className="p-6 space-y-4">
              <div className="grid grid-cols-2 gap-4">
                <div className="space-y-1">
                  <label className="text-xs font-bold text-gray-600 uppercase">Jenis Surat</label>
                  <select 
                    className="w-full p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none"
                    value={newLetter.type}
                    onChange={(e) => setNewLetter({...newLetter, type: e.target.value})}
                  >
                    <option value="Masuk">Surat Masuk</option>
                    <option value="Keluar">Surat Keluar</option>
                  </select>
                </div>
                <div className="space-y-1">
                  <label className="text-xs font-bold text-gray-600 uppercase">Tarikh</label>
                  <input 
                    type="date" 
                    required
                    className="w-full p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none"
                    value={newLetter.date}
                    onChange={(e) => setNewLetter({...newLetter, date: e.target.value})}
                  />
                </div>
              </div>
              <div className="space-y-1">
                <label className="text-xs font-bold text-gray-600 uppercase">No. Rujukan</label>
                <input 
                  type="text" 
                  placeholder="Contoh: KPM/100/1/1(01)"
                  required
                  className="w-full p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none"
                  value={newLetter.refNo}
                  onChange={(e) => setNewLetter({...newLetter, refNo: e.target.value})}
                />
              </div>
              <div className="space-y-1">
                <label className="text-xs font-bold text-gray-600 uppercase">Tajuk Surat</label>
                <input 
                  type="text" 
                  placeholder="Masukkan tajuk penuh surat"
                  required
                  className="w-full p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none"
                  value={newLetter.title}
                  onChange={(e) => setNewLetter({...newLetter, title: e.target.value})}
                />
              </div>
              <div className="space-y-1">
                <label className="text-xs font-bold text-gray-600 uppercase">Pengirim / Penerima</label>
                <input 
                  type="text" 
                  placeholder="Agensi atau Unit"
                  required
                  className="w-full p-2 border rounded-lg focus:ring-2 focus:ring-blue-500 outline-none"
                  value={newLetter.sender}
                  onChange={(e) => setNewLetter({...newLetter, sender: e.target.value})}
                />
              </div>
              <div className="flex justify-end gap-3 pt-4 border-t mt-6">
                <button 
                  type="button" 
                  onClick={() => setShowModal(false)}
                  className="px-4 py-2 text-sm font-medium text-gray-600 hover:bg-gray-100 rounded-lg transition-colors"
                >
                  Batal
                </button>
                <button 
                  type="submit"
                  className="px-4 py-2 text-sm font-medium bg-blue-600 text-white hover:bg-blue-700 rounded-lg shadow-sm transition-colors"
                >
                  Simpan Maklumat
                </button>
              </div>
            </form>
          </div>
        </div>
      )}
    </div>
  );
}

// Komponen Kecil: NavItem
function NavItem({ icon, label, active, onClick }) {
  return (
    <button 
      onClick={onClick}
      className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl text-sm font-medium transition-all ${
        active 
          ? 'bg-blue-600 text-white shadow-lg shadow-blue-900/20' 
          : 'text-slate-400 hover:bg-slate-800 hover:text-slate-100'
      }`}
    >
      {icon}
      <span>{label}</span>
    </button>
  );
}

// Komponen Kecil: StatCard
function StatCard({ label, value, icon, color }) {
  return (
    <div className="bg-white p-6 rounded-xl border shadow-sm flex items-center gap-4">
      <div className={`p-3 rounded-lg bg-${color}-50`}>
        {icon}
      </div>
      <div>
        <p className="text-sm font-medium text-gray-500">{label}</p>
        <p className="text-2xl font-bold text-gray-900">{value}</p>
      </div>
    </div>
  );
}

// Komponen Kecil: StatusBadge
function StatusBadge({ status }) {
  const styles = {
    'Selesai': 'bg-emerald-100 text-emerald-700 border-emerald-200',
    'Menunggu': 'bg-amber-100 text-amber-700 border-amber-200',
    'Proses': 'bg-blue-100 text-blue-700 border-blue-200',
    'Gagal': 'bg-rose-100 text-rose-700 border-rose-200',
  };

  const icons = {
    'Selesai': <CheckCircle size={12} />,
    'Menunggu': <Clock size={12} />,
    'Proses': <AlertCircle size={12} />,
    'Gagal': <AlertCircle size={12} />,
  };

  return (
    <span className={`inline-flex items-center gap-1.5 px-2.5 py-0.5 rounded-full text-xs font-semibold border ${styles[status] || styles['Menunggu']}`}>
      {icons[status] || icons['Menunggu']}
      {status}
    </span>
  );
}
