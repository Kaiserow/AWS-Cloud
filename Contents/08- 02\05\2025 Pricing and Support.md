# AWS Free Tier

AWS Free Tier, belirli hizmetleri belirli bir süre boyunca ücretsiz kullanmaya başlamanızı sağlar; böylece başlangıçta maliyet konusunda endişelenmenize gerek kalmaz. Üç tür ücretsiz teklif mevcuttur:

- Always Free (Her Zaman Ücretsiz): Süre sınırlaması olmadan, belirli kaynaklar sürekli ücretsizdir. Örneğin, AWS Lambda, ayda 1 milyon ücretsiz istek ve 3.2 milyon saniyeye kadar işlem süresi sunar veya Amazon DynamoDB, ayda 25 GB ücretsiz depolama alanı sağlar. 

- 12 Months Free (12 Ay Ücretsiz): AWS hesabınızı ilk oluşturduğunuz andan itibaren 12 ay boyunca geçerlidir. Örneğin, belirli miktarda Amazon S3 Standard depolama veya aylık olarak belirlenmiş saat sınırlarıyla Amazon EC2 işlem süresi.

- Trials (Deneme Süreçleri): Belirli hizmetler için sınırlı süreli ücretsiz deneme imkânı sunar (örneğin 30 gün). Mesela, Amazon Inspector, 90 günlük ücretsiz deneme sunar. Amazon Lightsail (sanal özel sunucular çalıştırmanızı sağlayan bir hizmet) ise 30 günlük süre içinde 750 saatlik ücretsiz kullanım sunar.


> How AWS pricing works?

AWS, kullandıkça öde (pay-as-you-go) modeliyle çeşitli bulut bilişim hizmetleri sunar. AWS fiyatlandırmasını daha iyi anlamak için aşağıdaki üç kategoriyi inceleyebilirsiniz:

1- Pay-as-you-go (Kullandıkça Öde): Yalnızca kullandığınız kaynaklar için, kullandığınız süre boyunca ödeme yaparsınız.

2- Save when you commit (Taahhütle Tasarruf Et): Belirli bir hizmeti belirli bir süre için (örneğin 1 yıl veya 3 yıl) kullanmayı taahhüt ederek indirimli fiyatlardan faydalanabilirsiniz.

3- Pay less by using more (Fazla Kullandıkça Daha Az Öde): Kullanım hacminiz arttıkça birim başına ödediğiniz fiyat azalır; bu da ölçekle birlikte tasarruf etmenizi sağlar.

## AWS Pricing Calculator

AWS Pricing Calculator, AWS hizmetlerini keşfetmenizi ve kullanım senaryolarınıza göre maliyet tahmini oluşturmanızı sağlar.

Tahminlerinizi, sizin tanımladığınız gruplara göre organize edebilirsiniz. Bu gruplar, örneğin şirketinizin maliyet merkezlerine göre düzenlenebilir. Bir tahmin oluşturduğunuzda, bunu kaydedebilir ve başkalarıyla paylaşmak için bir bağlantı oluşturabilirsiniz.

Diyelim ki şirketiniz Amazon EC2 kullanmak istiyor. Ancak henüz hangi AWS Region’ın ya da hangi instance türünün kullanım senaryonuz için en maliyet etkin seçenek olduğunu bilmiyorsunuz. AWS Pricing Calculator içinde;

- İhtiyacınız olan işletim sistemi türü,

- Bellek gereksinimleri,

- Input/Output (I/O) gereksinimleri gibi detayları girebilirsiniz. Bu sayede, AWS Pricing Calculator size farklı EC2 instance türlerini ve AWS Region’larını karşılaştırmalı olarak tahmini maliyetleriyle birlikte sunar.

## AWS pricing examples

### AWS Lambda Pricing

AWS Lambda için ücretlendirme, fonksiyonlarınıza yapılan istek sayısına ve bu fonksiyonların çalışma süresine göre yapılır.

### Amazon EC2 Pricing

Amazon EC2 ile, yalnızca instance'larınız çalışırken kullandığınız işlem süresi (compute time) için ödeme yaparsınız.

### Amazon S3 Pricing

Amazon S3 fiyatlandırması için aşağıdaki maliyet bileşenlerini göz önünde bulundurmak gerekir:

> Storage

Yalnızca kullandığınız depolama alanı için ödeme yaparsınız. Ücretlendirme; objelerin boyutlarına, kullandığınız depolama sınıfına ve her bir objeyi ay boyunca ne kadar süreyle sakladığınıza bağlıdır.

> Requests and Data Retrievals

Amazon S3 üzerindeki objelere ve bucket’lara yapılan istekler için ödeme yaparsınız. Örneğin, fotoğraf dosyalarını S3’e yükleyip bir web sitesinde barındırıyorsanız, site ziyaretçileri bu fotoğrafları her talep ettiğinde bu istekler ücretlendirilen istek sayısına eklenir.

> Data Transfer

Aynı AWS Region içindeki S3 bucket’ları arasında veya S3’ten diğer AWS hizmetlerine yapılan veri transferlerinde
ücret alınmaz. Ayrıca, S3'e dış internetten gelen veriler ücretsizdir, S3'ten Amazon CloudFront'a çıkan veri ücretsizdir ve S3'ten aynı Region’daki EC2 instance’a çıkan veri de ücretsizdir. Bunlar dışındaki veri input/output işlemleri için ücret alınır.

> Management and Replication

Amazon S3 bucket’larınızda etkinleştirdiğiniz yönetim özellikleri için ödeme yaparsınız. Bunlar şunları içerir:

- Amazon S3 inventory, Analytics, Object tagging gibi özellikler.

### AWS Billing Dashboard

AWS Billing & Cost Management dashboard'u kullanarak, AWS faturalarınızı ödeyebilir, kullanımınızı izleyebilir, maliyetlerinizi analiz edip kontrol edebilirsiniz.

## Consolidated Billing

Önceki bir modülde, birden fazla AWS hesabını merkezi bir yerden yönetmenizi sağlayan AWS Organizations hizmetini öğrenmiştiniz.
AWS Organizations, ayrıca consolidated billing (birleştirilmiş faturalama) seçeneğini de sunar. Consolidated billing sayesinde, organizasyonunuzdaki tüm AWS hesapları için tek bir fatura alırsınız. Bu sayede, bağlı tüm hesapların birleşik maliyetlerini kolayca takip edebilirsiniz. Ayrıca, aylık faturanızda, her bir hesabın oluşturduğu masrafları ayrıntılı olarak inceleyebilirsiniz.
Bu da hem şeffaflık sağlar, hem de tek fatura alma kolaylığını korur.

Consolidated billing'in bir diğer avantajı da; toplu indirim fiyatları, savings plans, Reserved Instances gibi avantajların organizasyondaki tüm hesaplar arasında paylaşılabilmesidir. Örneğin, tek bir hesap kendi başına indirim almaya yetecek kadar kullanım yapmasa da, birden fazla hesabın toplam kullanımı, bu indirimin tüm organizasyona uygulanmasına olanak tanır.

## AWS Budgets

AWS Budgets hizmetiyle, hizmet kullanımı, hizmet maliyetleri ve instance rezervasyonları için bütçeler oluşturabilirsiniz. 

AWS Budgets içerisindeki bilgiler günde üç kez güncellenir. Bu sayede, kullanımınızın belirlediğiniz bütçe sınırlarına veya AWS Free Tier limitlerine ne kadar yaklaştığını doğru bir şekilde takip edebilirsiniz.

Ayrıca, AWS Budgets ile özel uyarılar ayarlayabilirsiniz. Böylece kullanımınız: Bütçeyi aştığında, Veya aşması öngörüldüğünde
otomatik bildirim alabilirsiniz.

## AWS Cost Explorer

AWS Cost Explorer, AWS maliyetlerinizi ve kullanımınızı zaman içinde görselleştirmenize, anlamanıza ve yönetmenize olanak tanıyan bir araçtır. Cost Explorer, varsayılan olarak en fazla maliyet oluşturan ilk beş AWS hizmetine ait maliyet ve kullanım raporunu içerir.

## AWS Support

AWS, sorunları gidermenize, maliyetleri düşürmenize ve AWS hizmetlerini verimli kullanmanıza yardımcı olmak için farklı destek planları sunar:

- Basic

- Developer

- Business

- Enterprise On-Ramp

- Enterprise


> Basic Support 

Basic Support, tüm AWS müşterileri için ücretsizdir.

> Developer, Business, Enterprise On-Ramp ve Enterprise Support

Basic Support’un tüm avantajlarını içerir. Bunlara ek olarak, sınırsız sayıda teknik destek talebi oluşturma hakkı da sunarlar. Bu planlar, Aylık ödeme modeliyle fiyatlandırılır ve Uzun vadeli bir sözleşme gerektirmez.

### Technical Account Manager (TAM)

Enterprise On-Ramp ve Enterprise Support planları, bir Technical Account Manager (TAM) erişimi içerir.

TAM, AWS üzerindeki birincil iletişim noktanızdır.
Şirketiniz Enterprise Support veya Enterprise On-Ramp aboneliğine sahipse, TAM’iniz size AWS hizmetlerinin tamamında bulut yolculuğunuz boyunca rehberlik eder, sizi bilgilendirir, destekler ve süreci ilerletir. TAM'ler:

- Mühendislik konularında uzman rehberlik sağlar

- AWS hizmetlerini verimli şekilde entegre eden çözümler tasarlamanıza yardımcı olur

- Maliyet etkin ve dayanıklı mimariler oluşturmanızda destek olur

- AWS programlarına ve geniş bir uzman topluluğuna doğrudan erişim sunar

## AWS Marketplace

AWS Marketplace, bağımsız yazılım satıcılarına ait binlerce yazılım listesinin bulunduğu dijital bir katalogdur. AWS üzerinde çalışan yazılımları bulmak, test etmek ve satın almak için AWS Marketplace'i kullanabilirsiniz.

Ayrıca yazılım çözümlerini, sektöre ve kullanım senaryosuna göre inceleyebilirsiniz.
Örneğin, şirketinizin sağlık sektöründe faaliyet gösterdiğini varsayalım.

AWS Marketplace’te; Hasta kayıtlarını korumaya yönelik çözümler ya da Makine öğrenmesiyle hastanın tıbbi geçmişini analiz edip sağlık risklerini tahmin etme gibi kullanım senaryolarını inceleyebilirsiniz.

AWS Marketplace, yazılım ürünlerini şu gibi çeşitli kategorilerde sunar:

- Infrastructure Software

- DevOps

- Data Products

- Professional Services

- Business Applications

- Machine Learning

- Industries

- Internet of Things (IoT)



