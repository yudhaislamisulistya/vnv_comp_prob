
# PROB = Yss'(t,y)

menghitung Prob =![aman](/assets/aman.png) melalui path exploration, pertama-tama kita perlu mengetahui apa yang dimaksud dengan![aman](/assets/aman.png) dan bagaimana menghitungnya.

![aman](/assets/aman.png) adalah probabilitas bahwa sistem akan berada dalam keadaan ss' pada saat t, dengan asumsi bahwa sistem telah berada dalam keadaan y pada saat sebelumnya. Probabilitas ini dapat dihitung dengan mengeksplorasi semua jalur yang mungkin ditempuh oleh sistem dari keadaan y menuju ke keadaan ss'.

Untuk menghitung Prob =![aman](/assets/aman.png) melalui path exploration, kita perlu mengikuti langkah-langkah berikut:

1. Inisialisasi variabel Prob dan Error dengan nilai 0, serta variabel Paths dengan keadaan y.
2. Selama Paths tidak kosong (∅), lakukan langkah-langkah berikut:
   - Pilih salah satu jalur (σ) dari Paths.
   - Hapus jalur tersebut dari Paths.
   - Jika probabilitas jalur tersebut (P(σ)) lebih besar dari w dan panjang jalur tersebut (|σ|) kurang dari sama dengan N, lakukan langkah-langkah berikut:
      - Jika keadaan terakhir dari jalur tersebut (last(σ)) sama dengan ss', tambahkan PP(λt, |σ|) · P(σ) · Pr {Yt ≤ y | k(σ)} ke variabel Prob. Untuk setiap keadaan (s') yang ada dalam set S, tambahkan jalur baru (σ ◦ s') ke dalam Paths.
      - Jika tidak, abaikan jalur tersebut.
3. Setelah semua jalur di dalam Paths diperiksa, keluarkan hasil akhir dari Prob.

## Menghitung PP(λt, |σ|) atau Probabilitas Poisson

1. Tentukan nilai λt yang akan digunakan dalam perhitungan. Nilai λt ini dapat didapatkan dari data yang tersedia atau diestimasi dengan menggunakan metode yang sesuai.
2. Tentukan panjang jalur σ dengan menggunakan fungsi len(). Panjang jalur dapat dihitung dengan menghitung jumlah elemen dalam list atau tuple σ.
3. Hitung nilai PP(λt, |σ|) dengan menggunakan rumus PP(λt, n) = ![Rumus](/assets/Rumus.png)
4. Kembalikan nilai PP(λt, |σ|) yang telah dihitung sebagai hasil akhir dari perhitungan.

## Menghitung PP(σ) atau Probabilitas Path

1. Tentukan keadaan awal dari jalur σ, yaitu keadaan pertama dari list atau tuple σ.
2. Tentukan keadaan akhir dari jalur σ, yaitu keadaan terakhir dari list atau tuple σ.
3. Tentukan matriks probabilitas U yang akan digunakan untuk menghitung P(σ). Matriks ini dapat diperoleh dari data yang tersedia atau diestimasi dengan menggunakan metode yang sesuai.
4. Hitung probabilitas jalur σ dengan menggunakan rumus P(σ) = Us0s1 · Us1s2 · · · ·Usn−1sn. Dimana s0 adalah keadaan awal dari jalur σ yang telah ditentukan pada langkah 1, dan sn adalah keadaan akhir dari jalur σ yang telah ditentukan pada langkah 2.
5. Kembalikan nilai P(σ) yang telah dihitung sebagai hasil akhir dari perhitungan.

## Menghitung Pr(t, y, k_sigma) atau Probabilitas Rewards

1. Tentukan nilai t, y, dan k_σ yang akan digunakan dalam perhitungan. Nilai t adalah waktu yang akan dicari probabilitasnya, y adalah keadaan sebelumnya, dan k_σ adalah kondisi yang terkait dengan jalur σ.
2. Tentukan jumlah rewards yang diterima pada saat t, dengan menggunakan data yang tersedia atau dengan mengestimasinya dengan menggunakan metode yang sesuai.Tentukan batas atas rewards yang dianggap diterima, dengan menggunakan data yang tersedia atau dengan mengestimasinya dengan menggunakan metode yang sesuai.
3. Hitung probabilitas rewards dengan menggunakan rumus Pr(t, y, k_σ) = (jumlah rewards yang diterima pada saat t) / (batas atas rewards yang dianggap diterima).
4. Kembalikan nilai Pr(t, y, k_σ) yang telah dihitung sebagai hasil akhir dari perhitungan.

## Fungsi Generate Stochastic Matrix

1. kita membuat fungsi create_random_stochastic_matrix() yang menerima integer n dan m sebagai parameter dan mengembalikan sebuah matriks n x m dengan nilai-nilai acak.
2. Fungsi tersebut menggunakan fungsi rand() dari modul random untuk membuat matriks n x m dengan nilai-nilai acak antara 0 dan 1.
3. Kemudian, kita menggunakan operasi pembagian dan sumasi untuk memnormalisasi matriks tersebut sehingga jumlah dari setiap baris adalah 1.
