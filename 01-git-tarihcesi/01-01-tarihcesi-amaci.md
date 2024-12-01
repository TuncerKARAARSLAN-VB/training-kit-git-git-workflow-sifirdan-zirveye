# **Kodun Geçmişini İzleme**  

Git'in doğuşu, yazılım geliştirme tarihinde önemli bir dönüm noktasıdır. Git, Linus Torvalds tarafından 2005 yılında geliştirilmiştir. Bu gelişim, aslında Linux çekirdeği projesi ve bir dizi olumsuz olayla doğrudan ilişkilidir. 

## **1. Linux Çekirdeği ve Versiyon Kontrolüne İhtiyaç**

Linux, açık kaynaklı bir işletim sistemi çekirdeği olarak 1991 yılında Linus Torvalds tarafından başlatıldı. Başlangıçta, küçük bir toplulukla geliştirilmekte olan Linux çekirdeği, zamanla büyük bir açık kaynak projesine dönüştü. Bu, çok sayıda geliştiricinin katkı sağlaması gereken ve bu katkıları düzgün bir şekilde izlemek ve yönetmek için bir **versiyon kontrol sistemi (VCS)** gereksinimini ortaya çıkardı.

Linux çekirdeği ilk başta **BitKeeper** adlı ticari bir versiyon kontrol sistemi ile yönetiliyordu. BitKeeper, dağılmış bir yapıya sahipti ve Linux geliştiricilerinin kendi yerel kopyalarında bağımsız bir şekilde çalışabilmelerini sağlıyordu. Ancak, BitKeeper'in kullanımı belli sınırlamalarla geldi. Şirket, ücretsiz kullanım için lisans veriyordu ancak bu lisans bir noktada değişti ve ücretsiz kullanım sınırlandı.

## **2. BitKeeper Krizi**

2005 yılında, BitKeeper'in ücretsiz lisansını iptal etmesi ve bazı Linux geliştiricilerinin sistemin kaynak koduna erişim talebinin reddedilmesi, Linux çekirdeği geliştirme topluluğunda büyük bir kriz yarattı. Bu durum, Torvalds ve diğer geliştiriciler için büyük bir sorun teşkil etti. Linux çekirdeği projesinin büyük bir kısmı, BitKeeper gibi ticari bir yazılım aracılığıyla yönetiliyordu ve bu sistemin devre dışı kalması, projedeki iş akışlarını etkileyebilirdi.

Bu krizin ardından, Linus Torvalds kendi dağıtık versiyon kontrol sistemi yazmayı düşündü. Bu sistemin, özellikle **dağıtık (distributed)** bir yapıya sahip olması ve tüm geliştiricilerin yerel kopyalarında bağımsız bir şekilde çalışabilmesi gerekiyordu. Ayrıca, Torvalds, sistemin açık kaynaklı olmasını ve tamamen geliştirici topluluğu tarafından yönetilmesini istedi.

## **3. Git’in Doğuşu**

Linus Torvalds, BitKeeper krizinden sonra yeni bir versiyon kontrol sistemi tasarlamaya karar verdi. Git, hızlı, güvenli ve verimli olması için tasarlandı. Ayrıca, dağıtık yapısı sayesinde geliştiricilerin merkezi bir sunucuya bağlı kalmadan projelerinde çalışabilmeleri sağlandı. Git, ayrıca commit geçmişinin **hash değeriyle** güvenli bir şekilde kaydedilmesini sağlar, böylece her değişiklik izlenebilir ve geri alınabilir. Bu, Git’in açık kaynak projelerinde ve büyük yazılım projelerinde neden bu kadar yaygın kullanıldığını açıklayan önemli bir özelliktir.

Git’in temel felsefesi şu özelliklere dayanıyordu:

- **Dağıtık yapı:** Her geliştirici, kendi yerel bilgisayarında tam bir depo (repository) kopyasına sahip olur. Merkezi bir sunucuya bağımlılık ortadan kaldırılır.
- **Hız ve Verimlilik:** Git, büyük projelerde hızlı çalışacak şekilde optimize edilmiştir. Özellikle **branching** (dal oluşturma) ve **merging** (birleştirme) işlemleri, diğer sistemlere göre çok daha hızlıdır.
- **Veri bütünlüğü:** Git, her değişikliğin bir **hash** değeri ile kaydedilmesini sağlayarak verilerin güvenliğini artırır.

## **4. Git'in İlk Yayınlanması**

Git, 2005 yılında Linus Torvalds tarafından açık kaynak olarak geliştirilmeye başlandı. İlk başta birkaç temel özellik vardı ve bu özellikler zamanla geliştirildi. Git, **ilk olarak Linux çekirdeği geliştirme süreci** için tasarlanmış olsa da, kısa süre içinde tüm yazılım geliştirme toplulukları tarafından kabul edilmeye başlandı.

Torvalds'ın Git için oluşturduğu ana hedef, **hız, güvenlik, esneklik ve verimlilik**ti. Git’in popülaritesi hızla arttı, çünkü büyük yazılım projelerinin yönetilmesinde büyük avantajlar sundu. Ayrıca, diğer versiyon kontrol sistemlerine göre daha uygun maliyetli ve esnek bir seçenekti.

## **5. Git’in Evrimi ve Bugünkü Durumu**

Git, ilk başlarda yalnızca Linux çekirdeği projesiyle ilişkilendirilmiş olsa da, zamanla tüm yazılım endüstrisinde en yaygın kullanılan versiyon kontrol sistemi haline geldi. Git'in açık kaynaklı olması ve topluluk tarafından sürekli geliştirilmesi, onu çok hızlı bir şekilde popülerleştirdi.

Git, **GitHub** gibi platformlarla birleşerek **açık kaynak yazılım geliştirme** topluluklarını birbirine daha yakın hale getirdi. GitHub, Git’i daha erişilebilir kılarken, yazılım projelerinin daha kolay paylaşılmasını ve işbirliği yapılmasını sağladı. Bugün, Git ve GitHub, yazılım geliştirme dünyasında **geliştiricilerin vazgeçilmez araçları** olarak kabul edilmektedir.

---

## **Özetle: Git'in Doğuşu**

Git, Linus Torvalds tarafından 2005 yılında, Linux çekirdeği için daha etkili ve güvenli bir versiyon kontrol sistemi ihtiyacından doğmuştur. BitKeeper'in lisans sorunları ve kaynak kodunun kapalı olması, Git'in yaratılmasına zemin hazırlamıştır. Git’in dağılmış yapısı, hız, güvenlik, esneklik ve verimlilik gibi özellikleri, onu yazılım geliştirme dünyasında bir devrim haline getirmiştir. Bugün Git, en yaygın kullanılan versiyon kontrol sistemi olup, yazılım geliştirme süreçlerinde önemli bir rol oynamaktadır.
