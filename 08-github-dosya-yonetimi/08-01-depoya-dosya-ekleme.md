# **Modül 8: GitHub’da Dosya Yönetimi**

## **Dosya Ekleme ve Yönetme**

GitHub, yazılım geliştirme süreçlerinde dosyaların etkili bir şekilde eklenmesi, yönetilmesi ve izlenmesi için güçlü araçlar sağlar. Bu modülde, dosya ekleme ve yönetimi ile ilgili temel yöntemleri öğreneceksiniz.

---

## **1. Depoya Dosya Ekleme**

### **Dosya Ekleme Yöntemleri**

GitHub’a dosya eklemek için aşağıdaki yöntemlerden birini kullanabilirsiniz:

1. **Git Komut Satırı ile Dosya Ekleme**
2. **GitHub Web Arayüzü Üzerinden Dosya Ekleme**
3. **GitHub Desktop veya Diğer Git GUI Araçları Kullanarak**

---

### **Git Komut Satırı ile Dosya Ekleme**

**Adım 1: Yeni Bir Dosya Oluşturma**  
Öncelikle, projenizde bir dosya oluşturun veya var olan bir dosyayı güncelleyin.

**Örnek Komutlar:**

```bash
echo "Bu bir test dosyasıdır." > test.txt
```

**Adım 2: Dosyayı Takip Edin (Add)**
Git, yeni eklenen dosyaları takip etmeye başlamalıdır:

```bash
git add test.txt
```

**Adım 3: Değişiklikleri Kaydedin (Commit)**
Dosyanın depoya kaydedilmesi için bir commit mesajı yazın:

```bash
git commit -m "feat: Yeni bir test dosyası eklendi."
```

**Adım 4: Uzak Depoya Gönderin (Push)**
Son olarak, değişiklikleri GitHub’a gönderin:

```bash
git push origin main
```

---

### **GitHub Web Arayüzü Üzerinden Dosya Ekleme**

1. GitHub hesabınıza giriş yapın ve ilgili depoya gidin.
2. **Add file** düğmesine tıklayın ve **Upload files** veya **Create new file** seçeneğini belirleyin.
3. Dosyanızı ekleyin veya içerik oluşturun.
4. Değişiklikleri açıklayan bir commit mesajı girerek dosyayı depoya kaydedin.

---

## **2. Depoya Dosya Ekleme Senaryoları**

### **Senaryo: Yeni Bir Proje Dosyasını Eklemek**

**Durum:**  
Projenizde bir README dosyası oluşturmanız gerekiyor.

**Çözüm:**  

1. Komut satırını kullanarak yeni bir README dosyası oluşturun:

   ```bash
   echo "# Proje Başlığı" > README.md
   ```

2. Dosyayı ekleyin ve commit edin:

   ```bash
   git add README.md
   git commit -m "docs: README dosyası eklendi."
   git push origin main
   ```

**Hands-On:**  
Eğitim sırasında katılımcılar kendi projeleri için bir README dosyası oluşturacak ve GitHub’a yükleyecek.

---

### **Senaryo: Birden Fazla Dosyayı Aynı Anda Eklemek**

**Durum:**  

Projenize birkaç yeni kaynak dosyası eklendi ve bunların tümünü GitHub’a yüklemek istiyorsunuz.

**Çözüm:**

1. Dosyaları oluşturun:

   ```bash
   touch index.html style.css app.js
   ```

2. Tüm dosyaları tek seferde ekleyin:

   ```bash
   git add .
   ```

3. Değişiklikleri kaydedin ve uzak depoya gönderin:

   ```bash
   git commit -m "feat: Yeni proje dosyaları eklendi."
   git push origin main
   ```

**Hands-On:**  
Katılımcılar, birden fazla dosya ekleyerek projelerini güncelleyecek.

---

## **3. Dosyaları Güncelleme ve Silme**

### **Dosyaları Güncelleme**

Depoda bulunan bir dosyayı güncellemek için:

1. Dosyayı düzenleyin.
2. Düzenlemeleri takip etmek için `git add` komutunu kullanın.
3. Güncellemeyi kaydedin (`commit`) ve uzak depoya gönderin (`push`).

**Örnek:**

```bash
echo "Yeni satır eklendi." >> test.txt
git add test.txt
git commit -m "fix: test.txt dosyasına yeni satır eklendi."
git push origin main
```

### **Dosyaları Silme**

Bir dosyayı depodan silmek için:

1. Dosyayı yerel makinenizden kaldırın:

   ```bash
   rm test.txt
   ```

2. Silme işlemini Git'e bildirin:

   ```bash
   git add test.txt
   ```

3. Değişiklikleri kaydedin:

   ```bash
   git commit -m "chore: test.txt dosyası silindi."
   git push origin main
   ```

---

## **4. Dosya Yönetimi İçin En İyi Uygulamalar**

1. **Anlamlı Commit Mesajları Yazın:**  
   Dosya ekleme veya güncelleme işlemleriniz için açıklayıcı commit mesajları kullanın.
   Örnek:  
   - `feat: Yeni özellik belgeleri eklendi.`
   - `fix: Çalışmayan bağlantı düzeltildi.`

2. **Dosya Hiyerarşisi Kullanın:**  
   Projelerinizi düzenli tutmak için dosyaları belirli bir klasör yapısı altında organize edin.

3. **.gitignore Dosyasını Kullanın:**  
   Depoya dahil edilmemesi gereken dosyaları (örneğin, geçici dosyalar veya yapı artefaktları) `.gitignore` dosyasında belirtin.

---

## **5. Hands-On: GitHub’da Dosya Yönetimi**

### **Görev 1: Yeni Dosya Ekleme**

- Projeye yeni bir dosya ekleyin ve commit edin.
- Dosyayı uzak depoya gönderin.

### **Görev 2: Dosya Güncelleme**

- Daha önce eklediğiniz dosyada bir değişiklik yapın.
- Değişiklikleri commit edin ve uzak depoya gönderin.

### **Görev 3: Dosya Silme**

- Depodaki bir dosyayı yerel makinenizden silin ve uzak depoya bu değişikliği gönderin.

---

### **Sonuç**

Bu modülde, GitHub üzerinde dosya ekleme, güncelleme ve silme işlemlerinin nasıl yapıldığını öğrendiniz. Hands-on aktiviteler ile öğrendiklerinizi uygulama fırsatı buldunuz. Bu bilgi, GitHub projelerinde etkili dosya yönetimi için temel oluşturur.
