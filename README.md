<div align="center">

# Selenium Otomasyon Manuel Test
### *Java + Selenium + TestNG + REST Assured ile UI ve API Test Otomasyonu*

[![Stars](https://img.shields.io/github/stars/ahmetturan1687/selenium-otomasyon-manuel-test?style=for-the-badge&logo=github&color=yellow)](https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test/stargazers)
[![Forks](https://img.shields.io/github/forks/ahmetturan1687/selenium-otomasyon-manuel-test?style=for-the-badge&logo=github)](https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test/network/members)
[![License](https://img.shields.io/badge/License-Not_Specified-lightgrey.svg?style=for-the-badge)](#-lisans)
[![Java](https://img.shields.io/badge/Java-11-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/projects/jdk/11/)
[![Maven](https://img.shields.io/badge/Maven-3.6+-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)](https://maven.apache.org/)
[![Selenium](https://img.shields.io/badge/Selenium-4.18.0-43B02A?style=for-the-badge&logo=selenium&logoColor=white)](https://www.selenium.dev/)
[![TestNG](https://img.shields.io/badge/TestNG-7.9.0-E83A3F?style=for-the-badge&logo=testng&logoColor=white)](https://testng.org/)
[![REST Assured](https://img.shields.io/badge/REST_Assured-5.4.0-6DB33F?style=for-the-badge&logo=postman&logoColor=white)](https://rest-assured.io/)

</div>

---

> **Hedef Site:** [automationexercise.com](https://www.automationexercise.com) üzerinde **kullanıcı arayüzü (UI)** ve **API** seviyesinde uçtan uca test otomasyonu.
> **Mimari:** Page Object Model (POM) | **Yapı:** Maven multi-suite TestNG | **Raporlama:** ExtentReports + Surefire

---

## İçindekiler

- [Genel Bakış](#genel-bakış)
- [Özellikler](#özellikler)
- [Teknoloji Stack](#teknoloji-stack)
- [Proje Yapısı](#proje-yapısı)
- [Ön Gereksinimler](#ön-gereksinimler)
- [Kurulum](#kurulum)
- [Testleri Çalıştırma](#testleri-çalıştırma)
- [Konfigürasyon](#konfigürasyon)
- [Test Raporları](#test-raporları)
- [Test Senaryoları](#test-senaryoları)
- [Manuel Test Dökümantasyonu](#manuel-test-dökümantasyonu)
- [Katkıda Bulunma](#katkıda-bulunma)
- [Lisans](#-lisans)
- [Yazar & Katkıda Bulunanlar](#yazar--katkıda-bulunanlar)

---

## Genel Bakış

Bu repo, **[automationexercise.com](https://www.automationexercise.com)** sitesi üzerinde gerçekleştirilen kapsamlı bir test otomasyon projesidir. Proje hem **fonksiyonel UI testlerini** hem de **REST API testlerini** kapsayacak şekilde tek bir Maven projesi altında toplanmıştır.

**Proje Hedefleri:**

- Endüstri standardı **Page Object Model (POM)** mimarisini uygulamak
- UI ve API testlerini **tek bir TestNG paketinde** birleştirmek
- **Manuel test senaryolarını** otomasyon kodu ile birebir eşlemek
- **WebDriverManager** ile sıfır konfigürasyon driver yönetimi sağlamak
- **ExtentReports** ile zengin, paylaşılabilir test raporları üretmek

---

## Özellikler

| Kategori | Açıklama |
|----------|----------|
| **UI Test Otomasyonu** | Selenium 4 WebDriver ile Chrome üzerinde uçtan uca senaryolar |
| **API Test Otomasyonu** | REST Assured 5.4 ile JSON request/response doğrulaması |
| **Page Object Model** | `BasePage` üzerinden türeyen modüler sayfa sınıfları |
| **TestNG XML Suites** | UI ve API testleri ayrı paketlerde, tek komutla çalışır |
| **WebDriverManager** | Chrome driver otomatik indirilir, manuel kurulum gerekmez |
| **Manuel Test Dökümanı** | `manuel-test/test-cases.md` ile otomasyon-manuel eşlemesi |
| **Zengin Raporlama** | ExtentReports + Surefire HTML çıktıları |
| **Konfigürasyon Yönetimi** | `config.properties` ile URL, kullanıcı, timeout ayarları |
| **Log Yönetimi** | SLF4J 2.0.12 ile yapılandırılmış loglama |
| **Paralel Çalıştırmaya Hazır** | TestNG suite seviyesinde paralel yürütme yapılandırılabilir |

---

## Teknoloji Stack

| Teknoloji | Sürüm | Rol |
|-----------|:-----:|-----|
| **Java** | `11` | Programlama dili |
| **Maven** | `3.6+` | Bağımlılık & build yönetimi |
| **Selenium WebDriver** | `4.18.0` | UI tarayıcı otomasyonu |
| **TestNG** | `7.9.0` | Test runner & assertion framework |
| **REST Assured** | `5.4.0` | API test framework |
| **WebDriverManager** | `5.7.0` | Driver binary yönetimi |
| **ExtentReports** | `5.1.1` | HTML test raporlama |
| **Jackson** | `2.16.1` | JSON serileştirme/deserileştirme |
| **SLF4J** | `2.0.12` | Loglama API'si |
| **Tarayıcı** | Chrome (latest) | Test edilen browser |

---

## Proje Yapısı

```text
selenium-otomasyon-manuel-test/
├── src/
│   ├── main/java/
│   │   ├── pages/                       # Page Object Model sınıfları
│   │   │   ├── BasePage.java            # Tüm sayfaların atası (driver, wait, ortak metodlar)
│   │   │   ├── HomePage.java            # Ana sayfa elementleri ve aksiyonları
│   │   │   ├── LoginPage.java           # Login formu
│   │   │   ├── RegisterPage.java        # Kayıt formu
│   │   │   ├── ProductsPage.java        # Ürün listesi & arama
│   │   │   └── CartPage.java            # Sepet işlemleri
│   │   └── utils/
│   │       ├── DriverManager.java       # WebDriver yaşam döngüsü
│   │       └── ConfigReader.java        # config.properties okuyucu
│   └── test/
│       ├── java/
│       │   ├── ui/                      # UI test sınıfları
│       │   │   ├── BaseTest.java        # @BeforeMethod / @AfterMethod hooks
│       │   │   ├── LoginTest.java       # 4 login senaryosu
│       │   │   └── ProductTest.java     # 5 ürün senaryosu
│       │   └── api/                     # API test sınıfları
│       │       └── UserApiTest.java     # 11 API senaryosu
│       └── resources/
│           ├── testng.xml               # UI + API suite tanımları
│           └── config.properties        # URL, credential, timeout
├── manuel-test/
│   └── test-cases.md                    # Manuel test senaryoları (TR)
├── target/                              # Build & rapor çıktıları (auto)
│   └── surefire-reports/                # TestNG/Surefire raporları
├── CHANGELOG.md                         # Sürüm geçmişi (Keep a Changelog)
├── REQUIREMENTS.md                      # Sistem & bağımlılık gereksinimleri
└── pom.xml                              # Maven proje tanımı
```

---

## Ön Gereksinimler

Aşağıdaki araçların yüklü ve `PATH` üzerinde erişilebilir olması gerekir:

| Gereksinim | Minimum Sürüm | Doğrulama Komutu |
|------------|:-------------:|------------------|
| JDK | 11 | `java -version` |
| Maven | 3.6.0 | `mvn -version` |
| Chrome Browser | Latest stable | `google-chrome --version` |
| Git | 2.x | `git --version` |

> **Not:** Chrome **driver** binary'si **WebDriverManager** tarafından otomatik indirilir. Manuel `chromedriver` kurulumuna gerek yoktur.

Detaylı sistem ve bağımlılık matrisi için [`REQUIREMENTS.md`](REQUIREMENTS.md) dosyasına bakın.

---

## Kurulum

```bash
# 1. Repoyu klonla
git clone https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test.git
cd selenium-otomasyon-manuel-test

# 2. Bağımlılıkları indir (testleri çalıştırmadan)
mvn clean install -DskipTests

# 3. (Opsiyonel) IntelliJ IDEA / Eclipse içine Maven projesi olarak import et
```

---

## Testleri Çalıştırma

### Tüm Test Paketini Çalıştır (UI + API)

```bash
mvn clean test
```

Bu komut, `src/test/resources/testng.xml` dosyasındaki **her iki suite**'i (UI Tests - Chrome, API Tests) sırayla çalıştırır.

### Sadece UI Testleri

```bash
mvn clean test -Dtest="ui.*Test"
```

### Sadece API Testleri

```bash
mvn clean test -Dtest="api.*Test"
```

### Tek Bir Test Sınıfı

```bash
# Sadece login testleri
mvn clean test -Dtest=LoginTest

# Sadece ürün testleri
mvn clean test -Dtest=ProductTest

# Sadece API kullanıcı testleri
mvn clean test -Dtest=UserApiTest
```

### Tek Bir Test Metodu

```bash
mvn clean test -Dtest=LoginTest#testSuccessfulLogin
```

### Belirli Bir TestNG XML ile Çalıştır

```bash
mvn clean test -DsuiteXmlFile=src/test/resources/testng.xml
```

---

## Konfigürasyon

Tüm ortam ayarları `src/test/resources/config.properties` dosyasında merkezileştirilmiştir:

```properties
# Hedef Uygulama
base.url=https://www.automationexercise.com
api.url=https://automationexercise.com/api

# Test hesabı — automationexercise.com'da kayıt olup doldurun
test.email=ornek@example.com
test.password=ChangeMe123!

# Tarayıcı
browser=chrome
```

`ConfigReader.java` bu değerleri runtime'da yükler. CI/CD ortamında değerler `-Dkey=value` ile override edilebilir.

> **Güvenlik:** Gerçek kullanıcı bilgilerini repoya commit etmeyin. Üretim/CI ortamında credential'ları environment variable veya secret manager üzerinden geçirin.

---

## Test Raporları

Test koşumu tamamlandıktan sonra raporlar aşağıdaki dizinlerde oluşturulur:

| Rapor Türü | Konum | Açıklama |
|------------|-------|----------|
| **Surefire HTML** | `target/surefire-reports/index.html` | Standart Maven Surefire raporu |
| **TestNG HTML** | `target/surefire-reports/emailable-report.html` | TestNG e-posta dostu özet |
| **TestNG XML** | `target/surefire-reports/testng-results.xml` | Makine okunabilir TestNG çıktısı |
| **ExtentReports** | `target/extent-reports/` | Ekran görüntülü, zengin HTML rapor |

> Raporu tarayıcıda hızlıca açmak için: `xdg-open target/surefire-reports/index.html` (Linux) veya `open ...` (macOS).

---

## Test Senaryoları

### UI Test Senaryoları (9 test)

| # | Sınıf | Test Metodu | Açıklama |
|:-:|-------|-------------|----------|
| 1 | `LoginTest` | `testSuccessfulLogin` | Geçerli kullanıcı bilgileriyle başarılı giriş |
| 2 | `LoginTest` | `testLoginWithWrongPassword` | Yanlış parola ile hata mesajı doğrulama |
| 3 | `LoginTest` | `testLoginWithUnregisteredEmail` | Kayıtlı olmayan e-posta ile hata kontrolü |
| 4 | `LoginTest` | `testLogout` | Oturum kapatma akışı |
| 5 | `ProductTest` | `testNavigateToProducts` | Products sayfasına yönlendirme |
| 6 | `ProductTest` | `testSearchProductWithValidKeyword` | Geçerli ürün adıyla arama |
| 7 | `ProductTest` | `testSearchProductWithNoResult` | Sonuç dönmeyen arama doğrulaması |
| 8 | `ProductTest` | `testAddProductToCart` | Ürünü sepete ekleme |
| 9 | `ProductTest` | `testRemoveProductFromCart` | Sepetten ürün çıkarma |

### API Test Senaryoları (11 test)

| # | Endpoint | Test | Açıklama |
|:-:|----------|------|----------|
| 1 | `GET /productsList` | All Products List | Tüm ürünleri listele |
| 2 | `GET /brandsList` | All Brands List | Marka listesini getir |
| 3 | `POST /searchProduct` | Search (valid param) | Geçerli arama parametresi |
| 4 | `POST /searchProduct` | Search (missing param) | Parametre eksik – hata kontrolü |
| 5 | `POST /verifyLogin` | Valid credentials | Geçerli login |
| 6 | `POST /verifyLogin` | Invalid credentials | Geçersiz login |
| 7 | `POST /verifyLogin` | Missing credentials | Eksik alan kontrolü |
| 8 | `POST /createAccount` | Create User | Yeni kullanıcı oluşturma |
| 9 | `GET /getUserDetailByEmail` | Get User Detail | Kullanıcı detayını getir |
| 10 | `DELETE /deleteAccount` | Delete User | Kullanıcı silme |
| 11 | `GET /getUserDetailByEmail` | Non-existent User | Var olmayan kullanıcı sorgusu |

### Test İstatistikleri

| Metrik | Değer |
|--------|:-----:|
| UI Testleri | **9** |
| API Testleri | **11** |
| **Toplam Test** | **20** |
| Page Object Sayısı | **6** |
| Utility Sınıfları | **2** |

---

## Manuel Test Dökümantasyonu

Otomasyon kapsamına alınan ve **manuel olarak yürütülen** tüm senaryolar Türkçe olarak şu dosyada belgelenmiştir:

[`manuel-test/test-cases.md`](manuel-test/test-cases.md)

Bu döküman:

- Her senaryonun **ön koşullarını**, **adımlarını** ve **beklenen sonuçlarını** içerir
- Otomasyon kodundaki test metodları ile **birebir eşlenebilir**
- QA ekibinin manuel regresyon koşumları için referans olarak kullanılabilir

---

## Katkıda Bulunma

Katkılar memnuniyetle karşılanır! Aşağıdaki akışı izleyebilirsiniz:

```bash
# 1. Repoyu fork'la ve klonla
# 2. Yeni bir feature branch oluştur
git checkout -b feature/yeni-test-senaryosu

# 3. Değişikliklerini commit'le
git commit -m "feat: Add checkout flow UI tests"

# 4. Branch'ini push'la
git push origin feature/yeni-test-senaryosu

# 5. Pull Request aç
```

**Katkı Kuralları:**

- Yeni eklenen sayfa objeleri **POM** desenini takip etmelidir
- Her UI testi `BaseTest` sınıfından türemelidir
- Yeni testler `testng.xml` içine **uygun suite'e** eklenmelidir
- Manuel karşılığı olan testler `manuel-test/test-cases.md` dosyasına da yazılmalıdır
- Commit mesajları [Conventional Commits](https://www.conventionalcommits.org/) standardını takip etmelidir
- Anlamlı değişiklikler [`CHANGELOG.md`](CHANGELOG.md) dosyasının `[Unreleased]` bölümüne eklenmelidir

---

## Lisans

Bu repoda **lisans dosyası bulunmamaktadır**. Açık bir lisans tanımı yapılana kadar, projedeki kodun tüm hakları varsayılan olarak yazara aittir. Kullanım, kopyalama veya dağıtım için repo sahibiyle iletişime geçilmesi önerilir.

> **Öneri:** Açık kaynak topluluğuna katkı için `MIT`, `Apache-2.0` veya `BSD-3-Clause` gibi standart bir lisans eklenmesi tavsiye edilir.

---

## Yazar & Katkıda Bulunanlar

| Rol | İsim | Bağlantı |
|-----|------|----------|
| **Orijinal Yazar** | Ahmet Turan | [@ahmetturan1687](https://github.com/ahmetturan1687) |
| **Geliştirici / İyileştirici** | Dr. Ümit Kaçar | [@umitkacar](https://github.com/umitkacar) |

---

<div align="center">

### Hızlı Linkler

[![Repository](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test)
[![Issues](https://img.shields.io/badge/Bug_Bildir-red?style=for-the-badge)](https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test/issues)
[![Pull Requests](https://img.shields.io/badge/Pull_Request-green?style=for-the-badge)](https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test/pulls)
[![Site Under Test](https://img.shields.io/badge/Test_Sitesi-blue?style=for-the-badge)](https://www.automationexercise.com)

---

**Java • Selenium • TestNG • REST Assured ile geliştirildi**

</div>
