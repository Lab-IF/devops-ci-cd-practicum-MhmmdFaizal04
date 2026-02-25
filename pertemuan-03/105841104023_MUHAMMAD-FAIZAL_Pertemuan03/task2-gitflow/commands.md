# Daftar Commands - Task 2: GitFlow

Berikut adalah daftar perintah Git yang dijalankan untuk mengimplementasikan manajemen rilis menggunakan GitFlow:

```bash
# 1. Setup GitFlow (Membuka branch develop dari main)
git checkout main
git checkout -b develop
git push -u origin develop

# 2. Buat feature branch untuk mengembangkan fungsi
git checkout -b feature/user-auth develop

# 3. Kerjakan fitur di branch feature/user-auth (Beberapa commit)
echo "login functionality" > auth.js
git add auth.js
git commit -m "feat: add login function"

echo "logout functionality" >> auth.js
git add auth.js
git commit -m "feat: add logout function"

# 4. Merge hasil fitur ke dalam develop
git checkout develop
git merge --no-ff feature/user-auth -m "Merge feature/user-auth into develop"
git push origin develop

# 5. Buat release branch untuk stabilisasi rilis aplikasi
git checkout -b release/1.0.0 develop

# 6. Bump version (Simulasi pembaruan versi sebelum rilis)
echo "version: 1.0.0" > version.txt
git add version.txt
git commit -m "chore: bump version to 1.0.0"

# 7. Merge release branch secara resmi ke main
git checkout main
git merge --no-ff release/1.0.0 -m "Release 1.0.0"
git tag -a v1.0.0 -m "Version 1.0.0"
git push origin main --tags

# 8. Merge release ke develop agar semua track update release/hotfix disinkronisasi
git checkout develop
git merge --no-ff release/1.0.0 -m "Merge release/1.0.0 into develop"
git push origin develop

# 9. Cleanup - Hapus branch yang orientasinya sementara
git branch -d feature/user-auth
git branch -d release/1.0.0
```
