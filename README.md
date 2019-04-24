# utkuici
Utkuici - Kurbanı Ülgen'e ileten ruh

Günümüzde bilgi teknolojileri sistemlerinin yaygınlaşması ile birlikte siber güvenlik alanında yatırımlar büyük ölçüde artmıştır. Kurumlarımızın siber tehditlerden ne kadar etkilenebileceğini doğru belirlemek için zafiyet yönetimi, sızma testleri ve çeşitli analizler yapılmaktadır. Zafiyet yönetim araçlarından sektör lideri olan Tenable Nessus ile kurum ağına yeni katılan IP adresi, yeni açılan bir port, exploit edilebilir zafiyetler belirlenebilmektedir ve bu işlemlerin otomatik belirlenmesi için Tenable Nessus ile entegre çalışabilecek bir python uygulaması geliştirilmiştir.

Kurulum:

pip install requests

Kullanımı:

python yeniIPBulma.py  -> access ve secret keyleri girdikten sonra yeni bulunan IP adresini SIEM'e göndermeyi sağlar

python yeniPortBulma.py -> access ve secret keyleri girdikten sonra yeni bulunan port bilgisini SIEM'e göndermeyi sağlar

python exploitEdilebilirServisiBul.py -> access ve secret keyleri girdikten sonra yeni bulunan istismar edilebilir zafiyet hakkındaki bilgileri SIEM'e göndermeyi sağlar

Yapılan Çalışma:

Utkuiçi ile kurum/kuruluş ağına yeni katılan IP adresinin tespit edilmesi sağlanarak bu bilginin SIEM’e otomatik iletilmesi sağlanmıştır.
 
<img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_2.png">

Yeni bir IP adresinin tam olarak tespit edilebilmesi için Nessus tarama adında “Host Discovery” kelime öbeğinin geçip geçmediği kontrol edilmiş ve canlı olan IP adresleri zaman damgası ile veritabanına kaydedilmiş, fark IP adresi ise SIEM’e gönderilmiştir. Hosts tablosunun içeriği aşağıdaki şekildedir:
 
<img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_5.png">

Kurumda bir IP adresi envanterden çıktığı zaman veya sistem kapatıldığı zaman ipSil.py kodu ile veritabanından IP adresi silinebilmektedir.
 
<img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_7.png">

Nessus tarafından yapılan port taramalarını kontrol ederek port-IP-zaman damgası bilgisi veritabanına kaydedilmekte, yeni açılan bir servisin veritabanı üzerinden tespit ederek “Yeni Port:”port-IP-zaman damgası şeklinde SIEM’e veriyi iletmektedir.
Portlar tablosunun içeriği aşağıdaki şekildedir:
 
<img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_4.png">

SIEM tarafından gözlemlenen sonuç aşağıdaki şekildedir:
 
<img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_3.png">

Kurumda bulunan bir servis kapatıldığı zaman veritabanından aşağıdaki şekilde bilgi silinebilmektedir:
 
<img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_8.png">

Kurum ve kuruluşlarda yapılan zafiyet taramalarında çıkan bulgularda öncelikli olarak istismar edilebilir zafiyetlerin kapatılması gerekmektedir. Utkuiçi aynı zamanda kurumlarda bulunan metasploit ile istismar edilebilen zafiyetleri veritabanına kaydederek sistemler üzerinde farklı bir istismar edilebilen zafiyet bulduğu zaman SIEM’e bu bilgiyi iletmektedir.
Not: İstismar edilebilir zafiyetlerin net bir şekilde belirlenebilmesi için domain admin kullanıcısı ile istemci ve sunucular zafiyet taramasına tabi tutulması önerilmektedir. 
SIEM tarafında gözlemlenen istismar edilebilir zafiyetler:
 
<img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_1.png">

Uygulama kullanılması aşamasında Nessus tarafından üretilen secret ve access keyler python kodları içerisine düzenlenmelidir. Access ve secret keylere Nessusta Settings -> My Account -> API Keys sekmeleri tıklandıktan sonra generate butonuna basılmalıdır.

 <img src="https://github.com/anilbaranyelken/utkuici/blob/master/Screenshot_9.png">
