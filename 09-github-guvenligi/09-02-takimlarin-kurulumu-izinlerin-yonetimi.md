# **Takımların Kurulumu ve İzinlerin Yönetimi**  

GitHub, projelerde iş birliğini kolaylaştırmak için **takımlar** (teams) ve **izin yönetimi** özellikleri sunar. Bu özellikler, kullanıcı rollerini organize etmeyi ve erişim seviyelerini verimli bir şekilde kontrol etmeyi sağlar.  

---

## **1. Takımların Rolü ve Yapılandırılması**

### **a. Takım Nedir?**

- Takımlar, belirli bir organizasyon içindeki kullanıcıların gruplandırıldığı bir yapıdır.  
- Her takımın birden fazla projeye erişim yetkisi olabilir ve izin seviyeleri özelleştirilebilir.

---

### **b. Takım Türleri**

1. **Core Team (Çekirdek Takım):**  
   - Projenin ana geliştirme ekibini içerir.  
   - **Write** veya **Maintain** yetkileri verilir.  

2. **Review Team (İnceleme Takımı):**  
   - Pull request ve kod incelemesi yapan üyeler.  
   - **Read** veya **Triage** izinleri atanabilir.  

3. **Support Team (Destek Takımı):**  
   - Issues üzerinde çalışan ve topluluğa destek sağlayan üyeler.  
   - Genellikle **Triage** izni verilir.  

---

## **2. Takım Oluşturma ve Yönetimi**

### **a. Takım Nasıl Oluşturulur?**

1. **Organizasyon Ayarlarına Gidin:**  
   - `Settings > Teams` sekmesine tıklayın.  

2. **Yeni Bir Takım Ekleyin:**  
   - `Create a Team` butonuna basarak takım ismi ve açıklaması girin.  

3. **Üyeleri ve Projeleri Ekleyin:**  
   - Takıma kullanıcılar ekleyin.  
   - Projeleri ve erişim seviyelerini tanımlayın.  

---

### **b. Erişim Seviyeleri Yönetimi**

GitHub’da takımlara aşağıdaki erişim seviyeleri atanabilir:

- **Read:** Depoyu görüntüleme ve issues üzerinde geri bildirim sağlama.  
- **Write:** Kendi değişikliklerini yazma ve pull request oluşturma.  
- **Maintain:** Dalları yönetme, issues ve pull request’leri kapatma.  
- **Admin:** Tam yetkili erişim, depo ayarlarını değiştirme.

---

## **3. Senaryolar ve Çözümler**

### **Senaryo 1: Yeni Bir Projede Takım ve İzinlerin Yapılandırılması**

**Durum:**  
Yeni bir projede çekirdek geliştirme ekibi ve kod inceleme ekibi oluşturmanız gerekiyor.

**Çözüm:**  

1. Çekirdek ekip için bir takım oluşturun ve **Write** izni verin.  
2. Kod inceleme ekibi için ayrı bir takım oluşturun ve **Triage** izni verin.  
3. Projenin ana dalı için dal koruma kuralları ekleyin.  

**Hands-On Görev:**  

- Katılımcılar iki takım oluşturur ve farklı erişim seviyeleriyle projeye ekler.  
- Dalları korumak için kurallar uygular.  

---

### **Senaryo 2: Organizasyonda Yeni Bir Katılımcının Eklemesi**

**Durum:**  
Destek ekibine yeni bir kullanıcı katılıyor ve yalnızca issues yönetme izni verilmesi gerekiyor.

**Çözüm:**  

1. Kullanıcıyı organizasyona ekleyin.  
2. Destek ekibine atayın ve **Triage** izni verin.  

**Hands-On Görev:**  

- Katılımcılar, yeni bir kullanıcı ekleyerek yalnızca issues yönetim izni verir.  
- Destek ekibine eklenen kullanıcı bir issue oluşturur ve yanıtlar.  

---

### **Senaryo 3: Ekip Üyesinin Ayrılması**

**Durum:**  
Bir ekip üyesi projeden ayrılıyor ve erişiminin kaldırılması gerekiyor.

**Çözüm:**  

1. Kullanıcıyı ilgili takımdan kaldırın.  
2. Organizasyon erişimlerini gözden geçirerek erişimin tamamen kaldırıldığından emin olun.  

**Hands-On Görev:**  

- Katılımcılar, bir kullanıcıyı takımdan çıkarır ve erişimlerini kontrol eder.  

---

## **4. Güvenlik İçin En İyi Uygulamalar**

1. **Rolleri Düzenli Gözden Geçirin:**  
   - Projelerdeki izin seviyelerini düzenli olarak kontrol edin.  

2. **Minimum İzin Verin:**  
   - Kullanıcılara yalnızca ihtiyaç duydukları izin seviyelerini sağlayın.  

3. **Kritik Dallar İçin Koruma Kuralları Kullanın:**  
   - Çekirdek geliştirme ekipleri haricindeki kullanıcıların ana dalda doğrudan değişiklik yapmasını engelleyin.  

4. **Takım Hiyerarşisi:**  
   - Takımları, kullanıcılar yerine projelerdeki rollerine göre yapılandırın.  

---

## **5. Hands-On Görevler**

### **Görev 1: Takım Oluşturma ve Üye Ekleme**

- Yeni bir takım oluşturun, kullanıcıları ekleyin ve projelere erişim izni verin.  

### **Görev 2: Erişim Seviyeleri Testi**

- Farklı takımlara atanmış kullanıcıların izinlerini test edin (ör. sadece issues görüntüleme, kod yazma).  

### **Görev 3: Kritik Dallar için Koruma**

- Ana dalda doğrudan push yapılmasını engelleyen bir kural oluşturun.  

---

## **Sonuç**

GitHub'da takımlar ve izin yönetimi, projelerinizi güvenli ve düzenli bir şekilde yürütmek için kritik öneme sahiptir. Bu modülde, takımları yapılandırmayı, kullanıcı erişim seviyelerini yönetmeyi ve organizasyonunuzu güvenli hale getirmeyi öğrendiniz. Uygulamalı görevlerle, bu bilgileri pratiğe dökerek projelerinizde etkili bir iş birliği sağlayabilirsiniz.
