# **Commit Mesajı Etiketleri (Örn. "fix", "feat", "chore")**

Commit mesajı etiketleri, yazılım geliştirme süreçlerinde commit’leri kategorize etmek için kullanılan etiketlerdir. Bu etiketler, yapılan değişikliklerin türünü açıkça belirtir ve projenin tarihçesini daha anlamlı hale getirir. Commit mesajlarını düzenli ve anlaşılır tutmak, takımların ve iş ortaklarının yapılan değişiklikleri hızlıca anlamasına yardımcı olur.

Bu eğitimde, popüler commit mesajı etiketlerinden bahsedeceğiz, örnekler vereceğiz ve etiketlerin nasıl etkili bir şekilde kullanılacağına dair hands-on çalışmalar yapacağız.

---

## **1. Commit Mesajı Etiketleri Nedir?**

Commit mesajı etiketleri, bir commit’in ne tür bir değişiklik içerdiğini belirtmek için kullanılır. En yaygın kullanılan etiketler:

- **"fix"**: Hataların düzeltilmesi için kullanılır.
- **"feat"**: Yeni özelliklerin eklenmesi için kullanılır.
- **"chore"**: Küçük, rutin bakım işlemleri (kod temizlikleri, test düzenlemeleri, bağımlılık güncellemeleri vb.) için kullanılır.
- **"docs"**: Belgelerde yapılan değişiklikler için kullanılır.
- **"style"**: Kodun formatıyla ilgili yapılan değişiklikler (örneğin, beyaz alanlar, girintiler, noktalama işaretleri vb.) için kullanılır.
- **"test"**: Test dosyalarındaki değişiklikler için kullanılır.
- **"refactor"**: Kodun işleyişini değiştirmeden yapılan iyileştirmeler (yapısal değişiklikler vb.) için kullanılır.

Bu etiketler, proje yönetiminde düzeni artırır ve commit geçmişini takip etmeyi kolaylaştırır.

---

## **2. Commit Mesajı Etiketlerinin Kullanımı**

Commit mesajı etiketlerini kullanırken, her zaman tutarlı ve net olmak önemlidir. Her commit, yapılan değişikliğin türünü belirten bir etikete sahip olmalıdır. Aşağıda, bu etiketlerin kullanımını açıklayan örnekler verilmiştir:

### **"fix" - Hata Düzeltmeleri**

Bu etiket, bir hatanın düzeltildiği commit’ler için kullanılır. Örneğin:

```bash
git commit -m "fix: Kullanıcı girişi hatası düzeltildi"
```

**Senaryo:**
Bir kullanıcı, sisteme giriş yaparken hata alıyor. Hata tespit edildikten sonra düzeltilir ve commit mesajı şu şekilde olur:

```bash
git commit -m "fix: Kullanıcı girişinde çıkan hata düzeltildi"
```

### **"feat" - Yeni Özellik Eklenmesi**

Bu etiket, projeye yeni bir özellik eklendiğinde kullanılır. Örneğin:

```bash
git commit -m "feat: Kullanıcı profil sayfası eklendi"
```

**Senaryo:**
Bir kullanıcı profil sayfası ekleniyor. Bu işlem, aşağıdaki commit mesajıyla kaydedilir:

```bash
git commit -m "feat: Kullanıcı profil sayfası eklendi"
```

### **"chore" - Bakım ve Rutin İşlemler**

Bu etiket, genellikle kodun dışındaki rutin işler için kullanılır (bağımlılık güncellemeleri, kod düzenlemeleri vb.). Örneğin:

```bash
git commit -m "chore: Bağımlılıklar güncellendi"
```

**Senaryo:**
Projede kullanılan bir bağımlılık güncellenir, ancak fonksiyonel bir değişiklik yapılmaz. Commit mesajı şu şekilde olur:

```bash
git commit -m "chore: Bağımlılıklar güncellendi"
```

### **"docs" - Belgeler**

Bu etiket, proje belgelerinde yapılan değişiklikler için kullanılır. Örneğin:

```bash
git commit -m "docs: README dosyasına kurulum talimatları eklendi"
```

**Senaryo:**
Proje belgelerinde bir güncelleme yapılır, README dosyasına kurulum talimatları eklenir:

```bash
git commit -m "docs: README dosyasına kurulum talimatları eklendi"
```

### **"style" - Kod Stili Değişiklikleri**

Bu etiket, sadece stil değişiklikleri (girintiler, beyaz alanlar, kod formatlaması) için kullanılır. Örneğin:

```bash
git commit -m "style: Kodda gereksiz boşluklar temizlendi"
```

**Senaryo:**
Kodda yapılan stil düzenlemeleri (girintiler ve boşluklar) sonrası commit mesajı şu şekilde olur:

```bash
git commit -m "style: Kodda gereksiz boşluklar temizlendi"
```

### **"test" - Test Değişiklikleri**

Bu etiket, testlerde yapılan değişiklikler için kullanılır. Örneğin:

```bash
git commit -m "test: Kullanıcı doğrulama testi eklendi"
```

**Senaryo:**
Yeni bir test eklenmişse, commit mesajı şu şekilde olur:

```bash
git commit -m "test: Kullanıcı doğrulama testi eklendi"
```

---

## **3. Commit Mesajı Etiketlerini Kullanmanın En İyi Uygulamaları**

Commit mesajı etiketlerini kullanırken dikkat edilmesi gereken bazı noktalar:

- **Tutarlılık**: Commit mesajlarınızda kullanılan etiketlerin tutarlı olması gerekir. Takım arkadaşlarınızın aynı etiketleri kullanması, commit geçmişinin anlaşılabilirliğini artırır.
  
- **Kısa ve Net Mesajlar**: Commit mesajları kısa ve öz olmalıdır. Yalnızca yapılan değişikliğin ana amacını ifade edin.

- **Ekip İletişimi**: Ekip içinde hangi etiketlerin kullanılacağına dair bir konsensüs oluşturun. Proje başlangıcında, commit mesajlarıyla ilgili kuralları belirlemek uzun vadede faydalı olacaktır.

---

## **4. Senaryo ve Hands-On Uygulamaları**

### **Senaryo 1: Yeni Özellik Ekleme (feat)**

Bir projede, yeni bir kullanıcı kayıt sistemi ekleniyor. Bu özelliği eklemek için commit’ler yapılır.

1. **Yeni özellik ekleyin** ve commit edin:

```bash
git commit -m "feat: Kullanıcı kayıt sistemi eklendi"
```

2. **Veritabanı ve API entegrasyonları** için diğer commit’leri yapın.

3. **Commit mesajlarını gözden geçirin** ve doğru etiketleri kullandığınızdan emin olun.

**Hands-On:**  

- Katılımcılara basit bir özellik eklemelerini ve her commit’te doğru etiketleri kullanmalarını isteyin.
  
### **Senaryo 2: Hata Düzeltme (fix)**

Projede bir hata tespit edilir ve düzeltilir.

1. **Hata tespit edin** ve düzeltme yapın.

2. Commit mesajını şu şekilde yazın:

```bash
git commit -m "fix: Kullanıcı doğrulama hatası düzeltildi"
```

3. **Hata düzeltmesini kontrol edin** ve doğru commit mesajını kullandığınızdan emin olun.

**Hands-On:**  

- Katılımcılara hata düzeltmeleri yapmalarını ve uygun commit mesajı etiketlerini kullanmalarını sağlayın.

### **Senaryo 3: Bakım İşlemi (chore)**

Bir bağımlılık güncellenir ve bu işlem commit edilir.

1. **Bağımlılık güncellemesi yapın**.

2. Commit mesajı şu şekilde olur:

```bash
git commit -m "chore: Bağımlılık güncellendi"
```

**Hands-On:**  

- Katılımcılara bakım işlemleri (bağımlılık güncellemeleri, dosya düzenlemeleri vb.) yaptırarak, bu işlemler için uygun commit mesajları yazmalarını isteyin.

---

## **Sonuç**

Commit mesajı etiketleri, projedeki değişikliklerin düzenli ve anlaşılır olmasını sağlar. Bu etiketler, takım üyelerinin geçmiş değişiklikleri daha kolay takip etmelerini ve projenin sürdürülebilirliğini artırmalarını sağlar. Bu eğitimde öğrendiğiniz commit mesajı etiketlerini ve en iyi uygulamaları kullanarak, projelerinizi daha profesyonel ve düzenli bir şekilde yönetebilirsiniz.
