# Frequently Asked Questions

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

Kalian bisa setup untuk konek dengan SSH, dengan cara

Akses Jupyter Hub Server dengan akun kalian

Buka Terminal dan buat file ~/.ssh/authorized_keys

```bash
mkdir ~/.ssh
vim ~/.ssh/authorized_keys
```

Copy public key kalian kedalam file tersebut, save dan sekarang kalian bisa mengakses server dengan ssh, dari akses tersebut, gunakan tmux untuk menjalankan script yang perlu berjalan lama dan bisa ditinggal walaupun VPN bermasalah. Untuk detail mengenai membuat ssh key pair, bisa ikuti [Help dari Github](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

P.S. tmux mirip seperti `screen`, untuk pengenalan tmux bisa dicari sendiri, salah satu bacaan yang direkomendasikan adalah [artikel oleh Nick Janetakis](https://nickjanetakis.com/blog/who-else-wants-to-boost-their-productivity-with-tmux)

## Waktu install make pip dan conda kok gabisa ya? kena ProxyError

Nah ini masih bingung kenapanya, kadang error kadang aman, jadi kalau ada masalah gini cobain kasih manual [proxy ITB](https://ditsti.itb.ac.id/en/proxy-internet-itb/) kalian waktu manggil [`pip`](https://leifengblog.net/blog/how-to-use-pip-behind-a-proxy/) atau [`conda`](https://docs.anaconda.com/anaconda/user-guide/tasks/proxy/). 
