# Frequently Asked Questions

## Bagaimana cara memilih GPU

Hal ini tidak ada panduan umumnya. Karena saat ini semua GPU tersedia untuk semua user. Sehingga untuk menggunakan GPU, silahkan lakukan reservasi waktu untuk GPU tertentu di spreadsheet reservasi server (tautan di grup WhatsApp). Teknis pemilihan GPU didasari asas tanggung jawab bersama dan komunikasi antarpengguna server.

Berikut beberapa contoh cara pemilihan GPU pada library Python:
- [Tensorflow](https://stackoverflow.com/questions/40069883/how-to-set-specific-gpu-in-tensorflow)
- [Pytorch](https://discuss.pytorch.org/t/how-to-change-the-default-device-of-gpu-device-ids-0/1041/8)
- [Darknet](https://github.com/pjreddie/darknet/issues/291)

## Bagaimana cara memasang versi Python yang lain?

Gunakan terminal pada jupyterhub, lalu buat environment baru dengan menggunakan conda. Jangan lupa untuk menentukan python version dan juga menginstall ipython dan jupyter kernel
``` bash
# bila belum melakukan init
conda init bash 
# untuk memastikan conda sudah ter-init
source ~/.bashrc
# hal yang dalam bracket merupakan variable, 
# conda create -n [nama env] -y python=[python version] ipython jupyter
# misal
conda create -n test_env -y python=3.8 ipython jupyter
```

Aktivasi environment dan tambahkan kernel ke kernelspec
``` bash
conda activate [name env]

ipython kernel install --name "[nama env]" --user
```

Lalu buka JupyterHub Control Panel (File -> Hub Control Panel) untuk stop server lalu start server kembali.

Sekarang, kernel yang kamu buat akan ada di halaman utama JupyterHub. Jangan lupa untuk instal kembali package yang dibutuhkan karena package tidak terbawa antar-kernel.
``` python
# Untuk mengecek versinya sudah benar silahkan jalankan
from platform import python_version

print(python_version())
```

## Bagaimana cara menangani ProxyError atau Error 407

Kemungkinan hal ini terjadi karena kredensial proxy bawaan server sudah kedaluwarsa atau kredensial proxy tidak terbaca oleh program.

Jangan lupa untuk mencoba restart server JupyterHub di Control Panel (File -> Hub Control Panel) setiap selesai mencoba solusi-solusi di bawah untuk memastikan keberhasilan/kegagalan solusi 😁 Kalau masih tidak bisa, jangan sungkan mengubungi admin.

### Solusi 1: Mengatur program untuk pakai proxy

Beberapa program seperti pip dan conda memiliki alternatif solusi khusus untuk menggunakan proxy. Silakan telaah dokumentasi library/program tersebut atau cari cara pemasangan proxy khusus library/program tersebut di Google dengan kata pencarian "Configure proxy for [nama library/program]"

Berikut contoh cara konfigurasi proxy untuk [pip](https://pip.pypa.io/en/stable/user_guide/#using-a-proxy-server) dan [conda](https://stackoverflow.com/a/31120854).

### Solusi 2: Menggunakan kredensial proxy sendiri

Untuk menggunakan kredensial proxy milik sendiri, tambahkan kode berikut di dalam berkas `~/.bashrc` 
```bash
export http_proxy="http://{email_akun_itb}:{pass_proxy}@cache.itb.ac.id:8080"
export https_proxy="http://{email_akun_itb}:{pass_proxy}@cache.itb.ac.id:8080"
export pip_proxy="http://{email_akun_itb}:{pass_proxy}@cache.itb.ac.id:8080"
```

> Tips: gunakan perintah `nano ~/.bashrc` di Terminal untuk mengedit teks dengan [nano](https://www.howtogeek.com/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/)

Kredensial proxy bisa dilihat di [halaman manajemen akun ITB](https://dti.itb.ac.id/nic/manajemen_akun/informasi_password_proxy).

## Bagaimana cara salin-tempel di Terminal?

Untuk menyalin teks dari Terminal JupyterHub, blok teks yang ingin disalin dari Terminal kemudian klik kanan dan pilih "Copy". Untuk menempel teks, cukup klik kanan di Terminal kemudian pilih "Paste".

Untuk pengguna MacOS, Anda juga dapat langsung menggunakan pintasan keyboard `Command+C` dan `Command+V` untuk menyalin dan menempel 😁

![Salin-tempel di Terminal](./resources/tambora-terminal-cp.png)