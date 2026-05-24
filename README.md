# Praktikum KB - Pertemuan 9: Algoritma Genetika 1

Repositori ini berisi implementasi **Algoritma Genetika (Genetic Algorithm/GA)** untuk menyelesaikan masalah **Knapsack Problem**. Tujuannya adalah memilih kombinasi barang yang memiliki nilai profit (fitness) terbaik dengan tetap mempertimbangkan batasan kapasitas tas.

Algoritma ini diimplementasikan dalam bahasa Python dengan memisahkan fungsi-fungsinya ke dalam beberapa modul agar lebih terstruktur.

## Struktur File dan Folder

```text
.
├── README.md                      # Dokumentasi cara menjalankan proyek
└── Algoritma Genetika/            # Folder utama implementasi GA
    ├── inisiasipopulasi.py        # Modul untuk inisialisasi populasi (kromosom acak)
    ├── EvaluasiFitness.py         # Modul untuk menghitung fitness dari setiap individu
    ├── selection.py               # Modul seleksi (Roulette Wheel & Tournament Selection)
    ├── crossover.py               # Modul crossover (One-point, Two-point, Uniform)
    ├── mutation.py                # Modul mutasi (Swap, Inversion, Uniform)
    └── main.py                    # Script utama untuk menjalankan Algoritma Genetika
```

## Prasyarat (Requirements)

Sebelum menjalankan script utama, pastikan kamu telah menginstal library yang dibutuhkan. Buka terminal atau command prompt, kemudian jalankan perintah berikut:

```bash
pip install matplotlib numpy
```

*(Catatan: Modul `random` sudah termasuk dalam bawaan Python standard library, jadi tidak perlu diinstal).*

## Penjelasan Singkat Alur Algoritma

1. **Inisiasi Populasi**: Menggunakan fungsi `inisialisasi_populasi()` untuk membuat populasi awal berisi individu (kromosom) acak berupa gen biner `1` dan `0` (dipilih / tidak dipilih).
2. **Evaluasi Fitness**: Menggunakan `hitung_fitness()` untuk menghitung total nilai barang. Jika bobot barang melebihi kapasitas tas (50), fitness akan bernilai 0 (penalti).
3. **Seleksi**: Memilih kandidat orang tua terbaik. Dalam praktikum ini utamanya menggunakan _Roulette Wheel Selection_ untuk meneruskan keturunan ke generasi selanjutnya berdasarkan probabilitas fitness.
4. **Crossover**: Orang tua yang terpilih akan disilangkan (One-Point Crossover) untuk mendapatkan anak (solusi baru) dengan probabilitas *crossover_rate* (0.5).
5. **Mutasi**: Beberapa gen akan termutasi secara acak menggunakan *Swap Mutation* dengan *mutation_rate* (0.1) untuk memastikan variasi genetik yang baru.
6. **Perulangan Generasi**: Langkah-langkah di atas akan diulang sebanyak 50 generasi untuk mencari titik optimal (titik konvergen dari grafik plot).

## Cara Menjalankan Program

1. Buka Terminal / Command Prompt / PowerShell.
2. Navigasikan ke dalam folder **`Algoritma Genetika`**:
   ```bash
   cd "Algoritma Genetika"
   ```
3. Jalankan file `main.py`:
   ```bash
   python main.py
   ```
4. Output berupa grafik plot evaluasi nilai fitness per generasi (`matplotlib`) akan otomatis terbuka. 
5. Setelah jendela grafik ditutup (X), terminal akan memunculkan nilai fitness terbaik, total bobot, dan daftar barang yang terpilih di dalam knapsack.

  