---
title: "Belajar Bash Scripting Part 7 : Array dan String Slicing"
datePublished: Thu Feb 13 2025 05:55:24 GMT+0000 (Coordinated Universal Time)
cuid: cm72xejj2000309ks9qk15ase
slug: belajar-bash-scripting-part-7-array-dan-string-slicing
tags: unix, bash, bash-script

---

Dalam Bash, array memungkinkan kalian menyimpan banyak nilai dalam satu variabel. Sementara itu, string slicing membantu kalian mengambil bagian tertentu dari sebuah teks. Kedua fitur ini sangat berguna untuk memanipulasi data dalam script.

1. **Array di Bash**
    
    1. Mendeklarasikan Array
        
        Untuk membuat array, gunakan tanda kurung `()` dengan nilai yang dipisahkan oleh spasi :
        
        ```bash
        my_array=("nilai 1" "nilai 2" "nilai 3" "nilai 4"
        ```
        
        Kenapa Tidak Pakai Koma?
        
        Tidak seperti bahasa pemrograman lain seperti JavaScript atau Python yang menggunakan koma (`,`) untuk memisahkan elemen array, Bash menggunakan spasi.
        
        Kenapa begitu? Karena Bash memperlakukan spasi sebagai pemisah antara argumen dan elemen array.
        
    2. Mengakses Elemen Array
        
        Bash menggunakan indeks **zero-based**, jadi elemen pertama berada di indeks `0`. Untuk mengambil nilai, gunakan format berikut :
        
        ```bash
        echo ${my_array[1]} # Output: nilai 2
        ```
        
        1. Indeks Negatif (Negative Indexing)
            
            Kalian juga bisa menggunakan indeks negatif untuk mengambil elemen dari belakang :
            
            ```bash
            echo ${my_array[-1]} # Output: nilai 4
            ```
            
    3. Mengakses Semua Elemen
        
        Untuk menampilkan semua elemen dalam array :
        
        ```bash
        echo ${my_array[@]} # Output: nilai 1 nilai 2 nilai 3 nilai 4
        ```
        
    4. Menghitung Jumlah Elemen
        
        Gunakan tanda `#` sebelum nama array untuk mengetahui jumlah elemen dalam array :
        
        ```bash
        echo ${#my_array[@]} # Output: 4
        ```
        
    5. Ringkasan
        
 | Sintaks | Fungsi |
 | --- | --- |
 | `${my_array[0]}` | Mengakses elemen pertama |
 | `${my_array[-1]}` | Mengakses elemen terakhir |
 | `${my_array[@]}` | Mengakses semua elemen |
 | `${#my_array[@]}` | Menghitung jumlah elemen |


    | Sintaks | Fungsi |
    | --- | --- |
    | `${my_array[0]}` | Mengakses elemen pertama |
    | `${my_array[-1]}` | Mengakses elemen terakhir |
    | `${my_array[@]}` | Mengakses semua elemen |
    | `${#my_array[@]}` | Menghitung jumlah elemen |
        
2. **Array Slicing**
    
    Meskipun Bash tidak memiliki fitur slicing seperti beberapa bahasa pemrogramain lain (contoh: Python), kita masih bisa melakukan slicing menggunakan kombinasi indeks dan panjang.
    
    1. Sintaks Array Slicing
        
        ```bash
        ${array[@]:start:length}
        ```
        
        * start: Indeks awal (mulai dari 0)
            
        * length: Jumlah elemen yang ingin diambil
            
    2. Contoh Penggunaan
        
        ```bash
        #!/bin/bash
        
        array=("A" "B" "C" "D" "E")
        
        # Tampilkan seluruh array
        echo "${array[@]}" # Output: A B C D E
        
        # Ambil satu elemen
        echo "${array[@]}" # Output: B
        
        # Ambil 3 elemen mulai dari indeks 1
        echo "${array[@]:1:3}" # Output: B C D
        
        # Ambil semua elemen dari indeks 3 sampai akhir
        echo "${array[@]:3}" # Output: D E
        ```
        
    3. Hal yang Perlu Diperhatikan
        
        * Gunakan `[@]` untuk mengakses semua elemen.
            
        * Gunakan tanda kutip (`””`) untuk menjaga format output tetap rapi.
            
3. **String Slicing**
    
    Bash juga memungkinkan kalian untuk memotong bagian dari string dengan sintaks berikut :
    
    ```bash
    ${string:start:length}
    ```
    
    * start: Indeks awal (zero-based)
        
    * length: Jumlah karakter yang ingin diambil
        
    
    1. Contoh Penggunaan
        
        ```bash
        #!/bin/bash
        
        text="ABCDE"
        
        # Ambil 2 karakter dari indeks 0
        echo "${text:0:2}" # Output: AB
        
        # Ambil semua karakter dari indeks 3 hingga akhir
        echo "${text:3}" # Output: DE
        
        # Ambil 3 karakter dari indeks 1
        echo "${text1:3}" # Output: BCD
        
        # Jika panjang melebihi jumlah karakter yang tersedia, Bash akan mengambil sampai akhir
        echo "${text:3:3}" # Output: DE (karena hanya tersisa 2 karakter)
        ```
        
    2. Penjelasan
        
        Dalam Bash, parameter kedua (`length`) bukanlah indeks akhir, tetapi jumlah maksimum karakter yang ingin diambil. Jika jumlah karakter yang diminta lebih banyak dari yang tersedia, Bash hanya mengambil hingga karakter terakhir tanpa error.
        
        Contoh Perbedaan Bash vs Python
        
        ```bash
        text="ABCDEFG"
        
        echo "${text:2:3}" # Output: CDE
        
        echo "${text:5:10}" # Output: FG (hanya 2 karakter tersedia)
        ```
        
        ```python
        text = "ABDCEFG"
        print(text[2:5]) # Output: CDE
        print(text[5:15]) # Output: FG (tidak error, hanya mengambil yang tersedia)
        ```
        
    3. Contoh Praktis
        
        ```bash
        #!/bin/bash
        
        text="Hello, World!"
        
        # Ambil 5 karakter mulai dari indeks 7
        echo "${text:7:5}" # Output: World
        
        # Ambil 10 karakter mulai dari indeks 7 (meskipun ada 6 karakter tersisa)
        echo "${text:7:10}" # Output: World!
        ```
        
    4. Hal yang Perlu Diperhatikan
        
        * Bash tidak mendukung indeks negatif untuk slicing string. Jika `length` tidak diberikan, maka akan mengambil karakter hingga akhir string.
            

    | d | d | d | d | m |
    | --- | --- | --- | --- | --- |
    |  |  |  |  |  |
    | d | dd |  |  |  |
    | d | dd |  |  |  |