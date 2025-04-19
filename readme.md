# Footwear Image Classification

Proyek ini bertujuan untuk membangun model deep learning yang mampu mengklasifikasikan gambar alas kaki menjadi tiga kategori: **Boot**, **Sandal**, dan **Shoe**. Proyek ini mencakup tahap persiapan data, training model CNN, evaluasi, konversi model, hingga deployment menggunakan TensorFlow Lite dan TensorFlow.js.

---

## 🔍 Insight

### **Dataset**
- Dataset diperoleh dari Google Drive dengan nama **Footwear**.
- Dataset terdiri dari **3 kelas**: `Boot`, `Sandal`, dan `Shoe`.
- Masing-masing kelas memiliki **5000 gambar**, total **15.000 gambar**.
- Resolusi gambar awal bervariasi, namun telah disesuaikan saat proses pelatihan.

### **Modeling**
- Dataset telah dipisahkan menjadi:
  - **Train**: 9000 gambar
  - **Validation**: 3000 gambar
  - **Test**: 3000 gambar
- Model dibangun menggunakan arsitektur CNN `Sequential` dengan 3 blok konvolusi.
- Proses augmentasi dilakukan pada data training untuk meningkatkan generalisasi model.
- Teknik regularisasi seperti **Batch Normalization** dan **Dropout** digunakan.
- Model dilatih menggunakan `Adam` optimizer dan loss `sparse_categorical_crossentropy`.
- Callbacks seperti **EarlyStopping**, **ModelCheckpoint**, dan **ReduceLROnPlateau** digunakan untuk mengontrol training.

### **Evaluasi & Visualisasi**
- Akurasi model pada data test mencapai **95.16%**.
- Visualisasi **akurasi dan loss** per epoch menunjukkan bahwa model stabil dan tidak overfitting.
- **Confusion Matrix** menunjukkan prediksi yang akurat untuk setiap kelas.
- **Classification Report**:
  - Precision, Recall, dan F1-Score rata-rata berada pada **0.95** untuk semua kelas.

### **Konversi Model**
Model berhasil dikonversi ke dalam 3 format untuk kebutuhan deployment:

saved_model/
├── saved_model.pb
├── variables/
├── tflite/
│   ├── model.tflite
│   └── label.txt
└── tfjs_model/
    ├── model.json
    └── group1-shard1of1.bin

- Format `SavedModel`: digunakan untuk keperluan inferensi lokal atau deployment di server.
- Format `TFLite`: memungkinkan deployment pada perangkat mobile atau embedded.
- Format `TensorFlow.js`: dapat dijalankan langsung pada browser.

### **Inference**
- Model TFLite berhasil digunakan untuk memprediksi gambar baru.
- Hasil inference:
  - **sample7.jpg** → Sandal (90.62%)
  - **sample4.jpg** → Shoe (93.47%)
  - **sample3.jpg** → Boot (92.13%)
- Hal ini membuktikan bahwa model dapat mengklasifikasikan gambar baru dengan **akurasi tinggi** secara konsisten.

---

## 🚀 Teknologi yang Digunakan
- Python 3
- TensorFlow & Keras
- NumPy, Matplotlib, Seaborn
- scikit-learn
- PIL (Pillow)
- TensorFlow Lite Converter
- TensorFlow.js Converter

---

## 📌 Catatan
- Model ini menggunakan `class_mode='sparse'` untuk efisiensi memori saat menggunakan label numerik.
- Augmentasi data terbukti membantu meningkatkan kemampuan generalisasi model.
- Deployment multi-platform (TFLite, TF.js) memudahkan integrasi ke berbagai aplikasi.

---

## 🙌 Penutup
Proyek ini menunjukkan bagaimana pipeline **end-to-end image classification** dapat dibangun dan di-deploy dengan efektif. Dengan akurasi tinggi dan format model yang fleksibel, model ini siap digunakan untuk berbagai skenario aplikasi dunia nyata.


