# Selenium Otomasyon & Manuel Test — automationexercise.com

Java + Selenium WebDriver ve REST Assured ile yazılmış kapsamlı test otomasyon projesi.  
Hedef site: [automationexercise.com](https://www.automationexercise.com)

## İçerik

```
├── src/
│   ├── main/java/pages/       # Page Object Model sınıfları
│   └── test/java/
│       ├── ui/                # Selenium UI testleri
│       └── api/               # REST Assured API testleri
├── manuel-test/
│   └── test-cases.md          # Manuel test senaryoları
└── pom.xml
```

## Teknolojiler

| Araç | Versiyon |
|------|----------|
| Java | 23 |
| Selenium WebDriver | 4.18.0 |
| REST Assured | 5.4.0 |
| TestNG | 7.9.0 |
| WebDriverManager | 5.7.0 |
| Maven | 3.x |

## Kurulum

**Gereksinimler:** Java 23, Maven, Google Chrome

```bash
git clone https://github.com/ahmetturan1687/selenium-otomasyon-manuel-test.git
cd selenium-otomasyon-manuel-test
mvn test
```

## Test Senaryoları

### UI Testleri (Selenium)

| ID | Açıklama |
|----|----------|
| TC-UI-001 | Başarılı kullanıcı girişi |
| TC-UI-002 | Hatalı şifre ile giriş |
| TC-UI-003 | Başarılı çıkış (logout) |
| TC-UI-004 | Ürünler sayfasına gitme |
| TC-UI-005 | Ürün arama — geçerli kelime |
| TC-UI-006 | Sepete ürün ekleme |

### API Testleri (REST Assured)

| ID | Endpoint | Açıklama |
|----|----------|----------|
| TC-API-001 | GET /productsList | Tüm ürün listesini al |
| TC-API-002 | GET /brandsList | Tüm marka listesini al |
| TC-API-003 | POST /searchProduct | Ürün arama — geçerli kelime |
| TC-API-004 | POST /searchProduct | Ürün arama — eksik parametre |
| TC-API-005 | POST /verifyLogin | Geçerli kullanıcı girişi |
| TC-API-006 | POST /verifyLogin | Hatalı şifre ile giriş |
| TC-API-007 | POST /verifyLogin | Eksik parametre ile giriş |
| TC-API-008 | POST /createAccount | Yeni kullanıcı oluştur |
| TC-API-009 | GET /getUserDetailByEmail | E-posta ile kullanıcı detayı |
| TC-API-010 | DELETE /deleteAccount | Kullanıcı hesabı sil |
| TC-API-011 | GET /getUserDetailByEmail | Var olmayan kullanıcı ara |

## Testleri Çalıştırma

```bash
# Tüm testler
mvn test

# Sadece UI testleri
mvn test -Dgroups=ui

# Sadece API testleri
mvn test -Dgroups=api
```

## Manuel Test

`manuel-test/test-cases.md` dosyasında UI ve API için adım adım manuel test senaryoları bulunmaktadır.
