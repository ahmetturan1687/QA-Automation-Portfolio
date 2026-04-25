# Gereksinimler (Requirements)

Bu doküman, projenin çalıştırılabilmesi için ihtiyaç duyulan tüm sistem gereksinimlerini, bağımlılıkları (dependencies) ve araçları listeler. Python ekosistemindeki `requirements.txt` dosyasının Java/Maven dünyasındaki karşılığı olarak düşünülebilir; ancak Maven projelerinde bağımlılık yönetimi `pom.xml` üzerinden yapıldığı için bu dosya hem `pom.xml`'in özet bir matrisini hem de sistem seviyesindeki ön koşulları (prerequisites) belgeler.

> **Not:** Bağımlılıkları manuel olarak yüklemenize gerek yoktur. `mvn` komutu ilk çalıştırıldığında tüm Java bağımlılıkları Maven Central'dan otomatik olarak indirilir ve `~/.m2/repository` altına yerleşir.

---

## 1. Sistem Gereksinimleri (System Requirements)

| Bileşen | Minimum Sürüm | Önerilen | Doğrulama Komutu |
|---------|---------------|----------|------------------|
| İşletim Sistemi | Linux / macOS / Windows 10+ | Ubuntu 22.04+ veya macOS 13+ | `uname -a` |
| JDK | Java 11 | Java 17 (LTS) | `java -version` |
| Apache Maven | 3.6.x | 3.9.x | `mvn -version` |
| Google Chrome | Son kararlı (latest stable) | En güncel sürüm | `google-chrome --version` |
| Git | 2.20+ | 2.40+ | `git --version` |
| İnternet Bağlantısı | Zorunlu | Stabil broadband | `ping -c 3 www.automationexercise.com` |

> ChromeDriver'ı manuel olarak indirmenize **gerek yoktur**. `WebDriverManager` (Bonigarcia) Chrome sürümünüzü tespit edip uyumlu driver'ı otomatik yönetir.

---

## 2. Bağımlılık Matrisi (Dependency Matrix)

`pom.xml` dosyasından türetilmiştir. Tüm bağımlılıklar Maven Central üzerinden çekilir.

| groupId | artifactId | Sürüm | Amaç (Purpose) |
|---------|------------|-------|----------------|
| `org.seleniumhq.selenium` | `selenium-java` | `4.18.0` | Tarayıcı otomasyonu (UI testleri) |
| `io.github.bonigarcia` | `webdrivermanager` | `5.7.0` | ChromeDriver'ın otomatik yönetimi |
| `org.testng` | `testng` | `7.9.0` | Test framework, suite/runner |
| `io.rest-assured` | `rest-assured` | `5.4.0` | REST API test DSL |
| `io.rest-assured` | `json-schema-validator` | `5.4.0` | JSON Schema doğrulaması |
| `com.fasterxml.jackson.core` | `jackson-databind` | `2.16.1` | JSON serileştirme/deserileştirme |
| `com.aventstack` | `extentreports` | `5.1.1` | HTML test raporlama |
| `org.slf4j` | `slf4j-simple` | `2.0.12` | Loglama (basit konsol implementasyonu) |

---

## 3. Maven Plugin'leri

| Plugin | Sürüm | Amaç |
|--------|-------|------|
| `maven-surefire-plugin` | `3.2.5` | TestNG suite (`testng.xml`) çalıştırma motoru |
| `maven-compiler-plugin` | varsayılan | Java 11 kaynak/hedef derleme |

---

## 4. Önerilen Araçlar (Optional / Recommended Tools)

Bu araçlar zorunlu değildir ancak geliştirici deneyimini iyileştirir:

| Araç | Kullanım Amacı |
|------|----------------|
| IntelliJ IDEA (Community veya Ultimate) | Birincil önerilen IDE — TestNG ve Maven entegrasyonu mükemmel |
| Eclipse IDE for Java Developers | Alternatif IDE, TestNG plugin gerekir |
| Visual Studio Code + Extension Pack for Java | Hafif alternatif |
| Postman / Insomnia / Bruno | API testlerini manuel doğrulamak için |
| ExtentReports Viewer | Rapor görselleştirme |

---

## 5. Donanım Önerileri (Hardware Recommendations)

| Kaynak | Minimum | Önerilen |
|--------|---------|----------|
| CPU | 2 çekirdek (x86_64 / ARM64) | 4+ çekirdek |
| RAM | 4 GB | 8 GB+ (Chrome + IDE birlikte için) |
| Disk | 2 GB boş alan | 5 GB+ (Maven cache + tarayıcı profilleri) |
| Ekran | 1366x768 | 1920x1080 (UI testlerinde tarayıcı pencere boyutu için) |

---

## 6. Ağ Gereksinimleri (Network Requirements)

Aşağıdaki adreslere giden (outbound) HTTPS trafiğine izin verilmelidir:

| URL | Amaç |
|-----|------|
| `https://repo.maven.apache.org/maven2` | Maven Central — bağımlılık indirme |
| `https://www.automationexercise.com` | Test edilen UI uygulaması (SUT) |
| `https://automationexercise.com/api` | REST Assured API testlerinin hedefi |
| `https://googlechromelabs.github.io/chrome-for-testing` | WebDriverManager driver metadata |
| `https://storage.googleapis.com/chrome-for-testing-public` | ChromeDriver binary indirme |
| `https://github.com` | Repo klonlama |

> Kurumsal proxy arkasındaysanız `~/.m2/settings.xml` dosyasında proxy konfigürasyonu yapmanız gerekir.

---

## 7. Bağımlılıkların Kurulumu

Tüm Java bağımlılıkları tek komutla indirilir:

```bash
# Repoyu klonla
git clone https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test.git
cd selenium-otomasyon-manuel-test

# Bağımlılıkları indir (test çalıştırmadan)
mvn clean install -DskipTests
```

Bu komut:

- `pom.xml`'deki tüm transitive bağımlılıkları çözer
- Yerel Maven cache'ine (`~/.m2/repository`) indirir
- Projeyi derler (`target/` dizini oluşur)
- Testleri **çalıştırmaz** (`-DskipTests` flag'i nedeniyle)

---

## 8. Ortamı Doğrulama (Verifying the Environment)

Aşağıdaki komut bloğunu çalıştırarak ortamınızın hazır olduğundan emin olabilirsiniz:

```bash
# 1. Java 11+ kurulu mu?
java -version

# 2. Maven 3.6+ kurulu mu?
mvn -version

# 3. Chrome erişilebilir mi?
google-chrome --version    # Linux
# veya: "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --version  # macOS

# 4. SUT (test edilen sistem) ulaşılabilir mi?
curl -I https://www.automationexercise.com

# 5. Maven Central'a erişim var mı?
curl -I https://repo.maven.apache.org/maven2/

# 6. Bağımlılıklar başarıyla çözülüyor mu?
mvn dependency:resolve
```

Tüm komutlar hata vermeden tamamlanıyorsa, ortam test çalıştırmaya hazırdır.

---

## 9. Bağımlılıkları Güncelleme

Bağımlılıkların güncel sürümlerini kontrol etmek için `versions-maven-plugin` kullanılabilir:

```bash
# Bağımlılık güncellemelerini listele
mvn versions:display-dependency-updates

# Plugin güncellemelerini listele
mvn versions:display-plugin-updates
```

> Selenium gibi kritik bağımlılıkları güncellemeden önce regresyon testlerini çalıştırın. Selenium 4.x serisi içinde minor sürüm geçişleri (örn. 4.18 → 4.20) genellikle güvenlidir, ancak major geçişler (3.x → 4.x) API değişiklikleri içerir.

---

## Özet

Bu proje, modern bir Java test otomasyon yığını üzerine inşa edilmiştir: **Java 11 + Maven + Selenium 4 + TestNG + REST Assured + ExtentReports**. Yukarıdaki sistem gereksinimleri karşılandığı sürece proje, geliştirici makinelerinde, CI/CD pipeline'larında (Jenkins, GitHub Actions, GitLab CI) ve Docker container'larında sorunsuz çalışır.
