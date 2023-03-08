Riverpod Nedir?

Riverpod, Flutter uygulamaları için bir durum yönetim(State Management) paketidir. Bu uygulamanızın farklı bileşenlerindeki durumu merkezi bir yerden yönetmeye ve koordine etmenize olanak tanır. Flutter widget’larında kullanım için tasarlanmıştır. Riverpod, Provider paketinin sunduğu tüm özellikleri ve daha fazlasını içerir.

Riverpod’un sağladığı en büyük avantaj, merkezi bir yerden yönetmenin yanı sıra, güçlü bağımlılık enjeksiyonu(dependency injection) özelliğidir. Dependency Injection, bir bileşenin ihtiyaç duyduğu diğer bileşenleri dışarıdan sağlar ve bu bileşenleri değiştirmeden tekrar kullandırır.

Riverpod’un sunduğu bazı özellikler:

Provider’lar: Riverpod, Provider’ın temelini oluşturan Provider sınıfından türetilen ve bir nesneyi sağlamak için kullanılan Providerlar sunar.

ScopedProvider’lar: Scopedprovider’lar, özellikle alt bileşenlerde bir bileşenin kullanımını kısıtlamamıza engel olmaya olanak tanır.

FamilyProvider’lar: Familyproviderlar, aynı türden nesneleri, farklı anahtarlar kullanarak sağlar. Bu, örneğin bir veritabanı işlemcisi için farklı farklı veritabanı adlarıyla birden fazla örneği aynı anda kullanmanıza olanak tanır.

AsyncValue: AsyncValue, asenkron değerlerle çalışırken kullanılan bir sınıftır. Bu, özellikle bir API’den veri alırken veya bir dosya yüklerken kullanışlıdır.

StateNotifierProvider’lar: StateNotifierProviderlar, StateNotifier sınıfından türetilir ve uygulamanızdaki durumu yönetmenin bir yolun sağlar.

Riverpod, güçlü bir bağımlılık enjeksiyonu özelliği ve Provider paketinin tüm özellikleri ile birlikte gelişmiş bir Flutter state management çözümüdür. Bu sayede, Flutter uygulamalarında daha kolay, düzenli ve bakımı kolay bir şekilde durum yönetimi yapabilirsiniz.

Peki Riverpod Nasıl Kullanılır?
Öncelikle pubspec.yaml dosyamıza paketi ekliyoruz.


Ekledikten sonra flutter pub get’i çalıştırın. Paketi ekledikten sonra basit bir örnekle devam edelim. Verilen bir butona basıldığında değeri artıran uygulama yapalım. Hadi başlayalım. Başlamadan önce paketi import etmeyi unutmayalım.


Öncelikle kullanıcı bir butona bastığında sayacı artırmak istediğimiz için, tabi ki verilere de yazmamız gerekiyor. Bunu yapmanın en basit yolu bir StateProvider kullanmaktır.


StateProvider kullanıp gerekli tanımlamaları yaptıktan sonra MyApp sınıfımızı ProviderScope ile sarmalamamız gerekiyor.


Bu aşamada uygulamanın direkt HomePage sınıfında çalışmasını istemiyorum, bu yüzden Navigator ile farklı bir sayfaya yönlendirme yaparak sayaç işlemlerini o sayfada yapacağım.


Buraya, bizi diğer sayfaya götürecek butonu verdikten sonra asıl sayaç sayfasına geçiyoruz. Bu sayaç sayfasında ConsumerWidget’tan extend ettiğimiz CounterPage sınıfını oluşturduk. Build fonksiyonu içerisine WidgetRef ref parametrelerini ekledikten sonra gerekli tanımlamaları yapıyoruz. Butona verdiğimiz onPressed fonksiyonu ile, uygulamada ki “+” butonuna tıklandığı zaman “ref.read(counterProvider.notifier).state++“ yapısı ile sayaçta ki değişken değiştiğinde bunu bildirerek yeni değer yazdırılır.


Tanımladığımız refresh butonu içerisinde tanımlanan ref.invalidate(counterProvider) ile sayaç değeri istendiği zaman sıfırlanabilir. Peki bunu butona gerek kalmadan nasıl yapabiliriz.


autoDispose otomatik olarak verileri sıfırlamaya yarar ve kullanışlı bir yapıdır.

Son olarak örneğimize şöyle bir özellik ekleyelim. Sayaç değeri 5 ve 5'ten büyük olursa eğer uygulama tarafından bize uyarı verilsin ve sıfırlamamız gerektiğini belirtsin.


Burada build fonksiyonu içerisinde ref.listen kullanılarak gerekli parametreleri dinlemesini ve sırası geldiğinde işlem yapmasını, uyarı vermesini istedik.


