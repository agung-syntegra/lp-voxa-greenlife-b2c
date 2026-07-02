# Voxa Greenlife B2C — Landing

Landing page konsumen baterai sepeda listrik B2C. Single-page HTML statis, disajikan lewat Express kecil supaya siap deploy ke Railway (atau host Node manapun).

Duplikat dari `lp-voxa-greenlife-b2b` — struktur & tampilan identik, port default berbeda supaya bisa jalan berdampingan.

## Local dev

```bash
npm install
npm start
# buka http://localhost:5758
```

Port default `5758` dipilih supaya tidak bentrok dengan project lain di `C:\SYNTEGRA`
(3000 = website-syntegra / lp-syntia / mom-landing, 3001 = syntegra-pos, 5757 = lp-voxa-greenlife-b2b).
Override dengan `PORT=6000 npm start`. Di Railway, `$PORT` di-inject otomatis
dan mengabaikan default ini.

## Deploy ke Railway

1. Push repo ini ke GitHub (buat repo baru `syntegraindonesia/lp-voxa-greenlife-b2c`).
2. Buka [railway.app](https://railway.app) → **New Project** → **Deploy from GitHub repo** → pilih `lp-voxa-greenlife-b2c`.
3. Railway auto-detect Node (via Nixpacks) dan jalankan `npm start`.
4. **Settings → Networking → Generate Domain** untuk URL publik `*.up.railway.app`.

Config `railway.json` sudah aktifkan healthcheck di `/health`, restart on failure (max 3x).

## Struktur

```
lp-voxa-greenlife-b2c/
├─ index.html      # halaman utama
├─ server.js       # Express static server (pakai $PORT dari Railway)
├─ package.json
├─ railway.json    # config deploy
└─ .gitignore
```

## Kustomisasi

- **Palet & font** ada di blok `:root { ... }` di dalam `<style>` `index.html`.
  Skema saat ini: forest green (`--forest #0f3a26`), amber CTA (`--amber #f2b91c`),
  cream background (`--cream #eef3e6`), leaf accent (`--leaf #3fb968`).
- **Copy** semuanya inline dalam Bahasa Indonesia — bisa cari-ganti string
  `Voxa Greenlife` untuk rebrand.
- **Katalog produk** di section `#katalog` (18 varian: LFP + NMC + SLA × 6 voltage/capacity).
  Ubah/hapus tile sesuai stok riil.
