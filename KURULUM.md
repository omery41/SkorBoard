# SkorBoard — Kurulum (v2)

Sayfa GitHub Pages'te (`https://omery41.github.io/SkorBoard/`), veriler Firebase'de (`skorboard-2b486`) tutulur.

## Firebase ayarları
1. **Authentication → Sign-in method**: E-posta/Şifre açık olmalı.
2. **Authentication → Settings → User actions**: "Enable create (sign-up)" **açık** kalmalı; kullanıcılar kendileri kayıt oluyor.
3. **Authentication → Settings → Authorized domains**: `omery41.github.io` ekli olmalı.
4. **Firestore → Rules**: `firestore.rules` dosyasının tamamını yapıştırıp **Publish**.

## İlk kurulum
1. `https://omery41.github.io/SkorBoard/#kurulum` adresini aç, Admin şifresini belirleyip **Admin hesabını oluştur**'a bas. Bunu herkesten önce yap: Admin hesabı ilk açan kişiye ait olur.
2. Sonra `admin` nick'i ve o şifreyle giriş yapabilirsin.

## Nasıl çalışır
- Herkes **Kayıt ol** sekmesinden nick ve şifreyle hesap açar. Nick büyük/küçük harf duyarsızdır; Türkçe harfler girişte sadeleşir (Ömer = omer).
- Arka planda her nick `nick@skorboard.test` e-postası olarak saklanır; şifrenin başına `sb-` eklenir (Firebase en az 6 karakter istediği için).
- **Yeni skorboard**: kuran kişi pembe taraf olur, rakibini nick'iyle seçer (rakip önce kayıt olmalı).
- Oyuncular sadece kendi skorboardlarını görür, sadece kendi tarafına çentik atar ve sadece kendi çentiğini geri alır. Geri alma defterde görünür.
- **Admin** tüm skorboardları görür; her iki tarafa çentik ekler, kayıt siler, skorboard siler. Admin işlemleri defterde iz bırakmaz.
- Bir skorboard **bitir** ile "Bitenler"e taşınır, **Yeniden aç** ile devam eder.
