# CDN HMTIKA

---

## 🚀 USAGE

### 📦 Mirror 1
`https://cdn.hmtika.web.id/`

### 📦 Mirror 2 (Vercel)
`https://cdn-hmtika-web-id.vercel.app/`

### 📦 Mirror 3 (Netlify)
`https://cdn-hmtika2425.netlify.app/`

---

## 💡 Example Basic
`https://cdn.hmtika.web.id/images/logo-hmtika/main-logo-HMTIKA-1.png`

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
