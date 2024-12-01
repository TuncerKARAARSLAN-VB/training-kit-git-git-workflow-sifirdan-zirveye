# **Pull Request ve Fork Modeli: Açık Kaynak Projelerde Fork Kullanımı**

Fork modeli, özellikle açık kaynak yazılım geliştirme dünyasında, yazılımcıların projelere katkı sağlamak için kullandığı yaygın bir yöntemdir. GitHub gibi platformlarda, fork ve pull request kullanımı, yazılımcıların bir projeye katkı sağlamalarını ve yapılan değişikliklerin ana koda (upstream repository) eklenmesini kolaylaştırır. Bu süreç, özellikle projelerin bağımsız bir şekilde geliştirilmesini ve büyük bir ekip tarafından daha verimli bir şekilde yönetilmesini sağlar.

---

## **1. Fork ve Pull Request Süreci Nedir?**

Fork ve pull request süreci, dışarıdan bir geliştiricinin, bir projeye katkıda bulunmak amacıyla izlediği adımlar bütünüdür. Aşağıda bu sürecin detaylı bir açıklaması yer almaktadır.

### **a. Fork Nedir?**

Fork, bir başkasının GitHub üzerindeki depo (repository) kopyasını kendi hesabınıza almanız anlamına gelir. Bu işlem, ana projeden (upstream repository) bağımsız olarak üzerinde değişiklikler yapmanıza olanak tanır. Fork işlemi, açık kaynak projelere katkıda bulunmanın ilk adımıdır.

- **Fork Nasıl Yapılır?**  
  GitHub üzerinde bir projeyi forklamak için, projenin sayfasında "Fork" butonuna tıklamanız yeterlidir. Bu, projenin bireysel bir kopyasını sizin hesabınıza oluşturur.

### **b. Pull Request (PR) Nedir?**

Pull request (PR), forkladığınız depoda yaptığınız değişiklikleri, orijinal (upstream) depoya birleştirilmesi için göndermenizi sağlayan bir mekanizmadır. PR, takım arkadaşlarınızın veya proje sahiplerinin kodunuzu gözden geçirmesi, geri bildirimde bulunması ve onay vermesi için bir fırsat sağlar.

- **Pull Request Nasıl Yapılır?**  
  Forkladığınız projedeki değişiklikleri tamamladıktan sonra, bu değişiklikleri orijinal depoya göndermek için PR oluşturabilirsiniz. GitHub'da, "Compare & Pull Request" butonuna tıklayarak PR oluşturabilirsiniz.

---

## **2. Açık Kaynak Projelerde Fork Kullanımının Avantajları**

Fork modeli, özellikle açık kaynak projelerde birçok avantaj sağlar:

### **a. Bağımsız Geliştirme**

Forkladığınız projede bağımsız olarak geliştirme yapabilirsiniz. Ana projeye zarar vermeden yeni özellikler ekleyebilir veya hata düzeltmeleri yapabilirsiniz.

### **b. Katkıda Bulunma Kolaylığı**

Açık kaynak projelere katkıda bulunmak için, fork yaparak projeyi kendi hesabınızda geliştirebilir ve pull request ile orijinal depoya katkınızı sunabilirsiniz. Bu, yazılımcıların katkılarını kolayca paylaşmalarına olanak tanır.

### **c. Hata Ayıklama ve İyileştirme**

Forklar, yazılımcılara projeye katkıda bulunmak için kendi hatalarını ayıklama, yeni özellikler ekleme veya mevcut özellikleri iyileştirme fırsatı sunar. Projenin ana hattına katkı sağlarken, kendi fork’unuzda testler yapabilir ve hataları önceden düzeltebilirsiniz.

---

## **3. Senaryo: Açık Kaynak Bir Projeye Katkı Sağlama**

**Durum**:  
Bir geliştirici, açık kaynak bir projeye katkıda bulunmak istiyor. Bu projede bazı özelliklerin eksik olduğunu fark etti ve bu eksiklikleri gidermek için bir özellik eklemeyi planlıyor.

**Çözüm Adımları**:

1. **Fork Yapmak**:  
   GitHub üzerinde, katkı sağlamak istediğiniz projeyi bulun ve "Fork" butonuna tıklayın. Bu, projeyi sizin hesabınıza kopyalar.

2. **Yeni Bir Dal (Branch) Oluşturun**:  
   Forkladığınız projede yeni bir özellik eklemek için, öncelikle yeni bir dal oluşturun. Bu dalda sadece eklediğiniz özellikler olacak.

   ```bash
   git checkout -b yeni-ozellik
   ```

3. **Değişiklikleri Yapın**:  
   Yeni özellik ekleme işlemini gerçekleştirin. Kodda yaptığınız değişiklikleri test edin ve doğruluğundan emin olun.

4. **Commit Yapın**:  
   Yapılan değişiklikleri commit edin ve ardından uzak depoya (GitHub’a) gönderin.

   ```bash
   git add .
   git commit -m "Yeni özellik eklendi"
   git push origin yeni-ozellik
   ```

5. **Pull Request Oluşturun**:  
   GitHub üzerinden, forkladığınız projeye gidin ve "Compare & Pull Request" butonuna tıklayın. Pull request başlığına uygun bir açıklama yazın ve "Create Pull Request" butonuna tıklayarak katkınızı orijinal projeye sunun.

6. **Geri Bildirim ve Değişiklikler**:  
   Proje sahipleri ve diğer geliştiriciler, PR’ınızı gözden geçirecekler ve geri bildirimde bulunacaklardır. PR’ınızda gerekli değişiklikleri yaparak, geri bildirimleri uygulayabilirsiniz.

---

## **4. En İyi Uygulamalar**

Fork ve pull request sürecinde, bazı en iyi uygulamalar şunlardır:

### **a. Fork ve Pull Request'leri Küçük Tutun**

Her pull request, mümkün olduğunca küçük ve odaklanmış olmalıdır. Büyük PR’lar, incelemeyi zorlaştırabilir ve hataların gözden kaçmasına neden olabilir.

### **b. Açıklayıcı Commit Mesajları**

Commit mesajlarını açıklayıcı ve anlamlı tutun. Mesajlar, yapılan değişikliğin ne olduğunu açıkça anlatmalıdır.

### **c. Güncel Tutma**

Fork’unuzdaki değişiklikler orijinal depodan farklılaştıkça, fork’unuzu güncel tutmanız önemlidir. Bu, değişikliklerinizi orijinal depoya göndermeden önce çatışmaların önlenmesine yardımcı olur. Orijinal depodan en son değişiklikleri almak için aşağıdaki komutları kullanabilirsiniz:

```bash
git remote add upstream https://github.com/orijinal-depo/proje.git
git fetch upstream
git checkout main
git merge upstream/main
```

### **d. Kod İncelemeleri**

Açık kaynak projelerinde, katkı sağlanan her kodun başka geliştiriciler tarafından gözden geçirilmesi gerekir. Kod incelemeleri, yazılımın kalitesini artırır ve olası hataları erkenden yakalamaya yardımcı olur.

---

## **5. Hands-On: Fork ve Pull Request Sürecini Uygulama**

**Adım 1**: GitHub’da popüler bir açık kaynak projeyi bulun ve bu projeyi fork’layın.

**Adım 2**: Forkladığınız projede yeni bir dal oluşturun ve küçük bir özellik ekleyin (örneğin, basit bir hata düzeltme veya küçük bir yeni özellik).

**Adım 3**: Değişikliklerinizi commit edin ve uzak depoya gönderin.

**Adım 4**: GitHub’da yeni bir pull request oluşturun ve PR açıklaması yazın.

**Adım 5**: PR’iniz gözden geçirmeye alındıktan sonra, takımın geri bildirimlerini uygulayın.

---

## **6. Sonuç**

Fork modeli, açık kaynak projelerinde katkı sağlamak için en yaygın ve etkili yöntemlerden biridir. Bu model, bağımsız geliştirme yapmayı, kodu test etmeyi ve ana projeye katkıda bulunmayı kolaylaştırır. GitHub üzerinde pull request oluşturma süreci, projelerin sürdürülebilirliğini artırır ve yazılımın kalitesini garanti altına alır.
