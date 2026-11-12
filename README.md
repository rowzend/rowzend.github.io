# Catatan Fleksibel — situs resmi

Situs statis untuk aplikasi **Catatan Fleksibel**. Berisi halaman beranda,
kebijakan privasi, dan syarat layanan dalam bahasa Indonesia dan Inggris.

Situs ini sengaja tidak memakai cookie, analytics, iklan, font eksternal, atau
JavaScript. Semua halaman adalah HTML/CSS statis dan dihosting di GitHub Pages.

## URL

- Beranda (Indonesia): <https://rowzend.github.io/>
- Kebijakan privasi: <https://rowzend.github.io/privacy/>
- Syarat layanan: <https://rowzend.github.io/terms/>
- Beranda (English): <https://rowzend.github.io/en/>
- Privacy policy: <https://rowzend.github.io/en/privacy/>
- Terms of service: <https://rowzend.github.io/en/terms/>

## Pratinjau lokal

```bash
python3 -m http.server 8080
```

Lalu buka <http://127.0.0.1:8080/>.

## Deployment

Repositori ini adalah **user site** GitHub Pages. Halaman diterbitkan dari
branch `main`, folder root. File `.nojekyll` mencegah pemrosesan Jekyll.

Setelah mengubah file:

```bash
git add .
git commit -m "Perbarui halaman situs"
git push
```

GitHub Pages akan menerbitkan ulang dalam beberapa menit.

## Verifikasi Google Search Console

Google mewajibkan authorized domain OAuth diverifikasi di Search Console.
Untuk situs ini, gunakan **URL prefix property**:

```text
https://rowzend.github.io/
```

Langkah:

1. Buka <https://search.google.com/search-console/> dengan akun Google yang
   sama dengan pemilik project Google Cloud **947126970670**.
2. Tambahkan property **URL prefix** `https://rowzend.github.io/`.
3. Pilih metode verifikasi **HTML tag** atau **HTML file**.
   - **HTML tag:** salin meta tag dari Search Console ke dalam `<head>` file
     `index.html`, lalu commit dan push. Tunggu GitHub Pages selesai deploy,
     lalu klik **Verify**.
   - **HTML file:** unduh file verifikasi, letakkan di root repositori ini,
     commit, push, lalu klik **Verify**.
4. Setelah terverifikasi, pastikan akun tersebut menjadi **Owner** atau
   **Editor** di project Google Cloud yang dipakai OAuth.

## Nilai untuk Google Cloud Console

Buka **Google Auth Platform → Branding** (atau OAuth consent screen):

| Field | Nilai |
| --- | --- |
| Application home page | `https://rowzend.github.io/` |
| Application privacy policy link | `https://rowzend.github.io/privacy/` |
| Application Terms of Service link | `https://rowzend.github.io/terms/` |
| Authorized domain | `rowzend.github.io` |

**Hapus** authorized domain `github.com`. Domain itu milik GitHub, bukan milik
akun `rowzend`, sehingga tidak bisa diverifikasi dan akan membuat verifikasi
gagal.

Gunakan halaman Indonesia untuk field OAuth karena halaman tersebut adalah
halaman utama aplikasi. Halaman Inggris tersedia sebagai alternatif.

## Catatan penting

- Jangan memakai URL Gist (`gist.github.com/...`) sebagai homepage, privacy
  policy, atau terms. Gist bukan domain yang bisa diverifikasi di Search
  Console.
- Jangan memakai `github.com` sebagai authorized domain.
- Halaman ini tidak memuat data pribadi, token, atau kredensial.
- Jika nanti memakai domain kustom, tambahkan file `CNAME`, atur DNS, lalu
  verifikasi domain di Search Console dan perbarui nilai di Google Cloud.
