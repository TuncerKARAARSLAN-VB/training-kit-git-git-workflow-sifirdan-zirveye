# **Dosyaların Silinmesi ve Büyük Dosya Değişikliklerinin Yönetimi**  

## **1. Dosyaların Silinmesi**

### **Dosyayı Silme ve Takipten Çıkarma**

#### **a. Fiziksel ve Versiyon Kontrolünden Silme**

Git ile bir dosyayı hem fiziksel olarak hem de sürüm kontrol sisteminden kaldırabilirsiniz.  

- **Komut:**  

  ```bash
  git rm <dosya_adi>
  ```  

- **Sonraki Adımlar:**  
  1. Değişikliği commit edin:  

     ```bash
     git commit -m "Dosya silindi: <dosya_adi>"
     ```  

  2. Push ile uzak depoya gönderin:  

     ```bash
     git push
     ```  

#### **b. Sadece Git Takibinden Çıkarma**
Dosyayı fiziksel olarak koruyarak yalnızca sürüm kontrolünden çıkarabilirsiniz.  

- **Komut:**  

  ```bash
  git rm --cached <dosya_adi>
  ```  

- **Örnek Kullanım:**  
  Büyük bir medya dosyasını `.gitignore` ile hariç tutmadan önce takibinden çıkarmak için bu yöntemi kullanabilirsiniz.  

---

### **Senaryo: Gereksiz Dosyaların Silinmesi**

**Durum:**  
Proje depolarınızda kullanılmayan bir PDF dosyası yer kaplıyor. Bu dosyayı silerek depodan kaldırmanız gerekiyor.  

**Çözüm:**  

1. Dosyayı silin:  

   ```bash
   git rm dosya.pdf
   ```  

2. Commit edin:  

   ```bash
   git commit -m "Kullanılmayan dosya silindi: dosya.pdf"
   ```  

3. Uzak depoya gönderin:  

   ```bash
   git push
   ```  

**Hands-On:**  
Katılımcılar, örnek bir dosya oluşturup bu dosyayı silerek Git’te süreci test ederler.

---

## **2. Büyük Dosya Değişikliklerinin Yönetimi**

Büyük dosyalar veya sık güncellenen dosyalar depoda fazla yer kaplayabilir ve performansı olumsuz etkileyebilir. Git, bu tür durumlar için özel araçlar sunar.

### **a. Büyük Dosyaları İzlemek ve Yedeklemek**

1. **Git LFS (Large File Storage) Kullanımı**  

   Büyük dosyalar için Git LFS kullanarak, dosyaların depoda yalnızca pointer’larını saklayabilirsiniz.  

   - **Kurulum:**  

     ```bash
     git lfs install
     git lfs track "*.psd"
     ```  

   - **Dosya Ekleme:**  

     ```bash
     git add büyük_dosya.psd
     ```  

2. **Senaryo:** Bir proje için sık güncellenen büyük bir görsel dosya (`design.psd`) var.  
   - LFS ile takip ederek depo boyutunu optimize edin.  

### **b. Büyük Commit’leri Tespit Etmek**

1. **`git log` ile Büyük Commit'leri İzleme**  
   Büyük değişiklik içeren commit’leri tespit etmek için:  

   ```bash
   git log --stat
   ```  

2. **`git filter-repo` Kullanımı**  
   Eğer geçmişteki commit’lerde gereksiz büyük dosyalar varsa, geçmişten bu dosyaları kaldırabilirsiniz.  

   - **Kurulum:**  

     ```bash
     pip install git-filter-repo
     ```  

   - **Komut:**  

     ```bash
     git filter-repo --path büyük_dosya.pdf --invert-paths
     ```  

---

### **Senaryo: Büyük Dosyaların Geçmişten Silinmesi**

**Durum:**  
Bir geliştirici yanlışlıkla depoya 100 MB’lık bir dosya ekledi. Bu dosyayı depodan kaldırmanız gerekiyor.  

**Çözüm:**  

1. Dosyayı geçmiş commit’lerden kaldırın:  

   ```bash
   git filter-repo --path büyük_dosya.zip --invert-paths
   ```  

2. Değişiklikleri force-push ile uzak depoya gönderin:  

   ```bash
   git push --force
   ```  

**Hands-On:**  
Katılımcılar, geçmiş commit’lerdeki bir dosyayı kaldırarak süreci uygular.

---

## **3. Büyük Dosyaları Yedekleme ve Alternatif Yöntemler**

1. **Sık Güncellenen Dosyalar için Alternatif Depolama**  
   Büyük medya dosyalarını Git deposundan ayrı tutarak alternatif yedekleme yöntemleri (örneğin, bulut depolama) kullanılabilir.

2. **Dosya Sıkıştırma**  
   - Depoya eklemeden önce büyük dosyaları sıkıştırarak boyutunu azaltabilirsiniz.  
   - **Örnek:**  

     ```bash
     zip büyük_dosya.zip büyük_dosya.psd
     git add büyük_dosya.zip
     ```  

---

## **4. En İyi Uygulamalar**

1. **`gitignore` Dosyasını Kullanın:**  
   - Büyük veya gereksiz dosyaların yanlışlıkla depoya eklenmesini önlemek için.  
   - Örnek `.gitignore` girişi:  

     ```text
     *.log
     *.mp4
     ```

2. **Depo Boyutunu İzleyin:**  
   - Depo boyutunu kontrol altında tutmak için `git-sizer` gibi araçları kullanabilirsiniz.  

3. **Depo Temizliği Yapın:**  
   - Kullanılmayan dosyaları düzenli olarak silin ve gereksiz commit’leri temizleyin.  

---

## **5. Hands-On Görevler**

### **Görev 1: Büyük Bir Dosyayı Yönetmek**

- Katılımcılar, büyük bir dosyayı `git lfs` ile takip eder ve depo performansını değerlendirir.  

### **Görev 2: Geçmişten Bir Dosya Silmek**

- Katılımcılar, eski bir commit’te gereksiz bir dosyayı `git filter-repo` ile kaldırır.  
