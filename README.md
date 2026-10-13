**Türkçe** | [English](README.en.md)

# STM32 Tabanlı Gimbal Kontrol Kartı

İHA kamera stabilizasyonu için STM32F103RCT6, MPU6050 ve üç eksene ait sürücü katlarını tek PCB üzerinde birleştiren donanım projesi.

**Durum:** Kart üretildi ve gimbal sistemine entegre edilerek çalıştırıldı. Bu depo kart tasarımını, üretim dosyalarını ve görsellerini içerir; kontrol yazılımı ve sayısal stabilizasyon test sonuçları yayımlanmamıştır.

## Sistem Mimarisi

MPU6050 ölçümleri I²C üzerinden STM32'ye aktarılacak şekilde tasarlanmıştır. Mikrodenetleyici, üç eksene ait sürücü katlarını kontrol eder. Kartta programlama, haberleşme ve yardımcı giriş/çıkış bağlantıları bulunur.

| Bileşen | Görev |
|---|---|
| STM32F103RCT6 | Ana mikrodenetleyici |
| MPU6050 | İvme ve açısal hız ölçümü |
| TC4420CPA, 9 adet | Üç eksene ait sürücü katları; eksen başına üç kanal |
| LM1117-3.3 | 3,3 V regülasyonu |
| Mini USB | Kart üzerindeki USB bağlantısı |

## Bağlantı Arayüzleri

| Konnektör | Açıklama |
|---|---|
| J8 / J9 / J10 | Motor çıkışları; M0, M1, M2 |
| J3 | SWD programlama ve hata ayıklama |
| J4 | RC girişi |
| J1 | Dört kanallı RC bağlantısı |
| J7 | I²C |
| J2 | UART |
| J5 | Yardımcı çıkışlar |
| J6 | Buton girişi |

Kartın besleme gerilimi ve motor yük sınırları için bu depoda doğrulanmış sayısal çalışma aralığı verilmemektedir. Kart üzerindeki VBAT adı tek başına bir çalışma gerilimi aralığı tanımlamaz.

## Tasarım ve Kişisel Katkım

Sistem gereksinimleri, temel bileşen seçimi, şematik hazırlama ve PCB tasarımını gerçekleştirdim. STM32'nin besleme, saat, reset ve programlama devrelerini; MPU6050 bağlantılarını, sürücü katlarını ve haberleşme arayüzlerini tasarıma ekledim. Tasarım kontrollerinin ardından üretim dosyalarını hazırladım ve kartın üretim sürecini takip ettim.

Yerleşimde IMU'nun yüksek akımlı sürücü hatlarından ayrılmasına, besleme bypass elemanlarının ilgili bileşenlere yakın tutulmasına ve programlama bağlantılarına erişime dikkat ettim.

## Doğrulama Kapsamı

Kartın üretim ve sistem entegrasyonu gerçekleştirildi. Kapalı çevrim stabilizasyon başarımı, motor yükü altında sıcaklık sınırları ve eksen doğruluğuna ilişkin sayısal test kayıtları bu depoda yayımlanmamıştır.

Yayımlanabilecek ek doğrulama kayıtları:

- Test edilen besleme ve motor yükü
- IMU okuma ve programlama testleri
- Kontrol yazılımı ve kullanılan yöntem
- Stabilizasyon hatası, tepki süresi ve sürücü sıcaklıkları

## Depo İçeriği

| Dosya | İçerik |
|---|---|
| [10.08.2025.PrjPcb](10.08.2025.PrjPcb) | Altium proje dosyası |
| [Sheet2.SchDoc](Sheet2.SchDoc) | Şematik kaynak |
| [PCB2.PcbDoc](PCB2.PcbDoc) | PCB kaynak |
| [10.08.pdf](10.08.pdf) | PDF tasarım çıktısı |
| [Malzeme listesi](10.08.2025_malzeme%20listesi.pdf) | BOM belgesi |
| [Üretim çıktıları](Project%20Outputs%20for%2010.08.2025.rar) | Mevcut üretim arşivi |
| CAMtastic dosyaları | Mevcut CAM çıktıları |

## Görseller

### Şematik
![Şematik](sematik.jpeg)

### PCB Tasarımı
<table>
<tr><td><img src="pcb_görsel_2d.jpg" width="400" alt="PCB 2D görünümü"></td><td><img src="pcb_görsel_3d.jpg" width="400" alt="PCB 3D görünümü"></td></tr>
</table>

### Üretilen Kart
<table>
<tr><td><img src="pcb_görsel.jpg" width="400" alt="Kartın ön görünümü"></td><td><img src="pcb_görsel2.jpg" width="400" alt="Kartın arka görünümü"></td></tr>
</table>

[Mert Uzun - Proje Portfolyosu](https://github.com/mertuzun41/Projeler) | [LinkedIn](https://www.linkedin.com/in/mert-uzun-b74459308)

