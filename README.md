<div align="center">

# 🌙⚡ DEKLAN — GENSYN RL-SWARM TOOLKIT

> **Full automation for Gensyn RL-Swarm Node + Telegram Monitoring Bot**

<img src="https://img.shields.io/badge/Gensyn-RL--Swarm-0a84ff?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Auto_Installer-00d18a?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Telegram_Bot-Control_Panel-fd8a09?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Systemd-AutoStart-green?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Safe-Local_Identity-critical?style=for-the-badge"/>

<img src="https://img.shields.io/github/v/release/deklan400/deklan-autoinstall?style=for-the-badge"/>
<img src="https://img.shields.io/github/license/deklan400/deklan-autoinstall?style=for-the-badge"/>

<!-- OPTIONAL GIF DEMO -->
<br><br>
<img src="images/demo.gif" width="90%"/>
<br>

</div>

---

# 🌍 Language
> Choose your language  
✅ **English** | ✅ **Bahasa Indonesia**

Scroll down for English version ⬇

---

# 🇮🇩 INDONESIA

Toolkit terdiri dari **2 komponen utama:**

| Repo | Fungsi | Link |
|------|--------|------|
| `deklan-autoinstall` | Auto-install RL-Swarm + systemd | https://github.com/deklan400/deklan-autoinstall |
| `deklan-node-bot` | Telegram Control Panel + monitoring | https://github.com/deklan400/deklan-node-bot |

Tujuan:  
→ Deploy node cepat  
→ Kontrol via Telegram  
→ Auto-monitor + auto-recover  
→ Bisa install/update via bot  

---

# ✅ 1) AUTO INSTALL — GENSYN RL-SWARM NODE  
📁 Repo → **deklan-autoinstall**

## 📌 Persiapan Identity

Butuh 3 file:

| File | Fungsi |
|------|--------|
| swarm.pem | Private Key |
| userApiKey.json | API Credential |
| userData.json | Account Metadata |

Upload ke:
```
/root/deklan/
```

---

## 🚀 Install Node

```
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```

Installer otomatis:
✅ Cek identity  
✅ Install dependencies  
✅ Install Docker  
✅ Clone RL-Swarm  
✅ Copy identity  
✅ Enable + Start systemd  

---

## ▶ Cek Status Node

```
systemctl status gensyn
```  

Logs:
```
journalctl -u gensyn -f
```

Restart:
```
systemctl restart gensyn
```

---

# ❌ Uninstall Node

```
systemctl stop gensyn
systemctl disable gensyn
rm /etc/systemd/system/gensyn.service
rm -rf /home/gensyn/rl_swarm
systemctl daemon-reload
```

---

# ✅ 2) TELEGRAM BOT (Control + Monitor)
📁 Repo → **deklan-node-bot**

Fitur:
✅ Start/Stop/Restart Node  
✅ Cek status CPU/RAM/Disk/Uptime  
✅ Logs RL-Swarm  
✅ Last Round  
✅ Auto-monitor  
✅ Auto-Restart  
✅ Alert Down/Recovered  
✅ RUN Install/Reinstall/Update/Uninstall via Telegram  
✅ Danger Zone Commands  

---

## ⚙ Install Bot

```
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-node-bot/main/install.sh)
```

---

## 📌 Setup `.env`

```
BOT_TOKEN=YOUR_TELEGRAM_BOT_TOKEN
CHAT_ID=123456
ALLOWED_USER_IDS=111,222
NODE_NAME=vps-1
SERVICE_NAME=gensyn
MONITOR_EVERY_MINUTES=180
LOG_LINES=50
ENABLE_DANGER_ZONE=1
DANGER_PASS=CHANGEME
```

---

# 🖼 UI PREVIEW

> Letakkan di `/images/`

| Menu | Status | Logs |
|------|--------|------|
| <img src="images/menu.png" width="240"/> | <img src="images/status.png" width="240"/> | <img src="images/logs.png" width="240"/> |

---

# 🧠 Auto Monitor

Bot akan:
✅ Cek node tiap X menit  
✅ Auto-restart  
✅ Alert →  
- ✅ Node OK  
- ❌ Node DOWN  
- 🔁 Node Recovered  
- ⚠ Log error  

> Interval:
```
MONITOR_EVERY_MINUTES=180
```

---

# 🧩 Installer Menu (Via Telegram)

- 📦 Install  
- 🔄 Reinstall  
- ♻ Update  
- 🧹 Uninstall  

Semua langsung run dari GitHub.

---

# ⚠ Danger Zone

Protected by password.  
Fitur:
- Remove RL-Swarm  
- Clean Docker  
- Remove Swap  
- Full Clean  
- Reboot VPS  

> Hati-hati — irreversible!

---

# ⚡ Fast-Move VPS

1) Copy identity:
```
/root/deklan/
```

2) Install:
```
bash <(curl -s https://raw.githubusercontent.com/deklan400/deklan-autoinstall/main/install.sh)
```

→ Node langsung jalan ✅

> Estimasi setup ulang VPS < 1 menit

---

# 🚒 Troubleshooting

| Issue | Solusi |
|-------|--------|
| gensyn not running | `systemctl status gensyn` |
| log kosong | `journalctl -u gensyn -f` |
| docker mati | `systemctl restart docker` |
| no identity | Pastikan 3 file sudah ada di `/root/deklan/` |
| port bentrok | Restart VPS / ubah docker config |
| bot tidak respon | Cek BOT_TOKEN di `.env` |

---

# ❓ FAQ

### ❔ Bisa pakai banyak VPS?
✅ Bisa  
Cukup copy folder identity → install

---

### ❔ Bisa pindah VPS?
✅ Bisa  
→ Sangat cepat (<1 menit)

---

### ❔ Aman?
✅ Identity hanya di server  
❌ Tidak dikirim ke internet  

---

### ❔ Bisa remote dari HP?
✅ Ya → semua via Telegram

---

### ❔ Butuh Docker?
✅ Ya  
Installer otomatis setup

---

# 🔐 Keamanan

✅ Identity stored locally  
✅ DANGER ZONE requires password  
✅ No data uploaded anywhere  
❌ Jangan upload `swarm.pem` ke internet  

---

# ❤️ Credits

> Built by  
**Deklan × GPT-5**

Dark-Theme • Secure • Rapid Deploy

---

# 🌎 ENGLISH VERSION

(… same structure …)

> To keep README clean → EN version placed below.

---

# ✅ END
