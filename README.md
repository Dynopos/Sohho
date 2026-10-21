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
- **WhatsApp**: nombor `60178941093` digunakan dalam `index.html`. Semua butang bertanda `data-wa` membuka WhatsApp
  dengan mesej pertanyaan yang sudah diisi (lokasi, jenis kerja, ketinggian, tarikh/tempoh).
- **Gambar baharu**: mampatkan dahulu, contohnya:

      convert asal.jpg -resize '1600x1600>' -strip -interlace Plane -quality 80 assets/nama.jpg
      convert asal.jpg -resize '800x800>'  -strip -interlace Plane -quality 76 assets/nama-sm.jpg

## Lagu (chorus)
`assets/chorus.mp3` ialah bahagian chorus lagu "Sohho Skylift" (saat 23.6–32.1 lagu asal, ~8.6 saat). Ia mula berbunyi pada
sentuhan/klik pertama di mana-mana bahagian laman — pelayar tidak membenarkan audio berbunyi sebelum pelawat berinteraksi,
dan skrol sahaja tidak memulakannya. Butang bulat kecil di kiri bawah memainkan/menghentikan lagu.
Untuk tukar, ganti fail itu dengan nama yang sama, contohnya:

    ffmpeg -ss 23.6 -to 32.15 -i lagu.m4a -map 0:a:0 -af "afade=t=in:st=0:d=0.08,afade=t=out:st=8.1:d=0.45" -c:a libmp3lame -b:a 128k assets/chorus.mp3
