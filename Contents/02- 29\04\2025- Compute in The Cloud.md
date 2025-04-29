# Amazon Elastic Compute Cloud (EC2)

Amazon EC2, AWS tarafından yönetilen fiziksel sunucular üzerinde sanallaştırma kullanarak, kullanıcıların sanal sunucular (instance'lar) oluşturmasına ve bu kaynakları kendi ihtiyaçlarına göre esnek şekilde kullanmasına olanak tanıyan bir hizmettir.

#### NOT: EC2 kavramındaki "2" elastic compute fikrinin ikinci versiyonu anlamına geliyor. İlk tasarımları çok daha ilkel olduğundan ikinci versiyonu geliştirilmiştir.

Şirketinizin kaynaklarının mimarisinden sorumlu olduğunuzu ve yeni web sitelerini desteklemeniz gerektiğini düşünün. Geleneksel şirket içi kaynaklarla şunları yapmanız gerekir:

- Donanımlar için ön harcama yapmanız gerekir.

- Sunucuların size teslim edilmesini beklemeniz gerekir.

- Sunucuları kendi data center'ınızda kurmanız gerekir.

- Tüm gerekli yapılandırmaları kendiniz yapmalısınız.

Buna karşılık, bir Amazon EC2 instance ile AWS Cloud'da uygulamaları çalıştırmak için sanal bir sunucu kullanırsanız:

- Dakikalar içerisinde bir EC2 instance'ı hazırlayabilir ve başlatabilirsiniz.

- İş yükünüz bittiğinde veya azaldığında kullanmayı bırakabilirsiniz.

- Sadece kullandığınız süre boyunca ödeme yaparsınız.

- Sadece ihtiyacınız olan kaynak kadar ödeme yaparsınız.

## How Amazon EC2 works

EC2 başlatıldığında, hangi OS'in kullanılacağı, application server veya application gibi yapılandırmaları seçersiniz. Ayrıca instance'ınıza özel donanım yapılandırması olan "instance type" da seçersiniz. Ek olarak, instance'nızda trafiği denetlemenize olanak tanıyan güvenlik yapılandırmalarını da belirleyebilirsiniz.

Daha sonrasında instance'a bağlanırsınız. Programlarınızın ve uygulamalarınızın instance'a doğrudan bağlanmak ve veri alışverişinde bulunmak için birden fazla farklı yöntemi vardır. Kullanıcılar ayrıca oturum açarak ve bilgisayarın masaüstüne erişerek instance'a bağlanabilir.

Instance'a bağlandıktan sonra onu kullanmaya başlayabilirsiniz. Yazılım yüklemek, depolama alanı eklemek, dosyaları kopyalamak ve düzenlemek ve daha fazlası için komutlar çalıştırabilirsiniz.

## Amazon EC2 Instance Types

Amazon EC2 instance türleri farklı görevler için optimize edilmiştir. Bir instance türü seçerken, iş yüklerinizin ve uygulamalarınızın özel ihtiyaçlarını göz önünde bulundurursunuz. Bu, compute, memory veya storage gibi yetenekler için gereksinimleri içerebilir.

### General Purpose Instances

Genel amaçlı instance'lar, hesaplama (compute), bellek ve ağ kaynakları arasında bir denge sağlar. Bunları çeşitli iş yükleri için kullanabilirsiniz, örneğin:

- uygulama sunucuları

- oyun sunucuları

- kurumsal uygulamalar için backend sunucuları

- küçük ve orta ölçekli veritabanları

Eğer uygulamalarınız herhangi bir kaynağın spesifik olarak optimize edilmesini gerektirmiyorsa, tüm kaynakları dengeli bir şekilde kullanabilirsiniz. Genel amaç için instance'lar tam olarak bunun içindir.

### Compute Optimized Instances

Compute optimized instances, çok yoğun işlem gücü isteyen işler için özel olarak tasarlanmış EC2 instance türleridir. Yani CPU performansının çok kritik olduğu işler için idealdirler. Normal işler için general purpose kullanılırken, işlemciyi çok fazla kullanan işler için compute optimized tercih edilir. 

- High-Performance Web Servers (Çok fazla kullanıcıya hızlı cevap vermesi gereken web siteleri)

- Compute-Intensive Application Servers (Çok ağır matematiksel hesaplama yapan backend sunucular)

- Dedicated Gaming Servers (FPS oyun sunucuları gibi sürekli CPU kullanan şeyler)

- Batch Processing (Bir anda milyonlarca işlemi toplu şekilde işlemek: büyük veri analizleri, finansal işlemler vs.)

### Memory Optimized Instances

Eğer uygulama çok fazla RAM kullanıyorsa, yani hafızaya aşırı yükleniyorsa, o zaman memory optimized (bellek optimize edilmiş) EC2 instance kullanılmalıdır. Çünkü bu instance'lar normalden çok daha fazla RAM verir. Böylece büyük veriler, gerçek zamanlı işlemler, yüksek performanslı veritabanları rahatça çalışır.

- High-Performance Databases (RAM içinde çalışan dev veritabanları – örneğin SAP HANA gibi.)

- Real-time Big Data İşlemleri (Mesela canlı canlı milyonlarca kullanıcıdan veri akıyor ve bunu anında analiz ediyorsun.)

### Accelerated Computing Instances

Accelerated computing instance'lar, bazı işlemleri CPU üzerinde yazılım çalıştırarak yapmaktan daha verimli şekilde gerçekleştirebilmek için donanım hızlandırıcıları veya yardımcı işlemciler (coprocessorlar) kullanır.

Bu işlemlere örnek olarak ondalıklı sayı (floating-point) hesaplamaları, grafik işleme ve veri desen eşleştirme verilebilir.

Bilgisayar biliminde, bir donanım hızlandırıcı, veri işleme sürecini hızlandırabilen bir bileşendir.

Accelerated computing instance'lar, grafik uygulamaları, oyun akışı (game streaming) ve uygulama akışı (application streaming) gibi iş yükleri için idealdir.

Özet olarak, bilgisayarda her işlemi CPU yapsa da yüksek çözünürlüklü grafik işleme, video encode/decode gibi işlemler için yetersiz kalabilir. Bu noktada "Hardware Accelerator" yani donanım hızlandırıcılar devreye giriyor. AWS de Accelerated Computing Instances ile donanımlarda CPU'ya ek olarak NVIDIA Tesla gibi GPU'lar veya özel hızlandırıcılar sağlıyor.

Örneğin Netflix, AWS’de NVIDIA T4 GPU’ları kullanan G4 instance ailesiyle çalışıyor. Veya Nvidia GeForce Now, tamamen accelerated computing üzerine kurulu: her kullanıcı için bir oyun çalıştırılıyor ve canlı canlı stream ediliyor.

#### NOT: Bu noktada CPU ve GPU farkını anlamak önemlidir. CPU, az işlem için ama çok akıllıca davranan yani değişken işler için tasarlanmıştır. Yani görece az ama kompleks işler için kullanılır. Bununla beraber grafik, aşırı miktarda küçük, birbirine çok benzeyen işlemlerdir. Dolayısıyla da GPU'lar daha basit ama çok sayıda işlemler için kullanılır. Örneğin, bir video işlemeye çalıştınığınızı varsayalım. Bir video demek milyonlarca piksel ve çok sayıda renk demektir. CPU bu kadar fazla işlemi teknik olarak işlerken çok zorlanacaktır. Bunun yerine GPU bunun gibi işler için birebirdir. CPU ise daha akıllı davranır ve mantık gerektiren değişken işlemler için idealdir.

### Storage Optimized Instances

Eğer uygulama sürekli olarak çok veri okuyorsa ve yazıyorsa, yani veri trafiği aşırı fazlaysa, Storage Optimized Instances kullanılması gerekir.

IOPS (Input/Output Operations Per Second), bir disk ya da storage cihazının 1 saniyede kaç tane veri girdi/çıktı işlemi yapabildiğini gösteren bir performans ölçüsüdür.  Storage Optimized Instances, çok yüksek IOPS ile beraber düşük latency sağlar.

## Amazon EC2 Pricing

Amazon EC2 ile yalnızca kullandığınız işlem süresi için ödeme yaparsınız. Amazon EC2, farklı kullanım durumları için çeşitli fiyatlandırma seçenekleri sunar. Bunlar 5 kategoriye ayrılır:

### On-demand Instances

On-Demand Instance'lar, kesintiye uğratılamayan, kısa süreli ve düzensiz iş yükleri için idealdir. 

Ön ödeme gerektirmez ve minimum sözleşme şartı yoktur. Instance'lar, siz durdurana kadar kesintisiz olarak çalışır ve yalnızca kullandığınız işlem süresi için ödeme yaparsınız. On-Demand Instance'ların örnek kullanım senaryoları arasında, uygulama geliştirme ve test etme ile usage pattern'ları öngörülemeyen uygulamaları çalıştırmak bulunur.

On-Demand Instance'lar, bir yıl veya daha uzun süre devam edecek iş yükleri için önerilmez.
Çünkü bu tür uzun süreli iş yükleri, Reserved Instance kullanarak daha fazla maliyet tasarrufu sağlayabilir.

### Reserved Instance

Reserved Instance'lar, hesabınızdaki On-Demand Instance kullanımı üzerine uygulanan bir faturalandırma indirimi türüdür.

İki tür Reserved Instance bulunmaktadır:

- Standard Reserved Instances

- Convertible Reserved Instances

Standard Reserved ve Convertible Reserved Instance'ları 1 yıllık veya 3 yıllık süreler için satın alabilirsiniz.
3 yıllık seçenekle daha büyük maliyet tasarrufu sağlarsınız.

| Özellik                       | Standard Reserved Instance                          | Convertible Reserved Instance                       |
|--------------------------------|-----------------------------------------------------|-----------------------------------------------------|
| İndirim Oranı                  | Daha yüksek (maksimum indirim)                      | Biraz daha düşük indirim oranı                       |
| Esneklik (Instance Değişimi)   | Yok (instance tipi, platform, bölge sabit kalır)    | Var (instance tipi, platform ve bölge değiştirilebilir) |
| Süre Opsiyonu                  | 1 yıl veya 3 yıl                                    | 1 yıl veya 3 yıl                                    |
| Kullanım Senaryosu             | Sabit, uzun süreli ihtiyaçlar için (değişmeyecek iş yükü) | İş yükü zamanla değişebilecek sistemler için         |
| Capacity Reservation (Kapasite Garantisi) | İstersen belirli Availability Zone için rezervasyon yapabilirsin (Daha önceden hiç rezervasyon yapılmadıysa) | İstersen belirli Availability Zone için rezervasyon yapabilirsin (Daha önceden rezervasyon yapılmış olsa bile mevcut olan değiştirilebilir.) |
| En Uygun Kullanım Durumu       | 7/24 çalışan, sabit bir uygulama                    | Gelecekte instance türü değiştirme ihtimali olan uygulamalar |

> Platform = Operating System

> Availability Zone = AWS'nin bir bölgede (region'da) bulunan birbirinden bağımsız, fiziksel veri merkezleri topluluğudur. Başka bir deyişle, Aynı şehirde (veya yakın bir alanda) bulunan, birbirinden ayrı veri merkezleri. Birbirinden elektrik, internet, bina, altyapı olarak ayrıdırlar. Ama aralarında çok hızlı ve güvenli bağlantılar vardır.

Sonuç olarak, -Standart Reserved Instances- Bu seçenek, sabit durum uygulamalarınız için ihtiyaç duyduğunuz EC2 örnek türünü ve boyutunu ve bunları hangi AWS Bölgesinde çalıştırmayı planladığınızı biliyorsanız iyi bir uyumdur.




















