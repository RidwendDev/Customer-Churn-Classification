# Project Machine Learning Expert - Ridwan Akmal
## **Domain Proyek**
### **Latar Belakang** 
Dalam dunia bisnis, mendapatkan pelanggan baru cukuplah sulit lagipun menghabiskan biaya yang lebih mahal daripada mempertahankan pelanggan yang sudah ada. Mengapa? karena ketika mencari pelanggan baru maka perlu menghabiskan banyak  waktu dan biaya lagi untuk memikat hati calon pelanggan yang tentu saja belum pasti akan membuahkan hasil. Dalam penelitian yang dilakukan oleh Frederick Reichheld dari Bain & Company yang menunjukkan peningkatan tingkat penahanan pelanggan sebesar 5% meningkatkan keuntungan sebesar 25% hingga 95%. Sederhananya mempertahankan pelanggan yang tepat itu berharga. Salah satu metrik utama dalam memahami apakah perusahaan mempertahankan pelanggan adalah tingkat customer churn rate. Churn rate secara definisi diartikan sebagai hitungan persentase pelanggan atau pembeli yang tidak lagi mau berlangganan atau membeli produk. Churn rate pada umumnya dihitung pada rentang waktu spesifik tertentu seperti per bulan, kuartal, dan tahunan.Singkatnya, churn rate adalah tingkat retensi pelanggan. Saat kita dapat melakukan prediksi dengan metode yang tepat. Salah satunya adalah dengan menerapkan machine learning. Saya rasa kita dapat terbantu untuk setidaknya mengantisipasi tingkat churn yang meningkat dengan memanfaatkan fitur-fitur yang ada.Berdasarkan hal tersebut, saya berinisiatif melakukan penelitian tentang Klasifikasi tingkat Churn dari Customer suatu perusahaan Telekomunikasi.

## **Business Understanding**
### **Problem Statement**
Berdasarkan pada latar belakang di atas, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut:

* Bagaimana keterkaitan fitur seperti gender, Techsupport, Payment Method dapat berpengaruh dalam tingkat Churn?
* Bagaimana cara memproses data yang ada didalam dataset perusahaan telekomunikasi tersebut sehingga dapat di latih dengan baik oleh model machine learning?
* Bagaimana membangun model machine learning yang dapat mengklasifikasikan churn dari para customer?

### **Goals**
Tujuan dibuatnya proyek ini adalah sebagai berikut:

* Mendapatkan analisa yang cukup untuk memahami dataset churn dari perusahaan telekomunikasi.
* Melakukan EDA dan preprocesing agar dapat diolah dan dimengerti oleh model.
* Membuat model machine learning yang dapat memahami pola pada data dengan baik.

### **Solution Statement**
Solusi yang dapat diterapkan agar goals diatas terpenuhi adalah sebagai berikut:

* Mendapatkan analisa yang cukup untuk memahami dataset churn dari perusahaan telekomunikasi.  Analisa yang dapat dilakukan yaitu, seperti:
    * Menangani _missing value_
    * Memeriksa korelasi antar data penting untuk memahami hubungan data target dan data fitur baik numerik maupun kategorik.

* Melakukan EDA dan preprocesing agar dapat diolah dan dimengerti oleh model, seperti:
    * Mengatasi nilai NaN/missing value
    * Memplot grafik-grafik yang memiliki keterkaitan antar fitur-fitur dengan target
    * Melakukan encode pada data pada fitur kategorik.
    * Melakukan scalling di fitur numerik

* Membuat model machine learning yang dapat memahami pola pada data dengan baik. Beberapa algoritma yang akan saya gunakan yaitu, sebagai berikut:
    * Support Vector Classifier
    * K-Nearest Neighbours
    * Random Forest Classifier
    
## **Data Understanding**
Dataset yang di gunakan pada proyek machine learning ini merupakan dataset churn dari perusahaan telekomunikasi. Dataset tersebut dapat di unduh di website kaggle: [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn).

Setelah dilakukan analisa pada data, didapatkan informasi bahwa:

* Format dataset yaitu CSV (Comma-Seperated Values)
* Jumlah kolom data yang terdapat didalam dataset berjumla 20 kolom
* Dataset berdimensi 7043 baris dan 20 kolom
* Terdapat 18 kolom data yang memiliki tipe data object 
* Terdapat 1 kolom data yang memiliki tipe data float64
* Terdapat 2 kolom data yang memiliki tipe data int64
* Terdapat _missing value_ pada dataset


### **Fitur-fitur pada dataset antara lain sebagai berikut:**
Kumpulan data mencakup informasi tentang:
* Pelanggan yang pergi dalam sebulan terakhir – kolomnya disebut `Churn`
* Layanan yang telah didaftarkan oleh setiap pelanggan –  phone service, multiple lines, internet services, online security, online backup, device protection, tech support, and streaming TV dan streaming movies
* Informasi akun pelanggan - seperti contract, payment method, paperless billing, monthly charges, and total charges
* Info demografis tentang pelanggan – gender, tenure, lalu Partner, Dependents

Kita akan mengambil salah satu sampel data numeriknya, di program akan ditampilkan tidak ada nilai yang outlier
<image src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/out.png?raw=true'>
   
Karena terdapat nilai missing value pada kolom Total charges kita akan melakukan imputation, untuk itu sebelumnya kita akan lihat distribusi datanya agar dapat memilih metode yang terbaik.<br>
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/hist%20total.png?raw=true'>

Dari grafik  terlihat bahwa distribusi skewness sehingga akan kita lakukan imputation dengan metode median. 
    
## Analisis Univariat dan Multivariat
Baik kita akan mulai fokus menganalisis korelasi data pada feature-feature baik numerik maupun kategorik terhadap target kita(Churn). Untuk lebih lengkapnya dapat dilihat pada kode programnya, karena disini hanya akan menggambarkan sedikit pattern yang cukup menarik.
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/corr%20numer.png?raw=true'>
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/paymet.png?raw=true'>
   * Dapat dilihat dari grafik customer yang churn(pindah) dengan tingkat presentase terttnggi adalah yang menggunakan Elektronik check sebagai Metode Pembayaran.
   * Pelanggan yang memilih mailed check,bank transfer, credit card(automatic) sebagai Metode Pembayaran cenderung tidak pindah.
   
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/depen.png?raw=true'>

   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/partner.png?raw=true'>
   
   * Pelanggan yang tidak memiliki dependents(tanggungan) cenderungnya akan churn
   * Pelanggan yang tidak memiliki partners(pasangan) cenderungnya akan churn
   
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/monthlykde.png?raw=true'>
   
   * Terlihat dari grafik bahwa customer dengan monthly charges yang lebih tinggi akan cenderung lebih churn
   
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/tenurekde.png?raw=true'>
   
   * Terlihat dari grafik bahwa customer dengan tenure yang lebih tinggi akan lebih loyal dan sebaliknya pula customer baru akan cenderung lebih churn
   
    
## **Data Preparation**
Berikut merupakan tahapan dalam mempersiapkan data untuk keperluan pelatihan model:
### **Split dataset**
Membagi dataset menjadi data latih (_train_) dan data uji (_test_) merupakan hal yang harus kita lakukan sebelum membuat model.Data latih adalah sekumpulan data yang akan digunakan oleh model untuk melakukan pelatihan. Sedangkan, data uji adalah sekumpulan data yang akan digunakan untuk memvalidasi kinerja pada model yang telah dilatih. Proporsi pembagian yang saya lakukan pada dataset ini menggunakan proporsi pembagian 80:20 yang berarti sebanyak 80% merupakan data latih dan 20% persen merupakan data uji.
   
### **Normalisasi data**
Melakukan transformasi pada data fitur fitur yang akan dipelajari oleh model menggunakan _library_ _StandardScaler_. _StandardScaler_ mentransformasikan fitur dengan menskalakan setiap fitur ke rentang tertentu. _Library_ ini menskalakan dan mentransformasikan setiap fitur secara individual sehingga berada dalam rentang yang diberikan pada set pelatihan, _StandardScaler()_ akan menormalkan fitur-fitur (setiap kolom X) sehingga setiap kolom/fitur/variabel akan memiliki mean = 0 dan standard deviation = 1. Dengan merenapkan teknik normalisasi data, model akan dengan lebih mudah mengenali pola-pola yang terdapat pada data sehingga akan menghasilkan prediksi yang lebih baik daripada tidak menggunakan teknik normalisasi.

## **Modeling**
Algoritma _machine learning_ yang digunakan pada proyek ini yaitu _Support Vector Classifier, K-Nearest Neighbours, Random Forest Classifier_.
### **Support Vector Classifier**
_Support Vector Classifier_ (SVC)berusaha mencari ‘jalan’ terbesar yang bisa memisahkan sampel-sampel dari kelas berbeda, maka pada kasus regresi SVR berusaha mencari jalan yang dapat menampung sebanyak mungkin sampel di ‘jalan’.

Pada tahap ini model akan melakukan pelatihan terhadap data latih untuk mendapatkan error seminimal mungkin, kemudian setelah pelatihan model melakukan prediksi terhadap data yang belum pernah di lihat sebelumnya menggunakan data uji. Adapun algoritma ini memiliki keunggulan dan kekurangan.
Keunggulannya seperti SVC efektif pada data berdimensi tinggi (data dengan jumlah fitur atau atribut yang sangat banyak).Adapun kelemahan dari  Support Vector Classifier: Sulit dipakai dalam problem berskala besar. Skala besar dalam hal ini dimaksudkan dengan jumlah sample yang diolah.
   
### **K-Nearest Neighbours**
K-nearest neighbor adalah salah satu algoritma machine learning dengan pendekatan supervised learning yang bekerja dengan mengkelaskan data baru menggunakan kemiripan antara data baru dengan sejumlah data (k) pada lokasi yang terdekat yang telah tersedia. Algoritma ini menerapkan lazy learning” atau “instant based learning” dan merupakan algoritma non parametrik. Algoritma KNN digunakan untuk klasifikasi dan regresi. Pada pembuatan model ini akan menggunaka modul KNN yang terlah di sediakan oleh library _scikit-learn_ .Pada model ini hanya akan menggunakan 1 parameter yaitu `n_neighbours` (Jumlah tetangga). Jumlah _neighbours_ yang di gunakan yaitu sejumlah 11 neighbours. Kemudian, untuk menentukan titik mana dalam data yang paling mirip dengan input baru, KNN menggunakan perhitungan ukuran jarak. Metrik ukuran jarak yang digunakan secara default pada library sklearn adalah Minkowski distance. Setelah menentukan nilai-nilai pada parameter model melakukan pelatihan menggunakan data latih setelah itu model akan melakukan prediksi terhadap data yang belum pernah dilihat dengan menggunakan data uji. Namun algoritma ini memiliki keunggulan dan kekurangan.

Berikut keunggulan K-Nearest Neighbours:

* Sangat sederhana dan mudah dipahami
* Sangat mudah diterapkan
* Dapat digunakan dalam proses klasifikasi maupun regresi.
* Sangat mudah jika akan dilakukan penambahan data
* Parameter yang diperlukan sedikit, yaitu hanya jumlah tetangga yang dipertimbangkan (K), dan metode perhitungan jaraknya (distance metrik)

Berikut kelemahan K-Nearest Neighbours:

* Perlu menentukan nilai K yang tepat.
* Computation cost yang tinggi
* Waktu pemrosesan yang lama jika datasetnya sangat besar.
* Tidak cukup bagus jika diterapkan pada high dimensional data
* Sangat sensitif pada data yang memiliki banyak noise (noisy data), banyak data yang hilang (missing data), dan pencilan (outliers).

### **Random Forest Classifier**
Algoritma ini merupakan sekumpulan algoritma decision tree. Konsep dasar decision tree adalah mengubah data menjadi aturan-aturan keputusan. Kombinasi dari masing–masing decision tree yang baik kemudian dikombinasikan ke dalam satu model. Random Forest bergantung pada sebuah nilai vector random dengan distribusi yang sama pada semua pohon yang masing masing decision tree memiliki kedalaman yang maksimal. Algoritma ini bisa menyelesaikan permasalahan klasifikasi dan regresi. Pada kasus klasifikasi, prediksi akhir diambil dari prediksi terbanyak pada seluruh pohon. Sedangkan, pada kasus regresi, prediksi akhir adalah rata-rata prediksi seluruh pohon. Untuk pembuatan model Random Forest, akan menggunakan beberapa parameter, antara lain:
* `n_estimator`: jumlah trees (pohon) di forest. Di sini saya set `n_estimator`=500.
Setelah itu model akan melakukan pelatihan menggunakan data latih, setelah itu model bisa melakukan prediksi pada data yang belum pernah diliath dengan menggunakan data uji. Namun model ini sama seperti yang lainnya mempunyai plus minusnya.
   
Keunggulan Random Forest:
* Algoritma Random Forest merupakan algoritma dengan pembelajaran paling akurat yang tersedia. Untuk banyak kumpulan data, algoritma ini menghasilkan pengklasifikasi yang sangat akurat.
* Berjalan secara efisien pada data besar.
* Memiliki metode yang efektif untuk memperkirakan data yang hilang dan menjaga akurasi ketika sebagian besar data hilang.
   
Kelemahan Random Forest:
* Algoritma Random Forest overfiting untuk beberapa kumpulan data dengan tugas klasifikasi/regresi yang noise.

Pada proyek ini yang menjadi model dengan solusi terbaik adalah _Random Forest Classifier_. Dimana model ini memiliki nilai Akurasi paling tinggi dari kedua model lainnya.
   
## **Evaluation**
Pada proyek machine learning ini, didapatkan model terbaik dengan akurasi diatas 80% adalah Random Forest Classifier
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/model.png?raw=true'>
   
Untuk klasifikasi sesudah kita mendapatkan akurasi terbaik kita juga bisa memanfaatkan Confusion matrix
   <img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/cf.png?raw=true'>

Adapun penjelasannya sebagai berikut:
   * True Positive (TP) : Jumlah data yang bernilai Positif dan diprediksi benar sebagai Positif.
   * False Positive (FP) : Jumlah data yang bernilai Negatif tetapi diprediksi sebagai Positif.
   * False Negative (FN) : Jumlah data yang bernilai Positif tetapi diprediksi sebagai Negatif.
   * True Negative (TN) : Jumlah data yang bernilai Negatif dan diprediksi benar sebagai Negatif.
   
Confusion matrix testing model terbaik:<br>
<img src='https://github.com/RidwendDev/Customer-Churn-Classification/blob/main/Visualizations/ev%20rf.png?raw=true'>
   <br>Kesimpulan dari evaluasinya:
   Dari data terlihat bahwasannya model mampu memprediksi data dengan menghasilkan akurasi sebesar 80%, dengan detil tebakan churn yang sebenernya benar churn  adalah 185, tebakan tidak churn yang sebenernya tidak churn adalah 948, tebakan tidak churn yang sebenernya benar churn adalah 189 dan tebakan churn yang sebenernya tidak churn adalah 87.
   
   
   
   
   
