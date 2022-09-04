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
    




