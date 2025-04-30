# AWS Global Infrastructure

AWS küresel altyapısını anlamak için bir kahve dükkanını düşünebilirsiniz. Eğer bir olay; örneğin bir geçit töreni, sel ya da elektrik kesintisi bir şubeyi etkilerse, müşteriler sadece birkaç blok ötede bulunan başka bir şubeye giderek yine kahvelerini alabilirler. AWS Global Infrastructure da buna benzer çalışır.

AWS’in dünya genelinde “Region” adı verilen birçok coğrafi bölgeye yayılmış veri merkezleri vardır. Her Region, kendi içinde birden fazla “Availability Zone” barındırır ve bu Zone’lar birbirinden fiziksel olarak ayrıdır. Region’lar, birbirlerinden izole şekilde çalışır ve aralarında yüksek hızlı fiber ağ bağlantıları bulunur. Bu yapı, hem güvenliği artırır hem de olası felaket durumlarında high availability sağlamak açısından kritiktir. Hizmetleriniz, verileriniz ve uygulamalarınız için doğru AWS Region’ı belirlerken, aşağıdaki dört iş faktörünü göz önünde bulundurmalısınız:

> 1- Compliance with data governance and legal requirements

Compliance Requirements bir kuruluşun, yasal yükümlülüklere (veya sektörel standartlara) uyma zorunluluğudur. Şirketin iç politikaları, etik kuralları da buna dahil olabilir. Legal Requirements ise yasal yükümlülüklerdir. Devletin, ülkenin, düzenleyici kurumların koyduğu kanunlar ve mevzuatlardır.

Şirketinize ve bulunduğunuz konuma bağlı olarak, verilerinizi belirli bölgelerden çalıştırmanız gerekebilir. Örneğin, eğer şirketiniz, tüm verilerinin Birleşik Krallık sınırları içinde kalmasını şart koşuyorsa, London Region (Londra Bölgesi)’ni seçmeniz gerekir.

Ancak her şirketin böyle konuma özel veri düzenlemeleri olmayabilir. Bu durumda, diğer üç iş faktörüne (proximity to your customers, available services within a region ve pricing) daha fazla odaklanmanız gerekebilir.

> 2- Proximity to your customers

Müşterilerinize daha hızlı içerik ulaştırmak istiyorsanız, onlara yakın bir Region seçmek faydalı olacaktır. 

Örneğin, şirketiniz Washington, DC merkezliyse ve müşterilerinizin çoğu Singapur’da yaşıyorsa; altyapınızın bir kısmını Northern Virginia Region’da şirket merkeziyle yakın tutabilir, uygulamalarınızı ise Singapore Region’dan çalıştırarak müşterilere daha düşük latency ile hizmet sunabilirsiniz.

> 3- Available services within a Region

Bazen size en yakın olan AWS Region, müşterilere sunmak istediğiniz tüm hizmetleri içermeyebilir. AWS sürekli olarak yeni hizmetler geliştirir ve mevcut hizmetlerin yeteneklerini genişletir. Ancak bu yeni hizmetleri tüm dünyaya sunmak zaman alabilir çünkü AWS’nin, her Region için fiziksel altyapı kurması gerekebilir.

Örneğin, geliştiricileriniz Amazon Braket (AWS’nin kuantum bilişim platformu) kullanan bir uygulama geliştirmek istiyor. Şu anda Amazon Braket'ın tüm AWS Region'larında mevcut olmadığını varsayarsak, geliştiricileriniz uygulamayı, bu hizmetin zaten sunulduğu bir Region’da çalıştırmak zorundadır.

> 4- Pricing

Diyelim ki uygulamalarınızı hem Amerika Birleşik Devletleri’nde hem de Brezilya’da çalıştırmayı düşünüyorsunuz.Brezilya’nın vergi yapısı nedeniyle, aynı iş yükünü São Paulo Region’unda çalıştırmak, Oregon Region’una kıyasla %50 daha pahalı olabilir. Sonuç olarak, hizmet maliyetleri, Region’dan Region’a değişebilir.

--------------------------------------------------------------------------------------------------------------------------------

Availability Zone, bir Region (bölge) içindeki tekil bir veri merkezi veya birden fazla veri merkezinden oluşan bir gruptur. Availability Zone’lar, birbirlerinden onlarca mil uzaklıktadır. Bu mesafe; düşük gecikme süresi (low latency) sağlayacak kadar yakındır, ancak aynı zamanda, bir bölgede bir felaket (disaster) meydana geldiğinde, birden fazla Availability Zone’un aynı anda etkilenmesini önleyecek kadar da uzaktır.

Sadece bir availability zone'da çalışan bir instance'ınız olduğunu varsayarsak, bu availability zone'da oluşabilecek herhangi bir problem, sunduğunuz hizmeti veya instance üstünde yaptığınız herhangi bir işi tamamen devre dışı bırakacaktır.

AWS'in önerdiği en iyi yaklaşım, en az iki availability zone kullanmaktır. Böylece birinde problem olduğunda diğerini kullanabilirsiniz. Bu, resilient (dayanıklı) ve highly available (yüksek erişilebilirlik) bir mimari anlamına gelir. Yedek availability zone'lar, size disaster recovery sağlayacaktır.

## Edge Locations

Edge location, Amazon CloudFront’un içeriklerin önbelleğe alınmış (cached) kopyalarını, müşterilere daha yakın bir konumda depolayarak daha hızlı teslimat yapmasını sağlayan bir noktadır.

Amazon CloudFront, AWS’nin içerik dağıtım ağı (CDN - Content Delivery Network) servisidir. Amazon CloudFront'un amacı; veriyi, videoyu, uygulamayı veya API’yi kullanıcılara en hızlı ve en yakın yerden ulaştırmak.

Örneğin, EC2 üzerinde barındırdığınız bir web siteniz var. CloudFront bu verinin bir önbellek (cache) kopyasını, dünyanın dört bir yanındaki Edge Location’lara koyar. Kullanıcılar bu siteyi talep ettiğinde, en yakın edge location üzerinden teslim edilir. Böylece low latency ve yüksek hız sağlanır.

Ayrıca DNS çözümlemesi için Amazon Route 53 de bu lokasyonlarda çalışır.

### AWS Outposts

AWS Outposts, AWS’in kendi veri merkezinde sunduğu servisleri, senin binana, veri merkezine fiziksel olarak getirip kurduğu bir çeşit çözümdür. Örneğin, EC2'u kendi lokasyonunda çalıştırmak istiyorsun diyelim. AWS sana bir mini AWS altyapısı kuruyor, donanımıyla birlikte getiriyor.

Bu seçenek, özellikle verinin dışarı çıkmaması gereken sektörler için düşünülmüştür.

## Application Programming Interface (API)

Şimdiye kadar bir çok servisten konuştuk. Peki ama bu servislerle nasıl etkileşime geçiyoruz? Bunun cevabı API'lardır.

API en basit haliyle, farklı yazılımların veya sistemlerin birbirleriyle konuşmasını sağlayan bir arayüzdür. Yani bir menü gibi çalışır. 

Örneğin, bir restoranda menüde ne sipariş edebileceğin yazar. Sen yemeği yapmazsın, sadece sipariş verirsin. Aynı şekilde, API da sana "şunu yapabilirsin" diye bir liste sunar. Sen de o hizmeti kullanırsın ama nasıl yapıldığını bilmek zorunda değilsin.

Mesela telefonunuzda kullandığınız hava durumu, aslında başka bir meteoroloji API'sinden veri çeker.

AWS'de de aynı şekilde her şey bir API çağrısıdır (call). API, AWS servisleriyle etkileşime geçmek için önceden belirlenmiş yöntemler sunar. Bu API'ları çağırarak, AWS kaynaklarını oluşturabilir, yapılandırabilir ve yönetebilirsin.

Örneğin, bir EC2 instance’ı başlatmak veya bir AWS Lambda fonksiyonu oluşturmak istiyorsan, bunların her biri AWS’ye yapılacak farklı API çağrılarıdır. Bu çağrıları gerçekleştirmek için şunları kullanabilirsin:

- AWS Management Console

- AWS Command Line Interface (CLI)

- AWS Software Development Kits (SDK’ler)

- AWS CloudFormation gibi çeşitli araçlar

### AWS Management Console

- Web tabanlıdır. 

- AWS kaynaklarını görsel olarak, sindirmesi kolay bir şekilde yönetmeni sağlar.

- Başlangıçta AWS’i öğrenmek, test ortamları kurmak, fatura görüntülemek, izleme yapmak veya teknik olmayan kaynaklarla çalışmak için harikadır.

- Genellikle AWS’i öğrenmeye başladığında ilk gideceğin yerdir.

- Ayrıca konsol içinde yer alan sihirbazlar (wizards) ve otomatik iş akışları, görevleri tamamlamayı kolaylaştırır.

Bunların yanında, AWS Console mobil uygulaması ile:

- Kaynakları izleyebilir,

- Alarm durumlarını görebilir,

- Faturalama bilgilerine erişebilirsin.

Mobil uygulamada birden fazla kullanıcı kimliği (identity) aynı anda oturum açmış halde kalabilir.


*Ama bir üretim (production) ortamında çalışmaya başladıktan sonra, sadece tıklamalara dayalı görsel yöntemlere bağlı kalmak istemezsin. Örneğin, bir EC2 instance oluşturmak için birden fazla ekranı tıklaman, ayarları tek tek girmen gerekir. Sonra bir tane daha oluşturmak istersen, yine aynı adımları elle tekrar etmen gerekir. Bu tür manuel işlemlerde insan hatası riski çok yüksektir. Bu problemin çözümü, API çağrılarını betik (script) haline getiren araçlar kullanmaktır. Bunlardan biri de AWS Command Line Interface (CLI)'dır.*

### AWS Command Line Interface (CLI)

- Terminal üzerinden API çağrılarını yapmanı sağlar.

- Komut yazarak işlem yaparsın, bu da işlemleri script haline getirilebilir ve tekrar edilebilir kılar. Yani bir EC2 instance başlatmak için komut yazarsın, tekrar başlatmak istersen aynı komutu bir daha çalıştırırsın. İnsan hatası azalır ve bu komutları zamanlı veya olay tabanlı şekilde otomatik de çalıştırabilirsin.

Örneğin, bir Amazon EC2 instance’ı başlatma sürecini komutlarla gerçekleştirebilirsin.

Otomasyon, bulut ortamında başarılı ve öngörülebilir bir dağıtım için çok önemlidir.

##### NOT: Script, belirli işlemleri otomatik olarak ve sıralı şekilde yapan bir komutlar dizisidir. Yani tek tek elle yapacağın şeyleri, tek seferde ve hatasız şekilde yapmanı sağlar.

*AWS ile etkileşim kurmanın başka bir yolu da AWS Software Development Kits (SDK’ler) kullanmaktır.*

### AWS Software Development Kits (SDKs)

SDK genel olarak, bir servisi programlama dili üzerinden kullanmanı kolaylaştıran araç setidir.


AWS SDK’ler, AWS servislerini kullanmayı senin programlama diline veya platformuna özel API’ler aracılığıyla kolaylaştırır. SDK'ler sayesinde:

- Mevcut uygulamalarında AWS servislerini entegre edebilirsin,

- Ya da doğrudan AWS üzerinde çalışacak yepyeni uygulamalar geliştirebilirsin.

> AWS, SDK kullanmaya başlamanı kolaylaştırmak için; her desteklenen programlama dili için dökümantasyon ve örnek kodlar sağlar. Desteklenen diller arasında; C++, Java, .NET ve daha fazlası yer alır.


### AWS Elastic Beanstalk

AWS Elastic Beanstalk, sen sadece uygulama kodunu ve yapılandırma ayarlarını verirsin, gerisini o halleder. Elastic Beanstalk, uygulamanı çalıştırmak için gereken kaynakları otomatik olarak kurar ve şu işleri yapar:

- Kapasiteyi ayarlama (Adjust capacity)

- Load Balancing

- Auto-scaling

- Application health monitoring

Yani alt seviye altyapı işleriyle uğraşmadan, uygulamanı hızlıca yayına almanı sağlar.

Böylece, geliştirici sadece kendi uygulamasıyla ilgilenebilir, altyapı işlerini dert etmesine gerek kalmaz.

### AWS CloudFormation

AWS CloudFormation, altyapını kod gibi yönetmeni sağlayan bir servistir. Yani her şeyi AWS Console’da tıklayarak tek tek kurmak yerine, bir dosyaya (JSON veya YAML) yazarsın, CloudFormation da senin yerine o altyapıyı kurar.

- Sunucular (EC2)

- Veritabanları (RDS)

- Ağ ayarları (VPC, subnet)

- IAM rolleri, Lambda fonksiyonları, S3 bucket'ları gibi tüm kaynakları tek bir şablon (template) dosyasında tanımlarsın.

AWS CloudFormation, kaynaklarınızı güvenli ve tekrar edilebilir bir şekilde sağlar, bu sayede altyapınızı ve uygulamalarınızı sık sık tekrar oluşturabilir ve bunu yaparken manuel işlemler gerçekleştirmenize gerek kalmaz.

CloudFormation, bir yığını (stack) yönetirken gerçekleştirilmesi gereken doğru işlemleri belirler ve bir hata algılarsa değişiklikleri otomatik olarak geri alır (rollback).

#### NOT: Bu bağlamda stack, bir uygulama için EC2, S3, RDS ve IAM gibi AWS kaynaklarının (resources) bir arada tanımlanması ve yönetilmesidir.



















