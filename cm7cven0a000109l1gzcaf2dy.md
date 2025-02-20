---
title: "Belajar Bash Scripting Part 13 : Membuat  Perintah Bash Kustom"
datePublished: Thu Feb 20 2025 04:57:11 GMT+0000 (Coordinated Universal Time)
cuid: cm7cven0a000109l1gzcaf2dy
slug: belajar-bash-scripting-part-13-membuat-perintah-bash-kustom
tags: unix, bash, bash-script

---

Sebagai seorang developer atayu SysAdmin, tugas berulang-ulang di terminal bisa menjadi sangat membosankan. Salah satu cara efektif untuk mengoptimalkan tugas itu yaitu dengan cara membuat perintah Bash kustom, atau biasa disebut sebagai **aliases**. Chapter ini membahas bagaimana cara membuat, me-manage, dan menyimpan alas, beserta dengan best practices untuk meningkatkan alur kerja kalian.

1. **Mengapa Menggunakan Perintah Bash Kustom?**
    
    Membuat perintah Bash kustom membuat kalian bisa :
    
    * Hemat waktu : Menghindari pengetikkan perintah yang panjang berulang kali.
        
    * Meningkatkan produktivitas : Mengakses perintah yang sering digunakan dengan keyword yang singkat dan mudah diingat.
        
    * Mengurangi eror : Meminimalisir resiko typo pada perintah yang kompleks.
        
2. **Pengenalan Aliases**
    
    Aliases adalah shortcut untuk perintah yang panjang atau kompleks. Aliases memungkinkan kalian membuat custom commands tanpa harus menulis script lengkap.
    
    1. Sintaks
        
        ```bash
        alias name="command"
        ```
        
    2. Contoh
        
        ```bash
        alias ll="ls -la"
        ```
        
        Contoh di atas membuat shortcut `ll` untuk perintah `ls -la`.
        
3. **Membuat Custom Aliases**
    
    1. Contoh Skenario
        
        Bayangkan kalian sering memeriksa jumlah TCP connections pada port 80 dan 443. Biasanya, perintah yang digunakan adalah :
        
        ```bash
        netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l
        ```
        
        Mengetik perintah tersebut setiap kali dijalankan tentu tidak efisien. Sebagai gantinya, kalian bisa membuat alias untuknya.
        
    2. Membuat Alias
        
        ```bash
        alias conn="netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l"
        ```
        
        Dengan mengetik `conn`, output yang sama dengan perintah lengkap tersebut akan ditampilkan.
        
    3. Meningkatkan Alias
        
        Kalian dapat menambahkan pesan informatif agar alias lebih user-friendly :
        
        ```bash
        alias conn="echo 'Total connections on port 80 and 443:' ; netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l"
        ```
        
        Output :
        
        ```bash
        Total connections on port 80 and 443:
        12
        ```
        
4. **Membuat Aliases Tetap Ada (Persist)**
    
    Alias yang dibuat langsung di terminal bersifat sementara dan akan hilang saat logout. Untuk membuatnya permanen, tambahkan alias tersebut ke file profile shell kalian.
    
    1. Memilih File yang Tepat
        
        * Pada Ubuntu dan sebagian besar distribusi Linux: `~/.bashrc`
            
        * Pada macOS dan beberapa distribusi Linus: `~/.bash_profile`
            
        * Pada sistem modern yang menggunakan Zsh: `~/.zshrc`
            
    2. Menambahkan ke .bashrc
        
        Buka file `.bashrc` menggunakan text editor (misalnya, nano) :
        
        ```bash
        nano ~/.bashrc
        ```
        
        Tambahkan alias kalian di bagian bawah :
        
        ```bash
        alias conn="echo 'Total connections on port 80 and 443:' ; netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l"
        ```
        
5. **Best Practises untuk Membuat Custom Bash Commands**
    
    1. Gunakan Nama yang Deskriptif
        
        Pilih nama alias yang bermakna untuk menghindari konflik dengan perintah yang sudah ada.
        
        Contoh :
        
        ```bash
        alias listconn="netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l"
        ```
        
        Hindari menggunakan nama perintah umum seperti `ls`, `cd` atau `rm` sebagai alias.
        
    2. Kelompokkan Alias yang Berkaitan
        
        Atur aliases yang terkait bersama-sama di dalam file konfigurasi kalian untuk memudahkan pembacaan dan pemeliharaan :
        
        ```bash
        # Networking Aliases
        alias listconn="netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l"
        alias myip="curl ifconfig.me"
        ```
        
    3. Sertakan Komentar
        
        Tambahkan komentar untuk menjelaskan tujuan setiap alias, terutama jika perintahnya kompleks :
        
        ```bash
        # Check total connections on port 80 and 443
        alias listconn="netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l"
        ```
        
    4. Hindari Menimpa Perintah Sistem
        
        Berhati-hatilah saat memberi nama alias untuk menghindari secara tidak sengaja menimpa perintah sistem :
        
        ```bash
        # Not recommended
        alias rm="rm -i"
        ```
        
    5. Uji Alias Terlebih Dahulu
        
        Ujilah alias kalian langsung di terminal sebelum menambahkannya ke `.bashrc` atau file konfigurasi lainnya.
        
    6. Gunakan Functions untuk Perintah yang Kompleks
        
        Jika alias kalian melibatkan logika yang kompleks atau beberapa perintah, pertimbangkan untuk menggunakan function sebagai gantinya :
        
        ```bash
        conn() {
            echo "Total connections on port 80 and 443:"
            netstat -plant | grep '80\|443' | grep -v LISTEN | wc -l
        }
        ```