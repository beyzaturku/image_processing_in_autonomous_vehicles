# Otonom Araç Teknolojilerinde Görüntü İşleme Tekniklerinin Kullanımı

Proje kapsamında otonom sürüş için görüntü işleme tabanlı bir sistem geliştirilmiştir. Sistem, şerit tespiti ile birden fazla aracın gerçek zamanlı tespit ve takibini entegre bir ardışıl işlem hattı (pipeline) içinde gerçekleştirmektedir. Şerit tespiti aşamasında renk eşikleme, kenar bulma (Canny kenar tespiti) ve Bölge İlgi Alanı (ROI) dönüşümü gibi klasik görüntü işleme teknikleri kullanılmıştır. Araç tespiti için Ultralytics YOLOv8 derin öğrenme modeli, araç takibi için ise DeepSORT çoklu nesne takip algoritması uygulanmıştır.Proje, Udacity Lane Detection veri seti ve COCO gibi kamuya açık veri setleriyle farklı yol ve çevre koşullarında test edilmiş; sonuçlar, sistemin şeritleri doğru şekilde saptayıp birden fazla aracı kararlı bir biçimde tespit ve takip edebildiğini göstermektedir.

## Özellikler
*** **Şerit Tespiti (Lane Detection):**** Görüntülerdeki şerit çizgilerini algılamak için renk filtreleme, Canny kenar algılama ve perspektif dönüşümü teknikleri kullanılır. Sistem, yol şeritlerini tespit ederek aracın şeridini korumasına yardımcı olur.
*** Araç Tespiti (Vehicle Detection – YOLOv8):** Yol üzerindeki araçları gerçek zamanlı olarak tespit etmek için YOLOv8 modeli kullanılır. YOLOv8 (You Only Look Once v8), tek geçişte nesne tespiti yapabilen hızlı ve yüksek başarımlı bir derin öğrenme modelidir; bu projede önceden COCO üzerinde eğitilmiş ağırlıkları ile araç (ör. araba, otobüs) tespitine odaklanmıştır.
*** Araç Takibi (Vehicle Tracking – DeepSORT):** Tespit edilen araçlar, DeepSORT algoritması ile takip edilir. DeepSORT (Deep Simple Online and Realtime Tracking), her bir araca benzersiz bir ID atayarak nesnelerin video boyunca izlenmesini sağlar. Bu sayede çerçeveler arasında araçların hareketi takip edilerek tutarlı bir çoklu nesne takibi gerçekleştirilir.

## Kullanılan Teknolojiler ve Kütüphaneler
*** Python 3:** Projenin geliştirme dili.
*** OpenCV:** Görüntü işleme işlemleri (renk eşikleme, filtreleme, kenar bulma, vb.) için kullanılan açık kaynak kütüphane.
*** Ultralytics YOLOv8:** Nesne (araç) tespiti için kullanılan derin öğrenme modeli ve kütüphanesi. Gerçek zamanlı nesne algılama imkanı sağlar.
*** DeepSORT: **Nesne takip algoritması. YOLO tespit sonuçlarını kullanarak aynı nesneyi (aracı) ardışık karelerde takip etmeye olanak tanır.
*** Google Colab: **Projenin Jupyter Notebook dosyalarının çalıştırıldığı bulut ortamı. GPU desteği sayesinde derin öğrenme modelinin gerçek zamanlı çalışmasını kolaylaştırır.
*** NumPy: **Sayısal hesaplamalar ve dizi (array) işlemleri için Python kütüphanesi. Görüntü verilerinin işlenmesinde kullanılır.
*** MoviePy: **Video işleme kütüphanesi. Karelerin birleştirilerek çıktı video oluşturulması, videoya çizimler eklenmesi gibi işlemlerde kullanılmıştır.

## Klasör Yapısı 
Repository içerisinde projenin ana bölümlerini içeren üç adet Jupyter Notebook dosyası bulunmaktadır:
***serit_takip.ipynb** – Şerit tespiti ve takibi için hazırlanan notebook (yalnızca şerit algılama pipeline’ı).
*** car_detect_and_tracking.ipynb** – Araç tespiti (YOLOv8 ile) ve araç takibi (DeepSORT ile) için notebook.
*** **lane_and_car_detection_tracking_pipeline.ipynb**** – Tam entegre şerit ve araç tespit/takip pipeline’ını bir arada gerçekleştiren notebook (şerit tespiti ve çoklu araç takibini birlikte yapar).

## Kurulum ve Çalıştırma Talimatları 
Gerekli Kütüphaneler | Required Libraries
Projeyi lokal ortamda çalıştırmak isterseniz, aşağıdaki Python kütüphanelerinin kurulu olduğundan emin olun:
opencv-python (OpenCV için)
ultralytics (YOLOv8 modeli için Ultralytics paketi)
numpy
moviepy
Eğer Google Colab kullanıyorsanız, bu kütüphanelerin bir kısmı ortamda yüklü gelebilir. Notebook içerisinde ihtiyaç duyulan kütüphaneler pip install komutlarıyla da kurulabilir.
Google Colab Ortamında Çalıştırma | Running on Google Colab
Proje notebook’larını Google Colab üzerinde kolayca çalıştırabilirsiniz:
Bu repository’yi GitHub üzerinden Google Colab’de açın veya notebook dosyalarını Colab ortamına yükleyin. Colab, Jupyter notebook dosyalarını doğrudan açabilmektedir.
Colab’de Runtime > Change Runtime Type menüsünden GPU seçerek donanım hızlandırmayı aktif hale getirin (YOLOv8’in gerçek zamanlı çalışması için GPU önerilir).
Notebook açıldıktan sonra, sırasıyla tüm hücreleri çalıştırın. Gerekli kütüphaneler yüklenecek, model ağırlıkları indirilecek (ilk çalıştırmada YOLOv8, COCO pre-trained ağırlıklarını internetten çekecektir) ve algoritmalar videolar üzerinde çalışacaktır.
Jupyter Notebook Dosyaları ve Kullanımı | Notebook Files & Usage
Proje kapsamında üç ayrı Jupyter notebook dosyası farklı görevleri gerçekleştirmektedir. İhtiyacınıza göre ilgili notebook dosyasını çalıştırabilirsiniz:
Şerit Tespiti: serit_takip.ipynb dosyasını açıp çalıştırarak yalnızca şerit tespitine yönelik pipeline’ı çalıştırabilirsiniz. Bu notebook, verilen video görüntülerinde yol şeritlerini algılayarak sonuçları görselleştirir.
Araç Tespiti ve Takibi: car_detect_and_tracking.ipynb dosyası, bir video akışında araç tespiti ve takibini gerçekleştirir. YOLOv8 modelini kullanarak her karede araçları saptar ve DeepSORT ile bu araçları izleyerek her birine ID atar. Çalıştırıldığında, araçların üzerindeki sınıf etiketi ve ID’lerle birlikte çerçeveler çizilmiş olarak görüntülenir.
Entegre Pipeline: lane_and_car_detection_tracking_pipeline.ipynb dosyası, şerit algılama ile araç tespit & takibini tek bir pipeline olarak entegre etmektedir. Bu notebook’u çalıştırdığınızda, sistem aynı anda hem şerit çizgilerini tespit edip işaretler, hem de birden çok aracı yakalayıp takip eder. Bu entegre demo, otonom bir aracın aynı anda şerit takibi ve çevresindeki araçları izlemesini eş zamanlı olarak göstermektedir.
Her bir notebook, adım adım açıklamalar ve kod hücreleri içerir. Kendi verilerinizi denemek isterseniz, notebook içindeki video dosyası yolunu güncelleyerek farklı videolarla da sistemi test edebilirsiniz.
Veri Seti | Datasets
Udacity Lane Detection Veri Seti: Şerit tespiti algoritması, Udacity’nin otonom sürüş çalışmaları kapsamında sağladığı örnek yol videoları üzerinde denenmiştir. Bu veri seti, çeşitli sürüş koşullarında çekilmiş videolar ile şerit algılama yeteneklerini değerlendirmek için kullanılır. Sistem, bu videolarda yol üzerindeki şerit çizgilerini başarıyla tespit edecek şekilde ayarlanmıştır.
COCO Dataset (Common Objects in Context): Araç tespit modeli olarak kullanılan YOLOv8, COCO veri seti üzerinde önceden eğitilmiştir. COCO, araçlar (otomobil, otobüs, motosiklet gibi) dahil olmak üzere birçok obje sınıfını içeren geniş kapsamlı bir nesne tanıma veri setidir. Bu sayede model, gerçek trafik sahnelerindeki araçları yüksek doğrulukla tanıyabilmektedir. (Not: Projede, ek bir özel eğitim yapılmamış; doğrudan COCO üzerinde eğitilmiş YOLOv8n ağırlıkları kullanılmıştır.)

