# III-hafta-odevi

✅- .Net kodu nedir ve nasıl derlenir?

✅- Roslyn compiler ne işe yarar?

✅- Restful servisler nasıl çalışır? Alternatifleri nelerdir ve nasıl çalışırlar?

✅- Extension method nedir? Nasıl yazılır?

✅- MVC'nin alternatifleri nelerdir?

✅- Architectural pattern nedir? Neden ihtiyaç duyuyoruz?

- ViewData, ViewBag, TempData farkları nelerdir? Çalıştığımız proje üzerinde başka bir branch açarak bunları deneyiniz?

## .Net kodu nedir ve nasıl derlenir?
  * **.Net Nedir**
    * .NET Core modüler yapısıyla ve open source bir framework olarak contribute edilebilir ortam sağlamıştır. Microsoft hem kendi frameworkünü .NET ekosisteminde yaşayan geliştiricilerin isteklerine hızlı cevap verir hale getirirken hemde .NET Core ile uygulama geliştireceklere çok daha “modern” bir ortam sağlamayı başardı.
 *  **Nasıl derlenir**
    * Derlemeler, için temel dağıtım, sürüm denetimi, yeniden kullanım, etkinleştirme kapsamı ve güvenlik izinleri birimlerini oluşturur. NET tabanlı uygulamalar. Bir derleme, birlikte çalışacak ve mantıksal bir işlevsellik birimi oluşturacak biçimde oluşturulan bir tür ve kaynakların bir derlemesidir. Derlemeler yürütülebilir (. exe) veya dinamik bağlantı kitaplığı (. dll) dosyaları formunu alır ve .NET uygulamalarının yapı taşlarıdır. Ortak dil çalışma zamanını, tür uygulamalarının farkında olması için gereken bilgileri sağlar.
    
## Roslyn compiler ne işe yarar?
  * Rosyln kısaca, .NET için olan bir compiler platformu. Hatta resmi adı da zaten **.NET Compiler Platform.** .NET Runtime’ında çalışan kodları derleyen, compiler’ın servis olarak, API’lar üzerinden dışarı açılması olarak tanımlayabiliriz. Bu API’lar, lexical analiz, semantic analiz gibi compiler’ların olmazsa olmaz bileşenlerine müdahele etmeyi, genişletmeyi sağlayan parçalar olarak karşımıza çıkıyor. Ve tabi ki derleme aşamasına da aynı şekilde müdahale edebiliyoruz.
  * Yani, Her programlama dilinin bir grammer’i vardır; normal konuşma dillerinde olduğu gibi. Bu grammer, o dilin kurallarını oluşturur. if’den sonra () içerisinde true/false bir ifade kontrolü ile { } içerisinde ki kodların çalıştırılması gibi. Buradaki keyword ya da diğer ifadeler de dilin syntax’ını yani alfabesini oluşturur. Yazdığımız ifadeler, syntax’ın parse edilip, dilin kuralları ile yorumlanması ve derlenmesi ile de çalışır hale gelirler. Basitçe anlatmaya çalıştığım bütün bu adımlara, Rosyln ile artık çeşitli noktalarda müdahele etme şansımız ortaya çıkıyor.
  
## Restful servisler nasıl çalışır? Alternatifleri nelerdir ve nasıl çalışırlar?
* RESTful servisler’in birçok farklı response tipi olabilir. Bugünlerde popüler olarak JSON kullanılıyor fakat XML, CSV veya amaca bağlı olarak HMTL bile kullanılabilir. İlginç olan, önceki yıllarda bandwith düşük olmasına rağmen SOAP tabanlı servisler kullanarak kocaman kocaman verileri XML gibi verinin boyutunu daha da şişiren yöntemlerle aktarıyorduk. Şuan bandwith inanılmaz boyutlara ulaşmış durumda ve biz veri transferinde verinin boyutunu XML’e göre inanılmaz küçülten JSON kullanıyoruz

* **Rest servisler** 
  * Platform bağımsızlar. (Client’ın Windows, Server’ın Linux olmasının hiç bir önemi yok)
  * Dil bağımsızlar .
  * HTTP üzerinden çalışıyorlar.
  * Esnekler ve çok kolay genişletilebilirler.
  * Ayrıca belli kısıtları da var ;
  * Bunlara kısıttan daha çok REST mimarisinin hangi sınırlar içerisinde yer almasını belirleyen prensipler diyebiliriz.
* **Kısıtlar(Prensipler)**
  * Client-Server Mimarisi
    *  Burada anlatılmak istenilen aslında **Separation of Concerns** prensibi. Client’ın Server tarafındaki veri kaynağı hakkında hiç birşey bilmemesi, Server’ın da doğru istekler geldiği sürece doğru yanıtı vermesi. Client ile Server’ın birbirlerinden bağımsız olması. Amaç aslında platform bağımsız çalışmayı ve scalability’i arttırmak. Ayrıca aralarında ki interface ortak kaldığı sürece birbirlerinden bağımsız bir şekilde gelişmeleri de sağlanmış oluyor.
    
  * Stateless
    * Server tarafında client ile ilgili bir context veya Session tutulmaz. Client tarafından yapılan her request Server’ın response verebilmesi için gerekli bilgiyi taşır, yani her türlü state client tarafında tutulur, ihtiyaç duyulursa request içerisinde server’a bildirilir. Bu Scalability açısından da önemlidir, çünkü server’ın requestler arasında herhangi bir state’i saklamasını gereksiz kılar ve kaynak yönetimini kolaylaştırır. Visibility açısından önemlidir, çünkü request’in amacını anlamak için tek bir request’in içerdiği bilgiler yeterlidir.  
      
      Tabi stateless olmasının bazı dezavantajlarıda var. Client her request’de gerekli bilgileri eklemek zorundadır bu da network trafiğini arttırır. Bu ayrıca server’ın uygulamanın davranışlarındaki tutarlığı kontrol etmesini zorlaştırır, çünkü birçok farklı client’dan farklı içerikli requestler gelebilir, server’a validasyon açısından daha fazla yük binebilir.
      
  * Cacheable 
    * HTTP response’ları client tarafından “cache”lenebilir, o yüzden Server gönderdiği response’ların cacheable olup olmadığını belirtmek durumundadır, bu performans açısından önemlidir.
    
   * Uniform Interface
      * Client-Server’lar arasında ortak, tekbiçimli arayüzlerin olması REST’in en önemli prensiplerinden biridir. Bu hem iletişim yöntemini basitleştiriyor hem de ortak bir interface olması sayesinde her parçanın birbirinden bağımsız bir şekilde evrimleşmesine olanak sağlıyor. Bu konu daha önce bahsettiğim HTTP Methodları ilede alakalı.
        
        Bununla ilgili çok güzel bir örnek var, yukarıda LEGO’dan bahsetmiştim. LEGO ile oynayanlar bilirler, birbirinden farklı LEGO parçaları olsa da, onları birleştirmenin sadece birkaç yolu vardır, herhangi bir alışveriş mağzasından aldığınız yeni LEGO parçası, elinizdeki parçalarla kolay bir şekilde entegre olur, çünkü zaten standartları önceden tanımlanmıştır. Aklınıza “LEGO parçalarının birbirlerine bağlamanın bu kadar az yolu varken ortaya büyük şeyler çıkabilir mi?” gibisinden bir soru gelebilir.
   * Layered System
      * Burada kast edilen aslında client’ın son server’a mı yoksa bir aracı server’a mı bağlandığını bilmiyor olması, yani her katman aslında tek bir katmanı biliyor. Bu tür bir yapıya olanak sağlamasıyla birlekte, aracı serverlar load-balancing yaparak scalability arttırabiliyor ve client’ları belli security policy’lerine zorlayabiliyorlar. Bu yapı ayrıca encapsulation yapılması gereken yerlerde kullanılabiliyorlar. Tabi böyle bir pipe-line’ın aşırı kullanımı client — server arasında gecikmelere sebep olabiliyor.
  * Code on Demand
    * Server belli durumlar’da client tarafındaki fonksiyonaliteyi arttırmak veya değiştirmek için, client tarafına executable scriptler gönderebilir. Böyle bir kullanım bazı durumlarda Visibility’i düşürdüğü için, Code on Demand tek opsiyonel kısıttır.
    * Eğer bir servis **Code on demand** kısıtı hariç diğer kısıtları içermiyorsa tam olarak RESTful servis değildir. Bu kısıtların çoğu, bugünün modern programlama ortramlarında endişe edilmesi veya uygulanması zor kısıtlar değiller. Ayrıca bu kısıtların çoğu bize yabancı gelen kavramlar değiller, çoğumuz kendi mimarilerimizde de kullanmışızdır. Bence zaten en dikkat edilmesi gereken kısıt REST’in **Stateless** olması. REST’in hedefledikleri aslında ; Scalability, Simplicity, Modifiability, Visibility, Portability ve Reliability. Yukarıdaki kısıtlara ne kadar uyarsanız, hedeflediklerini o kadar gerçekleştirmiş olursunuz.
* **Alternatifleri nelerdir**
  * REST vs SOAP
    * |Rest'in Avantajları   |Soap'ın Avantajları   |
      |---|---|
      |Hafiftir, kolay extend edilebilir.   |Consume etmesi kolaydır, bir şemayla beraber gelir|
      |Gelen, giden data boyutu SOAP ile karlılaştırıldığında çok ufaktır |Type-safety’dir, sizi bu tür validasyonlarla uğraştırmaz|
      |Tasarlaması kolaydır ve implementasyonu kolaydır, herhangi bir ekstra tool’a ihtiyacı yoktur|Bir sürü development tool’u vardır|
      |HTTP üzerinden çalışır, platform bağımsızdır|Security implementasyonu REST’e göre daha kolaydır, bir sürü hazır yapı vardır.|
      
## Extension method nedir? Nasıl yazılır?
 * **Extension method nedir?**
   * Kelime anlamı genişletilebilir metod olan Extension Method'lar C#3.0 ile hayatımıza girmiştir ve yaptığı iş itibatiyle kullanım açısından son derece faydalı metodlardır. Tek cümleyle özetlemek gerekirse class ve struct yapılarını modify etmeden ilgili struct yada class'için extension metodlar eklememizi sağlar. 
      Extesion metod yazarken uymamız gereken bir kaç kural vardır. Bunlar;
      * Extension metodlar static bir class içerisinde static olarak tanımlanmalıdır. 
      * Extend edilecek class ilgili extension metoda metodun ilk parametresi olarak verilip önünde this keyword'ü ile tanımlanmalıdır
      * Extension metod da tanımlı parametrelerden sadece 1 tanesi this keyword'ü ile tanımlanır
 * **Nasıl yazılır?**
   * Yine örnek olarak ; bir Person class'ımız ver ve içerisinde DateTime tipinde ismi BirthDate olan bir property olsun. Bir tane GetBirthDate adında extension metod tanımlayalım ve bu metod bize parametre olarak aldığı Person objesinde bulunan BirthDate alanını return ettirsin.
     ```c# 
      public class Person
      {
        public string FullName {get;set;}
        public DateTime BirthDate {get;set;}
      } 
      public static class MyExtensions
      {
        public static DateTime GetBirthDate(this Person prs)
        {
            return prs.BirthDate;
        }
      }
     ```
     Şimdi bu metodu kullanan kısmı yazalım
     ```c# 
      using System;
                     
      class Program
      {
        static void Main(string[] args)
        {
          Person prs=new Person();
          DateTime bDAte = prs.GetBirthDate();
        }
      }
     ```
## MVC'nin alternatifleri nelerdir?
  * HMVC - Hierarchical Model-View-Controller
  * MVVM - Model-View-ViewModel
  * MVP - Model View Presenter
  * MVA - Model View Adapter
  * PAC - Presentation Abstraction Control
  * RMR - Resource-Method-Representation
  * ADR - Action-Domain-Responder

## Architectural pattern nedir? Neden ihtiyaç duyuyoruz?
 * **Architectural pattern nedir?**
    * Bir mimari desen, bir sistemin görüntüsünü taşısa da, bir mimari değildir. Mimari desen, bir yazılım mimarisinin bazı temel bütünleşik unsurlarını çözen ve tasvir eden bir kavramdır. Sayısız farklı mimari aynı kalıbı uygulayabilir ve ilgili özellikleri paylaşabilir. Kalıplar genellikle "kesin olarak tanımlanmış ve yaygın olarak bulunabilen" olarak tanımlanır
 * **Neden ihtiyaç duyuyoruz?**
   * Mimarı deseni bir binanın temeli gibi düşünecek olursak ki öyle düşünmeliyiz ve Bizim kodumuzun da bir temele ihtiyacı olacağı için kullanmaya ihtiyaç duyuyoruz.
      Şöyle de bir açıklama yapılabilir; Bizim kodumuzu daha okunaklı ve daha düzenli yapabilecek olay bu olduğu için buna ihtiyaç duyuyoruz.
      
## ViewData, ViewBag, TempData farkları nelerdir?
  * **ViewData**
    * Teknik olarak veri Controller sınıfından View sayfalarına ViewDataDictionary (ViewData) sınıfı ile taşınmaktadır. ViewData nesnesine veri aktarabilir ve bu veriyi okuyabiliriz.  ``` ViewData[“CurrentTime”] = DateTime.Now; ```
  * **ViewBag**
    * ViewBag ise ASP.NET MVC 3 te C# 4 ile gelen dynamic anahtar kelimesinin getirdiği bir yeniliktir. ViewData nın dinamik (run time binding) halidir. Söz dizimi de daha iyidir. ```ViewBag.CurrentTime = DateTime.Now;```
    
  * **TempData**
    * Bu nesne de diğer ikisinin yaptığı işi yapar.```TempData[“CurrentTime”] = DateTime.Now;``` Bu üç nesne arasında küçük ve kritik farklar vardır. Örneğin ViewBag nesnesi dynamic tipinde bir nesne olduğundan bununla alakalı hatalar compile time da değil run time da yakalanır. Teknik anlamda ViewData nesnesinden farkı yoktur. Söz dizim olarak farklıdır.
