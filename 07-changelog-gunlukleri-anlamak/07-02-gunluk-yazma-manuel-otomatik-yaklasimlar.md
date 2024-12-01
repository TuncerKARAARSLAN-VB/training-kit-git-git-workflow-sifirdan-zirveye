# **Değişiklik Günlüğü Yazma Yöntemleri: Manuel ve Otomatik Yaklaşımlar**

Değişiklik günlükleri (Changelog), yazılım geliştirme süreçlerinde önemli bir rol oynar ve yazılım projelerinin sürümlerinin belgelenmesini sağlar. Ancak, değişiklik günlüğü oluşturmanın birkaç farklı yolu vardır: **manuel yazma** ve **otomatik yaklaşımlar**. Her iki yöntemin de avantajları ve kullanım senaryoları vardır.

---

## **1. Manuel Yaklaşım:**

Manuel yaklaşımda, geliştirici veya yazılım ekibi, yapılan değişiklikleri elle yazarak değişiklik günlüğünü günceller. Bu yaklaşım, genellikle küçük ekipler ve basit projelerde kullanılır.

### **Adımlar:**

1. **Commit'leri İnceleme:**
   - Her yeni sürüm için yapılan değişiklikleri gözden geçirin. Git komutları ile commit geçmişini inceleyin.

     ```bash
     git log --oneline
     ```

2. **Kategorilere Ayırma:**
   - Değişiklikleri ana kategorilere ayırın:
     - **Added:** Yeni özellikler
     - **Fixed:** Hataların düzeltilmesi
     - **Changed:** Yapılan değişiklikler
     - **Deprecated:** Kullanımdan kaldırılan özellikler
     - **Removed:** Kaldırılan özellikler
     - **Security:** Güvenlik güncellemeleri

3. **Açıklama Yazma:**
   - Yapılan her değişiklik için kısa ve öz açıklamalar yazın. Değişikliğin amacını ve etkisini belirtin.

4. **Sürüm Numarası ve Tarih:**
   - Her yeni sürüm için sürüm numarası belirleyin ve tarihi yazın.
   - Örnek format:

     ```text
     ## [1.2.0] - 2024-12-01
     ### Added
     - Yeni kullanıcı paneli eklendi.
     
     ### Fixed
     - Kullanıcı şifre sıfırlama hatası düzeltildi.
     ```

### **Avantajlar:**

- **Tam Kontrol:** Her değişiklik el ile yazıldığı için tam kontrol sağlanır.
- **Esneklik:** Değişikliklerin açıklamaları dilediğiniz gibi özelleştirilebilir.
  
### **Dezavantajlar:**

- **Zaman Alıcı:** Özellikle büyük projelerde, her değişikliği elle yazmak zaman alabilir.
- **Hata Riski:** Özellikle büyük ekiplerde, her değişiklik kaydını tutmak zor olabilir.

---

## **2. Otomatik Yaklaşım:**

Otomatik yaklaşımda, yazılım geliştirme sürecindeki commit’leri, sürüm etiketlerini ve diğer meta verileri otomatik olarak kullanarak değişiklik günlüğü oluşturulabilir. Bu yaklaşım, özellikle büyük projelerde ve sürekli entegrasyon (CI) süreçlerinde yaygın olarak kullanılır.

### **Adımlar:**

1. **Git ve CI/CD Entegrasyonu:**
   - CI/CD araçları (Jenkins, GitLab CI, CircleCI) kullanılarak her yeni commit ve sürüm etiketlendiğinde, otomatik olarak bir changelog oluşturulabilir.

2. **Otomatik Araçlar Kullanma:**
   - **standard-version**, **semantic-release**, **git-chglog** gibi araçlar kullanarak, commit mesajları belirli bir kurala göre yazıldığında otomatik olarak changelog oluşturulabilir. Örneğin, `fix:` etiketli commitler "Fixed" kategorisinde yer alır.

3. **Commit Mesajı Düzenleme:**
   - Commit mesajlarını belirli bir formatta yazmak, otomatik changelog üretimi için gereklidir. Örneğin:

     ```text
     feat: Yeni kullanıcı girişi özelliği eklendi
     fix: Şifre sıfırlama hatası düzeltildi
     ```

   - Bu tür bir format, araçların doğru kategorileri ve açıklamaları oluşturmasına yardımcı olur.

4. **Sürüm Etiketleme ve Yayınlama:**
   - Git sürüm etiketlerini kullanarak her yeni sürümde changelog'u güncelleyin. CI/CD araçları sürüm etiketlerini takip ederek yeni changelog'ları otomatik olarak oluşturabilir.

### **Avantajlar:**

- **Zaman Tasarrufu:** Otomatik araçlar, değişiklik günlüklerini hızlı bir şekilde oluşturur.
- **Tutarlılık:** Commit mesajları belirli kurallara göre yazıldığı için changelog dosyası daha tutarlı olur.
- **Hata Azaltma:** Otomatik süreçler, insan hatası riskini azaltır.

### **Dezavantajlar:**

- **Yapılandırma Gereksinimi:** Otomatik araçlar başta doğru yapılandırılmadığı takdirde karmaşık olabilir.
- **Bağımlılık:** Birçok otomatik araç, belirli bir commit mesajı formatı gerektirir, bu da takımların alışkanlıklarını değiştirmesini gerektirir.

---

## **Senaryo: Manuel ve Otomatik Changelog Oluşturma**

### **Senaryo 1: Manuel Changelog**

**Durum:**
Bir yazılım geliştirici, yeni özellikler ekledi ve bazı hataları düzeltti. Değişikliklerin kaydını manuel olarak oluşturması gerekiyor.

**Çözüm:**

1. Geliştirici `git log` komutuyla commit geçmişini kontrol eder.
2. Değişiklikleri kategorilere ayırır (yeni özellikler, hatalar, güvenlik düzeltmeleri).
3. `CHANGELOG.md` dosyasına sürüm numarası ve tarihini ekler, ardından açıklamalar yazar.

**Adımlar:**

```bash
git log --oneline
```

Sonra, bu commit’lerden yapılan değişiklikleri uygun başlıklarla açıklayın.

```md
## [1.2.0] - 2024-12-01
### Added
- Yeni kullanıcı arayüzü özellikleri eklendi.
### Fixed
- Şifre sıfırlama hatası düzeltildi.
```

#### **Senaryo 2: Otomatik Changelog**

**Durum:**
Bir yazılım geliştirme ekibi, her yeni sürümde changelog otomatik olarak oluşturulmasını istiyor. Bu, sürekli entegrasyon süreciyle entegre edilmiş bir projede yapılacaktır.

**Çözüm:**

1. Geliştirici, commit mesajlarını belirli kurallara göre yazmalı (`feat:`, `fix:`, `docs:`, vb.).
2. CI/CD süreci her commit'i izler ve otomatik olarak changelog dosyasını oluşturur.
3. Yeni sürüm çıktığında, `semantic-release` veya benzeri bir araç kullanarak changelog güncellenir.

**Adımlar:**

- GitHub Actions veya Jenkins gibi bir CI aracı yapılandırın.
- `standard-version` veya `semantic-release` kullanarak commit mesajları üzerinden otomatik changelog oluşturulmasını sağlayın.

```bash
npx standard-version
```

---

### **Hands-On (Uygulamalı Çalışma):**

1. **Manuel Changelog Yazma:**
   - GitHub üzerinde bir projede çalışın. Yeni bir özellik ekleyin veya bir hata düzeltmesi yapın.
   - Yapılan değişiklikleri gözden geçirin ve `CHANGELOG.md` dosyasına yazın.

2. **Otomatik Changelog Yapılandırma:**
   - Projenizi **semantic-release** veya **standard-version** gibi araçlarla entegre edin.
   - Commit mesajlarını belirli bir formata uygun olarak yazın (örn. `feat:`, `fix:`).
   - CI/CD aracı ile otomatik changelog güncellenmesini sağlayın.

---

### **Sonuç:**

Manuel ve otomatik yaklaşımlar arasında seçim yapmak, projenizin büyüklüğüne, ekibinizin gereksinimlerine ve mevcut araçların entegrasyon seviyesine bağlıdır. Küçük projelerde manuel yaklaşım yeterli olabilirken, büyük projelerde otomatik araçlar daha verimli ve sürdürülebilir bir çözüm sağlar. Her iki yöntemi de anlamak ve gerektiğinde kullanmak, yazılım geliştirme süreçlerinizi iyileştirebilir.
