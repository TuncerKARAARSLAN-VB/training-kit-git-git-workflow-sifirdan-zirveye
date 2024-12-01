# **Depo Aktivitelerinin İzlenmesi**

Git ve GitHub, bir yazılım projesinin aktivite geçmişini detaylı bir şekilde inceleme ve izleme imkânı sunar. Depo aktivitelerinin izlenmesi, ekip iş birliğini geliştirme, değişikliklerin etkisini anlama ve sorunları hızlıca çözme açısından kritik öneme sahiptir.

---

## **1. Depo Aktivitelerini İzlemenin Önemi**

### **a. Neden İzlenmeli?**

1. **Değişikliklerin Görünürlüğü:**  
   Hangi dosyaların kim tarafından, ne zaman ve neden değiştirildiğini bilmek ekip koordinasyonunu sağlar.
   
2. **Hata Tespiti ve Çözümü:**  
   Sorunlu commit’leri bulup geri alarak yazılımın kararlılığını artırabilirsiniz.

3. **Ekip Performansı ve İş Birliği:**  
   Kimlerin hangi katkılarda bulunduğunu görmek, proje planlaması ve değerlendirme süreçlerini kolaylaştırır.

---

## **2. Araçlar ve Yöntemler**

### **a. Git Komutları ile İzleme**

- **`git log`:** Depodaki commit geçmişini gösterir.  

   ```bash
   git log
   ```

   **Kullanım Örnekleri:**

   - **Kısa Özet:**

     ```bash
     git log --oneline
     ```

   - **Belirli Kullanıcıya Göre Filtreleme:**

     ```bash
     git log --author="Kullanıcı Adı"
     ```

- **`git diff`:** İki commit arasındaki değişiklikleri gösterir.  

   ```bash
   git diff <commit1> <commit2>
   ```

- **`git blame`:** Bir dosyadaki her satırın kim tarafından ve ne zaman değiştirildiğini gösterir.  

   ```bash
   git blame <dosya_adi>
   ```

---

### **b. GitHub Arayüzü ile İzleme**

- **Insights > Pulse:**  
  Depodaki son değişiklikleri, açık ve kapalı pull request’leri ve diğer aktiviteleri gösterir.

- **Commit Geçmişi:**  
  GitHub arayüzünde, "Commits" sekmesi altında tüm commit’lerin detaylarına erişebilirsiniz.

- **Issues ve Pull Requestler:**  
  Hangi kullanıcıların hangi konular üzerinde çalıştığını görebilir, aktivite takibi yapabilirsiniz.

---

## **3. Senaryo ve Uygulamalar**

### **Senaryo 1: Son Değişikliklerin Kontrolü**

**Durum:**  
Bir proje yöneticisi, ekip üyelerinin son bir hafta içinde yaptığı değişiklikleri kontrol etmek istiyor.

**Çözüm:**  

1. `git log` komutunu tarih aralığına göre kullanın:  

   ```bash
   git log --since="1 week ago"
   ```

2. GitHub arayüzünde "Insights > Pulse" sekmesine göz atın.

**Hands-On:**  
Katılımcılar, belirli bir tarih aralığındaki değişiklikleri filtreler ve bu değişiklikleri analiz eder.

---

### **Senaryo 2: Sorunlu Commit’in Bulunması**

**Durum:**  
Son commit’lerden biri, projede hata oluşturdu ve sorunun hangi değişiklikten kaynaklandığı bilinmiyor.

**Çözüm:**  

1. `git log` ile commit geçmişine göz atın ve hatalı commit’i belirleyin.  
2. `git diff` kullanarak değişiklikleri inceleyin.  
3. Gerekirse, `git revert` veya `git reset` ile hatalı commit’i geri alın.

**Hands-On:**  
Katılımcılar, hatalı bir commit simüle eder ve bunu bulup geri alır.

---

### **Senaryo 3: Ekip Üyelerinin Katkılarının İzlenmesi**

**Durum:**  
Bir proje yöneticisi, ekip üyelerinin bireysel katkılarını incelemek istiyor.

**Çözüm:**  

1. `git log --author` ile belirli bir kullanıcının yaptığı değişiklikleri bulun:  

   ```bash
   git log --author="Kullanıcı Adı"
   ```

2. GitHub’da, her kullanıcının katkı geçmişine göz atın (Contributors sekmesi).

**Hands-On:**  
Katılımcılar, kendi commit’lerini filtreler ve analiz eder.

---

### **Senaryo 4: Dosya Bazında Değişikliklerin İzlenmesi**

**Durum:**  
Bir ekip üyesi, belirli bir dosyada yapılan tüm değişiklikleri görmek istiyor.

**Çözüm:**  

1. `git log` ile dosya değişiklik geçmişini görüntüleyin:  

   ```bash
   git log -- <dosya_adi>
   ```

2. `git blame` ile satır bazında değişiklikleri inceleyin.

**Hands-On:**  
Katılımcılar, bir dosyadaki değişiklikleri analiz eder ve hangi commit’lerin bu dosyayı etkilediğini belirler.

---

## **4. En İyi Uygulamalar**

- **Küçük ve Anlamlı Commit’ler Yapın:** İzlemeyi kolaylaştırır.  
- **Commit Mesajlarına Özen Gösterin:** Mesajlar, değişikliklerin amacını açıklamalıdır.  
- **Düzenli Olarak `git log` Kullanın:** Projeye hakimiyeti artırır.  
- **GitHub’da Takipçi Kalın:** Pulse ve Insights araçlarını düzenli olarak kullanarak ekip aktivitelerini izleyin.
