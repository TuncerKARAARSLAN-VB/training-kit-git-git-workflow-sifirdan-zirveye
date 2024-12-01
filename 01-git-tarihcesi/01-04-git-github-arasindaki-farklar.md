# **Git ve GitHub Arasındaki Farklar**

Git ve GitHub, yazılım geliştirme süreçlerinde sıkça karşılaşılan iki terimdir, ancak bu ikisi farklı kavramlardır ve farklı işlevlere sahiptir. Git, bir **versiyon kontrol sistemi** iken, GitHub, Git’i temel alan **bir platform**dur. Bu yazıda, Git ve GitHub arasındaki temel farkları, kullanım senaryolarını ve her birinin sağladığı faydaları detaylı bir şekilde inceleyeceğiz. Ayrıca, konu ile ilgili senaryo örnekleri ve hands-on uygulamalar da sunacağız.

---

## **1. Git Nedir?**

**Git**, bir versiyon kontrol sistemidir. Yazılımcıların projelerindeki tüm değişiklikleri takip etmelerini sağlar. Git, her değişikliği kaydederek yazılım projelerinin geçmişini izlemenize ve geçmişteki herhangi bir sürüme geri dönmenize olanak tanır. Git, **dağıtık bir versiyon kontrol sistemi** olduğu için her geliştirici kendi bilgisayarında tüm proje geçmişine erişebilir.

### **Git’in Temel Özellikleri:**

- **Dağıtık Sistem**: Her geliştirici kendi bilgisayarında tam bir kopya (repo) tutar.
- **Sürüm Kontrolü**: Her değişiklik, Git tarafından kayıt altına alınır (commit).
- **Branching (Dal) ve Merging (Birleştirme)**: Geliştiriciler paralel olarak farklı özellikler üzerinde çalışabilir, sonra bu değişiklikler ana dal ile birleştirilebilir.
- **Geriye Dönme (Rollback)**: Herhangi bir sürüme geri dönmek mümkündür.

---

## **2. GitHub Nedir?**

**GitHub**, Git’in üzerine kurulu bir platformdur. GitHub, yazılım projelerini barındırmak ve bu projelerde iş birliği yapmak için kullanılan bir **bulut tabanlı depolama platformu**dur. GitHub, Git'in sunduğu versiyon kontrolünü bulutta sunarak, projelerinizi merkezi bir yerde depolamanızı ve bir ekip olarak çalışmanızı kolaylaştırır. GitHub ayrıca kod gözden geçirme, hata takibi ve otomatikleştirilmiş iş akışları gibi bir dizi ekstra özellik de sunar.

### **GitHub’ın Temel Özellikleri:**

- **Depolama ve Barındırma**: GitHub, Git depolarınızı barındırır ve internet üzerinden erişilebilir kılar.
- **İş Birliği**: Ekipler, projeleri üzerinde aynı anda çalışabilir ve değişikliklerini (pull request) başkalarına sunabilir.
- **Açık Kaynak Katkıları**: Açık kaynak projelere kolayca katkı sağlanabilir (fork, pull request).
- **CI/CD Entegrasyonu**: GitHub Actions gibi araçlar, otomatikleştirilmiş iş akışları oluşturmanıza olanak tanır.
- **Proje Yönetimi Araçları**: Issues, Milestones, ve Project Boards gibi araçlarla proje yönetimi yapılabilir.

---

## **3. Git ve GitHub Arasındaki Temel Farklar**

### **Temel Farklar:**

| Özellik              | **Git**                                | **GitHub**                          |
|----------------------|----------------------------------------|-------------------------------------|
| **Tanım**            | Bir versiyon kontrol sistemi.          | Git’in üzerine kurulu bir bulut tabanlı platform. |
| **Veri Depolama**    | Verileri yerel bilgisayarda depolar.   | Verileri GitHub sunucularında depolar. |
| **Bağlantı**         | İnternete ihtiyaç duymadan çalışır.    | İnternet üzerinden erişim gerektirir. |
| **İş Birliği**       | Ekipler yerel olarak çalışabilir, ancak merkezi bir platform gereklidir. | Ekipler merkezi bir platformda birlikte çalışabilir. |
| **İş Akışları**      | Git ile iş akışları manuel olarak yapılır (branch, commit, merge). | GitHub, otomatikleştirilmiş iş akışlarını ve CI/CD süreçlerini destekler. |
| **Açık Kaynak**      | Git, açık kaynak projeleri destekler, ancak iş birliği gerektirir. | GitHub, açık kaynak projelere kolayca katkı yapmayı sağlar. |
| **Proje Yönetimi**   | Git, proje yönetimi için araçlar sunmaz. | GitHub, Issues ve Project Boards gibi proje yönetim araçlarına sahiptir. |

---

## **4. Senaryo Örnekleri ve Hands-On Uygulamalar**

### **Senaryo 1: Yerel Depo (Git) ve Bulut Deposu (GitHub) Kullanımı**

**Durum:**
Bir yazılım geliştirici, projeyi yerel olarak geliştiriyor ve bu projeyi GitHub’a göndermek istiyor. Burada, Git'in yerel depolama ve GitHub’ın merkezi barındırma işlevini kullanacağız.

**Adımlar:**

1. **Git ile Yerel Depo Oluşturma:**
   - Yeni bir proje dizini oluşturun ve Git deposu başlatın.

   ```bash
   mkdir my_project
   cd my_project
   git init
   ```

2. **Değişiklik Yapma ve Commit Etme:**
   - Projeye dosyalar ekleyin ve bu dosyaları Git ile commit edin.

   ```bash
   echo "print('Hello World')" > hello.py
   git add hello.py
   git commit -m "Initial commit"
   ```

3. **GitHub’da Yeni Repo Oluşturma ve Bağlantı Kurma:**
   - GitHub’da yeni bir repository oluşturun.
   - GitHub reposunun URL’sini alıp, yerel repoyu bu uzak repo ile ilişkilendirin.

   ```bash
   git remote add origin https://github.com/username/my_project.git
   git push -u origin main
   ```

**Hands-On:**
Eğitmenle birlikte GitHub üzerinde bir repo oluşturun ve yerel projeyi Git kullanarak GitHub’a gönderin.

---

### **Senaryo 2: GitHub’da Fork ve Pull Request (PR) Süreci**

**Durum:**
Bir yazılımcı, açık kaynak bir projeye katkı sağlamak istiyor. İlk olarak, projeyi fork eder, sonra değişiklik yaparak pull request gönderir.

**Adımlar:**

1. **Fork Yapma:**
   - GitHub’daki açık kaynak bir projeyi fork edin.

2. **Yerel Depoda Çalışma:**
   - Fork edilen projeyi bilgisayarınıza clone edin ve üzerinde değişiklik yapın.

   ```bash
   git clone https://github.com/username/open-source-project.git
   cd open-source-project
   ```

3. **Pull Request Gönderme:**
   - Değişiklikleri commit edip, kendi GitHub reposunda push edin ve ardından pull request açın.

   ```bash
   git add .
   git commit -m "Fixed bug in main.py"
   git push origin main
   ```

4. GitHub’daki pull request sayfasında, değişiklikleri gözden geçiren ekip üyeleri tarafından onaylanan değişiklik ana projeye dahil edilir.

**Hands-On:**
Bir açık kaynak projeyi fork edin, üzerinde değişiklik yapın ve pull request gönderin.

---

### **Senaryo 3: GitHub Actions ile CI/CD Süreci**

**Durum:**
Bir proje üzerinde çalışan ekip, her commit sonrası otomatik testlerin yapılmasını istiyor. Bunun için GitHub Actions kullanılarak basit bir CI süreci kurulur.

**Adımlar:**

1. GitHub’da projenin `.github/workflows` dizinini oluşturun.
2. `ci.yml` dosyasını oluşturup içerisine test süreçlerini tanımlayın.

```yaml
name: CI Pipeline

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
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.8'
      - name: Install dependencies
        run: |
          pip install -r requirements.txt
      - name: Run tests
        run: |
          pytest
```

3. Değişiklikleri push edin ve GitHub Actions'ın otomatik olarak test sürecini çalıştırmasını izleyin.

**Hands-On:**
Eğitmenle birlikte basit bir Python projesinde CI pipeline’ı kurarak otomatik testlerin nasıl çalıştığını gözlemleyin.

Git ve GitHub, yazılım geliştirme süreçlerinde farklı rollere sahiptir. Git, projelerin versiyon kontrolünü sağlarken, GitHub bu versiyon kontrolünü bulut tabanlı olarak yönetmenizi ve ekipler arasında iş birliğini kolaylaştırmanızı sağlar. Git ile yerel çalışma ve GitHub ile merkezi bir iş birliği yaparak daha verimli yazılım geliştirme süreçlerine imza atabilirsiniz.
