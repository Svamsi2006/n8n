# WAHA + n8n Setup Guide

Step-by-step guide to install **WAHA** (WhatsApp HTTP API) with Docker and integrate with **n8n**.

## Prerequisites

- Docker installed on your system
- n8n installed and running

## Step 1: Install WAHA with Docker

### 1.1 Pull WAHA Image
```bash
docker pull devlikeapro/waha
```

### 1.2 Create WAHA Directory
```bash
cd Downloads
mkdir wahaa
cd wahaa
```

### 1.3 Initialize WAHA (.env file)
```bash
docker run --rm -v "${pwd}:/app/env" devlikeapro/waha init-waha /app/env
```
This creates a `.env` file with credentials.

### 1.4 Start WAHA Server
```bash
docker run -it --env-file "$(pwd)/.env" -v "$(pwd)/sessions:/app/.sessions" --rm -p 3000:3000 --name waha devlikeapro/waha
```

**WAHA is now live at:** `http://localhost:3000`

### 1.5 Configure API Keys
1. Open `http://localhost:3000/dashboard`
2. Set your API keys
3. Save configuration

## Step 2: Install WAHA n8n Node

### Option A: n8n UI (Recommended)
1. Go to your n8n → **Settings** → **Community nodes**
2. Install: `@devlikeapro/n8n-nodes-waha`

### Option B: Command Line
```bash
npm i @devlikeapro/n8n-nodes-waha
```

## Step 3: Verify Installation

- ✅ WAHA Dashboard: `http://localhost:3000/dashboard`
- ✅ n8n WAHA Node: Available in n8n node palette

## Troubleshooting

**Port 3000 already in use?**
```bash
# Stop existing container
docker stop waha

# Or use different port
docker run -it --env-file "$(pwd)/.env" -v "$(pwd)/sessions:/app/.sessions" --rm -p 3001:3000 --name waha devlikeapro/waha
```
Access at `http://localhost:3001`

**Sessions not saving?**
- Check if `sessions` folder has write permissions
- Verify Docker volume mount: `-v "$(pwd)/sessions:/app/.sessions"`

## Reference
[Official WAHA Quick Start](https://waha.devlike.pro/docs/overview/quick-start/)

---

**⭐ Star this repo if it helped you!**
