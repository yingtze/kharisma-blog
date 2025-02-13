---
title: "Belajar Bash Scripting Part 6 : Argumen"
datePublished: Thu Feb 13 2025 02:15:13 GMT+0000 (Coordinated Universal Time)
cuid: cm72pjdjl000209ju83nvevi4
slug: belajar-bash-scripting-part-6-argumen
tags: unix, bash, bash-script

---

Bash memungkinkan kalian untuk meneruskan argumen saat menjalankan script. Dengan cara ini, script menjadi lebih fleksibel dan dapat digunakan kembali tanpa perlu mengubah kodenya.

1. **Mengirimkan Argumen ke Script**
    
    Untuk mengirimkan argumen, cukup tambahkan setelah nama script saat menjalankannya. Contoh :
    
    ```bash
    ./bangjono.sh contoh_argumen
    ```
    
    Di dalam script, kalian bisa mengakses argumen ini menggunakan variabel khusus :
    
    * `$1` adalah argumen pertama
        
    * `$2` adalah argumen kedua
        
    * `$3` adalah argumen ketiga, dan seterusnya
        
    
    Mari kita buat script baru bernama **argumen.sh** untuk melihat cara kerjanya :
    
    ```bash
    #!/bin/bash
    
    echo "Argumen pertama adalah: $1"
    echo "Argumen kedua adalah: $2"
    echo "Argumen ketiga adalah: $3"
    ```
    
    **Penjelasan :**
    
    * `$1`, `$2` dan `$3` adalah placeholder untuk argumen pertama, kedua dan ketiga yang diberikan saat menjalankan script.
        
2. **Menjalankan Script dengan Argumen**
    
    Pertama, buat script bisa dieksekusi :
    
    ```bash
    chmod +x argumen.sh
    ```
    
    Kemudian jalankan dengan tiga argumen :
    
    ```bash
    ./argumen.sh anjing kucing burung
    ```
    
    Output :
    
    ```bash
    Argumen pertama adalah : anjing
    Argumen kedua adalah : kucing
    Argumen ketiga adalah : burung
    ```
    
    Argumen diteruskan ke dalam script dalam urutan yang sama seperti yang diberikan di terminal.
    
3. **Mengakses Semua Argumen Sekaligus**
    
    Jika kalian ingin mengambil semua argumen sekaligus, gunakan `$@` :
    
    ```bash
    #!/bin/bash
    
    echo "Semua argumen: $@"
    ```
    
    Jalankan dengan :
    
    ```bash
    ./argumen.sh anjing kucing burung
    ```
    
    Output :
    
    ```bash
    Semua argumen: anjing kucing burung
    ```
    
    `$@` sangat berguna jika jumlah argumen tidak diketahui sebelumnya atau jika ingin mengulanginya dalam sebuah perulangan.
    
4. **Mengakses Nama Script**
    
    Bash menyediakan variabel khusus `$0` yang berisi nama script itu sendiri. Ini berguna untuk :
    
    * Menampilkan nama script dalam log atau pesan informasi
        
    * Membuat script yang bisa menghapus dirinya sendiri (self-destruct)
        
    
    Contoh script yang menampilkan namanya sendiri dan kemudian menghapusnya :
    
    ```bash
    #!/bin/bash
    
    echo "Nama script ini adalah: $0 dan akan dihapus setelah dijalankan."
    
    rm -f $0
    ```
    
    Output :
    
    ```bash
    Nama script ini adalah: ./argumen.sh dan akan dihapus setelah dijalankan.
    ```
    
    **Peringatan :** Script yang menghapus dirinya sendiri bisa beresiko. Pastikan kalian punya salinan sebelum menjalankannya!