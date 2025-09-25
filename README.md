# 🌐 HMTIKA CDN

CDN (Content Delivery Network) untuk kebutuhan statis HMTIKA, seperti logo, gambar, dan aset lainnya.  
Disediakan beberapa **mirror server** agar lebih aman dan reliabel.

---

## 📊 Status CDN

| Mirror  | URL | Status |
|---------|-----|--------|
| Primary | [cdn.hmtika.web.id](https://cdn.hmtika.web.id/) | ![UptimeRobot status](https://img.shields.io/uptimerobot/status/m801203496-9a66cb47d5749fea9c3c0b70) |
| Backup  | [cdn-2.hmtika.web.id](https://cdn-2.hmtika.web.id) | ![UptimeRobot status](https://img.shields.io/uptimerobot/status/m801446466-27d347e7ab0e984e10197dc1) |
| Vercel  | [cdn-hmtika-web-id.vercel.app](https://cdn-hmtika-web-id.vercel.app/) | ![UptimeRobot status](https://img.shields.io/uptimerobot/status/m801203600-eb846403205e1512fbfe0763) |
| Netlify | [cdn-hmtika2425.netlify.app](https://cdn-hmtika2425.netlify.app/) | ![UptimeRobot status](https://img.shields.io/uptimerobot/status/m801203496-9a66cb47d5749fea9c3c0b70) |



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

```

🛠️ Catatan

Gunakan mirror utama (cdn.hmtika.web.id) sebisa mungkin.

Jika mirror utama tidak bisa diakses, gunakan fallback (Netlify / Vercel).
