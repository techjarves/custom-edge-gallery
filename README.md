# Mobile Server

Welcome to **Mobile Server**! This project turns any modern Android phone into a completely free, 100% private, OpenAI-compatible local AI server.

> **Note:** This project was built by forking the incredible [Google AI Edge Gallery](https://github.com/google-ai-edge/gallery). We took their powerful on-device inference engine and extended it with a built-in Ktor server and tunneling capabilities!

**🎥 Watch the Setup & Demo Video:** [https://youtu.be/9Dh3kKWFFjg](https://youtu.be/43oZPoQiqoY)

[![Turn Your Android Into Private AI Server](https://img.youtube.com/vi/43oZPoQiqoY/maxresdefault.jpg)](https://youtu.be/43oZPoQiqoY)


---

## 🚀 What Does This Do?

With this app, you can run Large Language Models (like Google's Gemma 4) directly on your phone's hardware, and securely expose that model to the internet using **Ngrok** or **Cloudflare Tunnels**. 

Because the server perfectly mimics the standard OpenAI API structure (`/v1/models`, `/v1/chat/completions`), you can seamlessly integrate it into existing AI tools.

**Use Cases:**
1. **Free AI Coding Assistant:** Point the [Continue.dev](https://continue.dev) VS Code extension to your phone's Cloudflare URL to get $0/mo local code autocomplete and chat.
2. **Private Smart Home Brain:** Connect it to Home Assistant for a completely private, offline-capable smart home AI.
3. **The "EdgeNode" Web App:** Use our provided HTML/JS frontend to chat with your phone from any web browser in the world.

---

## ✨ Features

- **OpenAI-Compatible API:** Zero-configuration drop-in replacement for OpenAI endpoints.
- **Built-in Tunneling:** One-tap toggle to instantly expose your server to the internet via Ngrok or Cloudflare Tunnels (bypasses NATs and firewalls).
- **Foreground Service:** The server and the LLM remain running in the background even when your screen is off.
- **100% Private:** Your prompts and data never leave the phone (except via your own encrypted tunnel).

---

## 📦 Installation

You don't need to build this from source! 

👉 **[Download arm64-v8a](https://github.com/techjarves/mobile-server/releases/download/first/app-arm64-v8a-release.apk)** — for most modern phones

👉 **[Download armeabi-v7a](https://github.com/techjarves/mobile-server/releases/download/first/app-armeabi-v7a-release.apk)** — for older 32-bit devices

👉 **[Download universal](https://github.com/techjarves/mobile-server/releases/download/first/app-universal-release.apk)** — fallback for all devices

### Pick the right APK for your device

We provide **split ABI APKs** to reduce install size and fix parsing issues on certain devices. Choose the APK that matches your phone's CPU:

| APK | Size | Device Type |
|-----|------|-------------|
| [app-arm64-v8a-release.apk](https://github.com/techjarves/mobile-server/releases/download/first/app-arm64-v8a-release.apk) | ~63 MB | **Most modern phones** (Pixel, Samsung, Xiaomi, OnePlus, etc.) |
| [app-armeabi-v7a-release.apk](https://github.com/techjarves/mobile-server/releases/download/first/app-armeabi-v7a-release.apk) | ~35 MB | Older 32-bit ARM devices |
| [app-universal-release.apk](https://github.com/techjarves/mobile-server/releases/download/first/app-universal-release.apk) | ~73 MB | Fallback — works on all devices |

> 💡 **Not sure which one?** Download `app-arm64-v8a-release.apk` — it works on the vast majority of Android phones released after 2016.

Simply download the APK, install it on your Android device, download a model from the list, and turn the server on.

---

## 💻 Web App Demo

Want to test it out without writing any code? We have hosted a sleek, glassmorphism-styled web interface for you!

🌐 **[Try the Live Web App Demo](https://mobile-server-app.web.app)**

Just open the link, paste in your phone's Cloudflare or Ngrok tunnel URL, and start chatting instantly! (The source code for this web app is also available in the `/webapp-demo` folder).

---

## 🛠️ Development

If you want to build the project from source:

### Prerequisites
- Android SDK 35
- JDK 17+

### Build
```bash
cd Android/src
./gradlew :app:assembleRelease
```

The split APKs will be generated in:
```
Android/src/app/build/outputs/apk/release/
```

| Output | Description |
|--------|-------------|
| `app-arm64-v8a-release.apk` | Modern 64-bit ARM phones |
| `app-armeabi-v7a-release.apk` | Older 32-bit ARM devices |
| `app-universal-release.apk` | All ABIs in one APK (fallback) |

### Android Studio
1. Clone this repository.
2. Open the `/Android/src` folder in Android Studio.
3. Build the `Debug` or `Release` variant.

> **Note:** We have explicitly configured `android:extractNativeLibs="true"` so that the tunneling binaries extract properly in Release builds.

## 📄 License

Licensed under the Apache License, Version 2.0. See the [LICENSE](LICENSE) file for details.
