# **Son Dalları Görüntüleme: Git Branching ve Yönetimi**

Git, projelerdeki farklı geliştirme süreçlerini izlemek ve yönetmek için dalları (branches) kullanır. Her dal, proje üzerinde bağımsız değişiklikler yapmanıza olanak tanır. Git üzerinde bir dal ile çalışırken, bazen son dalları görüntülemek ve mevcut dalların durumunu takip etmek gerekebilir.

## **1. Son Dalları Görüntülemenin Önemi**

Bir projede birden fazla geliştirici çalışıyorsa, farklı dallarda yapılan değişiklikleri takip etmek kritik bir öneme sahiptir. Git’in sağladığı `git branch` komutu ile aktif dallar, son yapılan dallar ve bunların durumları kolayca izlenebilir. Bu, takım içi işbirliği ve değişikliklerin yönetilmesi için önemli bir adımdır.

**Son Dalları Görüntülemenin Avantajları:**

- **Değişiklik Takibi**: Hangi dalda ne tür değişikliklerin yapıldığını takip etmek, hataların izlenmesini ve düzeltilmesini kolaylaştırır.
- **Ekip Çalışması**: Takım üyeleri arasındaki işbirliğini destekler, hangi dalın aktif olduğunu ve hangi dalın tamamlandığını görmeyi sağlar.
- **Birleştirme (Merge) Hazırlığı**: Son dalları görmek, dalların birleştirilmeden önce hangi dosya değişikliklerini içereceğini anlamaya yardımcı olur.

---

## **2. Son Dalları Görüntülemek için Git Komutları**

Git, dallar hakkında çeşitli bilgileri görüntülemek için farklı komutlar sağlar. Bu komutlar, aktif dallar, son değişiklikler, dalların durumu ve daha fazlası hakkında bilgi edinmenizi sağlar.

- **`git branch`**: Yerel depodaki tüm dalları görüntüler.
  - **Kullanım**:

    ```bash
    git branch
    ```

    Bu komut, yerel depodaki tüm dalları listeleyecek ve şu an aktif olan dalı (*) ile işaretleyecektir.

- **`git branch -a`**: Hem yerel hem de uzak depodaki tüm dalları görüntüler.
  - **Kullanım**:

    ```bash
    git branch -a
    ```

- **`git branch -r`**: Sadece uzak depodaki dalları görüntüler.
  - **Kullanım**:

    ```bash
    git branch -r
    ```

- **`git log --oneline --graph`**: Dalları ve commit geçmişini görselleştirerek gösterir. Bu, dalların ve commit'lerin nasıl birleştirildiğini (merge) veya dallandığını (branch) kolayca görmeyi sağlar.
  - **Kullanım**:

    ```bash
    git log --oneline --graph --all
    ```

- **`git show-branch`**: Dalların geçmişini ve her dalda hangi commit'lerin yapıldığını görüntüler.
  - **Kullanım**:

    ```bash
    git show-branch
    ```

---

## **3. Senaryo: Son Dalları Görüntüleme ve Analiz Etme**

**Durum**:
Bir ekip, farklı özellikler üzerinde çalışmak için birden fazla dal oluşturmuş ve proje büyüdükçe hangi dalın aktif olduğunu takip etmek zorlaşmış. Şimdi, hangi dalların son olarak oluşturulduğunu görmek ve bunlar üzerinde hangi commit’lerin yapıldığını anlamak gerekiyor.

**Çözüm**:

1. **Yerel Dalları Görüntüleme**:
   - `git branch` komutunu kullanarak tüm yerel dalları görüntüleyin:

     ```bash
     git branch
     ```

   - Bu komut, tüm yerel dallarınızı ve aktif dalı gösterecektir.

2. **Uzak Dalları Görüntüleme**:
   - Uzak depodaki dalları görmek için `git branch -r` komutunu kullanın:

     ```bash
     git branch -r
     ```

3. **Tüm Dalları ve Geçmişi Görselleştirme**:
   - Dalların ve commit geçmişinin görselleştirilmesi için `git log --oneline --graph --all` komutunu kullanarak geçmişi izleyin:

     ```bash
     git log --oneline --graph --all
     ```

4. **Dalların Durumunu ve Geçmişini Görüntüleme**:
   - Hangi dalda hangi commit'lerin yapıldığını görmek için `git show-branch` komutunu kullanın:

     ```bash
     git show-branch
     ```

**Hands-On**:

- Eğitmenle birlikte bir Git projesinde `git branch`, `git branch -r`, `git log --oneline --graph --all` ve `git show-branch` komutlarını çalıştırın.
- Katılımcılara farklı senaryolar verin: Örneğin, hangi dalın en son oluşturulduğunu tespit etme, en son yapılan commit'leri ve değişiklikleri takip etme.

---

## **4. Dallarla Çalışma Senaryoları ve Uygulamalar**

- **Senaryo 1: Yeni Bir Dal Oluşturup Aktif Olan Dalı Görüntüleme**
  1. Yeni bir dal oluşturun:

     ```bash
     git checkout -b yeni-dal
     ```

  2. Yerel dalları görüntülemek için `git branch` komutunu çalıştırın:

     ```bash
     git branch
     ```

     Bu komut, oluşturduğunuz yeni dalı ve aktif dalı gösterecektir.

- **Senaryo 2: Uzak Dalları İncelemek ve Senkronize Etmek**
  1. Uzak depodaki tüm dalları görmek için `git branch -r` komutunu kullanın:

     ```bash
     git branch -r
     ```

  2. Uzak depodaki en son dallarla yerel dalı senkronize etmek için:

     ```bash
     git fetch
     ```

- **Senaryo 3: Dallar Arasında Geçiş Yapmak ve Değişiklikleri Gözden Geçirmek**
  1. Farklı bir dal üzerinde çalışmak için `git checkout` komutunu kullanın:

     ```bash
     git checkout <dal_adı>
     ```

  2. O dalda yapılan commit’leri görmek için `git log` komutunu kullanın:

     ```bash
     git log
     ```

**Hands-On**:

- Katılımcılara bir dal oluşturma, uzak dalları kontrol etme, ve dallar arasında geçiş yapmayı gösterin.
- Her bir adımda, dalların nasıl görselleştirildiğini ve hangi commit'lerin hangi dallarda yapıldığını takip etmelerini sağlayın.

---

## **5. En İyi Uygulamalar**

- **Aktif Dalı Kontrol Etme**: Git ile çalışırken aktif olduğunuz dalı her zaman kontrol edin. `git branch` komutu ile hangi dalda olduğunuzu doğrulayın.
- **Dalları Düzenli Aralıklarla Temizleyin**: Projenizin büyüklüğüne bağlı olarak, kullanılmayan dalları düzenli aralıklarla temizleyin (`git branch -d <dal_adı>`).
- **Dallarda Çakışmaları Gözlemleyin**: Özellikle büyük projelerde, dallar arasındaki çakışmaları takip edin. Git’in sunduğu görselleştirme araçları, çakışmaları ve farklı commit’leri anlamada faydalıdır.

---

### **Sonuç**

Git ile son dalları görüntülemek, projedeki farklı geliştirme süreçlerini ve işbirliklerini daha verimli hale getirir. Bu eğitimde, Git komutlarını kullanarak yerel ve uzak dalları nasıl takip edebileceğinizi öğrendiniz. Dalların geçmişini incelemek ve aktif dalları görmek, yazılım geliştirme sürecinde daha iyi bir kontrol sağlar ve takım çalışmasını iyileştirir.
