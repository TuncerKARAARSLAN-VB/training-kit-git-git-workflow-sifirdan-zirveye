# **SSH Anahtarları ve İki Faktörlü Kimlik Doğrulama (2FA) Kullanımı**

GitHub gibi platformlarda **SSH anahtarları** ve **iki faktörlü kimlik doğrulama (2FA)** kullanımı, güvenliği artırmak için en etkili yöntemler arasında yer alır. Bu modülde, SSH anahtarlarının nasıl oluşturulup kullanılacağını, 2FA’nın yapılandırılmasını ve her iki yöntemin kullanım senaryolarını ele alacağız.

---

## **1. SSH Anahtarları**

### **a. SSH Nedir ve Neden Kullanılır?**

- SSH (Secure Shell), uzak bir sunucuya güvenli bir şekilde bağlanmayı sağlar.  
- GitHub ile SSH kullanımı, parolasız bağlantı kurmanıza ve depolarınızı güvenli bir şekilde klonlamanıza, itmenize (push) ve çekmenize (pull) olanak tanır.  

**Avantajları:**  

1. Parola gereksinimini ortadan kaldırır.  
2. İletişimi şifreler.  
3. Güvenlik risklerini azaltır.  

---

### **b. SSH Anahtarı Nasıl Oluşturulur?**

**Adım 1: Anahtar Çifti Oluşturma**

```bash
ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
```

- `-t rsa`: RSA türünde bir anahtar oluşturur.  
- `-b 4096`: Anahtarın uzunluğu.  
- `-C`: Anahtarınıza bir açıklama ekler.  

Anahtar çiftiniz genellikle şu konumda saklanır:  
`~/.ssh/id_rsa` (özel anahtar)  
`~/.ssh/id_rsa.pub` (açık anahtar)

**Adım 2: SSH Anahtarını GitHub’a Eklemek**

1. **Açık Anahtarı Kopyalayın:**  

   ```bash
   cat ~/.ssh/id_rsa.pub
   ```

2. GitHub’da **Settings > SSH and GPG keys** bölümüne gidin ve yeni bir SSH anahtarı ekleyin.  
3. Anahtarı ekleyip kaydedin.

**Adım 3: Bağlantıyı Test Edin**

```bash
ssh -T git@github.com
```

---

### **c. SSH Kullanımı: Hands-On Görev**

1. Katılımcılar, kendi SSH anahtar çiftlerini oluşturur ve GitHub hesaplarına ekler.  
2. Uzak bir depoyu klonlayarak bağlantının çalıştığını test ederler:

   ```bash
   git clone git@github.com:kullanici_adi/depo_adi.git
   ```

---

## **2. İki Faktörlü Kimlik Doğrulama (2FA)**

### **a. 2FA Nedir ve Neden Önemlidir?**

- 2FA, hesaba giriş yaparken birden fazla kimlik doğrulama yöntemi kullanarak güvenliği artırır.  
- Parola tabanlı saldırılara karşı ek bir güvenlik katmanı sağlar.

**Kimlik Doğrulama Türleri:**  

1. **SMS:** Telefonunuza bir kod gönderilir.  
2. **Uygulama Tabanlı:** Google Authenticator, Authy gibi uygulamalar.  
3. **Donanım Tabanlı:** YubiKey gibi fiziksel cihazlar.

---

### **b. 2FA Nasıl Etkinleştirilir?**

1. **GitHub Ayarlarına Gidin:**  
   - `Settings > Password and authentication` sekmesine tıklayın.

2. **2FA’yı Etkinleştirin:**  
   - "Enable two-factor authentication" seçeneğini seçin.

3. **Yöntem Seçimi:**  
   - Bir kimlik doğrulama uygulaması veya SMS seçin.  
   - QR kodu taratın ve oluşturulan kodu girin.

4. **Yedek Kodları Kaydedin:**  
   - 2FA cihazınıza erişiminizi kaybederseniz, bu kodları kullanabilirsiniz.

---

### **c. 2FA Kullanımı: Hands-On Görev**

1. Katılımcılar, GitHub hesaplarında 2FA’yı etkinleştirir.  
2. Oturum açmayı ve kimlik doğrulama işlemini test ederler.  
3. 2FA etkinleştirildikten sonra bir depoyu klonlamaya çalışarak SSH anahtarlarının çalışıp çalışmadığını doğrularlar.

---

## **3. Senaryolar ve Çözümler**

### **Senaryo 1: SSH Anahtarı ile Parolasız Bağlantı**

**Durum:**  
Bir geliştirici, depoya sürekli giriş yapmak yerine parolasız bir çözüm arıyor.

**Çözüm:**  

- SSH anahtarı oluşturulur ve GitHub’a eklenir.  
- Depo, SSH protokolü kullanılarak klonlanır.

**Hands-On:**  
Katılımcılar, SSH ile bağlantı kurarak bir projeyi yönetir.

---

### **Senaryo 2: 2FA İle Hesap Güvenliği**

**Durum:**  
Bir ekip üyesi, GitHub hesabının güvenliğini artırmak için 2FA kullanmak istiyor.

**Çözüm:**  

- 2FA, kimlik doğrulama uygulaması kullanılarak etkinleştirilir.  
- Yedek kodlar kaydedilir.

**Hands-On:**  
Katılımcılar, 2FA etkinleştirir ve oturum açmayı test eder.

---

### **Senaryo 3: 2FA ve SSH ile Güvenli İş Akışı**

**Durum:**  
Bir kullanıcı, 2FA etkinleştirildiğinde `git push` sırasında parola istenmesinden rahatsız oluyor.

**Çözüm:**  

- SSH anahtarı ile bağlantı kurulması sağlanır.  
- 2FA etkinliğini korurken parolasız işlem yapılır.

**Hands-On:**  
Katılımcılar, SSH bağlantısını 2FA ile birleştirerek güvenli bir iş akışı oluşturur.

---

## **4. En İyi Uygulamalar**

- **SSH Anahtarlarını Güvende Tutun:** Özel anahtarınızı asla paylaşmayın.  
- **Güçlü Parolalar Kullanarak Anahtar Şifreleyin:** Anahtar oluştururken bir parola belirleyin.  
- **Yedek Kodları Güvende Saklayın:** 2FA cihazınıza erişiminizi kaybettiğinizde bu kodlar hayat kurtarabilir.  
- **Periyodik Kontroller:** SSH anahtarlarını ve 2FA ayarlarını düzenli olarak kontrol edin.  
