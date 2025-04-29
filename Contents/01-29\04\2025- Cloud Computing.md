# What is a client-server model?

Bilgisayarda, bir client bir kişinin bilgisayar serverlarına isteklerde bulunmak için etkileşimde bulunduğu bir web tarayıcısı veya masaüstü uygulaması olabilir. Bir server, Amazon Elastic Compute Cloud (Amazon EC2) gibi bir tür sanal sunucu gibi hizmetler olabilir. Kısaca client, serverdan bir hizmet talep eder ve sunucu da bu hizmeti sunar/sağlar.

# Cloud Computing

Cloud computing, "pay-as-you-go" (kullandığın kadar ödeme yapmak) ile "on-demand delivery of IT resources" (IT kaynaklarının, talebe göre teslimi) olarak özetlenebilir. On-demand delivery, AWS'nin ihtiyaç duyduğunuz kaynaklara ihtiyaç duyduğunuzda sahip olmanız anlamına gelir. Örneğin, anlık olarak 300 virtual servera ihtiyaç duyarsanız, kolay bir şekilde elde edebilirsiniz. Aynı şekilde, artık 300 sanal sunucuya ihtiyacınız yoksa, iptal de edebilirsiniz. Fakat kendi data centerlarınızı yönetirken bunu yapmanız mümkün olmayacaktır.

Çok sayıda AWS IT kaynağı vardır çünkü bu diğer işletmelerden sizi farklı kılar. Birçok işletmede ortak olan IT kaynakları sizi diğerlerinden farklı kılmayacaktır. Örneğin, MySQL motoru kurmak veya backup almak herkesin yapabileceği birşeydir, bu da sizi farklı yapmaz. Fakat MySQL'in içindeki veriler ve o veritabanının nasıl kurulup, nasıl yönetildiği sizi özel yapar.

AWS bu tür sıradan işleri "undifferentiated heavy lifting" diye adlandırır. Bunlar, herkesin yapmak zorunda olduğu ama seni diğerlerinden farklılaştırmayan ağır işlerdir. (Sunucu kurmak, motor yüklemek, bakım yapmak vs.) 

AWS de bu ağır işleri kendilerine bırakılmasını ve işletmelerin, rekabetlerinde kendilerini özel kılan şeylere odaklanmasını amaçlar. 

AWS hizmetlerine, web tarayıcından (AWS Console) veya programlama ile (API'lar kullanarak) kolayca ve güvenli bir şekilde erişilebilir. Ek olarak AWS bunu; satıcıyla konuşma olmadan, ekstra kontrata ihtiyaç duymadan ve kullandığın kadar ödemeni sağlayarak sunar.

AWS'in bu esnekliği kahve dükkanı analojisi ile açıklanabilir. Kahve dükkanında sabah kalabalık olduğunda fazla personel çalıştırılırken, gece müşteri olmadığında fazladan personele gerek kalmaz. Aynı mantıkla, mesela hafta sonu kimse çalışmıyorsa  geliştirme sunucularını kapatırsın. Böylece ihtiyacın olmadığı zaman için de ayrıca para ödemezsin.

## Deployment models for cloud computing

Bir bulut stratejisi seçerken, bir şirket gerekli bulut uygulama bileşenleri, tercih edilen kaynak yönetimi araçları ve eski IT altyapısı gereksinimleri gibi faktörleri göz önünde bulundurmalıdır. 3 farklı cloud deployment modeli vardır:

### Cloud-Based Deployment (Public Cloud)

• Uygulamanın tüm bölümleri bulutta çalışır.

• Mevcut uygulamalar buluta taşınır.

• Yeni uygulamaların tasarlanması ve oluşturulması artık bulutta gerçekleşir.

O uygulamalar, sistem yönetimi gibi işleri senin IT ekibinin yapması gereken düşük seviyeli altyapılar üzerinde kurulabilir.

Ama istersen, aynı uygulamaları daha yüksek seviyeli (managed) servislerle de kurabilirsin — böylece sistem kurma, ayarlama, ölçekleme gibi işlerle daha az uğraşırsın. Yani istersen her şeyi sen yönetirsin, ya da istersen işin yükünü azaltan hazır servisleri de kullanabilirsin. Örneğin, bir şirket tamamen bulut tabanlı sanal sunucular, veritabanları ve ağ bileşenlerinden oluşan bir uygulama oluşturabilir.

## On-Premises Deployment (Private Cloud)

Kısaca, kaynakların (sunucular, depolama, ağ vs.) kendi fiziksel binandaki veri merkezinde çalıştığı sistem ama daha modern hali diyebiliriz. Örneğin, VMware gibi sanallaştırma sağlayan araçlarla kendi sunucularının üstünde birden fazla sanal sunucu çalıştırabilirsin. Bu sanallaştırma sayesinde, kaynakları (CPU, RAM vs.) daha verimli kullanırsın. Eskisi gibi her uygulama/servis için ayrı fiziksel sunucu kullanmak yerine tek sunucuda çok iş yaparsın. Uygulamalarının hepsi senin on-premises data center’ında (yani kendi veri merkezinde) barınır. 

Sonuç olarak, "kendi altyapın, kendi kontrolün" diyebiliriz. Bu noktada AWS gibi cloud hizmetleri sağlayan şirketlerin bir rolü yoktur. 

#### NOT: Akıllara şöyle bir soru gelebilir; "madem on-premises ya da diğer adıyla private cloud uygulamalarında AWS gibi bulut sağlayıcılarının işi yok, o zaman neden cloud kavramı kullanılıyor?" Tam bu noktada bir kafa karışıklığını giderelim. Cloud kavramı, sadece "internette bir yerde olan" anlamına gelmez. Cloud; esneklik, self-service, kaynak havuzu, ölçeklenebilirlik sağlar. Private cloud kavramı da bu özellikleri içerdiği için cloud gibi çalışır ama sadece senin şirketinin kullandığı, dışarıya kapalı bir sistemdir. Public cloud'da ise başkalarının da kullandığı altyapıyı, ortak olarak paylaşırsınız.

> ⚡ Biraz genel kültür ama "Cloud" kavramının anlamı için önemli:

> Cloud yani bulut kelimesinin nereden geldiğine bakacak olursak; 1990'larda network diyagramlarında interneti veya dış ağları göstermek için bulut sembolü kullanılmaya başlandı. Şemalarda karmaşık internet alt yapısı yerine sadece bulut resmi çiziliyordu. Sonra insanlar şunu fark etti: "E biz artık altyapıyı tamamen soyutluyoruz, kullanıcı sadece hizmeti görüyor... O zaman buna da 'bulut/cloud' diyelim." 

> Tabi günümüzde cloud bundan da fazlası olduğu için sadece altyapının soyutlanması için değil, esneklik, self-service, kaynak havuzu, ölçeklenebilirlik gibi kavramlar için de kullanılıyor. Bu yüzden de yukarıda bahsettiğimiz üzere, on-premises uygulamaları için de private "cloud" diyebiliyoruz.

### Hybrid Deployment

Cloud tabanlı kaynakları (mesela AWS servisleri), kendi şirketinin fiziksel sunucularıyla (on-premises) bağlarsın ve birlikte kullanırsın. Yani aslında kendi altyapın ile bulut hizmetleri alıyorsun.

Bir noktada, cloud-based kaynakları (AWS Lambda, RDS vs.) kullanmanız gerekebilir. Ama aynı zamanda eski (legacy) uygulamaların var ve bunlar şirket binandaki sunucularda durmaya devam etmeli çünkü bazı regülasyonlar veya güvenlik kuralları sana "bu verileri kendi sunucunda tutacaksın" diyor. (özellikle sağlık, finans gibi sektörlerde). Hybrid Deployment tam olarak bu sorunu ortadan kaldırmaya yönelik uygulanıyor: Eski sistemleri on-premises çalıştırmaya devam ediyorsun, yeni ihtiyaçları ise cloud üzerinden karşılıyorsun ve ikisi birbirine bağlı bir şekilde çalışıyor. 

Örneğin, bir şirketiniz var ve muhasebe programı 2005 yılında yazılmış, çok eski ama sizin sunucunuzda durmalı. Fakat siz bir yandan da yeni veri analizi yapmak istiyorsunuz. Bu yüzden de AWS Big Data servislerini kullanacaksınız. Bu noktada hybrid kurulum yaparak, muhasebe programınızı on-premises bırakıyorsunuz. Analytics ise cloud'da çalışıyor ve ikisi arasındaki bağlantıyı VPN gibi araçlarla kuruyorsunuz.

## Benefits of cloud computing

> Trade upfront expense for variable expense

Upfront expense yani ön harcama, bir hizmet sunmadan o hizmet için yatırım yapmaya denir. Örneğin müşteriye herhangi bir sunucu hizmeti sunmadan önce bir sunucu almanız yani yatırım yapmanız gerekiyorsa, bu bir ön harcamadır. Variable expense yani değişken harcama ise nasıl kullanacağınızı bilmeden önce yatırım yapmak yerine yalnızca tükettiğiniz IT kaynakları kadar ödeme yapmanız anlamına gelir.

Bu sistem, şirketlerin daha az maliyet ile yenilikçi yaklaşımlar uygulamasına olanak tanır.

> Stop spending money to run and maintain data centers

Data center'ları kurmak, yönetmek ve bakımını sağlamak, hem maddi hem de zaman açısından maliyetli olabilir. Cloud computing, maddi maliyetleri azaltmanın yanında iş yükünü de hafifletir.

> Stop guessing capacity

Cloud computing, bir uygulamayı uygularken altyapının yetip-yetmeyeceği konusunda tahmin yürütme zahmetini ortadan kaldırır.

Örneğin, ihtiyaç duyduğunuzda Amazon EC2'yi başlatabilir ve yalnızca kullandığınız işlem süresi için ödeme yapabilirsiniz. Kullanılmayan kaynaklar için ödeme yapmak veya sınırlı kapasiteyle uğraşmak yerine, yalnızca ihtiyacınız olan kapasiteye erişebilirsiniz. Ayrıca talebe yanıt olarak ölçeklendirebilirsiniz.

> Benefit from massive economies of scale

Cloud kullanmak, kendi kendinize kuracağınız sunuculara göre daha ucuza gelir. Çünkü AWS gibi dev sağlayıcılar, milyonlarca müşteriye hizmet verir. Bu kadar fazla müşteri olması demek; donanım, enerji, bakım gibi masrafların çok büyük oranda bölünmesi demektir. Mesela milyon tane işlemciyi toptan alıyorlar bu yüzden de maliyetleri çok daha düşük oluyor. Ve sonuç olarak, sağladıkları bu ekonomi avantajını (economies of scale) kullanıcılara düşük fiyat olarak yansıtıyorlar.

#### NOT: Economies of Scale (Ölçek Ekonomisi) kısaca şu anlama gelir: Ne kadar fazla üretirsen veya toplu alırsan, birim başına maliyet o kadar düşer.

Yani economy of scale, daha düşük pay-as-you-go maliyetleri sunar.

> Increase speed and agility

Cloud computing'in esnekliği, uygulamaların daha kolay geliştirilmesini ve uygulanmasını sağlar. Bu esneklik size deneyimleyip yenilik yapmak için daha fazla zaman sağlar. Veri merkezlerinde hesaplama yaparken, ihtiyaç duyduğunuz yeni kaynakları elde etmek haftalar alabilir. Buna karşılık, bulut bilişim dakikalar içinde yeni kaynaklara erişmenizi sağlar. Çünkü bulut sağlayıcılarının sistemleri hep aktif ve ihtiyaç duyduğunuzda kullanımınıza hazır olarak bekliyor.

> Go global in minutes

AWS Cloud'un global footprint'i (AWS'in dünyanın her tarafına yayılmış veri merkezleri, sunucular, altyapılar ağı) düşük latency ile uygulamaları dünyanın dört bir yanındaki müşterilere hızla dağıtmanızı sağlar. Bu, müşterilerinize göre dünyanın farklı bir yerinde olsanız bile, müşterilerin uygulamalarınıza minimum latency ile erişebileceği anlamına gelir. 















