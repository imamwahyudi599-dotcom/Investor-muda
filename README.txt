INVESTOR MUDA — WEBSITE STATIS + SCAFFOLD INTEGRASI MARKET

FITUR WEBSITE
- Beranda edukasi investasi, komunitas, dan karier
- Market Explorer dengan pencarian kode/nama emiten melalui endpoint instrumen
- Area harga terbaru (quote) dan grafik historis penutupan harian
- Netlify Function sebagai proxy agar API key tidak terekspos ke browser
- Tautan ke sumber data dan portal lisensi BEI

PENTING: IZIN DAN BIAYA DATA
1. BEI menyatakan menyediakan produk Market Data real-time, delayed, end-of-day, dan historical melalui skema lisensi. Syarat penggunaan website BEI melarang redistribusi komersial tanpa izin tertulis dan melarang scraping/crawling. Lihat https://data.idx.co.id/ dan https://idx.co.id/id/syarat-penggunaan/.
2. Api.co.id mengiklankan paket gratis 500 hit/bulan dan endpoint historis harian; endpoint quote/harga terbaru tercantum mulai paket Starter. Harga paket dan cakupan dapat berubah. Lihat https://api.co.id/api-saham-indonesia/ dan https://docs.api.co.id/.
3. Halaman pemasaran API bukan pengganti kontrak lisensi. Sebelum data ditampilkan untuk publik, minta konfirmasi tertulis dari penyedia mengenai hak display/redistribusi di website publik, atribusi yang wajib, caching, penggunaan komersial/iklan, dan batasan data turunan. Jika perlu, konfirmasikan juga kewajiban lisensi kepada BEI.
4. Integrasi dilindungi compliance gate: API tidak mengirim data kecuali environment variable MARKET_PUBLIC_DISPLAY_APPROVED bernilai true. Jangan mengaktifkannya sebelum izin penggunaan publik dikonfirmasi.

CARA UJI / DEPLOY KE NETLIFY
1. Upload folder ini ke repositori GitHub atau deploy melalui Netlify dengan konfigurasi build yang mendukung Netlify Functions. Netlify Drop sederhana untuk file statis mungkin tidak cukup untuk menjalankan functions; gunakan deploy dari repositori Git atau CLI Netlify.
2. Di Netlify: Site configuration > Environment variables, tambahkan:
   API_CO_ID_KEY = API key dari dashboard penyedia (jangan pernah ditaruh di index.html).
   MARKET_PUBLIC_DISPLAY_APPROVED = true hanya setelah hak display publik dikonfirmasi tertulis.
3. Deploy ulang setelah menambahkan environment variables.
4. Paket gratis Api.co.id menurut halaman produk: 500 hit/bulan; endpoint Daily historis tercantum tersedia pada Free, sedangkan Quote/harga terbaru tercantum mulai Starter (harga pada halaman yang dicek: Rp149.000/bulan). Cek ulang paket saat mendaftar.
5. Pertama-tama uji endpoint daftar instrumen dan history satu saham. Setelah format respons nyata diterima, sesuaikan parser frontend bila schema provider berubah.

BATASAN IMPLEMENTASI SAAT INI
- Ini adalah integrasi teknis awal, belum terhubung ke API key pengguna dan belum diuji terhadap respons API akun nyata.
- Daftar instrumen diambil dari API; jika format respons berubah, parser mungkin perlu disesuaikan.
- Grafik dibuat dari data harian yang tersedia; opsi rentang memfilter titik yang dikembalikan API, bukan menjamin histori tertentu.
- Harga quote mungkin gagal di paket gratis; UI menampilkan pesan error alih-alih membuat harga palsu.
- Data publikasi wajib memiliki izin dan label sumber/timestamp sesuai kontrak provider.

WHATSAPP
Ganti nomor contoh 6281234567890 di index.html dengan nomor WhatsApp resmi sebelum website dipublikasikan.
