---
title: "Belajar Bash Scripting Part 12 : Debugging, Testing dan Shortcuts"
datePublished: Tue Feb 18 2025 04:47:19 GMT+0000 (Coordinated Universal Time)
cuid: cm7a068l7000v09l1gplzdouf
slug: belajar-bash-scripting-part-12-debugging-testing-dan-shortcuts
tags: unix, bash, bash-script

---

Ketika berurusan dengan Bash script, debugging dan testing sangat penting untuk memastikan script kalian berjalan dengan lancar dan efisien. Selain itu, menguasai shortcut terminal dapat meningkatkan produktivitas secara signifikan. Di chapter ini, kita akan membahas teknik debugging yang berguna, tools testing, dan shortcut terminal praktis yang wajib diketahui oleh setiap Bash scripter.

1. **Debugging di Bash**
    
    Debugging membantu kalian mengidentifikasi masalah dan memahami alur eksekusi scirpt. Bash menyediakan beberapa opsi untuk membantu proses ini,
    
    1. Menggunakan -x
        
        Kalian dapat menggunakan opsi -x saat menjalankan script untuk melihat setiap perintah dan argumen yang telah diperluas (expanded) saat dieksekusi. Ini sangat berguna untuk menemukan error atau perilaku yang tidak diharapkan.
        
        ```bash
        bash -x ./scipt_kamu.sh
        ```
        
    2. Menggunakan set -x dan set +x
        
        Alternatifnya, kalian bisa mengaktifkan debugging untuk bagian tertentu dari script dengan menambahkan set -x sebelum baris-baris yang ingin kalian debug, dan menonaktifkannya dengan set +x setelahnya.
        
        ```bash
        #!/bin/bash
        
        echo "Awal script"
        
        set -x
        
        # Debugging dimulai dari sini
        echo "Ini adalah pesan debug"
        # Debugging berakhir dari sini
        set +x
        
        echo "Akhir script"
        ```
        
        **Penjelasan :**
        
        * set -x mengaktifkan debugging mode, menampilkan setiap perintah sebelum dieksekusi.
            
        * set +x mematikan debugging mode, sehingga perintah selanjutnya tidak ditampilkan.
            
2. Test Scipt Kalian
    
    1. Menggunakan ShellCheck
        
        ShellCheck adalah tools analisis statis yang populer untuk Bash script. TOols ini membantu mengidentifikasi potensi error serta memberikan saran perbaikan.
        
        Versi Online :
        
        Kalian dapat menggunakan ShellCheck langsung di website : [ShellCheck Online](https://www.shellcheck.net)
        
    2. Instalasi Lokal :
        
        Kalian juga dapat menginstall ShellCheck secara lokal dan menjalanaknnya dari terminal. Petunjuk instalasi dapat ditemukan di GitHub : [ShellCheck on GitHub](https://github.com/koalaman/shellcheck)
        
        ```bash
        shellcheck script_kamu.sh
        ```
        
        **Penjelasan :**
        
        ShellCheck menganalisa script dan melaporkan syntax errors, potensi bug, serta masalah style.
        
3. Sebagai SysAdmin atau DevOps engineer, kalian mungkin menghabiskan banyak waktu di terminal. Menguasai shortcut berikut dapat menghemat waktu dan tenaga :
    
    1. Line and Word Navigation
        
        * Menghapus semua yang ada di kursor hingga akhir baris : Ctrl + k
            
        * Menghapus semua yang ada dari kursor ke awal baris : Ctrl + u
            
        * Menghapus satu kata secara mundur dari kursor : Ctrl + w
            
    2. History and Screen Management
        
        * Mencari riwayat perintah secara mundur : Ctrl + r
            
        * Mengosongkan layar (alih-alih mengetik `clear`) : Ctrl + l
            
    3. Output Control and Command Management
        
        * Mengehentikan output ke layar : Ctrl + s
            
        * Mengaktifkan output ke layar (jika sebelumnya dihentikan dengan Ctrl + s) : Ctrl + q
            
        * Menghentikan perintah saat ini : Ctrl + c
            
        * Mengirim perintah saat ini ke latar belakang : Ctrl+ z
            
4. Best Practices and Tips
    
    * Gunakan -x secara selektif : Jangan gunakan opsi ini untuk sleuruh scirpt kecuali diperlukan, karena dapat membuat output menjadi berantakan. Gunakan set -x dan set +x di sekitar baris yang ingin kalian debug untuk mempersempit area masalah.
        
    * Periksa script secara berkala dengan ShellCheck : Ini membantu menangkap syntax errors dan meningkatkan kualitas kode.
        
    * Hafalkan dan latih shortcut : Menguasai shortcut terminal sangat berguna untuk navigasi cepat, terutama saat berurusan dengan perintah panjang atau ketika troubleshooting script.