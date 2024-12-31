
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
    "elma": 182, # 1 adet elmanın gramı
    "muz": 118, # 1 adet muzun gramı
    "pirinç": 158, # gram (1 fincan pişmiş pirinç)
    "ekmek": 28, # gram (1 dilim beyaz ekmek)
    "tavuk": 140, # gram (1 porsiyon pişmiş tavuk)
    "peynir": 28, # gram (1 dilim peynir)
    "yumurta": 50 # 1 adet yumurtanın gramı
} #besinler ve ağırlıklar dictionery kullanılarak yazılmıştır.

# Kullanıcıdan alınan gram miktarları
cinsiyet = str(input("Cinsiyetiniz nedir? ").lower())
karbonhidrat_gram = float(input("Kaç gram karbonhidrat almak istiyorsunuz? "))
protein_gram = float(input("Kaç gram protein almak istiyorsunuz? "))
yağ_gram = float(input("Kaç gram yağ almak istiyorsunuz? "))
elma_adet = int(input("Kaç adet elma yemek istiyorsunuz? "))
muz_adet = int(input("Kaç adet muz yemek istiyorsunuz? "))
pirinç_adet = int(input("Kaç fincan pişmiş pirinç yemek istiyorsunuz? "))
ekmek_adet = int(input("Kaç dilim beyaz ekmek yemek istiyorsunuz? "))
tavuk_adet = int(input("Kaç porsiyon pişmiş tavuk yemek istiyorsunuz? "))
peynir_adet = int(input("Kaç dilim peynir yemek istiyorsunuz? "))
yumurta_adet = int(input("Kaç adet pişmiş yumurta yemek istiyorsunuz? "))
#Gram cinsindekiler ondalıklı sayıyla yazılabileceğinden float veri tipini kullandım,adetler ise doğal sayı olduğundan integer veri tipini kullandım.

# Toplam kalori hesaplama
toplam_kalori = (
    (karbonhidrat_gram * besinler["karbonhidrat"]) +
    (protein_gram * besinler["protein"]) +
    (yağ_gram * besinler["yağ"]) +
    (elma_adet * agirliklar["elma"] * besinler["elma"]) +
    (muz_adet * agirliklar["muz"] * besinler["muz"]) +
    (pirinç_adet * agirliklar["pirinç"] * besinler["pirinç"]) +
    (ekmek_adet * agirliklar["ekmek"] * besinler["ekmek"]) +
    (tavuk_adet * agirliklar["tavuk"] * besinler["tavuk"]) +
    (peynir_adet * agirliklar["peynir"] * besinler["peynir"]) +
    (yumurta_adet * agirliklar["yumurta"] * besinler["yumurta"])
) #besinleri ve ağırlıkları yazarken dictionery kullandığım için değerleri köşeli parantezle yazdım.

# Sonuçların yazdırılması
if cinsiyet == "kadın":
    print(f"\nToplam kalori: {toplam_kalori:.2f} kalori")
    print(f"Karbonhidrat: {karbonhidrat_gram} gram, Protein: {protein_gram} gram, Yağ: {yağ_gram} gram")
    print(f"Elma: {elma_adet} adet, Muz: {muz_adet} adet, Pirinç: {pirinç_adet} fincan")
    print(f"Ekmek: {ekmek_adet} dilim, Tavuk: {tavuk_adet} porsiyon, Peynir: {peynir_adet} dilim, Yumurta: {yumurta_adet} adet\n")
    print(f"Günlük Kalori İhtiyacınıza Göre Besin Miktarları: {kadın_günlük_kalori_ihtiyacı} kalori")

    if toplam_kalori > kadın_günlük_kalori_ihtiyacı:
        print("\nUyarı: Günlük kalori ihtiyacınızı aştınız (Kadın)")

elif cinsiyet == "erkek":
    print(f"\nToplam kalori: {toplam_kalori:.2f} kalori")
    print(f"Karbonhidrat: {karbonhidrat_gram} gram, Protein: {protein_gram} gram, Yağ: {yağ_gram} gram")
    print(f"Elma: {elma_adet} adet, Muz: {muz_adet} adet, Pirinç: {pirinç_adet} fincan")
    print(f"Ekmek: {ekmek_adet} dilim, Tavuk: {tavuk_adet} porsiyon, Peynir: {peynir_adet} dilim, Yumurta: {yumurta_adet} adet\n")
    print(f"Günlük Kalori İhtiyacınıza Göre Besin Miktarları: {erkek_günlük_kalori_ihtiyacı} kalori")

    if toplam_kalori > erkek_günlük_kalori_ihtiyacı:
        print("\nUyarı: Günlük kalori ihtiyacınızı aştınız (Erkek)")

