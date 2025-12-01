# Kurumsal Mesai Takip Sistemi

Modern, güvenli ve kullanıcı dostu bir mesai ve izin takip uygulaması. React, Tailwind CSS ve Microsoft Entra ID (Azure AD) teknolojileri ile geliştirilmiştir. PWA (Progressive Web App) özelliği sayesinde hem masaüstü hem de mobil cihazlarda yerel uygulama gibi çalışır.

## 🚀 Özellikler

*   **Rol Tabanlı Yetkilendirme:**
    *   **Personel:** Mesai girişi yapabilir, kendi geçmişini görüntüleyebilir.
    *   **Takım Lideri:** Ekibindeki personellerin mesai taleplerini onaylayabilir veya reddedebilir.
    *   **Yönetici (Admin):** Tüm veritabanını görüntüleyebilir, CSV raporu indirebilir, kullanıcıları yönetebilir.
*   **Microsoft Entra ID Entegrasyonu:** Kurumsal e-posta hesapları ile güvenli SSO (Single Sign-On) girişi.
*   **Otomatik Hesaplamalar:**
    *   Mesai saati hesaplama.
    *   Hafta sonu (1.5x) ve Resmi Tatil (2.0x) çarpanlarının otomatik tespiti.
    *   Çakışma kontrolü.
*   **Modern Arayüz:** Tailwind CSS ile tasarlanmış, duyarlı (responsive) ve şık tasarım.
*   **PWA Desteği:** İnternet kesintilerinde çalışabilme ve cihazlara yüklenebilme özelliği.

## 🛠 Teknoloji Yığını

*   **Frontend:** React 18+ (TypeScript)
*   **Styling:** Tailwind CSS
*   **Authentication:** Microsoft Authentication Library (MSAL) for React
*   **Icons:** Lucide React
*   **Build Tool:** Vite (veya benzeri modern bundler)

## 📦 Kurulum ve Çalıştırma

Bu projeyi yerel ortamınızda çalıştırmak için aşağıdaki adımları izleyin:

### 1. Projeyi Klonlayın

```bash
git clone https://github.com/kullaniciadi/mesai-takip-sistemi.git
cd mesai-takip-sistemi
```

### 2. Bağımlılıkları Yükleyin

```bash
npm install
```

### 3. Azure AD Yapılandırması

Uygulamanın çalışması için Azure Portal üzerinde bir **App Registration** oluşturmanız gerekir:

1.  [Azure Portal](https://portal.azure.com)'a gidin.
2.  **Microsoft Entra ID** > **App registrations** > **New registration** yolunu izleyin.
3.  **Name:** "Mesai Takip" yazın.
4.  **Supported account types:** "Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant)" seçeneğini işaretleyin.
5.  **Redirect URI:** "Single-page application (SPA)" seçin ve `http://localhost:5173` (veya kullandığınız port) adresini ekleyin.
6.  Oluşturulan uygulamanın **Application (client) ID** değerini kopyalayın.
7.  Projedeki `index.tsx` dosyasını açın ve `msalConfig` içerisindeki `clientId` alanını güncelleyin:

```javascript
const msalConfig = {
    auth: {
        clientId: "BURAYA_AZURE_CLIENT_ID_YAZIN",
        // ...
    }
};
```

### 4. Uygulamayı Başlatın

```bash
npm run dev
```

Tarayıcınızda `http://localhost:5173` adresine gidin.

## 📱 PWA Olarak Yükleme

Uygulama tarayıcıda açıldığında adres çubuğunun sağ tarafında beliren "Yükle" ikonuna tıklayarak bilgisayarınıza veya telefonunuza uygulama olarak indirebilirsiniz.

## 🧪 Demo Modu

Azure AD kurulumu yapmadan uygulamayı test etmek isterseniz, giriş ekranındaki **"Veya Demo Seçin"** bölümünü kullanabilirsiniz.

*   **Personel:** Standart veri giriş ekranlarını görür.
*   **Takım Lideri:** Onay mekanizmasını test eder.
*   **Admin:** Raporlama ve silme yetkilerini test eder.

## 📝 Lisans

Bu proje MIT lisansı altında lisanslanmıştır.