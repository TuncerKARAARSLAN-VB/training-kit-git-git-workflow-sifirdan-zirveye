# **Commit’leri Bölme (Splitting Commits) – Git ile Daha İyi Değişiklik Yönetimi**

Yazılım geliştirme süreçlerinde yapılan her değişiklik, bir commit ile kaydedilir. Ancak bazen bir commit, çok fazla farklı değişiklik içerir ve bu değişikliklerin her biri ayrı bir işlem olarak kaydedilmelidir. Böyle durumlarda, mevcut commit'i **bölmek** (split commit) iyi bir uygulama olabilir.

Git, commit'leri bölmek için çeşitli araçlar ve stratejiler sunar. Commit'leri bölmek, yazılım geliştirme sürecinde daha temiz ve anlamlı commit geçmişi oluşturmanıza yardımcı olur. Bu işlem, projede yapılan her değişikliğin amacını daha net hale getirir ve takım arkadaşlarınızın commit geçmişini daha kolay anlamasını sağlar.

---

## **1. Commit’leri Bölmek Nedir?**

Commit'leri bölme (splitting commits), bir commit'te bir araya getirilmiş birden fazla değişikliği birbirinden ayırarak, her bir değişikliği farklı commit'ler olarak kaydetme işlemidir. Bu işlem, özellikle aşağıdaki durumlar için gereklidir:

- **Yanlışlıkla birleştirilen değişiklikler**: Bir commit, farklı özelliklere ait değişiklikleri bir arada içeriyor. Bu durumda, her değişikliğin bağımsız olarak commit edilmesi gerekebilir.
- **Daha temiz commit geçmişi oluşturma**: Her commit'in belirli bir amaca hizmet etmesini sağlamak, projede daha şeffaf bir geçmiş bırakılmasına yardımcı olur.
- **Kod incelemesi ve hata takibi için daha iyi yapı**: Her commit, tek bir işlemi temsil ettiğinde, değişikliklerin takibi ve hata çözümü daha kolay olur.

---

## **2. Commit’leri Bölme Adımları**

Git'teki commit'leri bölme işlemi birkaç adımdan oluşur. Bu işlemi **interaktif rebase** ile yapabiliriz.

### **Adım 1: Interaktif Rebase Başlatma**

İlk olarak, commit geçmişinizi gözden geçirmek için interaktif rebase komutunu kullanacağız. Bu, belirli bir commit’i düzenlememize olanak tanıyacak.

```bash
git rebase -i HEAD~n
```

Burada `n`, geçmişteki commit sayısını belirtir. Örneğin, son 5 commit'i görmek için `HEAD~5` kullanılır.

### **Adım 2: Commit’i Seçme ve Bölme**

Rebase başlatıldığında, Git, editörde commit geçmişinizi gösterecektir. Buradan bölmek istediğiniz commit’i seçebilirsiniz. Commit’leri bölmek için, `edit` komutunu kullanıyoruz.

Örnek bir interaktif rebase editörü şöyle görünebilir:

```bash
pick 1234567 İlk commit mesajı
edit 89abcde Yeni özellik ekle
pick abc1234 Kod düzenlemeleri
pick def5678 Hata düzeltmeleri
```

Yukarıdaki örnekte, `89abcde` commit'ini bölmek istiyoruz. Bunun için `pick` yerine `edit` yazıyoruz.

### **Adım 3: Commit’i Bölme**

Commit'i düzenlemek için Git size bir komut istemi sunar. Şimdi, commit'inizi bölmeye başlayabiliriz. İlk olarak, bölmek istediğiniz commit'in bulunduğu çalışma dizinine gidin.

```bash
git reset HEAD^
```

Bu komut, son commit'i geri alır ancak değişiklikler çalışma dizininde kalır. Bu, commit’inizin içeriğini bölmenize olanak tanır.

### **Adım 4: Değişiklikleri Seçmek ve Commit'lemek**

Bu aşamada, commit içeriğini iki veya daha fazla parçaya ayırmanız gerekiyor. Bunun için `git add -p` komutunu kullanarak, her bir değişikliği ayrı ayrı seçebiliriz.

Örneğin, `git add -p` komutunu çalıştırdıktan sonra, değişiklikleri interaktif olarak seçebilirsiniz:

```bash
git add -p
```

Bu komut, her bir değişiklik için ekleme veya reddetme seçeneği sunar.

Değişiklikleri ayırdıktan sonra, her bir değişikliği ayrı ayrı commit'lemek için aşağıdaki komutları kullanabilirsiniz:

```bash
git commit -m "Yeni özellik ekle - kısmi değişiklik 1"
git add <dosya_adı>
git commit -m "Yeni özellik ekle - kısmi değişiklik 2"
```

Her değişikliği bağımsız olarak commit ettikten sonra, rebase işlemi devam eder.

### **Adım 5: Rebase’i Tamamlama**

Bütün commit'leri böldükten sonra, rebase işlemine devam edebiliriz. Aşağıdaki komutu kullanarak rebase'i tamamlayabilirsiniz:

```bash
git rebase --continue
```

Rebase tamamlandığında, commit geçmişinizde her bir değişikliğin ayrı bir commit olarak kaydedildiğini göreceksiniz.

---

## **3. Commit’leri Bölme Senaryoları ve Uygulamalar**

### **Senaryo 1: Yanlışlıkla Birleştirilen Değişikliklerin Ayrılması**

Bir commit, çok fazla farklı değişiklik içeriyor. Örneğin, kullanıcı giriş ekranı ile ilgili bir değişiklik ve hata düzeltmesi bir arada yapılmış.

1. Commit’inizi bölmek için interaktif rebase başlatın:

   ```bash
   git rebase -i HEAD~1
   ```

2. `edit` komutunu kullanarak commit’i düzenleyin ve `git reset HEAD^` komutunu çalıştırarak değişiklikleri geri alın.

3. Değişiklikleri uygun şekilde seçin ve her birini bağımsız commit'lere ayırın.

**Hands-On:**  

- Katılımcılara bir commit'in çoklu değişiklik içerdiği bir senaryo verin.
- `git reset` ve `git add -p` komutlarını kullanarak commit'lerini bölmelerini sağlayın.

---

### **Senaryo 2: Daha Temiz Commit Geçmişi Oluşturmak**

Bir proje üzerinde çalışırken, commit geçmişinin düzenli olması çok önemlidir. İyi bir commit geçmişi, kodun hangi amaca hizmet ettiğini daha iyi anlatır.

1. Birden fazla küçük değişiklik yapılmış ve bunlar tek bir commit’e dahil edilmiş.
2. Bu commit, projedeki belirli bir işlevi tanımlıyor ancak aynı commit’te yapılan birkaç değişiklik var.
3. Bu commit'i bölmek için adımları takip ederek her değişikliği bağımsız commit’ler olarak ayırın.

**Hands-On:**  

- Katılımcılara temiz ve şeffaf bir commit geçmişi için commit bölme işlemi yapmalarını sağlayın.

---

### **4. İleri Seviye Commit Bölme Teknikleri**

#### **Commit’leri Tek Bir Commit’e Toplama (Squash)**

Bazen birden fazla commit'i tek bir commit’te birleştirmeniz gerekebilir. Bu durumda, `git rebase -i` komutunu kullanarak, birleştirmek istediğiniz commit'leri seçip `squash` komutuyla birleştirebilirsiniz.

#### **Commit’in İçeriğini Düzenlemek**

Bazen commit içeriğini sadece değiştirmek ve yeni bir commit mesajı yazmak gerekebilir. Bunun için de `git commit --amend` komutunu kullanabilirsiniz.

---

### **Sonuç**

Commit'leri bölme, yazılım geliştirme süreçlerinde daha temiz bir geçmiş oluşturmanıza ve projelerde yapılan değişikliklerin daha anlaşılır bir şekilde izlenmesine yardımcı olur. Bu beceri, özellikle büyük projelerde ve ekip çalışmalarında önemli bir yer tutar. Eğitimde öğrendiğiniz commit bölme teknikleriyle, projelerinizde daha düzenli ve etkili bir git geçmişi yönetimi sağlayabilirsiniz.
