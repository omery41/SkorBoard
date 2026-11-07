# Tavla Çentik Tablosu — Kurulum

Sayfa GitHub Pages'te durur. Skorlar ve girişler Firebase'de (ücretsiz plan) tutulur.

## 1. Firebase projesi
1. https://console.firebase.google.com adresine Google hesabınla gir, **Proje ekle**'ye bas. İsim örneği: `tavla-skor`. Google Analytics'i kapatabilirsin.
2. **Build → Authentication → Başlayın → Sign-in method** sekmesinde **E-posta/Şifre**'yi etkinleştir.
3. **Users → Kullanıcı ekle** ile aşağıdaki 3 hesabı aç. Şifre sütunundakini aynen yaz: ekranda girilen 1234'ün başına sistem otomatik olarak `tavla-` ekliyor, çünkü Firebase en az 6 karakter istiyor.

   | Rol    | E-posta             | Şifre        |
   |--------|---------------------|--------------|
   | Admin  | admin@tavla.test    | `tavla-1234` |
   | Pervin | pervin@tavla.test   | `tavla-1234` |
   | Emin   | emin@tavla.test     | `tavla-1234` |

4. **Build → Firestore Database → Veritabanı oluştur** adımında konum olarak `eur3 (europe-west)`, mod olarak **Üretim modu**nu seç.
5. Firestore'un **Kurallar (Rules)** sekmesine `firestore.rules` dosyasının tamamını yapıştırıp **Yayınla**'ya bas.
6. **Proje ayarları (dişli) → Genel → Uygulamalarınız** bölümünde web simgesine (`</>`) bas ve bir isim ver. Çıkan `firebaseConfig` değerlerini `firebase-config.js` dosyasına kopyala.

## 2. GitHub Pages
1. GitHub'da yeni bir repo aç, örneğin `tavla-skor`.
2. `index.html` ve `firebase-config.js` dosyalarını yükle. `firestore.rules` ile bu dosyayı da yedek olarak yükleyebilirsin.
3. **Settings → Pages → Branch: main / (root) → Save** yap. Bir iki dakika sonra sayfa şu adreste açılır:
   `https://KULLANICI-ADIN.github.io/tavla-skor/`
4. Firebase'de **Authentication → Settings → Yetkili alan adları** bölümüne `KULLANICI-ADIN.github.io` ekle.

## 3. İlk giriş
- Admin olarak gir ve hemen **Şifre değiştir**'den kendi şifreni koy. 1234 Pervin ve Emin tarafından da bilindiği için bu adım önemli.
- Pervin ve Emin de ilk girişte kendi şifrelerini değiştirebilir.
- İzleyiciler linki açıp **İzleyici olarak gir**'e basar, şifre sorulmaz.

## Kurallar özeti
- Pervin sadece Pervin'e, Emin sadece Emin'e çentik atar ve sadece kendi çentiklerini geri alır. Admin hepsini yapabilir.
- Hiçbir kayıt silinmez. Geri alma ayrı bir satır olarak deftere yazılır, geri alınan çentik üstü çizili görünür.
- Bir çentik yalnızca bir kez geri alınabilir.
- Oyuncu isimlerini sadece Admin değiştirebilir.
- Skoru sıfırlamak için Firestore konsolunda `events` koleksiyonunu silmen yeterli.
