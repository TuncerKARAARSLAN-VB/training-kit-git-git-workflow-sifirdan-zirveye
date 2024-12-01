# **Commit’lerin Sıralı Olarak Test Edilmesi**

**Konunun Anlatımı:**

Git, bir projedeki her değişikliği (commit) izler ve bu değişikliklerin geçmişini tutar. Commit’lerin sıralı olarak test edilmesi, yazılım geliştirme sürecinde önemli bir uygulamadır, çünkü bazı durumlarda birden fazla commit’in birleşimi, yeni bir hatayı veya beklenmedik bir davranışı tetikleyebilir.

Commit’lerin sıralı olarak test edilmesi, yazılımdaki değişikliklerin her birinin doğru şekilde çalıştığından emin olmanın yanı sıra, bu değişikliklerin birbirleriyle nasıl etkileştiğini anlamaya da yardımcı olur.

**Test Edilen Commit'ler:**

- Her commit, bağımsız olarak test edilmelidir.
- Test süreci, her commit'in yazılımın önceki sürümleriyle uyumlu olduğunu doğrular.

---

## **Commit’lerin Sıralı Olarak Test Edilmesinin Adımları:**

1. **Test Edilecek Commit’leri Belirleme:**
   - Proje üzerindeki commit’lerin listesini almak için `git log` komutunu kullanabilirsiniz.
   - Belirli commit'ler arasında test yapabilmek için commit hash’lerini bilmeniz gerekir.

   ```bash
   git log
   ```

2. **Commit'leri Sırasıyla Uygulama:**
   - Bir commit’in diğerine nasıl etki ettiğini görmek için belirli bir commit’i kontrol edebilir ve bu commit'i test edebilirsiniz.
   - Commit’lerin sırasıyla uygulanması için `git checkout` komutunu kullanabilirsiniz.

   ```bash
   git checkout <commit_hash>
   ```

3. **Test Senaryoları Çalıştırma:**
   - Her commit’teki değişikliklerin doğru çalışıp çalışmadığını doğrulamak için otomatik test senaryoları çalıştırılır. Örneğin, bir test çerçevesi kullanarak testlerinizi çalıştırabilirsiniz:

   ```bash
   npm test  # JavaScript için örnek
   ```

4. **Sonraki Commit’e Geçme:**
   - Her commit’i test ettikten sonra, bir sonraki commit’e geçebilirsiniz.

   ```bash
   git checkout <next_commit_hash>
   ```

5. **Sonuçları Değerlendirme:**
   - Testlerin her biri başarılıysa, yazılımın her commit’inin doğru çalıştığını ve uyumlu olduğunu onaylarsınız.
   - Hatalı bir commit bulunursa, hatayı tespit etmek için ilgili commit’te yapılan değişiklikleri incelemeniz gerekir.

---

## **Senaryo Örneği: Commit’lerin Sıralı Olarak Test Edilmesi**

**Durum:**  
Bir proje üzerinde çalışıyorsunuz ve bir dizi commit yapılmış. Ancak, bir takım testlerde başarısızlıklar görülüyor ve bu başarısızlıkların hangi commit'ten kaynaklandığını bulmak istiyorsunuz.

**Çözüm:**  

1. Projenin son commit'ini test edin. Eğer testler başarılıysa, diğer commit’lere geçin.
2. Bir commit başarısız olduğunda, o commit'i kontrol ederek hatayı tespit edin ve düzeltin.

```bash
git log  # Commit geçmişini görmek için
git checkout <commit_hash>  # Belirli bir commit’e geçiş
npm test  # Testleri çalıştırma
```

Eğer testler başarısız olursa:

- Hatalı commit'i bulduktan sonra, bu commit'e yönelik düzeltmeleri uygulayarak bir sonraki commit'i test edin.

---

## **Hands-On (Uygulamalı Çalışma):**

1. **Proje Başlatma:**
   - Git depolarından herhangi birini seçin veya bir test projesi başlatın.
   - Projeye birkaç commit ekleyin.

2. **Test Ortamı Kurma:**
   - Test etmek için bir test çerçevesi kurun (örneğin, Jest, Mocha, vb.).
   - Testlerinizi kurduktan sonra, otomatik testler çalıştırmak için `npm test` veya uygun komutu kullanın.

3. **Commit’ler Üzerinde Çalışma:**
   - `git log` komutuyla commit geçmişini gözden geçirin.
   - `git checkout <commit_hash>` ile her commit’e geçiş yapın ve testleri çalıştırarak commit’lerin doğru şekilde çalışıp çalışmadığını doğrulayın.

4. **Hatalı Commit’in Tespiti:**
   - Testlerde başarısız olan commit’i bulun.
   - Hatalı commit’in içeriğini inceleyin ve çözüm önerileri geliştirin.

5. **Sonuçları Değerlendirme:**
   - Tüm commit’lerin sırasıyla test edilmesini sağlayın.
   - Sonuçları raporlayın ve hangi commit’in soruna yol açtığını belirleyin.

---

## **Sonuç:**

Commit’lerin sıralı olarak test edilmesi, yazılım geliştirme sürecinde sürekli entegrasyon (CI) ve sürekli teslimat (CD) ile uyumlu bir yaklaşım oluşturur. Bu süreç, hataların erken tespit edilmesine ve yazılımın her bir değişikliğinin doğru bir şekilde uygulanıp uygulanmadığının anlaşılmasına olanak sağlar.
