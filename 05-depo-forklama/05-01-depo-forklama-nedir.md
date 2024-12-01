# **Modül 5: Depo Forklama**

Forklama, GitHub ve diğer Git tabanlı platformlarda, açık kaynak projelere katkı sağlamak için yaygın olarak kullanılan bir yöntemdir. Forklama, bir projenin kendi kopyasını oluşturmanıza ve bu kopya üzerinde özgürce değişiklik yapmanıza olanak tanır. 

---

## **1. Forklama Nedir?**

Forklama, başka bir kullanıcıya ait bir GitHub reposunun tam bir kopyasını kendi hesabınıza kopyalamanız işlemidir. Bu, **açık kaynak projelerde** katkı sağlamak için yaygın olarak kullanılır. Forklama, orijinal projeyi bozmadan üzerinde değişiklikler yapmanıza ve yapılan değişiklikleri orijinal proje ile birleştirmenize (merge) olanak tanır.

### **Forklamanın Avantajları:**

- **Bağımsız Çalışma:** Orijinal depoya müdahale etmeden kendi kopyanız üzerinde özgürce çalışabilirsiniz.
- **Katkı Sağlama:** Fork edilen depoya yapılan değişiklikler, pull request (PR) yoluyla orijinal proje sahibine önerilebilir.
- **Riskiz Denemeler:** Orijinal proje bozulmaz; hatalarınızı sadece fork'unuzda görürsünüz.

---

## **2. Forklama ve Klonlama Arasındaki Farklar**

- **Forklama:** Bir depo, başka bir kullanıcı tarafından alınarak kendi GitHub hesabınıza kopyalanır. Forklama, genellikle açık kaynak projelerine katkı sağlamak için kullanılır.
- **Klonlama:** Bir depo, doğrudan yerel bilgisayarınıza kopyalanır ve burada değişiklik yapabilirsiniz. Klonlama, bir projeyi kendi bilgisayarınızda çalışmak için indirmeniz anlamına gelir.

### **Örnek Durum:**

- **Forklama:** Açık kaynak bir projeye katkı sağlamak istiyorsunuz. Orijinal proje GitHub üzerinde mevcut ve bu projeyi kendi GitHub hesabınıza fork'luyorsunuz. Bu şekilde, orijinal projeyi etkilemeden üzerinde çalışabilirsiniz.
- **Klonlama:** Kendi bilgisayarınızda üzerinde çalışmak istediğiniz bir GitHub projesi var. Bu projeyi kendi bilgisayarınıza klonluyorsunuz ve yerel ortamda değişiklik yapıyorsunuz.

---

## **3. Forklama ve Klonlama Adımları**

### **Forklama Adımları:**

1. **GitHub’a Giriş Yapın:** GitHub hesabınızda oturum açın.
2. **Forklamak İstediğiniz Depoyu Bulun:** Forklamak istediğiniz projeyi GitHub'da arayın.
3. **Fork Düğmesini Tıklayın:** Proje sayfasının sağ üst kısmında bulunan "Fork" butonuna tıklayın.
4. **Kendi Hesabınıza Fork Edin:** Fork butonuna tıkladığınızda, depo otomatik olarak GitHub hesabınıza kopyalanacaktır.

### **Klonlama Adımları:**

1. **Forklanmış Depoyu Klonlama:**
   - Forkladığınız projeye gitmek için GitHub hesabınızda ilgili depo sayfasına gidin.
   - Sağ üst köşede "Code" butonuna tıklayın ve URL’yi kopyalayın.

2. **Terminal veya Git Bash Üzerinden Klonlama:**
   - Kopyaladığınız URL’yi kullanarak depo bilgisini yerel bilgisayarınıza klonlayın:

     ```bash
     git clone https://github.com/username/repository.git
     ```

   - Bu komut, depo dosyalarını bilgisayarınıza indirir ve yerel bir kopyasını oluşturur.

---

## **4. Forklama Senaryosu: Açık Kaynak Katkısı**

**Senaryo:**
Bir açık kaynak projeye katkı sağlamak istiyorsunuz. Proje sahibi, projeye katkı sağlamak isteyen kullanıcıların fork yapmasını ve sonrasında pull request göndererek değişikliklerin projeye dahil edilmesini istiyor.

### **Adım Adım Çözüm:**

1. **Depoyu Forklayın:**
   - GitHub'da katkı sağlamak istediğiniz projeyi bulun.
   - Proje sayfasında "Fork" butonuna tıklayın. Proje, kendi GitHub hesabınıza kopyalanacak.

2. **Depoyu Klonlayın:**
   - Forkladığınız projeyi bilgisayarınıza klonlamak için proje sayfasında "Code" butonuna tıklayın ve URL’yi kopyalayın.
   - Terminal veya Git Bash üzerinden depo dosyalarını bilgisayarınıza klonlayın:

     ```bash
     git clone https://github.com/username/repository.git
     ```

3. **Değişiklik Yapın:**
   - Klonladığınız projede gerekli değişiklikleri yapın (yeni özellik ekleme, hata düzeltme vb.).
   - Değişikliklerinizi commit edin:

     ```bash
     git add .
     git commit -m "Fixed bug in user authentication"
     ```

4. **Pull Request Oluşturun:**
   - Yaptığınız değişikliklerin orijinal projeye dahil edilmesi için GitHub’da bir pull request oluşturun.
   - Pull request’inizi açıklayıcı bir şekilde doldurun ve proje sahibine gönderin.

### **Hands-On:**

1. **Forklama:** GitHub’da bir açık kaynak projeyi bulun ve fork'layın.
2. **Klonlama:** Forkladığınız projeyi bilgisayarınıza klonlayın.
3. **Değişiklik Yapma:** Yerel depoda değişiklik yapın ve commit edin.
4. **Pull Request Gönderme:** GitHub üzerinden orijinal projeye pull request oluşturun.

---

### **5. Fork ve Pull Request Senaryosu**

**Durum:**
Bir açık kaynak proje üzerinde çalışıyorsunuz ve projeye yeni bir özellik eklemek istiyorsunuz. Bu değişikliği, orijinal projeye göndermek için fork ve pull request kullanmanız gerekiyor.

#### **Adımlar:**

1. **Forklama:** Orijinal projeyi GitHub üzerinden kendi hesabınıza fork edin.
2. **Klonlama:** Forkladığınız projeyi bilgisayarınıza klonlayın.
3. **Özellik Ekleme:** Yeni bir özellik ekleyin (örneğin, kullanıcı kaydı için form).
4. **Commit:** Değişikliklerinizi commit edin.

   ```bash
   git add .
   git commit -m "Added user registration form"
   ```

5. **Push ve Pull Request:** Değişikliklerinizi GitHub’a gönderin ve orijinal projeye bir pull request oluşturun.

---

## **6. Sonuç**

Forklama, GitHub ve diğer Git tabanlı platformlarda açık kaynak projelere katkı sağlamak için önemli bir yöntemdir. Forklama ve klonlama arasındaki farkları anlayarak, projelerinizi güvenli bir şekilde yönetebilir ve katkılarınızı orijinal projelere etkili bir şekilde iletebilirsiniz. Bu süreç, özellikle ekip çalışması ve açık kaynak projelerde büyük önem taşır.
