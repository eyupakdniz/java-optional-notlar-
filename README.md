# java-optional-notlar 
## Optional
- Java 8 ile geldi. son halini java 11 ile aldı
- Null dönmek pahalıdır bundan dolayı `NullPointerException`'ları en aza indirgemek.
- Null kontrolü yapılmasına gerek kalmaz
- Yazılım ve okunabilirlik artar.
- Primitive type optional tarafında kabul edilmez nesne olmak zorunda

## Optional nesne oluşturma
`empty()` => Boş nesne oluşturulur<br>  
`Optional<Integer> maybeInteger = Optional.empty();`<br>
`of()` => Bir nesnenin değeri olduğundan eminisek kullanılır yoksa NullPointerException hatası ile karşılaşılır<br>
`Integer a = null;`<br>
`Optional<Integer> maybeInteger = Optional.of(a);`<br>
`ofNullable()` => null olabilecek nesneler için kullanılır ve hata olarak bir değer atar<br>
`Optional<Integer> maybeInteger = Optional.ofNullable(a);`<br><br>

## Değer kontrolü için kullanılan methodlar
`isPresent()` => not-null durumunu kontrol etmek için kullanılır boolean değer döner<br>
`isEmpty()` => isPresent() tam tersidir.<br>

Not: Bu iki methoddan sonra genellikle `get()` methodu kullanılır.

`ifPresent()` => optional içindeki variable null değil ise çalıştırılacak bloktur. Void methoddur.<br>
`maybeInteger.ifPresent(user -> { /* ...do something with number... */ });`<br>

`ifPresentOrElse()` => java 11 ile geldi. iki tane lambda çalışıtırlabilir.<br>

`maybeInteger.ifPresentOrElse(`<br>
    `   number -> { /* ...do something with number... */ },`<br>
    `   () -> { /* ...do something when no number found... */ }`<br>
`);`<br>


## Diğer kullanılan faydalı methodlar
 `orElse()` => Optional nesnesinde değer yoksa bir şey yaptırız.
 `orElseGet()` => orElse() benzer, null durumunda default değer tanımlamamıza izin verir. Performans açısından daha faydalıdır.
 `orElseThrow()` 
- `orElse()` benzer farkı kendi exception'umuzu oluşturmamızı sağlar. 
- Java 10 ile sunuludu.
- Optional boşsa iki şekilde hata fırlatır
  - `get()` methodu kullanmadan `NoSuchElementException` hatası vermemizi sağlar.
  - Optional boşsa herhangi bir `Throwable` nesneyi oluşturan bir Supplier'ı kabul eder ve onu atar.<br>

`get()`<br>
- Optional sınıfının get() metodu, Optional nesnesi içindeki değeri döndürür. <br>
- Ancak, Optional nesnesi null ise, get() metodu bir `NoSuchElementException` fırlatır. <br>
- Bu nedenle, get() metodu çağrılmadan önce, Optional nesnesinin boş olup olmadığı isEmpty() veya isPresent() metotları ile kontrol edilmelidir.<br>

 
