# 🚗 Otonom Araç Teknolojilerinde Görüntü İşleme Tekniklerinin Kullanımı

💡 **Şerit Tespiti • 🚘 Araç Tespiti • 📍 Araç Takibi (YOLOv8 + DeepSORT)**

---

## 📌 Proje Hakkında

Otonom sürüş sistemleri için geliştirilen bu projede; 📷 kamera görüntülerinden **şerit tespiti**, **araç tespiti** ve **çoklu araç takibi** yapılmaktadır.  
Geleneksel görüntü işleme + derin öğrenme yöntemleri hibrit bir pipeline içinde birleştirilmiştir.

> ✅ YOLOv8 ile araç tespiti  
> ✅ DeepSORT ile ID bazlı araç takibi  
> ✅ OpenCV ile şerit çizgisi algılama  
> ✅ MoviePy ile video çıktısı üretme

---

## 🔧 Kullanılan Teknolojiler

| Teknoloji/Kütüphane | Açıklama |
|---------------------|----------|
| 🐍 Python           | Geliştirme dili |
| 📹 OpenCV           | Görüntü işleme |
| 🧠 Ultralytics YOLOv8 | Nesne tespiti (araçlar) |
| 🎯 DeepSORT         | Nesne takibi (ID takibi) |
| 🧮 NumPy            | Sayısal işlemler |
| 🎬 MoviePy          | Video işleme |
| ☁️ Google Colab     | Geliştirme ve çalışma ortamı |

---

## 📁 Klasör / Dosya Yapısı

```
📦 image_processing_in_autonomous_vehicles
 ┣ 📓 serit_takip.ipynb
 ┣ 📓 car_detect_and_tracking.ipynb
 ┣ 📓 lane_and_car_detection_tracking_pipeline.ipynb
```

---

## 🚀 Kurulum ve Çalıştırma

🔹 Ortam: Google Colab veya lokal Jupyter Notebook  
🔹 Gerekli paketler:
```bash
pip install opencv-python ultralytics numpy moviepy
```

🔹 Çalıştırma adımları:
1. Notebook’u açın
2. GPU’yu aktif edin (Colab: `Runtime > Change runtime type > GPU`)
3. Hücreleri sırasıyla çalıştırın
4. Çıktı videolarını indirin / izleyin 🎥

---

## 🎥 Örnek Çıktı

<a href="https://drive.google.com/file/d/1qdTT4iR7_dNHe5hq7qQ6Y2EYpMJ2Xs5j/view?usp=sharing" target="blank" alt="Videoyu izlemek için tıklayınız." height="30" width="40" /></a>

- Araçlar renkli kutular ve ID’lerle takip edilir 🏷️  
- Şerit çizgileri vurgulanır ⚡  
- Her şey tek videoda entegre şekilde çalışır 🚗➡️📍

---

## 🗃️ Veri Setleri

- **Udacity Lane Detection** — Şerit tespiti videoları  
- **COCO Dataset** — YOLOv8 için önceden eğitilmiş ağırlıklar  

---


