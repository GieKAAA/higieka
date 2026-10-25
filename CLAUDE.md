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
| `index.html`   | Seluruh halaman: markup, gaya, dan ikon     |
| `netlify.toml` | Konfigurasi deploy dan tajuk keamanan       |
| `robots.txt`   | Izin perayapan mesin pencari                |
| `sitemap.xml`  | Peta situs                                  |

Seluruh CSS berada inline di dalam `index.html`. Jangan memecahnya menjadi berkas
terpisah tanpa diminta; sifat satu-berkas adalah keputusan desain yang disengaja.

## Arah desain

Tampilan mengacu pada gaya kiro.dev, atas permintaan pemilik situs.

- Latar nyaris hitam `#0B0B0F`, dengan gradien ungu lembut di bagian atas halaman
- Aksen utama ungu `#8B5CF6`, varian terang `#B99DFB`
- Amber `#F2A93B` khusus sebagai penanda status aktif
- Judul memakai JetBrains Mono tebal dengan tracking rapat; badan teks memakai Inter
- Panel bersudut membulat dengan bingkai gradien ungu

Palet amber dan ritme antarmuka diambil dari aplikasi desktop "Lokasi" buatan
pemilik situs, agar tampilan situs selaras dengan karyanya sendiri.

Ketentuan kualitas yang harus dipertahankan pada setiap perubahan:

- Responsif hingga lebar layar ponsel, tanpa gulir horizontal
- `prefers-reduced-motion` dihormati
- Cincin fokus papan ketik terlihat jelas
- Kontras warna memenuhi WCAG AA

## Bahasa

Seluruh teks situs dan pesan commit ditulis dalam bahasa Indonesia ragam formal.
Atribut `lang` pada elemen `html` adalah `id`.

## Isi yang belum lengkap

Bagian "Kerja" belum memuat entri skripsi. Topiknya adalah sistem presensi KKN
(LKH KKN), namun redaksi judul final belum tersedia. Setelah judul diperoleh,
tambahkan entri tersendiri pada bagian Kerja dan ganti keterangan "Menyusun tugas
akhir" pada bagian hero menjadi keterangan yang lebih spesifik.

Jangan mencantumkan karya milik orang lain pada situs ini. Beberapa judul skripsi
yang pernah dibahas pemilik situs adalah milik rekannya, bukan miliknya sendiri.

## Kendala yang sedang berjalan

Situs sudah ter-deploy dan DNS sudah mengarah dengan benar, tetapi belum dapat
diakses publik. Pengunjung dialihkan ke halaman "Team protection" milik Netlify.
Penyebabnya adalah proteksi akses tingkat tim pada akun Netlify, yang membuat
seluruh situs dalam tim bersifat privat. Setelan ini hanya dapat diubah oleh
pemilik akun melalui dasbor Netlify.

## Verifikasi sebelum push

Periksa struktur HTML dan tautan internal sebelum mendorong perubahan:

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
