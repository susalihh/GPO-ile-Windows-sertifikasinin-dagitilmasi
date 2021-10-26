# GPO (Group Policy Object) ile Windows sertifikasının dağıtılması

SSL sertifikası, bir web sitesinin kimliğini doğrulayan ve şifreli bir bağlantı sağlayan dijital bir sertifikadır. Web üzerinden bir sunucu ve tarayıcı arasındaki bağlantıyı şifreleyen bir güvenlik protokolüdür. 

İnternet bağlantılarını güvenli kılar ve iki sistem arasındaki bilgilerin okumasını ya da değiştirmesini önler.

Şirketler ve kurumlar müşteri bilgilerinin gizliliğini ve güvenliği sağlamak için web sitelerine SSL sertifikaları eklemelidir. Bu veriler adresler, kredi kartı numaraları veya diğer finansal bilgiler gibi hassas olabilecek bilgilerdir.

SSL sertifikası çalışma adımları;

1. Bir tarayıcı ya da sunucu, SSL ile güvenli hale getirilmiş bir web sunucusuna bağlanma girişiminde bulunur.
2. Tarayıcı ya da sunucu, web sunucusundan kendisini tanımlamasını ister.
3. Web sunucusu, yanıt olarak tarayıcı ya da sunucuya SSL sertifikasının bir kopyasını gönderir.
4. Tarayıcı ya da sunucu, SSL sertifikasına güvenip güvenmediğine karar vermek için sertifikayı kontrol eder. Sertifikaya güvenirse web  sunucusuna güvenli olduğuna dair bir sinyal gönderir.
5. Ardından web sunucusu, SSL şifreli oturum başlatmak için dijital olarak imzalanmış bir onay ile yanıt verir.
6. Şifreli veriler, tarayıcı veya sunucu ile web sunucusu arasında paylaşılır.

Web sitesi güvenli hale gelmişse URL'de HTTPS kısaltması görünür eğer SSL sertifikası yok ise S harfi olmadan sadece HTTP kısaltması görünür.

Kurumlar kullanıcılarının internet erişimi ve bant genişliğini proxy sistemleri üzerinden geçirerek kontrol eder ve yönetirler. Bu yönetimde http ile  çalışan siteler için sorun yoktur ancak https ile çalışan siteler için bir bloklama yada loglama gibi birşey yapılacaksa ilgili proxy ürününün self sign imzalanmış sertifikasının tüm istemcilere manuel olarak yüklenmesi gerekmektedir. Sonrasında proxy ürünü https'li siteleri yönetebilecektir.

**GPO (Group Policy Object) ile Windows sertifikasının dağıtılması**

İlk önce Windows Server Manager'dan **Tools/Group Policy Management**'ı açıyoruz.

![](https://github.com/susalihh/GPO-ile-Windows-sertifikasinin-dagitilmasi/blob/main/gpo1.png)

Daha sonra **Domains/domanin-name/Default Domain Policy**'ye sağ tıklayıp edit diyoruz.

![](https://github.com/susalihh/GPO-ile-Windows-sertifikasinin-dagitilmasi/blob/main/gpo2.png)

**Computer Configuration** altında **Policies/Windows Settings/SecuritySettings/Public Key Policies/ Trusted Root Certificate Authorities**'e tıklıyoruz ve sağdaki alana sağ tıklayıp **Import** seçeneğini seçiyoruz.

![](https://github.com/susalihh/GPO-ile-Windows-sertifikasinin-dagitilmasi/blob/main/gpo3.png)

Pencerede sertifikanın bilgisayar deposuna ekleneceğini görüyoruz. **Next** diye devam ediyoruz. Sonraki gelen ekranda sertifika dosyasını seçmemizi istiyor, sertifikanın olduğu dosyayı seçip **Next** diye devam ediyoruz.

![](https://github.com/susalihh/GPO-ile-Windows-sertifikasinin-dagitilmasi/blob/main/gpo4.png)

Tekrar **Next** diye devam ediyoruz ve sonraki ekranda bi özet bilgisi geliyor, **Finish** diyerek bitiriyoruz.

Son adımda işlemin başarılı olduğuna dair bir bilgilendirme kutusu çıkıyor ve sertifikanın GPO içine başarılı bir şekilde eklendiğini görüyoruz.

![](https://github.com/susalihh/GPO-ile-Windows-sertifikasinin-dagitilmasi/blob/main/gpo5.png)

Kullanıcı bir sonraki oturum açtığında, bu ayarlar uygulanacak ve sertifikaya Internet tarayıcısı tarafından güvenilecektir.
