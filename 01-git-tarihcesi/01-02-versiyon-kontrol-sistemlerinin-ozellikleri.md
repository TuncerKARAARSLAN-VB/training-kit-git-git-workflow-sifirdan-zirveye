# **Versiyon Kontrol Sistemlerinin Temel Özellikleri**

Versiyon kontrol sistemleri (VCS), yazılım geliştirme sürecinde önemli bir yer tutar ve projelerdeki dosyaların değişikliklerini takip etmek, geri almak, birleştirmek ve paylaşmak için kullanılır. Bu sistemler, ekiplerin birlikte çalışmasını kolaylaştırır, kodun geçmişi üzerinde izleme yapmayı mümkün kılar ve hata yönetimini basitleştirir. Git gibi dağıtık versiyon kontrol sistemleri, bu özellikleri daha da geliştirmiştir.

---

## **1. Değişikliklerin Kaydedilmesi (Commit)**

**Temel Özellik:**  
Bir versiyon kontrol sistemi, projedeki her değişikliği "commit" adı verilen bir işlemle kaydeder. Commit, bir dosyada yapılan değişikliklerin versiyon kontrolüne eklenmesidir. Her commit, değişikliklerin kim tarafından, ne zaman yapıldığını, hangi dosyaların değiştiğini ve yapılan değişikliklerin neler olduğunu belirtir.

**Özellikler:**  

- **Commit Mesajları:** Commit mesajları, yapılan değişiklikleri açıklayan metinlerdir ve iyi bir commit mesajı, yapılan değişikliklerin amacını anlamak için önemlidir.
- **Hash:** Her commit, benzersiz bir kimlik (hash değeri) ile tanımlanır, bu da güvenliği ve takibi kolaylaştırır.

**Senaryo:**  
Bir yazılım geliştiricisi, `index.html` dosyasındaki bir metni değiştiriyor ve bu değişikliği kaydetmek istiyor. Komutlar şu şekilde olacaktır:

```bash
git add index.html
git commit -m "index.html dosyasındaki başlık metni değiştirildi"
```

**Hands-On:**  
Eğitmenle birlikte bir proje oluşturun, dosyada küçük değişiklikler yapın ve bu değişiklikleri commit edin. `git log` komutunu kullanarak commit geçmişini inceleyin.

---

## **2. Branching (Dal Oluşturma) ve Merging (Birleştirme)**

**Temel Özellik:**  
Versiyon kontrol sistemleri, projelerde farklı özelliklerin paralel olarak geliştirilebilmesi için **branching** (dal oluşturma) özelliği sunar. Bir geliştirici, ana dalda (main branch) çalışmak yerine, yeni bir dal oluşturabilir ve değişiklikleri bu dalda yapabilir. Daha sonra, bu dalda yapılan değişiklikler **merging** (birleştirme) komutu ile ana dal ile birleştirilebilir.

**Özellikler:**

- **Branching:** Farklı özellikler veya düzeltmeler için bağımsız olarak çalışma imkanı sağlar.
- **Merging:** Farklı dallarda yapılan değişikliklerin ana dal ile birleştirilmesini sağlar. Merging sırasında çatışmalar (conflicts) olabilir ve bunlar manuel olarak çözülmelidir.

**Senaryo:**  
Bir ekip, `login` sayfasının tasarımını değiştirmek için bir dal oluşturur ve bu değişiklikleri tamamladıktan sonra ana dal ile birleştirir. Bu süreç şu şekilde işler:

```bash
git checkout -b login-page
# Tasarımlar üzerinde çalışılır...
git add .
git commit -m "login sayfası tasarımı tamamlandı"
git checkout main
git merge login-page
```

**Hands-On:**  
Eğitmenle birlikte bir proje başlatın, `login` dalı oluşturun, üzerinde değişiklik yapın ve bu dalı ana dal ile birleştirin. Çatışma oluşursa, çözüm adımlarını uygulayın.

---

## **3. Çatışma Çözümü (Conflict Resolution)**

**Temel Özellik:**  
Birden fazla geliştirici, aynı dosya üzerinde değişiklik yaparsa **çatışmalar** (conflicts) meydana gelir. Versiyon kontrol sistemleri, çatışmaları tespit eder ve geliştiricilere bu çatışmaları çözme imkanı verir. Çatışmalar, genellikle **merging** (birleştirme) sırasında ortaya çıkar.

**Özellikler:**

- **Çatışma Tespiti:** Versiyon kontrol sistemleri, birleştirme sırasında çatışmalar olup olmadığını kontrol eder.
- **Manuel Çözüm:** Çatışmalar, geliştiriciler tarafından dosya düzenleyici araçlarıyla manuel olarak çözülmelidir.

**Senaryo:**  
İki geliştirici aynı dosyada değişiklik yapar. İlk geliştirici, `header.html` dosyasındaki başlık metnini değiştirirken, ikinci geliştirici aynı dosyanın başlık kısmını başka bir şekilde değiştirir. Bu durumda, birleştirme sırasında çatışma meydana gelir.

Çatışma çözme adımları:

1. `git merge` komutunu çalıştırın.
2. Git, çatışma olan dosyayı işaret eder.
3. Çatışma olan dosyayı açarak, her iki değişikliği inceleyin ve çözün.
4. Çatışma çözülünce dosyayı kaydedin ve commit edin.

```bash
git add header.html
git commit -m "Çatışma çözüldü"
```

**Hands-On:**  
Çatışma oluşturan iki dalda değişiklik yapın ve çatışma çözme sürecini uygulayın. Sonrasında çözümün başarılı olup olmadığını kontrol edin.

---

## **4. Değişikliklerin İzlenmesi (Tracking Changes)**

**Temel Özellik:**  
Versiyon kontrol sistemleri, projedeki her dosyanın ne zaman ve nasıl değiştiğini izler. Bu, bir dosyanın önceki sürümlerine dönmeyi, hangi değişikliklerin yapıldığını görmek için kullanılır. Git, `git diff` komutuyla yapılan değişiklikleri karşılaştırma imkanı sağlar.

**Özellikler:**

- **Diff:** İki versiyon arasındaki farkları görmek için kullanılır.
- **Blame:** Bir dosyadaki her satırın kim tarafından, ne zaman değiştirildiğini gösterir.

**Senaryo:**  
Bir geliştirici, `style.css` dosyasını değiştirmiştir. Başka bir geliştirici bu değişiklikleri görmek istiyor. `git diff` komutunu kullanarak farkları görüntüler:

```bash
git diff style.css
```

**Hands-On:**  
Eğitmenle birlikte `git diff` komutunu kullanarak, değişikliklerin nasıl izlendiğini ve hangi satırlarda değişiklik yapıldığını gözlemleyin.

---

## **5. Geri Dönme ve Revizyonlar**

**Temel Özellik:**  
Git, yapılan yanlış değişiklikleri geri almayı kolaylaştırır. `git revert`, bir commit'i geri alırken, `git reset` daha eski bir commit'e dönmeyi sağlar. Bu özellikler, hata yapılması durumunda yazılımın stabilitesini korur.

**Özellikler:**

- **Revert:** Geri alma işlemi, mevcut commit'ten önceki bir commit’i geri alır.
- **Reset:** Commit geçmişinde ileri veya geri gitmek için kullanılır.

**Senaryo:**  
Geliştirici, yanlış bir commit yaptı ve bu commit’i geri almak istiyor. `git revert` komutunu kullanarak işlemi geri alır:

```bash
git revert <commit_hash>
```

**Hands-On:**  
Eğitmenle birlikte bir hata yapın ve `git revert` komutunu kullanarak hatalı commit’i geri alın. Ayrıca, `git reset` komutunu deneyerek geçmişe dönmeyi deneyin.

---

## **6. Dağıtık Çalışma (Distributed Work)**

**Temel Özellik:**  
Git, dağıtık versiyon kontrol sistemi olduğu için, her geliştirici projenin tam bir kopyasına sahiptir. Bu, geliştiricilerin internet bağlantısı olmadan da yerel olarak çalışabilmelerini sağlar ve merkezi bir sunucuya bağımlılığı ortadan kaldırır.

**Özellikler:**

- **Yerel Depo:** Her geliştirici, tam bir proje kopyasına sahip olur.
- **Push ve Pull:** Geliştiriciler, değişiklikleri ana depoya gönderebilir (push) veya ana depodan alabilir (pull).

**Senaryo:**  
Bir geliştirici yerel bilgisayarında çalıştıktan sonra değişikliklerini ana depoya gönderir. Bu, başkalarının bu değişiklikleri görmesini sağlar:

```bash
git push origin main
```

**Hands-On:**  
Bir projede yerel değişiklikler yapın ve `git push` komutunu kullanarak ana depoya gönderin. Başka bir geliştirici `git pull` komutuyla değişikliklerinizi alabilir.

---

## **Sonuç ve Değerlendirme**

Versiyon kontrol sistemleri, yazılım geliştirme sürecinin her aşamasında güvenliği artıran, iş birliğini kolaylaştıran ve hataları minimize eden araçlardır. Git gibi modern versiyon kontrol sistemleri, bu temel özellikleri sağlarken, ek olarak daha verimli ve hızlı çalışma imkanı sunar. Bu özellikler, yazılım projelerinin başarısını garantileyen önemli unsurlar olarak kabul edilir.
