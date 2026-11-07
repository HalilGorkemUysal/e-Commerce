# 🛒 MultiShop | ASP.NET Core Microservices E-Commerce

## 📌 Proje Hakkında

**MultiShop**, ASP.NET Core 6.0 kullanılarak mikroservis mimarisiyle geliştirdiğim kapsamlı bir e-ticaret uygulamasıdır.

Bu projede temel amacım, gerçek hayattaki e-ticaret sistemlerinin işleyişini mikroservis yaklaşımıyla ele almak, farklı teknolojilerin bir arada nasıl çalıştığını deneyimlemek ve yönetilebilir, modüler ve ölçeklenebilir bir yazılım altyapısı oluşturmaktı.

Monolitik bir yapı yerine, farklı iş süreçlerini birbirinden bağımsız servisler üzerinden yöneten bir mimari tercih ettim. Ürün yönetimi, sipariş işlemleri, sepet yönetimi, kullanıcı işlemleri ve diğer e-ticaret fonksiyonlarını ayrı servisler üzerinden ele aldım.

Backend tarafında ASP.NET Core Web API teknolojisini kullanırken, kullanıcı arayüzü için ASP.NET Core MVC yapısından yararlandım. Veri yönetimi, kimlik doğrulama, servisler arası iletişim ve asenkron işlemler için farklı teknolojileri projeye entegre ettim.

Proje, **Murat Yücedağ** tarafından verilen *ASP.NET Core MultiShop Mikroservis E-Ticaret* eğitimi kapsamında geliştirilmiştir.

---

## 🚀 Kullanılan Teknolojiler

Projeyi geliştirirken farklı ihtiyaçlara yönelik çeşitli teknolojilerden ve yazılım geliştirme yaklaşımlarından yararlandım.

### 💻 Backend ve Mimari

- **ASP.NET Core 6.0 (MVC & Web API):** Backend servislerinin ve web uygulamasının geliştirilmesi
- **Microservices Architecture:** İş süreçlerinin bağımsız servisler üzerinden yönetilmesi
- **RESTful API:** Servisler arasında HTTP tabanlı iletişim kurulması
- **Ocelot API Gateway:** API isteklerinin merkezi bir noktadan ilgili servislere yönlendirilmesi
- **Onion Architecture:** Katmanlı, sürdürülebilir ve bağımlılıkları kontrol altında tutan mimari yapı
- **CQRS & MediatR:** Komut ve sorgu işlemlerinin birbirinden ayrılması
- **Repository Pattern:** Veri erişim işlemlerinin soyutlanması
- **DTO & AutoMapper:** Katmanlar arasında veri aktarımı ve nesne eşleme işlemleri
- **API Consume:** Backend servislerinden alınan verilerin MVC arayüzünde kullanılması

### 🗄️ Veritabanı ve Önbellekleme

- **Microsoft SQL Server:** İlişkisel verilerin yönetimi
- **PostgreSQL:** İlişkisel veritabanı işlemleri
- **MongoDB:** NoSQL tabanlı veri yönetimi
- **Redis:** Sepet verilerinin saklanması ve önbellekleme işlemleri

### 🔐 Güvenlik ve Kimlik Yönetimi

- **IdentityServer:** Merkezi kimlik yönetimi
- **JWT (JSON Web Token):** Token tabanlı kimlik doğrulama
- **OAuth 2.0:** Yetkilendirme süreçleri ve güvenli erişim

### 🔄 Mesajlaşma ve Gerçek Zamanlı İşlemler

- **RabbitMQ:** Servisler arasında asenkron mesajlaşma
- **SignalR:** Gerçek zamanlı bildirimler ve canlı veri aktarımı

### 🐳 DevOps ve Bulut Teknolojileri

- **Docker:** Mikroservislerin container ortamında çalıştırılması
- **Google Cloud Storage:** Ürün görselleri ve dosyaların bulut ortamında yönetilmesi

### 🎨 Frontend

- **HTML5**
- **CSS3**
- **Bootstrap**
- **JavaScript**
- **Razor Views**
- **ViewComponent & PartialView**

### 🧪 API Test ve Dokümantasyon

- **Swagger:** API endpoint'lerinin dokümantasyonu ve test edilmesi
- **Postman:** API isteklerinin ve servis yanıtlarının test edilmesi

---

## 🏗️ Proje Mimarisi

MultiShop uygulamasını geliştirirken mikroservis mimarisinin sunduğu modülerlik ve bağımsız servis yönetimi yaklaşımını temel aldım.

Her mikroservis belirli bir iş alanından sorumludur. Böylece uygulamanın farklı bölümleri birbirinden bağımsız olarak geliştirilebilir ve yönetilebilir.

**Mimarinin temel bileşenleri:**

- **API Gateway:** İstemcilerden gelen isteklerin ilgili servislere yönlendirilmesi
- **Identity Service:** Kimlik doğrulama ve yetkilendirme işlemleri
- **Catalog Service:** Ürün, kategori ve ürün detaylarının yönetimi
- **Basket Service:** Kullanıcı sepetlerinin Redis üzerinden yönetilmesi
- **Order Service:** Sipariş oluşturma ve sipariş süreçlerinin yönetimi
- **Discount Service:** İndirim ve kampanya işlemleri
- **Message Service:** Kullanıcı mesajlaşma işlemleri
- **Diğer Servisler:** Uygulamanın farklı iş ihtiyaçlarına yönelik bağımsız servisler

Bu mimariyle servisler arasındaki bağımlılıkları azaltmayı, kodun bakımını kolaylaştırmayı ve farklı veri depolama teknolojilerini aynı sistem içinde kullanmayı hedefledim.

---

## 🖥️ Uygulama Modülleri

MultiShop üç temel arayüzden oluşmaktadır.

### 🛍️ 1. E-Ticaret Web Sitesi

Kullanıcıların ürünleri inceleyebildiği, alışveriş yapabildiği ve sipariş süreçlerini gerçekleştirebildiği ana uygulama bölümüdür.

**Başlıca özellikler:**

- Ürünlerin listelenmesi ve detaylarının görüntülenmesi
- Kategorilere göre ürün filtreleme
- Ürünlerin alışveriş sepetine eklenmesi
- Sepet içeriğinin güncellenmesi ve yönetilmesi
- Sipariş ve ödeme süreçleri
- Kampanya ve indirimlerin görüntülenmesi
- Döviz kuru bilgilerinin entegrasyonu
- Hava durumu verilerinin gösterilmesi
- Responsive ve kullanıcı dostu arayüz

### 🛠️ 2. Yönetici (Admin) Paneli

Sistemdeki içeriklerin ve operasyonel işlemlerin yönetilmesi için geliştirdiğim yönetim arayüzüdür.

Yetkili kullanıcılar bu panel aracılığıyla uygulamanın farklı bölümlerinde CRUD (Create, Read, Update, Delete) işlemleri gerçekleştirebilir.

**Başlıca özellikler:**

- Ürün yönetimi
- Kategori yönetimi
- Marka yönetimi
- Kampanya ve indirim yönetimi
- Slider ve vitrin içeriklerinin yönetimi
- Kullanıcı yönetimi
- İstatistiksel verilerin görüntülenmesi
- Dinamik içerik yönetimi

### 👤 3. Kullanıcı Paneli

Sisteme kayıtlı kullanıcıların kişisel bilgilerini ve e-ticaret işlemlerini takip edebildiği bölümdür.

**Başlıca özellikler:**

- Kullanıcı profil bilgilerinin görüntülenmesi
- Profil bilgilerinin güncellenmesi
- Geçmiş siparişlerin listelenmesi
- Sipariş detaylarının incelenmesi
- Gelen mesajların görüntülenmesi
- Gönderilen mesajların takip edilmesi
- Kullanıcıya özel işlemlerin yönetilmesi

---

## ⚙️ Teknik Yaklaşım

### 🔹 Mikroservisler Arası İletişim

Servisler arasındaki iletişim için RESTful API yaklaşımını kullandım. API Gateway tarafında Ocelot ile merkezi yönlendirme yapısı oluşturdum.

Asenkron işlem gerektiren senaryolarda RabbitMQ kullanarak mesaj tabanlı iletişim yaklaşımını uyguladım.

### 🔹 Veri Yönetimi

Projedeki servislerin ihtiyaçlarına göre MongoDB, MSSQL ve PostgreSQL veritabanlarından yararlandım.

Redis teknolojisini özellikle sepet yönetimi ve önbellekleme senaryolarında kullandım.

CQRS, MediatR ve Repository Pattern gibi yaklaşımlarla veri erişim ve iş mantığı süreçlerini daha düzenli hale getirdim.

### 🔹 Kimlik Doğrulama ve Yetkilendirme

IdentityServer, JWT ve OAuth 2.0 teknolojileriyle kullanıcı kimlik doğrulama ve yetkilendirme süreçleri üzerinde çalıştım.

Kullanıcı ve yönetici panelleri için rol bazlı erişim yaklaşımını uyguladım.

### 🔹 Gerçek Zamanlı İşlemler

SignalR kullanarak gerçek zamanlı bildirimlerin ve canlı istatistiklerin uygulama arayüzüne aktarılmasını sağladım.

### 🔹 Container Yönetimi

Docker teknolojisinden yararlanarak mikroservislerin container tabanlı ortamlarda çalıştırılmasını ele aldım.

---

## 📚 Proje Sürecinde Kazandığım Deneyimler

Bu projeyi geliştirirken yalnızca farklı teknolojileri kullanmakla kalmadım, aynı zamanda bu teknolojilerin birbirleriyle nasıl entegre edildiğini de deneyimledim.

Özellikle;

- Mikroservis mimarisinin tasarlanması ve servis sorumluluklarının ayrılması
- Farklı veritabanı sistemlerinin bir projede birlikte kullanılması
- API Gateway üzerinden servis iletişiminin yönetilmesi
- Kimlik doğrulama ve yetkilendirme mekanizmalarının uygulanması
- RabbitMQ ile asenkron mesajlaşma süreçlerinin oluşturulması
- Docker ile container tabanlı uygulama geliştirilmesi
- Backend servislerinin MVC arayüzüyle entegre edilmesi
- Gerçek bir e-ticaret sistemindeki iş süreçlerinin modellenmesi

konularında uygulamalı çalışma fırsatı buldum.

Bu proje, ASP.NET Core ekosisteminde mikroservis tabanlı uygulama geliştirme konusunda edindiğim bilgileri pekiştirmemi sağlayan kapsamlı bir çalışma oldu.

---
🙏 

---

⭐ **Projeyi faydalı bulduysanız GitHub üzerinden yıldız vererek destek olabilirsiniz!**
