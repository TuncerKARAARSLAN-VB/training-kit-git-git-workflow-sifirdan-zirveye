# **Commit’leri Birleştirme (Squashing) – Git ile Temiz ve Düzenli Bir Geçmiş Oluşturma**

Git'te commit'leri birleştirme (squashing), birkaç küçük ve anlamlı commit’i tek bir büyük commit’e dönüştürmek için kullanılır. Bu işlem, genellikle bir dizi küçük değişiklik, düzeltme veya iyileştirme yaptıktan sonra, bu değişiklikleri tek bir commit’te birleştirmek için kullanılır. Bu sayede commit geçmişi daha temiz ve anlaşılır olur.

Commit’leri birleştirme işlemi, yazılım geliştirme süreçlerinde kodun kalitesini ve takım içindeki iş birliğini artırır. Özellikle açık kaynak projelerde ve takım projelerinde, tek bir commit mesajı ile birden fazla küçük değişikliği birleştirmek önemlidir.

---

## **1. Commit’leri Birleştirme (Squashing) Nedir?**

Squashing, birden fazla commit’i tek bir commit’e dönüştürme işlemidir. Bu işlem, gereksiz commit'lerden kaçınmak ve commit geçmişini daha şeffaf hale getirmek için faydalıdır. Squashing, genellikle:

- **Birden fazla düzeltmeyi** tek bir commit’e indirgemek,
- **Kod düzenlemelerini** daha anlamlı ve tek bir commit olarak sunmak,
- **Komple bir özelliği veya işlevi** tek bir commit altında toplamak için kullanılır.

Squashing işlemi, `git rebase -i` komutu ile yapılır.

---

## **2. Commit’leri Squash Yaparak Birleştirme Adımları**

### **Adım 1: Interaktif Rebase Başlatma**

Commit’leri birleştirmeye başlamadan önce, geçmiş commit’leri gözden geçireceğiz. Bunun için interaktif rebase kullanacağız.

Örneğin, son 5 commit’i birleştirmek için aşağıdaki komutu kullanabilirsiniz:

```bash
git rebase -i HEAD~5
```

Buradaki `HEAD~5`, son 5 commit’inizi ifade eder. Rebase başlatıldığında Git, editörünüzde commit geçmişinizi gösterecektir.

### **Adım 2: Squash İşlemine Başlama**

Rebase editöründe, commit'leri düzenlemek için aşağıdaki adımları takip edebilirsiniz:

```bash
pick e3a1b35 İlk commit
squash 7f69d5a İkinci commit
squash 1d2d3f4 Üçüncü commit
pick f9a6c2b Dördüncü commit
```

Burada, `pick` komutu, bir commit’i olduğu gibi tutmak anlamına gelir. `squash` komutu ise, sonraki commit’lerinizi önceki commit ile birleştirmek anlamına gelir.

Yukarıdaki örnekte, ilk commit’i olduğu gibi bırakıyor, ancak ikinci ve üçüncü commit’leri birleştiriyoruz.

### **Adım 3: Commit Mesajını Düzenleme**

Squash işleminden sonra, Git birleştirdiğiniz commit’lerin mesajlarını gösterir. Buradan, tek bir commit mesajı yazabilirsiniz. Bu mesaj, birleştirilen commit’lerin hepsini kapsamalı ve anlamlı olmalıdır.

Git, şu tür bir mesajı önerebilir:

```bash
# Bu commit, 3 commit’i birleştirir:
# - İkinci commit mesajı
# - Üçüncü commit mesajı
```

Bu mesajı düzenleyebilir ve daha anlamlı bir açıklama yazabilirsiniz.

### **Adım 4: Rebase İşlemini Tamamlama**

Commit mesajını düzenledikten sonra, rebase işlemine devam etmek için aşağıdaki komutu kullanabilirsiniz:

```bash
git rebase --continue
```

Bu komut, commit’leri birleştirme işlemini tamamlar. Artık birden fazla commit, tek bir commit olarak kaydedilmiş olur.

---

## **3. Commit’leri Birleştirme (Squashing) Senaryoları ve Uygulamalar**

### **Senaryo 1: Küçük İyileştirmeleri Birleştirmek**

Bir proje üzerinde çalışıyorsunuz ve her küçük iyileştirme için ayrı commit'ler yapıyorsunuz. Ancak, bu commit'ler sonunda gereksiz hale geliyor ve daha temiz bir geçmiş için tek bir commit’te toplanması gerekiyor.

1. İlk olarak, son 5 commit'i görmek için interaktif rebase başlatın:

   ```bash
   git rebase -i HEAD~5
   ```

2. `pick` komutunu, birleştirilmesi gereken commit’ler için `squash` ile değiştirin.
3. Commit mesajını düzenleyin ve işlemi tamamlayın.

**Hands-On:**  

- Katılımcılara birkaç küçük düzeltme yapacakları bir senaryo verin.
- Bu düzeltmeleri her biri için ayrı commit olarak kaydedin ve sonra bu commit’leri squash yaparak birleştirmelerini sağlayın.

---

### **Senaryo 2: Özellik Geliştirme Sonrasında Commit'leri Birleştirmek**

Bir özellik üzerinde çalışırken, her adımda commit’ler yapılıyor, ancak sonunda bu commit’lerin tek bir anlamlı commit altında toplanması gerekiyor.

1. Özellik üzerinde çalışırken, birkaç commit yapın (özellik ekleme, düzeltme, iyileştirme).
2. Özellik tamamlandığında, bu commit'leri birleştirmek için `git rebase -i HEAD~<n>` komutunu kullanın.
3. Tüm commit'leri `squash` ile birleştirin ve birleştirilmiş commit için anlamlı bir mesaj yazın.

**Hands-On:**  

- Katılımcılara bir özellik üzerinde çalışacakları ve ardından commit’leri birleştirerek tek bir commit’e dönüştürecekleri bir senaryo verin.
- Commit'leri squash yaparken dikkat etmeleri gereken noktaları tartışın.

---

## **4. Squashing İçin İpuçları ve En İyi Uygulamalar**

- **Anlamlı Commit Mesajları**: Squash işleminden sonra, birleştirilen commit’lerin mesajlarını anlamlı ve açıklayıcı hale getirin. Bu, takım arkadaşlarınızın yapılan değişiklikleri daha iyi anlamalarına yardımcı olur.
  
- **Sadece Son Commit’leri Birleştirme**: Genellikle son commit’leri birleştirmek daha güvenlidir. Eski commit'leri birleştirmek, eski hataları veya yanlış anlaşılmaları geri getirebilir.

- **Çok Fazla Commit’i Birleştirmemek**: Çok fazla commit’i birleştirmek, değişiklikleri izlemeyi zorlaştırabilir. Yapılan her değişikliği kaydetmek ve anlamlı bir commit geçmişi oluşturmak önemlidir.

- **Squashing, Paylaşılan Depolarda Dikkatle Kullanılmalı**: Eğer commit’lerinizi başkalarıyla paylaşıyorsanız, squash işlemi sonrasında bu commit'leri paylaşmadan önce takımınızla iletişimde olun. Çünkü squash, commit geçmişini değiştirir ve başkalarının bu commit’lere dayalı işlerini etkileyebilir.

---

### **Sonuç**

Commit’leri birleştirme (squashing), projelerde daha temiz ve düzenli bir commit geçmişi oluşturmanın önemli bir aracıdır. Bu işlem, özellikle büyük projelerde, açık kaynak yazılımlarında ve takım çalışmalarında daha şeffaf bir yazılım geliştirme süreci sağlar. Eğitiminizde öğrendiğiniz squash komutları ve teknikleriyle, projelerinizi daha verimli bir şekilde yönetebilirsiniz.
