# **İleri Seviye Araçlar ve Teknikler: Depo Arşivleme**

Depo arşivleme, bir Git deposunun geçmişteki sürümlerini saklamak ve yönetmek için kullanılan tekniklerden biridir. Bu işlem, özellikle büyük projelerde ve çok sayıda commit ve dosya içeren projelerde önemlidir. Depo arşivleme, projenin gelecekteki sürümlerinin kolayca erişilebilir olmasını sağlar, aynı zamanda gereksiz yer kaplamayan, temiz ve verimli bir geçmiş kaydı sunar.

## **1. Depo Arşivlemenin Tanımı ve Önemi**

- **Depo Arşivleme Nedir?**
  - Git depoları zamanla büyük boyutlara ulaşabilir. Depo arşivleme, bu büyüklüğü yönetmek ve eski sürümleri veya dalları daha düzenli hale getirmek için kullanılır.
  - Git'in veritabanında çok fazla commit, dosya veya dal bulunduğunda, bunlar yer kaplayabilir. Arşivleme, bu tür verileri geçmişten ayırıp saklamayı sağlar.

- **Depo Arşivlemenin Avantajları**
  - **Sistem Performansının İyileştirilmesi**: Git deposu zamanla büyüdükçe işlem süresi uzayabilir. Arşivleme, gereksiz verileri temizleyerek işlemlerin hızlanmasına yardımcı olur.
  - **Depo Boyutunun Küçülmesi**: Git, her commit'i kaydeder, bu da depo boyutunun zamanla artmasına neden olabilir. Arşivleme, eski commit'leri ve gereksiz dosyaları kaldırarak depo boyutunu küçültür.
  - **Geçmişin Düzenlenmesi**: Depo arşivleme, geçmişi düzenlemeye ve yalnızca önemli sürümlerin aktif tutulmasına olanak tanır.

---

## **2. Depo Arşivleme Teknikleri**

- **Git’in `git gc` Komutu (Garbage Collection)**
  - `git gc`, Git'in "çöp toplama" (garbage collection) işlemi için kullanılır. Bu komut, gereksiz dosyaları, eski commit'leri ve kullanılmayan verileri temizler.
  - **Kullanım:**

    ```bash
    git gc --aggressive
    ```

  - Bu komut, Git deposunda gereksiz verileri temizler ve depo boyutunu küçültür.

- **Git'in `git filter-branch` Komutu**
  - Git'in `filter-branch` komutu, eski commit'lerdeki belirli dosyaları veya bilgileri temizlemek için kullanılır. Bu, depodan belirli dosyaların veya geçmiş sürümlerin çıkarılmasını sağlar.
  - **Örnek:**

    ```bash
    git filter-branch --tree-filter 'rm -rf <dosya_adı>' HEAD
    ```

- **Git'in `git repack` Komutu**
  - Git'in `repack` komutu, depo verilerini yeniden paketler. Bu, Git'in veritabanındaki tüm objeleri daha verimli bir şekilde sıkıştırarak depolama alanı kazandırır.
  - **Kullanım:**

    ```bash
    git repack -a -d
    ```

---

## **3. Senaryo: Depo Arşivleme ve Temizleme**

**Durum**:
Bir projede çok fazla geçmiş commit ve dosya var. Bu, depo boyutunu artırarak sistem performansını etkiliyor. Depoyu arşivleyerek geçmişi temizlemek gerekiyor.

**Çözüm:**

1. **`git gc` Komutunun Kullanımı:**
   - Öncelikle, depodaki gereksiz verileri temizlemek için `git gc` komutunu çalıştırın:

     ```bash
     git gc --aggressive
     ```

   - Bu işlem, eski dosya ve commit’leri temizler ve depoyu daha verimli hale getirir.

2. **Eski Commit’lerin Temizlenmesi:**
   - Eğer eski commit’lerde gereksiz dosyalar varsa, `git filter-branch` komutunu kullanarak bu dosyaları geçmişten temizleyin:

     ```bash
     git filter-branch --tree-filter 'rm -rf <dosya_adı>' HEAD
     ```

3. **Depo Yeniden Paketleme:**
   - Depo arşivleme işleminin son adımı olarak `git repack` komutunu kullanarak verileri daha verimli hale getirin:

     ```bash
     git repack -a -d
     ```

**Hands-On:**

- Öğrencilerle birlikte bir Git deposu üzerinde çalışarak `git gc`, `git filter-branch` ve `git repack` komutlarını kullanın.
- Depo boyutunu önce ölçün, sonra bu komutlarla depo boyutunu nasıl küçültebileceğinizi gözlemleyin.
- Öğrencilere farklı dosya türlerini ve commit’leri temizlemeleri için örnekler verin.

---

## **4. Depo Arşivlemenin En İyi Uygulamaları**

- **Düzenli Olarak Çöp Toplama Yapmak:**
  - Git depolarında zamanla biriken gereksiz dosyalar, depoların büyümesine neden olabilir. Bu nedenle `git gc` komutunu düzenli olarak çalıştırmak önemlidir.

- **Önemli Commit’leri Koruyarak Eski Dosyaları Temizlemek:**
  - Depo arşivleme yaparken, sadece gereksiz dosyaları ve eski commit’leri temizleyin. Önemli olan commit’lerin kaybolmaması için dikkatli olun.

- **`filter-branch` Komutunu Yalnızca Gerektiğinde Kullanmak:**
  - `git filter-branch` komutu, geçmişteki verileri kalıcı olarak değiştirir. Bu nedenle bu komutu yalnızca gerektiğinde kullanın ve işlemi tamamlamadan önce yedeğinizi alın.

- **Arşivleme ve Yedekleme:**
  - Depo arşivleme yapmadan önce depolarınızı yedekleyin. Bu, yanlışlıkla silinen verilerin geri alınabilmesi için önemlidir.

---

## **5. İleri Seviye Senaryo: Git Depolarında Arşivleme ve Yedekleme Stratejileri**

**Durum**:
Büyük bir yazılım projesinde sık sık depo temizliği yapılması gerekiyor. Ancak, bazı eski commit’lerin kritik dosyaları içerdiği için bu commit’lerin kaybolmaması gerekir. Ayrıca, düzenli yedekleme yapılması gerekiyor.

**Çözüm**:

1. Depoyu temizlemeden önce yedekleme alın. Yedekleme için `git clone --mirror` komutunu kullanarak depo yedeği oluşturun:

   ```bash
   git clone --mirror <depo_url> <yedek_dizin>
   ```

2. Yedekleme alındıktan sonra `git gc` komutunu çalıştırarak gereksiz verileri temizleyin:

   ```bash
   git gc --aggressive
   ```

3. `git filter-branch` komutunu kullanarak eski ve gereksiz dosyaları temizleyin:

   ```bash
   git filter-branch --tree-filter 'rm -rf <dosya_adı>' HEAD
   ```

**Hands-On:**

- Öğrencilerle birlikte, öncelikle bir depo yedeği alın ve ardından temizleme işlemi uygulayın. Öğrenciler, her adımda yapılan değişikliklerin depo üzerindeki etkilerini gözlemleyecekler.

---

### **Sonuç**

Depo arşivleme, Git depolarındaki gereksiz verilerin temizlenmesi ve sistemin daha verimli hale getirilmesi için önemli bir tekniktir. Bu eğitimde, depo arşivlemenin temel tekniklerini, en iyi uygulamalarını ve pratik senaryoları öğrendiniz. Arşivleme işlemi, projelerinizdeki geçmişi yönetmenize ve depolarınızın daha verimli çalışmasına yardımcı olacaktır.
