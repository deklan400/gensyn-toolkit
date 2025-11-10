# ⚡ Gensyn RL-Swarm — Auto Installer + Telegram Bot

[![Release](https://img.shields.io/badge/Release-Stable-green?style=flat-square)]()
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)]()
[![Status](https://img.shields.io/badge/Platform-Linux-orange?style=flat-square)]()
[![Node](https://img.shields.io/badge/Gensyn-RL--Swarm-purple?style=flat-square)]()

🔥 One-Command Installer untuk menjalankan **Gensyn RL-Swarm Node**  
+ Telegram Bot untuk monitoring dari mana saja 📱  

Termasuk:
✅ Auto-Install  
✅ Telegram Bot  
✅ Auto Monitor  
✅ Systemd Service  

Cocok untuk deploy cepat / pindah VPS massal 🚀  


---

# ✨ Fitur Utama

✅ 1-Klik Auto-Install  
✅ Bisa pindah VPS kapan saja  
✅ Telegram Bot → Start / Stop / Restart / Logs / Status  
✅ Auto-Restart & Auto-Monitor  
✅ Tidak kirim data keluar  
✅ Aman  


---

# 📦 Persiapan (WAJIB)

Sebelum install, siapkan 3 file identity:

| File | Fungsi |
|------|--------|
| `swarm.pem` | Private key |
| `userApiKey.json` | API credential |
| `userData.json` | Account info |

Upload ke:

```
/root/deklan/
```

Jika tidak lengkap → installer berhenti sampai file lengkap ✅  


---

# 🚀 Quick Install

Copy & jalankan:

```bash
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```

Akan menjalankan:

✅ Validasi identity  
✅ Install dependencies  
✅ Install Docker  
✅ Clone RL-Swarm  
✅ Copy identity → keys  
✅ Install systemd service  
✅ Start otomatis  


---

# 📂 Struktur Folder

```
/root/deklan/
│── swarm.pem
│── userApiKey.json
└── userData.json

/home/gensyn/rl_swarm/
│── keys/
│     ├── swarm.pem
│     ├── userApiKey.json
│     └── userData.json
└── (RL-Swarm source)
```

Identity otomatis dicopy ke:

```
/home/gensyn/rl_swarm/keys/
```


---

# 🤖 Telegram Bot

Kontrol node langsung dari Telegram.

## ✅ UI PREVIEW

Letakkan gambar UI di folder:

```
/images/
```

| Menu | Status | Logs |
|------|--------|------|
| <img src="./images/menu.png" width="240"/> | <img src="./images/status.png" width="240"/> | <img src="./images/logs.png" width="240"/> |


---

# 🧠 Auto Monitor

Bot memantau node otomatis & restart bila mati.  
Akan kirim notifikasi ke Telegram ✅  


---

# ✅ Cek Status Node

```bash
systemctl status gensyn
```

Log live:
```bash
journalctl -u gensyn -f
```


---

# 🔄 Restart Node

```bash
systemctl restart gensyn
```

atau via installer:

```bash
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/reinstall.sh)
```


---

# ⚙ Info Service

| Komponen | Lokasi |
|---------|--------|
| Service | `/etc/systemd/system/gensyn.service` |
| Folder  | `/home/gensyn/rl_swarm/` |
| Keys    | `/home/gensyn/rl_swarm/keys/` |


---

# ♻ Re-Install (pindah VPS)

Cukup pindahkan folder identity:

```
/root/deklan/
```

Lalu jalankan ulang installer:

```bash
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```

→ Node langsung jalan ✅  


---

# ❌ Uninstall

```bash
systemctl stop gensyn
systemctl disable gensyn
rm /etc/systemd/system/gensyn.service
rm -rf /home/gensyn/rl_swarm
systemctl daemon-reload
```

---

# ✅ Output Contoh

```
[1/9] Checking identity files... ✅
[2/9] Updating system...
[3/9] Installing dependencies...
[4/9] Installing Docker...
[5/9] Cloning rl-swarm repo...
[6/9] Copying identity files...
[7/9] Installing systemd service...
[8/9] Starting RL-Swarm...
✅ Node aktif!
```


---

# ❓ FAQ

**Q: Bisa pindah VPS?**  
✅ Bisa → cukup pindah folder `/root/deklan/` lalu install

**Q: Data aman?**  
✅ Tidak kirim ke server lain

**Q: Compatible OS?**  
✔ Ubuntu 20/22/24  
✔ Debian 12  

**Q: Perlu GPU?**  
❌ Tidak wajib  


---

# 🔧 Troubleshoot

| Masalah | Solusi |
|--------|--------|
| Service mati | `systemctl restart gensyn` |
| Tidak ada log | `journalctl -u gensyn -f` |
| Key salah | Pastikan 3 file lengkap di `/root/deklan/` |
| Repo rusak | Hapus `/home/gensyn/rl_swarm/` & reinstall |


---

# 🌍 English Version

✅ One-command Gensyn RL-Swarm installer  
✅ Telegram bot remote control  
✅ Auto monitor & auto restart  
✅ Easy VPS migration  

Install:
```bash
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```


---

# ❤️ Credit

Built by **Deklan × GPT-5**  
