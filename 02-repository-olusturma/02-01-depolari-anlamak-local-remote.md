# **Depoları Anlamak: Yerel (Local) ve Uzak (Remote) Depoların Farkı**

Git, yazılım geliştirme süreçlerinde projelerin geçmişini takip etmek için kullanılan bir versiyon kontrol sistemi olarak, **yerel** ve **uzak** olmak üzere iki tür depo (repository) kullanır. Her birinin farklı görevleri ve kullanım amaçları vardır. 

---

## **1. Yerel (Local) Depo Nedir?**

**Yerel depo**, bir Git projesinin bilgisayarınızda bulunan tam kopyasıdır. Git, projeyi yerel olarak yönetir ve geliştirici tüm değişiklikleri, commit'leri ve dallanmayı (branching) yerel depoda tutar. 

Yerel depo, üç ana bileşenden oluşur:

- **Work Directory (Çalışma Dizini)**: Proje dosyalarının bulunduğu yer.
- **Staging Area (Hazırlık Alanı)**: Değişikliklerin commit edilmeden önce bekletildiği yer.
- **Git Directory (Git Deposu)**: Git’in tüm geçmişi (commitler), dallar ve versiyon bilgilerini sakladığı yer.

Yerel depo, internet bağlantısı gerektirmeden çalışır. Yani, projede yapılan değişiklikler ve commit'ler sadece yerel ortamda tutulur.

### **Yerel Depo Kullanımı:**

- **İnternet Bağlantısı Gereksiz**: Yerel depo, internet bağlantısına ihtiyaç duymaz, bu sayede offline çalışma mümkündür.
- **Commit**: Yapılan değişiklikler yerel depoda commit edilir. Bu işlem sadece kişisel bilgisayarınızda kaydedilir.

---

## **2. Uzak (Remote) Depo Nedir?**

**Uzak depo**, GitHub, GitLab, Bitbucket gibi bir platformda barındırılan Git reposudur. Uzak depo, projeyi internet üzerinden erişilebilir kılar ve geliştiricilerin projede iş birliği yapmalarını sağlar. Genellikle bir takımın çalıştığı merkezi depo olarak kullanılır.

Uzak depo, tüm ekip üyelerinin erişebileceği tek kaynaktır ve genellikle her projenin **“origin”** (ilk) uzak deposu olur. Uzak depolar, genellikle **bulut** üzerinde barındırılır, bu da her yerde erişilebilir olmalarını sağlar.

### **Uzak Depo Kullanımı:**

- **İnternet Bağlantısı Gerektirir**: Uzak depo, internet bağlantısı gerektirir ve GitHub gibi platformlarda barındırılır.
- **Push & Pull**: Uzak depodaki değişiklikler yerel depoya "pull" (çekme) ile alınabilir ve yerel değişiklikler uzak depoya "push" (gönderme) ile aktarılabilir.

---

## **3. Yerel ve Uzak Depoların Temel Farkları**

| Özellik              | **Yerel Depo (Local)**                   | **Uzak Depo (Remote)**               |
|----------------------|------------------------------------------|--------------------------------------|
| **Tanım**            | Geliştiricinin kendi bilgisayarındaki proje kopyasıdır. | Git platformlarında (GitHub, GitLab) barındırılan merkezi depo. |
| **Bağlantı Gereksinimi** | İnternet bağlantısı gerektirmez.         | İnternet bağlantısı gereklidir.     |
| **Kullanıcı**        | Yerel depo, tek bir geliştiricinin kullanımına yöneliktir. | Uzak depo, birden fazla geliştiriciye açık ve erişilebilir olmalıdır. |
| **Veri Depolama**    | Sadece tek bir bilgisayarın üzerinde veri tutulur. | Proje verileri tüm geliştiriciler tarafından erişilebilir şekilde merkezi bir sunucuda depolanır. |
| **Değişiklikler**    | Yerel depoda yapılan değişiklikler sadece o bilgisayar üzerinden görülür. | Uzak depoda yapılan değişiklikler tüm ekibin erişimine sunulur. |
| **Bağlantı**         | Yerel depo doğrudan uzak depo ile bağlantı kurmaz, ancak bir bağlantı oluşturulabilir. | Uzak depo, birden fazla yerel depodan erişilebilir ve veri alışverişi yapılabilir. |

---

## **4. Yerel ve Uzak Depolar Arasındaki İletişim**

Yerel ve uzak depolar arasındaki işleyiş, genellikle aşağıdaki iki temel komutla yönetilir:

### **Push (Gönderme)**

`git push` komutu, yerel deponuzdaki değişiklikleri uzak depoya gönderir. Uzak depoya gönderim yapabilmek için, genellikle **push** yapmadan önce **commit** işlemi yapılmalıdır.

Örnek:

```bash
git push origin main
```

Bu komut, `main` dalındaki yerel değişiklikleri uzak depodaki `main` dalına gönderir.

### **Pull (Çekme)**

`git pull` komutu, uzak depodaki değişiklikleri yerel deponuza çeker. Bu komut, uzak depo ile yerel depo arasındaki farkları senkronize eder.

Örnek:

```bash
git pull origin main
```

Bu komut, uzak depodaki `main` dalındaki en son değişiklikleri yerel deponuza çeker.

---

## **5. Senaryo Örnekleri ve Hands-On Uygulamalar**

### **Senaryo 1: Yerel Depoda Çalışma ve Değişiklik Gönderme**

**Durum:**
Bir yazılım geliştiricisi, yerel depoda bir hata düzeltmesi yaptı ve bu değişikliği uzak depoya göndermek istiyor.

**Adımlar:**

1. **Yerel Depoda Çalışma:**
   - Projenin yerel kopyasında gerekli değişiklikleri yapın.

   ```bash
   echo "Bug fix applied" > fix.txt
   git add fix.txt
   git commit -m "Fixed bug in app"
   ```

2. **Uzak Depoya Push:**
   - Değişiklikleri uzak depoya göndermek için `git push` komutunu kullanın.

   ```bash
   git push origin main
   ```

**Hands-On:**
Eğitmenle birlikte bir değişiklik yapın ve bu değişikliği yerel depodan uzak depoya nasıl göndereceğinizi öğrenin.

---

### **Senaryo 2: Uzak Depodan Değişiklik Çekme**

**Durum:**
Bir ekip üyesi uzak depoya bir özellik ekledi ve şimdi bu değişiklikleri yerel bilgisayarınıza almak istiyorsunuz.

**Adımlar:**

1. **Uzak Depodan Çekme:**
   - `git pull` komutuyla uzak depodaki en son değişiklikleri yerel deponuza çekin.

   ```bash
   git pull origin main
   ```

2. **Değişiklikleri İnceleme:**
   - Çekilen değişiklikleri inceleyin ve gerekirse kendi değişikliklerinizi ekleyin.

**Hands-On:**
Eğitmenle birlikte uzak depodan değişiklikleri çekin ve proje üzerinde nasıl senkronize çalışılacağını gözlemleyin.

---

### **Senaryo 3: Yerel ve Uzak Depolar Arasında Çakışma Çözümü**

**Durum:**
İki geliştirici aynı dosyada farklı değişiklikler yaptı ve bu değişiklikler birleştirilmeye çalışıldığında çakışma oluştu.

**Adımlar:**

1. **Çakışmanın Tespiti:**
   - Birleştirme işlemi sırasında çakışmanın tespit edilmesi için:

   ```bash
   git pull origin main
   ```

2. **Çakışmayı Çözme:**
   - Git, çakışan dosyaları işaretler. Bu dosyaları manuel olarak çözün.

3. **Çözümü Commit Etme:**
   - Çakışmalar çözüldükten sonra, dosyaları yeniden commit edin.

   ```bash
   git add .
   git commit -m "Resolved merge conflict"
   git push origin main
   ```

**Hands-On:**
Ekip içinde bir proje oluşturun ve çakışmalarla ilgili uygulamalı çözümleme yapın.

---

## **Sonuç ve Değerlendirme**

Yerel ve uzak depolar, Git'in temel yapı taşlarını oluşturur ve her birinin kendine özgü avantajları vardır. Yerel depolar, bireysel olarak geliştirme yapmanızı sağlarken, uzak depolar ekiplerin iş birliği yapabilmesi ve proje üzerinde eşzamanlı çalışabilmesi için gereklidir. Bu iki depo tipi arasında yapılan push ve pull işlemleri, geliştirme süreçlerini senkronize eder ve ekip üyeleri arasında uyumlu bir çalışma ortamı sağlar.
