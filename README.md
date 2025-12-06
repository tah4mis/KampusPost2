## KampusPost – React Native Projesi

Bu proje, React Native kullanılarak geliştirilmiş basit bir **KampusPost** uygulaması iskeletidir.  
Ödev kapsamında şu özellikler uygulanmıştır:

- **Giriş ekranı (`LoginScreen`)** – E‑posta, şifre alanları ve “Giriş Yap / Kayıt Ol” butonları
- **Kayıt ekranı (`RegisterScreen`)** – E‑posta, şifre, şifre tekrar alanları ve şifre doğrulama
- **Ana ekran (`HomeScreen`)** – Uzak API’den post verisi çekme ve listeleme
- **React Navigation** ile **Stack Navigator** yapısı
- **Yeniden kullanılabilir `CustomInput` bileşeni**

## Projeyi Çalıştırma

Terminalde proje klasörüne girin:

```sh
cd KampusPost
```

Metro (React Native dev server) başlatın:

```sh
npm start
```

Yeni bir terminal penceresinde Android emülatörü veya cihaz üzerinde uygulamayı çalıştırın:

```sh
npm run android
```

> iOS için ek kurulumlar (macOS, Xcode, CocoaPods) gerektiğinden bu projede ana odak Android tarafıdır.

## Ekranlar ve Navigasyon

- **NavigationContainer + Stack Navigator**  
  `App.tsx` içinde `NavigationContainer` ve `createNativeStackNavigator` ile şu ekranlar tanımlıdır:
  - `Login` → `LoginScreen`
  - `Register` → `RegisterScreen`
  - `Home` → `HomeScreen`  
  Açılış ekranı **LoginScreen**’dir (`initialRouteName="Login"`).

- **LoginScreen**  
  - Üst yazı: **“KampüsPost’a Hoş Geldiniz!”**  
  - Başlık: **“Giriş Yap”**  
  - Alanlar: E‑posta, Şifre (`CustomInput` bileşeni ile)  
  - Butonlar:
    - **“Giriş Yap”** → şimdilik doğrulama yapmadan **HomeScreen**’e yönlendirir.
    - **“Kayıt Ol”** → **RegisterScreen**’e yönlendirir.

- **RegisterScreen**  
  - Alanlar: E‑posta, Şifre, Şifre Tekrar (tamamı `CustomInput` kullanır).  
  - **“Kayıt Ol”** butonu:
    - Şifreler uyuşmazsa: `Alert.alert("Hata", "Şifreler uyuşmuyor!")`
    - Şifreler aynıysa:
      - `console.log("Kayıt başarılı", { email })`
      - `Alert.alert("Başarılı", "Kayıt başarılı! Giriş yapabilirsiniz.")`
      - Ardından **LoginScreen**’e geri yönlendirir.

- **HomeScreen**  
  - `useEffect` ile `https://jsonplaceholder.typicode.com/posts` adresinden veri çeker.  
  - Gelen veriyi `Post[]` tipinde state’e kaydeder ve konsola `Posts verisi:` olarak yazdırır.  
  - `FlatList` ile her post için:
    - Başlık (`title`) → kalın/büyük
    - İçerik (`body`) → altında normal metin şeklinde gösterilir.  
  - Veri yüklenirken:
    - Ortada spinner ve **“Yükleniyor…”** metni görünür.

## Proje Klasör Yapısı (Özet)

- **App.tsx** – `NavigationContainer` + `Stack.Navigator`
- **components/**
  - `LoginScreen.tsx` – Giriş ekranı (form + butonlar)
  - `RegisterScreen.tsx` – Kayıt ekranı (şifre kontrolü + yönlendirme)
  - `HomeScreen.tsx` – Post listesini gösteren ekran (API + FlatList)
  - `CustomInput.tsx` – Ortak giriş bileşeni

## Teslim İçin Önerilen Ekran Görüntüleri

- **Proje klasör yapısı**  
  `KampusPost` klasörünün içini (özellikle `App.tsx` ve `components/` klasörünü) gösteren ekran görüntüsü.

- **Navigasyon yapısı**  
  `App.tsx` içindeki `NavigationContainer` + `Stack.Navigator` kodunun ekran görüntüsü.

- **Giriş ekranı**  
  `KampüsPost’a Hoş Geldiniz!` üst yazısı, `Giriş Yap` başlığı, e‑posta / şifre alanları ve  
  **“Giriş Yap” / “Kayıt Ol”** butonlarının göründüğü ekran.

- **Kayıt ekranı**  
  E‑posta, Şifre, Şifre Tekrar alanları ve **“Kayıt Ol”** butonunun göründüğü ekran.  
  Şifreler uyuşmadığında çıkan **Alert** penceresinin ekran görüntüsü.  
  Şifreler uyduğunda konsolda görünen **“Kayıt başarılı”** logunun ekran görüntüsü.

- **HomeScreen ve veri çekme**  
  - `Posts verisi:` log’unun göründüğü **DevTools Console** veya terminal ekranı.  
  - `FlatList` ile post’ların listelendiği HomeScreen ekran görüntüsü.  
  - Varsa **“Yükleniyor…”** metninin göründüğü anın ekran görüntüsü.


