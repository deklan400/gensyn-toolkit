# ⚡ Gensyn RL-Swarm Node + Telegram Control Bot
### ✅ One-Command Install • Systemd • Auto-Heal • Telegram Panel

<p align="center">
  Minimal • Cepat • Stabil • CPU-Only
</p>

---

## 📌 Overview
Project ini menyediakan:
1) **Auto-Installer RL-Swarm CPU Node**
2) **Telegram Control Bot + Auto Monitor + Auto Reinstall**

Sehingga VPS dapat menjalankan node Gensyn RL-Swarm **tanpa perlu SSH lagi**.

---

# ✅ 1) Install RL-Swarm Node

> Jalankan:

```bash
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```

### 📌 Fitur
✔ Install dependencies  
✔ Install Docker  
✔ Clone RL-Swarm repo  
✔ NEW USER → Auto buka WebUI untuk login  
✔ EXISTING USER → Langsung jalan  
✔ Auto create identity  
✔ Auto-systemd  
✔ Auto-restart  
✔ Reinstall / Update / Uninstall  

### 📂 Struktur Identity
File credential disimpan di:

```
/root/deklan/
│── swarm.pem
│── userApiKey.json
└── userData.json
```

Symlink otomatis dibuat ke:
```
/root/rl-swarm/user/keys → /root/deklan
```

> NEW USER → file identity otomatis dibuat setelah login UI  
> EXISTING USER → pastikan file tersimpan di folder di atas  

---

# ✅ 2) Install Telegram Control Bot

> Setelah node ter-install, jalankan:

```bash
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-node-bot/main/install.sh)
```

Installer akan:
✅ Clone repo  
✅ Buat `.env` (input BOT_TOKEN, CHAT_ID)  
✅ Setup systemd bot service  
✅ Setup auto-monitor timer  
✅ Start bot  

---

# ✅ Cara Pakai Telegram Bot

Ketik:
```
/start
```

Akan muncul menu kendali node:

✅ Status CPU / RAM / Disk / Uptime  
✅ Last Round  
✅ Logs realtime  
✅ Start / Stop / Restart  
✅ Swap Manager  
✅ Instalasi remote  
✅ Danger Zone (opsional + password)

---

## ✅ Commands
| Command | Fungsi |
|---------|--------|
| /start  | Open menu |
| /status | Resource + uptime |
| /logs   | Logs |
| /round  | Last round / progress |
| /restart | Restart node |
| /help   | Command info |

---

# ✅ Menu Utama

📊 Status  
🟢 Start  
🔴 Stop  
🔁 Restart  
📜 Logs  
ℹ Last Round  
💾 Swap Manager (16G/32G/64G/Custom)  
🧩 Installer  
⚠ Danger Zone (opsional)  

---

# ✅ Installer Menu

Dapat dilakukan langsung via Telegram:

✔ Install  
✔ Update  
✔ Reinstall  
✔ Uninstall  

Flow:
1) Klik menu
2) Bot konfirmasi
3) Balas: `YES`
4) Bot mengeksekusi

---

# ✅ Auto Monitor (Self-Heal)

Service monitor berjalan otomatis setiap beberapa jam:
- Cek apakah node UP
- Jika DOWN → restart
- Jika tetap gagal → reinstall
- Kalau gagal juga → kirim log via Telegram

Log detail disertakan agar mudah debug.

Status file:
```
/tmp/.node_status.json
```

---

# ✅ Swap Manager

Preset:
- 16 GB
- 32 GB
- 64 GB
- Custom (input angka)

Swap akan dibuat ulang otomatis:
- Update fstab
- swapon

---

# ✅ Paths Penting

| Resource | Path |
|----------|------|
| Identity | `/root/deklan/` |
| RL-Swarm | `/root/rl-swarm/` |
| Service | `/etc/systemd/system/gensyn.service` |
| Bot dir | `/opt/deklan-node-bot` |
| Bot env | `/opt/deklan-node-bot/.env` |

---

# 🔄 Systemd

## Node
```
systemctl status gensyn
systemctl restart gensyn
journalctl -u gensyn -f
```

## Bot
```
systemctl status bot
journalctl -u bot -f
```

## Monitor
```
systemctl status monitor.timer
systemctl start monitor.service
```

---

# ❌ Uninstall

## Node
```
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/uninstall.sh)
```

Identity tetap aman.

## Bot
```
systemctl stop bot monitor.service monitor.timer
systemctl disable bot monitor.service monitor.timer
rm -f /etc/systemd/system/bot.service
rm -f /etc/systemd/system/monitor.*
rm -rf /opt/deklan-node-bot
systemctl daemon-reload
```

---

# ✅ Backup Identity

> WAJIB DISIMPAN! (jangan dishare!)

```
/root/deklan/swarm.pem
/root/deklan/userApiKey.json
/root/deklan/userData.json
```

---

# ❗ Notes

✅ CPU-only → ringan  
✅ Bisa multi-VPS  
✅ Bisa migrasi VPS cukup pindahkan folder `/root/deklan/`  
✅ Bot & Node terpisah → modular  

---

# ✅ Next
- Multi-Node Visual Dashboard
- Multi-project helper
- Remote deploy
- Auto update bot

---

# ❤️ Credits
Built with ❤️ by **Deklan × GPT-5**
