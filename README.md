# SOHHO — Laman Web

Laman web satu halaman (HTML/CSS/JS tulen, tiada build) untuk SOHHO, perkhidmatan sewa skylift di Pantai Timur.
Reka bentuk mengikut gaya laman Naami Stable (loader, hero penuh skrin, marquee, kad bergerak, galeri lightbox, CTA berombak).

## Struktur
- `index.html` — keseluruhan laman (gaya & skrip sebaris)
- `assets/` — logo (`logo.svg`) dan gambar kerja skylift (`*.jpg` saiz penuh, `*-sm.jpg` untuk galeri)
- `CNAME` — domain GitHub Pages (`sohho.my`)

## Kemas kini biasa
- **Harga**: cari bahagian `id="harga"` dalam `index.html`. Setiap kad ada ketinggian, harga dan teks WhatsApp
  (`data-wa="skylift 15 meter (RM550)"`). Bar ketinggian di kad dikawal oleh `--h` (ketinggian ÷ 44).
- **WhatsApp**: nombor `60178941093` digunakan dalam `index.html`. Semua butang bertanda `data-wa` membuka WhatsApp
  dengan mesej pertanyaan yang sudah diisi (lokasi, jenis kerja, ketinggian, tarikh/tempoh).
- **Gambar baharu**: mampatkan dahulu, contohnya:

      convert asal.jpg -resize '1600x1600>' -strip -interlace Plane -quality 80 assets/nama.jpg
      convert asal.jpg -resize '800x800>'  -strip -interlace Plane -quality 76 assets/nama-sm.jpg
