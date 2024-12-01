# **Fork’u Güncel Tutma**

Bir projeyi fork ettiğinizde, orijinal depo üzerinde yapılan değişiklikler sizin fork'unuza yansımaz. Bunun anlamı, orijinal depoda güncellemeler veya yeni özellikler eklenirken, sizin fork'unuz bu değişikliklerden habersiz kalır. Bu nedenle, fork'unuzu düzenli olarak orijinal depo ile senkronize etmek çok önemlidir. Bu işlem, projede meydana gelen değişikliklerin sizin fork'unuza yansımasını sağlar ve olası uyumsuzlukları önler.

---

## **1. Fork’u Güncel Tutma Neden Önemlidir?**

- **Yeni Özellikler ve Düzeltmeler:** Orijinal depoda yapılan değişiklikler, sizin fork'unuza yansımaz. Senkronize ettiğinizde, orijinal depoda yapılan hata düzeltmeleri veya yeni özellikler sizin projenize dahil olur.
- **Çakışmaların Önlenmesi:** Orijinal depo ile fork'unuz arasında uyumsuzluklar oluşabilir. Senkronize etmek, çakışmaların önceden tespit edilmesini ve çözülmesini sağlar.
- **Projede Verimlilik:** Projeye devam ederken, orijinal depo ile olan senkronizasyon sürekli güncel ve uyumlu olmanızı sağlar.

---

## **2. Fork’u Güncel Tutma Adımları**

Fork'unuzu orijinal depo ile güncel tutmak için birkaç temel adımı takip etmeniz gerekir. Bu adımlar, hem yerel depolarınızda hem de GitHub’daki fork'unuzda uygulanabilir.

### **Adım 1: Orijinal Depoyu İleri Seviye Eklemek (Upstream Remote)**

Fork'unuzu senkronize etmeden önce, orijinal depoyu (upstream) uzak depo olarak eklemeniz gerekecek. Bu, orijinal depoya ulaşmanızı sağlar.

- Orijinal (upstream) deponun URL'sini almak için, GitHub'da orijinal depoya gidin ve URL'yi kopyalayın.

Örneğin, `https://github.com/orijinal-proje/proje-adi.git`

### **Adım 2: Upstream Remote Ekleme**

Fork'unuzun yerel depo üzerinde upstream depo eklemek için şu komutu kullanabilirsiniz:

```bash
git remote add upstream https://github.com/orijinal-proje/proje-adi.git
```

Bu komut, orijinal depoyu "upstream" olarak ekler.

### **Adım 3: Upstream Depodan Değişiklikleri Çekme (Fetch)**

Orijinal depodan en son değişiklikleri almak için `git fetch` komutunu kullanabilirsiniz:

```bash
git fetch upstream
```

Bu komut, orijinal depodan (upstream) tüm değişiklikleri alır ancak bunları sizin yerel deponuza yansıtmaz.

### **Adım 4: Ana Daldan (Main Branch) Değişiklikleri Birleştirme (Merge)**

Orijinal depodan gelen değişiklikleri kendi fork'unuza almak için ana dalda (genellikle `main` veya `master` dalı) birleştirmeniz (merge) gerekir.

1. Ana dalda olduğunuzdan emin olun:

    ```bash
    git checkout main
    ```

2. Orijinal deponun değişikliklerini kendi ana dalınıza birleştirin:

    ```bash
    git merge upstream/main
    ```

   Bu komut, orijinal depo ile fork'unuzu birleştirir ve orijinal depodaki güncellemeleri alır.

### **Adım 5: Değişiklikleri GitHub’a Gönderme (Push)**

Değişiklikleri yerel deponuzda başarılı bir şekilde birleştirdiğinizde, bu değişiklikleri GitHub'daki fork'unuza göndermeniz gerekir. Bunun için şu komutu kullanabilirsiniz:

```bash
git push origin main
```

Bu komut, yerel deponuzdaki güncel değişiklikleri GitHub’daki fork'unuza gönderir.

---

## **3. Senaryo: Fork Güncellemelerini Almak ve Çakışma Çözmek**

**Durum:**
Bir açık kaynak projeyi fork ettiniz ve üzerinde çalışıyorsunuz. Orijinal projede bazı değişiklikler yapıldı ve siz fork’unuzu güncel tutmalısınız. Ayrıca, fork’unuzda orijinal depo ile bazı çakışmalar da olabilir.

### **Adım Adım Çözüm:**

1. **Upstream Depoyu Ekleyin:**
   Orijinal projeyi upstream olarak ekleyin.

   ```bash
   git remote add upstream https://github.com/orijinal-proje/proje-adi.git
   ```

2. **Orijinal Depodan Değişiklikleri Çekin:**
   Orijinal depo ile güncel tutmak için fetch işlemi yapın.

   ```bash
   git fetch upstream
   ```

3. **Ana Dalda Olun ve Değişiklikleri Birleştirin:**
   Ana dalınıza geçin ve değişiklikleri orijinal depodan birleştirin.

   ```bash
   git checkout main
   git merge upstream/main
   ```

4. **Çakışmaların Çözülmesi:**
   Eğer bir çakışma varsa, Git size hangi dosyalarda çakışmalar olduğunu gösterecektir. Bu durumda, çakışmaları manuel olarak çözmelisiniz. Çakışma çözümü için dosyaları açın ve gerekli düzenlemeleri yapın.

5. **Değişiklikleri GitHub'a Gönderin:**
   Değişiklikleri GitHub’daki fork'unuza gönderin.

   ```bash
   git push origin main
   ```

#### **Hands-On:**

1. **Upstream Depoyu Ekleyin:** GitHub üzerinden orijinal bir projeyi bulun ve fork edin.
2. **Upstream Bağlantısını Ekleme:** `git remote add upstream <url>` komutunu kullanarak orijinal depoyu ekleyin.
3. **Güncellemeleri Çekme ve Birleştirme:** `git fetch upstream` ve `git merge upstream/main` komutlarıyla değişiklikleri alın.
4. **Çakışma Çözümü:** Çakışma durumunda dosyaları düzenleyerek çakışmaları çözün.
5. **Değişiklikleri Gönderme:** `git push origin main` komutu ile güncellemeleri GitHub’daki fork’unuza gönderin.

---

### **4. Sonuç**

Fork’unuzu güncel tutmak, açık kaynak projelere katkı sağlarken ve yerel projelerde orijinal kaynaklarla uyumlu çalışırken çok önemlidir. Bu işlem, çakışmaları önlemenin yanı sıra, projedeki yeniliklerden haberdar olmanızı sağlar. Düzenli olarak orijinal depo ile fork’unuzu senkronize ederek, sürekli güncel ve uyumlu bir proje üzerinde çalışabilirsiniz.
