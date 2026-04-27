# Changelog

Bu dosya projedeki tüm önemli değişiklikleri kaydeder.

---

## [1.0.0] — 2026-04-25

### Eklendi
- Java + Selenium WebDriver 4.18.0 ile Page Object Model (POM) mimarisi
- `BasePage` — reklam engelleme (JS), akıllı tıklama, sayfa yükleme bekleme
- `HomePage` — direkt URL navigasyonu (reklam bypass)
- `LoginPage` — giriş ve kayıt form işlemleri
- `ProductsPage` — ürün arama, hover ile sepete ekleme, modal yönetimi
- `CartPage` — sepet doğrulama ve ürün silme
- `RegisterPage` — kullanıcı kayıt formu
- UI test sınıfları: `LoginTest`, `ProductsTest`, `CartTest`
- REST Assured 5.4.0 ile API test sınıfı: `UserApiTest` (11 senaryo)
- `ConfigReader` — `config.properties` üzerinden merkezi konfigürasyon
- `BaseTest` — ThreadLocal WebDriver ile paralel test desteği
- `testng.xml` — UI ve API suite tanımları
- Manuel test senaryoları: `manuel-test/test-cases.md`
- `.gitignore` — Maven ve IDE dosyaları için

### Düzeltildi
- `RestAssured.registerParser("text/html", Parser.JSON)` — site JSON döndürür ama `text/html` Content-Type gönderir
- Reklam iframe'lerini JS ile kaldırma (`dismissAds`)
- `ElementClickInterceptedException` için JS fallback tıklama
- Test kimlik bilgileri tüm dosyalarda güncellendi
- `pom.xml` içindeki bozuk `<testSourceDirectory>` etiketi kaldırıldı

---

## [Unreleased]

- Test raporlama (Allure veya ExtentReports) entegrasyonu planlanıyor
- Paralel tarayıcı desteği (Firefox, Edge)
