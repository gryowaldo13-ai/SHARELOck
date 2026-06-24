# 🔥 Setup Firebase untuk ShareLock

## Langkah 1: Buat Firebase Project

1. **Buka:** https://console.firebase.google.com/
2. **Klik:** "Add project" atau "Tambah project"
3. **Nama project:** `sharelock-tracker` (atau nama lain)
4. **Google Analytics:** Boleh diaktifkan atau tidak (optional)
5. **Klik:** "Create project"

---

## Langkah 2: Setup Realtime Database

1. Di Firebase Console, pilih project Anda
2. **Klik menu** "Build" → "Realtime Database"
3. **Klik:** "Create Database"
4. **Location:** Pilih lokasi terdekat (misalnya: Singapore untuk Asia)
5. **Security rules:** Pilih **"Start in test mode"** (untuk development)
6. **Klik:** "Enable"

### ⚠️ Security Rules (Nanti Akan Diupdate)

Untuk sekarang, gunakan test mode:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

**PENTING:** Ini tidak aman untuk production! Nanti kita update dengan rules yang lebih baik.

---

## Langkah 3: Register Web App

1. Di Firebase Console, **klik icon</> (Web)** di bagian atas
2. **App nickname:** `sharelock-web`
3. **Centang:** "Also set up Firebase Hosting" (optional)
4. **Klik:** "Register app"
5. **Copy kode Firebase config** yang muncul

Akan terlihat seperti ini:

```javascript
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "sharelock-tracker.firebaseapp.com",
  databaseURL: "https://sharelock-tracker-default-rtdb.firebaseio.com",
  projectId: "sharelock-tracker",
  storageBucket: "sharelock-tracker.appspot.com",
  messagingSenderId: "123...",
  appId: "1:123..."
};
```

---

## Langkah 4: Update File Project

### A. Update `index.html`

Ganti bagian Firebase config (sekitar baris 10-20):

```javascript
const firebaseConfig = {
    apiKey: "PASTE_YOUR_API_KEY_HERE",
    authDomain: "PASTE_YOUR_AUTH_DOMAIN",
    databaseURL: "PASTE_YOUR_DATABASE_URL",
    projectId: "PASTE_YOUR_PROJECT_ID",
    storageBucket: "PASTE_YOUR_STORAGE_BUCKET",
    messagingSenderId: "PASTE_YOUR_SENDER_ID",
    appId: "PASTE_YOUR_APP_ID"
};
```

### B. Update `ad.html`

Ganti Firebase config yang sama di file ini.

### C. Update `locations.html`

Ganti Firebase config yang sama di file ini.

---

## Langkah 5: Update Security Rules (Production Ready)

Setelah testing berhasil, update security rules di Firebase Console:

```json
{
  "rules": {
    "links": {
      "$linkId": {
        ".read": true,
        ".write": true,
        "locations": {
          ".read": true,
          ".write": true
        },
        "clicks": {
          ".read": true,
          ".write": true
        }
      }
    }
  }
}
```

Rules ini memungkinkan:
- ✅ Semua orang bisa baca data
- ✅ Semua orang bisa tulis data (karena anonymous tracking)
- ⚠️ Tidak ada authentication (sesuai requirement)

### Untuk Security Lebih Baik (Optional):

```json
{
  "rules": {
    "links": {
      "$linkId": {
        ".read": true,
        "title": { ".write": "!data.exists()" },
        "description": { ".write": "!data.exists()" },
        "template": { ".write": "!data.exists()" },
        "created": { ".write": "!data.exists()" },
        "locations": {
          ".write": true
        },
        "clicks": {
          ".write": "newData.val() === data.val() + 1 || !data.exists()"
        }
      }
    }
  }
}
```

Rules ini:
- ✅ Lokasi bisa ditambahkan
- ✅ Clicks hanya bisa increment
- ✅ Data link tidak bisa diubah setelah dibuat

---

## Langkah 6: Testing

1. **Commit dan push** perubahan:
   ```bash
   git add .
   git commit -m "Add Firebase integration"
   git push origin main
   ```

2. **Deploy ke Vercel:**
   ```bash
   npx vercel --prod
   ```

3. **Test di browser:**
   - Buka https://sharelock-two.vercel.app
   - Buat link baru
   - Buka link di device/browser lain
   - Klik "Klaim Sekarang"
   - Kembali ke dashboard
   - Klik "📍 Lokasi"
   - ✅ **Lokasi akan muncul!**

---

## Troubleshooting

### Error: "Firebase not initialized"
- Pastikan Firebase SDK ter-load sebelum script lain
- Cek console browser (F12) untuk error detail

### Error: "Permission denied"
- Cek Firebase Database Rules
- Pastikan rules allow read/write

### Data tidak tersimpan
- Cek Firebase Console → Realtime Database
- Lihat apakah data muncul di database
- Cek browser console untuk error

### CORS Error
- Pastikan domain Vercel sudah terdaftar di Firebase
- Di Firebase Console → Project Settings → Add domain

---

## 📊 Monitoring Data

Untuk melihat data real-time di Firebase:

1. Buka Firebase Console
2. Klik "Realtime Database"
3. Lihat struktur data:
   ```
   links/
     ad_1234567890_xyz/
       title: "..."
       description: "..."
       clicks: 5
       locations/
         -N1234abc: {latitude, longitude, ...}
         -N1234def: {latitude, longitude, ...}
   ```

---

## 💰 Biaya Firebase

### Spark Plan (Gratis):
- ✅ 1 GB stored data
- ✅ 10 GB/month bandwidth
- ✅ 100k concurrent connections
- ✅ Cukup untuk 10,000+ tracking per bulan

### Upgrade ke Blaze (Pay as you go):
- Hanya bayar jika melebihi free tier
- ~$5/GB untuk bandwidth tambahan

---

## ✅ Checklist Setup

- [ ] Buat Firebase project
- [ ] Enable Realtime Database
- [ ] Register web app
- [ ] Copy Firebase config
- [ ] Update `index.html`
- [ ] Update `ad.html`
- [ ] Update `locations.html`
- [ ] Commit & push ke GitHub
- [ ] Deploy ke Vercel
- [ ] Test tracking dari device berbeda
- [ ] Update security rules untuk production

---

**Butuh bantuan?** Tanyakan jika ada error atau masalah saat setup!
