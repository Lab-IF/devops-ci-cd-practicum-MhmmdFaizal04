# Penjelasan Setiap Branch pada Praktik GitFlow

Berdasarkan *workflow* GitFlow yang diterapkan pada **Task 2**, berikut adalah fungsi dan tujuan tiap branch yang berada pada siklus repositori kita:

1. **`main`**  
   Merupakan branch mutlak (utama) yang menampung *source code* siap produksi (Production-Ready). Kode di branch ini sangat stabil dan sering mendeskripsikan versi rilis (*tagged release*, misalnya `v1.0.0`). Merging ke sini hanya bisa dilakukan dari branch khusus rilis atau *hotfix*.

2. **`develop`**  
   Titik penyatuan atau integrasi konstan. Kode pada fase pengembangan fitur dilemparkan lalu di-*merge* ke dalam branch ini. Dari sini pula, branch rilis dilahirkan saat fitur dirasa sudah dirangkum cukup.

3. **`feature/user-auth`**  
   Branch spesifik pendukung fitur. Dibuat semata-mata untuk mengaplikasikan fitur autentikasi (fokus kecil tersendiri). Branch ini disemai (dilahirkan) dari `develop` pada poin tertentu, lalu sesudah fiturnya benar dan stabil, akan di-*merge* kembali ke dalam `develop`, dan branch featur ini dapat dihapus sesudahnya.

4. **`release/1.0.0`**  
   Persiapan akhir peluncuran rilis program. Branch rilis dilahirkan dari `develop` untuk merapikan sentuhan terakhir—seperti memutakhirkan nomor versi—tanpa menghambat proses pengembangan fitur lain. Apabila pengeritingan sudah memadai di release branch ini, rilis pun diintegrasikan (di-merge) ke dalam `main` dan diklon pada `develop` juga untuk menyamakan siklus versi pengembangan. Setelah siap, branch `release/1.0.0` akan dihapus.
