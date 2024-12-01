# **Uzak Depo Ayarları (Remote Repository Settings)**

Git, yerel ve uzak depolar arasında sürekli bir bağlantı sağlar. Bu bağlantı, takım üyeleri arasında iş birliği yapmayı ve projeleri senkronize etmeyi kolaylaştırır. Uzak depolar, genellikle GitHub, GitLab veya Bitbucket gibi platformlarda barındırılır. Git ile çalışırken, uzak depolarla etkileşimde bulunmak için bazı ayarlar yapmanız gerekebilir.

---

## **1. Uzak Depo Nedir?**

Uzak depo, projelerinizi internete veya ağınıza bağlı bir sunucuda barındıran ve diğer kullanıcılarla paylaştığınız bir Git deposudur. Yerel depolarınız (bilgisayarınızda bulunan) ile bu uzak depolar arasındaki etkileşimle projelerinizi geliştirebilir ve iş birliği yapabilirsiniz.

### **Uzak Depo Özellikleri:**

- **Yedekleme**: Projenizin bir kopyası her zaman uzak depoda saklanır.
- **İşbirliği**: Birden fazla kişi, projeyi uzak depodan çekebilir (pull) ve değişiklik yapıp geri gönderebilir (push).
- **Versiyon Kontrolü**: Tüm proje geçmişi, uzak depoda da saklanır.

---

## **2. Uzak Depo Ekleme**

Yeni bir uzak depo eklemek, yerel deponuz ile uzak bir depo arasındaki bağlantıyı kurmanıza olanak tanır. Bu işlemde uzak depoları tanımlamak için `git remote` komutları kullanılır.

### **Uzak Depo Ekleme Adımları:**

1. **Uzak Depo URL’si Alın:**
   GitHub veya başka bir Git platformunda bir depo oluşturduğunuzda, depo sayfasında "Clone or Download" butonunu tıklayarak URL’yi alabilirsiniz.
   Örneğin:

   ```bash
   https://github.com/username/repository.git
   ```

2. **Uzak Depo Ekleme:**

   Uzak depo eklemek için şu komutu kullanabilirsiniz:

   ```bash
   git remote add origin https://github.com/username/repository.git
   ```

   Burada, `origin` uzak deponun adıdır (genellikle varsayılan olarak kullanılır). `origin` yerine başka bir ad da verebilirsiniz.

---

## **3. Uzak Depo Bağlantısını Kontrol Etme**

Bağlantı kurduktan sonra, uzak depo ayarlarınızı kontrol etmek için `git remote -v` komutunu kullanabilirsiniz.

```bash
git remote -v
```

Bu komut, uzak depo URL’lerini ve bağlantıları gösterir.

**Çıktı Örneği:**

```
origin  https://github.com/username/repository.git (fetch)
origin  https://github.com/username/repository.git (push)
```

---

## **4. Uzak Depo İle Çalışma**

Uzak depo ile etkileşim kurmak için aşağıdaki temel işlemleri yapabilirsiniz:

### **a. Değişiklikleri Uzak Depoya Göndermek (Push)**

Yerel deponuzda yaptığınız değişiklikleri uzak depoya göndermek için `git push` komutunu kullanırsınız.

**Komut:**

```bash
git push origin main
```

Bu komut, yerel `main` dalındaki değişiklikleri uzak `origin` deposuna gönderir.

**Senaryo:**
Bir proje üzerinde çalışıyorsunuz ve yerel değişikliklerinizi uzak GitHub deposuna göndermek istiyorsunuz. Aşağıdaki adımları takip ederek bunu gerçekleştirebilirsiniz:

1. **Yerel değişikliklerinizi ekleyin:**

   ```bash
   git add .
   git commit -m "Değişiklikler eklendi"
   ```

2. **Değişiklikleri uzak depoya gönderin:**

   ```bash
   git push origin main
   ```

**Hands-On:**
Eğitmenle birlikte, kendi yerel deponuzda değişiklik yapın, bu değişiklikleri uzak bir depoya (örneğin GitHub) gönderin.

### **b. Uzak Depodaki Değişiklikleri Çekmek (Pull)**

Uzak depodaki son değişiklikleri yerel bilgisayarınıza almak için `git pull` komutunu kullanabilirsiniz.

**Komut:**

```bash
git pull origin main
```

Bu komut, uzak deponun `main` dalındaki değişiklikleri yerel deponuza çeker.

**Senaryo:**
Başka bir ekip üyesi projeye yeni bir özellik ekledi ve uzak depoya gönderdi. Şimdi, bu yeni özellikleri kendi yerel deponuza çekmeniz gerekiyor.

**Adımlar:**

1. Uzak depodaki değişiklikleri almak için:

   ```bash
   git pull origin main
   ```

**Hands-On:**
Bir projede yerel ve uzak depo arasında değişiklikleri çekme ve gönderme işlemlerini uygulayın.

---

## **5. Uzak Depo ile Senkronizasyon**

Yerel ve uzak depolar arasında senkronizasyon, projeyi güncel tutmak için önemlidir. Eğer çok sayıda kişi projeye katkı sağlıyorsa, düzenli olarak `git pull` ve `git push` komutları kullanılarak değişiklikler yerel ve uzak depolar arasında aktarılır.

### **Çakışmaları Çözme:**

Çakışmalar, iki farklı kullanıcı aynı dosyayı değiştirip farklı commit’lerle uzak depoya göndermeye çalıştığında ortaya çıkar. Bu durumda, çakışmaları çözmek için şu adımlar izlenir:

1. **Değişiklikleri çekin:**

   ```bash
   git pull origin main
   ```

2. **Çakışmaları çözün**: Git, çakışmaların olduğu dosyaları işaretler. Çakışmaları manuel olarak düzenleyin.
3. **Düzeltilmiş dosyaları ekleyin ve commit yapın**:

   ```bash
   git add .
   git commit -m "Çakışmalar çözüldü"
   ```

4. **Değişiklikleri uzak depoya gönderin**:

   ```bash
   git push origin main
   ```

---

### **6. Uzak Depo Değişikliklerini Güncelleme (Fetch)**

`git fetch`, uzak depodaki değişiklikleri yerel bilgisayarınıza getirir, ancak bu değişiklikleri otomatik olarak yerel dalınıza uygulamaz. Yalnızca uzak depodaki son güncellemeleri görmek için kullanılır.

**Komut:**

```bash
git fetch origin
```

**Senaryo:**
Uzak depoda bir güncelleme yapıldı ama bu güncellemeyi yerel dalınıza uygulamak istemiyorsunuz. Yalnızca uzak depoyu güncellemek için `git fetch` komutunu kullanabilirsiniz.

---

### **7. Uzak Depo URL’sini Değiştirme (Remote URL Update)**

Uzak depo URL'sini değiştirmek gerekebilir, örneğin bir projeyi başka bir sunucuya taşımak ya da HTTPS'den SSH'ye geçmek.

**Komut:**

```bash
git remote set-url origin https://github.com/newusername/newrepository.git
```

Bu komut, uzak depodaki URL’yi günceller ve yeni URL üzerinden işlem yapmanıza olanak tanır.

---

### **Sonuç ve Değerlendirme**

Uzak depo ayarları, yazılım geliştirme sürecinin önemli bir parçasıdır ve Git ile yerel bilgisayarınız ile uzak depolar arasında sorunsuz bir şekilde veri aktarımı sağlar. Uzak depolar sayesinde, birden fazla kişi projeye katkıda bulunabilir, değişiklikleri takip edebilir ve iş birliği yapabilir. Git komutları ile uzak depo yönetimi, yazılım geliştirme süreçlerini daha düzenli ve verimli hale getirir.
