#RFM
***KPI (Key Performance Indicators):
   - Acquisition(müşteri kazanma oraanı)
   - Retention(müşteri elde tutma oranı)
   - Churn Rate
   - Conversion Rate
   - Growth Rate

***Analysis of Cohort :
     Bir grup insanı belirli bir kritere göre sınıflandırarak, bu grupların zaman içindeki davranışlarını ve
     özelliklerini inceleyen bir analiz yöntemidir. Genellikle müşteri davranışları, kullanıcı deneyimi, ürün
     performansı gibi alanlarda kullanılır. Cohort analizi, gruplar arasındaki farklılıkları ve değişimleri
     belirlemek, benzer grupların birbirleriyle karşılaştırılmasını sağlamak ve uzun vadeli trendleri tanımlamak için kullanılır.

***RFM :
     Müşteri segmentasyonunda kullanılan önemli bir analiz yöntemidir. RFM analizi, müşterileri üç ana kriter olan Recency (Yenilik),
     Frequency (Sıklık) ve Monetary (Miktar) ölçütlerine göre segmentlere ayırır. Her bir müşterinin bu üç kritere göre puanlanması ve
     ardından puanlara dayalı olarak segmentlere ayrılmasıyla yapılır.

    -Recency (Yenilik): Müşterinin son alışveriş yapma tarihinden bugüne kadar geçen süreyi ifade eder. Yani ne kadar yakın zamanda alışveriş
     yapıldığıdır. Yenilik kriterine göre, daha yakın zamanda alışveriş yapmış müşteriler daha yüksek bir puan alır.

    -Frequency (Sıklık): Belirli bir zaman diliminde müşterinin kaç kez alışveriş yaptığını ifade eder. Sıklık kriterine göre, daha sık alışveriş
     yapan müşteriler daha yüksek bir puan alır.

    -Monetary (Miktar): Müşterinin belirli bir zaman diliminde harcadığı toplam miktarı ifade eder. Yani müşterinin yaptığı alışverişlerin toplam
     değeridir. Miktar kriterine göre, daha yüksek miktarlarda harcama yapan müşteriler daha yüksek bir puan alır.

***RFM metriklerinin birbirleri ile karşılaştırılabilmesi için RFM skorlarına dönüştürülmesi gerekir(1-5).
     R ->en küçük olan 5 ,
     F ->en büyük olan 5,
     M ->en büyük olan 5

***RFM sokorları üzerinden segmentler oluşturulurken neden monatery kullanılmaz?
    -Monetary (harcama miktarı), müşterilerin alışverişlerinin parasal değerini ifade eder. Ancak, yüksek harcama yapan müşteriler her zaman en sadık
     veya en sık alışveriş yapan müşteriler olmayabilir. Harcama miktarı, kişisel gelir, ihtiyaçlar ve alışveriş alışkanlıkları gibi birçok faktörden
    etkilenir ve bu nedenle daha değişkendir.

***CLV(Customer Lifetime Value):
   CLV veya Müşteri Yaşam Boyu Değeri, bir müşterinin işletme ile olan ilişkisi boyunca getireceği toplam kârın tahmin edilmesidir.

   CLTV = (Customer Value / Churn Rate) * Profit Margin

   Customer Value = Avgerage order value * purchase frequency ( [Total Price(Kendi)/Total Transaction(hepsi)] * [Total Transction(kendi)/Total Number of Customers(hepsi)])
   Churn Rate = 1 - Repeat Rate ( 1-  [Birden çok alışveriş yapan müşteri sayısı/tüm müşteri sayısı])
   Profit Margin = Total price * PROFİT RATE(varsayılacak kar miktarı)

***CLTV Predictions:
   CLTV = (Expected Number of Transaction) * (Expected Avg. Profit) = (BG/NBD Model) * (Gamma Gamma Submodel)
   Hesaplamalar önce bütün kitlenin davranışları üzerinden yapılır ve model kurulur, sonra model kişiselleştirilir.

   -BG(beta geometric)/NBD(native binomial distribution) : Amaç olasılık dağılımları ile genel kitlenin satın alma davranışlarını modelleyip bunları kişilere indirgemek.

   -BG/NBD modeli, müşteri satın alma davranışını iki aşamalı bir süreç olarak ele alır:
      ~ Satın Alma Süreci(Transaction Process[r,α]): Müşterilerin belirli bir zaman diliminde alışveriş yapma olasılığı Geometrik Dağılım ile modellenir. Bu, her müşterinin satın alma
        alışkanlıklarının zaman içinde nasıl değiştiğini anlamaya yardımcı olur.Müşteri alive olduğu sürece belli bir zaman periyodunda geçekleştireceği işlem sayısı ile transaction
        rate(lambda, λ) parametresi poisson dağılır. Poisson dağılımı, bir olayın belirli bir zaman diliminde veya belirli bir alanda gerçekleşme olasılığını modellemek için kullanılan
        bir olasılık dağılımıdır. Poisson dağılımı, özellikle seyrek olayların sayısını modellemek için uygundur. Müşteri alive olduğu süre boyunca trans. ratei etrafında rastgele
        satın alma yapmaya devam edecektir. Transaction rateler her bir müşteri içn değişir ve gamma dağılır. Gamma dağılımı, pozitif değerlerin alındığı sürekli bir değişkeni 
        modellemek için kullanılır. Örneğin, bir ürünün ömrünü, bir işlemin tamamlanma süresini veya bir sistem arızasının ortaya çıkma zamanını modellemek için kullanılabilir.
        ***Dağılım türlerine göre kitlenin satın alma davranışı kontrol edilebilir.

      ~ Müşteri Yaşam Süreci(Dropout Process[a,b]): Müşterilerin ne kadar süre aktif kalacağını tahmin etmek için Negatif Binom Dağılım kullanılır. Bu, bir müşterinin aktif olarak
        alışveriş yapmaya devam etme olasılığını ve ne zaman "ölü" (yani, artık alışveriş yapmayacak) hale geleceğini belirler. Her müşterinin p olasılığpı ile dropout rate'i vardır.
        dropout rateler her müşteride değişir ve tüm kitle için Beta dağılır.
  
 - GAMMA GAMMA SUB MODEL: 
      ~ Bir müşterinin işlem başına ortalama ne kadar kar getirebileceğini tahmin etmek için kullanılır.       
      ~ bir müşterinin işlemlerinin parasal değeri (monatery) transaction valuleların ortalaması etrafında ratgele dağılır.
      ~ Ort. trans. val. zamanla kullanıcılar arasında değişebilir ancak tek kullanıcı diçin değişmez.

*** Her müşteriye RFM uygulanmaz çünkü müşteriyi değerlendiirebilmek için belirli bir alışkanlığı olmalı, RFM e girrce bri müşteri havuzu oluşturmak önemlidir.(örn: total_order_ever>4)

*** Organic Ratio : etki altında kalmadan kendi gelen müşteri.


































