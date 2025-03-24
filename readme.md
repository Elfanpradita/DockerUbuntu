# Panduan Install Docker di Ubuntu Server

## 1. Update Sistem
Jalankan perintah berikut untuk memastikan sistem kamu up-to-date:
```bash
sudo apt update && sudo apt upgrade -y
```

## 2. Install Dependensi
Docker memerlukan beberapa paket tambahan agar dapat diinstal dengan baik:
```bash
sudo apt install -y ca-certificates curl gnupg
```

## 3. Tambahkan GPG Key Resmi Docker
Jalankan perintah ini untuk menambahkan GPG key Docker:
```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo tee /etc/apt/keyrings/docker.asc > /dev/null
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

## 4. Tambahkan Repository Docker
Tambahkan repository resmi Docker ke sistem:
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## 5. Update Paket dan Install Docker
Setelah menambahkan repository, update paket dan install Docker:
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 6. Cek Status Docker
Pastikan Docker berjalan dengan baik:
```bash
sudo systemctl status docker
```
Jika Docker belum berjalan, jalankan:
```bash
sudo systemctl enable --now docker
```

## 7. (Opsional) Tambahkan User ke Grup Docker
Agar bisa menjalankan Docker tanpa `sudo`, tambahkan user ke grup `docker`:
```bash
sudo usermod -aG docker $USER
newgrp docker
```
Pastikan perubahan diterapkan dengan keluar dan masuk kembali ke sesi terminal.

## 8. Uji Instalasi
Coba jalankan container **Hello World** untuk memastikan Docker berfungsi:
```bash
docker run hello-world
```
Jika ada output sukses dari Docker, berarti instalasi sudah berhasil. 🚀

