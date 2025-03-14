# 🚀 GoDeploy — Effortless SPA Packaging

> **Simple, fast, and flexible Docker + Nginx containerization for SPAs.**  
> **No full-stack frameworks. No infrastructure headaches. Just ship.**

---

## 🤯 Why GoDeploy?

If you're building a **Single Page Application (SPA)**, chances are you've hit one of these:

- **"I don't want to use Next, Nuxt or Remix just to deploy a React/Vue app."**
- **"I hate dealing with infrastructure"**
- **"I just want to ship my app fast."**

👉 **GoDeploy is for you.**  
Package **any SPA** into a **production-ready Docker + Nginx container** in **minutes**, with **zero server config** and **no framework lock-in**.

---

## ✨ Features

### ✅ 1. Simplified SPA Containerization

No more fiddling with Dockerfiles or Nginx configs. Go from built assets to container-ready in seconds.

```bash
godeploy package
```

➡️ **Generates:**

- Dockerfile
- Nginx config
- Your app, ready to ship

---

### ✅ 2. Zero Infrastructure Headaches

Test and containerize without writing any server config or understanding container orchestration.

```bash
godeploy serve
```

➡️ Spin up your SPA **locally in Docker**, instantly previewing your production setup.

---

### ✅ 3. Blazing Fast, No Overhead — Powered by Nginx

Why force a full-stack framework to serve a static app when **Nginx is made for this**?

GoDeploy serves your SPA with **raw Nginx performance**, optimized for static delivery:

- **Optimized cache headers** (for hashed filenames like `app.234sd.js`).
- **Ultra-fast static file serving** — **50,000+ requests/sec** on commodity hardware.
- **HTML5 history mode routing** for clean URLs.

⚡ **Faster than Next.js, Nuxt, or Remix** when you just need an SPA — without SSR's bloat, without added runtime overhead.

> **Bonus**: Ready for CDNs (Cloudflare, Fastly) — plug-and-play global caching, no SSR "staleness" to manage.

---

### ✅ 4. Use Any Frontend Stack

React, Vue, Angular, Svelte — if it builds to static files, it works. No full-stack lock-in, **just containerize your frontend.**

```bash
npm run build  # or any build tool
godeploy init
```

---

### ✅ 5. Multi-SPA Support, Easy Routing

Host **multiple SPAs under one domain**, each on its own route, configured via `spa-config.json`.

```json
{
  "default_app": "auth",
  "apps": [
    { "name": "auth", "source_dir": "dist" },
    { "name": "dashboard", "source_dir": "dashboard-dist" }
  ]
}
```

➡️ Auto-routes to `/`, `/auth/`, `/dashboard/`.

---

### ✅ 6. Quick to Learn, Fast to Ship

Forget complex docs. GoDeploy is a **3-command workflow**:

```bash
godeploy init     # Scaffold config
godeploy serve    # Test locally
godeploy package  # Containerize for production
```

---

## 🚧 **Coming Soon: `godeploy deploy` — Instant SPA Hosting (Join Alpha)**

> Imagine running this:

```bash
godeploy deploy
```

➡️ And getting this:

```
🎉 Your app is live at: https://my-app.godeploy.app
```

- No AWS. No Cloudflare. No pipelines.
- **Just run the command and your app is online — optimized, secured, and served from a global CDN.**

💥 **Be first in line** for **alpha access**:  
👉 [**Sign up here**](https://godeploy.app/alpha) (coming soon)

**⭐ Star this repo** to support the project and follow updates!  
[https://github.com/matsilva/godeploy](https://github.com/matsilva/godeploy)

---

## 🚀 Quick Start

### 1. Install GoDeploy

```bash
go install github.com/audetic/godeploy/cmd/godeploy@latest
```

Or build from source:

```bash
git clone https://github.com/audetic/godeploy.git
cd godeploy && go build -o godeploy ./cmd/godeploy
```

---

### 2. Build Your SPA

```bash
npm run build  # React, Vue, Angular, etc.
```

---

### 3. Initialize GoDeploy

```bash
godeploy init
```

➡️ Edit `spa-config.json` to point to your build directory (e.g., `dist` or `build`).

---

### 4. Test Locally in Docker

```bash
godeploy serve
```

➡️ Visit: [http://localhost:8082](http://localhost:8082)

---

### 5. Generate Container-Ready Artifacts

```bash
godeploy package
```

➡️ Creates `/deploy` with:

- Dockerfile
- Nginx config
- SPA files

---

### 6. Deploy to Production

```bash
cd deploy
docker build -t my-app .
docker run -p 80:80 my-app
```

Or push to your container registry and deploy to your cloud provider.

---

## 🔧 Full CLI Reference

| Command                              | Description                                             |
| ------------------------------------ | ------------------------------------------------------- |
| `godeploy init`                      | Create default `spa-config.json`                        |
| `godeploy init --force`              | Overwrite existing config                               |
| `godeploy serve`                     | Serve SPA locally via Docker (port 8082)                |
| `godeploy serve --port <port>`       | Use custom port                                         |
| `godeploy serve --image-name <name>` | Use custom Docker image name                            |
| `godeploy package`                   | Generate containerized Docker + Nginx setup             |
| `godeploy package --output <dir>`    | Output to custom directory (default: `deploy/`)         |
| `godeploy --config <file>`           | Use custom config file (default: `spa-config.json`)     |
| 🚧 `godeploy deploy`                 | **Coming soon** — One-command SaaS deploy (join alpha!) |

---

## ✅ Requirements

- Go 1.16+
- Docker (for `serve` + `package`)

---

## 📖 Learn More

- [Advanced Multi-SPA & Custom Config](docs/advanced-configuration.md)

---

## 📝 License

MIT
