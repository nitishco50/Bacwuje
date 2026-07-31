# MediaGrabber - Social Media Video/Audio Downloader Python Backend

Yeh **MediaGrabber** Android app ka official Python FastAPI backend hai. Iss backend ke dwara aap **YouTube, Instagram, TikTok, Snapchat, aur Facebook** ke video aur audio links ko process aur download kar sakte ho.

---

## 🚀 Features
- ⚡ **FastAPI & yt-dlp Powered**: Express-speed media metadata extraction.
- 🎬 **Multi-Format Support**: Video (1080p, 720p, 480p) & Audio (320kbps MP3, M4A).
- 📦 **Batch Extraction**: Multiple social media URLs ek sath parse karne ka capability.
- ⚙️ **Admin Control Panel Endpoints**: Live stats, platform toggles, rate limits, status metrics.
- 🌐 **CORS Ready**: Android app se direct REST calls easily allow hoti hain.

---

## 🛠️ Render.com Par Free Host Kaise Kare (Step-by-Step Setup Guide)

### **Method 1: GitHub Se Direct Deploy (Recommended)**

1. **GitHub Par Push Kare**:
   - Apne repository me yeh `python` folder push kare.

2. **Render Account Banaye**:
   - Open kare [https://render.com](https://render.com) aur Google/GitHub se Signup/Login kare.

3. **New Web Service Create Kare**:
   - Render Dashboard par **New +** button dabaye aur **Web Service** select kare.
   - Apne GitHub repository ko connect kare.

4. **Settings Fill Kare**:
   - **Name**: `mediagrabber-backend` (Ya koi bhi manchaha naam)
   - **Root Directory**: `python`
   - **Environment**: `Python 3`
   - **Region**: `Singapore` (Asia ke liye best latency)
   - **Branch**: `main`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `uvicorn main:app --host 0.0.0.0 --port $PORT`
   - **Instance Type**: `Free`

5. **Deploy Button Par Click Kare**:
   - Render automatically build process start karega aur 2-3 minute me aapko ek Live URL milega:
     `https://mediagrabber-backend.onrender.com`

6. **Android App Me Backend URL Set Kare**:
   - MediaGrabber Android App open kare -> Top right **Admin / Settings (⚙️)** icon par click kare.
   - Apni Render URL (`https://mediagrabber-backend.onrender.com`) paste kare aur **"Test Connection"** dabaye!

---

## 💻 Local Machine Par Testing / Development Setup

If you want to run the server on your computer locally:

```bash
# 1. Python directory me jaye
cd python

# 2. Virtual environment create kare
python -m venv venv

# 3. Virtual environment activate kare (Windows)
venv\Scripts\activate
# Linux / macOS ke liye:
# source venv/bin/activate

# 4. Dependencies install kare
pip install -r requirements.txt

# 5. FastApi server start kare
python main.py
```

Server live ho jayega: `http://localhost:8000`
Swagger API Documentation view kare: `http://localhost:8000/docs`

---

## 📡 API Endpoints Overview

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | Health check, status, uptime |
| `POST` | `/api/extract` | Extract single media URL details & download links |
| `POST` | `/api/batch-extract` | Extract list of URLs in one request |
| `GET` | `/admin/stats` | View server statistics, requests, bandwidth |
| `POST` | `/admin/config` | Update platform access, maintenance mode, limits |

---

## 💡 Troubleshooting & Notes
- **yt-dlp Update**: Social media sites layout change karte rahte hain. Agarr koi specific site fail ho, toh `requirements.txt` me `yt-dlp` update karke commit push kar de. Render automatically re-deploy kar dega.
- **Render Free Tier Sleep**: Render ka free tier 15 minutes inactivity ke baad spin-down ho jata hai. First request me 15-20 seconds lag sakte hain warmup hone me. App me inbuilt fallback connection retry mechanisms add ki gayi hain!
