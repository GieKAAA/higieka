# higieka.web.id

Situs portofolio pribadi As Shadiq Nur.

## Struktur

Situs ini berupa satu halaman statis tanpa tahap build dan tanpa dependensi
selain berkas font yang dimuat dari Google Fonts.

| Berkas         | Keterangan                                   |
| -------------- | -------------------------------------------- |
| `index.html`   | Seluruh halaman: markup, gaya, skrip, ikon    |
| `CNAME`        | Domain khusus untuk GitHub Pages              |
| `.nojekyll`    | Menyajikan berkas apa adanya, tanpa Jekyll    |
| `robots.txt`   | Izin perayapan mesin pencari                  |
| `sitemap.xml`  | Peta situs                                    |
| `kkn/index.html` | Rancangan dashboard admin LKH KKN (hanya menampilkan berkas yang dimuat) |
| `kkn/Templat-Impor-LKH-KKN.xlsx` | Templat Excel impor data, diunduh dari halaman rancangan |
| `kkn/daftar/index.html` | Formulir uji coba pendaftaran KKN (pengiriman tidak aktif) |

## Menjalankan secara lokal

```sh
python3 -m http.server 8000
```

Lalu buka `http://localhost:8000`.

## Deploy

Situs di-host di GitHub Pages dan tayang otomatis setiap ada perubahan pada
branch `main`. Yang dipublikasikan adalah akar repositori, tanpa perintah build.

Domain `higieka.web.id` diarahkan lewat DNS di panel registrar (nameserver
`dns1.nyanhosting.id` dan `dns2.nyanhosting.id`): empat catatan A untuk akar
domain (`185.199.108.153` sampai `185.199.111.153`) dan satu CNAME `www` ke
`giekaaa.github.io`. Berkas `CNAME` di akar repositori menetapkan domain itu
pada GitHub Pages; jangan dihapus.

Situs ini dipindahkan dari Netlify pada 14 November 2026. GitHub Pages tidak
mendukung tajuk HTTP khusus dan tidak menyimpan isian formulir.
