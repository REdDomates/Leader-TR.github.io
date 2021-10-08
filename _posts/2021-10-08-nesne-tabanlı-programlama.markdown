---
layout: post
title:  "Merhabalar!"
date:   2021-10-08 08:36:26 -0400
categories: jekyll update
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
```c#
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
```c#
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
