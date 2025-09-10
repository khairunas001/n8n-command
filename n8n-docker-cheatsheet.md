# 🚀 Cheatsheet Docker CLI untuk n8n

Panduan singkat untuk menjalankan, menghentikan, dan mengelola **n8n** menggunakan Docker di **Windows** dan **Linux/Mac**.

---

## 📌 Perintah Utama

| Aksi                                | Windows (CMD / PowerShell)                                                                 | Linux / Mac (bash/zsh)                                                                 |
|-------------------------------------|--------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| **Run pertama kali (daemon mode)**  | `docker run -d --name n8n -p 5678:5678 -v C:\Users\<USERNAME>\.n8n:/home/node/.n8n n8nio/n8n` | `docker run -d --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n` |
| **Run sekali pakai (hapus otomatis saat stop)** | `docker run -it --rm -p 5678:5678 n8nio/n8n` | `docker run -it --rm -p 5678:5678 n8nio/n8n` |
| **Start container yang sudah ada**  | `docker start n8n` | `docker start n8n` |
| **Start + tampilkan log (attach)**  | `docker start -a n8n` | `docker start -a n8n` |
| **Stop container**                  | `docker stop n8n` | `docker stop n8n` |
| **Restart container**               | `docker restart n8n` | `docker restart n8n` |
| **Lihat log container**             | `docker logs -f n8n` | `docker logs -f n8n` |
| **Hapus container**                 | `docker rm n8n` | `docker rm n8n` |
| **Hapus + buat ulang container**    | `docker rm -f n8n && docker run -d --name n8n -p 5678:5678 -v C:\Users\<USERNAME>\.n8n:/home/node/.n8n n8nio/n8n` | `docker rm -f n8n && docker run -d --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n` |

# n8n User Management Reset Commands

Berikut adalah perbedaan command untuk reset user/email/password di **Linux** dan **Windows (PowerShell / CMD)**.

| OS / Shell | Command |
|------------|----------|
| **Linux / MacOS (bash/zsh)** | ```bash<br>docker exec -it n8n /bin/sh<br>n8n user-management:reset --email admin@example.com --password "Rahasia123"<br>``` |
| **Windows PowerShell** | ```powershell<br>docker exec -it n8n sh<br>n8n user-management:reset --email admin@example.com --password "Rahasia123"<br>``` |
| **Windows CMD** | ```cmd<br>docker exec -it n8n sh<br>n8n user-management:reset --email admin@example.com --password "Rahasia123"<br>``` |

## Catatan
- Gunakan `n8n user-management:reset` (pakai titik dua `:`), bukan spasi.  
- Pastikan image yang digunakan adalah **n8nio/n8n versi terbaru** (`>=1.0.0`), karena fitur ini tidak tersedia di versi lama.  
- Jika muncul error `Command "user-management" not found`, lakukan update image:  
  ```bash
  docker pull n8nio/n8n:latest
  docker stop n8n
  docker rm n8n
  docker run -d --name n8n -p 5678:5678 -v C:\Users\<USER>\.n8n:/home/node/.n8n n8nio/n8n:latest



---

## 📂 Catatan Path

- **Windows**: ganti `<USERNAME>` dengan nama user kamu. Contoh:  
  ```
  C:\Users\khair\.n8n
  ```

- **Linux/Mac**: default menggunakan home directory `~/.n8n`.



---

## 🌐 Akses n8n

Setelah container berjalan, buka di browser:  
👉 [http://localhost:5678](http://localhost:5678)

---

## 🛠️ Tips Tambahan

- Jika port `5678` sudah terpakai, bisa ganti ke port lain, misalnya:
  ```bash
  docker run -d --name n8n -p 5679:5678 ...
  ```
  lalu akses di [http://localhost:5679](http://localhost:5679).

- Untuk melihat semua container (jalan & berhenti):
  ```bash
  docker ps -a
  ```



---
