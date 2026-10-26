# Konteks proyek higieka.web.id

Berkas ini berisi konteks yang perlu diketahui sebelum mengerjakan repositori ini.

## Apa ini

Situs portofolio pribadi As Shadiq Nur, mahasiswa Teknik Informatika UIN Alauddin
Makassar. Satu halaman statis, tanpa tahap build, tanpa dependensi selain font
yang dimuat dari Google Fonts.

Domain: `higieka.web.id` (registrar NyanHosting, domain saja tanpa hosting).
Hosting: Netlify, deploy otomatis dari branch `main`, publish directory `.`.

## Struktur

| Berkas         | Keterangan                                  |
| -------------- | ------------------------------------------- |
| `index.html`   | Seluruh halaman: markup, gaya, skrip, ikon  |
| `netlify.toml` | Konfigurasi deploy dan tajuk keamanan       |
| `robots.txt`   | Izin perayapan mesin pencari                |
| `sitemap.xml`  | Peta situs                                  |

Seluruh CSS dan JavaScript berada inline di dalam `index.html`. Jangan memecahnya
menjadi berkas terpisah tanpa diminta; sifat satu-berkas adalah keputusan desain
yang disengaja.

## Arah desain

Atas permintaan pemilik situs, tampilan dirancang agar sederhana, elegan, dan
berwibawa, serta tidak berkesan dibuat oleh AI. Warna aksen adalah biru; jangan
dikembalikan ke ungu.

- Hero berupa langit malam penuh layar dengan bulan besar yang digambar sebagai
  SVG inline (bukan foto). Judul besar di kiri bawah, pil surel putih, dan dua
  kartu kaca (`.glass`, `backdrop-filter`) di kanan bawah
- Navigasi berupa pil kaca yang melayang di bagian atas layar
- Bagian di bawah hero memakai neumorphism gelap di atas latar `#151A24`:
  permukaan timbul (`--raise`, `.surface`) dan sumur cekung (`--inset`, `.well`)
  dengan cahaya dari kiri atas. Tombol yang aktif tampil tertekan (`--inset-sm`)
- Aksen utama biru `#3B82F6`, varian terang `#93C5FD`, varian gelap `#2563EB`
  untuk latar tombol bertulisan putih (aksen utama tidak memenuhi kontras AA)
- Amber `#F2A93B` khusus sebagai penanda status aktif
- Seluruh teks memakai Plus Jakarta Sans; JetBrains Mono hanya untuk data seperti
  angka, koordinat, kode, dan daftar teknologi

Warna dan bayangan ditetapkan sebagai variabel pada `:root` (`--accent`,
`--accent-rgb`, `--accent-lite`, `--accent-deep`, `--raise`, `--inset`, dan
seterusnya); gunakan variabel tersebut, bukan nilai mentah.

Hindari pola yang lazim pada halaman buatan AI: label kecil berkotak dengan huruf
kapital renggang, bingkai jendela tiruan bertitik tiga, judul aforistik, tanda pisah
panjang, dan daftar bertiga yang berulang. Judul bagian cukup berupa kata biasa
seperti "Tentang", "Proyek", dan "Kontak".

Ketentuan kualitas yang harus dipertahankan pada setiap perubahan:

- Responsif hingga lebar layar ponsel, tanpa gulir horizontal
- `prefers-reduced-motion` dihormati
- Cincin fokus papan ketik terlihat jelas
- Kontras warna memenuhi WCAG AA

## Interaksi dan visual proyek

Skrip inline di akhir `index.html` menjalankan beberapa interaksi: demo Lokasi pada
panel proyek Lokasi (joystick dapat diseret atau digerakkan dengan tombol panah,
peta dapat diklik), tahapan verifikasi wajah LKH KKN, tab laporan pemeriksa PKTI,
pilihan platform pada rekaman asal-usul korpus, tombol salin surel, jam WITA,
sorotan menu yang meluncur ke menu yang ditunjuk atau yang sedang dibaca, angka 192
yang menghitung naik, dan animasi muncul saat digulir.

Bulan pada hero bergerak dengan beberapa cara:

- Sisi terangnya mengikuti kursor, seolah kursor adalah matahari, sehingga fasenya
  berubah. Tanpa tetikus, fasenya berubah mengikuti guliran halaman.
- Bayangan bulan berada pada elemen `.moon__shade` di luar SVG dan dikendalikan
  oleh variabel `--lx`, `--ly`, dan `--k`, agar perubahan cahaya tidak menggambar
  ulang filter SVG. Gelung animasinya berbasis waktu dan berhenti saat cahaya tenang.
- Bulan melayang perlahan, pendarnya berdenyut, bintang berkelip, sesekali ada
  bintang jatuh, dan bulan bergerak paralaks saat digulir.

- Situs harus tetap utuh tanpa JavaScript. Kelas `js` pada `html` dipasang oleh
  skrip kecil di `head`; gaya yang menyembunyikan konten hanya berlaku di bawahnya.
- Animasi hanya berjalan di bawah `prefers-reduced-motion: no-preference`.
- Gelung animasi demo Lokasi berhenti saat joystick diam, meniru aplikasi aslinya.

Setiap kartu proyek memuat visual yang merupakan ilustrasi, bukan tangkapan layar
asli, dan keterangannya menyatakan hal itu. Jangan menyajikan ilustrasi seolah-olah
tangkapan layar asli. Jika pemilik situs memberikan tangkapan layar asli, visual
tersebut boleh diganti; periksa dahulu agar tidak memuat data pribadi.

## Gaya komunikasi

Saat berbicara langsung dengan pemilik repositori di dalam sesi, gunakan bahasa
Indonesia percakapan yang santai dan akrab sebagaimana berbicara dengan teman
dekat, serta sapa dia dengan panggilan "mate". Nada yang kaku dan formal tidak
dikehendaki dalam percakapan.

Ketentuan tersebut berlaku khusus untuk percakapan. Seluruh teks yang masuk ke
dalam berkas — isi situs, pesan commit, maupun dokumentasi — tetap ditulis dalam
bahasa Indonesia ragam formal sebagaimana diatur pada bagian Bahasa di bawah.

## Bahasa

Seluruh teks situs dan pesan commit ditulis dalam bahasa Indonesia ragam formal.
Atribut `lang` pada elemen `html` adalah `id`.

## Isi

Jangan mencantumkan karya milik orang lain pada situs ini. Beberapa judul skripsi
yang pernah dibahas pemilik situs adalah milik rekannya, bukan miliknya sendiri.

## Verifikasi sebelum push

Periksa struktur HTML sebelum mendorong perubahan, lalu buka halaman di peramban
untuk memastikan konsol bebas galat dan tidak ada gulir horizontal pada lebar 320px:

```sh
python3 -c "
from html.parser import HTMLParser
VOID={'area','base','br','col','embed','hr','img','input','link','meta','source','track','wbr'}
class P(HTMLParser):
    def __init__(self): super().__init__(); self.s=[]; self.e=[]
    def handle_starttag(self,t,a):
        if t not in VOID: self.s.append((t,self.getpos()[0]))
    def handle_endtag(self,t):
        if t in VOID: return
        o,l=self.s.pop() if self.s else ('?',0)
        if o!=t: self.e.append(f'<{o}> baris {l} ditutup </{t}>')
p=P(); p.feed(open('index.html',encoding='utf-8').read())
print(p.e or 'struktur bersih')
"
```
