---
layout: post
title:  "Merhabalar!"
date:   2021-10-08 08:36:26 -0400
categories: jekyll csharp
---
# Nesne tabanlı programlama (Object Oriented Programing)

Nesne tabanlı programlama birçok dilde kullanılmaktadır. Nesne tabanlı programlama bir kod yazma tekniği veya yaklaşımıdır diyebiliriz. Hayatımızda kullandığımız nesneleri kod halinde yazıp simüle etmemizi sağlayan bir tekniktir. Örnek olarak kitap nesnesini verebiliriz. Gerçek hayatta olduğu gibi kitabın adı, türü, sayfa sayısı, baskı numarası vs. bulunur, bu özelliklere sahip kitap adında bir nesne oluştururuz. Bu nesne tabanlı programlamanın temel mantığıdır. "Herşey bir nesnedir" mantığı bulunmaktadır, yani kitaplar, arabalar, kişiler, ağaçlar vb. bir nesnedir.

Oop'de en küçük parçaya nesne denir. Nesnelerin içinde veri tutulan alanlar bulunmaktadır ve bu alanlara field adı verilir. Nesneler sınıflardan türetilir, yani sınıflara nesne kalıpları diyebiliriz ve bu kalıplardan istediğimiz kadar nesne oluşturabiliriz. Örnek olarak araba nesnesini verelim. Araba adında bir class oluşturup bütün arabalardaki ortak özellikleri (rengi, kapı sayısı, motor gücü, motor türü vb.) bu classın içinde tanımlarız daha sonra nesne oluşturacağımız zaman bu class'dan nesneyi türetiriz. Nesneler referans türü yapılardır.

## Sınıflar(class)

Nesne tabanlı programlamada bir nesneyi tanımlayabilmemiz için o nesnenin bir kalıbının tanımlı olması gerekir, işte tam bu noktada class yapısı kullanılır. Çünkü class
içerisinde Field(alan), Property(özellik) ve kapsülleme yapılarını, metotlar vb. yapıları tanımlayabiliyoruz. BUnlar programlamanın temel yapılarıdır.  
`Arabalar` isminde bir sınıfımızın olduğunu var sayalım ve bu sınıftan `arba` isminde bir nesne tanımlayalım. Bu durunda `arba`, `Arabalar` sınıfının bir nesnesi ve `arba`, `Arabalar` tipinde bir değişken olur.  
Bir nesneyi tanımlamak için new operatörünü kullanırız.  
`SınıfAdı sınıfDeğişkeni = new SınıfAdı();` şeklinde sınıftan nesne oluştururuz. Burada SınıfAdı bir referans türüdür ve sınıfDeğişkeni bu türden üretilmiş bir nesnedir.  
Örnek:
```C#
class Program
{
    static void Main(string[] args)
    {
        Arabalar arba = new Arabalar();
        arba.renk = "Kırımız";
        arba.model = "Şahin";
        arba.kapıSayısı = 4;
        arba.OzellikYaz();
            
    }

}

class Arabalar
{
    public string renk;
    public string model;
    public int kapıSayısı;
        
    public void OzellikYaz()
    {
        Console.WriteLine($"renk {renk}, model {model}, kapıs sayısı {kapıSayısı}");
    }
}
```
Çıktı:
```
renk Kırımız, model Şahin, kapıs sayısı 4
```
Yukarıda `Arabalar arba = new Arabalar();` ile Araba sınıfına ait, arba isminde bir nesne tanımladık. Bu nesne Arabalar sınıfına ait renk, model, kapısayısı özellikleri ve OzellikYaz metodunu kullanabilmektedir.

Classlar 3 farklı yerde oluşabilir. Bunlar namespace içinde, namespace dışında ve class içerisinde(nested type) oluşturulabilir. Ama aynı isimde birden fazla class tanımlanamaz.

`namespace içinde`: Buradaki sınıflar aralarında namespace adı belirtmeden sadece sınıf adı ile iletişim kurabilir. Namespace dışında erişim sağlamak için namaspace ismi belirtmek gerekir.

`namespace dışında`: Bu sınıfa namespace ismi belirmeden heryerden erişim sağlayabiliriz.

`class içinde(nested type)`: Class içinde tanımlanan classlar sınıf elemanı değildir. Diyelimki class1 sınıfının içine class2 sınıfı tanımlı olsun. class2 sınıfından nesne oluşturmak için `class1.class2 nesneIsmi = new class1.class2();` şeklinde bir yapı kullanmalıyız.

### Class ve Elemanlarına Acıklama Ekleme

Bir elemena açıklama eklemek için hemen üst satırını:
```
/// <summary>
/// Açıklama
/// </summary>
```
şeklinde bir yapı ile açıklama ekleyebilirsiniz.  
Örnek:
```C#
/// <summary>
/// Bu bir öğrenci clasıdır.
/// </summary>
class Ogrenci
{
    /// <summary>
    /// Bu bir indexer'dır.
    /// </summary>
    /// <param name="x"> x parametresi </param>
    public int this[int x]
    {
        get
        {
            return x;
        }
        set
        {
            x = value;
        }
    }
        
    /// <summary>
    /// Bu bir Merhaba yazan bir metoddur.
    /// </summary>
    public void MerhabaYaz()
    {
        Console.WriteLine("Merhaba");
    }
}
```
Bu açıklama satırları yazdığımız kodun daha sonra rahat anlaşılmasını, yada başka biri okuduğunda rahat anlayabilmesini sağlamak için kullanılan yapılardır.

### Field(alan)
Nesne içinde veriyi sakladığımız alandır. Sadece class içinde tanımlanır ve herhangi bir türden olabilir. Class içerisine tanımlanan field'lara değer atamazsak varsayılan değer otomatik olarak atanır.

### Property

Property temelde bir metoddur. Ama metoddan farkı herhangi bir parametre almaması ve içinde 2 adet blok bulunmaktadır, bunlar get ve set bloklarıdır. Property'den bir değer alındığında get bloğu çalışır,  bir değer atandığında ise set bloğu çalışır. Nesnelerin içerisindeki field'lara erişimi kontrol etmek amacı ile kullanılır. Hem veri erişiminde hem de verileri dışarıya paylaşmada kontrol sağlamak istediğimizde bu yapıyı kullanılır. Bu kontrol mekanizmasına Encapsulation(Kapsülleme) denir.
#### Full Property
En sade property yapısıdır.  İçerisinde get ve set blokları tanımlanmalıdır.
```
ErişimBelirleyici GeriDÖnüşTürü PropertyAdı
{
    get{Property'den veri istendiğinde tetiklenir.}
    set{Property'e veri gönderildiğinde tetiklenir ve gönderilen veriyi value keywordü ile yakalar.}
{
```
Temelde property yapısı yukarıdaki gibidir. Full propertylerde set bloğu tanımlanmaz ise sadece okunabilir, get bloğu tanımlanmaz ise sadece yazılabilir olurlar.  
Örnek:
```C#
class Program
{
    static void Main(string[] args)
    {
        Arabalar arba = new Arabalar();
        // Burada set bloğu tetiklenmektedir.
        arba.Renk = "Kırmızı";
        
        // Burada ise get bloğu tetiklenmektedir.
        Console.ReadLine(arba.Renk);
    }
}

class Arabalar
{
    private string renk;
    public string Renk
    {
        get
        {
            return renk;
        }
        set
        {
            renk = value;
        }
    }
}
```
Yukarıda property yapısına bir örnek verdik. Property ismi büyük harfle başlamalıdır, bu zorunlu bir kural değildir ama genel olarak bu şekilde kullanılır. get bloğunun içinde return keywordü tanımlanması zorunludur, çünkü geriye döndürülecek bir değer beklenmektedir. set bloğunda ise value keywordü gönderilen değeri yakalamaktadır. Yani `arba.Renk = "Kırmızı";` ile set bloğu tetiklenmekte ve value keywordü "Kırmızı" değerini yakalamaktadır, ardından değeri renk field'ine atamaktadır. `Console.ReadLine(arba.Renk);` ile ise get bloğu tetiklenmekte renk field değeri return keywordü ile dışarı aktarılmaktadır.
#### Prop Property

Bir property encapsulation yapsa dahi temsil ettiği field'daki veriyi herhangi bir müdahele etmeden hem erişimi hem de veri atanmasını gerçekleştiriyorsa bu property türüne prop poperty denir.  
Bu normal kullanım:
```C#
class Ogrenci
{
    private string ismi;

    public string Ismi
    {
        get
        {
            return ismi;
        }
        set
        {
            ismi = value;
        }
    }
}
```
Buda prop kullanımdır:
```C#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci ogrnci = new Ogrenci();

        ogrnci.İsim = "Osman";
        Console.WriteLine(ogrnci.İsim);
    }
}

class Ogrenci
{

    public string İsim { get; set; }
}
```
Prop kullanıldığında field tanımlamamıza gerek yoktur. Çünkü field otomatik olarak tanımlanır.

#### Auto Property Initializers
Bir ptoperty'nin ilk değerini nesne ayağa kalkar kalkmaz tanımladığımız bir yapıdır.  
Örnek:
```C#
class Ogrenci
{

    public string İsim { get; set; } = "Osman";
}
```

#### Ref readonly Returns

Bu yapı bir sınıf içerisindeki field değerini referansıyla döndürmemizi sağlayan ve biryandan da bu değişkeni read only(sadece okunabilir) yapar.  
Örnek:
```C#
class Ogrenci
{
    private string isim = "Osman";
    public ref readonly string Isim => ref isim;
}
```


#### Computed(Hesaplanmış) Properties
İçerisinde türetilmiş bir bağıntı taşıyan propery'lerdir. Get veya set'in içerisinde farklı aritmatik işlemler yapmamızı sağlayan bir yapıdır.


#### Expression-Bodied Property
Lambda Expression kullanıldığı bir property yapısıdır. Auto Property Initializers yapısına benzer. Sadece readonly yapılarda kullanılır.  
Örnek:
```C#
class Ogrenci
{
    public string Isim => "Osman";
}
```

#### Init-Only Properties _ Init Accessor
.
.
.
.
.
.
.
.

#### Propertylere İlk Değer Verme
```C#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci og = new Ogrenci()
        {
            Myproperty1 = 10,
            Myproperty2 = 20,
            Myproperty3 = 30
        };
            
    }
}

class Ogrenci
{
    public int Myproperty1 { get; set; }
    public int Myproperty2 { get; set; }
    public int Myproperty3 { get; set; }
}
```
Şeklinde yada  
```C#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci og = new Ogrenci();
        og.Myproperty1 = 10;
        og.Myproperty2 = 20;
        og.Myproperty3 = 30;

    }
}

class Ogrenci
{
    public int Myproperty1 { get; set; }
    public int Myproperty2 { get; set; }
    public int Myproperty3 { get; set; }
}
```
Şeklinde property'e ilk değerini verebiliriz.  



### Indexer
Nesneye indexer özelliği kazandıran, property ile aynı özelliklere sahip olan bir yağıdır.
```
erişimBelirleyicisi geriDönüşDeğeri this[]
{
    get{    }
    set{    }
}
```
Örnek:
```C#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci ogrnci = new Ogrenci();
        ogrnci[1] = 2;
        ogrnci[2] = 4;

        Console.WriteLine(ogrnci[1]);
        Console.WriteLine(ogrnci[2]);
    }
}

class Ogrenci
{
    public int this[int x]
    {
        get
        {
            return x;
        }
        set
        {
            x = value;
        }
    }
}
```
Çıktı:
```
1
2
```

### This Keyword


This keywordü 3 farklı amaç ile kullanılır. Bunlar; Sınıf nesnesini temsil etme, Aynı isimden field ile metod parametrelerini ayırmak için, Bir Constructer'dan başka bir constructer'ı çağırmak için kullanılır.  
Örnek:
```C#
class Ogrenci
{
    public void Yaz()
    {
        this.MerhabaYaz();
    }
    public void MerhabaYaz()
    {
        Console.WriteLine("Merhaba");
    }
}
```
Burada this keywordü class'dan üretilmiş nesneyi temsil eder.  
Örnek:
```C#
class Ogrenci
{
    public string yazı = "Merhaba";
    
    public void EkranaYAz(string yazı)
    {
        Console.WriteLine(this.yazı);
    }
}
```
Burada ise this keywordü aynı isimlerde olan yazı fieldi ile metod içerisindeki yazı parametresini birbirinden ayırdı. Yani kodda field olan yazı değerini kullandı.

# Nesne Kavramı
Nesneye bir veri bütünü diyebiliriz. Mesela bir pervaneyi nesne olarak düşünelim. 
Bu nesnenin verileri yani özellikleri; kaç volt olduğu, kaç pervanesi olduğu, dönme hızı, yapıldığı malzeme vb. bunlar nesnenin özellikleridir.
Bir nesne örneği daha verelim. Bu nesne öğrenci olsun. Öğrenci nesnesinin elemanları; Adı, soyadı, sınıfı, numarası, cinsiyeti vb. dir. 
Ama bu elemanlara öğrencini saatinin rengi örneğini veremeyiz, çünkü her öğrencinin saati olmak zorunda değildir. 
Kısaca bir nesneyi tanımlarken nesnenin özelliklerini ortak şekilde belirlemeliyiz.
Bir nesneyi oluşturmak için new operatörünü kullanılır. `new nesnetipi()` şeklinde kullanılır. 
Bu işlemi yaparak ramdaki heap bölgesinde bir nesne tanımladık. 
Peki bu nesne nasıl erişim sağlayacağız? İşte tam bunun için stack bölgesinde aynı tipte referans türü bir değişken oluşturup atama işlemi gerçekleştiriyoruz. 
Bu işlem `nesneTipi değişkenAdı = new NesneTipi();` şeklinde tanımlanır. 
Burada = operatörü referans türü değerlerde kullanıldığı için atama operatörü depil , işaret etme , referans etme operatörü olarak adlandırılır.  
#### Target_Typed New Expressions
Nesne oluştururken referans direk atanıyor ise C# hangini nesne tipinin oluşturacağını anlamaktadır. 
Yani `NesneTipi nesneAdı = new NesneTipi()` yerine `NesnteTipi NesneAdı = new()` şeklindede nesne tanımlayabiliriz.
Bu özelliği kullanabilmek için en az .Net 5.0'ı kullanmalıyız.  

#### Referans
Referans ram'ın stack bölgesinde tanımlanıp, heap bölgesindeki nesneleri işaret eden bir tipdir.  
Örnek olarak `SınıfIsmi nesneAdı = new SınıfIsmi();` şeklinde referans tipi olan bir nesne oluşumunu örnek verelim. 
Burada `SınıfIsmi nesneAdı` kodu ile stack bölgesinde nesneAdı isminde bir referans noktası oluşturduk, `new SınıfIsmi` kodu ile ise heap bölgesinde 
`SınıfIsmi` cinsinde bir nesne oluşturduk. `=` ile stack bölgesindeki değişkeni, heap bölgesindeki nesneye işaretliyor, referans ediyor. 

#### Shallow copy

Kısaca bir nesneyi birden fazla referansın işaretlemesidir.   
Örnek:  
```C#
class Program
{
    static void Main(string[] args)
    {
        Myclass m1 = new Myclass();
        Myclass m2 = m1;
    }
}

class Myclass
{

}
```
Burada bir nesne tanımlıyoruz ve m1 ile referans gösteriyoruz. Daha sonra `Myclass m2 = m1;` m1'in gösterdiği aynı nesneyi m2 ile referans gösteriyoruz.
Yani ortada 1 adet nesne bulunmakta ve o nesneyi referans gösteren 2 adet değişken bulunmakta. Bunlardan birinde bir değişiklik olduğunda aynı nesneyi referans 
gösterdiğinden dolayı diğer nesnede de aynı değişiklik oluşur. Bu olaya shallow copy denir.  





## Erişilebilirlik
Sınıfları tanımlarken erişim belirleyiciler ile bu sınıflara nasıl ve hangi metotlarla
erişebileceğimizi tanımlarız. Erişim belirleyiciler;
#### Public :
Kısıtlama olmaksızın tanımlanan sınıfa erişim sağlar.  
`public class Daire { }`
#### Partial:
Projelerde yer alan büyük sınıfları parçalara ayırıp daha sonra
birleştirilmesini sağlar.  
`partial class Daire { }`
#### Sealed:
Kendisinden nesne türetilip, ancak kalıtımının bir başka sınıfa
aktarılmamasını sağlar. Bu özelliği ile Abstract erişim belirleyicisinin tam tersi
yönünde hareket eder.  
`sealed class Daire { }`
#### Abstract:
Sınıfların kendisinden kalıtım alınmasına izin verir fakat nesne
türetilmesine izin vermez. Bu erişim belirleyiciye sahip sınıfların abstract
metotları kalıtım yoluyla sınıflara aktarıldıklarında override edilerek
kullanılması gerekir.  
`abstract class Daire { }`
#### Internal:
Birlikte olduğu assembly içerisindeki sınıflar tarafından
kullanılabilirler.  
`internal class Daire { }`
#### Static:
Kendisine ait bir nesne üretilmeden içerisindeki metotların
kullanılmasını sağlar. Static erişim belirleyicisine sahip sınıfların içerisinde
tanımlanan metotlar ve değişkenler static olarak tanımlanmak zorundadırlar.

## Encapsulation (kapsülleme)

Kapsülleme nesnelerimizde ki alanları(field) kontrollü bir şekilde dışarıya açıp kapatmamıza yarayan bir yapıdır. 
Nesnelerin yanlış kullanımı önlemek için erişim kısıtlaması uygular.  
Kapsülleme 2 şekilde ugulanır. 
1. Metod yardımı ile
2. Property yardımı ile

Örnek:  
```C#
class Myclass
{
    private int x;
    // Göndereceğimiz veriyi burada kontrol ediyoruz.
    public int XGet()
    {
        return this.x; 
    }
    
    // Dışarıdan alacağımız veriyi buradan kontrol ediyoruz.
    public void XSet(int value)
    {
        this.x = value;
    }
}
```
Kodda metod yardımı ile bir kapsülleme yaptık. Bu şekilde dışarıdan alınan veriyi ve dışarıya verdiğimiz veriyi kontrol edebiliriz.
Bu yöntem eski bir yöntemdir, şimdi property ile nasıl yapılıyormuş ona bakalım.

```C#
class Myclass
{
    private int _x;

    public int X
    {
        get { return _x; }
        set { _x = value; }
    }
}
```
Bu da property yardımı ile oluşturduğumuz kapsülleme örneğidir.


## Records
Record yapısını öğrenmemiz için önce **Init-Only Properties** özelliğini bilmemiz lazım.
#### Init-Only Properties
Bu özellik bir nesnenin properylerine ilk değerinin verilmesi ve bu değerin değiştirilmememisini garanti altına alan bir özelliktir.
Bu özellik read-only bir property yapısına benzemekte ama read-only bir property özelliğine sahip bir nesneyi oluştururken propertylerine ilk değerini
veremezsin. Nesneyi oluştururken propertylere ilk değerini verebilmemiz için Init-Only Properties özelliğini kullanmalıyız. Yani Init-Only Properties,
hem property'i read-only yapıyor, hemde nesneyi oluştururken propertylere ilk değer vermemizi sağlıyor.  
Örnek:  
```C#
class Program
{
    static void Main(string[] args)
    {
        Film film = new Film()
        {
            adı = "Atların intikamı",
            imdb = 1
        };
            
    }
}


class Film
{
    public string adı { get; init; }
    public int imdb { get; init; }
}
```
Yukarıdaki Init-Only Properties örneğidir. Gördüğünüz gibi init özelliği sayesinde  property'e değeri nesneyi tanımlarken verdik ve property'ler read-only oldu.

Ayrıca readoly olarak tanımlanmış bir property'de initi kullanabiliriz.  
Örnek:  
```C#
class Film
{
    private readonly string adı;
    private readonly int imdb;
        
    public string Adı
    {
        get { return adı; }
        init { adı = value; }
    }

    public int Imdb
    {
        get { return imdb; }
        init { imdb = value; }
    }
}
```
readonly olarak tanımlanmış bir property'i init sayesinde nesne oluştururken ilk değer almasını sağlayabilirliz.  

Oluşturduğumuz bir nesnenin bütün değerleri bütünsel olarak değişmemesini istiyorsak records yapısını kullanmalıyız. Record bir nesnenin tamamen sabit ve değişmez olmasını
sağlayan ve bunu güvence altına alan bir yapıdır. Record sayesinde bu yapının nesnesinden ziyade sabitlediği değerleri ön plana çıkıyor. 
Class'larda tanımlanan bütün yapıları record'larda da tanımlayabiliriz.  

Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        MyRecord x1 = new MyRecord()
        {
            MyProb = 5
        };
        MyRecord x2 = new MyRecord()
        {
            MyProb = 5
        };
            
        Film x3 = new Film()
        {
            MyProb = 5
        };
        Film x4 = new Film()
        {
            MyProb = 5
        };

        Console.WriteLine(x1 == x2);
        Console.WriteLine(x3 == x4);

    }
}

record MyRecord
{
    public int MyProb { get; set; }
}
    
class Film
{
    public int MyProb { get; set; }
}
```
Çıktı:  
```
True
False
```
Yukarıda records ve classın farkını gösteren bir kod yazdık. Burada classtan üretin ve içindeki değerler aynı olan nesneleri karşılaştırdığımızda nesne ön planda olduğu için
false değeri döner, record'dan üretilen iki nesneyi karşılaştırdığımızda ise nesneler ön planda olduğu için true değeri dönecektir. Yani kısaca record nesneyi değer
ön planlı yapmaktadır. Record'u read-only ve oluşturulduğu anda tanımlamak istiyorsak init kullanmalıyız. Çünkü record kullanıyorsan değeri ön planda tuttarız, değer ön planlı
bir yapı kullanılıysan çoğunlukla değerlerinin değişmesini istemezsin bundan dolayı da init kullanırız.  
Örnek kullanım:  
```c#
class Program
{
    static void Main(string[] args)
    {
        MyRecord x1 = new MyRecord()
        {
            MyProb = 5,
            MyProb1 = 4
        };

    }
}

record MyRecord
{
    public int MyProb { get; init; }
    public int MyProb1 { get; init; }
}
```
Bu işlemlerin hepsini classla da yapılabilir ama çok property bulunan, salt okunur clastan ürettiğimiz bir nesnesin bir özelliği farklı bir nesne oluşturmak isetersek
bütün propertylere tekrardan değer vererek yeni bir nesne oluşturmamız gerekecektir. Çok property bulunan bir clastan böyle bir nesne oluşturmamız çok can sıkıcı ve zorlayıcı
olacaktır. İşte tam bu durumda class yerine record kullanılanmamız daha uygun olacaktır. Recordun with özeliği sayesinde bu durumu kolay bir şekilde halledebiliriz.  
Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        Film f1 = new Film()
        {
            isim = "cehennem melekleri",
            saat = "12.00",
            salonNo = 2
        };

        Film f2 = f1 with { salonNo = 4 };

        Console.WriteLine(f2.salonNo);

    }
}

record Film
{
    public string isim { get; init; }
    public string saat { get; init; }
    public int salonNo { get; init; }
}
```
Çıktı:
```
4
```
Burada with sayesinde salonNo'sunu değiştirdiğimiz bir kopyayı oluşturduk. Record'un bu özelliği bize baya bir avantaj sağladı.  
Bunu class ile yapmanın daha zahmetili bir yolu daha bulunmaktadır.  
Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        Film f1 = new Film()
        {
            isim = "cehennem melekleri",
            saat = "12.00",
            salonNo = 2
        };
        Film f2 = f1.With(4);
            

        Console.WriteLine(f2.salonNo);

    }
}

class Film
{
    public string isim { get; set; }
    public string saat { get; init; }
    public int salonNo { get; init; }

    public Film With(int salonNO)
    {
        return new Film()
        {
            isim = this.isim,
            saat = this.saat,
            salonNo = salonNO

        };
    }
}
```
Bu yöntem record'a göre çok daha karmaşık ve zordur. 


## Positional Record

Record içerisindeki constructor, deconstructor gibi özel tanımlı metodların kullanımlarını  özelleştirerek kullanılmasını sağlamaktadır. 

```c#
record MyRecord(int x, int y)
{

}
```
Positional record bu şekilde tanımlanır. Bu tanımlanımlama sonucu hem constructor hemde deconstructor oluşturmuş olduk.

Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        // Contructor'u tetikledik.
        MyRecord m = new MyRecord(1, 2);

        // Decontrocturu kullandık.
        var (a, b) = m;

    }
}

record MyRecord(int x, int y)
{
        
}
```
Yukarıda Positional record kullandığımızdan otomarik olarak x ve y propertyleri init olarak oluştu. Daha sonra nesne yaratırken parametre vererek
contructor özelliğini kullandık. Hemen altında ise decontructor kullanarak nesne oluştururken verdiğimiz x ve y değerlerini a ve b değişkenlerine atadık.

Bu recordlarda bulunan constructorlar overloading edilebilirler. Ama Positional recordın yarattığı constructoru tetiklemek zorunludur.  

Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        // Contructor'u tetikledik.
        MyRecord m = new MyRecord();

        // Decontrocturu kullandık.
        var (x, y) = m;

    }
}

record MyRecord(int x, int y)
{
    public MyRecord() : this(3, 4)
    {
            
    }
        
}
```

## Adlandırma kuralları
Sınıfları ve Metodları isimlendirirken büyük harfle başlanır, nesnlerini isimlendirirken küçük harf ile başlanır. Ama unutmayın ki record'an üretilmiş bir yapı bir nesnedir.
Boşluk kullanılmaz onun yerine _ karakteri kullanılır.  
Özel karakterler kullanılmaz.  
Rakam ile başlanılmaz.  
Programlama diline ait keyword(while, for, if vb.) kullanılmaz.  
En fazla 255 karakterden oluşur.


## Kurucu Metodlar(Constructors)
Constructors bir nesne tanımladığımızda nesneyi tanımladığımız sınıfta bulunan ve çalışan ilk metoddur.  
`MyClass m = new MyClass();` Nesne oluştururken burada parantezin görevi Constructors'u tetiklemektir.  
Kurucu metodlar herhangi bir sınıftan nesne tanımladığımızda belirlediğimiz özelliklerle otomatik olarak çalışan bir yapıdır.
Kurucu metodları isteğimize göre sınıf içerisinde tanımlayıp tanımlamamız bize kalmıştır. 
Sınıftan nesneyi türeddiğimiz anda kurucu metod çalışır. Kurucu metod ismi sınıf ismi ile aynı olmak zorundadır.
Herhangi bir geri dönüş değeri olamaz, bildirilemez ve erişim belirleyicisi public olmak zorundadır. Constructors parametre alabilen bir yapıya sahiptir.


### Varsayılan Kurucu Metod(Default Constructor)
Bir sınıf içerisinde bir kurucu metod tanımlayalım, bu kurucu metodun içerisindeki bir özelliğe kurucu metod içerisinde değer atayalım. İşte bu olaya (Default)Varsayılan kurucu metod denir.  
Örnek:
```C#
namespace ConsoleApp1
{
    class Program
    {

        static void Main(string[] args)
        {
            Deniz deniz1 = new Deniz();
            Console.WriteLine(deniz1.renk);
        }

    }

    class Deniz
    {
        public string renk { get; set; }

        public Deniz()
        {
            renk = "MAVİ";
            Console.WriteLine("Denizin rengi {0}dir", renk);
        }
    }
}
```
Çıktı:
```
Denizin rengi MAVİdir
MAVİ
```
Yukarıda gördüğünüz gibi renk özelliğini Deniz sınıfında, Deniz kurucu metodunun içerisinde varsayılan olarak mavi yaptık. 
Bu olaya varsayılan kurucu metod denir.

### Aşırı Yüklenmiş Kurucu Metod(Constructor Overloading)
Aşırı yüklenmiş kurucu metod kısaca bir sınıf içerisinden aynı isimde birden fazla kurucu metodun tanımlanma olayıdır. 
Nesne tanımlarken hangi kurucu metodu kullanacağımız verdiğimiz parametreye bağlıdır.  
Örnek:
```C#
namespace ConsoleApp1
{
    class Program
    {

        static void Main(string[] args)
        {
            Deniz deniz1 = new Deniz();
            Console.WriteLine(deniz1.Renk);

            Deniz deniz2 = new Deniz(33);
            Console.WriteLine(deniz2.Derinlik);

            Deniz deniz3 = new Deniz("Temiz");
            Console.WriteLine(deniz3.Durum);

        }

    }

    class Deniz
    {
        public string Renk { get; set; }
        public double Derinlik { get; set; }
        public string Durum { get; set; }

        public Deniz()
        {
            Renk = "MAVİ";
            Console.WriteLine("Denizin rengi {0}dir", Renk);
        }

        public Deniz(double derinlik)
        {
            this.Derinlik = derinlik;
        }

        public Deniz(string durum)
        {
            this.Durum = durum;
        }
    }
}
```
Çıktı:
```
Denizin rengi MAVİdir
MAVİ
33
Temiz
```

Gördüğünüz gibi birden fazla kurucu metod tanımladık. Bu kurucu metodların hangisini kullanacağımızı verdiğimiz parametre ile belirledik.
deniz1 nesnesini boş bir parametre vererek renk özelliğini kullandık. 
deniz2 nesnesine double türünde 33 parametresini vererek derinlik özelliğini kullandık. 
Son olarak deniz3 nesnesine string türünden Temiz parametresini vererek durum özelliğini kullandık.

### Constructors metodlarda  this keyword'ü

Constructors metodlarda this keyword'ü, overloading constructors metodlar arası geçiş yapmamıza olanak sağlıyor.  
Örnek:
````c#
class Program
{
    static void Main(string[] args)
    {
        MyClass m = new MyClass(2, 3);
    }
}

class MyClass
{
    public MyClass(int a)
    {
        Console.WriteLine("1. Constructors metod");
    }

    public MyClass(int b, int c) : this(b)
    {
        Console.WriteLine("2. Constructors metod");
    }
}
````
Çıktı:  
```
1. Constructors metod
2. Constructors metod
```
Burada 2 parametreli kurucu metodu çağırdık oda this keyword'ü ile tek parametreli metodu çağırdı. 
This keywordüne parametre olarak metod içersindeki değeri verebiliriz yada kendimiz manuel olarak değer veririz. 
Class içerisindeki field değerlerini veremeyiz çünkü görmüyecektir.

**Not: _Buradaki bütün özellikler Recordlar için de geçerlidir_.**

## Destructor Metod (Yıkıcı Metod)

Oluşturulan bir nesne imha edilirken otomatik olarak çağrılan metoda, destructor metod denir. Sadece classlarda destructor bulunur ve
sadece bir tanedir. Yani destructor metodlarda overload işlemi yapılmaz ve destructor metodlar herhangi bir parametre almaz.  
Bir nesnenin imha edildiği durumlar:
1. Nesne herhangi bir referans tarafından işaretlendirilmemişse,
2. Oluşturulduğu veya kullanıldığı bölüm bitmiş ise, yani birdaha erişilemez halde ise
nesne Garbage Collector tarafından imha edilir.

Destructor ismi class ismi ile aynıdır ve ismin başına `~` işaretini yerleştirmek zorunludur. 
Örnek:  
```c#
class MyClass
{
    ~MyClass()
    {
        Console.WriteLine("Byee");
    }
}
```

## Deconstruct Metodu

Bir sınıftan oluşturulan bir nesnenin belli fieldlarını almak istediğimizde deconstruct metodunu kullanırız. Bu metod sınıf içersinde Deconstruct ismiyle tanımlanmakta
ve nesne üzerinden belirtilen değerleri tuble olarak döndürmemize olanak sağlar.  

Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        MyClass ogrenci = new MyClass()
        {
            isim = "osman",
            yas = 33,
            no = 1212312
        };

        var (x, y) = ogrenci;

        Console.WriteLine($"{x} ve {y}");
    }
}

class MyClass
{
    public string isim { get; set; }
        
    public int yas { get; set; }
        
    public  int no { get; set; }

    public void Deconstruct(out string _x, out int _y)
    {
        _x = isim;
        _y = yas;
    }
        
        
}
```
Geriye herhangi bir değer döndürmediğimiz için void olarak tanımlanır. Deconstruct metodun parametleri out olarak
tanımlanır. out parametrelerin dışarı açılmasını sağlıyordu bu sayede parametreleri dışarı açtık.

## Static Constructor

Bir sınıftan nesne üretilirken ilk tetiklenen "constructor" değil "static constructor" dır. Şimdi construcktor bir sınıftan 
üretilen her nesnede tetiklenen metoddur. "static constructor" ise bir sınıftan üretilen ilk nesne esnasında tetiklenen bir metoddur ve ilk nesne üretimi dışında bir daha tetiklenmez.
Yani birisi her nesne üretildiğinde diğeri ise ilk nesne üretiminde tetiklenir.  
static constructor'larda overloading yapılmaz, parametre almaz, geri dönüş değeri ve erişim belirleyicileri tanımlanmaz. Sınıf ismi ile aynı isme sahiptir.  

Örnek:  
```c#
static void Main(string[] args)
{
    MyClass m1 = new MyClass();

    Console.WriteLine("******************");

    MyClass m2 = new MyClass();
}
}

class MyClass
{

    public MyClass()
    {
        Console.WriteLine("Constructor tetiklendi.");
    }
    static MyClass()
    {
        Console.WriteLine("Static Constructor tetiklendi.");
    }
}
```
Çıktı:  
```
Static Constructor tetiklendi.
Constructor tetiklendi.
******************
Constructor tetiklendi.
```
Gördüğünüz gibi ilk static constructor tetiklendi ve bir kez tetiklendikten sonra birdaha tetiklenmedi.  
Statik contrucktor'un tetiklenmesi için o sınıftan bir nesne oluşturulmalı yada sınıf içerisinde herhangi bir static yapılanmanın tetiklenmesi gerekmektedir.


# Metodlar

Metodlar belli bir işi yapan kod bloğundan oluşur ve bu kod bloğunun bir ismi vardır. Metodlar belli bir işi yapan kodları tekrar tekrar yazmamız yerine, kodu tek seferde yazıp tekrar tekrar kullanmamıza olanak sağlar. Bu bize daha hızlı ve verimli olmamıza olanak sağlar. Farklı sınıflarda yazılmış metodları kullanmamız için o sınıf türünde bir nesne üretmemiz gerekir. Metodlar parametre alıp almayacağı bizim yazdığımız koda bağlıdır. Metodları geriye değer döndüren veya geriye değer döndürmeyen metodlar olarak ikiye ayırabiliriz.  
Metodlar:  
`ErişimBelirleyicisi GeriyeDöndürecekDeğerTÜrü Metodİsmi(Parametreler)  
{
codlar...
}`
şeklinde kullanılır.
## Metod Çağırma

Metodları tanımlı oldukları yerlere göre farkı şekillerde çağırabiliriz. Metodu bulunduğu sınıfta `metodAdı();` şeklinde çağırabiliriz. Eğer metod farklı bir sınıfta ise
o sınıftan nesne üreterek `nensneİsimi.metodİsmi();` şeklinde çağırabiliriz. Ama metodu çağırabilip çağıramayacağımız erişim belirleyiciler ve metodun bulunduğu yere göre değişir. 6 farklı erişim belirleyici bulunmaktadır. Bunlar public, private, static, protected, internal, protectedinternal'dır.

`Public` : Her yerde kullanılabilir, herhangi bir kısıtlaması yoktur.  
`Private` : Başka sınıflarca kullanılamaz. Nesne üretilse dahi erişilemez. Sadece tanımlı olduğu sınıfta kullanılır.  
`Protected` : Tanımlı olduğu sınıfta ve kalıtım ile kullanıldığı sınıfta kullanılabilir.  
`Internal` : Sadece bulunduğu programda(namespace) kullanılabilir.  
`ProtectedInternal` : Bulunduğu projede ve projeden üretilen sınıflarda kullanılabilir.

## Parametre Alan ve Geriye Değer Döndüren Metodlar

Bu tür metodlar dışarıdan bir parametre alır ve geriye aldığı parametreye bağımlı yada bağımsız bir değer döndürürler. Örnek olarak fiyatını verdiğimiz bir ürünün, kdv dahil fiyatını döndüren bir metod yazalım.  
Örnek:
```C#
static void Main(string[] args)
{
    Console.WriteLine(KdvHesapla(100));
}
        
public static double KdvHesapla(double fiyat)
{
    return fiyat + fiyat * 18.0 / 100;
}
```
Çıktı:
```
118
```
Yukarıdaki metodumuzun erişim belirleyicisi public ve geriye döndürdüğü değeri double olarak tanımladık. Bu metodun görevi dışarıdan bir fiyat alarak, onun kdv dahil
fiyatını geri döndürmektir. Bu döndürme işlemini return keyword'ü ile yapmaktadır. Metodun türü double olduğundan geri döndürülen değer türününde double olması beklenir.

## Parametre Almayan ve Geriye Değer Döndüren Metodlar
Bu metodlar dışarıdan bir parametre almaz ama geriye bir değer döndürebilir.  
Örnek:
 ```C#
 static void Main(string[] args)
{
    Console.WriteLine(HarfVer());
}

public static char HarfVer()
{
    Random rastgele = new Random();
    int kod = rastgele.Next(65, 91);
    char karakter = Convert.ToChar(kod);
    return karakter;
}
 ```
Yukarıda parametre almayan ama geriye değer döndüren bir metod tanımladık. Bu metodun görevi çağırıldığında rasgele bir harf üretip geriye döndürmektir.

## Parametre Alan ve Geriye Değer Döndürmeyen Metodlar

Bu tür metodlar bir parametre alır ama geriye değer döndürmezler. Erişim belirleyici olarak `void` ifadesi kullanılır. `void` ifadesi metodun geri dönüş yapmayacağı durumlarda kullanılır. Bu tür metodlar genelde veri tabanına işlem yaparken yada ekrana yazı yazdırırken kullanılır.  
Örnek:
```C#
static void Main(string[] args)
{
    int yıl;
    Console.Write("Doğum yılınızı giriniz.");

    yıl = Convert.ToInt32(Console.ReadLine());
    YasVer(yıl);
}

public static void YasVer(int dogumYılı)
{
    Console.WriteLine(2021 - dogumYılı + "  yaşındasınız.");
}
```
Bu kod kullanıcıdan doğum yılını alıyor ver ekrana yaşını yazdırıyor. Kullandığımız metod bir parametre almaktadır ama geriye bir değer döndürmemektedir.

## Parametre Almayan ve Geriye Değer Döndürmeyen Metodlar

Bu metod türü geriye bir değer döndürmez ve parametre almaz. Genellikle uzun bir uyarı mesajı vb. göndermek için kullanılır.  
Örnek:
```C#
static void Main(string[] args)
{
    int yas;
    Console.Write("Yasınızı giriniz:");

    yas = Convert.ToInt32(Console.ReadLine());

    if (yas < 18)
    {
        Mesaj();
    }
}

public static void Mesaj()
{
    Console.WriteLine("Yaşınız 18'den küçüktür, giriş yapamazsınız!");
}
```
Bu program kullanıcıdan yaşı alır ve 18'den küçük ise ekrana bir mesaj yazar. Kullandığımız metod parametre almaz ve geriye bir değer döndürmez.

## Default Parametre Tanımlı Metodlar

Metod tanımlarken parametrelerine default değer verebiliriz.  
Örnek:
```C#
static void Main(string[] args)
{
    renkYaz("beyaz");
}

public static void renkYaz(string kapı, string kolu = "siyah")
{
    Console.WriteLine($"Kapının rengi {kapı}, kolunun rengi {kolu}.");
}
```
Çıktı:
```
Kapının rengi beyaz, kolunun rengi siyah.
```

Default olarak tanımladığımız parametre yerine değer vermediğimiz sürece varsayılan değer kullanılır. Yukarıda kolu parametresinin varsayılan değerini "siyah" olarak tanımladık ve metodu çağırırken bir değer atamadığımız için varsayılan değer kullanıldı.  
Metoda default değer atarken bu değerlerin en sağda olması zorunludur, aksi taktirde hata alırısınız.

## Ref and out keyword

```C#
class Program
{
    static void Main(string[] args)
    {
        short num1 = 20;
        short num2 = 40;

        Console.WriteLine(Total(num1, num2));
        Console.WriteLine(num2);
        Console.ReadLine();
    }

    static int Total(int num1, int num2)
    {
        num2 = 100;
        return num1 + num2;
    }
}
```
Sizce yukarıdaki programda num2'nin sonucu ne olur? Ben söylim 40. Ne kadar Total metodunun içinde num2 değişkeni 100 olarak değiştirilsede dışarıdaki yani globaldaki num2 değişkeni değişmez çünkü bunlar birbirinden farklı değişkenlerdir. Eğer dışarıdaki değişkeni metodun içinde değiştirmek istiyorsak aşağıdaki gibi ref veya out keywordünü kullanmalıyız . ref ve out aynı işlemi yaparlar farkları ref kullandığımız değişkene başta bir değer atanmak zorundadır yoksa program hata verir. out kullandığımızda ise değişkeni metodun içinde bir kez set etmeliyiz yani değiştirmeliyiz aksi taktirde program hata verecektir.

```C#
class Program
{
    static void Main(string[] args)
    {
        int num1 = 20;
        int num2 = 40;

        Console.WriteLine(Total(num1, ref num2));
        Console.WriteLine(num2);
        Console.ReadLine();
    }

    static int Total(int num1, ref int num2)
    {
        num2 = 100;
        return num1 + num2;
    }
}
```

## Params Keyword

Metot kullanırken istediğimiz kadar parametre almak için params keywordünü kullanırız. Params kısaca dışarıdan girilen bütün parametreleri bir dizi içerisinde metodun içine aktarıyor. Aşağıdaki Sum() metodu dizi içerisindeki bütün sayıları toplayan hazır bir metotdur.
```C#
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine(Topla(3,2,4,5,3,2));
        Console.ReadLine();
    }

    static int Topla(params int [] toplam)
    {
        return toplam.Sum();
    }
}
```

## Static Metodlar

Static metodlar bulundukları sınıflarda nesne üretilmeden kullanılabilirler ama bulundukları sınıfında static olması ve metodun public erişim belirleyicisi kullanması gerekmektedir.

## Metodlarda Aşırı Yükleme

Bu olay kısaca aynı isimde birden fazla metodun bulunmasıdır. Bu metodların hangisini kullanacağımız verdiğimiz parametreye göre belirlenmektedir.


# Kalıtım (Inheritance)

Bir sınıfa ait özelliklerin başka bir sınıfa aktarılmasına kalıtım denir.
Kalıtım bize kolaylık, performans ve verimlilik sağlar. Inheritancenin amacı aynı özelliklere sahip sınıfların özelliklerini tekrar tekrar
tanımlamaktansa, ortak özelliklere sahip temel bir sınıf oluşturup diğer sınıfların bu temel sınıfı miras almasını sağlamaktır.
Kalıtımda iki sınıf türü bulunur bu sınıflar; temel(base/parent) sınıf ve türetilmiş(derived/child) sınıftır.


## Temel (base/parent) Sınıf ve Türetilmiş (derived/child) Sınıf

Temel sınıf kendinden üretilen sınıflara referans olan ve alanını(field), özelliklerini(property), metodlarını kullandıran sınıf türüdür.
Türetilmiş sınıf ise temel sınıftan türüyen ve bu özellikleri kullanan sınıf türüdür.

Örnek:
```C#
public class Kisi
{
    private string ad;
    private string soyad;
    private double boy;
    private string cinsiyet;

    public string Ad
    {
        get { return ad; }
        set { ad = value; }
    }
    public string Soyad
    {
        get { return soyad; }
        set { soyad = value; }
    }
    public double Boy
    {
        get { return boy; }
        set { boy = value; }
    }
    public string Cinsiyet
    {
        get { return cinsiyet; }
        set { cinsiyet = value; }
    }

    public void BilgiGöster()
    {
        System.Console.WriteLine("Tanımlanan kişinin adı: {0}, soyadı: {1}, boyu: {2}, cinsiyeti: {3}", Ad, Soyad, Boy, Cinsiyet);
    }
}

public class Personel : Kisi
{
    private int personelNo;
    private double maas;
    private string bolum;

    public int PersonelNO { get => personelNo; set => personelNo = value; }
    public double Maas { get => maas; set => maas = value; }
    public string Bolum { get => bolum; set => bolum = value; }
}
```
Miras alma işlemi `class MirasAlanSınıfAdı : MirasAlınacakSınıfAdı` şeklinde `:` operatörü sayesinde gerçekleşir.
Temel sınıftaki yapıların miras alınabilmesi için public erişim belirleyicisi ile tanımlanmış olması gerekir. 
Burada Kişi sınıf temel sınıf, Personel sınıfı ise Kişi sınıfından türetilmiş bir sınıftır. 
Personel sınıf, Kişi sınıfından ad, soyad, boy, cinsiyet özelliklerini kendine katmıştır.
Bunun mantığı her persone aslında bir kişi olduğundan kişinin özelliklerini barındırır.  
Sınıfların dışında record'lar da kendi aralarında kalıtım alabilmektedir. 
Tek bir istisnai durum vardır oda sadece object türü sınıflardan kalıtım almasıdır.
Yani record'ların kalıtım aldığı tek sınıf türü object türü sınıflardır.

Bir class yanlızca tek base class'tan türeyebilir, yanı birden fazla class'tan türeyemez ve sadece bir adet base class'ı olabilir.
Örnek:  

```c#
class Program
{
    static void Main(string[] args)
    {
        C c = new C();
        c.K = 4;
    }
}

class A
{
    public int a;
    public int K { get; set; }
}

class B : A
{
    public int S { get; set; }
}

class C : B
{
        
}
```

Yukarıda C sınıfı B'den, B sınıfı A'dan kalıtım almaktadır. Bunun sonucundan C sınıfından tanımlanmış bir nesne A sınıfındaki özellikleride miras alır.  
Burada nesne yapısını oluştururken ilk önce A clasındaki nesneyi üretir, sonra B ve en son olarak C yapısındaki nesneyi üretir.

Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        C c = new C();
    }
}

class A
{
    public A()
    {
        Console.WriteLine("{0} Constructor'u çalıştı.", nameof(A));
    }
        
}

class B : A
{
    public B()
    {
        Console.WriteLine("{0} Constructor'u çalıştı.", nameof(B));
    }
}

class C : B
{
    public C()
    {
        Console.WriteLine("{0} Constructor'u çalıştı.", nameof(C));
    }
}
```
Çıktı:  
```
A Constructor'u çalıştı.
B Constructor'u çalıştı.
C Constructoru'u çalıştı.
```
Gördüğünüz gibi önce A class'ı sonra B en son ise C class'ının constructor'u çalıştı.  
Buradaki nameof() kodu, bulunduğu sınıfın ismini vermektedir.  

## Temel(base) Class Constructor'ını Çağırma

Kalıtımla türetilen sınıfın kurucu metodudan, temel sınıfın kurucu metoduna erişim sağlanabilir. Bu erişimi sağlayabilmek için `base()` keywordünü kullanmalıyız.

`base()` keywordünü base classının constructor metodu parametre aldığında kullanırız,
parametresiz constructor metodu class miras alındığında zaten otomatik olarak çağrılmaktadır.  
Yani `base()` keywordünü constructor metoda parametre vermek için kullanırız ve base classta birden
fazla constructor metod var ise hangisinin tetikleneceğini `base()` keywordü sayesinde seçeriz.  
Base class'ın constructor'u parametre alıyor ise derived(türetilmiş) clasın constructor'ünde `base()` keyword'ü ile parametre vermek zorundayız.
Ayrıca derived(türetilmiş) class'tan base class'daki public olan verilere ulaşmak için `base` keywordünü kullanabiliriz,
ve son olara derived(türetilmiş) class verileri miras aldığından aynı verilere `this` keywordü ile de ulaşabiliriz ama bu keywordleri kullanmak zorunda değiliz. 
Yani bunları kullanmadan da verilere ulaşabiliriz.

Örnek:
```C#
class Program
{
    static void Main(string[] args)
    {
        Ogrenci ogr1 = new Ogrenci();
        Ogrenci ogr2 = new Ogrenci("Parametre alan temel sınıf kucuru metodu çalıştı.");

        Console.ReadLine();
    }
}

public class Kisi
{
    public int x { get; set; }
    public Kisi()
    {
        Console.WriteLine("Temel sınıf kurucu metodu çalıştı.");
    }

    public Kisi(string parametre)
    {
        Console.WriteLine(parametre);
    }

}

public class Ogrenci : Kisi
{
    public Ogrenci() : base() { }
    public Ogrenci(string parametre) : base(parametre) { }
    base.x = 20;
}
```
Çıktı:
```
Temel sınıf kurucu metodu çalıştı.
Parametre alan temel sınıf kucuru metodu çalıştı.
```  
Burada ogr1 adında Ogrenci sınıfına ait bir nesne tanımladık. 
Nesneyi tanımlarken parametre vermediğimiz için Ogrenci sınıfının `public Ogrenci() : base() { }` kurucu metodu çalıştı
ve bu kurucu metod `base() { }` ile Kişi sınıfının kurucu metodunu yani parametresiz olan `public Kisi()` metodunu kalıtım aldı.

Not: C#'da bütün sınıflar `Object` sınıfından kalıtım almaktadır. Yani `Object` sınıfından türetilmektedir. 
Başka sınıflardan kalıtım alan sınıflar ise dolaylı yoldan `Object` sınıfının özellikleri alır. 
Equals, GetType, ToString, GetHashCode metodları buradan gelmektedir.

### Name Hiding
Name Hiding durumu base class'tan kalıtım alan herhangi bir class'ın aynı isimde üyelere sahip olmasıdır.  
Örnek:  
```c#
class MyClass1
{
    public int A { get; set; }
}

class MyClass2 : MyClass1
{
    public int A { get; set; }
}
```

Böyle bir durumda A property'sine ulaşmak istediğimizde base class'daki property saklanacak, onun yerine derived(türemiş) sınıftaki property'e ulaşacağız.  
Bu bir durumda derleyci sadece bir uyarı mesajı verecektir.
Geçmiş yıllarda Name Hiding yaparken new operatörünü kullanmak zorunluydu ama artık böyle bir zorunluluk yok.  
Örnek:  

```c#
class MyClass1
{
    public int A { get; set; }
}

class MyClass2 : MyClass1
{
    public new int A { get; set; }
}
```
new ile işaretlediğimiz durumda bir uyarı mesajı almıyacağız.

## Nesneleri Birbirine Atamak

Bir sınıftan üretilen bir nesne, aynı sınıftan üretilen başka bir nesneye atanabilir. Bu işlem gerçekleştiğinde birinin bütün özellikleri diğerine atanır.  
Örnek:
```C#
static void Main(string[] args)
{
    Personel per1 = new Personel();

    per1.Bolum = "Muhasebe";
    per1.Maas = 12412;
    per1.PersonelNO = 234;
    per1.Ad = "Osman";
    per1.Soyad = "Kara";

    Personel per2 = new Personel();
    per2 = per1;

    Console.WriteLine($"isim: {per2.Ad}, Soyisim: {per2.Soyad}, personel no: {per2.PersonelNO}, maaş: {per2.Maas}");

    Console.ReadLine();
}
}
public class Kisi
{
    private string ad;
    private string soyad;
    private double boy;
    private string cinsiyet;

    public string Ad
    {
        get { return ad; }
        set { ad = value; }
    }
    public string Soyad
    {
        get { return soyad; }
        set { soyad = value; }
    }
    public double Boy
    {
        get { return boy; }
        set { boy = value; }
    }
    public string Cinsiyet
    {
        get { return cinsiyet; }
        set { cinsiyet = value; }
    }

    public void BilgiGöster()
    {
        System.Console.WriteLine("Tanımlanan kişinin adı: {0}, soyadı: {1}, boyu: {2}, cinsiyeti: {3}", Ad, Soyad, Boy, Cinsiyet);
    }
}

public class Personel : Kisi
{
    private int personelNo;
    private double maas;
    private string bolum;

    public int PersonelNO { get => personelNo; set => personelNo = value; }
    public double Maas { get => maas; set => maas = value; }
    public string Bolum { get => bolum; set => bolum = value; }
}
```
Çıktı:
```
isim: Osman, Soyisim: Kara, personel no: 234, maaş: 12412
```

Gördüğünüz gibi per1'i per2'ye atadığımız zaman bütün özelliklerde atanmış oldu.

## New Metodu

Bu metodun görevi bir nesne oluşturarak sınıfın özelliklerini nesneye aktarmaktır.  `SınıfAdı nesneAdı = new SınıfAdı();` şeklinde kullanılır.

## Virtual Metodu

Temel(base) sınıfın içerisinde tanımlanan sanal metodlardır. 
Sanal metod sayesinde temel sınıftan miras aldığımız metodları iptal edebilir, türetilmiş sınıfta değiştirebiliriz. 
Bunu yapabilmek için temel sınıftaki değiştirmek istediğimiz metodu virtual olarak tanımlayıp  virtual metodu sayesinde sanal metodu iptal edebiliriz.

## Override Metodu

Temel sınıfta tanımlanmış sanal elemanı, türetilmiş sınıfta düzenlenip tekrar kullanılmasını sağlayan bir metoddur.
Kullanılması için türetilmiş sınıftaki elemanın aynı isimle kullanılması ve override keyword ile tanımlanması gerekir.
Bu yöntemi miras aldığımız sınıftaki bir elemanı iptal etmek ve değiştirmek istediğimizde kullanırız. 
Override metodunu kullandığımızda temel sınıftaki eleman devre dışı kalır, bu metodu tekrar aktif edebilmemiz için base keywordünü kullanmalıyız.

Örnek:
```C#
class Program
{
    static void Main(string[] args)
    {
        Türetilmis yaz = new Türetilmis();
        yaz.EkranaYaz();
        Console.ReadLine();
    }
}

public class Temel
{
    public virtual void EkranaYaz(string sıralama)
    {
        Console.WriteLine("{0}. Base sınıftaki sanal metod çalıştı", sıralama);
    }

    // bu metodu main metodundaki yaz.EkranaYaz(); kodunun hata vermemesi için yazdık.
    // bu metod ile aşırı yükleme yapmasaydık yaz.EkranaYaz();'de bir parametre vermek zorunda kalırdık.
    public virtual void EkranaYaz()
    {
        Console.WriteLine("Base sınıftaki sanal metod çalıştı");
    }

}

public class Türetilmis : Temel
{
    public override void EkranaYaz()
    {
        base.EkranaYaz("1");
        Console.WriteLine("Türetilen sınıfdaki override metodu çalıştı.");
        base.EkranaYaz("2");
    }
}
```
Çıktı:
```
1. Base sınıftaki sanal metod çalıştı
Türetilen sınıfdaki override metodu çalıştı.
2. Base sınıftaki sanal metod çalıştı
```
Yukarıda EkranaYaz metodunu override ederek iptal ettik.
Türetilmis sınıfından bir nesne oluşturup Ekrana yaz metodunu çalıştırdığımızda sanal metod değil, override ettiğimiz metod çalıştı.
Daha sonra ovverride metodunu içinde base.EkranaYaz("1"); ile sanal metodu tekrardan çalıştırdık.  


Bir sınıfta override edilen bir eleman, override edilmiş bir şekilde oğul ve torunlarına miras verir.
Örnek2:  

```c#
class Program
{
    static void Main(string[] args)
    {
        Saat s = new Saat();
        s.RenkBilgiVer();
        s.OncekiRenk();
            
        Makas m = new Makas();
        m.RenkBilgiVer();
            
        Kalem k = new Kalem();
        k.RenkBilgiVer();
    }
}

class Esya
{
    public virtual string renk { get; set; } = "kırmızı";

    public void RenkBilgiVer()
    {
        Console.WriteLine($"Benim rengim {renk}");
    }

}

class Saat : Esya
{
    // renk property'sini override ederek tekrardan düzenledik.
    public override string renk { get; set; } = "Beyaz";

    // base keywordü ile temel sınıftaki renk propertysine ulaştık.
    public void OncekiRenk()
    {
        Console.WriteLine($"Menim önceki rengim {base.renk}");
    }
}

class Makas : Saat
{
    // renk property'sini override ederek tekrardan düzenledik.
    public override string renk { get; set; } = "Sarı";
        
}

class Kalem : Makas
{
        
}
```
Çıktı:  
```
Benim rengim Beyaz
Menim önceki rengim kırmızı
Benim rengim Sarı
Benim rengim Sarı
```
Fark ettiğiniz gibi miras aldığı sınıftan bir eleman override edilmmiş ise türetilmiş sınıflara override edilmiş şekilde miras vermektedir.  
Makas sınıfında renk properry'si override edilerek "sarı" olarak değiştirildi, daha sonra kalem sınıfı makas sınıfını miras aldı. Burada kalem sınıfı
renk property'sini override halini yani "sarı" değerini miras almıştır.  

# Polimorfizm
Kısaca bir nesnenin birden fazla referans ile işaretlenebilmesi olayıdır. Bu özellik sayesinde nesne işaretlendiği referansın özelliği kullanır.  
Örnek verecek olursak insan nesnesini ele alalım. Bu nesne hem insan sınıfından referans alabilir hemde memeli sınıfından referans alabilir.
Hangi sınıftan referans alırsa o sınıfın özelliklerini alır.
Yani burada olay insan nesnesinin birden fazla şekilde tarif edilebilmesi, referanslanmasıdır.
Ama bir nesnenin başka bir nesne ile işaretlenebilmesi için ilgili nesne o türden türemiş,
yani aralarında kalıtımsal ilişkinin olması şarttır.

Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        MyClass3 m = new MyClass1();
            
    }
}

class MyClass1 : MyClass2
{
    public void Yaz()
    {
            
    }
}

class MyClass2 : MyClass3
{
    public void Ciz()
    {
            
    }
}
 
class MyClass3
{
    public void Sil()
    {
            
    }
}
```

Gördüğünüz gibi normal şartlarda MyClass1 türündeki nesneyi MyClass3 ile işaretlememiz mümkün değişdir ama MyClass1 MyClass3'ü miras aldığından dolayı
işaretleye/referanslaya biliyoruz. MyClass1, MyClass2 ve MyClass3 classlarını miras aldığınıdan dolayı bu iki clasın bütün memberları MyClass1 nesnesinin
içerisinde bulunmaktadır ama MyClass2 ile işaretlendiğindan dolayı sadece Ciz ve Sil metodlarına erimi vardır, Yaz metouna erişimi bulunmamaktadır.


# Arayüz (Interface)

Interface diğer sınıfları yönlendiren bir kalıptır diyebiliriz.
İçerisinde sadece metod isimleri ve özellikler(property) vardır. Yani sadece member imzaları bulunur.
Bu yapı genelde grup halinde yazılan projelerde kullanılır.
Proje yoneticisi interface içerisinde kullanılacak metod ve özellik kalıplarını tanımlar.
Geriye kalan classları oluşturup içine doldurmaktır.

### Arayüz Tanımlama

`public interface Iisim` şeklinde tanımlanır. 
Interface tanımlarken public erişim belirleyicisi kullanılır ve 
interface isimleri adlandılırken ismin başı I ile başlar bu zorunlu değildir ama gelenek gibi birşeydir.

Örnek:
```C#
public interface IOgrenci
{
    double yas { get; set; }
    string isim { get; set; }
    string soyisim { get; set; }

    int DersNotları(int matematik, int fizik, int kimya);
}
```
### Arayüz Kısıtlamaları

İçerisindeki memberları tanımlarken erişim belirleyici kullanmayız.
Varsayılan olarak public erişim belirleyicisi ile tanımldır.  
Alan(field) yerine özellik tanımlanır.
Kurucu veya yıkıcı metod bulundurmaz.
Arayüzeler sadece arayüzlerden türetilir.
Statik bir yapı bulunamaz.

### Arayüzün Kullanımı

Arayüzü tanımladıktan sonra herhangi bir class'a miras vererek kullanırız. Miras alınan class'ta interface'in memberları tanımlı olması zorunludur.  

Örnek:  

```c#
public interface IOgrenci
{
    double yas { get; set; }
    string isim { get; set; }
    string soyisim { get; set; }

    int DersNotları(int matematik, int fizik, int kimya);
}

public class A5 : IOgrenci 
{
    public double yas { get; set; }
    public string isim { get; set; }
    public string soyisim { get; set; }
        
    public int DersNotları(int matematik, int fizik, int kimya)
    {
        Console.WriteLine("Hello");
        return 0;
    }
}
```

_Bir class birden fazla classtan kalıtım alamaz amam birden falza Interface'den kalıtım alabiliri._

Bir class iki farklı interface'den aynı imzaya sahip memberi kalıtım aldığında name hiding olayı gerçekleşir. Bu durumdan kurtulmak için
aşağıdaki yöntemi kullanıp sınıf nesnesi ınterface ile referans etmeliyiz, aksi taktirde memberlara erişim sağlayamayız.  

Örnek:  
```c#
static void Main(string[] args)
{
    IA a = new MyClass();
    a.x();
}
}

interface IA
{
    void x();
}

interface IB
{
    void x();
}

class MyClass : IA, IB
{
    void IA.x()
    {
            
    }

    void IB.x()
    {
            
    }
}
```

# Soyut sınıflar (Abstract Class)

Abstract sınıflar sınıf isminin başına abstract keywordü getirilerek tanımlanır.  
Örnek:  `public abstract class Tur`  

Abstract metodlar tanımlandığı sınıfta sadece metod imzasını alır, yani metodun gövdesi bulunmaz ve herhangi bir işlem yapmaz. İşlemler miras alındığı
class içerisinde uygulanır.
Miras aldığı sınıfta ise metodun override ile tanımlanması gerekmektedir. Aynı durum propertyler için de geçerilidir.  
Abstract metodlar ve propertyler virtual bir yapıya sahiptir.
Abstract metodlar ve propertyler tanımlanması için sınıfında abstract olması gerekmektedir. 
Abstract sınıflarda abstract olmayan metod ve propertyler bulunabilir. 
Abstract sınıflardan nesne üretilemez. 
Statcic metodlar abstract olarka tanımlanamazlar.  

Abstract classlar yapı olarak Interface'e benzemektedir. Tek farkı Interface'de tanımlanan bütün imzalar miras alındığı sınıfta tanımlanmak
zorundayken, abstract'a abstract olarak tanımlanmayan metod ve özellikler miras alınırken kullanılmak zorunda değildir ama Abstract olarak
tanımlanan metod ve propertyler mirass alındığı sınıfta kullanılmak zorundadır. Abstract olarak tanımlanan metod ve propertylerin içi boştur
yani sadece imza tanımlanır. Abstract classlar static olarak tanımlanamazlar ve kendilerinden nesne üretilemez. Abstract metodlar public olarak
tanımlanır.


Örnek:
```c#
class Program
{
    static void Main(string[] args)
    {
        Telefon t = new Telefon();
        t.BilgiVer();
    }
}

public abstract class ElektronikEsya
{
    public abstract int fiyat { get; set; }
    public abstract string marka { get; set; }
    public abstract string renk { get; set; }

    public abstract void BilgiVer();

}

public class Telefon : ElektronikEsya
{
    public override int fiyat { get; set; } = 100;
    public override string marka { get; set; } = "samsung";
    public override string renk { get; set; } = "siyah";
    public override void BilgiVer()
    {
        Console.WriteLine($"fiyat: {fiyat}TL,  marka: {marka},  renk: {renk}");
    }
}
```

Çıktı:  
```
fiyat: 100TL,  marka: samsung,  renk: siyah
```

Abstract'lar Interface benzemektedirler iksi de yapılarını miras verdikleri sınıflara zorla kullandırmaktadırlar ama aralarında fark ise;  
Interface bütün memberlarını kullandırırken, Abstract sadece abstract olarak tanımlana memberların kullanımını zorunlu kılıyor.


### Sealed Class (Mühürleme)

Kısaca bir classın başka classlarca miras alınmasını engellemek için kullanılır.  
```public sealed class ClassAdı``` Şeklinde tanımlanır. 





# Generic Class
Generic sınıfları kullanarak birçok sınıftan tasarruf edebiliriz. Yani generic sınıf birçok sınfın yaptığı işi tek başına yapabilir.  

Örnek:  
```C#
class Program
{
    static void Main(string[] args)
    {
        MyClass<string> t = new MyClass<string>();
        t.veriler = "merhaba";
    }
}

class MyClass<T>
{
    public T veriler { get; set; }
}
```
Yukarıda basit bir örnek bulunmakta. Burada anlatmak istediğim int, string, float vb.. her tür için ayrı bir class oluşturmaktansa sadece bir generic class ile bütün türleri kullanabiliriz. Yukarı main metodunun içerisinde MyClass generic classından hangi türden  nesne oluşturursak veriler property'si o türden olacaktır.  

Bunun yanı sıra vereceğimiz generic classa vereceğimiz parametre türünü kısıtlayabiliriz.  

Örnek:  
```C#
class Program
{
    static void Main(string[] args)
    {
        MyClass<Ogrenci> t = new MyClass<Ogrenci>();
        t.veriler.no = 123;
    }
}

class Ogrenci
{
    public int no { get; set; }
    public string sınıf { get; set; }
}
class MyClass<T> where T : class
{
    public T veriler { get; set; }
}
```
Burada where keywordü ile generic classa parametre olarak sadece class alma şartı koyduk. 

Generic class'lara birden fazla parametre vermemizde mümkündür ama verceğimiz parametrenin ismini belirtmemiz kodun okunabilirliğini artıracaktır.  
```C#
class Program
{
    static void Main(string[] args)
    {
        MyClass<Ogrenci, int> t = new MyClass<Ogrenci, int>();
        t.veriler.no = 123;
        t.not = 88;
    }
}

class Ogrenci
{
    public int no { get; set; }
    public string sınıf { get; set; }
}
class MyClass<TVeriler, TNot> where TVeriler : class where TNot : struct
{
    public TVeriler veriler { get; set; }
    public TNot not { get; set; }
}
```
Yukarıda generic class'da 2 adet parametre tanımladık. Biri TVeriler diğeri ise TNot. Fark ettiğiniz gibi parametreleri isimlendirirken başlarına T ve devamdaki ismi büyük harfle başlattık. Main metodunda generic class'tan nesne oluştururken 2 parametreyide vermek zorundayız aksi taktirde hata alırız. Son olarak yukarıda 2 adet where keywordü kullandık. TVeriler'i class, Tnot'u ise struct olarak tanımladık.  
Not:  Generic class'tan nesne tanımlarken parametre olarak verdiğimiz int değeri struct türü bir yapıdır. 

# DELEGATES

Delegates bir yada birden fazla metodu işaret eden yani referanslayan yapılardır. 
Delegates class hizasında aşağıdaki gibi tanımlanmaktadır.  
```c#
ErişimBelirleyiciAdı delegate metodunGeriDöndüreceğiDegerTipi DelegateAdı(Parametreler);
```
Delegates tanımlarken temsil edeceği metodun geri dönüş değerini ve alacağı parametreleri önceden belirleyip tanımlamalıyız. Yani metodun imzası ile delegate imzası aynı olmalıdır. 

Örnek olarak hemen delegates ile statik bir metodu nasıl çağıracağımıza bakalım.
```c#
class Program
{
    static void Main(string[] args)
    {
        MyDelegate nesne = new MyDelegate(MerhabaYaz);
        nesne();
    }

    public static void MerhabaYaz()
    {
        Console.WriteLine("Merhaba");
    }
}

public delegate void MyDelegate();
```
MyDelegate adında bir degates oluşturduk. Daha sonra MyDelegate türünde bir nesne oluşturduk ve bu nesneyi MerhabaYaz metoduna referans ettik. nesne(); şeklinde metodumuzu çağırdık.  
Eğer metod statik olmasaydı metodu çağırmak için aşağıdaki yöntemi kullanmak zorunda kalırdık.  
```c#
class Program
{
    static void Main(string[] args)
    {
        Program p = new Program();
        MyDelegate nesne = new MyDelegate(p.MerhabaYaz);
        nesne();
    }

    public  void MerhabaYaz()
    {
        Console.WriteLine("Merhaba");
    }
}

public delegate void MyDelegate();
```
Gördüğünüz gibi statik olmayan metodu delegate ile işaretleyebilmek için classtan nesne oluşturduk ve o nesne sayesinde MerhabaYAz metoduna erişim sağlayıp delegate nesnesine referansladık.

Örnek:  
```c#
class Program
{
    static void Main(string[] args)
    {
        // alan metoduna ulaşmak için DaireHesap clasından bir nesne oluşturduk.
        DaireHesap d = new DaireHesap();
        MyDelegate1 nesne1 = new MyDelegate1(d.Alan);
        // VeriAll metodu statik olduğundan direk class üzerinden erişim sağladık.
        MyDelegate2 nesne2 = new MyDelegate2(VeriAl.VeriAll);
        Console.WriteLine(nesne1(nesne2(),3.14f ));
    }

    public  void MerhabaYaz()
    {
        Console.WriteLine("Merhaba");
    }
}

class DaireHesap
{
    public double Alan(double r, double pi)
    {
        return (pi * r * r);
    }
}

class VeriAl
{
    public static double VeriAll()
    {
        Console.WriteLine("Yarı çapı giriniz");
        return Convert.ToDouble(Console.ReadLine());
    }
}

public delegate double MyDelegate1(double x, double y);
public delegate double MyDelegate2();
```
Dikkat ettiyseniz burada delegates imzaları ile metod imzaları aynı, aksi taktirde program hata verecektir.  C# herhangi bir varsayılan değer ataması durumunda delagatenin imzasını dikkate alır.

Örnek:  
```c#
public delegate void MyDelegates();
class Program
{
    static void Main(string[] args)
    {
        // d nesnesini oluşturduk ve nesneye Selamver metodunu referans gösterdik.
        MyDelegates d = SelamVer;
        d();
        Console.WriteLine("******************");
        // d nesnesine bir metod daha ekledik
        d += SaatSor;
        d();
        Console.WriteLine("******************");
        // d nesnesinde SaatSor metodunu çıkardık.
        d -= SaatSor;
        d();

    }
    public static void SelamVer()
    {
        Console.WriteLine("Selam");
    }
    public static void SaatSor()
    {
        Console.WriteLine("Saat kaç");
    }
}
```

Çıktı: 
```
Selam
******************
Selam
Saat kaç
******************
Selam

```
Delegates türünden bir nesne oluştururken `new DelegateAdı(MetodAdı)` şeklinde kullanmak zorunda değiliz. Onun yerine  yukarıdaki gibi sadece MetoAdını Kullanırız.  
Yukarıda MyDelegates türünden oluşturuduğumuz d nesnesine birden fazla metod işaretledik. Bu işaretlemeyi += yardımı ile yaptık. 2. metodu işaretledikten sonra d nesnesini çağırdığımızda nesneye atanan 2 metodun da çalıştığını gördük. Daha sonra -= SaatSor metodu nesneden çıkardık.
