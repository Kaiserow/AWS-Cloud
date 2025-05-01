# AWS Shared Responsibility Model

Bu zamana kadar AWS Cloud'unda oluşturabileceğin çeşitli kaynakları öğrendin. Bu kaynaklara Amazon EC2 instance’ları, Amazon S3 bucket’ları ve Amazon RDS veritabanları dahildir. Peki bu kaynakların güvenliğinden kim sorumludur: sen mi (müşteri) yoksa AWS mi?

Aslında iki taraf da sorumludur. Çünkü AWS ortamını tek bir bütün gibi değil, birbiri üzerine kurulu parçalardan oluşan bir sistem gibi ele alırsın. Bu parçaların bazıları AWS’nin, bazıları da senin sorumluluğundadır. Bu kavram, paylaşılan sorumluluk modeli (shared responsibility model) olarak adlandırılır. 

Müşteri sorumlulukları → “buluttaki güvenlik (security in the cloud)”

AWS sorumlulukları → “bulutun güvenliği (security of the cloud)”

![image](images/sharedmodel.png)

Bu modeli, bir ev sahibi ile ev inşa eden kişi arasındaki sorumlulukların bölünmesine benzetebilirsin.

İnşaatçı (AWS), evi inşa etmekten ve yapının sağlam olmasını sağlamaktan sorumludur.

Ev sahibi (yani müşteri) ise, evin içindekileri korumaktan; yani kapıların kapalı ve kilitli olduğundan emin olmaktan sorumludur.

> Security in the cloud

Müşteriler, AWS Bulutu'nda oluşturdukları ve yerleştirdikleri her şeyin güvenliğinden sorumludur.

AWS hizmetlerini kullanırken, içeriğin üzerinde tam kontrol sende olur. Hangi içeriği AWS üzerinde saklayacağın, hangi AWS hizmetlerini kullanacağın ve bu içeriğe kimin erişeceği gibi güvenlik gereksinimlerinin yönetimi sana aittir. Erişim haklarının nasıl verileceğini, yönetileceğini ve iptal edileceğini de sen belirlersin.

Aldığın güvenlik önlemleri; kullandığın hizmetlere, sistemlerinin karmaşıklığına ve şirketinin operasyonel ve güvenlik ihtiyaçlarına göre değişir.

Bu önlemlere örnek olarak:

- Amazon EC2 instance’larında çalışacak işletim sistemlerinin seçilmesi, yapılandırılması ve yamalanması,

- Güvenlik gruplarının (security groups) yapılandırılması,

- Kullanıcı hesaplarının yönetilmesi verilebilir.

> Security of the cloud

AWS, altyapının tüm katmanlarındaki bileşenleri işletir, yönetir ve kontrol eder. Buna, hizmetlerin çalıştığı veri merkezlerinin fiziksel güvenliği, host işletim sistemi, sanallaştırma katmanı gibi alanlar dahildir.

AWS, AWS Bulutu'nda sunulan tüm hizmetleri çalıştıran global infrastructure korunmasından sorumludur. Bu altyapı; AWS Region’ları, Availability Zone’lar ve uç noktaları (edge locations) içerir.

AWS, kaynaklarının barındırıldığı fiziksel altyapının güvenliğini yönetir. Bu altyapıya şunlar dahildir:

- Physical security of data centers
  
- Hardware and software infrastructure

- Network infrastructure

- Virtualization infrastructure

AWS veri merkezlerini doğrudan ziyaret edemesen de, AWS çeşitli bağımsız denetçi raporları sunar. Bu denetçiler, AWS’nin birçok bilgi güvenliği standardı ve düzenlemesine uyduğunu doğrulamıştır.

# User Permissions and Access

## AWS Identity and Access Management (IAM)

AWS IAM, bir authentication ve authorization hizmetidir. AWS Identity and Access Management (IAM), AWS hizmetlerine ve kaynaklarına güvenli bir şekilde erişimi yönetmenizi sağlar. IAM, şirketinizin özel operasyonel ve güvenlik ihtiyaçlarına göre erişimi yapılandırma esnekliği sunar. IAM şu özellikleri sunar:

- IAM kullanıcıları, grupları ve roller

- IAM politikaları

- Multi-factor Authentication (MFA)

### AWS account root user

AWS hesabınızı ilk oluşturduğunuzda, root user (kök kullanıcı) olarak bilinen bir kimlikle başlarsınız.

Root user, AWS hesabınızı oluştururken kullandığınız e-posta adresi ve parolayla oturum açarak erişilir. Root user’ı, bir kahve dükkanının sahibi gibi düşünebilirsiniz. Hesaptaki tüm AWS services (AWS hizmetleri) ve resources (kaynaklar) üzerinde tam erişime sahiptir.

*Best practice olarak, Root user’ı günlük görevler için kullanmanız önerilmez. Bunun yerine, root user ile ilk IAM user’ınızı oluşturun ve bu kullanıcıya diğer kullanıcıları oluşturma yetkisi verin. Root user’ı yalnızca, sadece root user’a özel olan sınırlı sayıdaki görevi yerine getirmeniz gerektiğinde kullanın.*

### IAM users

Bir IAM user, AWS'te sizin oluşturduğunuz bir kimliktir. AWS hizmetleri ve kaynaklarıyla etkileşime giren kişiyi ya da uygulamayı temsil eder. Bir adı (name) ve kimlik bilgileri (credentials) vardır.

Varsayılan olarak, AWS’te yeni bir IAM user oluşturduğunuzda, bu kullanıcıya hiçbir permission (izin) tanımlı değildir. Bu IAM user’ın AWS üzerinde belirli işlemleri yapabilmesi için — örneğin bir Amazon EC2 instance başlatmak ya da bir Amazon S3 bucket oluşturmak gibi — gerekli izinleri (permissions) vermeniz gerekir.

*Best practice olarak, AWS’e erişmesi gereken her kişi için ayrı IAM user oluşturulması önerilir.*

*Aynı erişim düzeyine ihtiyaç duyan birden fazla çalışanınız olsa bile, her biri için ayrı IAM user oluşturmalısınız. Bu yaklaşım, her IAM user’ın kendine özgü security credentials (güvenlik kimlik bilgileri) olmasını sağlayarak ek güvenlik sunar.*

### IAM policies

Bir IAM policy, çeşitli AWS hizmetlerine ve kaynaklarına izin veren (allow) veya bunları reddeden (deny) bir belgedir.

IAM policies, kullanıcıların kaynaklara erişim düzeylerini özelleştirmenizi sağlar. Örneğin, kullanıcıların AWS hesabınızdaki tüm Amazon S3 buckets’lara erişmesine izin verebilir ya da yalnızca belirli bir bucket’a erişim izni tanıyabilirsiniz.

*Best practice olarak, izin (permission) verirken en az ayrıcalık (least privilege) güvenlik ilkesini takip edin. Bu ilkeyi uygulayarak, kullanıcıların veya rollerin görevlerini yerine getirmek için gerekenden fazla permission (izin) almasını önlemiş olursunuz.*

*Örneğin, bir çalışanın yalnızca belirli bir Amazon S3 bucket’a erişmesi gerekiyorsa, IAM policy içinde sadece o bucket’a izin tanımlayın. Çalışana AWS hesabınızdaki tüm bucket’lara erişim vermek yerine bu şekilde daha güvenli bir erişim kontrolü sağlamış olursunuz.*

> IAM policy örneği:

![image](images/IAM.png)

İşte IAM policies’in nasıl çalıştığını gösteren bir örnek: Diyelim ki kahve dükkanı sahibi, yeni işe alınan bir kasiyer için bir IAM user oluşturmak zorunda. Kasiyerin, Amazon S3 üzerinde tutulan ve kimliği AWSDOC-EXAMPLE-BUCKET olan bir bucket’taki fişlere erişmesi gerekiyor.

Bu örnekte, IAM policy belirli bir Amazon S3 işlemi olan "ListObject" eylemine izin veriyor. Policy aynı zamanda belirli bir bucket ID’si olan AWSDOC-EXAMPLE-BUCKET’ı da içeriyor.

Kahve dükkanı sahibi, bu policy’yi kasiyerin IAM user’ına eklediğinde, kasiyer AWSDOC-EXAMPLE-BUCKET içindeki tüm nesneleri (objects) görüntüleyebilecek.

Eğer dükkan sahibi, kasiyerin başka AWS hizmetlerine de erişmesini veya farklı işlemler gerçekleştirmesini istiyorsa, bu hizmetleri ve işlemleri belirten ek policies de tanımlayıp kullanıcısına eklemelidir.

### IAM Groups

Şimdi, diyelim ki kahve dükkanı birkaç yeni kasiyer daha işe aldı. Her bir IAM user için ayrı ayrı izin atamak yerine, sahip bu kullanıcıları bir IAM group içine yerleştirir. Bu yöntemle, sahip aynı permissions’ları (izinleri) tek seferde gruba uygulayarak, gruptaki tüm kullanıcıların bu izinleri otomatik olarak almasını sağlar. Böylece yönetim daha kolay ve tutarlı hale gelir.

İzinleri grup düzeyinde atamak, bir çalışanın farklı bir göreve geçmesi durumunda da izin yönetimini kolaylaştırır. Örneğin, bir kasiyer Inventory Specialist (Envanter Uzmanı) olduğunda, sahip bu kullanıcıyı “Cashiers” grubundan çıkarır ve “Inventory Specialists” grubuna ekler. Böylece çalışanlar yalnızca mevcut rollerine uygun izinlere sahip olur.

*Peki ya bir çalışan kalıcı olarak görev değiştirmemişse, fakat gün içinde farklı iş istasyonları arasında rotasyona giriyorsa? Bu durumda, ihtiyaç duyduğu erişimi IAM roles (roller) aracılığıyla alabilir.*

### IAM Roles

Kahve dükkanında bir çalışan gün içinde farklı iş istasyonları arasında rotasyon yapar. Dükkanın o anki personel durumuna göre bu çalışan birden fazla görevi yerine getirebilir: kasada çalışmak, envanter sistemini güncellemek, çevrimiçi siparişleri işlemek vb.

Çalışan farklı bir göreve geçtiğinde, bir iş istasyonuna olan erişimini bırakır ve bir sonraki iş istasyonuna erişim kazanır. Çalışan bu geçişleri kolayca yapabilir, ancak herhangi bir anda yalnızca tek bir iş istasyonuna erişimi olabilir. Bu kavram, AWS’te IAM roles (roller) ile aynı şekilde uygulanır.

Bir IAM role, geçici erişim izinleri kazanmak için assume (üstlenilebilen) bir kimliktir.

Bir IAM user, uygulama ya da hizmet bir IAM rolünü üstlenmeden önce, bu role geçiş yapmak için gerekli permissions’lara sahip olmalıdır. Bir kişi bir IAM rolünü assume ettiğinde, önceki rolündeki tüm izinleri bırakır ve yeni rolün izinlerini devralır.

*Best practice olarak, IAM roles, bir hizmete veya kaynağa geçici erişim sağlanması gereken durumlar için idealdir. Uzun vadeli erişim yerine, kısa süreli ve göreve özel erişim gerektiğinde IAM rolleri kullanılmalıdır.*

#### NOT: IAM roles, yukarıda da bahsettiğimiz gibi, sadece bir user'a değil; uygulama ya da hizmete de atanabilir.

## Multi-factor authentication (MFA)

IAM içinde, MFA, AWS hesabınıza ek bir güvenlik katmanı sağlar. MFA şu şekilde çalışır:

1- Öncelikle kullanıcı, AWS web sitesinde oturum açmak için IAM kullanıcı kimliğini ve parolasını girer.

2- Sonraki adımda, kullanıcıdan AWS MFA cihazı üzerinden bir doğrulama yanıtı (authentication response) girmesi istenir. Bu cihaz;

- hardware security key

- hardware device

- telefon gibi bir cihazda bulunan MFA App'i olabilir.

-------------------------------------------------------------------------------------------------------------------------------

## AWS Organizations

Diyelim ki şirketinizin birden fazla AWS hesabı var. Bu hesapları merkezi bir yerden birleştirmek ve yönetmek için AWS Organizations hizmetini kullanabilirsiniz.

Bir organization oluşturduğunuzda, AWS Organizations otomatik olarak bir root (tüm hesapların üst kapsayıcısı) oluşturur.

AWS Organizations içinde, organizasyonunuzdaki hesaplara ait izinleri merkezi olarak kontrol etmek için service control policies (SCPs) kullanabilirsiniz. SCP’ler, her bir hesaptaki kullanıcıların ve rollerin erişebileceği AWS hizmetleri, kaynaklar ve bireysel API işlemleri üzerinde kısıtlamalar getirmenizi sağlar.

> Organizational units

AWS Organizations içinde, benzer iş veya güvenlik gereksinimlerine sahip hesapları daha kolay yönetebilmek için bu hesapları organizational unit (OU) adı verilen gruplar altında toplayabilirsiniz.

Bir OU’ya bir politika (policy) uyguladığınızda, o OU içindeki tüm hesaplar bu policy’de belirtilen izinleri otomatik olarak devralır.

Ayrı hesapları OU’lara göre düzenlemek, özellikle özel güvenlik gereksinimleri olan iş yüklerini veya uygulamaları izole etmek açısından oldukça kullanışlıdır.

Örneğin, şirketinizde yalnızca belirli regülasyonlara (örneğin sağlık ya da finans gibi) uygun AWS hizmetlerine erişmesi gereken hesaplar varsa, bu hesapları tek bir OU altında toplayabilirsiniz. Sonrasında bu OU’ya, regülasyonlara uymayan tüm AWS hizmetlerine erişimi engelleyen bir policy ekleyebilirsiniz.


#### NOT: Hesapları, kullanıcılarla karıştırmamak gerekir. Her hesabın bir root user'ı vardır ve bu hesabın içinde IAM User'lar tanımlanabilir. AWS Organizations, kullanıcıları değil daha genel olarak hesapları organize etmenize olanak tanır. Bu yüzden, IAM Policy; IAM user, group, role için uygulanabilirken, OU, accounts ve root için uygulamayazsınız. Onlar için SCP uygulanabilir. Yani accountlar, kullanıcılara göre daha geniş bir kümedir diyebiliriz.




















  
