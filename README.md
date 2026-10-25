# higieka.web.id

Situs portofolio pribadi As Shadiq Nur.

## Struktur

Situs ini berupa satu halaman statis tanpa tahap build dan tanpa dependensi
selain berkas font yang dimuat dari Google Fonts.

| Berkas         | Keterangan                                   |
| -------------- | -------------------------------------------- |
| `index.html`   | Seluruh halaman: markup, gaya, dan ikon       |
| `netlify.toml` | Konfigurasi deploy dan tajuk keamanan         |
| `robots.txt`   | Izin perayapan mesin pencari                  |
| `sitemap.xml`  | Peta situs                                    |

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
