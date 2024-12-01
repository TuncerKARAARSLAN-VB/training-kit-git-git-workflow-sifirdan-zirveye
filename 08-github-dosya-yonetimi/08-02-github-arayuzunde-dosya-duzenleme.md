# **GitHub Arayüzünde Dosya Düzenleme**

GitHub, kullanıcıların dosyaları doğrudan web arayüzünden düzenlemesine olanak tanır. Bu özellik, küçük düzenlemeler veya hata düzeltmeleri için hızlı ve kullanışlı bir yöntem sunar.

---

## **1. GitHub Arayüzünde Dosya Düzenleme Nedir?**

GitHub’ın web arayüzü üzerinden depodaki herhangi bir dosyayı:  

- **Hızlı bir şekilde güncelleyebilir**,  
- **Değişiklikleri açıklayan bir commit mesajı ekleyebilir** ve  
- **Doğrudan ana dalda veya farklı bir dalda** bu değişiklikleri kaydedebilirsiniz.  

---

## **2. GitHub Arayüzünde Dosya Düzenleme Adımları**

### **Adım 1: Düzenlenecek Dosyayı Seçme**

1. GitHub hesabınıza giriş yapın.  
2. İlgili depoya gidin ve düzenlemek istediğiniz dosyayı bulun.  
3. Dosyanın üzerine tıklayarak içeriğini görüntüleyin.  

---

### **Adım 2: Düzenleme Moduna Geçiş**

1. Sağ üst köşede bulunan **Edit this file** (Kalem ikonu) düğmesine tıklayın.  
2. Dosya, düzenlenebilir bir metin editörü modunda açılacaktır.  

---

### **Adım 3: Dosyada Değişiklik Yapma**

1. Gerekli düzenlemeleri yapın.  
2. Büyük dosyalar veya karmaşık yapılar için dikkatli olun; yalnızca küçük düzenlemeler için uygundur.  

---

### **Adım 4: Commit Mesajı Ekleme**

1. Dosya düzenlemesinden sonra, sayfanın altında bulunan **Commit changes** bölümüne gidin.  
2. Bir **başlık** ve isteğe bağlı olarak bir **açıklama** yazın:  
   - Başlık: Düzenlemenin ana amacı.  
   - Açıklama: Daha fazla detay (isteğe bağlı).  

Örnek:  

- Başlık: `fix: Yazım hatası düzeltildi`  
- Açıklama: `Proje açıklamasındaki yanlış kelimeler düzeltildi.`  

---

### **Adım 5: Commit Türünü Seçme**

1. **Doğrudan ana dala commit etme**: Değişiklikler doğrudan ana dala eklenir.  
2. **Yeni bir dal oluşturma ve pull request başlatma**: Değişiklikler için yeni bir dal oluşturulur ve inceleme süreci başlatılır.  

---

### **Adım 6: Commit’i Kaydetme**

1. Commit türünü belirledikten sonra **Commit changes** düğmesine tıklayın.  
2. Değişiklikler, belirlediğiniz dalda kaydedilir.  

---

## **3. Senaryo: GitHub Arayüzünde Bir README Dosyasını Düzenlemek**

### **Durum:**  

Projenizin README dosyasındaki bir yazım hatasını düzeltmeniz gerekiyor.

### **Çözüm:**  

1. Depoya gidin ve `README.md` dosyasını bulun.  
2. Dosyayı düzenleme modunda açın (**Edit this file** düğmesine tıklayın).  
3. Yazım hatasını düzeltin.  
4. Commit mesajını ekleyin:  
   - Başlık: `fix: README dosyasındaki yazım hatası düzeltildi.`  
   - Açıklama: `Başlık kısmındaki yanlış yazılan "Değerlendirme" kelimesi düzeltildi.`  
5. Değişikliği doğrudan ana dala commit edin.  

**Hands-On:**  
Katılımcılar, kendi depolarındaki bir README dosyasını düzenleyerek yazım hatalarını düzeltecek.

---

## **4. Senaryo: Kod Dosyasındaki Bir Hata Düzenlemesi**

### **Durum:**  

Bir JavaScript dosyasındaki `console.log` satırında bir hata var ve bunu hızlıca düzeltmek istiyorsunuz.

### **Çözüm:**  

1. İlgili dosyayı bulun (örneğin: `app.js`).  
2. **Edit this file** düğmesine tıklayın.  
3. Hatalı kodu düzeltin:  
   - Eski: `consol.log("Merhaba Dünya!");`  
   - Yeni: `console.log("Merhaba Dünya!");`  
4. Commit mesajını yazın:  
   - Başlık: `fix: console.log hatası düzeltildi.`  
5. Yeni bir dal oluşturun ve değişiklikleri bu dala commit edin.  

**Hands-On:**  
Katılımcılar, bir JavaScript dosyasındaki yazım hatasını düzeltecek ve değişiklikleri yeni bir dalda kaydedecek.

---

## **5. GitHub Arayüzünde Düzenleme için En İyi Uygulamalar**

1. **Küçük ve Net Düzenlemeler Yapın:**  
   Büyük dosyalar veya karmaşık değişiklikler için yerel bir düzenleme aracı kullanmayı tercih edin.  

2. **Anlamlı Commit Mesajları Yazın:**  
   Commit mesajlarını, yapılan düzenlemenin amacını açıkça belirtmek için kullanın.

3. **Dal Yönetimini Kullanın:**  
   Doğrudan ana dala commit etmek yerine, yeni bir dal oluşturup pull request başlatmayı tercih edin.  

4. **Kod Gözden Geçirme Sürecini Kullanın:**  
   Özellikle ekip projelerinde, yapılan düzenlemelerin diğer ekip üyeleri tarafından incelenmesini sağlayın.  

---

## **6. Hands-On Görevleri**

### **Görev 1: README Dosyasını Güncelleme**

- Projenizdeki README dosyasına bir satır ekleyin.  
- Commit mesajınızı yazın ve değişiklikleri doğrudan ana dala kaydedin.  

### **Görev 2: Kod Dosyasını Düzenleme**

- Bir `.js` veya `.py` dosyasındaki basit bir yazım hatasını düzeltin.  
- Değişikliği yeni bir dalda kaydedin ve pull request başlatın.  

---

## **Sonuç**

GitHub’ın arayüzünde dosya düzenleme, küçük değişiklikler veya hata düzeltmeleri için etkili bir yöntemdir. Bu modülde öğrendiğiniz adımları ve senaryoları kullanarak, projelerinizde hızlı ve doğru düzenlemeler yapabilirsiniz. Hands-on aktiviteler sayesinde bilgilerinizi uygulayarak pekiştirdiniz.
