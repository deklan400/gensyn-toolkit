<START>

<!-- BANNER -->
<p align="center">
  <img src="https://i.ibb.co/3zxGBM4/GENSYN-BANNER.png" width="90%" />
</p>

<h1 align="center">⚡ Gensyn RL-Swarm — Auto Installer + Telegram Bot</h1>

<p align="center">
  One-Click Installer • Telegram Control • Auto-Monitor • Danger Zone
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Gensyn-Testnet-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Telegram-Bot-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Auto--Install-YES-orange?style=for-the-badge">
  <img src="https://img.shields.io/badge/Systemd-Supported-yellow?style=for-the-badge">
  <img src="https://img.shields.io/badge/Linux-Ubuntu%2020.04%20%7C%2022.04-purple?style=for-the-badge">
</p>

---

## 🧠 Overview

Bundle ini menyediakan:  
✅ Auto-Installer Gensyn RL-Swarm  
✅ Telegram Control panel  
✅ Auto-Monitor + Auto-Restart  
✅ Update / Reinstall / Uninstall via Telegram  
✅ Systemd Service  
✅ Danger Zone actions  

> Semua bisa dikontrol tanpa SSH — cukup Telegram 📱  

**Support VPS:**  
- Ubuntu 20.04 / 22.04 / 24.04  
- Debian 12  

---

## ✨ Features

✅ One-Command Install  
✅ Start / Stop / Restart Node  
✅ CPU / RAM / Disk / Uptime Monitoring  
✅ Last Round tracking  
✅ Log Viewer (`journalctl`)  
✅ Auto-Monitor (systemd timer)  
✅ Auto-Restart + Auto-Reinstall  
✅ Status Cache Anti-Spam  
✅ Danger Zone (optional password)  
✅ Multiple allowed Telegram users  
✅ AUTO_INSTALLER → update installer tanpa update bot  

---

# 🚀 Quick Install

> Jalankan di VPS

```bash
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```

Installer akan:  
✅ Install dependencies  
✅ Install docker  
✅ Clone RL-Swarm  
✅ Copy keys → /root/rl_swarm/keys  
✅ Setup Telegram bot  
✅ Setup auto-monitor  
✅ Enable systemd  
✅ Start node  

---

# 🔑 Identity (Wajib)

Simpan 3 file identity Anda di:

```
/root/deklan/
```

| File | Keterangan |
|------|------------|
| swarm.pem | Private key |
| userApiKey.json | API key |
| userData.json | Profile |

Jika kurang → install akan berhenti.

---

# 🏗 Struktur Folder

```
/root/deklan/
│── swarm.pem
│── userApiKey.json
└── userData.json

/root/rl_swarm/
│── keys → symlink → /root/deklan/
│── docker-compose.yml
│── run_node.sh
│── .env
└── ...
```

Keys otomatis:

```
/root/rl_swarm/keys
```

---

# 🤖 Telegram Bot

### ✅ After install → edit .env

```
nano /opt/deklan-node-bot/.env
```

Isi minimal:

```
BOT_TOKEN=YOUR_TOKEN
CHAT_ID=123456
```

Restart:

```
systemctl restart bot
```

---

## ☰ Menu Telegram

| Menu | Fungsi |
|------|--------|
| 📊 Status | CPU, RAM, Disk, uptime |
| 🟢 Start | Start service |
| 🔴 Stop | Stop service |
| 🔁 Restart | Restart |
| 📜 Logs | Show logs |
| ℹ round | Last round |
| 🧩 Installer | Install/update/reinstall/uninstall |
| ⚠ Danger Zone | Hard cleanup + reboot |

---

# 🔧 Installer Menu (Telegram)

Aksi → konfirmasi → ketik `YES`

| Action | Script |
|--------|--------|
| Install | install.sh |
| Reinstall | reinstall.sh |
| Update | update.sh |
| Uninstall | uninstall.sh |

Semua dijalankan remote → tanpa SSH.

---

# 🛰 Auto-Monitor

`monitor.timer` akan:  
✅ Cek status node  
✅ Jika mati → restart  
✅ Jika gagal → reinstall  
✅ Jika tetap gagal → kirim logs ke Telegram  

```
systemctl status monitor.timer
```

---

# ✅ Perintah Sistem

### Status
```
systemctl status gensyn
```

### Logs
```
journalctl -u gensyn -f
```

### Restart
```
systemctl restart gensyn
```

---

# ♻ Move VPS (Pindah)

1) Copy folder `/root/deklan/`  
2) Jalankan:

```
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```

Done ✅

---

# ❌ Uninstall

```
systemctl stop gensyn
systemctl disable gensyn
rm /etc/systemd/system/gensyn.service
rm -rf /root/rl_swarm
systemctl daemon-reload
```

---

# 🧩 ENV Full Options

```
BOT_TOKEN=
CHAT_ID=
ALLOWED_USER_IDS=
SERVICE_NAME=gensyn
NODE_NAME=Gensyn-VPS
LOG_LINES=80
MONITOR_EVERY_MINUTES=180
ENABLE_DANGER_ZONE=0
DANGER_PASS=
AUTO_INSTALLER_GITHUB=https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/
```

---

# 🧨 Danger Zone

> ENABLE_DANGER_ZONE=1 + DANGER_PASS wajib

Aksi tersedia:  
- Hapus RL-Swarm  
- Clean Docker  
- Remove Swap  
- Full Clean  
- Reboot  

---

# 📁 Repo Structure

```
├── install.sh
├── reinstall.sh
├── update.sh
├── restart.sh
├── uninstall.sh
├── run_node.sh
│
├── bot.py
├── monitor.py
├── .env.example
│
├── bot.service
├── monitor.service
├── monitor.timer
├── gensyn.service
│
└── README.md
```

---

# ✅ Sample Telegram Alerts

✅ UP
```
✅ Node UP
CPU 23% • RAM 68% • Disk 50%
Round: Join X
```

🚨 DOWN
```
🚨 DOWN — Restarting…
```

🟢 Recovered
```
✅ Recovered
```

❌ Failed
```
❌ FAILED — manual fix required
<logs>
```

---

# ❓ FAQ

**Q: Perlu GPU?**  
Tidak.

**Q: Aman?**  
Tidak kirim data ke server mana pun.

**Q: Support OS?**  
Ubuntu 20/22/24, Debian 12.

---

# ❤️ Credit

❤️ Built by **Deklan × GPT-5**

<END>
