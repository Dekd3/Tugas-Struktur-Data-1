# Sistem Untuk Menganalisis Nilai

Program Python sederhana untuk mengolah nilai 10 mahasiswa pakai array. Aplikasi ini menghitung nilai terbaik dan terburuk, rata-rata kelas, persentase kelulusan (nilai ≥60), dan menampilkan hasil dalam bentuk 2 grafik batang berdampingan.

### Array
Array adalah cara menyimpan banyak data dalam satu kotak dengan nomor urut mulai dari 0. Jadi gampang banget ngambil data jika menggunakan nomor kotaknya.
Array cocok untuk menyimpan daftar nilai mahasiswa karena bisa langsung dihitung semuanya sekaligus.

# Cara Program Bekerja

### Membuat Kotak Penyimpanan
Langkah pertama, buat kotak kosong untuk menyimpan 10 nilai:

```
nilai = []
```


# Mengisi Data (Input)
Program akan meminta user untuk memasukan total 10 nilai ke user. jika user memasukan angka di atas 100 program akan meminta user untuk memasukan nomor ulang sampai angka berada di 0-100. 

```
for i in range(10):
    while True:
        try:
            n = float(input(f"Nilai {i+1}: "))
            if 0 <= n <= 100:
                nilai.append(n)
                break
            print("Nilai 0-100")
        except:
            print("Angka valid")
```

### Contoh saat program jalan:
```
Nilai 1: 44    Masuk kotak 0
Nilai 2: 55    Masuk kotak 1
Nilai 3: 66    Masuk kotak 2
Nilai 4: 77    Masuk kotak 3
Nilai 5: 88    Masuk kotak 4
Nilai 6: 99    Masuk kotak 5
Nilai 7: 76    Masuk kotak 6
Nilai 8: 87    Masuk kotak 7
Nilai 9: 65    Masuk kotak 8
Nilai 10: 67   Masuk kotak 9
```

#### Hitungan Statistik
Program akan menghitung 3 hal penting:

```
max_n = max(nilai)     > Cari yang paling tinggi = 99
min_n = min(nilai)     > Cari yang paling rendah = 44
rata = sum(nilai) / 10 > Jumlah semua dibagi 10 = 72.4
```

### Hasil hitungan:
- Paling tinggi: 99.0
- Paling rendah: 44.0  
- Rata-rata: 72.4


### Mengcek berapa yang lulus
Program cek berapa orang yang nilainya 60 ke atas:

```
lulus = sum(1 for x in nilai if x >= 60)
```

Program membuka tiap kotak satu-satu, kalau isinya ≥60 berarti lulus. Hasil: 8 orang lulus dari 10 orang.

#### Menampilkan Hasil
Hasilnya ditampilkan 2 cara: tulisan dan grafik.

Tulisan di layar:
```
print("\nHASIL ANALISIS:")
print(f"Tertinggi: {max_n}")
print(f"Terendah: {min_n}")
print(f"Rata-rata: {rata:.1f}")
print(f"Lulus (>=60): {lulus}/10")
```

```
HASIL ANALISIS:
Tertinggi: 99.0
Terendah: 44.0
Rata-rata: 72.4
Lulus (>=60): 8/10
```

### Grafik (Bar Chart):
```
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

# Grafik 1: Nilai paling tinggi vs paling rendah
ax1.bar(['Tertinggi', 'Terendah'], [max_n, min_n], color=['green', 'red'])
ax1.set_ylim(0, 100)

# Grafik 2: Lulus vs Tidak lulus
ax2.bar(['Lulus', 'Gagal'], [lulus, 10-lulus], color=['green', 'red'])
ax2.set_ylim(0, 10)
```
# Analisis Kompleksitas

Kompleksitas utama yang dipakai program ini adalah `O(n)` karena ada banyak operasi yang harus memproses semua data satu per satu sebanyak `n` kali. Contohnya:

```python
for i in range(10):      
    n = float(input(f"Nilai {i+1}: "))
    nilai.append(n)
```
dan juga:
```
max_n = max(nilai)          
min_n = min(nilai)          
rata = sum(nilai) / 10      
lulus = sum(1 for x in nilai if x >= 60)  
```

Di kasus kita, `n = 10` jadi setiap operasi harus cek 10 data secara berurutan.Makanya disebut `O(n)` - linear time complexity.
Selain `O(n)`, program juga pakai `O(1)` yaitu operasi yang super cepat dan ga peduli berapa banyak data. `O(1)` adalah kompleksitas tercepat.
Notasi `O(1)` dipakai di:
```
nilai.append(n)     
10 - lulus          
len(nilai)          
```

Fungsi `len()` punya kompleksitas `O(1)` karena Python udah nyimpen info jumlah elemen list secara langsung di memori, jadi ga perlu hitung ulang dari awal.

# Apa Yang Dipelajari
Dari program ini kita belajar implementasi array Python untuk menyimpan dan mengelola 10 data nilai mahasiswa, pola traversal O(n) yang harus memeriksa setiap elemen untuk operasi statistik seperti max/min/sum, pentingnya validasi input menggunakan try-except dan range checking untuk menjaga kualitas data, teknik subplot Matplotlib untuk visualisasi multi-grafik secara bersamaan, serta perbedaan kompleksitas waktu O(n) versus O(1) dalam evaluasi performa algoritma. 
