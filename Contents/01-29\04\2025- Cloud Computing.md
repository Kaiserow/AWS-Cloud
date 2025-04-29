# What is a client-server model?

Bilgisayarda, bir client bir kişinin bilgisayar serverlarına isteklerde bulunmak için etkileşimde bulunduğu bir web tarayıcısı veya masaüstü uygulaması olabilir. Bir server, Amazon Elastic Compute Cloud (Amazon EC2) gibi bir tür sanal sunucu gibi hizmetler olabilir. Kısaca client, serverdan bir hizmet talep eder ve sunucu da bu hizmeti sunar/sağlar.

# Cloud Computing

Cloud computing, "pay-as-you-go" (kullandığın kadar ödeme yapmak) ile "on-demand delivery of IT resources" (IT kaynaklarının, talebe göre teslimi) olarak özetlenebilir. On-demand delivery, AWS'nin ihtiyaç duyduğunuz kaynaklara ihtiyaç duyduğunuzda sahip olmanız anlamına gelir. Örneğin, anlık olarak 300 virtual servera ihtiyaç duyarsanız, kolay bir şekilde elde edebilirsiniz. Aynı şekilde, artık 300 sanal sunucuya ihtiyacınız yoksa, iptal de edebilirsiniz. Fakat kendi data centerlarınızı yönetirken bunu yapmanız mümkün olmayacaktır.

Çok sayıda AWS IT kaynağı vardır çünkü bu diğer işletmelerden sizi farklı kılar. Birçok işletmede ortak olan IT kaynakları sizi diğerlerinden farklı kılmayacaktır. Örneğin, MySQL motoru kurmak veya backup almak herkesin yapabileceği birşeydir, bu da sizi farklı yapmaz. Fakat MySQL'in içindeki veriler ve o veritabanının nasıl kurulup, nasıl yönetildiği sizi özel yapar.

AWS bu tür sıradan işleri "undifferentiated heavy lifting" diye adlandırır. Bunlar, herkesin yapmak zorunda olduğu ama seni diğerlerinden farklılaştırmayan ağır işlerdir. (Sunucu kurmak, motor yüklemek, bakım yapmak vs.) 

AWS de bu ağır işleri kendilerine bırakılmasını ve işletmelerin, rekabetlerinde kendilerini özel kılan şeylere odaklanmasını amaçlar. 

AWS hizmetlerine, web tarayıcından (AWS Console) veya programlama ile (API'lar kullanarak) kolayca ve güvenli bir şekilde erişilebilir. Ek olarak AWS bunu; satıcıyla konuşma olmadan, ekstra kontrata ihtiyaç duymadan ve kullandığın kadar ödemeni sağlayarak sunar.

AWS'in bu esnekliği kahve dükkanı analojisi ile açıklanabilir. Kahve dükkanında sabah kalabalık olduğunda fazla personel çalıştırılırken, gece müşteri olmadığında fazladan personele gerek kalmaz. Aynı mantıkla, mesela hafta sonu kimse çalışmıyorsa  geliştirme sunucularını kapatırsın. Böylece ihtiyacın olmadığı zaman için de ayrıca para ödemezsin.

