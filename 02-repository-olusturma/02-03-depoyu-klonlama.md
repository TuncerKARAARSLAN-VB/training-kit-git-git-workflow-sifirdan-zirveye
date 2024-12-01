# **Depoyu Klonlama (Clone Repository)**

Git ile çalışırken, başkalarının projelerine katkı sağlamak veya mevcut bir projeyi kendi bilgisayarınızda çalıştırmak için bir depo klonlamak gereklidir. **Klonlama**, uzak bir Git deposunun bir kopyasını yerel bilgisayarınıza indirmenizi sağlar. Bu işlem, orijinal projeye katkı sağlamak, testler yapmak ya da değişiklikler üzerinde çalışmak için gerekli bir adımdır.

---

## **1. Depoyu Klonlama Nedir?**

Klonlama, uzak bir Git deposunun (örneğin, GitHub, GitLab veya Bitbucket üzerindeki bir depo) tamamını yerel bilgisayarınıza indirmenizi sağlayan bir işlemdir. Klonlanan depo, uzak depoyla senkronize bir şekilde çalışır; yani, bu depodaki değişiklikleri yerel bilgisayarınızda görmek, yeni değişiklikler yapıp uzak depoya göndermek mümkündür.

### **Klonlamanın Temel Adımları:**

1. Git deposunun URL’sini almak.
2. Bu URL’yi kullanarak terminal üzerinden `git clone` komutunu çalıştırmak.
3. Proje dosyalarını yerel bilgisayarınıza almak.

---

## **2. Git Deposu Klonlama İşlemi**

Depoyu klonlamak için, önce klonlamak istediğiniz deponun URL'sini almanız gereklidir. Bu URL, genellikle GitHub veya diğer platformlarda "Clone" butonuna tıklayarak elde edilir. URL, genellikle HTTPS ya da SSH protokollerini kullanır.

### **Adımlar:**

1. **Uzak Depo URL’sini Alın:**
   GitHub üzerinde bir depoyu klonlamak için, deponun sayfasına gidin ve "Code" butonuna tıklayın. Oradan HTTPS veya SSH bağlantısını kopyalayın.

   Örneğin:

   ```url
   https://github.com/username/repository.git
   ```

2. **Terminali Açın:**
   Git komutlarını kullanarak depo klonlamak için terminal veya komut satırını açın.

3. **Depoyu Klonlama:**
   Klonlamak istediğiniz depo URL’sini terminale şu komutla girin:

   ```bash
   git clone https://github.com/username/repository.git
   ```

   **Bu komut, şu işlemleri yapar:**
   - Uzak depoyu yerel bilgisayarınıza indirir.
   - Yerel bilgisayarınızda aynı adı taşıyan bir klasör oluşturur.
   - Depodaki tüm dosyaları ve geçmiş commit’leri yerel bilgisayarınıza alır.

4. **Depo Klasörüne Geçiş Yapın:**
   Klonlanan depoya gitmek için şu komutu kullanabilirsiniz:

   ```bash
   cd repository
   ```

5. **Depo İçeriğini İnceleyin:**

   Klonlanan projede herhangi bir dosya değişikliği yapmak veya inceleme yapmak için `ls` komutunu kullanarak dosya yapısını kontrol edebilirsiniz.

   ```bash
   ls
   ```

---

### **3. Uzak Depo ile Senkronizasyon**

Klonlama işlemi tamamlandıktan sonra, yerel deponuz uzak depo ile senkronize edilmeye devam eder. Yani, uzak depodaki yeni değişiklikleri yerel deponuza almak ve yerel değişikliklerinizi uzak depoya göndermek mümkündür.

#### **Adımlar:**

1. **Uzak Depodaki Değişiklikleri Almak (Pull):**
   Uzak depodaki yeni commit'leri yerel deponuza almak için şu komutu kullanabilirsiniz:

   ```bash
   git pull origin main
   ```

2. **Yerel Değişiklikleri Uzak Depoya Göndermek (Push):**
   Yerel deponuzda yapılan değişiklikleri uzak depoya göndermek için şu komutu kullanabilirsiniz:

   ```bash
   git push origin main
   ```

---

### **4. Git Deposu Klonlama Senaryoları ve Hands-On Uygulamalar**

#### **Senaryo 1: Yeni Bir Depoyu Klonlayarak Çalışmaya Başlamak**

**Durum:**  
Bir ekip olarak açık kaynak bir projeye katkıda bulunmak istiyorsunuz. Proje GitHub'da mevcut ve projeyi yerel bilgisayarınıza klonlamanız gerekiyor.

**Adımlar:**

1. GitHub üzerindeki projeyi bulun ve "Clone" butonuna tıklayarak URL'yi alın.
2. Terminali açın ve aşağıdaki komutu girin:

   ```bash
   git clone https://github.com/username/repository.git
   ```

3. Klonlanan projeye geçiş yapın:

   ```bash
   cd repository
   ```

4. Proje dosyalarını inceleyin ve üzerinde çalışmaya başlayın.

**Hands-On:**  
Eğitmenle birlikte, bir açık kaynak projeyi GitHub'dan klonlayarak yerel bilgisayarınızda çalışın. Proje dosyalarını açın ve değişiklik yapmayı deneyin.

---

#### **Senaryo 2: Klonlanan Depo ile Senkronizasyon**

**Durum:**  
Yerel bilgisayarınızda çalışmaya başladıktan sonra, uzak depodaki yeni değişiklikleri almak ve yerel değişikliklerinizi uzak depoya göndermek istiyorsunuz.

**Adımlar:**

1. Uzak depodaki yeni commit'leri almak için:

   ```bash
   git pull origin main
   ```

2. Yapılan yerel değişiklikleri uzak depoya göndermek için:

   ```bash
   git push origin main
   ```

**Hands-On:**  
Eğitmenle birlikte bir proje üzerinde çalışarak, `git pull` ve `git push` komutlarını kullanarak uzak ve yerel depolar arasındaki senkronizasyonu test edin.

---

### **5. Uzak Depo Türleri ve Klonlama Protokolleri**

Git, depolarla iletişim kurarken çeşitli protokoller kullanır. En yaygın iki protokol:

1. **HTTPS Protokolü:**
   HTTPS, kimlik doğrulama işlemleri için kullanıcı adı ve şifre gerektirir. Her işlemde şifre girmeniz gerekebilir, ancak bu işlemler güvenlidir.

2. **SSH Protokolü:**
   SSH, kimlik doğrulaması için anahtar çiftleri kullanır. Bir kez anahtarınızı yüklediğinizde, şifre girmenize gerek kalmaz.

   SSH bağlantı komutu örneği:

   ```bash
   git clone git@github.com:username/repository.git
   ```

---

### **Sonuç ve Değerlendirme**

Git deposunu klonlamak, başkalarının projeleriyle çalışırken önemli bir adımdır. Klonlama, projeleri kendi bilgisayarınıza indirmenizi sağlar ve yerel olarak üzerinde değişiklik yapıp bu değişiklikleri uzaktaki depoya gönderebilmenizi mümkün kılar. Bu işlemde kullanılan `git clone` komutu, yazılım geliştirme sürecindeki iş birliğini hızlandırır ve projeleri kolayca takip etmenizi sağlar.
