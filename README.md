# higieka.web.id

Situs portofolio pribadi As Shadiq Nur.

## Struktur

Situs ini berupa satu halaman statis tanpa tahap build dan tanpa dependensi
selain berkas font yang dimuat dari Google Fonts.

| Berkas         | Keterangan                                   |
| -------------- | -------------------------------------------- |
| `index.html`   | Seluruh halaman: markup, gaya, skrip, ikon    |
| `netlify.toml` | Konfigurasi deploy dan tajuk keamanan         |
| `robots.txt`   | Izin perayapan mesin pencari                  |
| `sitemap.xml`  | Peta situs                                    |
| `kkn/index.html` | Rancangan dashboard admin LKH KKN (data contoh) |
| `kkn/Templat-Impor-LKH-KKN.xlsx` | Templat Excel impor data, diunduh dari halaman rancangan |
| `kkn/daftar/index.html` | Formulir uji coba pendaftaran KKN (Netlify Forms) |

## Menjalankan secara lokal

```sh
python3 -m http.server 8000
```

Lalu buka `http://localhost:8000`.

## Deploy

Situs di-host di Netlify dan dideploy otomatis dari branch `main`.
Direktori publikasi adalah akar repositori, tanpa perintah build.

Untuk menghubungkan domain, arahkan `higieka.web.id` ke Netlify melalui
pengaturan DNS di panel registrar, lalu tambahkan domain tersebut sebagai
custom domain pada situs Netlify.
