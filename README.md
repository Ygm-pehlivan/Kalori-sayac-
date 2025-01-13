import matplotlib.pyplot as plt

# Kadın ve erkeklerin ortalama günlük kalori ihtiyaçları (kalori cinsinden)
kadın_günlük_kalori_ihtiyacı = 2000
erkek_günlük_kalori_ihtiyacı = 2500

# Besin türlerinin gram başına kalori miktarları
besinler = {
    "karbonhidrat": 4, # 1 gram karbonhidrat = 4 kalori
    "protein": 4,      # 1 gram protein = 4 kalori
    "yağ": 9,          # 1 gram yağ = 9 kalori
    "elma": 0.52,      # 1 gram elma = 0.52 kalori
    "muz": 0.89,       # 1 gram muz = 0.89 kalori
    "pirinç": 1.3,     # 1 gram pişmiş pirinç = 1.3 kalori
    "ekmek": 2.64,     # 1 gram beyaz ekmek = 2.64 kalori
    "tavuk": 2.39,     # 1 gram pişmiş tavuk = 2.39 kalori
    "peynir": 4.02,    # 1 gram peynir = 4.02 kalori
    "yumurta": 1.55    # 1 gram pişmiş yumurta = 1.55 kalori
}

# Ortalama ağırlıklar
agirliklar = {
    "elma": 182,       # 1 adet elmanın gramı
    "muz": 118,        # 1 adet muzun gramı
    "pirinç": 158,     # gram (1 fincan pişmiş pirinç)
    "ekmek": 28,       # gram (1 dilim beyaz ekmek)
    "tavuk": 140,      # gram (1 porsiyon pişmiş tavuk)
    "peynir": 28,      # gram (1 dilim peynir)
    "yumurta": 50      # 1 adet yumurtanın gramı
}
 #besinler ve ağırlıklar dictionery kullanılarak yazılmıştır.
 # Kullanıcıdan alınan gram miktarları
cinsiyet = str(input("Cinsiyetiniz nedir? ").lower())

# Haftalık kalori alımı için veri girişi
haftalik_kalori_alimi = []
for gun in range(7):
    print(f"\n{gun + 1}. Gün:")

  # Günlük karbonhidrat, protein ve yağ alımı
    karbonhidrat_g = float(input("Günlük kaç gram karbonhidrat almak istiyorsunuz? "))
    protein_g = float(input("Günlük kaç gram protein almak istiyorsunuz? "))
    yağ_g = float(input("Günlük kaç gram yağ almak istiyorsunuz? "))

    # Sabah öğünü besinleri
    elma_adet_sabah = int(input("Sabah kaç adet elma yemek istiyorsunuz? "))
    yumurta_adet_sabah = int(input("Sabah kaç adet yumurta yemek istiyorsunuz? "))
    peynir_adet_sabah = int(input("Sabah kaç dilim peynir yemek istiyorsunuz? "))
    ekmek_adet_sabah = int(input("Sabah kaç adet ekmek yemek istiyorsunuz? "))

    # Öğlen öğünü besinleri
    muz_adet_oglen = int(input("Öğlen kaç adet muz yemek istiyorsunuz? "))
    elma_adet_oglen = int(input("Öğlen kaç adet elma yemek istiyorsunuz? "))

    # Akşam öğünü besinleri
    pirinç_adet_aksam = int(input("Akşam kaç fincan pişmiş pirinç yemek istiyorsunuz? "))
    ekmek_adet_aksam = int(input("Akşam kaç dilim ekmek yemek istiyorsunuz? "))
    tavuk_adet_aksam = int(input("Akşam kaç porsiyon pişmiş tavuk yemek istiyorsunuz? "))
    #Gram cinsindekiler ondalıklı sayıyla yazılabileceğinden float veri tipini kullandım,adetler ise doğal sayı olduğundan integer veri tipini kullandım.

    # Günlük toplam kalori hesaplama
    toplam_kalori_gunluk = (
        (karbonhidrat_g * besinler["karbonhidrat"]) +
        (protein_g * besinler["protein"]) +
        (yağ_g * besinler["yağ"]) +
        (elma_adet_sabah * agirliklar["elma"] * besinler["elma"]) +
        (yumurta_adet_sabah * agirliklar["yumurta"] * besinler["yumurta"]) +
        (peynir_adet_sabah * agirliklar["peynir"] * besinler["peynir"]) +
        (ekmek_adet_sabah * agirliklar["ekmek"] * besinler["ekmek"]) +

        (muz_adet_oglen * agirliklar["muz"] * besinler["muz"]) +
        (elma_adet_oglen * agirliklar["elma"] * besinler["elma"]) +

        (pirinç_adet_aksam * agirliklar["pirinç"] * besinler["pirinç"]) +
        (ekmek_adet_aksam * agirliklar["ekmek"] * besinler["ekmek"]) +
        (tavuk_adet_aksam * agirliklar["tavuk"] * besinler["tavuk"])
    )
    haftalik_kalori_alimi.append(toplam_kalori_gunluk)
"""
Yukarıdaki kalori hesaplaması; alınan karbonhidrat, protein ve yağ oranlarının 1 gramındaki kalori değerleri ile
çarpılıp toplanmasıyla hesaplanmıştır. Besinlerin kalori hesaplaması da ağırlıkları ve kalori değerlerinin
çarpılıp toplanmasıyla toplam kalori hesaplanmıştır.
"""
#besinleri ve ağırlıkları yazarken dictionery kullandığım için değerleri köşeli parantezle yazdım.

# Haftalık kalori alımını sütun grafiği şeklinde gösterme
gunler = ["Pazartesi", "Salı", "Çarşamba", "Perşembe", "Cuma", "Cumartesi", "Pazar"]
plt.bar(gunler, haftalik_kalori_alimi, color='skyblue')
plt.xlabel('Günler')
plt.ylabel('Kalori Alımı')
plt.title('Haftalık Günlük Kalori Alımı')
plt.axhline(y=(kadın_günlük_kalori_ihtiyacı if cinsiyet == "kadın" else erkek_günlük_kalori_ihtiyacı), color='r', linestyle='--', label='Günlük Kalori İhtiyacı')
plt.legend()
plt.show()

# Kalori miktarını aşma durumunda diyet önerme
for gun, kalori in zip(gunler, haftalik_kalori_alimi):
    if cinsiyet == "kadın" and kalori > kadın_günlük_kalori_ihtiyacı:
        print(f"\nUyarı: {gun} günü günlük kalori ihtiyacınızı aştınız. Daha dengeli bir diyet için daha az kalorili besinler tercih edin.")
    elif cinsiyet == "erkek" and kalori > erkek_günlük_kalori_ihtiyacı:
        print(f"\nUyarı: {gun} günü günlük kalori ihtiyacınızı aştınız. Daha dengeli bir diyet için daha az kalorili besinler tercih edin.")

