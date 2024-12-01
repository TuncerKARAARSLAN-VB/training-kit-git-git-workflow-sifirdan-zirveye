# **Modül 7: Değişiklik Günlüklerini (Changelog) Anlamak**

**Değişiklik Günlükleri Nedir?**

Değişiklik günlüğü (Changelog), bir yazılım projesinde yapılan değişikliklerin, iyileştirmelerin, hataların düzeltilmesinin ve yeni özelliklerin zaman içinde nasıl geliştiğini belgelendiren bir dosyadır. Her yazılım sürümünde yapılan önemli değişikliklerin ve güncellemelerin kaydını tutar, böylece yazılım geliştirme süreci boyunca ne zaman hangi değişikliklerin yapıldığını ve bu değişikliklerin ne işe yaradığını takip edebilirsiniz.

---

## **Değişiklik Günlüklerinin Rolleri ve Önemi:**

1. **Proje Geçmişini İzleme:**
   - Changelog, projedeki tüm önemli değişikliklerin kaydını tutarak yazılımın geçmişini takip etmenizi sağlar. Hangi sürümde ne değiştiğini bilmek, proje yönetimini kolaylaştırır.

2. **Ekip İçi İletişim:**
   - Ekip üyeleri, yeni sürümlere eklenen özellikleri veya düzeltilen hataları görmek için changelog'u inceleyebilir. Bu, ekip içinde iletişimi ve işbirliğini artırır.

3. **Kullanıcılar İçin Güncellemeler:**
   - Changelog, yazılım kullanıcılarına hangi özelliklerin eklendiği veya hangi hataların düzeltildiği hakkında bilgi verir. Bu, kullanıcıların yazılımı nasıl kullanacaklarını bilmeleri açısından önemlidir.

4. **Sürüm Yönetimi:**
   - Her sürümde yapılan değişikliklerin belgelenmesi, sürüm numaralandırmasını ve sürüm yönetimini daha şeffaf hale getirir. Bu sayede, sürüme özel hatalar veya eksiklikler kolayca izlenebilir.

5. **Yazılımın Kalitesini Artırma:**
   - Changelog, yazılımın hangi alanlarda geliştiğini ve hangi alanlarda iyileştirmeler yapıldığını gösterir. Bu, kaliteyi izlemek için önemli bir kaynaktır.

---

## **Değişiklik Günlüğü Yazma Yöntemleri:**

Değişiklik günlüğü yazarken, açık ve tutarlı bir format kullanmak çok önemlidir. Aşağıda, popüler formatlardan biri olan **"Keep a Changelog"** önerilerini bulabilirsiniz:

1. **Başlıklar:**
   - Her sürüm için bir başlık kullanın. Örneğin:

     ```text
     ## [1.2.0] - 2024-12-01
     ```

2. **Kategori Başlıkları:**
   - Değişiklikleri kategorilere ayırarak yazın. Örneğin:
     - **Added** (Yeni özellikler)
     - **Changed** (Değiştirilen özellikler)
     - **Fixed** (Düzeltmeler)
     - **Deprecated** (Kullanımdan kaldırılan özellikler)
     - **Removed** (Kaldırılan özellikler)
     - **Security** (Güvenlik düzeltmeleri)

3. **Açıklamalar:**
   - Her bir değişikliği kısa ve öz bir şekilde açıklayın.
   - Değişikliğin ne işe yaradığını, nasıl çalıştığını ve hangi sorunu çözdüğünü belirtin.

Örnek Changelog:

```text
## [1.2.0] - 2024-12-01
### Added
- Yeni bir kullanıcı yönetim paneli eklendi.
- API'ye yeni arama özelliği entegre edildi.

### Fixed
- Hatalı e-posta onayı düzeltildi.
- Kullanıcı girişi sırasında yaşanan zaman aşımı hatası giderildi.

### Security
- Veritabanı şifreleme yöntemi güncellendi.
```

---

### **Senaryo: Değişiklik Günlüğü Yazmak**

**Durum:**
Bir yazılım geliştirme ekibi olarak, yeni bir sürüm yayınlayacaksınız ve bu sürümdeki değişiklikleri içeren bir changelog yazmanız gerekiyor. Hangi değişikliklerin hangi sürümde yapıldığını belirlemeniz ve kullanıcılarla paylaşmanız gerekecek.

**Çözüm:**

1. Son yapılan commit'leri gözden geçirin ve hangi değişikliklerin hangi sürümde yapılacağını belirleyin.
2. Değişiklikleri uygun kategorilere ayırın (yeni özellikler, hata düzeltmeleri, güvenlik güncellemeleri vb.).
3. Changelog dosyasına bu değişiklikleri yazın ve sürüm numarasını ekleyin.

```bash
git log --oneline
```

Çıkan commit'leri analiz ederek hangi değişikliklerin yapıldığını not alın.

---

### **Hands-On (Uygulamalı Çalışma):**

1. **Proje Başlatma:**
   - GitHub üzerinde bir proje oluşturun veya mevcut bir projeyi kullanın.
   - Bu projeye birkaç yeni özellik ekleyin veya hata düzeltmeleri yapın.

2. **Changelog Dosyası Oluşturma:**
   - Proje kök dizininde `CHANGELOG.md` adında bir dosya oluşturun.
   - Bu dosyada, yazılımda yapılan değişiklikleri kategorilere ayırarak yazın.

3. **Commit’leri İnceleme:**
   - `git log` komutunu kullanarak yapılan commit'leri inceleyin.
   - Commit’lerdeki değişiklikleri not alarak changelog’u güncelleyin.

4. **Changelog Formatı Uygulama:**
   - Her commit için uygun kategorilerde (Added, Changed, Fixed, vb.) açıklamalar yazın.
   - Son olarak, yazdığınız changelog'u commit edin:

   ```bash
   git add CHANGELOG.md
   git commit -m "Changelog güncellendi"
   ```

5. **Sürüm Yayınlama:**
   - Son sürümde yapılan değişiklikleri içeren changelog’u kullanıcılarla paylaşın.
   - GitHub üzerinde sürüm notları oluşturun.

---

## **Sonuç:**

Değişiklik günlükleri, yazılım geliştirme sürecini daha şeffaf hale getirir, ekip içi iletişimi güçlendirir ve kullanıcılar için faydalı bir kaynak sağlar. Değişiklikleri kategorilere ayırarak ve açıklamalarla destekleyerek yazılımın gelişimini daha anlaşılır hale getirebilirsiniz.
