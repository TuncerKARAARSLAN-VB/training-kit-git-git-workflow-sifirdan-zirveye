# **Değişikliklerin İzlenmesi ve Dosya Silme**

## **1. Değişikliklerin İzlenmesi**

Git, projedeki her değişikliği kaydederek geçmişteki durumları incelemenize olanak tanır. 

### **`git log` Komutunun Kullanımı**

- **Amaç:** Commit geçmişini görüntülemek.  
- **Komut:**  

  ```bash
  git log
  ```

  - Commit mesajları, hash kodları, yazar bilgileri ve tarihleri gösterir.

#### **Parametrelerle `git log` Kullanımı**

1. **Sadece Son Commit’leri Görüntüleme**:  

   ```bash
   git log -n 5
   ```

   (Son 5 commit’i görüntüler.)  

2. **Bir Dosya İçin Commit Geçmişi**:  

   ```bash
   git log <dosya_adi>
   ```

   (Belirli bir dosyada yapılan değişiklikleri listeler.)  

3. **Grafiksel Gösterim**:  

   ```bash
   git log --graph --oneline
   ```

   (Daha sade ve dallar arasında görsel bir temsil.)  

---

### **`git diff` Komutunun Kullanımı**

- **Amaç:** Yapılan değişikliklerin detaylarını görmek.  
- **Komut:**  

  ```bash
  git diff
  ```

  - Çalışma alanındaki değişiklikleri, commit’lenmemiş dosyaları ve farkları gösterir.

#### **Farklı `git diff` Kullanımları**

1. **Bir Commit ile Karşılaştırma**:  

   ```bash
   git diff <commit_hash>
   ```

   (Belirli bir commit ile güncel durumu karşılaştırır.)  

2. **İki Commit Arasındaki Farklar**:  

   ```bash
   git diff <commit1_hash> <commit2_hash>
   ```

   (Belirli iki commit arasındaki değişiklikleri gösterir.)  

3. **Bir Dosyadaki Değişiklikler**:  

   ```bash
   git diff <dosya_adi>
   ```

   (Sadece bir dosyada yapılan değişiklikleri inceler.)  

---

## **2. Dosya Silme**

Git’te bir dosyayı silmek yalnızca fiziksel olarak dosyayı kaldırmakla sınırlı değildir; bu değişikliği Git’e bildirmek de gerekir.

### **`git rm` Komutunun Kullanımı**

- **Amaç:** Bir dosyayı çalışma alanından ve Git deposundan kaldırmak.  
- **Komut:**  

  ```bash
  git rm <dosya_adi>
  ```

  - Dosya fiziksel olarak silinir ve Git’e kaydedilir.

#### **Bir Commit ile Dosya Silme Süreci**

1. Dosyayı silin:  

   ```bash
   git rm <dosya_adi>
   ```

2. Değişikliği commit edin:  

   ```bash
   git commit -m "Dosya silindi: <dosya_adi>"
   ```

#### **Sadece Depodan Silmek (Fiziksel Dosyayı Korumak)**

- Eğer dosyayı fiziksel olarak silmeden yalnızca Git deposundan kaldırmak istiyorsanız:  

  ```bash
  git rm --cached <dosya_adi>
  ```

---

## **3. Senaryo: Eski Bir Dosyayı Silmek**

### **Durum:**

Projenizde artık kullanılmayan bir `notes.txt` dosyası var ve bunu Git deposundan kaldırmak istiyorsunuz.

### **Çözüm:**

1. **Dosyayı Silin:**  

   ```bash
   git rm notes.txt
   ```

2. **Commit Edin:**  

   ```bash
   git commit -m "Dosya silindi: notes.txt"
   ```

3. **Push Edin:**  

   ```bash
   git push
   ```

**Hands-On:**  
Katılımcılar, kendi projelerinde eski bir dosyayı kaldırarak süreci uygular.

---

## **4. Senaryo: Değişiklikleri İnceleme**

### **Durum:**

Bir ekip üyesi bir dosyada beklenmedik değişiklikler yaptı ve neyin değiştirildiğini incelemeniz gerekiyor.

### **Çözüm:**

1. **Değişiklikleri Görüntüleyin:**  

   ```bash
   git diff
   ```

2. **Commit Geçmişini Kontrol Edin:**  

   ```bash
   git log
   ```

3. **Belirli Bir Commit ile Karşılaştırma Yapın:**  

   ```bash
   git diff <commit_hash>
   ```

**Hands-On:**  
Katılımcılar, bir dosyada yapılan değişiklikleri inceleyerek önceki commit’lerle karşılaştırır.

---

## **5. En İyi Uygulamalar**

1. **Commit Mesajlarını Anlamlı Tutun:**  
   - Dosya silme işlemleri gibi değişiklikler için net mesajlar yazın.  

2. **İhtiyaç Duyulmayan Dosyaları Silin:**  
   - Projede yer kaplayan ve kullanılmayan dosyaları düzenli olarak kaldırın.  

3. **Değişiklikleri Sıkça Kontrol Edin:**  
   - `git log` ve `git diff` komutlarını kullanarak düzenli inceleme yapın.  

---

## **6. Hands-On Görevleri**

### **Görev 1: Bir Dosyayı Silmek**

- Depo içindeki gereksiz bir dosyayı silin.  
- Silme işlemini commit edin ve push edin.  

### **Görev 2: Değişiklikleri Karşılaştırmak**

- Bir dosyayı güncelleyin ve değişiklikleri `git diff` ile inceleyin.  
- Sonrasında commit edip bir önceki commit ile karşılaştırın.  
