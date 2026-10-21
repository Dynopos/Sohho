# SOHHO — Laman Web

Laman web satu halaman (HTML/CSS/JS tulen, tiada build) untuk SOHHO, perkhidmatan sewa skylift di Pantai Timur.
Reka bentuk mengikut gaya laman Naami Stable (loader, hero penuh skrin, marquee, kad bergerak, galeri lightbox, CTA berombak).

## Struktur
- `index.html` — keseluruhan laman (gaya & skrip sebaris)
- `assets/` — logo (`logo.png`, `favicon.png`), gambar kerja skylift (`*.jpg` saiz penuh, `*-sm.jpg` untuk galeri)
  dan sijil pendaftaran (`sijil-*.jpg`, maklumat peribadi pegawai disembunyikan — jangan muat naik PDF asal)
- `CNAME` — domain GitHub Pages (`sohho.my`)

## Kemas kini biasa
- **Harga**: cari bahagian `id="harga"` dalam `index.html`. Setiap kad ada ketinggian, harga dan teks WhatsApp
  (`data-wa="skylift 15 meter (RM550)"`). Bar ketinggian di kad dikawal oleh `--h` (ketinggian ÷ 44).
- **WhatsApp**: nombor `60139981855` digunakan dalam `index.html`. Semua butang bertanda `data-wa` membuka WhatsApp
  dengan mesej pertanyaan yang sudah diisi (lokasi, jenis kerja, ketinggian, tarikh/tempoh).
- **Galeri**: setiap gambar ialah satu `<button class="g-item" data-cat="...">` dalam bahagian `id="galeri"`. Kategori
  (`bangunan`, `iklan`, `struktur`, `dalaman`, `pokok`) dipadankan dengan butang penapis; tambah `wide` pada kelas untuk
  gambar panorama. 9 gambar pertama (8 di telefon) dipaparkan dahulu, selebihnya selepas butang "Lihat semua".
- **Gambar baharu**: mampatkan dahulu (`kerja-NN.jpg` saiz penuh, `kerja-NN-sm.jpg` lebar 720px), contohnya:

      convert asal.jpg -resize '1600x1600>' -strip -interlace Plane -quality 80 assets/nama.jpg
      convert asal.jpg -resize '720x>' -strip -interlace Plane -quality 74 assets/nama-sm.jpg

## Lagu (chorus)
`assets/chorus.mp3` ialah chorus lagu "Sohho Skylift" yang diulang hingga ~2 minit (16 pusingan × 7.575 saat, iaitu
4 bar pada ~127 BPM, mula saat 23.70 lagu asal), disambung tepat pada rentak dengan crossfade 20ms dan fade-out 3 saat
di hujung. Ia mula berbunyi pada sentuhan/klik pertama di mana-mana bahagian laman — pelayar tidak membenarkan audio
berbunyi sebelum pelawat berinteraksi, dan skrol sahaja tidak memulakannya. Butang bulat kecil di kiri bawah
memainkan/menghentikan lagu. Fail hanya dimuat turun bila mula dimainkan.

Untuk bina semula: potong satu pusingan (`ffmpeg -ss 23.70 -t 7.62 -i lagu.m4a -ar 48000 -ac 2 seg.wav`), ulang 16 kali
dengan sambungan setiap 7.575 saat, kemudian `ffmpeg -i loop.wav -c:a libmp3lame -b:a 96k assets/chorus.mp3`.
