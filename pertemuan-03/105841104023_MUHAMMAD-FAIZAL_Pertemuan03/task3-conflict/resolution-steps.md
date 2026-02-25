# Langkah-langkah Penyelesaian Merge Conflict

Berikut adalah langkah demi langkah saat mensimulasikan dan menyelesaikan konflik merge (Merge Conflict) pada Git:

### Langkah 1: Skenario Konflik Terjadi
1. Sebuah file percontohan bernama `conflict.txt` diinisialisasi di branch `main`.
2. Dua branch (`branch-a` dan `branch-b`) diciptakan mengambil referensi *commit* yang identik dari basis origin `main`.
3. Keduanya melakukan pengubahan kode **pada baris yang sama** di file `conflict.txt` secara mandiri.
4. Ketika `branch-a` dilebur (*merge*) masuk ke dalam `main`, proses berjalan aman karena hal ini semacam *Fast-Forward* yang murni pergeseran pointer.

### Langkah 2: Identifikasi Merge Conflict
1. Sesudah repositori lokal `main` telah bersilangan isi dengan `branch-a`, ada benturan logis saat menginstruksikan Git melebur (merge) `branch-b` ke `main`. Git tidak akan bisa menafsirkan baris mana yang harus dibuang/dipertahankan.
2. Ketika dijalankan `git merge branch-b`, muncullah peringatan semacam **`CONFLICT (content): Merge conflict in conflict.txt`**.
3. Git memberikan jeda proses supaya intervensi *developer* diberlakukan.

### Langkah 3: Eksekusi Perbaikan (Resolving)
1. Perintah `git status` dijalankan dan mengonfirmasi keberadaan *Unmerged paths*, menandakan `conflict.txt` yang perlu kita tengok dan bereskan.
2. Saat saya membuka teks terkait lewat editor (misalnya VS Code/Nano), git meninggalkan jejak pembatas penanda konflik di file:
   - `<<<<<<< HEAD` yang menunjuk isi saat ini `branch-a` / *Current Change*,
   - `=======` seperator antar baris sengketa,
   - `>>>>>>> branch-b` penunjuk konten pasokan `branch-b` / *Incoming Change*.
3. Dengan hati-hati, baris-baris penanda (`<<<`, `===`, `>>>`) saya lenyapkan manual lewat editor. Kemudian memastikan hasil akhir (tampilan penggabungan fungsional file sebelum dan sesudah) berdasar konteks aplikasi.

### Langkah 4: Penyelesaian
1. Setelah teks berhasil dimodifikasi sedemikian rupa sebagai tahap resolusi akhir dan di-save.
2. Kita perlu 'meneruskan' kepada Git bahwa *conflict stage* usai. Sederhananya memberitahu lewat _staging_ baru pada file yang disengketa (`git add conflict.txt`).
3. Dilanjutkan dengan menutup status merge dengan mengonfirmasi komit *merge default* tanpa modifikasi berlebih dari sisa jeda (*commit* terakhir dikesahkan, `git commit -m "resolve: merge conflict between branch-a and branch-b"`). Konflik berhasil diatasi.
