# SGP-NET: Sistem Pemantauan Kursi Prioritas Berbasis Scene Graph

Sebuah sistem cerdas untuk memantau penggunaan kursi prioritas di transportasi umum secara *real-time* menggunakan *deep learning* dan analisis kontekstual. Proyek ini dirancang untuk mengidentifikasi pelanggaran dan memberikan umpan balik secara otomatis untuk mendorong lingkungan transportasi yang lebih inklusif dan etis.

-----

## ✨ Fitur Utama

  * **Deteksi Real-time**: Menggunakan **YOLOv8n** untuk mendeteksi individu dan objek relevan (seperti kruk) dengan kecepatan tinggi.
  * **Analisis Kontekstual dengan Scene Graph**: Inovasi utama yang tidak hanya mendeteksi objek, tetapi juga **memodelkan hubungan spasial dan kontekstual** antar entitas (misalnya, kedekatan seseorang dengan kruk).
  * **Logika Keputusan Hierarkis**: Menerapkan aturan inferensi cerdas untuk menentukan prioritas berdasarkan urutan: (1) Penggunaan alat bantu, (2) Penggunaan masker, (3) Kategori usia.
  * **Umpan Balik Multi-modal**: Memberikan respons otomatis berupa **anotasi visual** (kotak berwarna dan teks) dan **umpan balik audio** (pesan suara informatif) secara dinamis.
  * **Manajemen Pelacakan**: Memberikan **ID pelacakan unik** pada setiap individu untuk memastikan konsistensi analisis di setiap *frame*.

-----

## ⚙️ Cara Kerja Sistem

SGP-NET dirancang sebagai sistem pemantauan kursi prioritas *end-to-end* yang memproses *feed* kamera secara *real-time*. Prosesnya dimulai dengan deteksi individu menggunakan model **YOLO**, yang kemudian memberikan ID pelacakan unik. Inovasi utama sistem ini terletak pada tahap ekstraksi atribut (usia, masker, kruk) yang kemudian dimodelkan secara relasional menggunakan **Scene Graph dinamis**. Mekanisme ini memungkinkan analisis berbasis **konteks dan interaksi antar entitas**, bukan sekadar deteksi terisolasi.

Berdasarkan pemahaman kontekstual dari Scene Graph tersebut, keputusan prioritas diambil secara **hierarkis** dan memicu **umpan balik multi-modal** yang adaptif, berupa anotasi visual dan pesan suara, yang dilengkapi mekanisme *cooldown* untuk menghindari repetisi.

-----

## 🛠️ Teknologi yang Digunakan

  * **Bahasa**: Python
  * **Framework Deep Learning**: PyTorch, TensorFlow/Keras
  * **Model Inti**:
      * **Deteksi Objek**: `ultralytics` (YOLOv8n)
      * **Klasifikasi**: `MobileNetV2` (via TensorFlow/Keras), CNN Kustom (via PyTorch)
  * **Manipulasi Citra**: OpenCV, Pillow
  * **Analisis Data**: NumPy, Pandas
  * **Audio**: gTTS, playsound
  * **Visualisasi**: Matplotlib, Seaborn

## Datasets
1. Penumpang dengan Kruk: https://universe.roboflow.com/kelvin-slsxl/crutches-rg3he
2. Usia: https://www.kaggle.com/datasets/frabbisw/facial-age
3. Masker: https://www.kaggle.com/datasets/omkargurav/face-mask-dataset