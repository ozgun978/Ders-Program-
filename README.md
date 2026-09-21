# BPR 26 Girişliler Ders Programı

![Önizleme](og-image.png)

<p>
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
  <img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" />
  <img alt="JavaScript" src="https://img.shields.io/badge/JAVASCRIPT-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />
  <img alt="Font Awesome" src="https://img.shields.io/badge/FONT%20AWESOME-528DD7?style=for-the-badge&logo=fontawesome&logoColor=white" />
  <img alt="Google Fonts" src="https://img.shields.io/badge/GOOGLE%20FONTS-4285F4?style=for-the-badge&logo=googlefonts&logoColor=white" />
</p>

BPR 26 girişli öğrencilerin haftalık ders programını tek sayfada gösteren statik bir site. Adını yaz ya da listeden seç, programın açılsın.

Derleme adımı, paket yöneticisi ya da sunucu gerekmiyor. Tek bir `index.html` dosyası.

## Özellikler

- İsimle arama (büyük/küçük harf fark etmez) ve tek tıkla öğrenci seçimi
- Pazartesi–Cuma, 08.30–20.15 arası saat dilimleriyle haftalık tablo
- Peş peşe gelen aynı dersler tek blokta birleşir, bloğun altında toplam süre yazar
- Öğle arası ve boş saatler ayrı gösterilir
- Duyuru slider'ı (otomatik geçiş, ok ve nokta kontrolleri, kaydırma hareketi)
- İletişim bölümü ve resmî ders programına bağlantı
- Mobil uyumlu: dar ekranda tablo yatay kayar, saat sütunu sabit kalır
- Fare olan cihazlarda özel imleç, dokunmatik cihazlarda dokunma efekti
- `prefers-reduced-motion` desteği
- Open Graph ve Twitter Card etiketleri, favicon ve Apple Touch ikonu

## Dosyalar

| Dosya | Görevi |
| --- | --- |
| `index.html` | Sayfanın tamamı: yapı, stil, script ve öğrenci verisi |
| `og-image.png` | Paylaşım önizleme görseli (1200×630) |
| `favicon.svg`, `favicon-32.png` | Tarayıcı sekmesi ikonu |
| `apple-touch-icon.png` | iOS ana ekran ikonu |

## Yerelde çalıştırma

`index.html` dosyasını tarayıcıda açmak yeterli. Yazı tipleri ve ikonlar CDN'den geldiği için internet bağlantısı gerekir.

Yerel sunucu isteyenler için:

```bash
python3 -m http.server 8000
```

Ardından `http://localhost:8000` adresini aç.

## Öğrenci ve ders ekleme

Veri, `index.html` içindeki `students` nesnesinde durur. Her öğrencinin altında gün gün bir dizi var ve dizinin her elemanı bir saat dilimine denk geliyor:

| Sıra | Saat | Sıra | Saat |
| --- | --- | --- | --- |
| 0 | 08.30 - 09.15 | 6 | 15.30 - 16.15 |
| 1 | 09.30 - 10.15 | 7 | 16.30 - 17.15 |
| 2 | 10.30 - 11.15 | 8 | 17.30 - 18.15 |
| 3 | 11.30 - 12.15 | 9 | 18.30 - 19.15 |
| 4 | 12.30 - 13.15 | 10 | 19.30 - 20.15 |
| 5 | 14.30 - 15.15 | | |

Yeni bir öğrenci için mevcut bir kaydı kopyalayıp adını değiştirmen yeterli:

```js
Ada: {
  dersler: {
    Pazartesi: [
      "-",
      "Algoritma ve Programlamaya Giriş C blok/C303",
      "Algoritma ve Programlamaya Giriş C blok/C303",
      "Algoritma ve Programlamaya Giriş C blok/C303",
      "Öğle Arası",
      // ...
    ],
    Salı: [ /* ... */ ],
    Çarşamba: [ /* ... */ ],
    Perşembe: [ /* ... */ ],
    Cuma: [ /* ... */ ],
  },
},
```

Bilmen gerekenler:

- `"-"` boş saat, `"Öğle Arası"` öğle arası demek.
- Dizi kısa kalırsa eksik saatler otomatik boş sayılır.
- Aynı ders adı art arda yazılırsa tablo bunları tek blok yapar. Ders adı, blok ve sınıf bilgisiyle birebir aynı olmalı (harf büyüklüğü önemsiz).
- Öğrenci butonları `students` içindeki sıraya göre listelenir.

Duyurular `announcement-slide` etiketlerinde, iletişim bilgileri `contact-card` bağlantılarında bulunuyor. Doğrudan HTML'den düzenlenir.

## Yayınlama

Site tamamen statik olduğu için GitHub Pages, Netlify ya da Vercel gibi herhangi bir statik barındırmada çalışır.

Yayına aldıktan sonra `index.html` içindeki şu iki etiketi mutlak adresle güncelle. Sosyal medya önizlemeleri göreli yolu çözemez:

```html
<meta property="og:image" content="https://alanadi.com/og-image.png" />
<meta name="twitter:image" content="https://alanadi.com/og-image.png" />
```

## İletişim

Özgün Aksade

- GitHub: [ozgun978](https://github.com/ozgun978)
- LinkedIn: [Özgün Aksade](https://www.linkedin.com/in/özgün-aksade-636a79396/)
- E-posta: aksade1912ozgun@gmail.com

© Tüm hakları Özgün AKSADE'ye aittir.
