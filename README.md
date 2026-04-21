🏡 K-Nearest Neighbors (KNN) ile Ev Fiyat Tahmini

Bu projede, ev satış fiyatlarını tahmin etmek amacıyla K-Nearest Neighbors (KNN) algoritması uygulanmıştır. Çalışmanın temel hedefi, KNN’in ölçek duyarlılığı, K parametresinin etkisi, aşırı uyum (overfitting) davranışı ve model seçimi gibi kritik noktalarını deneysel olarak incelemektir. Son aşamada KNN modeli, Linear Regression modeli ile karşılaştırılmıştır.

📌 Proje Amaçları
KNN algoritmasının mesafe tabanlı yapısını anlamak
Özellik ölçeklemenin (scaling) KNN performansına etkisini gözlemlemek
Küçük K değerlerinde aşırı uyumu incelemek
En uygun K değerini belirlemek
KNN ve Linear Regression modellerini aynı metriklerle karşılaştırmak
📊 Veri Seti
Veri seti: houses_clean.csv
Hedef değişken: SalePrice
Özelliklerin çoğu önceden normalize edilmiştir
GrLivArea değişkeni bilinçli olarak farklı ölçekte bırakılmıştır
(ölçek duyarlılığını göstermek için)
🧪 Uygulanan Adımlar
1. Veri Yükleme ve İnceleme
Veri seti projeye dahil edildi
Tanımlayıcı istatistikler incelendi
GrLivArea değişkeninin diğer özelliklere kıyasla farklı ölçekte olduğu gözlemlendi
2. Varsayılan KNN Modeli
Varsayılan KNeighborsRegressor (k=5) kullanıldı
5-fold cross-validation ile R² skoru hesaplandı
Sonuç base_knn_score değişkeninde saklandı
3. Ölçek Duyarlılığı (Scaling)
Tüm özellikler MinMaxScaler ile 0–1 aralığına ölçeklendi
Ölçeklenmiş veri üzerinde KNN tekrar değerlendirildi
Performans artışı gözlemlendi
Sonuç rescaled_score değişkeninde saklandı
4. K Parametresi Optimizasyonu
K değerleri 1–25 aralığında denendi
Her K için cross-validation R² skorları hesaplandı
Performans–K grafiği çizildi
En iyi performans k = 11 civarında elde edildi
En uygun K değeri best_k değişkenine atandı
5. Aşırı Uyum (Overfitting) Analizi
k = 2 için train ve test skorları karşılaştırıldı
Eğitim skoru yüksek, test skoru düşük bulundu
Bu durumun küçük K değerlerinden kaynaklanan aşırı uyum olduğu gözlemlendi
6. İdeal K ile Model Davranışı
best_k değeri kullanılarak model yeniden eğitildi
Train ve test skorlarının birbirine yakın olduğu görüldü
Bu durum daha iyi genelleştirme yapıldığını gösterdi
7. Model Hatası (MAE)
Optimize edilmiş KNN modeli için Mean Absolute Error (MAE) hesaplandı
Cross-validation ile neg_mean_absolute_error metriği kullanıldı
Ortalama fiyat tahmin hatası price_error değişkeninde saklandı
8. Model Seçimi
Aynı veri ve aynı metrikle Linear Regression modeli değerlendirildi
Linear Regression MAE değeri KNN ile karşılaştırıldı
KNN modelinin daha düşük hata yaptığı gözlemlendi
Nihai model seçimi:
best_model = "KNN"
🏆 Sonuç
KNN modeli, uygun ölçekleme ve K optimizasyonu sonrası Linear Regression modelini geride bırakmıştır
KNN’in doğrusal olmayan ilişkileri yakalayabilmesi bu performans farkının temel nedenidir
Mesafe tabanlı algoritmalar için ölçekleme ve hiperparametre ayarlamanın kritik olduğu açıkça gözlemlenmiştir
🧠 Çıkarımlar
KNN mesafe tabanlı olduğu için ölçekleme hayati öneme sahiptir
Küçük K → aşırı uyum
Büyük K → aşırı genelleme
Doğru K değeri bias–variance dengesini sağlar
🚀 Kullanılan Teknolojiler
Python
pandas
scikit-learn
matplotlib
Jupyter Notebook
📁 Proje Yapısı
S16D1-S-data-knn/
│
├── data/
│   └── houses_clean.csv
├── KNN.ipynb
├── README.md
├── dataset-description.md
└── tests/
