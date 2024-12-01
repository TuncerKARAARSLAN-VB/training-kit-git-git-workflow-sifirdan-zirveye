# **GitHub Actions’a Giriş**

GitHub Actions, yazılım geliştirme süreçlerini otomatikleştirmek için kullanılan güçlü bir araçtır. Sürekli entegrasyon (CI), sürekli teslimat (CD) ve yazılım geliştirme işlemleri boyunca birçok farklı görevin otomatikleştirilmesine olanak tanır. GitHub Actions sayesinde, yazılım projelerinde testleri çalıştırmak, uygulamaları dağıtmak, kodu analiz etmek, güvenlik taramaları yapmak ve daha pek çok işlemi otomatikleştirebilirsiniz.

---

## **1. GitHub Actions Nedir?**

GitHub Actions, GitHub üzerinde depolar için **iş akışları (workflows)** oluşturmanıza olanak tanır. Bu iş akışları, çeşitli eylemler (actions) içerir ve bu eylemler belirli olaylara tepki olarak çalıştırılır. GitHub Actions, CI/CD (Sürekli Entegrasyon/Sürekli Teslimat) süreçlerinin kolayca otomatikleştirilmesini sağlar ve bunun yanında pek çok farklı senaryo için uygun yapılandırmalar sunar.

### **Ana Bileşenler:**

- **Workflow:** İş akışı, belirli bir işlemi gerçekleştiren bir veya birden fazla adım (steps) içerir.
- **Actions:** İş akışlarında kullanılan, belirli bir görevi yerine getiren, tekrar kullanılabilir kod bloklarıdır. Örneğin, bir test çalıştırma, uygulama dağıtımı yapma gibi görevler.
- **Events:** GitHub Actions iş akışını tetikleyen olaylardır. Örneğin, bir commit yapıldığında, pull request oluşturulduğunda veya bir issue oluşturulduğunda tetiklenebilir.
- **Jobs:** Bir iş akışındaki farklı adımlardan oluşan bir gruptur ve paralel veya sırasıyla çalıştırılabilir.
- **Runners:** GitHub Actions’ın iş akışlarını çalıştırdığı sanal makineler veya konteynerlerdir.

---

## **2. GitHub Actions’ın Temel Özellikleri ve Kullanım Alanları**

### **a. Sürekli Entegrasyon (CI):**

- GitHub Actions, her commit ve pull request ile birlikte otomatik olarak testlerinizi çalıştırabilir. Bu, yazılım geliştirme sürecindeki hataları erken aşamada tespit etmenizi sağlar.

### **b. Sürekli Teslimat (CD):**

- GitHub Actions, her başarılı build'den sonra yazılımınızı otomatik olarak dağıtabilir. Böylece yazılımınız her zaman üretime hazır hale gelir.

### **c. Otomatik Bildirimler ve Görevler:**

- GitHub Actions, belirli bir işin tamamlanıp tamamlanmadığını bildiren otomatik e-posta ve Slack mesajları gönderebilir.

### **d. Kod Kalitesi ve Güvenlik Testleri:**

- Kodunuzu analiz etmek için otomatik araçlar (linting, güvenlik taramaları vb.) çalıştırabilir ve hatalı kodun projeye dahil edilmesini engelleyebilirsiniz.

---

## **3. GitHub Actions Workflow Yapısı**

GitHub Actions iş akışları, `.github/workflows` dizininde yer alan YAML dosyalarında tanımlanır. Bir iş akışının genel yapısı şu şekilde olabilir:

```yaml
name: CI/CD Workflow

on:
  push:
    branches:
      - main
  pull_request:
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

### **Açıklama:**

- **on:** Olaylar (events) kısmı, iş akışının tetikleneceği durumu tanımlar (örneğin, `push` veya `pull_request`).
- **jobs:** Her iş akışı bir veya daha fazla `job` içerir. Bir job, bir veya birden fazla adımı içerir.
- **runs-on:** İşin hangi ortamda çalışacağını belirtir (örneğin, `ubuntu-latest`, `windows-latest`).
- **steps:** İş adımlarını belirtir. Bu adımlar sırasıyla çalıştırılır.

---

## **4. GitHub Actions’a İlk Adım**

### **a. Basit Bir Workflow Oluşturmak**

1. GitHub repo’nuzda `.github/workflows` dizinini oluşturun.
2. Bu dizin içinde bir YAML dosyası oluşturun, örneğin `ci.yml`.
3. Aşağıdaki gibi basit bir CI iş akışı tanımlayın:

```yaml
name: Simple CI

on:
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Check out code
        uses: actions/checkout@v2
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.x'
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run tests
        run: pytest
```

**Hands-On:**
- Katılımcılar, kendi GitHub reposunda bir workflow dosyası oluşturacak ve basit bir CI süreci kuracaklardır. Bu süreç, bir push (yeni commit) sonrası otomatik test çalıştırma işlevi görür.

---

## **5. GitHub Actions’ta Kullanılan Bazı Popüler Actions**

- **actions/checkout:** Kodunuzu checkout etmek için kullanılır. Çoğu iş akışında ilk adım olarak bulunur.
- **actions/setup-node:** Node.js için ortam kurulumunu yapar.
- **actions/setup-python:** Python ortamını kurar.
- **actions/cache:** Build sürelerini azaltmak için bağımlılıkları önbelleğe alır.
- **docker/build-push-action:** Docker image’ları inşa eder ve bir Docker registry'ye push eder.
- **slackapi/slack-github-action:** GitHub Actions ile Slack entegrasyonu sağlar.

---

## **6. Senaryolar ve Hands-On Çalışmalar**

### **Senaryo 1: Basit CI/CD Süreci Kurulması**

**Durum:**  
Bir Node.js projesinde, her push işleminde testlerin otomatik olarak çalıştırılması ve başarılıysa üretime dağıtım yapılması gerekmektedir.

**Çözüm:**  
GitHub Actions ile basit bir CI/CD iş akışı oluşturulur. GitHub Actions, her push işlemi sonrasında testleri çalıştırır ve başarılı testlerden sonra uygulamayı üretime aktarır.

**Hands-On:**

- Katılımcılar, bu adımları uygulayarak, kendi projelerinde testlerin otomatik olarak çalıştırıldığı bir iş akışı oluşturur.

---

### **Senaryo 2: Farklı Ortamlarda Testler Çalıştırmak**

**Durum:**  
Projenizin birden fazla Python versiyonunda test edilmesi gerekiyor.

**Çözüm:**  
GitHub Actions iş akışı, `actions/setup-python` ile farklı Python sürümleri kurulacak ve testler her sürüm için çalıştırılacaktır.

**Hands-On:**

- Katılımcılar, birden fazla Python sürümü kullanarak testleri çalıştıracak ve sonuçları karşılaştıracaktır.

---

## **7. En İyi Uygulamalar**

- **Temiz ve Modüler Workflow'lar:** İş akışlarını küçük ve anlamlı parçalara ayırın. Bu, yönetimi ve bakımını kolaylaştırır.
- **Cache Kullanımı:** Bağımlılıkları önbelleğe alarak işlem sürelerini önemli ölçüde azaltabilirsiniz.
- **Gizli Veriler:** API anahtarları ve şifreler gibi hassas verileri GitHub Secrets kullanarak güvenli bir şekilde yönetin.
- **İyi Kapsamlı Testler:** CI/CD süreçlerini başlatmadan önce yeterli test kapsamına sahip olun. Bu, hataların erkenden tespit edilmesine yardımcı olur.
