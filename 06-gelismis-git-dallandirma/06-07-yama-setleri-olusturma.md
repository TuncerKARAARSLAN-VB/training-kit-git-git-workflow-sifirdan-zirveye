# **Yama Setleri (Patch Sets) Oluşturma: Git ile Değişiklik Yönetimi**

Git, yazılım geliştirme sürecinde yapılan değişiklikleri takip etme, organize etme ve paylaşma konusunda güçlü araçlar sunar. Bu araçlardan biri de **patch set** (yama setleri) olarak bilinen özelliktir. Patch setleri, bir veya birden fazla commit'in içeriğini dışa aktararak başka bir depoya veya proje sürümüne uygulamak için kullanılır. Bu yöntem, değişikliklerin taşınabilirliğini artırır ve yazılım projeleri arasında paylaşılmasını kolaylaştırır.

---

## **1. Patch Set Nedir?**

Git'teki **patch** terimi, bir dosya veya bir dizi dosya üzerindeki değişiklikleri temsil eden bir farktır (diff). **Patch set** ise, bir veya birden fazla commit'in içeriğini içeren bir koleksiyondur. Yama setleri, genellikle bir geliştirme dalındaki değişikliklerin başka bir dalda veya projede uygulanmasını sağlamak için kullanılır.

Patch set, genellikle aşağıdaki durumlarda kullanılır:

- **Aynı değişikliklerin birden fazla projeye veya depoya uygulanması**.
- **Commit'leri dışa aktararak taşınabilir hale getirme**.
- **Birden fazla commit'i birleştirerek tek bir yama dosyası oluşturma**.

---

## **2. Patch Set Oluşturma Adımları**

Patch set oluşturmanın temel adımları şunlardır:

### **Adım 1: Değişiklikleri Hazırlama**

İlk olarak, patch set'e dahil edilmek istenen commit'lerin bulunduğu dalda çalışmanız gerekir. Bu dalda yapılan değişiklikler, patch olarak dışa aktarılacak.

Örnek:

- `feature/user-registration` dalında birkaç commit yapılmış olsun.
- Bu commit'lerin her biri, kullanıcı kaydı ile ilgili geliştirmeleri içeriyor.

### **Adım 2: Git Diff ile Patch Oluşturma**

Patch oluşturmak için `git diff` komutu kullanılabilir. Bu komut, iki commit arasındaki farkları gösterir ve bunları bir yama dosyasına çıkartmak için kullanılabilir.

Örnek:

```bash
git diff commit1 commit2 > my-patch.patch
```

Bu komut, `commit1` ile `commit2` arasındaki farkları içeren bir `.patch` dosyası oluşturur.

### **Adım 3: Patch Set’i Birleştirme (Opsiyonel)**

Eğer birden fazla commit'in değişikliklerini tek bir patch set olarak dışa aktarmak istiyorsanız, bu commit'leri tek bir dosyada birleştirmeniz gerekir. Bunun için `git format-patch` komutunu kullanabilirsiniz.

Örnek:

```bash
git format-patch -n <commit_hash>
```

Bu komut, belirtilen commit'ten başlayarak tüm commit'leri `.patch` dosyalarına dönüştürür. Burada `-n` seçeneği, çıkartılacak patch sayısını belirtir.

---

## **3. Patch Set’i Uygulama (Patch’i Uygulama)**

Bir patch set oluşturulduktan sonra, başka bir projeye veya dalda bu patch set'ini uygulamak gerekir. Bunun için `git apply` veya `git am` komutları kullanılabilir.

### **Git Apply Kullanımı**

`git apply`, bir patch dosyasını mevcut çalışma dizinine uygular.

Örnek:

```bash
git apply my-patch.patch
```

Bu komut, `my-patch.patch` dosyasındaki değişiklikleri çalışma dizininize uygular.

### **Git Am Kullanımı**

`git am`, bir patch set'ini alır ve her patch’i bir commit olarak uygular.

Örnek:

```bash
git am < my-patch.patch
```

Bu komut, `.patch` dosyasındaki tüm değişiklikleri tek tek commit olarak uygular.

---

## **4. Patch Set Kullanım Senaryoları ve Uygulamalar**

### **Senaryo 1: Çift Dalda Çalışmak ve Patch Set Kullanmak**

Bir yazılım geliştirme sürecinde, bir geliştirici `feature/user-login` dalında çalışıyor ve yaptığı değişiklikleri başka bir dalda, örneğin `feature/user-profile` dalında da kullanmak istiyor. Bu durumda patch set kullanmak çok yararlı olabilir.

1. `feature/user-login` dalındaki commit’leri dışa aktarmak için patch oluşturulur:

   ```bash
   git format-patch -1 HEAD
   ```

2. Oluşturulan patch dosyası, `feature/user-profile` dalına uygulanır:

   ```bash
   git checkout feature/user-profile
   git am < user-login.patch
   ```

3. Bu işlem ile, `feature/user-login` dalındaki yapılan değişiklikler, `feature/user-profile` dalına aktarılır ve her iki dalda da paralel geliştirme yapılabilir.

**Hands-On:**

- Katılımcılara bir projede iki farklı dalda çalışmaları için bir görev verin.
- Bir dalda yapılan commit’leri dışa aktarın ve diğer dalda patch set olarak uygulamalarını sağlayın.

---

### **Senaryo 2: Açık Kaynak Projesine Katkı Sağlamak**

Bir açık kaynak projesine katkıda bulunmak için yapılan değişiklikler önce bir fork üzerinde çalışılır. Değişiklikler, patch set olarak dışa aktarılır ve orijinal projeye uygulanabilir.

1. Katkı yapılacak proje fork edilir ve geliştirme yapılır.
2. Yapılan değişiklikler, patch set olarak dışa aktarılır:

   ```bash
   git format-patch origin/main
   ```

3. Katkılar orijinal projeye gönderilir.

**Hands-On:**

- Katılımcılara bir açık kaynak projeye katkıda bulunma sürecini simüle etmelerini sağlayın.
- Forklama, patch oluşturma ve orijinal projeye gönderme işlemlerini uygulamalı olarak gösterin.

---

## **5. Patch Set’leri Yönetme ve İleri Seviye Kullanım**

Patch set’lerini yönetmek için aşağıdaki araçlar ve komutlar kullanılabilir:

### **Patch Dosyalarını Yönetme:**

Birden fazla patch dosyasını yönetmek için `git am` ile birden fazla dosya uygulanabilir.

Örnek:

```bash
git am *.patch
```

### **Patch’i Geri Almak:**

Bir patch set’i yanlışlıkla uygularsanız, değişiklikleri geri almak için `git am --abort` komutunu kullanabilirsiniz.

Örnek:

```bash
git am --abort
```

---

## **6. Sonuç ve Katılımcı Değerlendirmesi**

Patch set’leri oluşturmak ve kullanmak, yazılım geliştirme sürecini daha taşınabilir ve esnek hale getirir. Özellikle çoklu projelerde veya ekiplerle çalışırken, değişikliklerin bir yerden bir yere aktarılması, işleri kolaylaştırır ve hataları azaltır. Eğitim boyunca, patch set’leri nasıl oluşturulacağı, uygulanacağı ve yönetileceği konusunda bilgi edinmiş oldunuz. Uygulamalı çalışmalarla bu becerilerinizi geliştirerek daha verimli bir yazılım geliştirme süreci sağlayabilirsiniz.
