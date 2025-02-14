---
title: "Belajar Bash Scripting Part 8 : Conditional Expression"
datePublished: Fri Feb 14 2025 02:23:51 GMT+0000 (Coordinated Universal Time)
cuid: cm745abwx000v09l13ctwhjnt
slug: belajar-bash-scripting-part-8-conditional-expression
tags: unix, bash, bash-script

---

Dalam Bash, conditional expression memungkinkan kalian menjalankan aksi berbeda berdasarkan kondisi yang bernilai true atau false. Fitur ini sangat penting untuk pengambilan keputusan sehingga script bisa merespon berbagai situasi secara dinamis. Bash menggunakan perintah gabungan `[[ … ]]` (atau sintaks lama `[ … ]` untuk mengevaluasi ekspresi, baik saat memeriksa atribut file, membandingkan string, atau mengevaluasi kondisi aritmetika.

1. File Expressions
    
    File expressions digunakan untuk menguji berbagai properti file dan direktori. Dengan cara ini, script dapat berinteraksi dengan sistem file secara aman.
    
    1. Common File Test
        
        True jika file ada dan merupakan block special file (misal: perangkat penyimpanan).
        
        ```bash
        [[ -b ${file} ]]
        ```
        
        True jika file ada dan merupakan chracter special file (misal: perangkat input/output).
        
        ```bash
        [[ -c ${file} ]]
        ```
        
        True jika file ada dan merupakan direktori.
        
        ```bash
        [[ -d ${file} ]]
        ```
        
        Return true jika file ada (tanpa memandang jenisnya).
        
        ```bash
        [[ -e ${file} ]]
        ```
        
        True jika file ada dan merupakan file biasa (bukan direktori atau file khusus)
        
        ```bash
        [[ -f ${file} ]]
        ```
        
        True jika file ada dan merupakan link simbolik/symlink
        
        ```bash
        [[ -h ${file} ]] atau [[ -L ${file} ]]
        ```
        
        True jika file ada dan dapat dibaca.
        
        ```bash
        [[ -r ${file} ]]
        ```
        
        True jika file ada dan ukurannya lebih dari nol.
        
        ```bash
        [[[ -s ${file} ]]
        ```
        
        True jika file ada dan dapat ditulis.
        
        ```bash
        [[ -w ${file} ]]
        ```
        
        True jika file ada dan dapat dieksekusi.
        
        ```bash
        [[ -x ${file} ]]
        ```
        
    2. Contoh: Pengujian Atribut File
        
        ```bash
        #!/bin/bash
        
        file="contoh.txt"
        
        if [[ -e ${file} ]]; then
          echo "File ada."
        
          if [[ -d ${file} ]]; then
            echo "Ini adalah direktori."
          elif [[ -f ${file} ]]; then
            echo "Ini adalah file biasa."
          fi
        
          if [[ -r ${file} ]]; then
            echo "File dapat dibaca."
          fi
        
          if [[ -w ${file} ]]; then
            echo "File dapat ditulis."
          fi
        
          if [[ -x ${file} ]]; then
            echo "File dapat dieksekusi."
          fi
        else
          echo "File tidak ada."
        fi
        ```
        
2. String Expression
    
    Pengujian string digunakan untuk memverifikasi isi atau kondisi data teks dalam variabel.
    
    1. Common String Test
        
        * Variabel Sudah Diset :
            
            ```bash
            [[ -v varname ]]
            ```
            
            True jika variabel `varname` telah diberikan nilai. (*Jangan gunakan* `${varname}` di sini.)
            
        * String Kosong :
            
            ```bash
            [[ -z ${string} ]]
            ```
            
            True jika string kosong.
            
        * String Tidak Kosong :
            
            ```bash
            [[ -n ${string} ]]
            ```
            
            True jika string tidak kosong.
            
        * Pemeriksaan Keamanan/Equality Check (termasuk pattern matching)
            
            ```bash
            [[ ${string1} == ${string2} ]]
            ```
            
            True jika kedua string sama.
            
        * Pemeriksaan Ketidaksamaan/Inequality Check
            
            ```bash
            [[ ${string1} != ${string2} ]]
            ```
            
            True jika kedua string tidak sama.
            
        * Perbandingan Leksikografis
            
            ```bash
            [[ ${string1} < ${string2} ]]
            [[ ${string1} > ${string2} ]]
            ```
            
            Membandingkan string berdasarkan dictionary order.
            
    2. Contoh : String Comparisons
        
        ```bash
        #!/bin/bash
        
        var="BangJono"
        
        if [[ -n ${var} ]]; then
            echo "Variabel telah di-set dan tidak kosong."
        fi
        
        string1="Apel"
        string2="Pisang"
        
        if [[ ${string1} < ${string2} ]]; then
            echo "${string1} diurutkan sebelum ${string2}."
        fi
        
        if [[ ${string1} != ${var} ]]; then
            echo "${string1} tidak sama dengan ${var}."
        fi
        ```
        
3. Operator Aritmetika
    
    Operator aritmetika di Bash memungkinkan perbandingan angka dengan sintaks khusus.
    
    1. Operator Aritmetika Umum
        
        * Sama dengan
            
            ```bash
            [[ ${num1} -eq ${num2} ]]
            ```
            
        * Tidak sama dengan
            
            ```bash
            [[ ${num1} -ne ${num2} ]]
            ```
            
        * Kurang dari
            
            ```bash
            [[ ${num1} -lt ${num2} ]]
            ```
            
        * Kurang dari atau sama dengan
            
            ```bash
            [[ ${num1} -le ${num2} ]]
            ```
            
        * Lebih besar dari
            
            ```bash
            [[ ${num1} -gt ${num2} ]]
            ```
            
        * Lebih besar atau sama dengan
            
            ```bash
            [[ ${num1} -ge ${num2} ]]
            ```
            
            **Catatan :** Bash menganggap argumen operator aritmetika sebagai bilangan bulat (integer) yang bisa bernilai positif atau negatif.
            
    2. Contoh : Perbandingan Numerik
        
        ```bash
        #!/bin/bash
        
        num1=15
        num2=20
        
        if [[ ${num1} -lt ${num2} ]]; then
          echo "${num1} lebih kecil dari ${num2}"
        fi
        
        if [[ ${num2} -ge ${num1} ]]; then
          echo "${num2} lebih besar atau sama dengan ${num1}"
        fi
        
        if [[ ${num1} -ne ${num2} ]]; then
          echo "${num1} tidak sama dengan ${num2}"
        fi
        ```
        
4. Menggabungkan Kondisi
    
    Kalian dapat membuat pengujian yang lebih kompleks dengan menggabungkan beberapa ekspresi kondisional menggunakan operator logika.
    
    1. Operator Logika
        
        * AND (&&): kedua kondisi harus bernilai true.
            
            ```bash
            [[ kondisi1 ]] && [[ kondisi2 ]]
            ```
            
        * OR (||): setidaknya salah satu kondisi harus bernilai true.
            
            ```bash
            [[ kondisi1 ]] || [[ kondisi2 ]]
            ```
            
    2. Contoh : Kondisi Gabungan
        
        ```bash
        #!/bin/bash
        
        umur=22
        negara="Indonesia"
        
        if [[ ${umur} -ge 17 ]] && [[ ${negara} == "Indonesia" ]]; then
            echo "Kalian memenuhi syarat untuk mencoblos."
        else
            echo "Kalian tidak memenuhi syarat untuk mencoblos."
        fi
        ```
        
5. Operator Exit Status
    
    Bash menyimpan exit status dari perintah terakhir dalam variabel khusus `$?`. Ini digunakan untuk menentukan apakah perintah berhasil atau gagal.
    
    1. Mengecek Exit Status
        
        * Perintah Berhasil (exit status 0) :
            
            ```bash
            [[ $? -eq 0 ]]
            ```
            
        * Perintah Gagal (exit status non-zero) :
            
            ```bash
            [[ $? -ne 0 ]]
            ```
            
    2. Contoh : Mengecek Keberhasilan Perintah
        
        ```bash
        #!/bin/bash
        
        ls /nonexistent/path
        if [[ $? -eq 0 ]]; then
            echo "Perintah berhasil dijalankan."
        else
            echo "Perintah gagal dijalankan."
        fi
        ```
        
        Jika perintah `ls` tidak menemukan path, exit status non-zero akan membuat script menampilkan “Perintah gagal dijalankan”