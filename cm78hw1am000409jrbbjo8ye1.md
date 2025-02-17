---
title: "Belajar Bash Scripting Part 10 : Loops"
datePublished: Mon Feb 17 2025 03:27:44 GMT+0000 (Coordinated Universal Time)
cuid: cm78hw1am000409jrbbjo8ye1
slug: belajar-bash-scripting-part-10-loops
tags: unix, bash, bash-script

---

Loops dalam Bash sangat penting untuk mengotomatisasi tugas-tugas berulang. Dengan loops, kalian dapat melakukan iterasi melalui daftar, memproses file, dan mengeksekusi perintah secara berulang hingga kondisi tertentu terpenuhi. Dalam panduan ini, kita akan membahas berbagai jenis loops yang tersedia di Bash **for, while** dan **until** serta cara mengendalikan alur loop dengan **continue** dan **break**, termasuk contoh nested loops dan penerapan dalam kasus nyata.

1. For Loops
    
    For loops digunakan untuk melakukan iterasi melalui daftar item atau urutan angka.
    
    1. Sintaks Dasar For Loop
        
        ```bash
        for var in ${list}
        do
            <commands>
        done
        ```
        
        Pada sintaks diatas, variabel `list` berisi kumpulan nilai yang akan diiteras, dan setiap elemen akan disimpan sementara ke dalam variabel `var`.
        
    2. Contoh : Looping Melalui Daftar
        
        ```bash
        #!/bin/bash
        
        users="bangjono anton toni"
        
        for user in ${users}
        do
            echo "${user}"
        done
        ```
        
        **Penjelasan :**
        
        * Variabel `users` menyimpan daftar nama yang dipisahkan oleh spasi.
            
        * Loop akan mengambil setiap nama dan mencetaknya.
            
    3. Contoh : Looping Melalui Angka
        
        ```bash
        #!/bin/bash
        
        for num in {1..10}
        do
            echo ${num}
        done
        ```
        
        **Penjelasan :**
        
        * Ekspresi `{1..10}` menghasilkan angka 1 hingga 10 secara berurutan.
            
    4. C-Style For Loop
        
        ```bash
        #!/bin/bahs
        
        for (( i=1; i<=5; i++ ))
        do
            echo "Iterasi ke-$i"
        done
        ```
        
        **Penjelasan :**
        
        * Sintaks ini menyerupai loop dalam bahasa C, yang berguna untuk iterasi berbasis aritmetika.
            
2. While Loops
    
    While loops akan terus menjalankan perintah selama kondisi yang ditentukan bernilai true.
    
    1. Sintaks Dasar While Loops
        
        ```bash
        while [[ condition ]]
        do
            <commands>
        done
        ```
        
    2. Contoh : Menghintung Hingga 10
        
        ```bash
        #!/bin/bash
        
        counter=1
        while [[ $counter -le 10 ]]
        do
            echo $counter
            ((counter++))
        done
        ```
        
        **Penjelasan :**
        
        * Loop mencetak angka dari 1 hingga 10.
            
        * Ekspresi `((counter++))` bertugas menambah nilai `counter` setiap iterasi.
            
    3. Contoh : Validasi Input User
        
        ```bash
        #!/bin/bash
        
        read -p "Siapa nama kalian? " nama
        
        while [[ -z ${name} ]]
        do
            echo "Nama tidak boleh kosong. Silahkan masukkan nama yang valid!"
            read -p "Masukkan nama kalian lagi: " nama
        done
        
        echo "Hai ${nama}"
        ```
        
        **Penjelasan :**
        
        * Loop akan terus meminta input hingga user memasukkan nama yang tidak kosong.
            
3. Until Loops
    
    Until loops mirip dengan while loops, namun dengan logika terbalik. Loop akan berjalan sampai kondisi yang ditentukan menjadi true.
    
    1. Sintaks Dasar Until Loop
        
        ```bash
        until [[ condition ]]
        do
            <commands>
        done
        ```
        
    2. Contoh : Menghitung Hingga 10
        
        ```bash
        #!/bin/bash
        
        count=1
        until [[ $count -gt 10 ]]
        do
            echo $count
            ((count++))
        done
        ```
        
        **Penjelasan :**
        
        * Loop akan terus berjalan hingga nilai `count` lebih besar dari 10.
            
4. Kontrol Loop : Continue dan Break
    
    Untuk mengatur alur eksekusi dalam loop, kita dapat menggunakan perintah continue dan break.
    
    1. Continue Statement
        
        Continue digunakan untuk melewati sisa perintah dalam iterasi saat ini dan langsung melanjutkan ke iterasi berikutnya.
        
        Contoh :
        
        ```bash
        #!/bin/bash
        
        for i in {1..5}
        do
            if [[ $i -eq 2 ]]
            then
                echo "Melewati angka 2"
                continue
            fi
            echo "i sama dengan $i"
        done
        ```
        
        **Penjelasan :**
        
        * Ketika `i` bernilai 2, perintah `continue` membuat loop langsung melanjutkan ke iterasi berikutnya tanpa menjalankan perintah di bawahnya.
            
    2. Break Statement
        
        Break digunakna untuk menghentikan loop secara keseluruhan.
        
        Contoh :
        
        ```bash
        #!/bin/bash
        
        num=1
        while [[ $nunm -lt 10 ]]
        do
            if [[ $num -eq 5 ]]
            then
                break
            fi
            echo $num
            ((num++))
        done
        echo "Loop selesai"
        ```
        
        **Penjelasan :**
        
        * Loop akan berhenti saat `num` mencapai nilai 5.
            
    3. Break pada Nested Loops
        
        Untuk keluar dari loop bersarang, kita bisa menggunakan `break` dengan parameter, msialnya `break 2` untuk menghentikan dua level loop sekaligus.
        
        Contoh :
        
        ```bash
        #!/bin/bash
        
        for (( a = 1; a < 10; a++ ))
        do
            ehco "Outer loop: $a"
            for (( b = 1l b < 100; b++ ))
            do
                if [[ $b -gt 5 ]]
                then
                    break 2
                fi
                echo " Inner loop: $b"
            done
        done
        ```
        
        **Penjelasan ":**
        
        * `break 2` akan keluar dari kedua loop, baik inner maupun outer, begitu kondisi di dalam inner loop terpenuhi.
            
5. Teknik Lanjutan dan Contoh Dunia Nyata
    
    1. Looping pada File di Direktori
        
        ```bash
        #!/bin/bash
        
        director="/path/to/directory"
        
        for file in "$directory"/*
        do
            if [[ -f "$file" ]]; then
                echo "Memproses file: $file"
                # Lakukan aksi pada file disini
            fi
        done
        ```
        
        **Penjelasan :**
        
        * Script akan mengiterasi setiap file reguler dalam direktori yang ditentukan.
            
    2. Looping pada Output Perintah
        
        ```bash
        #!/bin/bash
        
        for user in $(cut -d: -f1 /etc/passwd)
        do
            echo "User: $user"
        done
        ```
        
        **Penjelasan :**
        
        * Menggunakan output dari perintah `cut` untuk mengambil daftar username dari file `/etc/passwd` dan mencetaknya.
            
    3. Menggabungkan Loops dengan Functions
        
        ```bash
        #!/bin/bash
        
        process_user() {
            local user=$1
            echo "Memproses uer: $user"
        }
        
        users=("bangjono" "anton" "toni")
        
        for user in ${users[@]}"
        do
            process_user "$user"
        done
        ```
        
        **Penjelasan :**
        
        * Menggunakan function membuat kode lebih modular dan maintainable.
            
    4. Eksekusi Paralel dalam Loops
        
        ```bash
        #!/bin/bash
        
        for i in {1..5}
        do
            (
                echo "Memproses $i"
                sleep 2
            ) &
        done
        wait
        echo "Semua tugas selesai!"
        ```
        
        **Penjelasan :**
        
        * Setiap iterasi dijalankan sebagai background process menggunakan `&`.
            
        * Perintah wait memastikan bahwa script akan menunggu sampai semua background process selesai sebelum melanjutkan.