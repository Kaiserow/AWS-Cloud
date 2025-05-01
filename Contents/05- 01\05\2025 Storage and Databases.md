# Instance Stores

Instance store'lar blok düzeyinde (block-level) depolama birimleri, fiziksel sabit diskler gibi davranır.

Bir instance store, Amazon EC2 instance’ı için geçici block-level depolama sağlar. Bu depolama türü, EC2 instance’ının çalıştığı ana bilgisayara fiziksel olarak bağlı bir disk alanıdır. Bu nedenle, ömrü instance ile aynıdır. Instance sonlandırıldığında, instance store’daki tüm veriler silinir.

Amazon EC2 instance’ları sanal sunuculardır. Bir instance’ı durdurulmuş durumdan başlatırsan, instance farklı bir fiziksel ana bilgisayarda başlatılabilir. Bu durumda, daha önce kullandığın instance store volume artık mevcut olmayabilir. Bu nedenle AWS, instance store’ları sadece geçici verilere ihtiyaç duyulan kullanım senaryoları için önerir — yani uzun vadede saklaman gerekmeyen veriler için idealdir.

*Uzun vadeli depolama istiyorsanız, "Amazon Elastic Block Store (Amazon EBS)" kullanmanız gerekebilir.*

# Amazon Elastic Block Store (Amazon EBS)

Amazon Elastic Block Store (Amazon EBS), Amazon EC2 instance’larıyla birlikte kullanabileceğin block-level (blok düzeyinde) depolama alanı sağlayan bir servistir.

Bir EC2 instance’ını durdurur ya da sonlandırırsan, ona bağlı olan EBS volume üzerindeki veriler kaybolmaz, erişilebilir olmaya devam eder. Çünkü EC2 instance'larından ayrı çalışırlar, yani instance store'lar gibi fiziksel olarak bağlı değillerdir.

Bir EBS volume oluşturmak için, önce yapılandırmasını (örneğin boyut ve tür) belirlersin ve provisioning işlemiyle oluşturursun. Oluşturduktan sonra bu volume, bir EC2 instance’a bağlanabilir.

EBS volume’lar kalıcı veri saklamak için kullanıldığından, veriyi yedeklemek önemlidir. Bu yüzden Amazon EBS snapshot oluşturarak artımlı (incremental) yedeklemeler alabilirsin.

## Amazon EBS snapshots

Incremental (artımlı) yedekleme, sadece önceki yedekten sonra değişen verileri yedekleyen bir tekniktir. Örneğin, ilk başta 10 GB'lık bir yedek aldın diyelim. Daha sonra yedek alacağın zaman, aynı yedekleri tekrar tekrar almak yerine, sadece değişen veriyi yedek alırsın. Örneğin, sadece 1 GB veri değiştiyse, 1 GB veriyi yedekler. EBS snapshot'ları tam bu şekilde çalışır. İlk snapshot tüm veriyi içerir, sonraki snapshot’lar sadece değişiklikleri içerir. Full backup ise değişmemiş verileri bile tekrar tekrar kopyalar.

# Amazon Simple Storage Service (Amazon S3) [Baş harflerinde 3 tane S olduğundan S3]

## Object Storage

Nesne (object) depolamada, her nesne veri, metadata (üst veri) ve bir anahtardan (key) oluşur.

- Veri (data): Görsel, video, metin dosyası ya da başka herhangi bir dosya türü olabilir.

- Metadata (üst veri): Verinin ne olduğu, nasıl kullanıldığı, nesnenin boyutu gibi bilgileri içerir.

- Anahtar (key): Nesnenin benzersiz tanımlayıcısıdır. Bu anahtar sayesinde nesneye erişilir.

Yani, nesne depolamada her şey bu üç parçanın birleşimiyle tanımlanır.

Hatırlarsanız, blok depolamada (block storage) bir dosyayı değiştirdiğinde, yalnızca değişen parçalar güncelleniyordu. Ama nesne depolamada (object storage) bir dosya değiştirildiğinde, tüm nesne (object) yeniden güncellenir ve yüklenir.

#### NOT: Bu olay, incremental ve yedekleme konularından bağımsız, dosyada herhangi bir değişiklik olmasıyla ilgilidir.

> Block Storage vs Object Storage

Daha net anlatmak gerekirse; Object storage'da; Nesne (object) = Data + Metadata + Key 'den oluşur ve bunlar tek parça olarak ele alınır. Bu nesnede oluşan en ufak değişiklik bile tüm nesnenin (data, metadata, key birlikte) yeniden yazılmasına sebep olur. Yeniden yazmak, içeriği değiştirmek değildir. Bazı içerikler aynı kalabilir ama sonuç olarak aynı şey de olsa tekrar yazılır. Örneğin, metadata’yı değiştirmezsen bile, yeni nesneye aynı metadata tekrar yazılmış olur.

Block storage'da; Veri, küçük bloklara bölünür. Bir dosyada sadece değişen bloklar güncellenir.

Örneğin, Bir EBS volume üzerinde 10 MB’lık bir dosyan var. Sen bu dosyada sadece son 1 MB’ı değiştiriyorsun.

Object storage olsaydı -> Tüm 10 MB yeniden yazılırdı. Fakat:

Block storage olduğu için -> Sadece değişen 1 MB’lık blok yeniden yazılır.

*Amazon Simple Storage Service (Amazon S3)'e devam edecek olursak:*

Amazon Simple Storage Service (Amazon S3), object düzeyinde depolama sağlayan bir servistir. Amazon S3, verileri bucket’lar içinde nesneler (object) olarak depolar.

Amazon S3’e görseller, videolar, metin dosyaları gibi her türlü dosyayı yükleyebilirsin. Örneğin, yedekleme dosyalarını, bir web sitesi için medya dosyalarını veya arşivlenmiş belgeleri saklamak için Amazon S3’ü kullanabilirsin. 

S3, sınırsız depolama imkanı sunar fakat Amazon S3’teki bir nesne başına maksimum dosya boyutu 5 TB’tır. Örneğin, 10 tane 5 TB dosya yüklersen 50 TB olur. Daha fazlasını yüklersen de daha fazlası olabilir. Tek sınırlama dosya başına 5 TB olmasıdır.

Bir dosyayı Amazon S3’e yüklediğinde, dosyanın görünürlüğünü ve erişimini kontrol etmek için izinler ayarlayabilirsin. Ayrıca, zaman içinde nesnelerindeki değişiklikleri takip etmek için Amazon S3 versioning (versiyonlama) özelliğini kullanabilirsin.

Versioning (versiyonlama), Amazon S3’te aynı nesnenin birden fazla sürümünü saklamanı sağlayan özelliktir. Böylece, bir dosyayı (nesneyi) yanlışlıkla silersen veya üzerine yazarsan, önceki sürümüne geri dönebilirsin. Her yükleme veya değişiklik, yeni bir versiyon oluşturur. Eski sürüm silinmez, sadece "önceki versiyon" olarak kalır.

## Amazon S3 storage classes

Amazon S3 ile yalnızca kullandığın kadar ödeme yaparsınız. İşine ve maliyet ihtiyaçlarına uygun olanı seçmek için çeşitli depolama sınıfları arasından seçim yapabilirsin. Bir Amazon S3 depolama sınıfı seçerken şu iki faktörü göz önünde bulundur:

- Verine ne sıklıkla erişmeyi planlıyorsun?

- Verinin ne kadar erişilebilir (available) olması gerekiyor?

Amazon S3 storage sınıfları şu şekilde ayrılır:

### S3 Standard

- Sık erişilen veriler için tasarlanmıştır.

- Verileri en az üç farklı Availability Zone'da depolar.

Bu nedenle, web siteleri, içerik dağıtımı, veri analitiği gibi kullanım senaryoları için uygundur. Ancak, infrequently (seyrek erişilen) veya arşivlenmiş veriler için tasarlanmış diğer sınıflara göre daha pahalıdır.

### S3 Standard-Infrequent Access (S3 Standard-IA)

- Seyrek erişilen ancak gerektiğinde high availability gerektiren veriler için idealdir.

S3 Standard ile benzer yapıdadır, ancak:

- Depolama maliyeti daha düşüktür,

- Veriye erişim (retrieval) maliyeti daha yüksektir.

Veriler, tıpkı S3 Standard gibi en az üç Availability Zone Bölgesinde saklanır. High availability sağlar ama sık erişilmeyen (infrequently) yedekler, felaket kurtarma dosyaları gibi senaryolarda tercih edilir.

### S3 One Zone-Infrequent Access (S3 One Zone-IA)

Verileri tek bir Availability Zone (Erişilebilirlik Bölgesi) içinde depolar. Düz ınfrequent access'ten farkı, verilerin sadece 1 AZ'de tutulmasıdır. Yani yedekleme, felaket kurtarma gibi senaryoları azaltır ama beraberinde maliyeti de azaltır.

### S3 Intelligent-Tiering

Erişim şekli bilinmeyen veya zamanla değişen veriler için idealdir. Bu sınıfla beraber, Amazon S3, nesnelerin erişim desenlerini otomatik olarak izler:

Eğer bir nesneye 30 gün boyunca erişilmezse; Otomatik olarak S3 Standard-IA katmanına taşınır.

Eğer o nesneye tekrar erişilirse; S3 Standard katmanına taşınır.

Maliyet açısından, küçük bir aylık izleme ve otomasyon ücreti ödersin (nesne başına) ama bu ücret, veriyi yanlış sınıfta tutmanın maliyetinden genelde düşüktür.

Erişim sıklığını önceden tahmin edemediğin veriler varsa veya verilerin bazen sık, bazen seyrek kullanılıyorsa tercih edilebilir.

### S3 Glacier Instant Retrieval

- Hemen erişilmesi gereken arşiv verileri için uygundur. 

- Hem arşivlenecek hem de anında erişilmesi gereken veriler için idealdir.

- Verin sık kullanılmıyor, ama erişim gerektiğinde anında lazım diyorsan, tercih edilebilir.

- Nesneleri, milisaniyeler içinde, S3 Standard ile aynı performansla alabilirsiniz.

### S3 Glacier Flexible Retrieval

- Düşük maliyetli, arşiv odaklı bir depolama sınıfıdır.

- Veri arşivleme için tasarlanmıştır (eski müşteri kayıtları, yıllar öncesine ait fotoğraflar, videolar vb.).

- Depolama maliyeti çok düşüktür.

- Ancak veriye erişim anında değil, 1 dakika ile 12 saat arasında sürebilir.

Veriye sadece çok nadiren erişeceksen, ve geri alma (retrieval) süresi acil değilse, kullanılabilir.

### S3 Glacier Deep Archive

AWS’in sunduğu en düşük maliyetli nesne depolama sınıfıdır. Uzun vadeli arşivleme için idealdir.

- Yılda 1-2 kez erişilecek veriler için uygundur (örneğin yasal arşivler, eski kayıtlar).

- Veriyi 12 ila 48 saat içinde geri alabilirsin. Yani acil erişim gerektirmeyen veriler için tasarlanmıştır.

- Bu depolama sınıfındaki tüm nesneler, coğrafi olarak dağıtılmış en az üç farklı AZ'de çoğaltılarak (replicate) saklanır.

### S3 Outposts

Amazon S3 Outposts üzerinde S3 bucket’ları oluşturulur. AWS Outposts üzerinde veriyi geri almak (retrieve), depolamak ve erişmek daha kolay hale gelir.

Amazon S3 Outposts, object storage hizmetini on-premises AWS Outposts ortamına getirir. Amazon S3 Outposts, veriyi dayanıklı (durable) ve fazlalıklı (redundant) bir şekilde, Outposts üzerindeki birden fazla cihaz ve sunucu arasında depolamak için tasarlanmıştır. Bu hizmet, verinin yerel (local) olarak tutulması gereken, veri yerleşimi (data residency) zorunluluğu olan ve yüksek performans gerektiren iş yükleri için uygundur. Veriyi, on-premises uygulamalara yakın tutarak bu ihtiyaçları karşılar.

> *S3 ile EBS farkı, diğer farklar dışında temelde block storage ve object storage kullanmalarından gelir.*

>  Sık yazma/düzenleme varsa block tercih edilir çünkü verilerin sadece o bloğunu günceller.

>  Read-heavy / append-only / archive ise object tercih edilir çünkü tüm nesne yeniden yazılır. Bu da performans açısından dezavantaj sağlar.

-------------------------------------------------------------------------------------------------------------------------------

# Amazon Elastic File System (Amazon EFS)

> File Storage

Dosya depolamada (file storage), birden fazla istemci (kullanıcılar, uygulamalar, sunucular vb.) paylaşılan dosya klasörlerinde depolanan verilere erişebilir. Bu yaklaşımda, bir depolama sunucusu, dosyaları düzenlemek için yerel bir dosya sistemiyle birlikte blok depolamayı kullanır. İstemciler verilere dosya yolları aracılığıyla erişir.

Blok depolama ve nesne depolamayla karşılaştırıldığında, dosya depolama; çok sayıda hizmetin ve kaynağın aynı anda aynı veriye erişmesi gereken kullanım senaryoları için idealdir.

Amazon Elastic File System (Amazon EFS), AWS Cloud servisleri ve şirket içi kaynaklarla birlikte kullanılan ölçeklenebilir bir dosya sistemidir. Dosya ekledikçe veya sildikçe, Amazon EFS otomatik olarak büyür ya da küçülür (shrink). Uygulamaları kesintiye uğratmadan petabaytlara kadar isteğe bağlı olarak ölçeklenebilir.

File storage aslında en basit tabiriyle, blok depolamanın üzerine dosya sistemi eklenmiş halidir.

Altta yatan şey blok storage ama üstünde, ext4, NFS gibi bir dosya sistemi var gibi düşünebilirsiniz. Bu dosya sistemi sayesinde istemciler klasör, dosya yolu, izinler gibi yapılara erişebilir.

> Comparing Amazon EBS and Amazon EFS

Amazon EBS -> Bir Amazon EBS volume, verileri tek bir Availability Zone içinde depolar.

Bir Amazon EC2 instance’ını bir EBS volume’e bağlamak için, hem Amazon EC2 instance’ının hem de EBS volume’ün aynı Availability Zone içinde bulunması gerekir. Çünkü EBS ile EC2 instance'lar fiziksel olarak bağlı olmasalar bile birbiriyle "attached" haldedirler.

Amazon EFS -> Amazon EFS, bölgesel (regional) bir servistir. Verileri birden fazla Availability Zone içinde ve arasında depolar.

Bu çoğaltılmış depolama (duplicate storage), bir dosya sisteminin bulunduğu Region’daki tüm Availability Zone’lardan aynı anda veriye erişmeni sağlar. Ayrıca, şirket içi (on-premises) sunucular AWS Direct Connect kullanarak Amazon EFS’e erişebilir.

-------------------------------------------------------------------------------------------------------------------------------

# Amazon Relational Database Service (Amazon RDS)

> Relational databases

Relational bir database'de, veriler diğer veri parçalarıyla ilişkili olacak şekilde depolanır. İlişkisel bir veritabanına örnek olarak kahve dükkanının envanter yönetim sistemi verilebilir. Veritabanındaki her kayıt, ürün adı, boyutu, fiyatı gibi tek bir ürüne ait verileri içerir.

İlişkisel veritabanları, verileri depolamak ve sorgulamak için yapılandırılmış sorgu dili (SQL) kullanır. Bu yaklaşım, verilerin kolayca anlaşılabilir, tutarlı ve ölçeklenebilir bir şekilde depolanmasını sağlar. Örneğin, kahve dükkanı sahipleri, en sık tercih edilen içeceği orta boy latte olan tüm müşterileri bulmak için bir SQL sorgusu yazabilirler.

> Amazon Relational Database Service (Amazon RDS)

Amazon Relational Database Service (Amazon RDS), AWS Bulutu’nda ilişkisel veritabanları çalıştırmanı sağlayan bir hizmettir.

Amazon RDS, donanım sağlama, veritabanı kurulumu, yama uygulama ve yedekleme gibi görevleri otomatikleştiren yönetilen (managed) bir hizmettir. 

Bu yetenekler sayesinde, idari görevlerle daha az zaman harcar ve uygulamalarını geliştirmek için verileri kullanmaya daha fazla odaklanabilirsin. Amazon RDS’i, iş ve operasyon ihtiyaçlarını karşılamak için diğer servislerle entegre edebilirsin; örneğin, sunucusuz bir uygulamadan veritabanına sorgu göndermek için AWS Lambda ile birlikte kullanabilirsin.

Amazon RDS çeşitli güvenlik seçenekleri sunar. Birçok Amazon RDS veritabanı motoru, veriler depolanırken koruma sağlamak için rest halindeyken şifreleme (encryption at rest) ve veriler gönderilirken/alınırken koruma sağlamak için iletim sırasında şifreleme (encryption in transit) özellikleri sunar.

## Amazon RDS database engines

Amazon RDS, bellek, performans veya input/output (I/O) için optimize edilmiş altı veritabanı motorunda kullanılabilir. Desteklenen veritabanı motorları şunlardır:

- Amazon Aurora

- PostgreSQL

- MySQL

- MariaDB

- Oracle Database

- Microsoft SQL Server

### Amazon Aurora

Amazon Aurora, kurumsal düzeyde bir ilişkisel veritabanıdır. MySQL ve PostgreSQL ilişkisel veritabanlarıyla uyumludur. Standart MySQL veritabanlarından beş kata kadar, standart PostgreSQL veritabanlarından ise üç kata kadar daha hızlıdır.

Amazon Aurora, gereksiz giriş/çıkış (I/O) işlemlerini azaltarak veritabanı maliyetlerini düşürmeye yardımcı olur ve veritabanı kaynaklarının güvenilirliğini ve erişilebilirliğini korur.

İş yüklerin high availability gerektiriyorsa Amazon Aurora’yı değerlendirebilirsin. Verinin altı kopyasını üç farklı Availability Zone’da çoğaltır ve verilerini sürekli olarak Amazon S3’e yedekler.

-------------------------------------------------------------------------------------------------------------------------------

# Amazon DynamoDB

> Nonrelational databases

İlişkisel olmayan bir veritabanında, tablolar oluşturursun. Tablo, verileri depolayıp sorgulayabileceğin bir yerdir.

İlişkisel olmayan veritabanları bazen “NoSQL veritabanları” olarak adlandırılır çünkü verileri düzenlemek için satır ve sütunlar dışında yapılar kullanırlar. Nonrelational veritabanları için yapısal yaklaşımlardan biri anahtar-değer (key-value) çiftleridir. Anahtar-değer çiftlerinde, veriler öğeler (keys) olarak düzenlenir ve öğeler özelliklere (values) sahiptir.

Bir key-value veritabanında, tablodaki öğelere istediğin zaman özellik (attribute) ekleyebilir veya çıkarabilirsin. Ayrıca, tablodaki her öğenin aynı özelliklere sahip olması gerekmez.

*DynamoDB de tam bu şekilde nonrelational, key-value bir database servisidir. Her ölçekte milisaniyelik performans sağlar.*

DynamoDB serverless’tır, bu da sunucu sağlama (provision), yamalama veya yönetme işlemleri yapmana gerek olmadığı anlamına gelir. Ayrıca herhangi bir yazılım kurman, bakımını yapman veya işletmen de gerekmez.

Veritabanının boyutu küçüldükçe veya büyüdükçe, DynamoDB kapasitedeki değişikliklere uyum sağlamak için otomatik olarak ölçeklenir ve tutarlı performansı korur. Yani auto-scaling sağlar. Bu özelliği, yüksek performans gerektiren ve ölçeklenebilirliği önemli olan kullanım senaryoları için uygun bir seçenek haline getirir.

-------------------------------------------------------------------------------------------------------------------------------

# Amazon Redshift

Modern veritabanları, yüksek hızlı, gerçek zamanlı veri alımı ve sorgular için tasarlanmıştır. Ama geçmişe dayalı sorgularda aynı performansı veremezler. Örneğin, “Üretim, başladığımızdan beri nasıl gelişti?” gibi geçmişe dayalı (tarihsel) analiz sorularını yanıtlamak için kullanılan veriler, sürekli olarak üst üste birikir. Modern telemetri sistemleri ve IoT’nin patlamasıyla birlikte, veri hacmi, geleneksel (traditional) ilişkisel (relational) veritabanlarını bile ezip geçebilir hale gelmiştir.

Bununla beraber sadece veri hacmi değil, veri çeşitliliği de sorun olabilir. Envanter, finans ve perakende satış sistemleri gibi farklı veri kaynaklarından gelen verilerle işlem yapmak istediğin zaman, geleneksel veritabanları bu durumu kolayca kaldıramaz.

Veri, geleneksel ilişkisel veritabanlarının başa çıkamayacağı kadar karmaşık hale geldiğinde, artık veri ambarlarının (data warehouses) dünyasına girmiş oluyorsun. Veri ambarları, operasyonel analiz yerine tarihsel analiz için özel olarak tasarlanmıştır.

Ama şunu netleştirelim. “Tarihsel” veriden kasıt, örneğin: “Geçen saatin tüm mağazalardaki satış rakamlarını göster” olabilir. Buradaki kilit nokta: Bu veri artık sabit, geçmişte kaldı. O saatte daha fazla satış yapmıyoruz. "Şu anda envanterimizde kaç çuval kahve var?” sorusunun cevabı ise şu anda değişiklik gösteriyor olabilir. İş sorunun geçmişe yönelikse, o zaman veri ambarı bu tür iş zekâsı (BI) için doğru çözümdür.

Amazon Redshift, büyük veri (big data) analitiği için kullanabileceğin bir veri ambarı (data warehousing) servisidir. Birçok kaynaktan veri toplayabilme yeteneği sunar ve verilerin arasındaki ilişkileri ve eğilimleri (trends) anlamana yardımcı olur.

Redshiftin deyatlarına çok fazla girmeyeceğiz, tek anlamamız gereken; Büyük veri BI çözümlerine ihtiyacın olduğunda, Redshift ile sadece tek bir API çağrısıyla bunu halledebilirsin.

# AWS Database Migration Service (AWS DMS)

AWS Database Migration Service (AWS DMS), relational veritabanlarını, nonrelational veritabanlarını ve diğer veri depolarını taşımanı sağlar. AWS DMS ile, verileri bir kaynak veritabanından bir hedef veritabanına taşırsın. Kaynak ve hedef veritabanları aynı türde olabileceği gibi farklı türde de olabilir. Taşıma sırasında, kaynak veritabanın çalışmaya devam eder; bu sayede, veritabanına bağlı uygulamalar için kesinti süresi azalır.

Örneğin, yerel bir ortamda Amazon EC2 instance’ı üzerinde veya Amazon RDS içinde saklanan bir MySQL veritabanın olduğunu düşün. Bu MySQL veritabanı senin kaynak veritabanın olur. AWS DMS kullanarak, verilerini Amazon Aurora gibi bir hedef veritabanına taşıyabilirsin.

*Other use cases for AWS DMS:*

> Development and test database migrations

AWS DMS, canlı (production) veritabanındaki verileri kesinti olmadan hedef (test) veritabanına kopyalayarak geliştiricilerin gerçek veriye benzer ortamda test yapmasını sağlar; bu sayede canlı kullanıcılar etkilenmez, üretim sistemi zarar görmez ve geliştiriciler karmaşık veriyle güvenli şekilde çalışabilir.

> Database consolidation

AWS DMS, birden fazla veritabanını tek bir veritabanında birleştirmenize olanak tanır.

> Continuous replication

AWS DMS sadece bir kereye mahsus veri taşımak için değil, aynı zamanda "sürekli veri akışı" sağlayarak yedekleme benzeri ya da veriyi farklı bir bölgeye veya sisteme canlı olarak çoğaltabileceğin senaryolarda kullanılabilir.

## Additional Database Services

> Amazon DocumentDB

Amazon DocumentDB, MongoDB iş yüklerini destekleyen bir belge veritabanı (document database) servisidir. (MongoDB, bir belge tabanlı veritabanı programıdır.)

Özellikle içerik yönetimi, kullanıcı profilleri, blog sistemleri, ürün katalogları gibi veri yapısı kayıt bazında değişken olan yerlerde tercih edilir.

> Amazon Neptune

Amazon Neptune, bir graf veritabanı servisidir.

Amazon Neptune’u, yüksek düzeyde ilişkili veri kümeleriyle çalışan uygulamalar geliştirmek ve çalıştırmak için kullanabilirsin; örneğin öneri sistemleri, sahtekarlık (fraud) tespiti ve bilgi grafikleri (knowledge graphs) gibi senaryolarda tercih edilir.

> Amazon Quantum Ledger Database (Amazon QLDB)

Amazon Quantum Ledger Database (Amazon QLDB), bir defter (ledger) veritabanı servisidir.

Amazon QLDB’yi, uygulama verinde yapılan tüm değişikliklerin eksiksiz geçmişini incelemek için kullanabilirsin.

> Amazon Managed Blockchain

Amazon Managed Blockchain, açık kaynaklı framework’lerle blockchain ağları oluşturmak ve yönetmek için kullanabileceğin bir servistir. Blockchain, birden fazla tarafın merkezi bir otorite olmadan işlem yapmasına ve veri paylaşmasına olanak tanıyan dağıtık defter (distributed ledger) sistemidir.

> Amazon ElastiCache

Amazon ElastiCache, veritabanlarının üzerine önbellekleme (caching) katmanları ekleyerek sık yapılan sorguların okuma sürelerini iyileştirmeye yardımcı olan bir servistir.

> Amazon DynamoDB Accelerator (DAX)

Amazon DynamoDB Accelerator (DAX), DynamoDB için bellek içi (in-memory) bir önbellek sistemidir.

Yanıt sürelerini milisaniyeler seviyesinden mikrosaniyeler seviyesine düşürerek performansı artırmaya yardımcı olur.

















































