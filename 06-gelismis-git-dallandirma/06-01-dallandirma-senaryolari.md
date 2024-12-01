# **Modül 6: Gelişmiş Git Dallandırma Araçları**

## **1. Dal (Branch) Nedir?**

Dal, ana projeden (master veya main dalı) bağımsız olarak üzerinde çalışılabilen bir "kopya"dır. Dallar, yeni özellikler eklerken, hata düzeltmeleri yaparken veya deneysel kodlar yazarken kullanılır.

### **Dal Kullanım Senaryoları:**

- **Yeni Özellik Geliştirme:** Yazılım geliştiriciler, yeni bir özellik üzerinde çalışırken ana dalı bozmak yerine kendi dalında geliştirme yaparlar.
- **Hata Düzeltmeleri (Bug Fixing):** Bir hata keşfedildiğinde, ana dalı değiştirmeden yalnızca ilgili dalda hata düzeltmesi yapılabilir.
- **Kod İncelemeleri:** Kodun başkaları tarafından incelenmesi gerektiğinde, ilgili dalda değişiklikler yapılır ve bu dal daha sonra ana dal ile birleştirilir.

### **Temel Dal Komutları:**

- Yeni bir dal oluşturma:

  ```bash
  git branch yeni-ozellik
  ```

- Dal oluşturduktan sonra bu dala geçiş yapma:

  ```bash
  git checkout yeni-ozellik
  ```

- Dal oluşturma ve geçiş yapma:

  ```bash
  git checkout -b yeni-ozellik
  ```

---

## **2. Birleştirme (Merge) Nedir?**

Birleştirme, bir dalda yapılan değişikliklerin başka bir dal ile entegre edilmesi işlemidir. Genellikle, bir geliştirme dalındaki özelliklerin ana dal ile birleştirilmesi gerektiğinde kullanılır.

### **Birleştirme İşlemi:**

Birleştirme, genellikle `main` veya `master` dalına yeni bir özellik dalı eklemek için kullanılır. Birleştirme sırasında, eğer iki dalda aynı dosyada farklı değişiklikler yapılmışsa, bu çakışmalar meydana gelebilir. Bu durumda, çakışmalar manuel olarak çözülmelidir.

### **Temel Birleştirme Komutları:**

- Bir dalı ana dal ile birleştirme:

  ```bash
  git checkout main
  git merge yeni-ozellik
  ```

- Çakışmaların çözülmesi: Eğer çakışmalar varsa, dosyaları düzenleyip `git add` komutu ile çözülmüş dosyaları işaretledikten sonra, birleştirme işlemini tamamlayabilirsiniz.

  ```bash
  git commit
  ```

---

## **3. Senaryo 1: Yeni Özellik Geliştirme ve Ana Dal ile Birleştirme**

**Durum:**
Bir yazılım geliştiricisi, bir projeye yeni bir özellik eklemek istiyor ancak bu özelliğin geliştirilmesi sırasında ana dalın bozulmaması gerekiyor.

### **Çözüm:**

1. **Yeni Bir Dal Oluşturun:** Yeni özellik için bir dal oluşturun.

   ```bash
   git checkout -b yeni-ozellik
   ```

2. **Yeni Özelliği Geliştirin:** Bu dalda değişikliklerinizi yapın, testleri geçirin ve kodu yazın.

3. **Ana Dal ile Birleştirin:** Özellik tamamlandıktan sonra, `main` dalına geri geçin ve değişiklikleri birleştirin.

   ```bash
   git checkout main
   git merge yeni-ozellik
   ```

4. **Çakışma Çözümü:** Eğer çakışmalar varsa, bu çakışmaları çözün ve birleştirme işlemini tamamlayın.

5. **Değişiklikleri GitHub’a Gönderin:** Son olarak, değişiklikleri uzaktaki depoya gönderin.

   ```bash
   git push origin main
   ```

### **Hands-On:**

1. Bir proje başlatın ve yeni bir özellik dalı oluşturun.
2. Dalda çalışarak bazı değişiklikler yapın.
3. Değişiklikleri ana dal ile birleştirin ve çakışmalar varsa çözün.
4. Kodları GitHub'a gönderin.

---

## **4. Senaryo 2: Hata Düzeltmesi ve Çakışma Çözümü**

**Durum:**
Bir hata tespit edildi ve bu hatayı düzeltmek için bir dal oluşturuldu. Ancak, bu esnada başka bir geliştirici de aynı dosya üzerinde değişiklik yapmış.

### **Çözüm:**

1. **Hata Düzeltmesi Dalı Oluşturun:** Öncelikle, hata düzeltme için yeni bir dal oluşturun.

   ```bash
   git checkout -b hata-duzeltme
   ```

2. **Hata Düzeltmesini Yapın:** Hatalı kodu düzelttikten sonra, ana dala geri dönün.

   ```bash
   git checkout main
   ```

3. **Hata Düzeltme Dalını Ana Dal ile Birleştirin:** `git merge` komutunu kullanarak hata düzeltme dalını ana dal ile birleştirin.

   ```bash
   git merge hata-duzeltme
   ```

4. **Çakışmaları Çözün:** Eğer çakışmalar varsa, çakışmaları manuel olarak çözün. Çakışmalar çözüldükten sonra değişiklikleri commit edin ve push yapın.

   ```bash
   git add .
   git commit -m "Çakışmalar çözüldü"
   git push origin main
   ```

### **Hands-On:**

1. Bir hata düzeltme dalı oluşturun.
2. Ana dalda bir değişiklik yaparak çakışma oluşturun.
3. Hata düzeltme dalındaki değişiklikleri ana dal ile birleştirin ve çakışmaları çözün.
4. Sonuçları GitHub’a gönderin.

---

## **5. Gelişmiş Dallandırma Stratejileri**

Büyük projelerde, dallandırma stratejileri geliştirmek önemli bir adımdır. Geliştiricilerin birbirleriyle çakışmadan etkili bir şekilde çalışabilmesi için bu stratejiler gereklidir.

### **Örnek Dallandırma Stratejileri:**

- **Feature Branch Workflow:** Her yeni özellik için ayrı bir dal oluşturulması, her geliştirme sürecinin bağımsız olarak yapılmasını sağlar.
- **GitFlow Workflow:** Özellik dalları, geliştirme dalları, sürüm dalları ve yama dallarından oluşan kapsamlı bir çalışma akışıdır.
- **Forking Workflow:** Her geliştiricinin projeyi forkladığı ve kendi fork'larında çalışarak sonunda orijinal depoya pull request göndermeyi içerir.

---

## **Sonuç**

Git dalları ve birleştirme işlemleri, yazılım geliştirmede büyük esneklik ve verimlilik sağlar. Doğru dallandırma stratejileri kullanılarak, geliştiriciler birbirlerinin işlerine müdahale etmeden bağımsız olarak çalışabilirler. Bu modülde, dallandırma ve birleştirme temelleri ile ilgili senaryoları ve en iyi uygulamaları öğrendiniz. Bu bilgileri gerçek projelerde kullanarak daha etkili bir yazılım geliştirme süreci oluşturabilirsiniz.
