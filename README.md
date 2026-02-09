# Otomotiv Bakım Yönetim PWA

Google Apps Script (GAS) ile geliştirilmiş, Google Sheets tabanlı Otomotiv Bakım Yönetim Progressive Web App (PWA).

## Bileşenler

1. **Kullanıcı Arayüzü (Raporlama)** – Arıza raporu oluşturma, LocalStorage ile kalıcı giriş
2. **Bakım Paneli (Technician)** – Personel atama, iş başlatma, arıza tamamlama
3. **TV Dashboard** – 7/24 ekran, 30 saniyede bir veri yenileme, önceliğe göre renkler

## Kurulum (Google Apps Script)

1. [Google Drive](https://drive.google.com) → **Yeni** → **Google Apps Script**
2. Varsayılan `Code.gs` içeriğini bu projedeki `Code.gs` ile değiştirin
3. **Dosya** → **Yeni** → **HTML dosyası** ile `index` ve `Dashboard` adında iki HTML dosyası oluşturun; içeriklerini bu projedeki `index.html` ve `Dashboard.html` ile değiştirin
4. Script’i bir **Google Sheets** ile ilişkilendirin: **Dosya** → **Yeni** → **Spreadsheet** oluşturun veya mevcut bir Sheet’i kullanın. Script editöründe **Proje ayarları** veya Sheet’te **Uzantılar** → **Apps Script** ile aynı projeyi açın
5. İlk çalıştırmada `Code.gs` içindeki `getActiveSheet()` ve `getArchiveSheet()` fonksiyonları **Aktif_Arızalar** ve **Arıza_Arşivi** sayfalarını otomatik oluşturur
6. **Dağıtım** → **Yeni dağıtım** → **Web uygulaması**
   - Açıklama: “Bakım Yönetim”
   - **Kullanıcı olarak**: Kendiniz
   - **Erişim**: Herkes (veya kurum içi)
   - **Dağıt** ile URL’i alın

## URL’ler

- Ana uygulama (Raporlama + Bakım Paneli): `[Web App URL]`
- TV Dashboard: `[Web App URL]?page=dashboard`
- PWA manifest (Ana ekrana ekleme): `[Web App URL]?page=manifest`

## Teknik Özellikler

- **Backend:** Google Sheets (Aktif_Arızalar, Arıza_Arşivi), UTC+3 zaman damgaları
- **Fonksiyonlar:** `saveReport`, `assignStaff`, `startJob`, `completeJob`, `getActiveFaults`
- **Frontend:** Bootstrap 5, responsive, dark theme
- **PWA:** Manifest ile “Ana ekrana ekle” desteği
- **TV Dashboard:** 30 saniyede bir sayfa yenilenmeden veri güncelleme; Çok Acil (yanıp sönen kırmızı), Acil (sarı), Normal (mavi)

## Lisans

Bu proje örnek kullanım içindir.
