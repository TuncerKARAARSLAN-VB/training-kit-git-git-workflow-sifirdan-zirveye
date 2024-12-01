# **GitHub’da Kullanıcı Rolleri ve İzin Seviyeleri**

GitHub, depolar üzerinde farklı kullanıcı rollerine farklı izinler verir. Bu izinler, bir kullanıcının bir projede hangi işlemleri gerçekleştirebileceğini belirler.

## **Izinler Depo Ayarları**

### **a. İzin Seviyeleri**

1. **Read (Okuma):**  
   - Depodaki kodu ve açık issues/pull requests’i görüntüleyebilir.  
   - Yazma izni yoktur.  

2. **Triage (Öncelik Belirleme):**  
   - Issues ve pull requests’i düzenleyebilir.  
   - Geri bildirim sağlayabilir.  

3. **Write (Yazma):**  
   - Yeni dallar oluşturabilir.  
   - Kendi değişikliklerini depoya yazabilir.  

4. **Maintain (Bakım):**  
   - Pull request birleştirebilir.  
   - Depodaki kullanıcı izinlerini yönetemez.  

5. **Admin (Yönetici):**  
   - Tam yetkilidir.  
   - Depo ayarlarını değiştirebilir ve kullanıcı erişimini yönetebilir.  

---

#### **b. Uygulama Alanları**

- Açık kaynak projelerde, katkıda bulunacak geliştiriciler genellikle **Read** veya **Triage** izniyle sınırlıdır.  
- Özel projelerde, **Write** ve **Admin** izinleri belirli rollere atanabilir.

---

### **2. Depo Ayarları ve Güvenlik Yönetimi**

GitHub'da güvenliği artırmak için depo ayarlarında birkaç yapılandırma seçeneği mevcuttur.

#### **a. Erişim Ayarları**

1. **Depo Görünürlüğü:**
   - **Public (Herkese Açık):** Tüm kullanıcılar depoyu görüntüleyebilir.  
   - **Private (Özel):** Sadece yetkilendirilmiş kullanıcılar erişebilir.  

2. **Branch Protection Rules (Dal Koruma Kuralları):**  
   - Ana dal üzerinde doğrudan değişiklik yapılmasını engelleyebilirsiniz.  
   - **Zorunlu Onay:** Pull request’lerin birleştirilmeden önce inceleme gerektirmesi.  

3. **2FA (İki Faktörlü Kimlik Doğrulama):**  
   - Güvenliği artırmak için tüm kullanıcılar için 2FA kullanımı zorunlu hale getirilebilir.  

---

### **3. Senaryolar ve Çözümler**

#### **Senaryo 1: Özel Bir Projede Katkı Sağlayanların Yetkilerini Yönetme**

**Durum:**  
Bir ekip üyesine kod yazma izni verilmesi gerekiyor, ancak ana dal üzerinde değişiklik yapmasını istemiyorsunuz.

**Çözüm:**  

1. Ekip üyesine **Write** izni verin.  
2. Ana dal için dal koruma kuralı ekleyin:  
   - `Settings > Branches > Branch protection rules` yolunu izleyin.  
   - Ana dalı seçin ve "Require pull request reviews" seçeneğini aktif edin.  

**Hands-On Görev:**  

- Katılımcılar, bir kullanıcıya **Write** izni atar ve ana dalda koruma kuralları oluşturur.  

---

#### **Senaryo 2: Bir Açık Kaynak Projede Güvenlik Sağlama**

**Durum:**  
Projeye katkıda bulunan kişiler, depo içeriğini değiştirmeden pull request göndermeli.

**Çözüm:**  

1. Projeyi **Public** olarak ayarlayın.  
2. Tüm katkıda bulunanların **Read** izniyle sınırlı olduğundan emin olun.  

**Hands-On Görev:**  

- Bir depo oluşturun ve katılımcıların pull request göndermesini sağlayın.  

---

### **4. Güvenlik İçin En İyi Uygulamalar**

1. **İki Faktörlü Kimlik Doğrulama (2FA):**  
   - Tüm kullanıcılar için zorunlu hale getirilmelidir.  

2. **Gizli Anahtarları ve Şifreleri Saklamayın:**  
   - API anahtarları ve şifreleri yanlışlıkla depoya eklenmemelidir.  
   - **Araç:** `git-secrets` veya GitHub’ın **Secret Scanning** özelliği.  

3. **Branch Protection Rules:**  
   - Önemli dallar için koruma kuralları belirleyin.  

4. **Erişimleri Düzenli Gözden Geçirin:**  
   - Artık projede yer almayan kullanıcıların erişimlerini kaldırın.  

---

### **5. Hands-On Görevler**

#### **Görev 1: Kullanıcı Rolleri Atama**

- Katılımcılar, bir projede farklı rollere sahip kullanıcılar ekler ve rolleri test eder.

#### **Görev 2: Branch Protection Kuralları Oluşturma**

- Ana dalda doğrudan push işlemini engellemek için dal koruma kuralları uygular.

#### **Görev 3: Gizli Anahtar Taraması**

- Katılımcılar, yanlışlıkla depoya eklenmiş API anahtarlarını tespit eder ve kaldırır.  
