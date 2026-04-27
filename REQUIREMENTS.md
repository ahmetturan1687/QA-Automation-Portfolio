# Gereksinimler

## Sistem Gereksinimleri

| Gereksinim | Minimum | Önerilen |
|------------|---------|----------|
| İşletim Sistemi | Windows 10 / macOS 12 / Ubuntu 20.04 | Windows 11 |
| RAM | 4 GB | 8 GB |
| Disk | 2 GB boş alan | 5 GB boş alan |
| İnternet | Gerekli | Gerekli |

## Yazılım Gereksinimleri

### Zorunlu

| Yazılım | Versiyon | İndirme |
|---------|----------|---------|
| Java JDK | 11+ (23 önerilir) | [adoptium.net](https://adoptium.net) |
| Apache Maven | 3.8+ | [maven.apache.org](https://maven.apache.org) |
| Google Chrome | Son versiyon | [chrome.google.com](https://www.google.com/chrome) |

> **Not:** ChromeDriver otomatik olarak WebDriverManager tarafından indirilir, ayrıca kurulum gerekmez.

### Opsiyonel

| Yazılım | Amaç |
|---------|------|
| IntelliJ IDEA Community 2024.3+ | IDE üzerinden test çalıştırma |
| Git | Versiyon kontrolü |
| Postman | Manuel API testi |

## Maven Bağımlılıkları

```xml
<!-- pom.xml içinde tanımlı -->
selenium-java          4.18.0
rest-assured           5.4.0
testng                 7.9.0
webdrivermanager       5.7.0
jackson-databind       2.16.1
slf4j-simple           2.0.12
lombok                 1.18.30
```

## Ortam Değişkenleri

Maven veya sistem yoluna eklenmesi gerekenler:

```
JAVA_HOME  = C:\Program Files\Java\jdk-23   (JDK kurulum dizini)
M2_HOME    = C:\apache-maven-3.x.x           (Maven kurulum dizini — isteğe bağlı)
```

## Konfigürasyon

`src/test/resources/config.properties` dosyasında aşağıdaki değerleri güncelle:

```properties
base.url=https://www.automationexercise.com
api.url=https://automationexercise.com/api
test.email=<kayıtlı-email>
test.password=<şifre>
browser=chrome
```

## Kurulum Adımları

```bash
# 1. Repoyu klonla
git clone https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test.git
cd selenium-otomasyon-manuel-test

# 2. Bağımlılıkları indir
mvn dependency:resolve

# 3. Testleri çalıştır
mvn test
```

## Bilinen Kısıtlamalar

- `automationexercise.com` zaman zaman `503 Service Unavailable` döndürebilir; ilgili testler bu durumu tolere eder.
- Site reklam iframe'leri yükleme süresini artırabilir; testler JS ile bu engeli aşar.
- CDP uyarısı (`Unable to find CDP implementation matching 147`) zararsızdır, testleri etkilemez.
