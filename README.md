# Gençlerin Çevrim İçi Davranışlarının Analizi ve Siber Güvenlik Risklerinin Öngörülmesi

Bu proje, Samsun Üniversitesi Yazılım Mühendisliği MYAZ468 Büyük Veri dersi için dönem projesi olarak geliştirilmiştir. Proje gençlerin çevrim içi aktivitelerine ilişkin verileri analiz ederek siber güvenlik davranışlarını sınıflandırmayı ve potansiyel riskleri öngörmeyi amaçlamaktadır. Proje kapsamında, veri madenciliği ve makine öğrenmesi yöntemleri kullanılarak veri ön işleme, özellik mühendisliği ve modelleme süreçleri gerçekleştirilmiştir.

## Proje Amacı

- Genç kullanıcıların çevrim içi davranışlarından yola çıkarak “Safe” ve “Risky” kategorilerine ayrılmalarını sağlayacak bir tahmin modeli geliştirmek.
- Riskli davranışlara neden olan etkenleri istatistiksel ve grafiksel olarak analiz etmek.
- Eğitim, ebeveyn farkındalığı ve teknik önlemler konusunda çıkarımlar yaparak siber güvenlik bilincinin artırılmasına katkı sağlamak.

## Kullanılan Veri Seti

- Kaynak: [Teenage Online Behavior and Cybersecurity Risks (Kaggle)](https://www.kaggle.com/datasets/datasetengineer/teenage-online-behavior-and-cybersecurity-risks/data)
- Boyut: 67.921 gözlem, 30 özellik
- Veri türleri: Teknik (VPN kullanımı, Firewall logları, Antivirus uyarıları) ve davranışsal (Sosyal medya kullanımı, reklam tıklamaları, parola gücü) değişkenler
- Veri anonimleştirilmiş olup kişisel bilgi içermemektedir.

## Kullanılan Yöntemler

### 1. Veri Ön İşleme
- Eksik değer kontrolü
- Kategorik verilerin sayısallaştırılması
- SMOTE ile sınıf dengesi sağlanması

### 2. Özellik Mühendisliği
- `Risk_Index`, `Suspicious_Flag`, `Download_And_Purchase_Risk` gibi yeni değişkenler türetildi
- Yaş grubu ve sosyal medya etkileşimi gibi çapraz öznitelikler oluşturuldu

### 3. Modelleme Aşamaları
- **Aşama 1:** Çok sınıflı XGBoost (başarısız oldu, dengesizlik sorunu)
- **Aşama 2:** 2 sınıflı XGBoost + türetilmiş öznitelikler
- **Aşama 3:** Ensemble (XGBoost + RandomForest + Logistic Regression)
- **Aşama 4:** KMeans ile kümeye dayalı temizlik + XGBoost

### 4. Görsel Analizler
- Parola gücü ve risk oranları
- Sosyal medya kullanımı ve risk ilişkisi
- VPN ve Risk davranışı ilişkisi
- Yaş dağılımı ve risk durumu
- Özellik önemleri ve ısı haritaları

## Sonuçlar

- En iyi doğruluk oranı %56 ile ensemble modelden elde edilmiştir.
- Dengelenmiş veri sayesinde Risky sınıfı da başarıyla tespit edilebilmiştir.
- Ancak özniteliklerin sınıflandırma gücü sınırlıdır, veri kalitesi bu nedenle performansın üst sınırını belirlemiştir.

## 📚 Kullanılan Kütüphaneler

- `pandas`, `numpy`, `scikit-learn`, `xgboost`, `matplotlib`, `seaborn`, `imblearn`
