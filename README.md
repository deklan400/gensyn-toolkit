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
  <img src="https://img.shields.io/badge/Ubuntu-20.04%20%7C%2022.04-purple?style=for-the-badge">
</p>

---

## 🧠 Overview

Bundle ini menyediakan:

✅ Auto-Installer RL-Swarm  
✅ Telegram Control Menu  
✅ Auto-Monitor + Auto-Heal  
✅ Update / Reinstall / Uninstall via Telegram  
✅ Systemd Service  
✅ Danger Zone tools  

> Semua bisa dikontrol TANPA SSH — cukup Telegram 📱  

Support VPS: Ubuntu 20/22/24, Debian 12

---

# 🚀 Quick Install

Jalankan:

bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)

---

# 🔑 Identity (WAJIB)

Folder:
  /root/deklan/

Harus berisi:
  swarm.pem
  userApiKey.json
  userData.json

Jika salah satu hilang → INSTALL STOP

---

# 📁 Struktur Folder

/root/deklan/
  swarm.pem
  userApiKey.json
  userData.json

/root/rl_swarm/
  keys → symlink → /root/deklan/
  docker-compose.yaml
  run_node.sh
  .env

---

# 🤖 Telegram Bot

Edit setelah install:
  nano /opt/deklan-node-bot/.env

Isi minimal:
  BOT_TOKEN=YOUR_TOKEN
  CHAT_ID=123456

Restart bot:
  systemctl restart bot

Sudah siap kontrol via Telegram ✅

---

## ☰ Menu Telegram

📊 Status — CPU/RAM/Disk/uptime  
🟢 Start — Start node  
🔴 Stop — Stop node  
🔁 Restart — Restart node  
📜 Logs — Show logs  
ℹ Round — Last round info  
🧩 Installer — Install/Update/Reinstall/Uninstall  
⚠ Danger Zone — Clean + Reboot  

---

# 🔧 Installer Menu

Melalui Telegram → Konfirmasi → Ketik YES

Install     → install.sh  
Reinstall   → reinstall.sh  
Update      → update.sh  
Uninstall   → uninstall.sh  

---

# 🛰 Auto-Monitor

monitor.timer otomatis:
✅ Cek node  
✅ Restart jika mati  
✅ Reinstall jika tetap fail  
✅ Kirim logs ke Telegram  

Status
  systemctl status monitor.timer

---

# ✅ Perintah Sistem

Status:
  systemctl status gensyn

Start:
  systemctl start gensyn

Restart:
  systemctl restart gensyn

Logs:
  journalctl -u gensyn -f

---

# 🔄 Migrasi VPS

Copy folder:
/root/deklan/

Install ulang:
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)

Done ✅

---

# ❌ Uninstall

systemctl stop gensyn
systemctl disable gensyn
rm -f /etc/systemd/system/gensyn.service
rm -rf /root/rl_swarm
systemctl daemon-reload

---

# 🧩 ENV Full Options

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

---

# 🧨 DANGER ZONE

ENABLE_DANGER_ZONE=1 + DANGER_PASS wajib

Fitur:
- Hapus RL-Swarm  
- Clean Docker  
- Remove Swap  
- Full Clean  
- Reboot VPS  

Only expert ⚠

---

# 📁 Repo Structure

install.sh  
reinstall.sh  
update.sh  
restart.sh  
uninstall.sh  
run_node.sh  

bot.py  
monitor.py  
requirements.txt  
.env.example  

gensyn.service  
bot.service  
monitor.service  
monitor.timer  

README.md  

---

# ✅ Sample Alerts

✅ UP  
Node UP  
CPU 23% • RAM 68% • Disk 50%  
Round: Join X  

🚨 DOWN  
DOWN — Restarting…  

🟢 Recovered  
Recovered  

❌ FAILED  
FAILED — manual fix required  
<logs>  

---

# ❓ FAQ

Q: Perlu GPU?  
A: Tidak  

Q: Aman?  
A: Tidak kirim data ke server lain  

Q: OS support?  
A: Ubuntu 20/22/24, Debian 12  

---

# ❤️ Credits

❤️ Built by Deklan × GPT-5
