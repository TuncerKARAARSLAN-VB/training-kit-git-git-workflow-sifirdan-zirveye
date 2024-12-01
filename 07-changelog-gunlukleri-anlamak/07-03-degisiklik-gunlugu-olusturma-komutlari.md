# **Değişiklik Günlüğü (Changelog) Oluşturma Komutları**

## **Değişiklik Günlüğü Oluşturma Nedir?**

Değişiklik günlüğü, yazılım projelerinde yapılan değişikliklerin tarihsel bir kaydını tutar. Bu güncellemeler genellikle yazılım sürüm notlarında yer alır ve proje ekibi, kullanıcılar ve katkıda bulunan diğer kişilere yapılan değişiklikleri bildirir. Git ve GitHub gibi versiyon kontrol sistemleri, bu değişikliklerin düzenli ve tutarlı bir şekilde izlenmesine yardımcı olur.

**Değişiklik Günlüğü** genellikle şunları içerir:

- Yeni özellikler.
- Hata düzeltmeleri.
- İyileştirmeler.
- Geriye dönük uyumluluk ve kırılma değişiklikleri.
  
---

## **1. Değişiklik Günlüğü Yazma Yöntemleri**

### **Manuel Günlük Yazma:**

Geliştiriciler, proje değişikliklerini manuel olarak günlüğe kaydedebilirler. Bu yaklaşımda, geliştiricilerin commit mesajlarını anlamlı bir şekilde yazmaları önemlidir. Her yeni sürüm için bir günlük girişi eklenir.

**Şablon Örneği (Manuel):**

```markdown
## [1.1.0] - 2024-12-01
### Added
- Kullanıcı profil güncellemeleri eklendi.
- Admin paneline yeni raporlama modülü eklendi.

### Fixed
- "Şifremi Unuttum" özelliği çalışmıyordu, düzeltildi.

### Changed
- Ana sayfa tasarımı yenilendi.
```

---

### **Otomatik Günlük Yazma:**

Otomatik değişiklik günlükleri yazmanın iki temel yolu vardır:

1. **Conventional Commits:** Geliştiricilerin belirli bir formatta commit mesajları yazmasını zorunlu kılar. Bu format, otomatik changelog üretmek için kullanılabilir.
2. **GitHub Changelog Generator:** GitHub üzerinden yapılan commit'leri kullanarak bir değişiklik günlüğü oluşturur.

**Araçlar:**

- **Conventional Changelog:** Bu araç, commit mesajlarındaki etiketleri analiz ederek değişiklik günlüğü oluşturur. Etiketler genellikle `feat`, `fix`, `docs` gibi terimler olur.
- **Standard Version:** Commit mesajlarını analiz eder ve yeni sürüm numarasıyla birlikte changelog dosyasını otomatik olarak günceller.

---

## **2. Değişiklik Günlüğü İçin En İyi Uygulamalar**

### **Commit Mesajı Formatı (Conventional Commits):**

Conventional Commits, commit mesajlarının belirli bir formata uygun olmasını sağlar ve otomatik changelog oluşturmayı kolaylaştırır.

**Örnek Commit Mesajları:**

- `feat: Kullanıcı profili ekleme ekranı eklendi.`
- `fix: Admin panelinde giriş hatası düzeltildi.`
- `docs: Kullanıcı kılavuzuna yeni özellik ekledi.`
  
**Yararları:**

- Değişikliklerin düzenli ve tutarlı bir şekilde kaydedilmesi.
- Otomatik changelog oluşturma kolaylığı.
- Sürüm numaralarını doğru belirleme.

### **Changelog Şablonları:**

Yazılımcılar değişiklik günlüğü oluştururken standart şablonlar kullanabilirler. En yaygın şablonlar:

- **Keep a Changelog**: Bu metodoloji, tüm changelogların belirli bir formatta yazılmasını sağlar.
- **Semantic Versioning**: Bu yaklaşım, sürüm numaralandırmasının mantıklı ve anlamlı olmasını sağlar.

**Şablon Örneği (Keep a Changelog):**

```markdown
# [Unreleased]

## Added
- Yeni ödeme yöntemleri eklendi.

## Fixed
- Şifremi unuttum hatası düzeltildi.

## Changed
- Profil sayfası tasarımı yeniden düzenlendi.
```

---

## **3. Git Komutları ve Araçlarla Changelog Oluşturma**

### **GitHub Changelog Generator:**

Bu araç, GitHub reposundaki commit geçmişine bakarak otomatik olarak changelog oluşturur. GitHub Changelog Generator kullanarak günlük oluşturmak için aşağıdaki komutları takip edebilirsiniz:

**Kurulum:**

```bash
npm install -g github-changelog-generator
```

**Günlük Oluşturma:**

```bash
github-changelog-generator --user <github_user> --repo <repo_name>
```

Bu komut, projedeki tüm commit'leri inceleyerek bir değişiklik günlüğü oluşturur.

---

### **Conventional Changelog Kullanımı:**

Conventional Changelog kullanarak commit mesajlarını analiz edebilir ve otomatik olarak bir changelog oluşturabilirsiniz.

**Kurulum:**

```bash
npm install -g conventional-changelog-cli
```

**Günlük Oluşturma:**

```bash
conventional-changelog -p angular -i CHANGELOG.md -s
```

Bu komut, tüm commit mesajlarını analiz eder ve güncellenmiş bir `CHANGELOG.md` dosyası oluşturur.

---

### **4. Hands-On: Değişiklik Günlüğü Oluşturma**

**Senaryo:**
Projenizde birkaç yeni özellik eklendi, bazı hatalar düzeltildi ve birkaç iyileştirme yapıldı. Şimdi, bu değişiklikleri bir changelog dosyasına kaydetmeniz gerekiyor.

**Adımlar:**

1. Projede birkaç commit yapın:
   - Yeni özellikler (örn. `feat: Kullanıcı girişi yapıldı`)
   - Hatalar düzeltildi (örn. `fix: Admin giriş hatası düzeltildi`)
   - İyileştirmeler (örn. `chore: Kod optimizasyonu yapıldı`)

2. `CHANGELOG.md` dosyasını oluşturun ve manuel olarak yukarıdaki şablonu kullanarak bu değişiklikleri ekleyin.

**Örnek Günlük:**

```markdown
## [1.1.0] - 2024-12-01
### Added
- Kullanıcı girişi eklendi.
- Admin paneli raporlama sekmesi eklendi.

### Fixed
- Admin paneline giriş hatası düzeltildi.

### Changed
- Kullanıcı profil sayfası güncellendi.
```

3. GitHub Changelog Generator veya Conventional Changelog aracını kullanarak değişikliklerinizi otomatik olarak günlüğe ekleyin.

---

## **5. Senaryo: Otomatik Changelog Üretimi**

**Durum:**  
Bir projede sürekli yeni özellikler ekleniyor ve hatalar düzeltiliyor. Her sürümde bir değişiklik günlüğü tutmak istiyorsunuz.

**Adımlar:**

1. Git commit'leri oluşturun:
   - `feat: Yeni ödeme sistemi entegre edildi.`
   - `fix: Kayıt hatası düzeltildi.`
2. Otomatik changelog üretimi için `conventional-changelog` aracını kullanın:

   ```bash
   conventional-changelog -p angular -i CHANGELOG.md -s
   ```

**Hands-On:**  

1. Yeni commit'ler yapın.
2. `CHANGELOG.md` dosyasını otomatik olarak güncellemek için `conventional-changelog` komutunu kullanın.

---

## **Sonuç:**

Bu modülde, yazılım projelerinizde değişiklik günlüğü oluşturmanın temellerini öğrendiniz. Manuel ve otomatik yaklaşımlar arasındaki farkları ve en iyi uygulamaları kullanarak, projelerinizi daha organize ve profesyonel hale getirebilirsiniz. Otomatik araçlar kullanarak, commit mesajlarınızı düzenli tutabilir ve değişikliklerinizi etkili bir şekilde güncelleyebilirsiniz.
