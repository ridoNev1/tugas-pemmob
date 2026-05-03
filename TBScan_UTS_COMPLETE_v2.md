**TBScan**  — Project UTS | **Explainable Deep Learning untuk Deteksi TB**

**DOKUMEN PROJECT UTS**

**IDENTIFIKASI CITRA MEDIS PARU-PARU**

**UNTUK MENDETEKSI VISUALISASI AREA FOKUS**

**PENYAKIT TUBERKULOSIS DENGAN**

**EXPLAINABLE DEEP LEARNING BERBASIS MOBILE**

 

 

| KELOMPOK PROJECT |  |  |
| :---: | :---- | :---- |
| **Peran** | **Nama** | **NIM** |
| **Ketua** | \[Nama Ketua\] | \[NIM Ketua\] |
| Anggota 1 | \[Nama Anggota 1\] | \[NIM Anggota 1\] |
| Anggota 2 | \[Nama Anggota 2\] | \[NIM Anggota 2\] |
| Anggota 3 | \[Nama Anggota 3\] | \[NIM Anggota 3\] |
| Anggota 4 | \[Nama Anggota 4\] | \[NIM Anggota 4\] |

 

 

Program Studi Teknik Informatika

Tahun Akademik 2024/2025

# **A. KONSEP OVERVIEW PROJECT**

## **1\. Latar Belakang**

Tuberkulosis (TB) merupakan salah satu penyakit infeksi menular yang masih menjadi masalah kesehatan global. Menurut WHO, Indonesia termasuk dalam 8 negara dengan beban TB tertinggi di dunia. Deteksi dini TB sangat krusial untuk mencegah penularan lebih lanjut dan meningkatkan efektivitas pengobatan.

Pemeriksaan foto rontgen dada (Chest X-Ray / CXR) adalah metode utama yang digunakan untuk mendiagnosis TB. Namun keterbatasan jumlah radiolog dan ketidakmerataan distribusi tenaga kesehatan di daerah terpencil menjadi hambatan besar dalam upaya deteksi dini. Solusi berbasis kecerdasan buatan (AI), khususnya Deep Learning, menjadi alternatif yang menjanjikan untuk membantu proses diagnosis secara otomatis dan cepat.

Namun, permasalahan utama model Deep Learning adalah sifatnya yang "Black Box" — sulit dipahami bagaimana model sampai pada keputusannya. Hal ini menghambat kepercayaan klinisi terhadap sistem AI. Oleh karena itu, pendekatan Explainable AI (XAI) diperlukan untuk menghasilkan visualisasi area fokus penyakit yang dapat diinterpretasi secara medis.

 

## **2\. Deskripsi Project**

**Nama Aplikasi:** TBScan — TB Detection with Explainable AI

**Platform:** Mobile Application (Android/iOS) menggunakan Flutter

**Topik Utama:** Deep Learning, Computer Vision, Explainable AI (XAI)

 

TBScan adalah aplikasi mobile berbasis Deep Learning yang dirancang untuk membantu tenaga kesehatan dan kader TB dalam melakukan skrining awal tuberkulosis melalui analisis citra foto rontgen paru-paru (Chest X-Ray). Keunggulan utama aplikasi ini adalah integrasi Explainable AI menggunakan metode Grad-CAM (Gradient-weighted Class Activation Mapping) yang menghasilkan heatmap visual pada area paru-paru yang terindikasi TB, sehingga output model dapat diinterpretasi dan dipercaya oleh tenaga medis.

 

## **3\. Tujuan Project**

* Membangun model klasifikasi citra medis berbasis Convolutional Neural Network (CNN) untuk mendeteksi TB dari foto Chest X-Ray

* Mengimplementasikan teknik Grad-CAM untuk menghasilkan visualisasi area fokus penyakit (explainability)

* Mengembangkan aplikasi mobile cross-platform (Flutter) yang terintegrasi dengan model AI melalui REST API

* Menyediakan antarmuka yang ramah pengguna bagi tenaga kesehatan di lapangan

* Membantu program penanggulangan TB nasional melalui teknologi AI yang transparan dan akuntabel

 

## **4\. Output / Deliverable yang Dihasilkan**

| No | Output | Deskripsi |
| :---: | :---- | :---- |
| **1** | **Model AI (.h5/.tflite)** | Model CNN (MobileNetV2) terlatih untuk klasifikasi Normal vs TB dari Chest X-Ray |
| **2** | **Grad-CAM Heatmap** | Visualisasi area paru-paru yang menjadi fokus prediksi model |
| **3** | **Backend API (Flask)** | REST API untuk inference model dan generate heatmap Grad-CAM |
| **4** | **Mobile App (Flutter)** | Aplikasi Android/iOS untuk upload foto, tampil hasil, dan riwayat scan |
| **5** | **Database (SQLite/Firebase)** | Penyimpanan riwayat pemeriksaan pasien secara dinamis |
| **6** | **Laporan Akurasi** | Evaluasi model: Accuracy, Precision, Recall, F1-Score, AUC-ROC |

 

## **5\. Arsitektur Sistem Secara Umum**

**Layer 1 — Mobile App (Flutter):** Antarmuka pengguna, kamera, upload gambar, tampilan hasil dan heatmap

**Layer 2 — Backend API (Flask/FastAPI):** Menerima request gambar, preprocessing, inference model, generate Grad-CAM

**Layer 3 — AI Engine:** Model CNN berbasis MobileNetV2 \+ Grad-CAM, dikonversi ke TensorFlow Lite untuk deployment

**Layer 4 — Data Layer:** Firebase Firestore untuk riwayat scan, Firebase Storage untuk penyimpanan citra

# **B. FUNCTIONAL & NON-FUNCTIONAL REQUIREMENT**

## **1\. Functional Requirement**

*Tabel berikut menjelaskan seluruh kebutuhan fungsional dari aplikasi TBScan:*

| No | Kode | Nama Fitur | Deskripsi |
| :---: | ----- | :---- | :---- |
| 1 | **FR-01** | **Autentikasi Pengguna** | Sistem menyediakan fitur registrasi dan login untuk tenaga kesehatan, dengan role: Admin, Dokter, dan Kader TB |
| 2 | **FR-02** | **Upload Citra X-Ray** | Pengguna dapat mengunggah foto Chest X-Ray dari galeri atau mengambil gambar langsung melalui kamera perangkat |
| 3 | **FR-03** | **Preprocessing Gambar** | Sistem melakukan preprocessing otomatis: resize (224×224), normalisasi pixel, dan konversi grayscale ke RGB |
| 4 | **FR-04** | **Klasifikasi TB** | Model CNN melakukan prediksi: Normal atau TB Positif, disertai confidence score (0–100%) |
| 5 | **FR-05** | **Visualisasi Grad-CAM** | Sistem menghasilkan heatmap overlay Grad-CAM yang menunjukkan area fokus penyakit pada foto X-Ray |
| 6 | **FR-06** | **Tampil Hasil Diagnosis** | Aplikasi menampilkan hasil: label prediksi, confidence score, heatmap Grad-CAM, dan rekomendasi tindak lanjut |
| 7 | **FR-07** | **Manajemen Data Pasien** | Pengguna dapat menambah, mengedit, dan melihat data pasien (nama, usia, jenis kelamin, ID pasien) |
| 8 | **FR-08** | **Riwayat Pemeriksaan** | Sistem menyimpan dan menampilkan riwayat scan per pasien dengan filter tanggal dan status diagnosis |
| 9 | **FR-09** | **Export Laporan PDF** | Pengguna dapat mengexport hasil pemeriksaan ke dalam format PDF yang siap dicetak |
| 10 | **FR-10** | **Notifikasi Hasil** | Sistem mengirimkan notifikasi push ketika proses analisis AI selesai |
| 11 | **FR-11** | **Statistik Dashboard** | Admin dapat melihat statistik: jumlah scan, persentase TB positif, grafik tren per bulan |
| 12 | **FR-12** | **Manajemen Master Data** | Admin dapat mengelola data referensi: jenis pemeriksaan, fasilitas kesehatan, dan threshold confidence |

 

 

## **2\. Non-Functional Requirement**

*Tabel berikut menjelaskan seluruh kebutuhan non-fungsional dari aplikasi TBScan:*

| No | Kode | Kategori | Kebutuhan | Kriteria Terukur |
| :---: | ----- | :---- | :---- | :---- |
| 1 | **NFR-01** | **Performance** | Waktu respons prediksi | Hasil prediksi \+ heatmap tersedia dalam ≤ 5 detik pada koneksi WiFi |
| 2 | **NFR-02** | **Akurasi Model** | Akurasi klasifikasi TB | Minimum akurasi 90%, Sensitivity ≥ 85%, Specificity ≥ 88% |
| 3 | **NFR-03** | **Availability** | Ketersediaan sistem | Uptime backend API ≥ 99% per bulan |
| 4 | **NFR-04** | **Scalability** | Kapasitas pengguna | Backend mampu menangani ≥ 100 concurrent request |
| 5 | **NFR-05** | **Usability** | Kemudahan penggunaan | SUS Score (System Usability Scale) ≥ 70 dari evaluasi pengguna |
| 6 | **NFR-06** | **Security** | Keamanan data pasien | Seluruh data terenkripsi (AES-256), transmisi via HTTPS/TLS 1.3 |
| 7 | **NFR-07** | **Compatibility** | Kompatibilitas device | Mendukung Android 8.0+ dan iOS 13.0+ (minimal 85% device di pasar) |
| 8 | **NFR-08** | **Reliability** | Ketahanan model | False Negative Rate (FNR) ≤ 10% untuk mencegah missed diagnosis |
| 9 | **NFR-09** | **Maintainability** | Kemudahan pemeliharaan | Kode mengikuti clean architecture, test coverage ≥ 70% |
| 10 | **NFR-10** | **Privacy** | Privasi data pasien | Sesuai regulasi PDPA (UU PDP Indonesia No. 27 Tahun 2022\) |
| 11 | **NFR-11** | **Offline Capability** | Fungsi offline | Model TFLite tersedia on-device; prediksi dapat dilakukan tanpa internet |
| 12 | **NFR-12** | **Portability** | Ukuran aplikasi | Ukuran APK/IPA ≤ 50 MB termasuk model TFLite |

# **C. LOGIC ALGORITMA / ALUR / METODE**

## **1\. Metode yang Digunakan**

| No | Metode | Kegunaan | Library/Tools |
| :---: | :---- | :---- | :---- |
| 1 | **MobileNetV2 (CNN)** | Arsitektur backbone untuk ekstraksi fitur Chest X-Ray. Pre-trained ImageNet, fine-tuned dataset TB | TensorFlow/Keras |
| 2 | **Transfer Learning** | Memanfaatkan bobot pre-trained model untuk mempercepat konvergensi dan meningkatkan akurasi | TensorFlow Hub |
| 3 | **Grad-CAM** | Menghasilkan heatmap visualisasi area aktif pada layer konvolusi terakhir model | tf-explain / OpenCV |
| 4 | **Data Augmentation** | Memperluas dataset: rotasi ±15°, flip horizontal, zoom 10%, brightness adjustment | Keras ImageDataGenerator |
| 5 | **Binary Cross-Entropy** | Fungsi loss untuk klasifikasi biner (Normal vs TB Positif) | TensorFlow/Keras |
| 6 | **Adam Optimizer** | Optimizer adaptif untuk training model dengan learning rate 0.0001 | TensorFlow/Keras |
| 7 | **TensorFlow Lite** | Konversi model ke format ringan untuk deployment on-device di mobile | TFLite Converter |
| 8 | **REST API (Flask)** | Endpoint untuk menerima gambar, inference, dan return hasil \+ heatmap | Flask, Python |

 

## **2\. Alur Sistem End-to-End**

### **2.1 Alur Training Model (Offline)**

| Step | Proses | Detail |
| :---: | :---- | :---- |
| **1** | **Pengumpulan Dataset** | Dataset: NIH ChestX-ray14 \+ Montgomery County CXR \+ Shenzhen Hospital CXR (label: Normal / TB Positive) |
| **2** | **Preprocessing** | Resize semua citra ke 224×224px, normalisasi nilai piksel \[0,1\], konversi grayscale ke RGB (3-channel) |
| **3** | **Split Dataset** | Train:Validation:Test \= 70%:15%:15%, stratified sampling memastikan distribusi kelas seimbang |
| **4** | **Data Augmentation** | Augmentasi pada training set: rotasi, flip, zoom, brightness, shear untuk menghindari overfitting |
| **5** | **Load MobileNetV2** | Load arsitektur MobileNetV2 dengan bobot ImageNet, bekukan layer base (freeze), tambah custom head |
| **6** | **Custom Head** | GlobalAveragePooling2D → Dense(128, ReLU) → Dropout(0.5) → Dense(1, Sigmoid) |
| **7** | **Compile Model** | optimizer=Adam(lr=0.0001), loss=binary\_crossentropy, metrics=\[accuracy, AUC, Recall, Precision\] |
| **8** | **Fine-tuning** | Fase 1: train head saja (10 epoch). Fase 2: unfreeze 30 layer terakhir, train dengan lr=1e-5 (20 epoch) |
| **9** | **Evaluasi** | Confusion Matrix, Classification Report, ROC Curve, AUC pada test set |
| **10** | **Konversi TFLite** | Konversi model .h5 ke .tflite dengan optimasi quantization int8 untuk deployment mobile |

 

 

### **2.2 Alur Inference & Grad-CAM (Runtime)**

*Berikut adalah pseudocode lengkap alur inference pada backend API:*

| ALGORITMA: TB\_Detection\_with\_GradCAM   INPUT  : image (JPEG/PNG dari kamera atau galeri) OUTPUT : { label, confidence, heatmap\_base64, recommendation }   BEGIN   // \=== STEP 1: PREPROCESSING \===   img\_raw     ← load\_image(input\_file)   img\_resized ← resize(img\_raw, target=(224, 224))   img\_rgb     ← convert\_to\_RGB(img\_resized)   // pastikan 3-channel   img\_array   ← normalize(img\_rgb) / 255.0   img\_batch   ← expand\_dims(img\_array, axis=0) // shape: (1,224,224,3)     // \=== STEP 2: INFERENCE MODEL \===   model       ← load\_model('mobilenetv2\_tb.h5')   raw\_score   ← model.predict(img\_batch)\[0\]\[0\]   confidence  ← raw\_score \* 100   // dalam persen     IF confidence \>= THRESHOLD (default: 50%)     label          ← 'TB POSITIF'     recommendation ← 'Segera rujuk ke fasilitas kesehatan untuk pemeriksaan lanjutan'   ELSE     label          ← 'NORMAL'     recommendation ← 'Tidak terdeteksi indikasi TB. Tetap jaga kesehatan paru-paru'   END IF     // \=== STEP 3: GRAD-CAM COMPUTATION \===   last\_conv\_layer ← model.get\_layer('Conv\_1')  // layer konvolusi terakhir MobileNetV2   grad\_model      ← Model(inputs=model.input,                           outputs=\[last\_conv\_layer.output, model.output\])     WITH GradientTape() AS tape:     conv\_outputs, predictions ← grad\_model(img\_batch)     loss ← predictions\[:, 0\]   // output neuron kelas TB   END WITH     grads        ← tape.gradient(loss, conv\_outputs)   pooled\_grads ← GlobalAveragePooling(grads)   // bobot tiap filter     FOR i IN range(pooled\_grads.shape\[-1\]):     conv\_outputs\[0, :, :, i\] \*= pooled\_grads\[i\]   END FOR     heatmap ← mean(conv\_outputs\[0\], axis=-1)   // rata-rata semua filter   heatmap ← ReLU(heatmap)                    // ambil nilai positif saja   heatmap ← normalize(heatmap, range=\[0,1\])  // normalisasi ke \[0,1\]     // \=== STEP 4: OVERLAY HEATMAP \===   heatmap\_resized  ← resize(heatmap, target=(224, 224))   heatmap\_colored  ← apply\_colormap(heatmap\_resized, colormap=JET)   heatmap\_colored  ← convert\_to\_RGB(heatmap\_colored)   superimposed     ← weighted\_add(heatmap\_colored\*0.4, img\_rgb\*0.6)   heatmap\_base64   ← encode\_base64(superimposed)     // \=== STEP 5: RETURN RESPONSE \===   RETURN {     'label'           : label,     'confidence'      : round(confidence, 2),     'heatmap\_base64'  : heatmap\_base64,     'recommendation'  : recommendation,     'timestamp'       : now()   } END |
| :---- |

 

 

### **2.3 Alur Aplikasi Mobile (User Flow)**

| 📱 MOBILE APP (Flutter) |   | ☁️ BACKEND \+ AI ENGINE |
| ----- | :---- | ----- |
| **● START** ↓ Buka Aplikasi ↓ Login Pengguna ↓ Pilih / Buat Data Pasien ↓ Upload Foto X-Ray (Kamera / Galeri) ↓ \[Validasi format & ukuran\]   ↓  valid Preview Gambar ↓ Tekan 'Analisis'      ↓  POST /predict Tampil Loading...      ↓  response JSON Tampil Hasil:   Label  |  Confidence   Heatmap | Rekomendasi ↓ Auto-save ke Database ↓ Export PDF / Selesai ↓ **⬛ END** |   |                 **← Terima Image** ↓ Preprocessing resize(224×224) \+ normalize ↓ Inference MobileNetV2 → confidence score ↓ Generate Grad-CAM → heatmap overlay ↓ \[TB Positif?\] YES → label \= TB POSITIF NO  → label \= NORMAL ↓ **Return JSON Response →**         |

 

 

## **3\. Tabel Alur Aplikasi Mobile**

| No | Aksi Pengguna | Respons Sistem |
| :---: | :---- | :---- |
| 1 | **Buka Aplikasi** | Splash screen → Cek auth token → Arahkan ke Login atau Dashboard |
| 2 | **Login** | Validasi kredensial via Firebase Auth → Generate JWT → Redirect Dashboard |
| 3 | **Pilih Pasien / Buat Baru** | Form input data pasien (nama, usia, gender, ID) → Simpan ke Firestore |
| 4 | **Upload / Foto X-Ray** | Akses galeri atau kamera → Pilih/ambil gambar → Preview pratampil gambar |
| 5 | **Konfirmasi & Analisis** | Tombol 'Analisis' ditekan → Kompresi gambar → Kirim ke API endpoint /predict |
| 6 | **Proses Backend** | API menerima gambar → Preprocessing → Inference model → Grad-CAM → Return JSON |
| 7 | **Tampil Hasil** | Animasi loading → Tampil: label, confidence gauge, heatmap overlay, rekomendasi |
| 8 | **Simpan Hasil** | Auto-save hasil ke Firestore → Gambar asli \+ heatmap ke Firebase Storage |
| 9 | **Export PDF** | Tombol Export → Generate PDF laporan → Share ke WhatsApp/Email atau Print |
| 10 | **Lihat Riwayat** | Tab Riwayat → List scan per pasien → Detail setiap scan \+ heatmap historis |

# **D. RANCANGAN DIAGRAM UML**

## **1\. Use Case Diagram**

Use Case Diagram menggambarkan interaksi antara aktor (pengguna sistem) dengan fungsionalitas utama aplikasi TBScan.

| ACTORS 👤 Admin   • Kelola master data   • Lihat statistik   • Kelola pengguna 👨‍⚕️ Dokter   • Semua UC Kader \+   • Buat diagnosis 👤 Kader TB   • Login & logout   • Upload X-Ray   • Analisis AI   • Lihat riwayat   • Export PDF | USE CASES |
| :---- | :---- |
|  | **(UC-01) Login & Manajemen Akun** **Aktor:** Semua Aktor   **|   Relasi:** *—* |
|  | **(UC-02) Manajemen Data Pasien** **Aktor:** Dokter, Kader TB   **|   Relasi:** *UC-01 (include)* |
|  | **(UC-03) Upload Citra X-Ray** **Aktor:** Dokter, Kader TB   **|   Relasi:** *UC-02 (include)* |
|  | **(UC-04) Analisis AI & Prediksi TB** **Aktor:** Dokter, Kader TB   **|   Relasi:** *UC-03 (include)* |
|  | **(UC-05) Visualisasi Grad-CAM** **Aktor:** Dokter, Kader TB   **|   Relasi:** *UC-04 (extend)* |
|  | **(UC-06) Lihat Riwayat Pemeriksaan** **Aktor:** Semua Aktor   **|   Relasi:** *UC-01 (include)* |
|  | **(UC-07) Export Laporan PDF** **Aktor:** Dokter, Kader TB   **|   Relasi:** *UC-06 (extend)* |
|  | **(UC-08) Kelola Master Data** **Aktor:** Admin   **|   Relasi:** *UC-01 (include)* |
|  | **(UC-09) Dashboard Statistik** **Aktor:** Admin, Dokter   **|   Relasi:** *UC-01 (include)* |
|  | **(UC-10) Notifikasi Hasil Analisis** **Aktor:** Dokter, Kader TB   **|   Relasi:** *UC-04 (extend)* |

 

 

## **2\. Class Diagram**

Class Diagram menggambarkan struktur kelas, atribut, metode, dan relasi antar kelas dalam sistem.

| *«class»* User ──────────────────────── \- id: String \- name: String \- email: String \- role: UserRole \- createdAt: DateTime ──────────────────────── \+ login(): bool \+ logout(): void \+ register(): bool | *«class»* Patient ──────────────────────── \- id: String \- name: String \- age: int \- gender: String \- examinations: List ──────────────────────── \+ addExamination(): void \+ getHistory(): List \+ exportPDF(): File | *«class»* Examination ──────────────────────── \- id: String \- patientId: String \- xrayImageUrl: String \- prediction: Prediction \- createdAt: DateTime ──────────────────────── \+ analyze(): Prediction \+ getHeatmap(): Image \+ save(): bool |
| ----- | ----- | ----- |
| *«class»* **Prediction** ──────────────────────── \- id: String \- label: String \- confidence: double \- heatmapUrl: String \- recommendation: String ──────────────────────── \+ getLabel(): String \+ isPositive(): bool | *«class»* **AIService** ──────────────────────── \- modelPath: String \- threshold: double \- gradCamLayer: String ──────────────────────── \+ loadModel(): void \+ predict(img): Prediction \+ generateGradCAM(): Image \+ preprocessImage(): Tensor | *«class»* **Report** ──────────────────────── \- examinationId: String \- generatedAt: DateTime \- format: String ──────────────────────── \+ generate(): File \+ share(): void \+ print(): void |
| **Relasi Antar Kelas:** • User 1 ──── \* Examination  (creates) : Satu user dapat membuat banyak pemeriksaan • Patient 1 ── \* Examination  (has)    : Satu pasien memiliki banyak riwayat pemeriksaan • Examination 1 ─ 1 Prediction (generates) : Setiap pemeriksaan menghasilkan satu prediksi • AIService ◇──── Examination  (uses)  : Examination menggunakan AIService untuk analisis • Examination ──── Report     (generates) : Pemeriksaan dapat dikonversi menjadi laporan PDF |  |  |

 

 

## **3\. Activity Diagram**

Activity Diagram berikut menggambarkan alur lengkap proses analisis TB dari upload gambar hingga tampil hasil di aplikasi mobile.

| 📱 MOBILE APP (Flutter) |   | ☁️ BACKEND \+ AI ENGINE |
| ----- | :---- | ----- |
| **● START** ↓ Buka Aplikasi ↓ Login Pengguna ↓ Pilih / Buat Data Pasien ↓ Upload Foto X-Ray (Kamera / Galeri) ↓ \[Validasi format & ukuran\]   ↓  valid  |  ↓  invalid Preview Gambar   ↓  invalid → Pesan Error → Ulang ↓ Tekan 'Analisis' ↓ POST /predict Tampil Loading... ↓ response JSON Tampil Hasil:   Label | Confidence   Heatmap | Rekomendasi ↓ Auto-save ke Database ↓ Export PDF / Selesai ↓ **⬛ END** |   |                 ← Terima Image ↓ Preprocessing resize(224×224) \+ normalize ↓ Inference MobileNetV2 → confidence score ↓ Generate Grad-CAM → heatmap overlay ↓ \[TB Positif?\] YES → label \= TB POSITIF NO  → label \= NORMAL ↓ **Return JSON Response** {label, confidence, heatmap\_base64, recommendation, timestamp} →   |

 

 

## **4\. Component Diagram**

Component Diagram menggambarkan komponen-komponen sistem, dependensi, dan antarmuka antar komponen.

| TBSCAN SYSTEM COMPONENT ARCHITECTURE |  |
| :---: | ----- |
| 📱 **LAYER 1 — MOBILE APP (Flutter)** |  **UI Layer** *Screens & Widgets* **State Mgmt** *Bloc / Riverpod* **Camera Svc** *image\_picker pkg* **API Client** *http / dio* **Local DB** *Hive / SQLite*  |
| ☁️ **LAYER 2 — BACKEND API (Flask/FastAPI)** |  **Auth Module** *JWT \+ Firebase Auth* **Predict Endpoint** *POST /api/predict* **GradCAM Module** *tf-explain \+ OpenCV* **Report Generator** *reportlab PDF*  |
| 🤖 **LAYER 3 — AI ENGINE (TensorFlow)** |  **MobileNetV2** *CNN Backbone* **Grad-CAM** *XAI Visualizer* **Preprocessor** *Image Pipeline* **TFLite Model** *On-device Inference*  |
| 🗄️ **LAYER 4 — DATA LAYER (Firebase)** |  **Firestore** *NoSQL Database* **Firebase Storage** *Image & Heatmap* **Firebase Auth** *User Auth* **FCM** *Push Notif*  |

 

 

## **5\. Deployment Diagram**

Deployment Diagram menggambarkan distribusi fisik komponen sistem pada infrastruktur perangkat keras dan cloud.

| 📱  \<\<device\>\> User Mobile Device Android 8+ / iOS 13+ | ☁️  \<\<cloud server\>\> Google Cloud Platform Cloud Run / GCE (Asia-SE) | 🔥  \<\<cloud platform\>\> Google Firebase BaaS (asia-southeast1) |
| ----- | ----- | ----- |
| **«artifact»TBScan.apk / .ipa** ──────────────────── **Components:** • Flutter UI Engine • TFLite Runtime • Hive Local DB • Firebase SDK • HTTP Client (Dio) ──────────────────── **Specs / Protocol:** *• HTTPS (TLS 1.3)* *• WebSocket (notif)* | **«container» Dockertbscan-api:latest** ──────────────────── **Components:** • Flask/FastAPI App • TF Model Server • Grad-CAM Engine • Nginx (Reverse Proxy) • Gunicorn (WSGI) ──────────────────── **Specs / Protocol:** *• CPU: 4 vCPU* *• RAM: 8 GB* *• GPU: Optional (T4)* | **Services:• Firebase Auth• Firestore (NoSQL)• Firebase Storage• FCM Push Notif.** ──────────────────── **Components:** • Email \+ Google SSO • users collection • patients collection • examinations col. • X-Ray \+ Heatmap ──────────────────── **Specs / Protocol:** *• Firestore Security Rules* *• Storage Security Rules* |
| **Communication Channels:** • Mobile App  ←— HTTPS/REST —→  Cloud Run API  (port 443, JSON payload, max 5MB) • Mobile App  ←— Firebase SDK —→  Firebase Services  (Firestore SDK, Auth SDK, FCM) • Cloud Run   ←— Internal VPC —→  Firebase Admin SDK  (service account, gRPC) • CI/CD: GitHub Actions → Docker Build → Push to GCR → Deploy Cloud Run (on merge to main) |  |  |

# **E. DATASET OPEN PUBLIC**

Sesuai ketentuan, project ini menggunakan dataset Chest X-Ray open public yang bersumber dari institusi medis dan akademik terkemuka. Seluruh dataset memiliki label yang jelas, sumber yang terverifikasi, dan lisensi yang mengizinkan penggunaan untuk riset dan pendidikan.

| No | Nama Dataset | Sumber | Jumlah Citra | Label | Link / DOI |
| :---: | :---- | :---- | ----- | :---- | :---- |
| 1 | **Montgomery County Chest X-Ray** | National Library of Medicine (NLM) / US NIH | 138 CXR (58 TB, 80 Normal) | TB Positive / Normal | openi.nlm.nih.gov/imgs/collections/NLM-MontgomeryCXRSet.zip |
| 2 | **Shenzhen Hospital Chest X-Ray** | Shenzhen No.3 People's Hospital / NLM | 662 CXR (336 TB, 326 Normal) | TB Positive / Normal | openi.nlm.nih.gov/imgs/collections/ChinaSet\_AllFiles.zip |
| 3 | **NIH Chest X-ray14** | National Institutes of Health (NIH) Clinical Center | 112,120 CXR, 14 penyakit | 14 label termasuk Infiltration | kaggle.com/datasets/nih-chest-xrays/data |
| 4 | **TBX11K Dataset** | MICCAI 2020 Workshop on TB Detection | 11,200 CXR (1,200 TB, 10,000 Healthy/Sick) | TB / Healthy / Sick | kaggle.com/datasets/usmanshams/tbx-11 |
| 5 | **VinDr-CXR** | Vinmec Healthcare System (Vietnam) | 18,000 CXR berlabel dari 17 radiolog | 22 kondisi paru termasuk TB | physionet.org/content/vindr-cxr/1.0.0/ |

 

 

## **Dataset yang Digunakan dalam Project ini**

* Montgomery County CXR \+ Shenzhen Hospital CXR sebagai dataset utama karena label TB yang eksplisit dan bersih

* TBX11K sebagai dataset tambahan untuk meningkatkan volume data training

* Total kombinasi: ±12.000 citra X-Ray berlabel (TB Positif dan Normal)

 

 

## **Struktur Master Data Dinamis pada Sistem**

Sesuai ketentuan project, sistem dirancang dengan master data yang dinamis dan dapat dikonfigurasi oleh Admin. Berikut adalah koleksi/tabel master data yang tersedia:

| No | Master Data | Field | Keterangan |
| :---: | :---- | :---- | :---- |
| 1 | **m\_thresholds** | threshold\_id\*, name, value, description, updated\_by, updated\_at | Threshold confidence level model AI (default 50%). Admin bisa ubah tanpa recompile app |
| 2 | **m\_fasyankes** | faskes\_id\*, name, address, type, province, contact | Data fasilitas kesehatan yang terdaftar untuk rujukan hasil TB positif |
| 3 | **m\_roles** | role\_id\*, role\_name, permissions (JSON), description | Hak akses per role: Admin, Dokter, Kader TB — dapat dikonfigurasi granular |
| 4 | **m\_jenis\_pemeriksaan** | jenis\_id\*, name, description, ai\_model\_version, active | Jenis pemeriksaan (TB Screening, Follow-up, dll), version model terkait |
| 5 | **m\_rekomendasi** | rekomendasi\_id\*, label, confidence\_range, text, priority | Teks rekomendasi tindak lanjut berdasarkan label dan range confidence, dapat diubah Admin |
| 6 | **m\_app\_config** | config\_key\*, config\_value, description, editable | Konfigurasi umum: max file size upload, supported formats, API base URL |

 

 

| RINGKASAN TEKNOLOGI YANG DIGUNAKAN |  |  |
| ----- | :---- | :---- |
| **Kategori** | **Teknologi** | **Fungsi** |
| **AI / Deep Learning** | **TensorFlow 2.x \+ Keras** | Training model CNN (MobileNetV2) |
| **Explainable AI** | **Grad-CAM (tf-explain)** | Visualisasi area fokus penyakit |
| **Mobile Frontend** | **Flutter 3.x (Dart)** | Cross-platform mobile app |
| **Backend API** | **Flask \+ Python 3.10** | Inference server & API endpoints |
| **Cloud & Database** | **Google Firebase \+ GCP** | Auth, Storage, Firestore, Hosting |
| **Deployment** | **Docker \+ Cloud Run** | Containerized scalable backend |
| **Model Optimization** | **TensorFlow Lite (int8)** | On-device inference di mobile |
| **CI/CD** | **GitHub Actions** | Automated testing & deployment |

