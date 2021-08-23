# Frequently Asked Questions

## Bagaimana cara install versi python yang lain?

Gunakan terminal pada jupyterhub, lalu buat environment baru dengan menggunakan conda. Jangan lupa untuk menentukan python version dan juga menginstall ipython dan jupyter kernel
```
# bila belum melakukan init
conda init bash 

conda create -n [nama env] python=[python version] ipython jupyter
```

Aktivasi environment dan tambahkan kernel ke kernelspec
```
conda activate [name env]

ipython kernel install --name "[nama env]" --user
```

Lalu buka [jupyterhub control panel](http://167.205.32.108/hub/home) untuk stop server lalu start server kembali

sekarang kernel yang kamu bikin akan ada di halaman utama jupyterhub. Jangan lupa untuk install kembali package yang dibutuhkan karena package tidak terbawa antar kernel.
