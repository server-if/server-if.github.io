# Frequently Asked Questions

## Bagaimana cara memilih GPU

Hal ini tidak ada panduan umumnya. Karena saat ini semua GPU tersedia untuk semua user. Sehingga untuk menggunakan GPU, silahkan booking waktu untuk GPU tertentu di [form booking server](https://docs.google.com/spreadsheets/d/1abFMd7kmAc2AeMesAhmw1Of0ukaGwSNNUB3BTQ_Zz6I/edit?usp=sharing). Sedangkan untuk teknis pemilihan GPU nya didasari asas tanggung jawab bersama.

Jadi kamu diharapkan untuk secara bertanggung jawab memilih GPU yang digunakan sesuai dengan tools/framework masing-masing. Beberapa contoh yang cukup bermanfaat:
- [Tensorflow](https://stackoverflow.com/questions/40069883/how-to-set-specific-gpu-in-tensorflow)
- [Pytorch](https://discuss.pytorch.org/t/how-to-change-the-default-device-of-gpu-device-ids-0/1041/8)
- [Darknet](https://github.com/pjreddie/darknet/issues/291)

## Bagaimana cara install versi python yang lain?

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

Lalu buka [jupyterhub control panel](http://167.205.32.108/hub/home) untuk stop server lalu start server kembali

sekarang kernel yang kamu bikin akan ada di halaman utama jupyterhub. Jangan lupa untuk install kembali package yang dibutuhkan karena package tidak terbawa antar kernel.
``` python
# Untuk mengecek versinya sudah benar silahkan jalankan
from platform import python_version

print(python_version())
```

## Koneksi VPN nya ga stabil, dan kadang servernya mati sebelum selesai, gimana ya baiknya?

kamu bisa setup untuk konek dengan SSH, dengan cara

Akses Jupyter Hub Server dengan akun kamu

Buka Terminal dan buat file ~/.ssh/authorized_keys

```bash
mkdir ~/.ssh
vim ~/.ssh/authorized_keys
```

Copy public key kamu kedalam file tersebut, save dan sekarang kamu bisa mengakses server dengan ssh, dari akses tersebut, gunakan tmux untuk menjalankan script yang perlu berjalan lama dan bisa ditinggal walaupun VPN bermasalah. Untuk detail mengenai membuat ssh key pair, bisa ikuti [Help dari Github](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

P.S. tmux mirip seperti `screen`, untuk pengenalan tmux bisa dicari sendiri, salah satu bacaan yang direkomendasikan adalah [artikel oleh Nick Janetakis](https://nickjanetakis.com/blog/who-else-wants-to-boost-their-productivity-with-tmux)

## Waktu install make pip dan conda kok gabisa ya? kena ProxyError

Nah ini masih bingung kenapanya, kadang error kadang aman, jadi kalau ada masalah gini cobain kasih manual [proxy ITB](https://ditsti.itb.ac.id/en/proxy-internet-itb/) kamu waktu manggil [`pip`](https://leifengblog.net/blog/how-to-use-pip-behind-a-proxy/) atau [`conda`](https://docs.anaconda.com/anaconda/user-guide/tasks/proxy/). 

### Update 1: Ternyata Masalah Akun

Ternyata masalah ini muncul karena akun yang dipake kemarin sudah kadaluarsa. Jadi kalau terjadi lagi kayak gini bisa lapor ke Admin, dan untuk sementara bisa menambahkan http_proxy di bashrc masing2.

pada terminal jupyterhub: `nano ~/.bashrc` lalu di paling bawah masukkan:
```bash
export http_proxy="http://{user_ina}:{pass_ina}@cache.itb.ac.id:8080"
export https_proxy="http://{user_ina}:{pass_ina}@cache.itb.ac.id:8080"
```

untuk `{user_ina}` dan `{password}` bisa dilihat di [halaman akun INA kamu](https://ditsti.itb.ac.id/nic/manajemen_akun/informasi_password_proxy).

kalau belum bisa juga bisa coba matikan dan nyalakan jupyterhubnya kembali.

### Update 2: Sudah menggunakan dedicated proxy credential

Saat ini sudah menggunakan proxy credentials khusus untuk server, sehingga seharusnya tak ada masalah lagi karena kadaluarsa (admin lulus). Namun untuk mencegah kuota habis, sangat direkomendasikan untuk menggunakan credential masing-masing, hal ini bisa dilihat pada bagian [proxy](https://github.com/server-if/server-if.github.io/issues/4)

## Bagaimana Cara Copy Paste ke Terminal Jupyter Hub

Untuk Copy dan Paste bisa melakukan select biasa pada tulisan, lalu gunakan <kbd>SHIFT</kbd> + <kbd>RIGHT CLICK</kbd> untuk membuka context menu, dan bisa memilih <kbd>Copy</kbd> dan <kbd>Paste</kbd>


