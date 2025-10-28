# Retina Damar Segmentasyonu


Bu proje, retina görüntülerinde **kalın ve ince damarların tespitini ve segmentasyonunu** gerçekleştiren bir derin öğrenme pipeline’ını içermektedir. Proje, **U-Net tabanlı modeller** kullanılarak damar yapılarının otomatik olarak tespit edilmesini sağlar.

---

## Proje Aşamaları

### 1. Kalın Damarların Tespiti
1. Retina görüntülerinin **gri seviyede yüklenmesi**  
2. **Sharpening (keskinleştirme)** ile damar hatlarının belirginleştirilmesi  
3. **Skeletonize** ile label görüntüsünün damar merkez çizgisinin elde edilmesi  
4. Skeleton görüntüde gezilen her damardan **19x19 boyutlu patchler** alınması ve ilgili label ile retina patchlerinin eşleştirilmesi  
5. **Gaussian Pyramid** ile skeleton, label ve retina patchlerinin 3 farklı seviyesinin çıkarılması ve U-Net modeline verilmesi  
6. Eğitime uygun olmayan patchlerin elenmesi (belli kalınlığın altındaki damarlar alınmadı)  
7. Eşleştirilen patchlerle **model eğitim verilerinin hazırlanması**  
8. **Modelin eğitimi ve test edilmesi**

---

### 2. İnce Damarların Tespiti
1. Retina görüntülerinin **gri seviyede yüklenmesi**  
2. **Sharpening** ile damar hatlarının belirginleştirilmesi  
3. Label görüntüsünün **BWDist** ile ince ve kalın damarların ayrıştırılması  
4. Sadece **ince damarlar** üzerinde skeletonize uygulanarak tek pikselli yapı elde edilmesi  
5. Skeleton görüntü üzerinde belli bir eşik değerinin üstündeki yapılar takip edilerek patchler alınması  
6. Alınan patchlerin label ve retina karşılıklarının çıkarılması  
7. Patchlerin **Gaussian Pyramid** ile 3 seviyeli versiyonlarının oluşturulması  
8. Retina patchlerinin level 1 halinin 2 kat büyütülmüş hali ile level 0’daki hali modele verilir, model çıktısı ile label level 0 karşılaştırılır  
9. **Kalın ve ince damar modellerinin birleştirilmesi** ile tek bir final model elde edilir

---

## Model ve Veri Linki

- Eğitilmiş model ve patch verileri [Kaggle linki](https://www.kaggle.com/models/batuhannacitarhan/retina-damar-segmentasyonu-pth) üzerinden erişilebilir.

---

## İletişim

- **LinkedIn:** [https://www.linkedin.com/in/batuhan-nacitarhan](https://www.linkedin.com/in/batuhan-nacitarhan)  
- **GitHub:** [https://github.com/BatuhanNacitarhan](https://github.com/BatuhanNacitarhan)  
- **E-posta:** batuhannacitarhan@gmail.com

