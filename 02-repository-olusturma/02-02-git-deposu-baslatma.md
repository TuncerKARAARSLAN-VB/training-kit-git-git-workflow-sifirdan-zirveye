# **Depo Nasıl Oluşturulur? - Git Deposu Başlatma**

Git ile yazılım geliştirme sürecinde, bir projeyi versiyon kontrolüne almak için öncelikle bir Git deposu (repository) oluşturmanız gerekir. Bu depo, projenizin tüm geçmişini, yapılan değişiklikleri ve sürümleri saklar. Git deposu oluşturmanın birkaç farklı yolu ve bununla ilgili temel komutlar vardır. 

---

## **1. Yeni Bir Git Deposu Başlatma**

Yeni bir Git deposu oluşturmak için, önce terminal veya komut satırını açarak bir proje dizini oluşturmanız gerekir. Bu dizin içerisinde Git, projeyi takip etmeye başlayacak ve tüm değişiklikleri kaydedecektir.

### **Adımlar:**

1. **Yeni bir proje dizini oluşturun:**
   Git deposunu başlatmak için, önce projeyi saklayacağınız bir dizin oluşturmanız gerekiyor. Örneğin:

   ```bash
   mkdir my_project
   cd my_project
   ```

2. **Git deposu başlatma:**
   Proje dizinine gidip, aşağıdaki komutu kullanarak Git deposu başlatabilirsiniz:

   ```bash
   git init
   ```

   Bu komut, mevcut dizinde `.git` adında gizli bir klasör oluşturur. Bu klasör, Git’in projenizi takip etmek için kullandığı dosyaları içerir.

   **`git init` komutunun yaptığı şeyler:**
   - Mevcut dizinde bir Git depo klasörü oluşturur.
   - Bu dizini Git tarafından izlenen bir proje haline getirir.
   - Projeye ait tüm geçmişi kaydedebilecek bir sistem başlatır.

---

## **2. Git Konfigürasyonu**
Git depoları başlatıldığında, her kullanıcının kimlik bilgilerini belirlemek için bazı temel konfigürasyonlar yapılır. Bu, Git’in kimlerin değişiklik yaptığına dair doğru bilgileri kaydetmesi için gereklidir.

### **Adımlar:**

1. **Kullanıcı adı ve e-posta adresi belirleme:**
   Git, her commit’te kullanıcı adı ve e-posta adresini saklar. Aşağıdaki komutlarla Git’e bu bilgileri tanımlayabilirsiniz:

   ```bash
   git config --global user.name "Adınız"
   git config --global user.email "email@domain.com"
   ```

2. **Konfigürasyonu doğrulama:**
   Yapılandırmayı doğrulamak için aşağıdaki komutu kullanabilirsiniz:

   ```bash
   git config --list
   ```

   Bu komut, tüm Git yapılandırmalarını listeler.

---

## **3. Depoya İlk Dosyaları Ekleme**

Git deposu başlatıldıktan sonra, projedeki dosyaları Git takibine almak için bu dosyaları **staging area** (hazırlık alanı) ile eklemeniz gerekmektedir.

### **Adımlar:**

1. **Bir dosya oluşturun:**
   Yeni bir dosya ekleyin veya mevcut dosyaları ekleyin. Örneğin:

   ```bash
   echo "Hello World" > hello.txt
   ```

2. **Dosyayı Git’e ekleme (staging area):**
   Dosyayı Git takibine almak için şu komutu kullanın:

   ```bash
   git add hello.txt
   ```

   **`git add`** komutu, dosyayı Git’in staging alanına ekler, ancak henüz commit edilmemiştir.

3. **Değişiklikleri commit etme:**
   Dosyayı commit ederek, yaptığınız değişiklikleri Git deposuna kaydedebilirsiniz:

   ```bash
   git commit -m "İlk dosya eklendi"
   ```

   **`git commit`** komutu, yapılan değişiklikleri versiyon kontrolüne alır ve `.git` dizininde kaydeder. Commit mesajı, değişikliğin ne olduğunu belirtmek için kullanılır.

---

## **4. Uzak Depo Bağlantısı Kurma (Opsiyonel)**
Projenizi uzak bir Git platformuna (GitHub, GitLab, Bitbucket gibi) göndermek isterseniz, öncelikle uzak depo (remote repository) oluşturmanız ve ardından yerel deponuzu bu uzak depoya bağlamanız gerekir.

### **Adımlar:**

1. **Uzak depo oluşturma:**
   GitHub, GitLab veya Bitbucket üzerinde bir uzak depo oluşturun. Örneğin, GitHub üzerinde "my_project" adında bir repo oluşturduğunuzu varsayalım.

2. **Uzak depoyu yerel depoya ekleme:**
   Uzak depo bağlantısını eklemek için şu komutu kullanabilirsiniz:

   ```bash
   git remote add origin https://github.com/username/my_project.git
   ```

3. **Değişiklikleri uzak depoya gönderme (push):**
   Yerel depoda yaptığınız commit'leri uzak depoya göndermek için şu komutu kullanabilirsiniz:

   ```bash
   git push -u origin main
   ```

   Bu komut, yerel deponuzdaki `main` dalındaki değişiklikleri uzak depoya gönderir.

---

### **5. Depo Oluşturma Senaryoları ve Hands-On Uygulamalar**

#### **Senaryo 1: Yeni Bir Git Deposu Oluşturma ve İlk Commit Yapma**

**Durum:**
Yeni bir projeye başlıyorsunuz ve bu projeyi Git ile versiyon kontrolüne almak istiyorsunuz.

**Adımlar:**

1. Yeni bir proje dizini oluşturun ve bu dizine gidin.
2. Git deposu başlatın.
3. Proje dosyasını oluşturun ve Git’e ekleyin.
4. İlk commit’i yapın.

**Hands-On:**
Eğitmenle birlikte bir proje oluşturun ve yukarıdaki adımları takip ederek ilk Git commit’inizi yapın.

---

#### **Senaryo 2: Uzak Depo İle Çalışma**

**Durum:**
Uzak bir Git depoya bağlanarak, projeyi çevrimiçi bir platformda yönetmek istiyorsunuz.

**Adımlar:**

1. GitHub üzerinde yeni bir depo oluşturun.
2. Uzak depoyu yerel deponuza ekleyin.
3. Değişikliklerinizi uzak depoya gönderin.

**Hands-On:**
Eğitmenle birlikte GitHub’da bir uzak depo oluşturun ve bu depoyu yerel deponuza bağlayarak ilk gönderiminizi yapın.

---

### **Sonuç ve Değerlendirme**

Git deposu başlatma, yazılım geliştirme sürecinin temel adımlarından biridir. Yerel ve uzak depolar arasındaki işleyişi anlamak, versiyon kontrolünün verimli bir şekilde kullanılmasını sağlar. Bu süreçte kullanılan komutlar (`git init`, `git add`, `git commit`, `git push`) geliştiricilerin projelerini güvenli bir şekilde yönetmelerine ve iş birliği yapmalarına olanak tanır.
