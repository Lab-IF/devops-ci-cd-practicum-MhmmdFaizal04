# Daftar Commands - Task 1: GitHub Flow

Berikut adalah daftar perintah Git yang dijalankan untuk mengimplementasikan GitHub Flow dalam praktik ini:

```bash
# 1. Clone atau buat repository baru
git init github-flow-practice
cd github-flow-practice

# 2. Buat file awal di main
echo "# My Project" > README.md
git add README.md
git commit -m "initial commit"

# 3. Buat feature branch
git checkout -b feature/add-homepage

# 4. Tambah file baru
echo '<!DOCTYPE html>
<html>
<head><title>Homepage</title></head>
<body><h1>Welcome!</h1></body>
</html>' > index.html

git add index.html
git commit -m "feat: add homepage"

# 5. Push branch
git push -u origin feature/add-homepage

# 6. Buat Pull Request di GitHub (Screenshot diambil pada tahap ini)

# 7. Merge ke main (setelah review via PR)
git checkout main
git merge feature/add-homepage
git push origin main

# 8. Hapus feature branch lokal dan remote
git branch -d feature/add-homepage
git push origin --delete feature/add-homepage
```
