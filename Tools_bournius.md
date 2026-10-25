tools Termux. Saya pilihkan versi BOURNIUS All-in-One sebagai pilihan awal.

Salin perintah ini ke aplikasi Termux:

pkg update -y && pkg upgrade -y
pkg install python git curl dnsutils iproute2 -y
mkdir -p ~/bournius
cd ~/bournius

Lalu buat menu terminal:

cat > bournius.sh <<'EOF'
#!/data/data/com.termux/files/usr/bin/bash

clear
echo -e "\033[1;34m"
echo "  ██████╗  ██████╗ ██╗   ██╗"
echo "  ██╔══██╗██╔═══██╗██╗   ██║"
echo "  ██████╔╝██║   ██║██║   ██║"
echo "  ██╔══██╗██║   ██║╚██╗ ██╔╝"
echo "  ██████╔╝╚██████╔╝ ╚████╔╝ "
echo "  ╚═════╝  ╚═════╝   ╚═══╝  "
echo -e "\033[1;31m       BOURNIUS TERMINAL\033[0m"
echo "================================"
echo "1. Informasi sistem"
echo "2. Cek koneksi internet"
echo "3. Cek DNS domain"
echo "4. Python terminal"
echo "5. Update paket"
echo "0. Keluar"
echo "================================"
read -p "Pilih menu: " pilih

case "$pilih" in
  1)
    uname -a
    df -h "$HOME"
    ;;
  2)
    curl -I --max-time 10 https://example.com
    ;;
  3)
    read -p "Masukkan domain: " domain
    dig "$domain"
    ;;
  4)
    python
    ;;
  5)
    pkg update && pkg upgrade
    ;;
  0)
    exit 0
    ;;
  *)
    echo "Pilihan tidak valid"
    ;;
esac

read -p "Tekan Enter untuk kembali..."
exec bash bournius.sh
EOF

chmod +x bournius.sh
bash bournius.sh

Menu ini menyediakan diagnostik dasar dan pemeriksaan DNS, bukan alat untuk membobol perangkat atau akun.

Referensi resmi: Termux di GitHub
 dan panduan paket Termux
.
GitHub
+1

Langkah selanjutnya: Setelah menu ini berjalan, kita bisa menambahkan tampilan neon, tools keamanan jaringan milik sendiri, dan server website lokal.
