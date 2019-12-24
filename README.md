## YazilimMimarisi

## Proxy Pattern

Yaratılması pahalı bir çok işlem yapan bir nesneyi taklit eden bir başka nesnenin kullanılmasıdır. Örneğin bir nesne yarattığımızda veya bir nesnenin bir yordamını çağırdığımızda, bu çağırım bellekte çok yer tutan daha başka bir çok nesne yaratabilir veya ağa bağlanma, veritabanından büyük bir veri alma gibi pahalı işlemler yapabilir. Fakat uygulamanın akışına göre, bu işlemleri gerçekten yapmaya ihtiyaç olmayabilir. İşte bu durumlarda, bu pahalı işlemlerden doğan zaman ve kaynak kayıplarını önlemek için özdeş nesne kullanılır. Gerçekten bu pahalı işlem çağırılırsa, gerçek nesne oluşturulup, bu pahalı işlemler ihtiyaç olduğunda yapılır. Bu tasarım deseni kullanılarak, sisteme yük getiren gereksiz pahalı işlemler önlenir, böylece sistem daha hızlı ve sağlıklı hale gelir.Tanım olarak havalı ve güzel gelse de algorita mantığı olarak çok iyi anlayabildiğim söylenemez.(sadece isminin havalı olduğunu düşündüğüm için seçmiştim :D)

![Image of Class](https://github.com/Odesyus/YazilimMimarisi/blob/master/Proxy.jpg)

```java
public interface Image {
    void display();
}
public class ProxyImage implements Image{

    private RealImage realImage;
    private String fileName;

    public ProxyImage(String fileName){
        this.fileName = fileName;
    }

    @Override
    public void display() {
        if(realImage == null){
            realImage = new RealImage(fileName);
        }
        realImage.display();
    }
}
public class ProxyPatternDemo {

    public static void main(String[] args) {
        Image image = new ProxyImage("test_10mb.jpg");

        //image will be loaded from disk
        image.display();
        System.out.println("");

        //image will not be loaded from disk
        image.display();
    }
}public class RealImage implements Image {

    private String fileName;

    public RealImage(String fileName){
        this.fileName = fileName;
        loadFromDisk(fileName);
    }

    @Override
    public void display() {
        System.out.println("Displaying " + fileName);
    }

    private void loadFromDisk(String fileName){
        System.out.println("Loading " + fileName);
    }
}
```

## Builder Pattern

Bunda da en kısa haliyle tek bir bütün haliyle almaktansa küçük parçalara ayırıp sonradan o parçaları bir bütün haline getirmek denilebilir. Gerçek hayattan bir örnek vermek gerekirse restoranta gittiğimizde garsonun tüm siparşi tek seferde almaktansa ilk önce neyli çorba istediğimizi soruyor ve çorbayı getiriyor ardından ana yemek ve ana yemek ardından tatlıyı soruyor gibi düşününebiliriz.

![Image of Class](https://github.com/Odesyus/YazilimMimarisi/blob/master/Builder.jpg)

Seçtiğim kod biraz fazla uzun olduğu için açıklasam sadece daha iyi gibi...

Sistem bir hamburger sipariş sistemi ve sistemde her şeyi tek seferde almak yerine deminki dediğim gibi başta hamburgerin nasıl bir hamburger olduğununun (Veg veya Chicken) ve kolanın nasıl olduğununun (Pepsi veya Coke) bilgilerini tek tek alıyor sonra onun üstünden devam ediyor.




