# Amazon CloudWatch

Amazon CloudWatch, çeşitli metrikleri izlemenize ve bu metriklerden gelen verilere göre alarm eylemleri yapılandırmanıza olanak tanıyan bir web hizmetidir.

CloudWatch, kaynaklarınıza ait veri noktalarını temsil etmek için metric (metrik) kullanır. AWS servisleri bu metrikleri CloudWatch’a gönderir. CloudWatch da bu metrikleri kullanarak, zaman içinde performansın nasıl değiştiğini gösteren grafikler oluşturur.

### Amazon CloudWatch Alarms

CloudWatch ile, bir metrik değeri önceden tanımlanmış bir eşik değerin üzerine çıktığında veya altına düştüğünde otomatik olarak işlem yapan alarmlar oluşturabilirsiniz. Örneğin, şirketinizin geliştiricileri uygulama geliştirme veya test amaçlı Amazon EC2 instance’ları kullanıyor olsun. Geliştiriciler bazen bu instance’ları durdurmayı unutabilir. Bu durumda instance’lar çalışmaya devam eder ve maliyet oluşturur. Bu senaryoda, CPU kullanım oranı belirli bir süre boyunca belirli bir eşik değerin altında kaldığında, Amazon EC2 instance’ını otomatik olarak durduran bir CloudWatch alarmı oluşturabilirsiniz. Alarmı yapılandırırken, alarm tetiklendiğinde bildirim almayı da seçebilirsiniz.

CloudWatch dashboard özelliği, kaynaklarınıza ait tüm metriklere tek bir yerden erişmenizi sağlar. Örneğin, bir Amazon EC2 instance’ının CPU kullanımını, bir Amazon S3 bucket’a yapılan toplam istek sayısını ve daha fazlasını izlemek için bir CloudWatch dashboard kullanabilirsiniz. Farklı iş amaçları, uygulamalar veya kaynaklar için ayrı dashboard’lar bile özelleştirebilirsiniz.

## AWS CloudTrail

AWS CloudTrail, hesabınıza ait API çağrılarını (calls) kaydeder. Kaydedilen bilgiler arasında, API çağrısını yapan kişinin kimliği, çağrının zamanı, çağrıyı yapanın IP adresi ve daha fazlası bulunur. "Trail" kelimesinden de anlayabileceğiniz üzere CloudTrail’i, birinin arkasında bıraktığı ekmek kırıntılarından oluşan bir iz (ya da log günlüğü) olarak düşünebilirsiniz.

API çağrılarını AWS kaynaklarınızı oluşturmak, yönetmek ve yapılandırmak için kullanabileceğinizi hatırlayın. CloudTrail sayesinde, uygulamalarınız ve kaynaklarınızla ilgili kullanıcı etkinliklerinin ve API çağrılarının tam geçmişini görüntüleyebilirsiniz. Olaylar (events), API çağrısından sonra genellikle 15 dakika içinde CloudTrail’de güncellenir. Bir API çağrısının gerçekleştiği zaman ve tarih, çağrıyı yapan kullanıcı, çağrıda yer alan kaynak türü gibi kriterlere göre olayları filtreleyebilirsiniz.

### CloudTrail Insights

CloudTrail içinde, isteğe bağlı bir özellik olan CloudTrail Insights'ı da etkinleştirebilirsiniz. Bu özellik, AWS hesabınızda olağandışı API etkinliklerini otomatik olarak tespit etmesini sağlar.

Örneğin, CloudTrail Insights, hesabınızda normalden daha fazla sayıda Amazon EC2 instance’ının kısa süre önce başlatıldığını algılayabilir. Sonrasında, tam olay ayrıntılarını inceleyerek hangi adımları atmanız gerektiğine karar verebilirsiniz.

## AWS Trusted Advisor

AWS Trusted Advisor, AWS ortamınızı inceleyen ve gerçek zamanlı olarak AWS best practices'a göre öneriler sunan bir web hizmetidir. Trusted Advisor, bulgularını AWS best practices ile karşılaştırır ve bunu beş kategori altında yapar:

- cost optimization

- performance

- security

- fault tolerance

- service limits.

Her kategori için Trusted Advisor, önerilen işlemlerin bir listesini ve daha fazla bilgi edinebileceğiniz ek kaynakları sunar.

Her kategori için:

✅ Yeşil tik, herhangi bir sorun tespit edilmeyen öğelerin sayısını gösterir.

⚠️ Turuncu üçgen, inceleme yapılması önerilen öğelerin sayısını gösterir.

⛔ Kırmızı daire, eylem alınması gereken öğelerin sayısını temsil eder.


