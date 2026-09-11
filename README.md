# Portfolyo

Ahmed Talha Güler'in kişisel portfolyo sitesi.

**Yayında: https://ahmetqler.github.io**

Tek HTML dosyası, build adımı yok, bağımlılık yok. Tarayıcıda `index.html`'e
çift tıklayınca da çalışır.

```
index.html        tüm site — HTML, CSS, JS aynı dosyada
gorseller/        proje ekran görüntüleri
```

## Siteyi güncelleme

Yayın GitHub Pages üzerinden, `main` dalının kökünden yapılıyor. Yani **push
ettiğin an site güncellenir** — ayrıca bir derleme ya da panel işi yok.

```bash
git add .
git commit -m "ne degistiyse onu yaz"
git push
```

Değişiklik bir iki dakika içinde yayına yansır. Hemen görünmezse tarayıcının
önbelleğini atlamak için sayfayı Ctrl+F5 ile yenile.

Yerelde denemek için `index.html`'e çift tıklaman yeterli; sunucu gerekmiyor.

## Dil

Sayfa iki dilli. **İlk girişte İngilizce** açılır; sağ üstteki EN/TR düğmesi tüm
sayfayı çevirir ve seçim tarayıcıda hatırlanır. Varsayılanı değiştirmek için
script başındaki `VARSAYILAN_DIL` değerini `"tr"` yap.

Çeviriler iki yerde:

- **`METIN`** — sayfa çerçevesi: üst etiket, giriş paragrafı, künye hücreleri,
  bölüm başlıkları, düğme yazıları. `tr` ve `en` altında birebir aynı alanlar var.
- **Her projenin `tr` ve `en` bloğu** — özet, anlatı, özellikler, sayılar vb.

Dilden bağımsız alanlar (ikon, teknoloji etiketleri, görsel dosya adları, linkler)
proje nesnesinin dışında, bir kez yazılır.

Yeni bir metin eklerken **iki dile de eklemeyi unutma** — eksik kalan alan o dilde
boş görünür.

## İçeriği güncelleme

Her şey `index.html` içindeki `<script>` bloğunun en üstünde:

- **`KISI`** — e-posta, GitHub ve LinkedIn adresin. LinkedIn boş bırakılırsa
  o düğme sayfada hiç görünmez; doldurunca kendiliğinden çıkar.
- **`PROJELER`** — her proje bir nesne. Alanlar:

  **Dilden bağımsız alanlar** (proje nesnesinin doğrudan içinde):

  | Alan | Ne işe yarıyor |
  |---|---|
  | `ad` | Proje adı — iki dilde de aynı |
  | `glif` | Kart ve künyedeki ikon (`GLIF` nesnesinden seçilir) |
  | `rozetTipi` | Rozet rengi: `"yayinda"` yeşil, `"gelisiyor"` pembe, `"yakinda"` çerçeveli |
  | `gizli` | `true` ise kart tıklanamaz, künye açılmaz. Sadece ad, rozet ve tek satır görünür — detay vermek istemediğin projeler için (şu an GANO böyle) |
  | `teknoloji` | Künyedeki teknoloji etiketleri |
  | `gorseller` | `{ src, tr, en }` listesi — dosya yolu ortak, alt yazı iki dilde. Boş bırakılırsa bölüm çıkmaz |
  | `canli` | Canlı adres. Boş bırakılırsa düğme çıkmaz |
  | `depo` | Kaynak kodu adresi. Boş bırakılırsa düğme çıkmaz |

  **Dile bağlı alanlar** (`tr` ve `en` bloklarının içinde, ikisinde de aynı alanlar):

  | Alan | Ne işe yarıyor |
  |---|---|
  | `durum` | Rozetin yazısı (ör. "Yayında" / "Live") |
  | `ozet` | Listede görünen tek cümle |
  | `olcu` | Listede en altta duran küçük sayı satırı |
  | `anlati` | Künyenin açılış paragrafı — projeyi neden yaptın |
  | `sayilar` | Künyedeki sayı şeridi (`{ ad, deger }` listesi) |
  | `ozellikler` | "Neler yapıyor" maddeleri. `<b>...</b>` ile başlık verilebilir |
  | `guvence` | Testler / doğruluk paragrafı. Boş bırakılırsa bölüm çıkmaz |
  | `not` | Uyarı/çekince notu. Boş bırakılırsa çıkmaz |

Yeni proje eklemek için `PROJELER` dizisine aynı şablonda bir nesne eklemek yeterli;
sayaç ve kartlar kendiliğinden güncellenir.

Yeni ekran görüntüsü eklerken dosyayı `gorseller/` içine koy ve `src` alanına
`gorseller/dosya-adi.png` diye yaz.

## Depo bağlantıları hakkında

Projelerin şu an GitHub'da **private**. `depo` alanları bu yüzden boş bırakıldı:
private bir depoya giden bağlantı, siteye bakan kişide 404 verir. Bir projeyi
public yaparsan adresini `depo` alanına yazman yeterli, düğme kendiliğinden gelir.

## Sitedeki projeler

| Proje | Kaynak | Durum |
|---|---|---|
| GANO | `ahmetqler/not-takip` | Gizli — sadece "çok yakında App Store'da" |
| Skyphrase | `ahmetqler/skyphrase` | Geliştirmede |
| Tekstil ERP | yalnızca yerelde (`Documents/tekstil-erp`) | Geliştirmede |
| Kulüp Takip | `ahmetqler/Kulup-takip` | Yayında — 4 ekran görüntüsü var |
| Tempo | `ahmetqler/tempo` | Yayında — canlı link |
| Jack'in Pusulası | `ahmetqler/jackin-pusulasi` | Yayında — canlı link |
| Dış Beynim | `ahmetqler/dis-beynim` | Yayında — canlı link |
| Kulüp Evi | `ahmetqler/kulup-evi` | Geliştirmede |
| Ders Notlarım | `ahmetqler/ders-asistani` | Yayında |

Canlı linkler senin Vercel dağıtımlarına gidiyor. Bir tanesini herkese açık
göstermek istemiyorsan o projenin `canli` alanını boşalt, düğme kaybolur.

## Arka plandaki uçaklar

Sayfanın arkasında iz bırakarak uçan uçaklar var (`index.html` sonundaki
"ARKA PLANDA UÇAN UÇAKLAR" bloğu). Skyphrase'in Flutter'daki
`FlightTrailsBackground` widget'ından uyarlandı; uçak görselleri de oradan
geldi (`ucaklar/`).

Görsellerin yalnızca alfa kanalı kullanılıyor, gövde tema rengiyle boyanıyor —
Flutter'da `BlendMode.srcIn`, burada canvas'ın `source-in` birleştirmesi. Tema
değişince kendiliğinden yeniden boyanıyor.

Ayarlar modülün başında:

| Ne | Nerede | Şu an |
|---|---|---|
| Uçak sayısı | `basla()` içinde `adet` | dar ekranda 3, geniş ekranda 6 |
| Görünürlük | `boya()` içindeki alfa değerleri | uçak 0.30, iz 0.13, vurgulu iz 0.20 |
| Hız | `yeniUcus()` içinde `sure` | geçiş başına 14-27 saniye |
| Boy | `yeniUcus()` içinde `boy` | 18-34 piksel |
| Yay oranı | `yeniUcus()` içinde `sapma` | uçuşların ~%35'i belirgin yay çizer |

Kalp ve gösteri formasyonları alınmadı; sadece düz ve yay rotalar var.

İşletim sisteminde "hareketi azalt" açıksa animasyon hiç başlamıyor, canvas
oluşturulmuyor. Görseller yüklenemezse de sessizce devre dışı kalıyor.
