# Changelog

Bu dosya, projedeki tüm önemli değişiklikleri belgelemektedir.

Format [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/) standardına dayanmakta olup, bu proje [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html) kurallarına uymaktadır.

Sürüm numaralandırma kuralları: `MAJOR.MINOR.PATCH`

- **MAJOR**: Geriye dönük uyumsuz API değişiklikleri
- **MINOR**: Geriye dönük uyumlu yeni özellikler
- **PATCH**: Geriye dönük uyumlu hata düzeltmeleri

---

## [Unreleased]

### Added

- `README.md` — proje rozetleri (badges), içindekiler tablosu (TOC), kurulum adımları, kullanım örnekleri, proje yapısı, test senaryosu tabloları ve katkıda bulunma rehberi.
- `CHANGELOG.md` — Keep a Changelog 1.1.0 formatına uygun sürüm geçmişi takibi.
- `REQUIREMENTS.md` — sistem gereksinimleri (JDK 11+, Maven 3.6+, Chrome), bağımlılık matrisi, donanım önerileri ve ağ gereksinimleri.

### Changed

- Proje dokümantasyonu profesyonel standartlara taşındı; yeni geliştiricilerin katılım süresi (onboarding) iyileştirildi.

---

## [1.0.0] - 2025-12-01

İlk kararlı sürüm. UI otomasyon, API test ve manuel test senaryolarını kapsayan tam test çatısı.

### Added

#### Çekirdek Altyapı

- `pom.xml` — Maven proje yapılandırması ve bağımlılık yönetimi.
- Java 11 ve Maven tabanlı proje iskeleti.
- `DriverManager` — WebDriver yaşam döngüsü yönetimi.
- `ConfigReader` — `config.properties` dosyasından yapılandırma okuma yardımcısı.
- `BaseTest` — TestNG `@BeforeMethod` / `@AfterMethod` yaşam döngüsü ile ortak setup-teardown mantığı.
- `config.properties` — ortam, tarayıcı, base URL ve test kullanıcı parametreleri.
- `testng.xml` — UI ve API testlerini iki ayrı suite altında çalıştıran TestNG yapılandırması.
- `.gitignore` — Maven, IntelliJ IDEA ve OS spesifik dosyalar için ignore kuralları.

#### Page Object Model (POM)

- `BasePage` — ortak sayfa etkileşimleri (click, sendKeys, waitFor, getText) için temel sınıf.
- `HomePage` — ana sayfa elementleri ve navigasyon aksiyonları.
- `LoginPage` — giriş formu lokatörleri ve `loginWithCredentials(email, password)` metodu.
- `RegisterPage` — kullanıcı kayıt akışı için sayfa nesnesi.
- `ProductsPage` — ürün listeleme, arama ve sepete ekleme aksiyonları.
- `CartPage` — sepet görüntüleme, ürün silme ve içerik doğrulama.

#### UI Test Senaryoları (9 test)

- `LoginTest` — 4 senaryo: başarılı giriş, hatalı şifre, kayıtlı olmayan e-posta, başarılı çıkış.
- `ProductTest` — 5 senaryo: ürünler sayfasına gitme, geçerli arama, sonuç dönmeyen arama, sepete ekleme, sepetten silme.

#### API Test Senaryoları (11 test)

- `UserApiTest` — REST Assured tabanlı 11 API testi:
  - `GET /productsList` — tüm ürünleri listele
  - `GET /brandsList` — tüm markaları listele
  - `POST /searchProduct` — geçerli ve eksik parametre senaryoları
  - `POST /verifyLogin` — geçerli, geçersiz ve eksik bilgi senaryoları
  - `POST /createAccount` — yeni kullanıcı oluşturma
  - `GET /getUserDetailByEmail` — kullanıcı detayı sorgulama (var/yok)
  - `DELETE /deleteAccount` — kullanıcı silme

#### Manuel Test Dokümantasyonu

- `manuel-test/test-cases.md` — Türkçe manuel test senaryoları, ön koşullar, adımlar ve beklenen sonuçlar.

#### Bağımlılıklar

- Selenium Java 4.18.0 — tarayıcı otomasyonu.
- TestNG 7.9.0 — test çalıştırma ve assertion framework'ü.
- REST Assured 5.4.0 — API test kütüphanesi.
- REST Assured JSON Schema Validator 5.4.0 — JSON şema doğrulama.
- WebDriverManager 5.7.0 — driver binary yönetimi otomasyonu.
- ExtentReports 5.1.1 — zengin HTML raporlama.
- Jackson Databind 2.16.1 — JSON serileştirme/deserileştirme.
- SLF4J Simple 2.0.12 — loglama implementasyonu.
- Maven Surefire Plugin 3.2.5 — TestNG suite çalıştırma motoru.

### Security

- Hassas bilgiler `config.properties` üzerinden yönetilmekte; gerçek üretim sırlarının repoya commit edilmemesi için `.gitignore` kuralları uygulandı.

---

[Unreleased]: https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test/releases/tag/v1.0.0
