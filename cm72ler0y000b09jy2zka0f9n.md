---
title: "Belajar Bash Scripting Part 4 : User Input"
datePublished: Thu Feb 13 2025 00:19:38 GMT+0000 (Coordinated Universal Time)
cuid: cm72ler0y000b09jy2zka0f9n
slug: belajar-bash-scripting-part-4-user-input
tags: unix, bash, bash-script

---

Pada part sebelumnya, kita telah belajar bagaimana mendefinisikan variabel dan menampilkannya menggunakan `echo`. Sekarang, mari kita buat script lebih interaktif dengan meminta input langsung dari user.

1. **Mendapatkan Input User dengan** `read`
    
    Bash menyediakan command `read` untuk menangkap input user dan menyimpannya dalam variabel.
    
    Buka file bangjono.sh dan perbarui scriptnya menjadi seperti ini :
    
    ```bash
    #!/bin/bash
    
    echo "Siapa nama kalian?"
    read nama
    
    echo "Hai, $nama!"
    echo "Selamat datang di toko kami"
    ```
    
    **Penjelasan :**
    
    * `echo “Siapa nama kalian?”` menampilkan pertanyaan ke user.
        
    * `read nama` menangkap input dari user dan menyimpannya ke dalam variabel `nama`.
        
    * nilai yang tersimpan dalam variabel digunakan untuk menampilkan pesan sambutan.
        
2. **Menjalankan Script**
    
    Setelah menyimpan perubahan, pastikan script bisa dieksekusi dengan menjalankan :
    
    ```bash
    chmod +x bangjono.sh
    ```
    
    Lalu, jalankan scriptnya :
    
    ```bash
    ./bangjono.sh
    ```
    
    Kalian akan melihat prompt seperti ini :
    
    ```bash
    Siapa nama kalian?
    ```
    
    Setelah mengetikkan nama (misalnya: Anton) dan menekan Enter, hasilnya akan seperti ini :
    
    ```bash
    Hai, Anton!
    Selamat datang di toko kami
    ```
    
3. **Menyederhanakan Kode dengan** `read -p`
    
    Kalian bisa membuat script lebih ringkas dengan menggunakan opsi `-p` pada `read`, yang memungkinkan prompt ditampilkan di baris yang sama dengan input user.
    
    ```bash
    #!/bin/bash
    
    read -p "Siapa nama kalian? " nama
    
    echo "Hai, $nama!"
    echo "Selamat datang di toko kami"
    ```
    
    **Penjelasan :**
    
    * `read -p “Siapa nama kalian? “ nama` menampilkan pertanyaan dan menangkap input dalam satu baris.
        
    * hasil yang diperoleh tetap sama, tetapi script menjadi lebih bersih dan mudah dibaca.