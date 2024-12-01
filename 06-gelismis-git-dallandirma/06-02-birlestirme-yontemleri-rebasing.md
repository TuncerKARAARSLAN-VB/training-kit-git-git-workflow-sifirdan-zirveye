# **Birleştirme Yöntemleri: Fast-Forward, 3-Yönlü Birleştirme, Rebasing**

## **1. Fast-Forward Birleştirme (Fast-Forward Merge)**

**Fast-Forward Merge**, eğer bir dal, ana daldaki en son commit’e kadar doğrusal olarak ilerliyorsa kullanılır. Yani, başka bir deyişle, ana daldaki değişikliklerin üzerine eklenen değişiklikler varsa ve bu değişiklikler herhangi bir çakışma yaratmıyorsa, Git sadece baştaki dalın `HEAD`'ini ilerletir. Bu, genellikle bağımsız çalışarak ana daldan en son commit’ten sonra dalın ilerlediği durumlarda kullanılır.

### **Fast-Forward Birleştirme Senaryosu**

**Durum:**
Bir geliştirici, `feature-xyz` adında bir dal üzerinde çalıştı ve hiç kimse `main` dalına yeni bir şey eklemedi.

### **Çözüm:**

1. **Yeni Bir Dal Oluşturun:**

   ```bash
   git checkout -b feature-xyz
   ```

2. **Feature üzerinde değişiklik yapın ve commit edin.**

   ```bash
   git add .
   git commit -m "Feature xyz implement edildi"
   ```

3. **Ana Dala Geçin ve Fast-Forward Birleştirme Yapın:**

   ```bash
   git checkout main
   git merge feature-xyz
   ```

4. **Sonuç:**
   Git, `main` dalındaki commit geçmişini değiştirmeden sadece `HEAD`'i `feature-xyz` dalına ilerletir. Bu, herhangi bir merge commit’i oluşturmadan basit bir ilerleme ile birleştirme sağlar.

### **Hands-On:**

1. Ana dalda bir proje başlatın.
2. `feature-xyz` adında bir dal oluşturun.
3. Bu dalda bazı değişiklikler yapın.
4. `git merge` komutunu kullanarak ana dala fast-forward birleştirmesi yapın.

---

## **2. 3-Yönlü Birleştirme (3-Way Merge)**

**3-Yönlü Birleştirme**, birleştirilmek istenen dallarda farklı değişiklikler yapılmışsa ve bu değişikliklerin birbiriyle çakışması varsa, Git bir **3-yönlü birleştirme** gerçekleştirir. Burada, üç farklı noktadan bilgi alınır:

- **Common Ancestor (Ortak Ata):** Her iki dalın temel aldığı son ortak commit.
- **HEAD (Ana Dal):** Ana dalda yapılan değişiklikler.
- **Branch (Feature Dalı):** Özellik dalındaki değişiklikler.

Bu durumda, Git her iki dalda yapılan değişiklikleri karşılaştırarak uygun şekilde birleştirir ve eğer çakışmalar varsa bu çakışmaları kullanıcıya bildirir.

### **3-Yönlü Birleştirme Senaryosu**

**Durum:**
Bir geliştirici `feature-xyz` dalında çalışırken, başka bir geliştirici aynı dosyada `main` dalında değişiklik yaptı. Bu durumda, `feature-xyz` dalını `main` dalı ile birleştirirken çakışmalar olacaktır.

### **Çözüm:**

1. **Ana Dalda Çalışan Diğer Geliştirici Değişiklik Yapsın.**

2. **Kendi Özellik Dalınızı Oluşturun ve Değişiklik Yapın.**

3. **Ana Dal ile Birleştirme Yapın:**

   ```bash
   git checkout main
   git merge feature-xyz
   ```

4. **Çakışmalar:** 

   Eğer dosyada çakışmalar varsa, Git bu dosyayı "çakışmış" olarak işaretler. Çakışmaları manuel olarak düzenleyin.

   ```bash
   git add dosya.txt
   git commit -m "Çakışma çözüldü"
   ```

### **Hands-On:**

1. `main` dalında bazı değişiklikler yapın.
2. `feature-xyz` dalını oluşturun ve farklı değişiklikler yapın.
3. Çakışmayı tetiklemek için her iki dalı birleştirmeyi deneyin.
4. Çakışmaları çözün ve değişiklikleri commit edin.

---

## **3. Rebasing (Yeniden Temellendirme)**

**Rebasing**, bir dalı başka bir dalın üzerine “yeniden temellendirme” işlemidir. Bu işlem, dalları birleştirmek yerine, bir dalın commit’lerini başka bir dalın en son commit’inin üzerine taşıyarak "temiz" bir commit geçmişi oluşturur. Rebasing, genellikle feature dalındaki commit’lerin ana dalın en son commit’inden sonra sıralanmasını sağlamak amacıyla kullanılır.

### **Rebasing Senaryosu**

**Durum:**
Bir geliştirici, `feature-xyz` dalında bir dizi değişiklik yaptı. Bu esnada, başka bir geliştirici `main` dalında bazı değişiklikler yaptı ve `feature-xyz` dalı ile ana dal arasındaki geçmiş farklılaştı. Burada `rebase` kullanarak geçmişi düzeltmek faydalıdır.

### **Çözüm:**

1. **Feature Dalında Çalışın ve Değişiklik Yapın.**

2. **Ana Dalı Güncel Tutun (Rebase):**

   ```bash
   git checkout feature-xyz
   git fetch origin
   git rebase origin/main
   ```

   Bu komut, `feature-xyz` dalındaki commit’leri, `main` dalının son commit’inin üzerine alır. Eğer çakışmalar varsa, Git çakışmaları bildirir ve kullanıcıya çözme şansı tanır.

3. **Birleştirme Yapın:** 
   Rebasing işlemi tamamlandıktan sonra, feature dalını ana dal ile birleştirebilirsiniz:

   ```bash
   git checkout main
   git merge feature-xyz
   ```

4. **Sonuç:**
   Rebase işlemi, daha temiz ve doğrusal bir commit geçmişi sağlar. Ancak, rebase işleminden sonra uzak depoya push yapmadan önce, diğer geliştiricilerin dalı üzerinde çalışmadığından emin olmalısınız.

### **Hands-On:**

1. `feature-xyz` dalında bazı değişiklikler yapın.
2. `main` dalında başka değişiklikler yapın.
3. `git rebase` komutunu kullanarak feature dalını main dalının üzerine alın.
4. Rebasing işleminden sonra ana dala birleştirme yapın.

---

## **Özet: Birleştirme Yöntemleri**

- **Fast-Forward Merge:** Eğer dallarda çakışma yoksa ve dal doğrusal olarak ilerlemişse, Git yalnızca `HEAD`’i günceller. Bu, hızlı ve temiz bir birleştirme sağlar.
- **3-Yönlü Birleştirme:** İki dalda değişiklikler yapılmışsa ve çakışmalar varsa, Git her iki dalın geçmişini karşılaştırarak çakışmaları çözer.
- **Rebasing:** Bir dalın commit’lerini başka bir dalın üzerine sıralayarak doğrusal bir commit geçmişi oluşturur. Bu, commit geçmişini temiz tutmak için kullanılır ancak dikkatli kullanılmalıdır.

Bu yöntemler, yazılım geliştirme sürecinde farklı senaryolara göre en uygun birleşme yöntemini seçmenizi sağlar. Her bir yöntem, belirli bir ihtiyaç doğrultusunda geliştirme sürecini daha verimli hale getirebilir.
