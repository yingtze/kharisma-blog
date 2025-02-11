---
title: "Belajar Bash Scripting Part 2 : Hello World"
datePublished: Tue Feb 11 2025 10:05:44 GMT+0000 (Coordinated Universal Time)
cuid: cm70bgre9001p0ale1fds9co7
slug: belajar-bash-scripting-part-2-hello-world
tags: bash, bash-script

---

Setelah kalian membuat file `bangjono.sh` dan menambahkan shebang di baris paling awal, kalian siap untuk membuat Bash Script pertama kalian : “Hello World!”

1. **Menambahkan Perintah Hello World**
    
    Buka file `bangjono.sh` dan tambahkan baris berikut setelah **shebang** :
    
    ```bash
    #!/bin/bash
    
    echo "Hello World!"
    ```
    
    Penjelasan :
    
    Command echo digunakan untuk menampilkan teks di terminal.
    
    Dalam contoh ini, teks **“Hello World!”** akan dicetak di layar.
    
2. **Menyimpan File dan Membuatnya Bisa Dieksekusi**
    
    Setelah menambahkan perintah diatas, simpan file dan keluar dari editor.
    
    Sebelum script bisa dijalankan, kalian harus memberikan izin eksekusi pada file tersebut dengan perintah ini di terminal :
    
    ```bash
    chmod +x bangjono.sh
    ```
    
    Penjelasan :
    
    Command `chmod +x bangjono.sh` memberikan izin eksekusi pada file, sehingga bisa dijalankan sebagai program.
    
    Mengenai **izin eksekusi pada file** akan saya buatkan pada postingan mandiri, jika ada waktu luang.
    
3. **Menjalankan Script**
    
    Setelah script memiliki izin eksekusi, jalankan dengan perintah ini di terminal :
    
    ```bash
    ./bangjono.sh
    ```
    
    Apa yang terjadi?
    
    Saat kalian menjalankan `./bangjono.sh`, sistem akan mengeksekusi script, dan kalian akan melihat output berikut di terminal :
    
    ```bash
    Hello World!
    ```
    
4. **Cara Alternatif Menjalankan Script**
    
    Jika kalian ingin menjalankan script tanpa mengubah izinnya, kalian bisa meng-*invoke* Bash secara langsung untuk menjalankannya di terminal :
    
    ```bash
    bash bangjono.sh
    ```
    
    Tips Tambahan :
    
    Bash juga bisa digunakan secara interaktif. Misalnya, jika kalian langsung mengetik perintah berikut di terminal :
    
    ```bash
    echo "Halo Rek!"
    ```
    
    Kalian akan langsung mendapatkan output seperti ini :
    
    ```bash
    Halo Rek!
    ```
    
    Ini menunjukkan bahwa perintah yang kalian tulis dalam script juga bisa dijalankan langsung di terminal.
    
5. **Mengapa Menulis Command dalam Script itu Berguna?**
    
    Menggabungkan beberapa command ke dalam satu script membuat tugas yang berulang atau kompleks menjadi lebih mudah dikelola.
    
    Meskipun contoh ini hanya menampilkan teks sederhana, script bisa digunakan untuk mengotomatiskan berbagai tugas, menghemat waktu, dan mengurangi kesalahan yang terjadi saat menjalanakn perintah secara manual.