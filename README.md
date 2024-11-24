Debian'da repository (depo) ekleme konusunda size yardımcı olacağım. İşte farklı yöntemlerle repository ekleme adımları:
Debian'da repository (depo) ekleme konusunda size yardımcı olacağım. İşte farklı yöntemlerle repository ekleme adımları:

1. Sources.list Dosyası Üzerinden Ekleme:
```bash
# Sources.list dosyasını açın
sudo nano /etc/apt/sources.list

# Veya yeni bir dosya oluşturun
sudo nano /etc/apt/sources.list.d/yeni_repo.list
```

2. Temel Repository Formatı:
```bash
deb http://depo-adresi/debian version main contrib non-free
deb-src http://depo-adresi/debian version main contrib non-free
```

3. Debian'ın Resmi Repository'leri (Örnek):
```bash
# Debian 12 (Bookworm) için
deb http://deb.debian.org/debian bookworm main contrib non-free non-free-firmware
deb http://deb.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware

# Debian 11 (Bullseye) için
deb http://deb.debian.org/debian bullseye main contrib non-free
deb http://security.debian.org/debian-security bullseye-security main contrib non-free
deb http://deb.debian.org/debian bullseye-updates main contrib non-free
```

4. GPG Anahtarı Ekleme:
```bash
# Anahtar indirme
wget -qO - https://paket-adresi/KEY.gpg | sudo apt-key add -

# Veya
curl -fsSL https://paket-adresi/KEY.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/paket.gpg
```

5. Repository Güncelleme:
```bash
# Paket listelerini güncelle
sudo apt update

# Tüm paketleri güncelle
sudo apt upgrade
```

6. Backports Repository Ekleme:
```bash
# Bookworm için
deb http://deb.debian.org/debian bookworm-backports main contrib non-free

# Bullseye için
deb http://deb.debian.org/debian bullseye-backports main contrib non-free
```

7. Third-Party Repository Örnekleri:

PHP Repository:
```bash
# Ondrej PHP PPA
wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/php.list
```

Node.js Repository:
```bash
# NodeSource repository
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo bash -
```

8. Repository Silme:
```bash
# sources.list.d dizininden silme
sudo rm /etc/apt/sources.list.d/repo_adi.list

# veya sources.list içinden ilgili satırları silme/yorum satırı yapma
sudo nano /etc/apt/sources.list
```

9. Repository Yönetimi İçin Yararlı Komutlar:
```bash
# Mevcut repository'leri listele
apt policy

# Repository anahtarlarını listele
sudo apt-key list

# Bozuk repository'leri kontrol et
sudo apt update 2>&1 | grep Err

# Repository önbelleğini temizle
sudo apt clean
```

10. HTTPS Desteği İçin:
```bash
sudo apt install apt-transport-https ca-certificates
```

Önemli Notlar:
- Repository eklerken güvenilir kaynaklardan eklediğinizden emin olun
- Her repository ekledikten sonra `sudo apt update` komutunu çalıştırın
- Eski/kullanılmayan repository'leri sistemden kaldırın
- Third-party repository'leri dikkatli kullanın
- Her zaman GPG anahtarlarını doğrulayın

Bu adımları takip ederek Debian sisteminize güvenli bir şekilde yeni repository'ler ekleyebilirsiniz.

Debian terminalinde kopyalama ve yapıştırma işlemleri için size farklı yöntemleri açıklayacağım:

1. Terminal İçinde Kopyalama-Yapıştırma:
```bash
# Kopyalama
CTRL + SHIFT + C

# Yapıştırma
CTRL + SHIFT + V
```

2. Sağ Tık Menüsü:
```bash
# Fare sağ tıklama ile:
Kopyala (Copy)
Yapıştır (Paste)
```

3. Orta Fare Tuşu ile:
```bash
# Metni seçtikten sonra:
Orta tuş (tekerlek) ile tıklayarak yapıştırma
```

4. Terminal Kısayolları:
```bash
# Metin seçimi:
SHIFT + Sol/Sağ ok tuşları

# Tüm metni seçme:
CTRL + SHIFT + A

# Kesme:
CTRL + SHIFT + X
```

5. Screen Kullanıcıları İçin:
```bash
# Copy mode'a geçiş:
CTRL + A + [

# Seçimi başlatma:
SPACE

# Seçimi kopyalama:
CTRL + A + ]
```

6. Tmux Kullanıcıları İçin:
```bash
# Copy mode'a geçiş:
CTRL + B + [

# Seçimi başlatma:
SPACE

# Seçimi kopyalama:
ENTER

# Yapıştırma:
CTRL + B + ]
```

7. Terminal Buffer Kopyalama:
```bash
# Son çıktıyı kopyalama
!$

# Son komutun tamamını kopyalama
!!
```

8. xclip Kullanımı:
```bash
# xclip kurulumu
sudo apt install xclip

# Dosya içeriğini panoya kopyalama
cat dosya.txt | xclip -selection clipboard

# Komut çıktısını panoya kopyalama
pwd | xclip -selection clipboard
```

9. Terminal Yapılandırması:
```bash
# .bashrc veya .zshrc dosyasına eklenebilecek alias'lar:
alias c='xclip -selection clipboard'
alias v='xclip -selection clipboard -o'
```

10. Vim Kullanıcıları İçin:
```bash
# Vim içinde kopyalama-yapıştırma:
# Visual mode'a geçiş
v

# Tüm satırı seçme
V

# Kopyalama
y

# Yapıştırma
p
```

11. SSH Üzerinden Kopyalama:
```bash
# SSH oturumunda kopyalama-yapıştırma aktif etme
ssh -X kullanici@sunucu
```

Önemli İpuçları:

- Terminal emülatörünüzün ayarlarından kopyalama-yapıştırma davranışını özelleştirebilirsiniz
- Bazı terminal emülatörleri otomatik kopyalama özelliğine sahiptir
- UTF-8 karakter kodlaması sorunlarına dikkat edin
- Güvenlik nedeniyle bazı terminaller yapıştırma işlemini onay gerektirebilir

Güvenlik Notları:
- Hassas bilgileri kopyalarken dikkatli olun
- Pano içeriğini düzenli olarak temizleyin
- Güvenilmeyen kaynaklardan yapıştırma yaparken dikkatli olun

Terminal türüne göre ek özelleştirmeler:

GNOME Terminal:
```bash
# Ayarlar menüsünden:
Düzenle > Tercihler > Kısayollar
```

Konsole:
```bash
# Ayarlar menüsünden:
Ayarlar > Kısayolları Yapılandır
```

Bu yöntemlerden size en uygun olanı kullanabilirsiniz. 

``````
The system will suspend now!
``````
Bu mesaj sistemin askıya alınacağını (suspend/uyku moduna geçeceğini) belirten bir uyarıdır. İşte bu durumla ilgili bilmeniz gerekenler ve yapabilecekleriniz:

1. Sistemin Askıya Alınmasını Engellemek İçin:
```bash
# Askıya almayı iptal etmek için
sudo systemctl cancel-shutdown

# veya
sudo shutdown -c
```

2. Açık Dosyaları Kaydetme:
- Tüm açık belgelerinizi kaydedin
- Çalışan programları düzgünce kapatın
- Devam eden indirmeleri durdurun

3. Sistem Durumunu Kontrol:
```bash
# Sistemi kullanan kullanıcıları görmek için
who

# Çalışan işlemleri görmek için
ps aux

# Sistem kaynaklarını kontrol etmek için
top
```

4. Askıya Alma İşlemini Yönetme:
```bash
# Manuel askıya alma
sudo pm-suspend

# Veya
sudo systemctl suspend
```

5. Zamanlı Askıya Alma:
```bash
# 30 dakika sonra askıya alma
sudo shutdown -h +30

# Belirli bir saatte askıya alma
sudo shutdown -h 23:00
```

Önemli Notlar:
- Açık dosyalarınızı kaydettiğinizden emin olun
- Önemli işlemlerin tamamlandığından emin olun
- Sistem yeniden başlatıldığında işlerinize kaldığınız yerden devam edebilirsiniz
