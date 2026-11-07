# 🛒 MultiShop – Mikroservis Tabanlı E-Ticaret Uygulaması

MultiShop, ASP.NET Core 6.0 ile geliştirdiğim, mikroservis mimarisi üzerine kurulu bir e-ticaret projesidir. Amacım; tek parça (monolitik) bir uygulama yerine, her biri kendi işini yapan ve birbirinden bağımsız çalışabilen servislerden oluşan gerçekçi bir sistem kurmak ve bu süreçte modern backend pratiklerini uçtan uca uygulamaktı.

Projede kimlik doğrulama, API Gateway, mesaj kuyruğu, önbellekleme, gerçek zamanlı bildirimler ve container yönetimi gibi gerçek hayatta karşılaşılan birçok konu bir arada yer alıyor.

> 📌 Bu proje, Murat Yücedağ'ın eğitmenliğindeki **"ASP.NET Core MultiShop Mikroservis E-Ticaret Kursu"** sürecinde geliştirilmiştir.

---

## 📑 İçindekiler

- [Proje Hakkında](#-proje-hakkında)
- [Uygulama Bölümleri](#-uygulama-bölümleri)
- [Mimari Yaklaşım](#-mimari-yaklaşım)
- [Kullanılan Teknolojiler](#-kullanılan-teknolojiler)
- [Kurulum](#-kurulum)
- [Ekran Görüntüleri](#-ekran-görüntüleri)
- [Neler Öğrendim](#-neler-öğrendim)
- [İletişim](#-iletişim)

---

## 💡 Proje Hakkında

MultiShop'ta alışveriş akışının tamamı mikroservisler üzerinden yürüyor: ürünler, sepet, sipariş, indirim, yorum, mesajlaşma ve kullanıcı yönetimi ayrı servisler olarak tasarlandı. Servisler dışarıya **Ocelot API Gateway** üzerinden açılıyor, yetkilendirme ise **IdentityServer** ile yönetiliyor.

Her servisin ihtiyacına göre farklı bir veritabanı tercih ettim (MongoDB, MSSQL, PostgreSQL). Sepet gibi hızlı erişim gereken veriler ise Redis üzerinde tutuluyor.

---

## 🧩 Uygulama Bölümleri

### 🖥️ Kullanıcı Arayüzü (Vitrin)
Ziyaretçilerin ve müşterilerin kullandığı ana alışveriş bölümü:
- Ürün listeleme ve kategoriye göre filtreleme
- Ürün detay sayfaları
- Sepete ekleme ve ödeme adımları
- Kampanya ve indirim alanları
- Döviz kuru ve hava durumu entegrasyonları

### 🛠️ Admin Paneli
Yönetici rolündeki kullanıcıların siteyi yönettiği bölüm:
- Ürün, kategori, marka, kampanya ve slider için tam CRUD işlemleri
- Kullanıcı yönetimi
- SignalR ile canlı güncellenen istatistikler

### 👤 Kullanıcı Paneli
Kayıtlı müşterilerin kendi hesaplarını yönettiği alan:
- Profil bilgilerini görüntüleme ve düzenleme
- Geçmiş siparişleri takip etme
- Gelen ve giden mesajları yönetme

---

## 🏗️ Mimari Yaklaşım

- **Mikroservis mimarisi:** Servisler bağımsız geliştirilir, dağıtılır ve ölçeklenir.
- **Onion Architecture:** Katmanlar arası bağımlılıklar kontrol altında tutulur, kod modüler kalır.
- **CQRS + MediatR:** Okuma ve yazma işlemleri birbirinden ayrılır.
- **Repository Pattern:** Veri erişim katmanı soyutlanır, tekrar kullanılabilirlik artar.
- **Event-driven iletişim:** Servisler arası asenkron haberleşme RabbitMQ ile sağlanır.
- **API Gateway:** Tüm istekler Ocelot üzerinden merkezi olarak yönlendirilir.

---

## 🧰 Kullanılan Teknolojiler

| Kategori | Teknolojiler |
|---|---|
| **Backend** | ASP.NET Core 6.0 (MVC & Web API), C# |
| **Mimari & Desenler** | Microservices, Onion Architecture, CQRS, MediatR, Repository Pattern |
| **API Gateway** | Ocelot |
| **Kimlik & Güvenlik** | IdentityServer, JWT, OAuth 2.0 |
| **Veritabanları** | MongoDB, MSSQL, PostgreSQL |
| **Önbellek** | Redis (sepet ve cache yönetimi) |
| **Mesajlaşma** | RabbitMQ |
| **Gerçek Zamanlı İletişim** | SignalR |
| **Nesne Eşleme** | DTO, AutoMapper |
| **Container** | Docker |
| **Depolama** | Google Cloud Storage (ürün görselleri) |
| **API Test & Dokümantasyon** | Swagger, Postman |
| **Frontend** | HTML5, CSS3, Bootstrap, JavaScript, ViewComponent, PartialView |

---

## 🚀 Kurulum

> Aşağıdaki adımlar genel bir akıştır. Klasör ve dosya adlarını kendi proje yapına göre düzenle.

### Gereksinimler
- [.NET 6.0 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Visual Studio 2022 veya VS Code

### Adımlar

1. Projeyi klonla:
   ```bash
   git clone https://github.com/KULLANICI_ADIN/PROJE_ADIN.git
   cd PROJE_ADIN
   ```

2. Gerekli altyapı servislerini (MongoDB, PostgreSQL, MSSQL, Redis, RabbitMQ) Docker ile ayağa kaldır:
   ```bash
   docker-compose up -d
   ```

3. Her servisin `appsettings.json` dosyasındaki bağlantı bilgilerini kendi ortamına göre güncelle.

4. Veritabanı migration'larını uygula (Entity Framework kullanan servisler için):
   ```bash
   dotnet ef database update
   ```

5. Servisleri sırayla çalıştır:
   - IdentityServer
   - Mikroservisler (Catalog, Basket, Order, Discount, Comment, Message vb.)
   - Ocelot API Gateway
   - Web arayüzü

6. Tarayıcıdan uygulamayı aç ve API'leri Swagger üzerinden test et.

---

## 🖼️ Ekran Görüntüleri

<!-- Görsellerini bir /images klasörüne koyup aşağıdaki gibi ekleyebilirsin -->

| Ana Sayfa | Admin Paneli | Kullanıcı Paneli |
|---|---|---|
| ![Ana Sayfa](images/home.png) | ![Admin](images/admin.png) | ![Kullanıcı](images/user.png) |

---

## 📚 Neler Öğrendim

Bu proje boyunca şunları hem öğrenme hem uygulama fırsatı buldum:

- Mikroservis mimarisinde servisleri doğru sınırlarla ayırmayı
- API Gateway ile merkezi yönlendirme ve güvenlik yönetimini
- IdentityServer, JWT ve OAuth 2.0 ile kimlik doğrulama/yetkilendirmeyi
- Aynı sistemde birden fazla veritabanı teknolojisini bir arada kullanmayı
- RabbitMQ ile asenkron, event-driven iletişim kurmayı
- Redis ile performans odaklı veri saklamayı
- Docker ile servisleri container olarak yönetmeyi
- SignalR ile gerçek zamanlı özellikler geliştirmeyi

---

## 📬 İletişim

Görüşlerini, önerilerini veya sorularını paylaşmaktan çekinme.

- 💼 LinkedIn: [linkedin.com/in/KULLANICI_ADIN](https://www.linkedin.com/in/KULLANICI_ADIN)
- 🌐 Blog: [gorkemsblog.runasp.net](https://gorkemsblog.runasp.net/)
- 🐙 GitHub: [github.com/KULLANICI_ADIN](https://github.com/KULLANICI_ADIN)

⭐ Projeyi beğendiysen bir yıldız bırakmayı unutma!
