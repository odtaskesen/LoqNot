# LoqNot

**Sosyal medya ajansları için marka bazlı içerik-ilham panosu.**

🔗 **Canlı site:** [loqnot.vercel.app](https://loqnot.vercel.app)

![Vanilla JS](https://img.shields.io/badge/Vanilla_JS-F7DF1E?logo=javascript&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?logo=tailwindcss&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase_Firestore-FFCA28?logo=firebase&logoColor=black)
![PWA](https://img.shields.io/badge/PWA-Ana_ekrana_eklenebilir-5A0FC8?logo=pwa&logoColor=white)
![Build](https://img.shields.io/badge/Build-Gerekmiyor-success)

Sosyal medya ekipleri gün içinde onlarca iyi içerik görür: *"Bu Reel formatı bizim müşteriye birebir uyar."* Sorun, o anlık fikrin akışta kaybolmasıdır. LoqNot bunun için var — gördüğün içeriğin linkini yapıştır, hangi markaya uyduğunu yaz, gerisini uygulama halleder.

[Sosyaloq](https://sosyaloq.com) ajansının günlük iş akışı için tasarlandı ve ekip tarafından aktif olarak kullanılıyor.

<!-- Ekran görüntüsü eklemek için: uygulamanın görüntüsünü docs/screenshot.png olarak kaydedin ve alttaki satırın başındaki yorum işaretlerini kaldırın -->
<!-- ![LoqNot ekran görüntüsü](docs/screenshot.png) -->

## ✨ Özellikler

- **Otomatik marka algılama** — Nota "özgür koldaş şuna benzer bir video çekebilir" yazarsınız, not kendiliğinden Özgür Koldaş kategorisine etiketlenir. Kısaltmalar da tanınır (`ök`, `ok` gibi), birden fazla marka geçerse hepsine etiketlenir.
- **Akıllı link rozetleri** — Yapıştırılan linkler ham URL olarak değil, platform renginde şık rozetler olarak görünür: `● Instagram Reel ↗`, `● TikTok`, `● YouTube Shorts`...
- **Acil bayrağı** — Öncelikli işler tek dokunuşla işaretlenir, her listede otomatik en üste çıkar.
- **Arşiv akışı** — Çekilen/tamamlanan fikirler tik ile arşive taşınır, marka listelerini kalabalıklaştırmaz.
- **Akıllı kenar çubuğu** — Markalar not sayısına göre sıralanır, boş markalar tek satıra katlanır.
- **Kapsamlı arama** — Hem not metninde hem marka adı ve kısaltmalarında arar.
- **Kart / kompakt liste görünümü** — Tercihe göre iki yerleşim, seçim hatırlanır.
- **Açık / koyu tema** — Sistem tercihini algılar, elle değiştirilebilir.
- **Gerçek zamanlı senkronizasyon** — Bir cihazda eklenen not, açık olan tüm cihazlarda anında görünür.
- **PWA** — Telefonda ana ekrana eklenir, uygulama gibi açılır.

## 🧠 Nasıl çalışır?

```
"şu reel formatını ök için uyarlayalım https://instagram.com/reels/..."
        │                │                        │
        │                │                        └─ platform algılanır → "● Instagram Reel ↗" rozeti
        │                └─ "ök" kısaltması eşleşir → not Özgür Koldaş'a etiketlenir
        └─ not gerçek zamanlı olarak tüm ekibin panosuna düşer
```

Marka eşleştirme Türkçe'ye duyarlıdır (`toLocaleLowerCase('tr-TR')`), boşluklu marka adlarını ve virgülle tanımlanan kısaltmaları destekler.

## 🛠 Teknoloji

| Katman | Tercih | Neden |
|---|---|---|
| Arayüz | Vanilla JS + Tailwind CSS | Bağımlılık yok, build adımı yok — tek `index.html` |
| Veri | Firebase Firestore | Gerçek zamanlı senkron, ücretsiz katman üç kişilik ekibe fazlasıyla yeter |
| Dağıtım | Vercel (statik hosting) | Sunucu maliyeti sıfır, push ile otomatik yayın |
| Mobil | PWA (manifest + service worker) | App Store'suz "uygulama" deneyimi |

Bilinçli bir tercih olarak framework kullanılmadı: proje tek HTML dosyasından oluşur, herhangi bir tarayıcıda doğrudan açılır ve bakımı kod bilmeyen birine bile devredilebilecek kadar basittir.

## 🚀 Çalıştırma

Derleme yok. Klonlayın ve açın:

```bash
git clone https://github.com/odtaskesen/LoqNot.git
cd LoqNot
python3 -m http.server 8000
# http://localhost:8000
```

> Kendi kopyanız için [Firebase konsolundan](https://console.firebase.google.com) ücretsiz bir proje oluşturup `index.html` içindeki `firebaseConfig` bölümünü kendi değerlerinizle değiştirmeniz yeterli.

## 📁 Dosya yapısı

```text
LoqNot/
├── index.html            # Uygulamanın tamamı (arayüz + mantık)
├── manifest.webmanifest  # PWA tanımı
├── sw.js                 # Service worker (çevrimdışı kabuk önbelleği)
└── icons/                # Uygulama ikonları
```

---

*Sosyaloq ajansında sosyal medya uzmanı olarak çalışırken ekibin gerçek bir ihtiyacından doğdu: gördüğümüz iyi içerikleri müşterilerimize uyarlama fikirlerini tek yerde toplamak.*
