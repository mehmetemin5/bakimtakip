# Bakım Takip – GitHub Pages (github.io)

Arayüz burada (github.io), veriler **Google Sheets**'te tutulur. GAS sadece API olarak kullanılır.

## Kurulum

### 1. Google Apps Script (API)

- Projeyi **Google Sheet**'ten açın (Uzantılar → Apps Script).
- **Code.gs** içeriğini bu repodaki **Code.gs** ile değiştirin (API sürümü: doGet JSONP, doPost form).
- **setSpreadsheetId** fonksiyonunu Script editöründe bir kez çalıştırın.
- **Script özellikleri:** `TECHNICIAN_PASSWORD` = bakım paneli şifresi.
- **Dağıtım** → **Yeni dağıtım** → **Web uygulaması**
  - Kim çalıştırır: **Ben**
  - Erişim: **Herkes**
  - Dağıt → çıkan **URL'yi** kopyalayın (örn. `https://script.google.com/macros/s/.../exec`).

### 2. config.js

- **config.js** dosyasında `GAS_URL` değişkenine, yukarıda kopyaladığınız GAS Web App URL'sini yapıştırın.

```javascript
var GAS_URL = 'https://script.google.com/macros/s/SIZIN_ID/exec';
```

### 3. GitHub Pages

- Bu klasördeki dosyaları (`config.js`, `index.html`, `dashboard.html`) **bakimtakip** reposuna commit/push edin.
- Repo ayarlarında **Pages** → Source: **main** (veya master) → **/ (root)** veya bu klasörü root yapın.
- Site adresi: `https://kullaniciadi.github.io/bakimtakip/` (veya repo adına göre).

## Dosyalar

- **index.html** – Raporlama + Bakım paneli (şifre ile).
- **dashboard.html** – TV paneli (30 saniyede bir yenilenir).
- **config.js** – GAS Web App URL (burayı mutlaka doldurun).

## Nasıl çalışır

- **Veri okuma:** Tarayıcı GAS URL'ye JSONP isteği atar (`?action=getFaults&callback=...`), cevap Sheet'ten okunur.
- **Veri yazma:** Form POST ile GAS'e gider, GAS Sheet'e yazar; cevap iframe içinde `postMessage` ile sayfaya iletilir.
- Arızalar ve arşiv **Google Sheets**'te (Aktif_Arızalar, Arıza_Arşivi) kalır.
