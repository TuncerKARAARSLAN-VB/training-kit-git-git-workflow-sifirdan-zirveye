# **GitHub'ın Yazılım Geliştirmedeki Rolü**

GitHub, dünyadaki en popüler yazılım geliştirme platformlarından biridir ve yazılım projelerini yönetmek, iş birliği yapmak ve dağıtım süreçlerini düzenlemek için geniş bir araç seti sunar. GitHub, Git’i temel alan bir platformdur ve Git'in sunduğu sürüm kontrolü özelliklerini bulutta sunarak, ekiplerin daha verimli çalışmasını sağlar. GitHub, özellikle açık kaynak projelerde büyük bir rol oynar, ancak kurumsal yazılım geliştirme süreçlerinde de oldukça etkilidir.

---

## **1. GitHub ve Git: Temel Farklar**

**GitHub**, Git’in sağladığı sürüm kontrol özelliklerinin bulut tabanlı bir platformda erişilebilir olmasını sağlar. Git, yerel olarak çalışan bir sürüm kontrol sistemiyken, GitHub, projelerinizi internet üzerinde merkezi bir depoda tutarak daha geniş bir iş birliği alanı sunar.

**Özellikler:**

- **Git**: Versiyon kontrolü sağlayan, dağıtık bir sistemdir. Her geliştirici kendi bilgisayarında çalışır.
- **GitHub**: Git’in sunduğu tüm özellikleri sunar, ancak aynı zamanda iş birliği, depolama, dağıtım ve takım yönetimi araçları da sağlar.

**Senaryo Örneği:**
Bir yazılım geliştirme ekibi, bir projede çalışmak için GitHub’ı kullanır. Her geliştirici kendi bilgisayarında çalışırken, değişikliklerini GitHub’daki merkezi depoya göndermek (push) ve oradan almak (pull) için Git kullanır.

```bash
git push origin main
git pull origin main
```

**Hands-On:**
Eğitmenle birlikte bir proje başlatın, değişiklik yapın, GitHub’a push edin ve başkalarının bu değişiklikleri alıp çalışabilmesini sağlayın.

---

## **2. GitHub ile İş Birliği**

GitHub, yazılım projelerinde ekip içi iş birliğini kolaylaştırır. Ekipler, projede yaptıkları değişiklikleri takip edebilir, birbirlerinin değişikliklerini inceleyebilir ve kodu tek bir merkezi depoda toplayabilirler. 

**Özellikler:**

- **Forking:** Başka bir kullanıcının projesini kendi hesabınıza alarak üzerinde çalışabilirsiniz. Bu işlem, açık kaynak projelere katkıda bulunmak için sıklıkla kullanılır.
- **Pull Requests (PR):** Bir geliştirici, yaptığı değişiklikleri ana projeye göndermek için PR açar. Bu, değişikliklerin incelenmesini sağlar.
- **Code Review:** Pull request’ler üzerinden yapılan değişiklikler gözden geçirilir, hatalar giderilir ve onay verildikten sonra ana projeye dahil edilir.

**Senaryo Örneği:**
Bir yazılım geliştirici, başka birinin projesini fork eder ve üzerinde geliştirmeler yapar. Yapılan değişiklikleri ana projeye dahil etmek için bir PR açar. Diğer geliştiriciler bu PR'yi gözden geçirir ve geri bildirimde bulunur.

**Steps:**

1. Fork edilen bir repo alınır.
2. Yerel ortamda değişiklikler yapılır.
3. GitHub'a push edilir ve PR açılır.

**Hands-On:**
Eğitmenle birlikte bir proje fork edin, değişiklik yapın ve ardından PR açarak kodunuzu gözden geçirilmesi için gönderebilirsiniz.

---

## **3. Sürekli Entegrasyon ve Dağıtım (CI/CD)**

GitHub, sürekli entegrasyon (CI) ve sürekli dağıtım (CD) süreçlerini yönetmek için güçlü entegrasyon araçları sunar. GitHub Actions, bu süreçlerin otomatikleştirilmesini sağlar.

**Özellikler:**

- **GitHub Actions:** Yazılım geliştirme, test, derleme ve dağıtım süreçlerini otomatikleştirmenizi sağlar. Herhangi bir değişiklik yapıldığında belirli işlemler otomatik olarak başlatılabilir.
- **CI/CD:** Yazılım geliştirme süreçlerinin sürekli olarak entegrasyon ve dağıtımını sağlar. Bu, hataları erken tespit etmeye, üretim ortamına güvenli bir şekilde kod göndermeye olanak tanır.

**Senaryo Örneği:**
Bir ekip, bir web uygulaması geliştiriyor ve her değişiklik sonrası uygulamanın test edilmesi gerekiyor. GitHub Actions, her pull request açıldığında veya her commit sonrası testlerin otomatik olarak çalışmasını sağlar.

**Steps:**

1. `.github/workflows/ci.yml` dosyası oluşturulup içerisine test sürecini tanımlayan bir workflow eklenir.
2. Her commit veya PR sonrası bu workflow otomatik olarak çalışır ve testler yapılır.

**Hands-On:**
GitHub Actions kullanarak basit bir CI/CD pipeline’ı kurun ve test süreçlerinin nasıl otomatikleştiğini gözlemleyin.

---

## **4. Proje Yönetimi ve İssue Takibi**

GitHub, yazılım geliştirme sürecindeki proje yönetimini de kolaylaştırır. **Issues** (Sorunlar) ve **Project Boards** gibi araçlar sayesinde ekip üyeleri, yapılacak işlere dair izleme yapabilir, görevleri atayabilir ve ilerlemeyi takip edebilir.

**Özellikler:**

- **Issues:** Yazılım geliştirme sırasında ortaya çıkan problemleri izlemek ve çözmek için kullanılır.
- **Project Boards:** Scrum veya Kanban gibi yöntemleri kullanarak projeyi yönetmek için görsel panolar sunar.
- **Milestones:** Proje takımlarının belirli hedeflere ulaşmasını sağlar ve bu hedeflere yönelik ilerlemeyi takip edebilir.

**Senaryo Örneği:**
Bir ekip, belirli bir özellik üzerinde çalışırken, bu özelliğin tamamlanması için bir milestone belirler. Her sorun (issue) ile bu hedefe yaklaşılır ve her biri bitirildikçe milestone ilerler.

**Steps:**

1. GitHub Issues kullanarak yeni bir issue oluşturulur.
2. İlgili geliştiriciye atanır ve ilerleme takip edilir.
3. Milestone tamamlanınca, projenin durumu güncellenir.

**Hands-On:**
GitHub Issues kullanarak bir bug rapor edin, bunu bir milestone’a atayın ve bir proje board üzerinden yönetmeyi deneyin.

---

## **5. Açık Kaynak Projelere Katkı**

GitHub, açık kaynak yazılım projelerine katkıda bulunmak için en popüler platformdur. Herkesin katkı sağlayabileceği projeler için kolay bir erişim sağlar.

**Özellikler:**

- **Forking:** Başka projeleri kopyalayarak kendi versiyonunuzu geliştirme imkanı verir.
- **Open Source:** GitHub, yazılım geliştiricilerinin açık kaynak projelerde katkı sağlamasına olanak tanır.
- **Contributing:** Katkı sağlamak için belirli kurallar ve yönergeler içerir.

**Senaryo Örneği:**
Bir geliştirici, GitHub’daki açık kaynak bir projeye katkı sağlamak için repo’yu fork eder, geliştirme yapar ve pull request gönderir.

**Steps:**

1. GitHub üzerinden popüler bir açık kaynak proje bulunur.
2. Proje fork edilir, üzerinde değişiklik yapılır ve PR açılır.

**Hands-On:**
Bir açık kaynak proje fork edin, üzerinde değişiklik yapın ve PR gönderin. Geliştiriciler tarafından gözden geçirilen değişikliklerin nasıl kabul edildiğini gözlemleyin.
