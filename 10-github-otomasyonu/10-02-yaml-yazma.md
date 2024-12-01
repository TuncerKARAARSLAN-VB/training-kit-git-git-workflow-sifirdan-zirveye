# **.yml Dosyaları Yazma**

YAML (YAML Ain’t Markup Language), genellikle yapılandırma dosyalarında kullanılan, insan tarafından okunabilir bir veri serileştirme dilidir. GitHub Actions, CI/CD iş akışlarını tanımlamak için `.yml` dosyalarını kullanır. GitHub Actions iş akışları, `.github/workflows` dizininde YAML formatında tanımlanır.

Bu modülde, `.yml` dosyalarının nasıl yazılacağını, doğru bir biçimde nasıl yapılandırılacağını, GitHub Actions’ta nasıl kullanılacağını ve yaygın hatalardan nasıl kaçınılacağını öğreneceksiniz.

---

## **1. YAML Formatına Giriş**

YAML, anahtar-değer çiftlerinden oluşan, hiyerarşik verileri temsil etmek için kullanılan bir dildir. Genellikle bu format, liste, dizi, sözlük ve daha karmaşık veri yapılarını temsil etmek için kullanılır.

### **YAML Temel Kuralları:**

- **Girintiler (Indentation):** YAML, girinti tabanlı bir format kullanır. Genellikle her seviye için iki boşluk girintisi kullanılır.
- **Anahtar-değer çiftleri (Key-Value Pairs):** Anahtarlar ve değerler arasına `:` koyarak belirlenir.
- **Listeler:** Listeler, `-` işaretiyle başlar.
- **Yorumlar:** Yorumlar `#` işaretiyle başlar ve satırın geri kalanını açıklamak için kullanılır.

Örnek YAML dosyası:

```yaml
# Bu bir örnek YAML dosyasıdır

name: My CI/CD Workflow

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out the code
        uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

Bu dosyada:

- `name` anahtarı iş akışının adını belirtir.
- `on` anahtarı, iş akışının hangi olaylarla tetikleneceğini belirler.
- `jobs` anahtarı altında `build` adında bir iş tanımlanır ve bu işin hangi ortamda çalışacağı (`runs-on`), hangi adımların takip edileceği (`steps`) belirtilir.

---

## **2. GitHub Actions İçin YAML Dosyası Yapısı**

GitHub Actions iş akışları için `.yml` dosyalarının temel yapı taşları şunlardır:

### **a. Olaylar (Events)**

GitHub Actions iş akışları, belirli olaylar sonucunda tetiklenir. Bu olaylar, `on` anahtarı ile tanımlanır. Örnek olaylar:

- `push`: Bir commit yapıldığında tetiklenir.
- `pull_request`: Bir pull request oluşturulduğunda tetiklenir.
- `schedule`: Belirli zaman dilimlerinde otomatik olarak tetiklenir.
- `workflow_dispatch`: Manuel olarak tetiklenebilir.

Örnek:

```yaml
on:
  push:
    branches:
      - main
```

### **b. İşler (Jobs)**

Bir iş, bir veya daha fazla adım (step) içerir. Her iş, belirli bir ortamda (`runs-on`) çalışır. İşler, paralel olarak veya sırasıyla çalıştırılabilir.

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
```

### **c. Adımlar (Steps)**

Her işteki adımlar, sırasıyla çalıştırılır ve her bir adım bir eylem veya komut çalıştırır. Adımlar `run`, `uses` veya `with` gibi anahtarlarla tanımlanabilir.

```yaml
steps:
  - name: Checkout code
    uses: actions/checkout@v2
  - name: Run tests
    run: npm test
```

---

## **3. Örnek Senaryolar ve Hands-On**

### **Senaryo 1: Basit CI İş Akışı**

Bir Node.js projesinde, her commit sonrası testlerin çalıştırılmasını istiyoruz.

#### **YAML Dosyası:**

```yaml
name: Node.js CI

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

#### **Açıklama:**

- `on.push.branches.main`: Bu iş akışı, yalnızca `main` dalına yapılan her push işleminde tetiklenecek.
- `actions/setup-node@v2`: Node.js ortamını kurar.
- `npm test`: Testleri çalıştırır.

**Hands-On:**

- Katılımcılar bu iş akışını kendi projelerinde uygulayarak her commit sonrası otomatik testlerin çalıştırılmasını sağlayacaklardır.

---

### **Senaryo 2: Manual Trigger (Manuel Tetikleyici)**

Bir iş akışını manuel olarak tetiklemek istiyoruz. Bu, belirli bir işin sadece ihtiyaca göre çalıştırılmasını sağlar.

#### **YAML Dosyası:**

```yaml
name: Manual Workflow Trigger

on:
  workflow_dispatch:

jobs:
  run-manually:
    runs-on: ubuntu-latest
    steps:
      - name: Check out the code
        uses: actions/checkout@v2
      - name: Run a manual task
        run: echo "This is a manual trigger!"
```

#### **Açıklama:**

- `workflow_dispatch`: Bu iş akışı, manuel olarak tetiklenebilir.
- `run: echo "This is a manual trigger!"`: Manuel tetikleme sonrası çalışacak adım.

**Hands-On:**

- Katılımcılar, GitHub arayüzünden manuel tetikleme işlemi ile iş akışını başlatacaklardır.

---

### **Senaryo 3: Farklı Ortamlarda Test Çalıştırma**

Projenizin farklı Node.js sürümleriyle test edilmesini istiyorsunuz.

#### **YAML Dosyası:**

```yaml
name: Node.js CI for Multiple Versions

on:
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [12, 14, 16]
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: ${{ matrix.node-version }}
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

#### **Açıklama:**

- `matrix.node-version`: Bu iş, farklı Node.js sürümleriyle çalışacak.
- İş akışı üç farklı Node.js sürümünde testleri çalıştıracak: 12, 14 ve 16.

**Hands-On:**

- Katılımcılar, farklı sürümlerle testlerin çalıştığı iş akışlarını oluşturacak ve sonuçları inceleyeceklerdir.

---

## **4. En İyi Uygulamalar ve Hatalardan Kaçınma**

- **YAML Dosyalarını İyi Düzenleyin:** YAML, girintiye duyarlı bir dildir. Her seviyede iki boşluk kullanmaya dikkat edin, tab karakteri kullanmamaya özen gösterin.
- **Yorumlar Ekleyin:** Özellikle karmaşık iş akışlarında, her adımın ne yaptığına dair yorumlar eklemek işleri kolaylaştırır.
- **Hata Ayıklama İçin `echo` Kullanımı:** İş akışınızda hataları tespit etmek için `echo` komutuyla değişkenlerin değerlerini yazdırabilirsiniz.
- **Secrets ve Çevresel Değişkenler:** Gizli bilgileri (API anahtarları, şifreler) `secrets` olarak saklayın ve YAML dosyasında kullanırken `${{ secrets.MY_SECRET_KEY }}` şeklinde erişin.
