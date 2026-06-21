# Analisis Sentimen Komentar Instagram untuk Deteksi Cyberbullying

Proyek Kecerdasan Buatan ini berfokus pada deteksi tindakan perundungan digital atau ujaran kebencian pada kolom komentar Instagram berbahasa Indonesia. Sistem ini memanfaatkan integrasi metode pembobotan Term Frequency-Inverse Document Frequency (TF-IDF) dan algoritma klasifikasi Multinomial Naive Bayes.

## Metode dan Alur Sistem

Proyek ini dikembangkan melalui beberapa tahapan pengolahan data teks, yaitu:

1. Text Preprocessing: Meliputi tahap Case Folding untuk menyamakan huruf kecil, Filtering untuk membersihkan karakter pengganggu, Tokenizing untuk memotong kata, serta Stemming menggunakan library Sastrawi untuk mengubah kata berimbuhan menjadi kata dasar.
2. Ekstraksi Fitur: Menggunakan TF-IDF untuk memberikan nilai numerik atau bobot statistik pada setiap kata berdasarkan tingkat kepentingannya di dalam dokumen.
3. Klasifikasi: Menerapkan algoritma Multinomial Naive Bayes untuk mengelompokkan teks komentar secara otomatis ke dalam kategori Positive atau Negative.

## Karakteristik Dataset

Dataset yang digunakan disimpan dalam berkas CSV dengan nama dataset_komentar_instagram_cyberbullying.csv. File ini memuat tiga atribut utama, yaitu:
* Id: Sebagai nomor identifikasi unik.
* Sentiment: Sebagai label target, yaitu positive atau negative.
* Instagram Comment Text: Berisi data teks komentar mentah berbahasa Indonesia.

## Hasil dan Evaluasi Model

Pengujian dilakukan dengan membagi dataset secara acak menggunakan metode stratified splitting dengan proporsi 80 persen data pelatihan (320 sampel) dan 20 persen data pengujian (80 sampel).

Model berhasil memprediksi dengan benar sebanyak 65 data teks dari total 80 data uji, yang menghasilkan tingkat akurasi akhir sebesar 81.25 persen.

Detail visualisasi matriks evaluasi (Confusion Matrix) menunjukkan distribusi sebagai berikut:
* True Negative (TN): 35 data komentar aktual kelas negatif yang berhasil diprediksi secara tepat oleh sistem.
* True Positive (TP): 30 data komentar aktual kelas positif yang berhasil diprediksi secara tepat oleh sistem.
* False Positive (FP): 5 data komentar aktual kelas negatif yang keliru diprediksi sebagai kelas positif.
* False Negative (FN): 10 data komentar aktual kelas positif yang keliru diprediksi sebagai kelas negatif.

Batas kesalahan prediksi model sebesar 18.75 persen dipengaruhi oleh beberapa faktor linguistik khas media sosial, seperti penggunaan kata negasi atau sarkasme yang belum mampu ditangkap konteksnya secara utuh oleh asumsi independensi Naive Bayes, serta adanya variasi penulisan kata non-baku yang tidak berhasil diubah ke kata dasar asli saat proses stemming.

## Fitur Program

Kode program yang dijalankan pada Google Colab menyediakan fitur-fitur sebagai berikut:
* Pemisahan data otomatis.
* Ekstraksi fitur teks.
* Visualisasi heatmap Confusion Matrix.
* Sesi demo interaktif, di mana pengguna dapat memasukkan kalimat komentar baru untuk langsung diuji dan dilihat hasil prediksi sentimen beserta nilai probabilitas keyakinan model secara real-time.
