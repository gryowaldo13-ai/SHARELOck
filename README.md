# 🎯 Website Generator Link Iklan dengan Location Tracking

Website ini memungkinkan Anda untuk membuat link iklan dummy yang dapat melacak lokasi live dari perangkat yang mengklik link tersebut.

## ✨ Fitur

- 📝 **Generator Link Iklan** - Buat link iklan dengan judul dan deskripsi custom
- 🎨 **Multiple Templates** - Pilih dari berbagai template iklan (Promo, Hadiah, Info, Urgent)
- 📍 **Location Tracking** - Lacak lokasi GPS dari pengunjung yang mengklik link
- 📊 **Dashboard Analytics** - Lihat statistik klik dan data lokasi
- 💾 **Local Storage** - Data tersimpan di browser (tidak perlu database)
- 🗺️ **Google Maps Integration** - Link langsung ke Google Maps untuk setiap lokasi

## 🚀 Cara Menggunakan

### 1. Setup

Cukup buka file `index.html` di browser Anda. Tidak perlu instalasi atau server!

```bash
# Buka langsung di browser
start index.html        # Windows
open index.html         # MacOS
xdg-open index.html     # Linux
```

Atau gunakan live server untuk pengalaman yang lebih baik:

```bash
# Jika Anda punya Python
python -m http.server 8000

# Atau gunakan npx
npx serve
```

### 2. Membuat Link Iklan

1. Buka `index.html`
2. Isi form dengan:
   - **Judul Iklan**: Judul yang menarik perhatian
   - **Deskripsi**: Penjelasan singkat tentang iklan
   - **Template**: Pilih jenis template iklan
3. Klik "Generate Link Iklan"
4. Copy link yang dihasilkan

### 3. Membagikan Link

- Share link yang sudah di-generate ke target audience
- Link akan membuka halaman iklan yang menarik
- Ketika seseorang klik tombol "Klaim Sekarang", lokasi mereka akan terekam

### 4. Melihat Data Lokasi

1. Kembali ke dashboard (`index.html`)
2. Lihat tabel "Daftar Link yang Dibuat"
3. Klik tombol "📍 Lokasi" untuk melihat detail lokasi
4. Data yang terekam meliputi:
   - Latitude & Longitude
   - Akurasi lokasi (dalam meter)
   - Platform perangkat
   - Browser yang digunakan
   - Bahasa sistem
   - Waktu klik

## 📁 Struktur File

```
├── index.html          # Dashboard utama & generator link
├── ad.html            # Halaman iklan yang akan diklik
├── locations.html     # Halaman untuk melihat data lokasi
└── README.md          # Dokumentasi ini
```

## 🔒 Privasi & Keamanan

⚠️ **PENTING - UNTUK TUJUAN EDUKASI SAJA**

Website ini dibuat untuk tujuan **edukasi dan demonstrasi** tentang:
- Cara kerja geolocation API
- Tracking location dengan JavaScript
- Privacy concern dalam web development

**JANGAN GUNAKAN UNTUK:**
- Tracking orang tanpa izin
- Aktivitas ilegal atau merugikan
- Melanggar privasi orang lain

## 🛠️ Teknologi yang Digunakan

- **HTML5** - Struktur website
- **CSS3** - Styling dan animasi
- **JavaScript (Vanilla)** - Logic dan functionality
- **Geolocation API** - Untuk mendapatkan lokasi pengguna
- **LocalStorage** - Penyimpanan data di browser

## 📱 Browser Support

- ✅ Chrome/Edge (Recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Opera
- ⚠️ Geolocation memerlukan HTTPS atau localhost

## 💡 Tips & Trik

1. **Akurasi Lokasi**: Akurasi tergantung pada perangkat dan pengaturan GPS
2. **Permission**: User harus memberikan permission untuk akses lokasi
3. **HTTPS**: Untuk production, gunakan HTTPS agar geolocation berfungsi
4. **Mobile**: Akurasi lebih baik di perangkat mobile dengan GPS

## 🔧 Customization

Anda dapat dengan mudah customize:

### Mengubah Warna Theme
Edit bagian CSS di masing-masing file HTML:

```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Menambah Template Baru
Edit object `templates` di file `ad.html`:

```javascript
const templates = {
    custom: { icon: '✨', badge: 'CUSTOM', class: 'template-custom' }
};
```

### Mengubah Text
Semua text dapat diubah langsung di HTML atau JavaScript

## 📝 Data yang Dikumpulkan

Setiap klik akan merekam:

- ✅ Koordinat GPS (Latitude/Longitude)
- ✅ Akurasi lokasi
- ✅ Timestamp (Waktu klik)
- ✅ User Agent (Browser info)
- ✅ Platform (OS)
- ✅ Bahasa sistem

## ⚡ Future Improvements

Ide untuk pengembangan lebih lanjut:

- [ ] Export data ke CSV/JSON
- [ ] Visualisasi peta dengan markers
- [ ] Backend integration (PHP/Node.js)
- [ ] Database storage (MySQL/MongoDB)
- [ ] User authentication
- [ ] Email notifications
- [ ] Analytics dashboard yang lebih detail
- [ ] QR Code generator untuk link

## 🐛 Troubleshooting

**Lokasi tidak terdeteksi?**
- Pastikan browser mendukung Geolocation API
- Cek permission browser untuk akses lokasi
- Gunakan HTTPS atau localhost
- Pastikan GPS/Location Services aktif di perangkat

**Data tidak tersimpan?**
- Jangan gunakan mode incognito/private
- Cek apakah LocalStorage diaktifkan di browser
- Pastikan tidak ada extension yang block storage

## 📜 License

MIT License - Bebas digunakan untuk tujuan edukasi dan pembelajaran.

## ⚠️ Disclaimer

Penggunaan tool ini sepenuhnya tanggung jawab pengguna. Developer tidak bertanggung jawab atas penyalahgunaan tool ini. Selalu hormati privasi orang lain dan patuhi hukum yang berlaku.

---

Dibuat dengan ❤️ untuk tujuan edukasi
