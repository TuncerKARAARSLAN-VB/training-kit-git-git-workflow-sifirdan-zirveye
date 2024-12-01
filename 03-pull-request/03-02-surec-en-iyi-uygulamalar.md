# **Pull Request Oluşturma: Süreç ve En İyi Uygulamalar**

Pull request (PR) oluşturmak, yazılım geliştirme sürecinin kritik adımlarından biridir. Bir PR, yapılan değişikliklerin ana koda entegre edilmeden önce gözden geçirilmesini sağlayan bir araçtır. Bu süreç, özellikle iş birliği yapan takımlar için büyük önem taşır. PR, bir geliştiricinin yaptığı değişiklikleri gözden geçirmeyi, test etmeyi ve onaylamayı sağlayarak yazılımın kalitesinin korunmasına yardımcı olur.

---

## **1. Pull Request Oluşturma Süreci**

Pull request süreci, temel olarak aşağıdaki adımları içerir:

### **a. Yeni Bir Dal Oluşturma (Branch)**

Bir değişiklik yapmadan önce, genellikle projede mevcut ana dal (main veya master) üzerinde çalışmak yerine, **feature branch** adı verilen bir dal oluşturulur. Bu dalda yalnızca yapılacak değişiklikler bulunur.

```bash
git checkout -b yeni-ozellik
```

### **b. Değişiklikleri Yapma**

Bu yeni dalda, gerekli değişiklikler yapılır. Değişiklikler test edildikten ve çalıştığından emin olduktan sonra commit edilir.

```bash
git add .
git commit -m "Yeni özellik eklendi"
```

### **c. Değişiklikleri Uzak Depoya Gönderme**

Değişiklikler yerel ortamda kaydedildikten sonra, bu değişikliklerin uzak depoya (remote repository) gönderilmesi gerekir.

```bash
git push origin yeni-ozellik
```

### **d. Pull Request Oluşturma**

GitHub veya benzeri bir platformda, bu değişiklikler için bir pull request oluşturulur. PR oluştururken, aşağıdaki bilgileri eklemek önemlidir:

- **Başlık**: Değişiklik hakkında kısa ve öz bir açıklama.
- **Açıklama**: Yapılan değişikliklerin detaylı bir açıklaması ve neden yapıldığına dair bilgiler.
- **Etiketler ve Gözden Geçirenler**: PR’i inceleyecek kişilerin etiketlenmesi, gerektiğinde ilgili etiketlerin eklenmesi (örneğin, bug fix veya feature).

---

## **2. En İyi Uygulamalar**

Pull request oluşturma sürecinde dikkate alınması gereken en iyi uygulamalar şunlardır:

### **a. Küçük ve Anlaşılır Pull Request’ler**

Çok büyük ve karmaşık pull request’ler, incelemeyi zorlaştırır. Mümkünse, her pull request tek bir amaç için odaklanmalı ve küçük, anlaşılır parçalara ayrılmalıdır. Bu, gözden geçirenlerin hızlıca inceleme yapabilmesini sağlar.

### **b. Anlamlı Commit Mesajları**

Her commit’in amacı açık olmalıdır. Commit mesajları, yapılan değişikliği açıkça açıklamalı, böylece diğer geliştiriciler mesajları okuduklarında yapılan işin ne olduğunu anlayabilmelidir.

- **İyi örnek**: `Fixes button alignment issue in header`
- **Kötü örnek**: `Update index.html`

### **c. Kodun Gözden Geçirilmesi ve Test Edilmesi**

Pull request’i oluşturduktan sonra, takım arkadaşlarının kodu gözden geçirmesi gerekir. Yapılan değişikliklerin doğruluğunu test etmek ve herhangi bir hata veya iyileştirme önerisi almak önemlidir. 

- **Test Edilebilirlik**: Kodun test edilebilir olduğundan emin olun. Otomatik testler eklemek ve test senaryoları sağlamak iyi bir uygulamadır.
- **Kod Kalitesi**: Kodun okunabilir ve sürdürülebilir olması önemlidir. Takım standartlarına uyulması gerekir.

### **d. Çatışmaların Çözülmesi**

Pull request sırasında çatışmalar oluşmuşsa, bu çatışmaların çözülmesi gerekir. Git, çatışmaları işaretler ve geliştiricinin müdahale etmesini bekler. Çatışmalar çözülmeli ve pull request güncellenmelidir.

```bash
git pull origin main
# Çatışmaları çözün
git add .
git commit -m "Çatışmalar çözüldü"
git push origin yeni-ozellik
```

---

## **3. Senaryo: Yeni Özellik Ekleme ve Pull Request Oluşturma**

**Durum:**
Bir ekip, projeye yeni bir özellik eklemek üzere çalışıyor. Bu özellik, kullanıcıların profil bilgilerini güncelleyebileceği bir form olacak. Geliştirici, bu özelliği eklemek için bir dal oluşturacak ve pull request oluşturacak.

**Çözüm Adımları:**

1. **Yeni Dal Oluşturulacak**:

   ```bash
   git checkout -b profil-formu-ekle
   ```

2. **Değişiklik Yapılacak**: Kullanıcı profil bilgilerini güncelleyebileceği formu oluşturacak ve ilgili frontend değişikliklerini yapacak.

3. **Değişiklikler Commit Edilecek**:

   ```bash
   git add .
   git commit -m "Kullanıcı profil formu eklendi"
   ```

4. **Değişiklikler Uzak Depoya Gönderilecek**:

   ```bash
   git push origin profil-formu-ekle
   ```

5. **Pull Request Oluşturulacak**:
   GitHub’a gidilip, `Yeni Pull Request` seçeneği ile yeni bir PR oluşturulacak. PR açıklaması şu şekilde olabilir:

   - **Başlık**: `Kullanıcı Profil Formu Eklendi`
   - **Açıklama**: `Bu PR, kullanıcıların profil bilgilerini güncelleyebileceği bir formu içeriyor. Formun tasarımı ve doğrulama işlemleri tamamlandı. Lütfen gözden geçirin ve geri bildirimde bulunun.`

---

### **4. Hands-On: Pull Request Sürecini Uygulama**

**Adım 1**: Bir proje üzerinde yeni bir dal oluşturun ve bu dalda bir özellik ekleyin. Örneğin, kullanıcı profil formu gibi basit bir özellik.

**Adım 2**: Yapılan değişiklikleri commit edin ve uzak depoya gönderin.

**Adım 3**: GitHub üzerinde yeni bir pull request oluşturun. PR’in başlığını ve açıklamasını yazın.

**Adım 4**: Pull request’i incelemeleri için ekip arkadaşlarını etiketleyin.

**Adım 5**: Takım üyeleri tarafından PR’in gözden geçirilmesini bekleyin ve gerekirse çatışmaları çözün.

**Adım 6**: Pull request onaylandıktan sonra, değişikliklerin ana koda (main branch) birleştirilmesini sağlayın.

---

### **5. Pull Request İnceleme ve Birleştirme**

Pull request oluşturulduktan sonra, takım üyeleri bu değişiklikleri gözden geçirecek ve tartışacaktır. İnceleme sırasında şunlara dikkat edilmelidir:

- **Kodun Okunabilirliği**: Kod açık ve anlaşılır mı?
- **Test Edilebilirlik**: Kodun test edilebilirliği sağlanmış mı?
- **Kod Standartları**: Projeye ait kod yazım kurallarına uygun mu?

İnceleme tamamlandıktan sonra, pull request birleştirilebilir:

1. GitHub üzerinde pull request sayfasında **Merge** butonuna tıklanır.
2. Ana dal ile birleştirilir ve PR kapatılır.

---

### **Sonuç ve Değerlendirme**

Pull request oluşturma süreci, bir yazılım geliştirme projesinin düzgün ve verimli bir şekilde ilerlemesi için kritik öneme sahiptir. Bu süreç, iş birliğini teşvik eder, kod kalitesini artırır ve hataların önlenmesine yardımcı olur. İyi bir PR süreci, projenin sürdürülebilirliğini sağlar ve takım üyeleri arasında güçlü bir iletişim kurar.
