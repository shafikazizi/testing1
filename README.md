# Laman Pinjaman Kenderaan - Pejabat (Starter)

Ini adalah aplikasi demo untuk mengurus permohonan pinjaman kenderaan pejabat. Versi ini adalah prototaip ringkas dengan penyimpanan di memori.

Cara gunakan (tempatan):

1. Pasang dependensi:
   ```
   npm install
   ```

2. Jalankan server:
   ```
   npm start
   ```

3. Buka di pelayar:
   ```
   http://localhost:3000
   ```

Apa yang disediakan:
- Borang permohonan (frontend)
- API asas: /api/apply, /api/applications, /api/applications/:id/action
- Penyimpanan sementara (in-memory). Untuk produksi: sambungkan ke DB (Postgres/MySQL/MongoDB).

Langkah seterusnya yang saya boleh bantu:
- sambungkan ke pangkalan data dan buat migrasi,
- tambah autentikasi (SSO/LDAP/username-pass),
- tambah peranan (pegawai, pelulus), notifikasi e-mel, dan muat naik dokumen.