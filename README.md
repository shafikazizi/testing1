import React, { useState } from 'react';
import { 
  Inbox, 
  Send, 
  FileText, 
  PlusCircle, 
  LayoutDashboard, 
  Search, 
  Bell, 
  User, 
  ChevronRight,
  ArrowLeft,
  Clock
} from 'lucide-react';

// Data Awalan (Mock Data)
const mockLetters = [
  {
    id: 1,
    refNo: 'MOE/100-1/3/2',
    title: 'Jemputan Mesyuarat Penyelarasan ICT',
    sender: 'Kementerian Pendidikan',
    recipient: 'Jabatan Pendidikan Negeri',
    date: '2026-03-09',
    type: 'masuk',
    status: 'Dalam Tindakan',
    content: 'Tuan/Puan,\n\nDengan segala hormatnya perkara di atas adalah dirujuk.\n\n2. Sukacita dimaklumkan bahawa mesyuarat penyelarasan ICT peringkat negeri akan diadakan pada ketetapan berikut...'
  },
  {
    id: 2,
    refNo: 'KKM/500-2/1/1',
    title: 'Garis Panduan Kesihatan Terkini',
    sender: 'Kementerian Kesihatan Malaysia',
    recipient: 'Semua Agensi Kerajaan',
    date: '2026-03-08',
    type: 'masuk',
    status: 'Selesai',
    content: 'Pekeliling ini dikeluarkan bagi memaklumkan mengenai garis panduan kesihatan terkini di tempat kerja bagi tahun 2026...'
  },
  {
    id: 3,
    refNo: 'JPN/SAB/400-1/2',
    title: 'Permohonan Kelulusan Bajet Tambahan',
    sender: 'Sektor Pengurusan',
    recipient: 'Kementerian Kewangan',
    date: '2026-03-10',
    type: 'keluar',
    status: 'Dihantar',
    content: 'Merujuk kepada perkara di atas, pihak kami memohon kelulusan bajet tambahan sebanyak RM50,000 untuk tujuan menaik taraf infrastruktur pelayan...'
  }
];

export default function App() {
  const [currentView, setCurrentView] = useState('dashboard');
  const [letters, setLetters] = useState(mockLetters);
  const [selectedLetter, setSelectedLetter] = useState(null);
  const [searchQuery, setSearchQuery] = useState('');

  const [formData, setFormData] = useState({
    refNo: '',
    title: '',
    recipient: '',
    content: ''
  });

  const totalMasuk = letters.filter(l => l.type === 'masuk').length;
  const totalKeluar = letters.filter(l => l.type === 'keluar').length;
  const pendingAction = letters.filter(l => l.status === 'Dalam Tindakan').length;

  const handleNavigation = (view) => {
    setCurrentView(view);
    setSearchQuery('');
  };

  const handleViewLetter = (letter) => {
    setSelectedLetter(letter);
    setCurrentView('papar');
  };

  const handleInputChange = (e) => {
    const { name, value } = e.target;
    setFormData(prev => ({ ...prev, [name]: value }));
  };

  const handleSubmitLetter = (e) => {
    e.preventDefault();
    const newLetter = {
      id: letters.length + 1,
      refNo: formData.refNo,
      title: formData.title,
      sender: 'Pengguna Semasa',
      recipient: formData.recipient,
      date: new Date().toISOString().split('T')[0],
      type: 'keluar',
      status: 'Dihantar',
      content: formData.content
    };
    
    setLetters([newLetter, ...letters]);
    setFormData({ refNo: '', title: '', recipient: '', content: '' });
    setCurrentView('keluar');
  };

  const getStatusColor = (status) => {
    switch(status) {
      case 'Selesai': return 'bg-green-100 text-green-800';
      case 'Dalam Tindakan': return 'bg-yellow-100 text-yellow-800';
      case 'Dihantar': return 'bg-blue-100 text-blue-800';
      default: return 'bg-gray-100 text-gray-800';
    }
  };

  const filteredLetters = letters.filter(letter => {
    if (currentView === 'masuk' && letter.type !== 'masuk') return false;
    if (currentView === 'keluar' && letter.type !== 'keluar') return false;
    
    return letter.title.toLowerCase().includes(searchQuery.toLowerCase()) || 
           letter.refNo.toLowerCase().includes(searchQuery.toLowerCase());
  });

  const renderContent = () => {
    switch(currentView) {
      case 'dashboard':
        return (
          <div className="space-y-6 animate-in fade-in duration-300">
            <h2 className="text-2xl font-bold text-gray-800">Papan Pemuka</h2>
            
            <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div className="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex items-center space-x-4">
                <div className="p-3 bg-blue-50 text-blue-600 rounded-lg">
                  <Inbox size={24} />
                </div>
                <div>
                  <p className="text-sm text-gray-500 font-medium">Surat Masuk</p>
                  <p className="text-2xl font-bold text-gray-800">{totalMasuk}</p>
                </div>
              </div>
              <div className="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex items-center space-x-4">
                <div className="p-3 bg-purple-50 text-purple-600 rounded-lg">
                  <Send size={24} />
                </div>
                <div>
                  <p className="text-sm text-gray-500 font-medium">Surat Keluar</p>
                  <p className="text-2xl font-bold text-gray-800">{totalKeluar}</p>
                </div>
              </div>
              <div className="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex items-center space-x-4">
                <div className="p-3 bg-orange-50 text-orange-600 rounded-lg">
                  <Clock size={24} />
                </div>
                <div>
                  <p className="text-sm text-gray-500 font-medium">Dalam Tindakan</p>
                  <p className="text-2xl font-bold text-gray-800">{pendingAction}</p>
                </div>
              </div>
            </div>

            <div className="bg-white rounded-xl shadow-sm border border-gray-100 overflow-hidden">
              <div className="p-6 border-b border-gray-100 flex justify-between items-center">
                <h3 className="text-lg font-semibold text-gray-800">Surat Terkini</h3>
                <button onClick={() => handleNavigation('masuk')} className="text-blue-600 text-sm hover:underline font-medium">Lihat Semua</button>
              </div>
              <div className="divide-y divide-gray-100">
                {letters.slice(0, 5).map(letter => (
                  <div key={letter.id} className="p-4 hover:bg-gray-50 transition flex items-center justify-between cursor-pointer" onClick={() => handleViewLetter(letter)}>
                    <div className="flex items-center space-x-4">
                      <div className={`p-2 rounded-full ${letter.type === 'masuk' ? 'bg-blue-50 text-blue-500' : 'bg-purple-50 text-purple-500'}`}>
                        {letter.type === 'masuk' ? <Inbox size={18} /> : <Send size={18} />}
                      </div>
                      <div>
                        <p className="font-medium text-gray-800">{letter.title}</p>
                        <p className="text-sm text-gray-500">{letter.refNo} • {letter.date}</p>
                      </div>
                    </div>
                    <div className="flex items-center space-x-3">
                      <span className={`px-3 py-1 rounded-full text-xs font-medium ${getStatusColor(letter.status)}`}>
                        {letter.status}
                      </span>
                      <ChevronRight size={18} className="text-gray-400" />
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        );
      
      case 'masuk':
      case 'keluar':
        return (
          <div className="space-y-6 animate-in fade-in duration-300">
            <div className="flex flex-col sm:flex-row justify-between items-start sm:items-center space-y-4 sm:space-y-0">
              <h2 className="text-2xl font-bold text-gray-800">
                {currentView === 'masuk' ? 'Peti Surat Masuk' : 'Peti Surat Keluar'}
              </h2>
              {currentView === 'keluar' && (
                <button 
                  onClick={() => handleNavigation('cipta')}
                  className="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg flex items-center space-x-2 transition shadow-sm"
                >
                  <PlusCircle size={18} />
                  <span>Cipta Surat</span>
                </button>
              )}
            </div>

            <div className="bg-white rounded-xl shadow-sm border border-gray-100 overflow-hidden">
              <div className="p-4 border-b border-gray-100 flex items-center bg-gray-50">
                <div className="relative w-full max-w-md">
                  <Search className="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400" size={18} />
                  <input 
                    type="text" 
                    placeholder="Cari no rujukan atau tajuk..." 
                    className="w-full pl-10 pr-4 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
                    value={searchQuery}
                    onChange={(e) => setSearchQuery(e.target.value)}
                  />
                </div>
              </div>
              <div className="overflow-x-auto">
                <table className="w-full text-left border-collapse">
                  <thead>
                    <tr className="bg-white text-gray-500 text-sm border-b border-gray-100">
                      <th className="p-4 font-medium">No. Rujukan</th>
                      <th className="p-4 font-medium">Tajuk</th>
                      <th className="p-4 font-medium">{currentView === 'masuk' ? 'Pengirim' : 'Penerima'}</th>
                      <th className="p-4 font-medium">Tarikh</th>
                      <th className="p-4 font-medium">Status</th>
                      <th className="p-4 font-medium">Tindakan</th>
                    </tr>
                  </thead>
                  <tbody className="divide-y divide-gray-100">
                    {filteredLetters.length > 0 ? filteredLetters.map(letter => (
                      <tr key={letter.id} className="hover:bg-gray-50 transition group">
                        <td className="p-4 text-sm font-medium text-gray-800">{letter.refNo}</td>
                        <td className="p-4 text-sm text-gray-800 max-w-xs truncate">{letter.title}</td>
                        <td className="p-4 text-sm text-gray-600">{currentView === 'masuk' ? letter.sender : letter.recipient}</td>
                        <td className="p-4 text-sm text-gray-600">{letter.date}</td>
                        <td className="p-4">
                          <span className={`px-2.5 py-1 rounded-full text-xs font-medium ${getStatusColor(letter.status)}`}>
                            {letter.status}
                          </span>
                        </td>
                        <td className="p-4">
                          <button 
                            onClick={() => handleViewLetter(letter)}
                            className="text-blue-600 hover:text-blue-800 text-sm font-medium"
                          >
                            Papar
                          </button>
                        </td>
                      </tr>
                    )) : (
                      <tr>
                        <td colSpan="6" className="p-8 text-center text-gray-500">Tiada rekod surat dijumpai.</td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        );

      case 'cipta':
        return (
          <div className="max-w-3xl mx-auto space-y-6 animate-in fade-in duration-300">
            <div className="flex items-center space-x-4">
              <button onClick={() => handleNavigation('keluar')} className="p-2 bg-white rounded-full text-gray-600 hover:bg-gray-100 shadow-sm border border-gray-100">
                <ArrowLeft size={20} />
              </button>
              <h2 className="text-2xl font-bold text-gray-800">Cipta Surat Baharu</h2>
            </div>
            
            <div className="bg-white rounded-xl shadow-sm border border-gray-100 p-6 sm:p-8">
              <form onSubmit={handleSubmitLetter} className="space-y-6">
                <div className="grid grid-cols-1 sm:grid-cols-2 gap-6">
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-2">No. Rujukan</label>
                    <input 
                      type="text" 
                      name="refNo"
                      required
                      value={formData.refNo}
                      onChange={handleInputChange}
                      className="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
                      placeholder="Contoh: KKM/100-1/2/3"
                    />
                  </div>
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-2">Penerima</label>
                    <input 
                      type="text" 
                      name="recipient"
                      required
                      value={formData.recipient}
                      onChange={handleInputChange}
                      className="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
                      placeholder="Nama Jabatan / Agensi"
                    />
                  </div>
                </div>
                
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">Tajuk Surat</label>
                  <input 
                    type="text" 
                    name="title"
                    required
                    value={formData.title}
                    onChange={handleInputChange}
                    className="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
                    placeholder="Perkara/Tajuk Utama"
                  />
                </div>

                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">Kandungan</label>
                  <textarea 
                    name="content"
                    required
                    value={formData.content}
                    onChange={handleInputChange}
                    rows="8"
                    className="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 resize-none text-sm"
                    placeholder="Taipkan kandungan surat di sini..."
                  ></textarea>
                </div>

                <div className="flex justify-end space-x-3 pt-4 border-t border-gray-100">
                  <button 
                    type="button" 
                    onClick={() => handleNavigation('keluar')}
                    className="px-6 py-2 border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-50 transition text-sm font-medium"
                  >
                    Batal
                  </button>
                  <button 
                    type="submit" 
                    className="px-6 py-2 bg-blue-600 rounded-lg text-white hover:bg-blue-700 transition flex items-center space-x-2 text-sm font-medium shadow-sm"
                  >
                    <Send size={16} />
                    <span>Hantar Surat</span>
                  </button>
                </div>
              </form>
            </div>
          </div>
        );

      case 'papar':
        if (!selectedLetter) return null;
        return (
          <div className="max-w-4xl mx-auto space-y-6 animate-in fade-in duration-300">
            <div className="flex items-center justify-between">
              <div className="flex items-center space-x-4">
                <button onClick={() => handleNavigation(selectedLetter.type === 'masuk' ? 'masuk' : 'keluar')} className="p-2 bg-white rounded-full text-gray-600 hover:bg-gray-100 shadow-sm border border-gray-100">
                  <ArrowLeft size={20} />
                </button>
                <h2 className="text-xl font-bold text-gray-800">Maklumat Surat</h2>
              </div>
              <div className="flex space-x-2">
                <button className="px-4 py-2 bg-white border border-gray-200 rounded-lg text-gray-700 hover:bg-gray-50 flex items-center space-x-2 shadow-sm text-sm font-medium">
                  <FileText size={16} />
                  <span>Cetak PDF</span>
                </button>
              </div>
            </div>

            <div className="bg-white rounded-xl shadow-sm border border-gray-100 overflow-hidden">
              <div className="p-6 sm:p-8 border-b border-gray-100 bg-gray-50 flex flex-col sm:flex-row justify-between items-start gap-4">
                <div>
                  <h3 className="text-2xl font-bold text-gray-900 mb-2">{selectedLetter.title}</h3>
                  <div className="flex flex-wrap gap-4 text-sm text-gray-600">
                    <span className="flex items-center space-x-1">
                      <FileText size={16} className="text-gray-400" />
                      <span>{selectedLetter.refNo}</span>
                    </span>
                    <span className="flex items-center space-x-1">
                      <Clock size={16} className="text-gray-400" />
                      <span>{selectedLetter.date}</span>
                    </span>
                  </div>
                </div>
                <span className={`px-3 py-1.5 rounded-full text-sm font-medium whitespace-nowrap ${getStatusColor(selectedLetter.status)}`}>
                  {selectedLetter.status}
                </span>
              </div>

              <div className="p-6 sm:p-8 grid grid-cols-1 md:grid-cols-2 gap-8 border-b border-gray-100">
                <div>
                  <p className="text-sm text-gray-500 font-medium mb-1">Daripada:</p>
                  <p className="text-base font-semibold text-gray-800">{selectedLetter.sender}</p>
                </div>
                <div>
                  <p className="text-sm text-gray-500 font-medium mb-1">Kepada:</p>
                  <p className="text-base font-semibold text-gray-800">{selectedLetter.recipient}</p>
                </div>
              </div>

              <div className="p-6 sm:p-8">
                <p className="text-sm text-gray-500 font-medium mb-4">Kandungan Surat:</p>
                <div className="bg-gray-50 p-6 rounded-lg whitespace-pre-wrap text-gray-800 leading-relaxed border border-gray-100 text-sm sm:text-base">
                  {selectedLetter.content}
                </div>
              </div>
            </div>
          </div>
        );

      default:
        return <div>Paparan tidak ditemui</div>;
    }
  };

  return (
    <div className="min-h-screen bg-slate-50 flex flex-col md:flex-row font-sans">
      {/* Sidebar Navigasi */}
      <aside className="w-full md:w-64 bg-white border-r border-gray-200 flex flex-col flex-shrink-0 md:h-screen">
        <div className="p-6 border-b border-gray-100 flex items-center space-x-3">
          <div className="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center text-white shadow-sm">
            <FileText size={24} />
          </div>
          <div>
            <h1 className="text-lg font-bold text-gray-900 leading-tight">e-Surat</h1>
            <p className="text-xs text-gray-500">Sistem Pengurusan</p>
          </div>
        </div>
        
        <nav className="flex-1 p-4 space-y-1 overflow-y-auto">
          <button 
            onClick={() => handleNavigation('dashboard')}
            className={`w-full flex items-center space-x-3 px-4 py-3 rounded-lg transition text-left text-sm font-medium ${currentView === 'dashboard' ? 'bg-blue-50 text-blue-700' : 'text-gray-600 hover:bg-gray-50'}`}
          >
            <LayoutDashboard size={20} />
            <span>Papan Pemuka</span>
          </button>
          
          <div className="pt-6 pb-2 px-4 text-xs font-bold text-gray-400 uppercase tracking-wider">
            Peti Mel
          </div>
          
          <button 
            onClick={() => handleNavigation('masuk')}
            className={`w-full flex items-center justify-between px-4 py-3 rounded-lg transition text-left text-sm font-medium ${currentView === 'masuk' ? 'bg-blue-50 text-blue-700' : 'text-gray-600 hover:bg-gray-50'}`}
          >
            <div className="flex items-center space-x-3">
              <Inbox size={20} />
              <span>Surat Masuk</span>
            </div>
            {totalMasuk > 0 && (
              <span className="bg-blue-100 text-blue-600 py-0.5 px-2.5 rounded-full text-xs font-bold">{totalMasuk}</span>
            )}
          </button>
          
          <button 
            onClick={() => handleNavigation('keluar')}
            className={`w-full flex items-center space-x-3 px-4 py-3 rounded-lg transition text-left text-sm font-medium ${currentView === 'keluar' ? 'bg-blue-50 text-blue-700' : 'text-gray-600 hover:bg-gray-50'}`}
          >
            <Send size={20} />
            <span>Surat Keluar</span>
          </button>

          <div className="pt-6 pb-2 px-4 text-xs font-bold text-gray-400 uppercase tracking-wider">
            Tindakan
          </div>

          <button 
            onClick={() => handleNavigation('cipta')}
            className={`w-full flex items-center space-x-3 px-4 py-3 rounded-lg transition text-left text-sm font-medium ${currentView === 'cipta' ? 'bg-blue-50 text-blue-700' : 'text-gray-600 hover:bg-gray-50'}`}
          >
            <PlusCircle size={20} />
            <span>Cipta Surat Baharu</span>
          </button>
        </nav>

        <div className="p-4 border-t border-gray-100">
          <div className="flex items-center space-x-3 p-3 rounded-xl bg-gray-50 border border-gray-200 cursor-pointer hover:bg-gray-100 transition">
            <div className="w-9 h-9 rounded-full bg-blue-200 flex items-center justify-center text-blue-700 shadow-inner">
              <User size={18} />
            </div>
            <div className="flex-1 min-w-0">
              <p className="text-sm font-bold text-gray-900 truncate">Pentadbir Sistem</p>
              <p className="text-xs text-gray-500 truncate">admin@kerajaan.my</p>
            </div>
          </div>
        </div>
      </aside>

      {/* Kawasan Utama (Main Content) */}
      <main className="flex-1 flex flex-col h-screen overflow-hidden">
        {/* Header Top */}
        <header className="bg-white h-16 border-b border-gray-200 flex items-center justify-between px-6 flex-shrink-0">
          <div className="flex-1"></div>
          <div className="flex items-center space-x-4">
            <button className="relative p-2 text-gray-400 hover:text-gray-600 transition bg-gray-50 rounded-full border border-gray-100">
              <Bell size={18} />
              <span className="absolute top-1.5 right-1.5 w-2.5 h-2.5 bg-red-500 rounded-full border-2 border-white"></span>
            </button>
          </div>
        </header>

        {/* Dynamic Content */}
        <div className="flex-1 overflow-y-auto p-6 md:p-8">
          {renderContent()}
        </div>
      </main>
    </div>
  );
}
