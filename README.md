# bilet-fiyati-hesaplama
Java101_13 Çoklu koşullara göre bilet fiyatı hesaplayan program

https://www.patika.dev/tr

/*Ödev - Uçak Bileti Fiyatı Hesaplama
Java ile mesafeye ve şartlara göre uçak bileti fiyatı hesaplayan programı yapın. Kullanıcıdan Mesafe (KM), yaşı ve yolculuk tipi (Tek Yön, Gidiş-Dönüş) bilgilerini alın. Mesafe başına ücret 0,10 TL / km olarak alın. İlk olarak uçuşun toplam fiyatını hesaplayın ve sonrasında ki koşullara göre müşteriye aşağıdaki indirimleri uygulayın ;

Kullanıcıdan alınan değerler geçerli (mesafe ve yaş değerleri pozitif sayı, yolculuk tipi ise 1 veya 2) olmalıdır. Aksi takdirde kullanıcıya "Hatalı Veri Girdiniz !" şeklinde bir uyarı verilmelidir.
Kişi 12 yaşından küçükse bilet fiyatı üzerinden %50 indirim uygulanır.
Kişi 12-24 yaşları arasında ise bilet fiyatı üzerinden %10 indirim uygulanır.
Kişi 65 yaşından büyük ise bilet fiyatı üzerinden %30 indirim uygulanır.
Kişi "Yolculuk Tipini" gidiş dönüş seçmiş ise bilet fiyatı üzerinden %20 indirim uygulanır.*/


import java.util.Scanner;
public class Main
{
	public static void main(String[] args) {
	    double km, yas, yolculukTipi, normalTutar, yasIndirimi1, yasIndirimi2, yasIndirimi3 ;
	    
	    Scanner input=new Scanner(System.in);
	    System.out.print("Mesafe/km : ");
	    km=input.nextDouble();
	    if (km<0){
	        System.out.println("Hatalı Veri Girdiniz !");
	    }
	    System.out.print("Yaşınız : ");
	    yas=input.nextDouble();
	    if (yas<0){
	        System.out.println("Hatalı Veri Girdiniz !");
	    }
	    System.out.print("Yolculuk Tipi\n1 => Tek Yön :\n2 => Gidiş Dönüş :");
	    yolculukTipi=input.nextDouble();
	    if (!(yolculukTipi==1 || yolculukTipi==2)){
	        System.out.println("Hatalı Veri Girdiniz !");
	    }
	    
	    normalTutar=km*0.10 ;
	    yasIndirimi1=normalTutar-(normalTutar*0.50) ;
	    yasIndirimi2=normalTutar-(normalTutar*0.10) ;
	    yasIndirimi3=normalTutar-(normalTutar*0.30) ;
	    
	    if (yas>=0 && yas<12){
	        if(yolculukTipi==1){
	        System.out.println("Toplam Tutar : "+yasIndirimi1+" TL");
	            }
	            else if(yolculukTipi==2){
	                System.out.println("Toplam Tutar :"+ ((yasIndirimi1-=yasIndirimi1*0.20))*2+" TL");
	            }
	    }
	    else if(yas>=12 && yas<=24){
	        if(yolculukTipi==1){
	            System.out.println("Toplam Tutar : "+yasIndirimi2+" TL");
	            }
	            else if(yolculukTipi==2){
	                System.out.println("Toplam Tutar : "+((yasIndirimi2-=yasIndirimi2*0.20))*2+" TL");
	            }
	    }
	    else if(yas>65){
	        if(yolculukTipi==1){
	            System.out.println("Toplam Tutar : "+yasIndirimi3+" TL");
	        }
	        else if (yolculukTipi==2){
	            System.out.println("Toplam Tutar : "+((yasIndirimi3-=yasIndirimi3*0.20)*2)+" TL");
	        }
	    }
	    else{
	        if(yolculukTipi==1){
	            System.out.println("Toplam Tutar : "+normalTutar+" TL");
	        }
	        else if(yolculukTipi==2){
	            System.out.println("Toplam Tutar : "+((normalTutar-=normalTutar*0.20)*2)+" TL");
	        }
	    }

	}
}
