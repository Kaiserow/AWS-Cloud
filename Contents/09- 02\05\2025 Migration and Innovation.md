# AWS Cloud Adoption Framework (AWS CAF)

AWS Cloud Adoption Framework (AWS CAF), bir organizasyonun bulut bilişime geçiş sürecini planlamasına, yönetmesine ve optimize etmesine yardımcı olan bir rehberdir.

En üst düzeyde, AWS Cloud Adoption Framework (CAF) rehberliği altı odak alanına (perspective) ayırır.

Her bir perspektif, organizasyondaki farklı sorumluluk alanlarını ele alır.
Planlama süreci, organizasyondaki doğru kişilerin, yaklaşan değişimlere hazırlıklı olmasını sağlar. Genel olarak:

Business, People ve Governance perspektifleri → İş odaklı yeteneklere yöneliktir

Platform, Security ve Operations perspektifleri → Teknik yeteneklere odaklanır

> Business Perspective

Business Perspective, BT'nin (IT) iş ihtiyaçlarıyla uyumlu olmasını ve BT yatırımlarının temel iş sonuçlarıyla bağlantılı olmasını sağlar.

Bu perspektifi kullanarak:

- Bulut benimseme (cloud adoption) için güçlü bir iş gerekçesi oluşturabilir,

- Bulut girişimlerini önceliklendirebilir,

- İş stratejilerinizin ve hedeflerinizin, BT strateji ve hedeflerinizle uyumlu olduğundan emin olabilirsiniz.

Business Perspective kapsamındaki yaygın roller:

- İş yöneticileri (Business managers)

- Finans yöneticileri (Finance managers)

- Bütçe sahipleri (Budget owners)

- Strateji paydaşları (Strategy stakeholders)

> People Perspective

People Perspective, başarılı bir cloud adoption süreci için kurum genelinde bir değişim yönetimi stratejisinin geliştirilmesini destekler.

Bu perspektifi kullanarak:

- Organizasyonel yapıları ve rolleri değerlendirebilir,

- Gerekli yeni becerileri ve süreç ihtiyaçlarını belirleyebilir,

- Mevcut eksiklikleri tespit ederek eğitim, işe alım ve organizasyonel değişikliklerin önceliklendirilmesini sağlayabilirsiniz.

People Perspective kapsamındaki yaygın roller:

İnsan kaynakları (Human resources)

İşe alım uzmanları (Staffing)

İnsan yönetimi sorumluları (People managers)

> Governance Perspective

Governance Perspective, BT stratejisini iş stratejisiyle uyumlu hale getirecek beceri ve süreçlere odaklanır.
Bu sayede iş değeri en üst düzeye çıkarılırken riskler en aza indirilmiş olur.

Bu perspektifi kullanarak:

Bulutta iş yönetişimini (governance) sağlamak için personel becerileri ve süreçlerin nasıl güncellenmesi gerektiğini anlayabilirsiniz.

Bulut yatırımlarını yönetebilir ve ölçerek, iş sonuçlarını değerlendirebilirsiniz.

Governance Perspective kapsamındaki yaygın roller:

- Bilgi Teknolojileri Yöneticisi (Chief Information Officer – CIO)

- Program yöneticileri (Program managers)

- Kurumsal mimarlar (Enterprise architects)

- İş analistleri (Business analysts)

- Portföy yöneticileri (Portfolio managers)

> Platform Perspective

Platform Perspective, bulutta yeni çözümler geliştirmenin ve mevcut on-premises iş yüklerini buluta taşımanın temel ilkelerini ve kalıplarını içerir.

Bu perspektifi kullanarak:

- Farklı mimari modelleri kullanabilir,

- BT sistemlerinin yapısını ve bileşenler arasındaki ilişkileri anlayıp açıklayabilirsiniz,

- Hedeflenen bulut ortamının mimarisini detaylı bir şekilde tanımlayabilirsiniz.

Platform Perspective kapsamındaki yaygın roller:

- Teknoloji Direktörü (Chief Technology Officer – CTO)

- BT yöneticileri (IT managers)

- Çözüm mimarları (Solutions architects)

> Security Perspective

Security Perspective, bir organizasyonun güvenlik hedeflerini — görünürlük, denetlenebilirlik, kontrol ve çeviklik (agility) — karşılamasını sağlar.

Bu perspektifi kullanarak:

- Organizasyonun ihtiyaçlarına uygun güvenlik kontrollerinin seçimini ve uygulanmasını AWS CAF yapısına göre planlayabilirsiniz.

Security Perspective kapsamındaki yaygın roller:

- Bilgi Güvenliği Yöneticisi (Chief Information Security Officer – CISO)

- BT güvenlik yöneticileri (IT security managers)

- BT güvenlik analistleri (IT security analysts)

> Operations Perspective

Operations Perspective, BT iş yüklerini işletme, kullanma, çalıştırma ve gerektiğinde kurtarma süreçlerini, iş paydaşlarınızla üzerinde anlaşılan seviyede gerçekleştirmenizi sağlar.

Bu perspektifi kullanarak:

- Günlük, çeyreklik ve yıllık iş süreçlerinin nasıl yürütüleceğini tanımlayabilir,

- Bulut geçişi sürecinde mevcut operasyonel prosedürleri belirleyebilir,

- Gereken süreç değişikliklerini ve eğitim ihtiyaçlarını tespit ederek bulut benimsemesini başarıyla uygulayabilirsiniz.

Operations Perspective kapsamındaki yaygın roller:

- BT operasyon yöneticileri (IT operations managers)

- BT destek yöneticileri (IT support managers)

-------------------------------------------------------------------------------------------------------------------------------
# 6 strategies for migration

Uygulamaları cloud ortamına taşırken uygulanabilecek en yaygın altı migration stratejisi şunlardır:

- Rehosting

- Replatforming

- Refactoring / Re-architecting

- Repurchasing

- Retaining

- Retiring

## Rehosting

Rehosting, yani yaygın bilinen adıyla "lift-and-shift", uygulamaların herhangi bir değişiklik yapılmadan cloud ortamına taşınmasını ifade eder. 

Büyük çaplı bir legacy migration senaryosunda, şirket hızlı şekilde ölçeklenmek ve iş gerekçesini karşılamak istiyorsa, uygulamaların büyük kısmı rehost edilir.

## Replatforming

Replatforming, yani diğer adıyla "lift, tinker, and shift", uygulamayı cloud ortamına taşımadan önce birkaç küçük iyileştirme (optimization) yapmayı içerir. 

Bu iyileştirmeler, uygulamanın temel mimarisi **değiştirilmeden** gerçekleştirilir ve genellikle somut faydalar (örneğin maliyet tasarrufu, performans artışı) sağlamak amacıyla yapılır.

## Refactoring/re-architecting

Refactoring (diğer adıyla re-architecting), bir uygulamanın mimarisinin ve geliştirme yönteminin, cloud-native özellikler kullanılarak yeniden tasarlanması sürecidir.

Refactoring, genellikle uygulamaya yeni özellikler ekleme, ölçeklenebilirlik veya performans gibi konularda güçlü bir iş ihtiyacı olduğunda tercih edilir — bu ihtiyaçlar, mevcut ortamda karşılanması zor olan gereksinimlerdir.

## Repurchasing

Repurchasing, geleneksel lisanslı bir yazılımdan software-as-a-service (SaaS) modeline geçişi ifade eder.

Örneğin, bir işletme bu stratejiyi uygulayarak mevcut customer relationship management (CRM) sisteminden Salesforce.com gibi bir SaaS çözümüne migrate etmeyi tercih edebilir.

## Retaining (tutma, muhafaza etme manasında)

Retaining, iş açısından kritik olan bazı uygulamaların kaynak ortamda tutulmasını ifade eder. 

Bu durum genellikle, cloud ortamına migrate edilmeden önce büyük ölçüde refactoring gerektiren uygulamaları veya daha sonraya ertelenebilecek işleri kapsar.

## Retiring (emekli etmek manasında)

Retiring, artık ihtiyaç duyulmayan uygulamaların kaldırılması (devre dışı bırakılması) sürecidir.

-------------------------------------------------------------------------------------------------------------------------------

# AWS Snow Family 

AWS Snow Family, exabyte seviyesine kadar veriyi fiziksel olarak AWS ortamına taşıma veya dışa aktarma sürecinde kullanılan fiziksel cihazlardan oluşan bir koleksiyondur.

AWS Snow Family şu üç üyeden oluşur:

- AWS Snowcone

- AWS Snowball

- AWS Snowmobile


Bu cihazlar farklı kapasite seçenekleri sunar ve çoğu, yerleşik compute yeteneklerine sahiptir. AWS, Snow Family cihazlarının sahipliğini ve yönetimini üstlenir ve bu cihazlar, AWS security, monitoring, storage management ve computing yetenekleriyle entegre şekilde çalışır.

## AWS Snowcone

AWS Snowcone, küçük, dayanıklı ve güvenli bir edge computing ve data transfer cihazıdır. Bu cihazda:

- 2 CPU,

- 4 GB bellek,

- ve 14 TB'a kadar kullanılabilir storage bulunur.

## AWS Snowball

AWS Snowball, iki farklı cihaz türü sunar:

> Snowball Edge Storage Optimized

Bu cihazlar, büyük ölçekli veri migration, tekrarlayan transfer işlemleri ve yüksek kapasiteli local compute ihtiyaçları için uygundur.

Storage -> Block volume ve Amazon S3 uyumlu nesne depolama için 80 TB sabit disk sürücüsü (HDD) kapasitesi ve block volume için 1 TB SATA katı hal sürücüsü (SSD).

Compute -> 104 vCPU, 416 GiB bellek ve isteğe bağlı NVIDIA Tesla V100 GPU. Cihazlar, C5, M5a, G3 ve P3 örneklerine eşdeğer olan Amazon EC2 sbe-c ve sbe-g örneklerini çalıştırır.

> Snowball Edge Compute Optimized

Snowball Edge Compute Optimized, machine learning, full motion video analysis, analytics ve local computing stacks gibi kullanım senaryoları için güçlü computing kaynakları sağlar.

Storage -> Storage: Amazon S3 compatible object storage veya Amazon EBS compatible block volumes için 80 TB kullanılabilir HDD kapasitesi ve Amazon EBS compatible block volumes için 28 TB kullanılabilir NVMe SSD kapasitesi.

Compute -> 104 vCPU, 416 GiB memory ve isteğe bağlı NVIDIA Tesla V100 GPU.
Cihazlar, C5, M5a, G3 ve P3 instances ile eşdeğer olan Amazon EC2 sbe-c ve sbe-g instances çalıştırır.

## AWS Snowmobile

AWS Snowmobile, büyük miktarda veriyi AWS'ye taşımak için kullanılan exabyte-scale data transfer service’dir.

Her bir Snowmobile ile 100 petabyte'a kadar veri transfer edebilirsiniz. Snowmobile, 45 feet uzunluğunda, dayanıklı bir shipping container olup, bir semi trailer truck tarafından çekilir.

#### NOT: Snow Family'nin her bir üyesi, veriyi fiziksel olarak taşımak için kullanılır. 

### Innovate with AWS Services

AWS servislerini nasıl kullanacağınızı incelerken, ulaşmak istediğiniz sonuçlara odaklanmak önemlidir.
Cloud ortamında yeniliği (innovation) sağlıklı bir şekilde yönlendirebilmek için aşağıdaki durumları açıkça ifade edebiliyor olmanız gerekir:

Mevcut durum

Ulaşılmak istenen durum

Çözmek istediğiniz problemler

> AWS ile nasıl inovasyon yapılacağı hakkında:

#### Serverless applications

AWS'de serverless, sunucuları sağlamanızı, bakımını yapmanızı veya yönetmenizi gerektirmeyen uygulamaları ifade eder.
Fault tolerance veya availability konularını düşünmenize gerek yoktur — AWS bu yetenekleri sizin yerinize sağlar.

AWS Lambda, serverless applications çalıştırmak için kullanabileceğiniz bir servise örnektir.
Mimarinizi, kodunuzu çalıştırmak için Lambda functions tetiklenecek şekilde tasarlarsanız, bir sunucu filosunu yönetme ihtiyacını tamamen ortadan kaldırabilirsiniz.

Serverless applications ile mimari kurmak, geliştiricilerin sunucu yönetmek yerine asıl ürüne odaklanmasını sağlar.


#### Artificial intelligence

AWS, artificial intelligence (AI) destekli çeşitli hizmetler sunar.

Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:

- Amazon Transcribe ile konuşmayı metne dönüştürmek

- Amazon Comprehend ile metinlerdeki kalıpları keşfetmek

- Amazon Fraud Detector ile potansiyel olarak sahte çevrimiçi aktiviteleri tespit etmek

- Amazon Lex ile sesli ve yazılı chatbot'lar oluşturmak

#### Machine learning

Geleneksel machine learning (ML) geliştirme süreci karmaşık, maliyetli, zaman alıcı ve hata yapmaya açık bir süreçtir.
AWS, bu zorlukları ortadan kaldırmak ve ML modellerini hızlı bir şekilde oluşturmanızı, eğitmenizi ve dağıtmanızı sağlamak için Amazon SageMaker hizmetini sunar.

ML kullanarak verileri analiz edebilir, karmaşık problemleri çözebilir ve olaylar gerçekleşmeden önce sonuçları tahmin edebilirsiniz.

##### Amazon Q Developer

Amazon Q Developer, machine learning destekli bir code generator’dır ve gerçek zamanlı olarak kod önerileri sunar.

IDE (Integrated Development Environment) içinde kod yazarken, Kodunuzu ve yazdığınız yorum satırlarını analiz eder, Mevcut koda ve yorumlara göre otomatik olarak kod önerileri üretir.

*Sonuç olarak AWS, size sadece altyapı sunmaz; aynı zamanda daha az uğraşla daha hızlı yenilik yapabilmeniz için araçlar sunar ve inovasyonu kolaylaştırır.*
