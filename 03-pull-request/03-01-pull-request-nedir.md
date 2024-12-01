# **Pull Request Nedir?**

Pull Request (PR), yazılım geliştirme sürecinde bir kullanıcı tarafından yapılan değişikliklerin, başkaları tarafından gözden geçirilmesi ve projeye dahil edilmesi için yapılan bir istektir. Bu, özellikle birden fazla geliştiriciyle çalışan projelerde önemli bir iş birliği aracıdır. Pull Request’ler, **değişikliklerin tartışılması**, **kod gözden geçirmesi** ve **geliştirilen yeni özelliklerin ana koda entegrasyonu** sürecini yönetir.

---

## **1. Pull Request'in Temel Amacı**

Pull Request’in temel amacı, yapılan değişikliklerin doğru ve etkili bir şekilde projeye dahil edilmesini sağlamaktır. Bu süreç aşağıdaki adımları içerir:

- **Kod Gözden Geçirme**: Diğer geliştiriciler, yapılan değişiklikleri inceleyerek kodun kalitesini değerlendirir.
- **İletişim ve Tartışma**: Değişikliklerle ilgili fikir alışverişi yapılabilir. PR üzerinden yorumlar yapılarak iyileştirmeler önerilebilir.
- **Test ve Onay**: Yapılan değişikliklerin doğru çalıştığından emin olmak için testler yapılır. Değişiklikler onaylandığında ana projeye dahil edilir.

---

## **2. Pull Request Süreci**

Bir pull request oluşturulmadan önce, genellikle aşağıdaki adımlar takip edilir:

1. **Yeni Bir Dal (Branch) Oluşturmak**: Öncelikle, projede yapılacak değişiklikler için bir dal oluşturulur. Bu dal, ana koda (main veya master) zarar vermeden yapılan geliştirmelerin uygulanacağı yerdir.

   ```bash
   git checkout -b yeni-ozellik
   ```

2. **Kod Değişikliklerini Yapmak**: Geliştirici, bu dalda gerekli değişiklikleri yapar.

3. **Değişiklikleri Yerel Depoya Commit Etmek**: Yapılan değişiklikler yerel depoya commit edilir.

   ```bash
   git add .
   git commit -m "Yeni özellik eklendi"
   ```

4. **Değişiklikleri Uzak Depoya Göndermek (Push)**: Yapılan değişiklikler uzak depoya gönderilir.

   ```bash
   git push origin yeni-ozellik
   ```

5. **Pull Request Oluşturmak**: GitHub veya benzeri bir platformda, uzak depoya gönderilen bu dal için bir pull request oluşturulur.

---

## **3. Pull Request İle Çalışma**

Pull request’lerin işlevi sadece birleştirme (merge) değil, aynı zamanda ekip üyeleri arasındaki iş birliğini, kod kalitesini ve sürdürülebilirliği artırmaktır.

### **a. Pull Request Oluşturma (GitHub Örneği)**

1. GitHub üzerinde projeyi açın ve `New Pull Request` butonuna tıklayın.
2. Hangi dalın hangi dala birleştirileceğini seçin. Genellikle, geliştirme dalınız (`feature branch`) `main` dalına birleştirilecektir.
3. Pull request’in başlığı ve açıklaması eklenir. Burada yapılan değişiklikler özetlenir.
4. Pull request oluşturulup, proje sahiplerine veya takım üyelerine inceleme için gönderilir.

---

## **4. Pull Request’in Ortak Çalışmadaki Rolü**

Pull request'ler, ortak çalışmada şu temel rolleri oynar:

- **Kod Gözden Geçirme**: Bir geliştirici tarafından yapılan değişiklikler, başka bir geliştirici tarafından gözden geçirilir. Kod gözden geçirme, hata bulma, güvenlik açıklarını kapatma ve kod kalitesini artırma sürecidir.
- **İletişim ve İş Birliği**: Takım üyeleri, pull request üzerinden değişiklikler hakkında yorum yapabilir, önerilerde bulunabilir ve tartışabilir. Bu, takımın iletişimini geliştirir.
- **Test ve Süreklilik**: Pull request’in test edilmesi, yeni özelliklerin projeye sorunsuz bir şekilde entegre edilmesini sağlar. Entegrasyon testleri, pull request’in başarılı bir şekilde tamamlanıp tamamlanmadığını kontrol eder.
- **Sürüm Yönetimi**: Yeni özellikler veya düzeltmeler, ana koda (main branch) birleştirildiğinde, proje sürümü güncellenir ve yazılım geliştirme sürecinin doğru bir şekilde takip edilmesi sağlanır.

---

## **5. Senaryo: Pull Request ile Yeni Özellik Eklemek**

**Durum:**  
Bir ekip üyesi, bir projeye yeni bir özellik ekledi ve bu değişikliği ana koda dahil etmek istiyor. Yeni özelliklerin projeye entegrasyonu için bir pull request oluşturulacak.

**Çözüm Adımları:**

1. **Yeni Dal Oluşturulacak**:

   ```bash
   git checkout -b yeni-ozellik
   ```

2. **Değişiklik Yapılacak**: `yeni-ozellik` dalında gerekli değişiklikler yapılır.

3. **Değişiklikler Commit Edilecek**:

   ```bash
   git add .
   git commit -m "Yeni özellik eklendi"
   ```

4. **Değişiklikler Uzak Depoya Gönderilecek**:

   ```bash
   git push origin yeni-ozellik
   ```

5. **GitHub’da Pull Request Oluşturulacak**:
   - GitHub’a gidin ve `Pull Request` sekmesine tıklayın.
   - Ana dal (main) ve yeni dal (feature branch) arasındaki farkı gösteren PR oluşturulacak.
   - Pull request başlığı ve açıklaması eklenip, takım üyelerine inceleme için gönderilecek.

---

## **6. Pull Request İnceleme ve Birleştirme**

Pull request oluşturulduktan sonra, takım üyeleri bu değişiklikleri gözden geçirecek ve tartışacaktır. Gözden geçirme sürecinde dikkate alınması gerekenler şunlardır:

- **Kodun Okunabilirliği**: Değişiklikler, anlaşılabilir ve bakımı kolay mı?
- **Kodun Test Edilebilirliği**: Yapılan değişiklikler test edilebilir mi?
- **Performans**: Değişiklikler, uygulamanın performansını etkiler mi?
- **Güvenlik**: Değişiklikler güvenlik açıklarına yol açar mı?

Eğer değişiklikler onaylanırsa, pull request şu şekilde birleştirilir:

1. GitHub üzerindeki pull request sayfasında **Merge** butonuna tıklanır.
2. Geliştirilen özellik, ana koda dahil edilir ve PR kapanır.

**Hands-On:**
Eğitmenle birlikte, bir projeye yeni bir özellik ekleyin ve PR oluşturun. PR’in gözden geçirilmesi, yorumlar yapılması ve sonunda birleştirilmesi süreçlerini uygulamalı olarak deneyimleyin.

---

## **7. Pull Request'te Çatışma Çözme**

Bir pull request oluşturulduğunda, başka biri de aynı dosyada değişiklik yapmışsa çatışmalar oluşabilir. Git, bu çatışmaları otomatik olarak çözemez ve geliştiriciden müdahale isteyebilir. Bu durumda çatışmayı çözmek için şu adımlar takip edilir:

1. **Çatışmayı Çekmek (Pull)**:

   ```bash
   git pull origin main
   ```

2. **Çatışma Olan Dosyayı Düzenlemek**: Git, hangi satırlarda çatışma olduğunu belirtir. Çatışan satırları manuel olarak düzenleyin.

3. **Değişiklikleri Commit Etmek**:

   ```bash
   git add .
   git commit -m "Çatışmalar çözüldü"
   ```

4. **Pull Request’i Güncellemek**:
   Çatışmalar çözüldükten sonra, pull request’i tekrar güncelleyebilir ve birleştirilmek üzere gönderebilirsiniz.

---

## **Sonuç ve Değerlendirme**

Pull request'ler, yazılım geliştirme sürecinde kritik bir rol oynar. Bu araç, takım üyeleri arasında iş birliğini teşvik eder, kod kalitesini artırır ve değişikliklerin dikkatlice gözden geçirilmesini sağlar. Pull request’ler, değişikliklerin projeye entegrasyonunu yönetmek için vazgeçilmez bir yöntemdir ve özellikle büyük projelerde sürüm kontrolünü daha etkili hale getirir.
