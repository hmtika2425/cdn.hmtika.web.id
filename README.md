# 🌐 HMTIKA CDN

CDN (Content Delivery Network) untuk kebutuhan statis HMTIKA, seperti logo, gambar, dan aset lainnya.  
Disediakan beberapa **mirror server** agar lebih aman dan reliabel.

---

## 📊 Status CDN

| Mirror  | URL | Status |
|---------|-----|--------|
| Primary | [cdn.hmtika.web.id](https://cdn.hmtika.web.id/) | ![UptimeRobot status]([https://img.shields.io/uptimerobot/status/801203496?apikey=ur3078768-56c5c98cf1e6f31f95d667e1&label=cdn.hmtika.web.id](https://img.shields.io/uptimerobot/status/801203496?apikey=ur3078768-56c5c98cf1e6f31f95d667e1&label=Primary))
| Vercel  | [cdn-hmtika-web-id.vercel.app](https://cdn-hmtika-web-id.vercel.app/) | ![UptimeRobot status](https://img.shields.io/uptimerobot/status/MONITOR_ID_2) |
| Netlify | [cdn-hmtika2425.netlify.app](https://cdn-hmtika2425.netlify.app/) | ![UptimeRobot status](https://img.shields.io/uptimerobot/status/MONITOR_ID_3) |

> 🔧 Ganti `MONITOR_ID_X` dengan **Monitor ID** dari [UptimeRobot](https://uptimerobot.com).

---

## 🚀 Mirror URLs

- **Mirror 1 (Primary)**  
  👉 `https://cdn.hmtika.web.id/`

- **Mirror 2 (Vercel)**  
  👉 `https://cdn-hmtika-web-id.vercel.app/`

- **Mirror 3 (Netlify)**  
  👉 `https://cdn-hmtika2425.netlify.app/`

---

## 💡 Contoh Penggunaan

### 🔹 Basic (langsung URL)
```txt
https://cdn.hmtika.web.id/images/logo-hmtika/main-logo-HMTIKA-1.png
```

## 💡 Example Failover

```ts
const CDN_PRIMARY = "https://cdn.hmtika.web.id";
const CDN_BACKUP = "https://cdn-hmtika2425.netlify.app";

const MAIN_LOGO_HMTIKA_PATH = "/images/logo-hmtika/main-logo-HMTIKA-1.png";

export default function LogoHMTIKA() {

    const [mainLogoHmtika, setmainLogoHmtika] =useState<string>();

    useEffect(() => {
        setmainLogoHmtika(`${CDN_PRIMARY}${MAIN_LOGO_HMTIKA_PATH}`);
    }, []);

    const handleErrorMminLogoHmtika = (path: string) => {
        setmainLogoHmtika(`${CDN_BACKUP}${path}`);
    };


    return (
        <img
            src={mainLogoHmtika}
            onError={() => handleErrorMminLogoHmtika(MAIN_LOGO_HMTIKA_PATH)}
        />
    );
}
