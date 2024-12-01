# **CI/CD Pipeline Örnekleri**

CI/CD (Continuous Integration / Continuous Delivery), modern yazılım geliştirme süreçlerinin temel bileşenleridir. Bu yaklaşım, yazılımın daha hızlı, güvenli ve sürdürülebilir bir şekilde geliştirilmesini sağlar.

## **1. CI/CD Nedir?**

- **Continuous Integration (CI)**: Yazılım geliştiricilerinin yaptıkları değişiklikleri sürekli olarak merkezi bir depo ile entegre etmeleri işlemidir. Her entegrasyon, otomatik testlerle kontrol edilir.
  
- **Continuous Delivery (CD)**: Entegre edilen yazılımın otomatik olarak test edilip, prodüksiyon ortamına yakın bir ortama (staging) veya doğrudan prodüksiyona gönderilmesidir.

CI/CD, geliştirme sürecini otomatikleştirir, hata oranını düşürür ve yazılım güncellemelerinin hızlı bir şekilde yapılmasını sağlar.

### **2. CI/CD Pipeline Yapısı**

Bir CI/CD pipeline’ı tipik olarak aşağıdaki aşamalardan oluşur:

1. **Kod Depolama (Source Code)**: Git gibi bir sürüm kontrol sistemi, yazılımın kaynak kodunu depolar.
2. **Build**: Kod bir araya getirilir (derlenir), bağımlılıklar çözülür ve uygulama hazır hale gelir.
3. **Test**: Kodun doğru çalışıp çalışmadığı, testler aracılığıyla kontrol edilir.
4. **Deploy**: Uygulama, bir test ortamına veya prodüksiyon ortamına dağıtılır.
5. **Monitor**: Uygulama dağıtıldıktan sonra izlenir.

### **3. GitHub Actions ile CI/CD Pipeline Örneği**

GitHub Actions, CI/CD süreçlerini otomatikleştirmek için kullanılan güçlü bir araçtır. GitHub'da depolarınız için iş akışları (workflow) yazabilir ve CI/CD pipeline'larını kolayca yönetebilirsiniz.

---

### **4. CI/CD Pipeline Örnek Senaryoları**

#### **Senaryo 1: Basit Node.js CI/CD Pipeline**

Bu örnekte, bir Node.js projesi için sürekli entegrasyon ve teslimat pipeline’ı oluşturacağız. Her `main` dalına yapılan `push` işleminden sonra, Node.js bağımlılıkları yüklenecek, testler çalıştırılacak ve uygulama staging ortamına dağıtılacaktır.

#### **YAML Dosyası (GitHub Actions)**:

```yaml
name: Node.js CI/CD

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

  deploy:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to staging server
        run: |
          echo "Deploying to staging environment"
          # Deploy commands go here
```

#### **Açıklama:**

- `on.push.branches.main`: Bu iş akışı, `main` dalına yapılan her push işleminde tetiklenecek.
- `jobs.build`: Kodun derlenmesi, bağımlılıkların yüklenmesi ve testlerin çalıştırılması adımlarını içerir.
- `jobs.deploy`: Build işlemi başarıyla tamamlandığında, staging ortamına dağıtım yapılır.

#### **Hands-on:**

1. GitHub repository’sinde yeni bir `.github/workflows/node-ci-cd.yml` dosyası oluşturun.
2. YAML dosyasını yukarıdaki örnekle doldurun.
3. `main` dalına yapılan her push işlemi sonrasında bu pipeline’ın otomatik olarak çalıştığından emin olun.

---

#### **Senaryo 2: Python Uygulaması İçin CI/CD Pipeline**

Bir Python projesinde, her commit sonrası otomatik olarak testlerin çalıştırılması ve ardından uygulamanın staging ortamına dağıtılması gerekir. Ayrıca, hatalı testlerin raporlanması gerekir.

#### **YAML Dosyası (GitHub Actions)**:

```yaml
name: Python CI/CD Pipeline

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.8'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run tests
        run: |
          pytest

  deploy:
    runs-on: ubuntu-latest
    needs: test
    steps:
      - name: Deploy to staging environment
        run: |
          echo "Deploying Python app to staging server"
          # Deploy commands go here
```

#### **Açıklama:**

- `on.push` ve `on.pull_request`: Hem `push` hem de `pull_request` olayları tetiklendiğinde bu pipeline çalışacaktır.
- `pytest`: Python testlerini çalıştırır.
- `needs: test`: Testler başarılı olduktan sonra dağıtım işlemi yapılır.

#### **Hands-on:**

1. GitHub repository’sinde `.github/workflows/python-ci-cd.yml` dosyasını oluşturun.
2. Python proje dosyanızda testler ve bağımlılıkları içeren bir `requirements.txt` dosyası bulunduğundan emin olun.
3. Her push veya pull request sonrası bu pipeline’ın çalıştığını doğrulayın.

---

#### **Senaryo 3: Çoklu Ortamda Test (Matrix Strategy)**

Farklı ortamlar için (örneğin, farklı Node.js sürümleri veya Python sürümleri) testlerin çalıştırılmasını sağlamak istiyoruz. Bu senaryoda, testlerin farklı Node.js sürümleriyle çalıştırılmasını sağlayacağız.

#### **YAML Dosyası (GitHub Actions)**:

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

- `matrix.node-version`: Bu iş, Node.js'in 12, 14 ve 16 sürümleriyle test edilecek.
- `strategy.matrix`: Çoklu sürümdeki testler paralel olarak çalışacak.

#### **Hands-on:**

1. GitHub repository’sinde `.github/workflows/node-matrix-ci.yml` dosyasını oluşturun.
2. Node.js sürümlerini test etmek için bu pipeline’ı kullanarak farklı sürümleri test edin.

---

### **5. En İyi Uygulamalar ve Hatalardan Kaçınma**

- **Pipeline’a Adım Atlamaları Ekleyin:** İş akışınızın her aşamasını açıklamak ve hata oluştuğunda ne yapılması gerektiğini belirtmek faydalıdır.
- **Bağımlılıkları İzleyin:** Testler veya build işlemleri sırasında kullanılan bağımlılıkların güncel olduğundan emin olun.
- **Branch Filtrelemeleri:** Sadece belirli dal (branch) işlemleri için pipeline tetiklemek, kaynakları verimli kullanmanıza yardımcı olur.
- **Gizli Bilgileri Koruyun:** API anahtarları ve şifreler gibi hassas bilgileri GitHub Secrets üzerinden yönetebilirsiniz.
