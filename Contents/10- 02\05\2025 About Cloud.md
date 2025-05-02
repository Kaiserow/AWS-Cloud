# The AWS Well-Architected Framework

AWS Cloud üzerinde güvenilir (reliable), güvenli (secure), verimli (efficient) ve maliyet açısından etkili (cost-effective) sistemler tasarlayıp işletmenize yardımcı olur. Mimarinizi, best practices (en iyi uygulamalar) ve design principles (tasarım ilkeleri) doğrultusunda tutarlı bir şekilde değerlendirme ve iyileştirme alanlarını belirleme imkânı sunar.

The Well-Architected Framework 6 temel üzerine kuruludur:

- Operational excellence ⚙️

- Security 🔐

- Reliability 🔁

- Performance efficiency 🚀

- Cost optimization 💰

- Sustainability 🌱 (sürdürülebilirlik)

## Operational excellence

Operational excellence, sistemleri çalıştırma ve izleme becerisiyle iş değerini sağlamak ve bu süreçte destekleyici süreçleri ve prosedürleri sürekli olarak geliştirmektir. 

Cloud ortamında operational excellence için design principles (tasarım ilkeleri) şunları içerir:

- Operations as code (işlemleri kod olarak gerçekleştirme)

- Annotating documentation (dokümantasyonu açıklamalarla zenginleştirme)

- Anticipating failure (hataları önceden öngörme)

- Making small, reversible changes frequently (sık sık küçük ve geri alınabilir değişiklikler yapma)

## Security

Security pillar’ı, iş değeri sunarken bilgi, sistem ve varlıkları risk değerlendirmeleri ve önleme stratejileri (risk assessments and mitigation strategies) aracılığıyla koruma yeteneğidir.

Mimarinizin security durumunu değerlendirirken şu best practices (en iyi uygulamaları) göz önünde bulundurun:

- Mümkün olduğunda security best practices (güvenlik en iyi uygulamaları) otomatikleştirin

- Security at all layers (tüm katmanlarda güvenlik) uygulayın

- Protect data in transit and at rest (veriyi aktarım sırasında ve depolandığında koruyun)

## Reliability (Güvenirlik/Süreklilik)

Reliability, bir sistemin aşağıdaki yeteneklere sahip olmasıdır:

- Recover from infrastructure or service disruptions

- talebi karşılamak için dinamik olarak computing resources elde etme.

- yanlış yapılandırmalar veya geçici ağ problemleri gibi kesintileri azaltma

Reliability, şu unsurları da içerir:

- Testing recovery procedures (kurtarma prosedürlerini test etme)

- Scaling horizontally to increase aggregate system availability (toplam sistem kullanılabilirliğini artırmak için yatay ölçekleme yapma)

- Automatically recovering from failure (hatalardan otomatik kurtarma)

## Performance Efficiency

Performance efficiency, sistem gereksinimlerini karşılamak için computing resources (hesaplama kaynaklarını) verimli bir şekilde kullanma ve bu verimliliği talep değiştikçe ve teknolojiler geliştikçe sürdürme yeteneğidir.

Mimarinizin performance efficiency durumunu değerlendirmek şunları içerir:

- Daha sık experimenting (deney yapmak)

- Serverless architectures (sunucusuz mimariler) kullanmak

- Sistemleri go global in minutes (dakikalar içinde küresel yayına geçebilecek şekilde) tasarlamak

## Cost Optimization

Cost optimization, sistemleri en düşük maliyetle çalıştırarak iş değeri sağlama yeteneğidir.

Cost optimization 💰 (Maliyet Optimizasyonu)
Cost optimization, sistemleri en düşük maliyetle çalıştırarak iş değeri sağlama yeteneğidir.

Cost optimization şunları içerir:

- Adopting a consumption model (tüketime dayalı bir model benimsemek)

- Analyzing and attributing expenditure (harcamaları analiz etmek ve ilgili yerlere atamak)

- Using managed services to reduce the cost of ownership (sahip olma maliyetini azaltmak için yönetilen hizmetler kullanmak)

## Sustainability

Aralık 2021’de AWS, AWS Well-Architected Framework içine sustainability pillar’ını da ekledi.

Sustainability, provisioned resources (tahsis edilmiş kaynaklardan) maksimum fayda sağlayarak ve gereken toplam kaynağı en aza indirerek, energy consumption (enerji tüketimi) azaltılarak ve efficiency (verimlilik) artırılarak workload’un tüm bileşenlerinde sustainability impact (sürdürülebilirlik etkisini) sürekli geliştirme yeteneğidir.

Sustainability için iyi tasarımı kolaylaştırmak adına:

- Understand your impact (Etkinizi anlayın)

- Establish sustainability goals (Sürdürülebilirlik hedefleri belirleyin)

- Maximize utilization (Kaynak kullanımını maksimize edin)

- Anticipate and adopt new, more efficient hardware and software offerings (Yeni ve daha verimli donanım ve yazılım çözümlerini öngörün ve benimseyin)

- Use managed services (Yönetilen hizmetleri kullanın)

- Reduce the downstream impact of your cloud workloads (Cloud workload’larınızın dolaylı etkilerini azaltın)

-------------------------------------------------------------------------------------------------------------------------------

# Advantages of cloud computing

AWS Cloud ortamında çalışmak, on-premises (yerinde kurulum) veya hybrid environments (hibrit ortamlar) ile karşılaştırıldığında birçok avantaj sunar. Cloud computing’in altı avantajına bakalım:

1- Trade upfront expense for variable expense (Peşin maliyeti değişken maliyetle değiştirin): Yani donanımlara peşin olarak para vermek yerine, donanım yatırımı yapmadan, sadece kullandığın kadar öde.

2- Benefit from massive economies of scale (Büyük ölçek ekonomilerinden faydalanın): AWS gibi dev hizmet sağlayıcılar sayesinde daha düşük birim maliyet. 

3- Stop guessing capacity (Kapasite tahmini yapmayı bırakın): Trafik artarsa otomatik ölçeklenir, fazla tahmin yapmaya gerek kalmaz.

4- Increase speed and agility (Hız ve çevikliği artırın): Dakikalar içinde kaynak oluşturabilir, test ve inovasyon sürecini hızlandırabilirsin.

5- Stop spending money running and maintaining data centers (Veri merkezlerini çalıştırmak ve bakımını yapmak için harcama yapmayı bırakın): Altyapı operasyonlarını AWS’e bırak, kaynaklarını daha verimli kullan.

6- Go global in minutes (Dakikalar içinde küreselleşin): Farklı AWS Regions (AWS Bölgeleri) sayesinde uygulamanı hızlıca dünya çapında kullanıma açabilirsin.

