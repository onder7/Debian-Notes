Debian install Notes..

1. Debian Repository Ekleme / Adding Debian Repository
   - Sources.list Dosyası Ekleme / Adding Sources.list File
   - Temel Repository Formatı / Basic Repository Format
   - Resmi Repository'ler / Official Repositories
   - GPG Anahtarı Ekleme / Adding GPG Key
   - Repository Güncelleme / Repository Update
   - Backports Repository / Backports Repository
   - Third-Party Repository / Third-Party Repository
   - Repository Silme / Remove Repository
   - Repository Yönetimi / Repository Management
   - HTTPS Desteği / HTTPS Support

2. Terminal Kopyalama-Yapıştırma / Terminal Copy-Paste
   - Terminal İçi Kopyalama / In-Terminal Copy
   - Sağ Tık Menüsü / Right Click Menu
   - Orta Fare Tuşu / Middle Mouse Button
   - Terminal Kısayolları / Terminal Shortcuts
   - Screen Kullanımı / Screen Usage
   - Tmux Kullanımı / Tmux Usage
   - Buffer Kopyalama / Buffer Copy
   - xclip Kullanımı / xclip Usage
   - Terminal Yapılandırması / Terminal Configuration
   - Vim Kopyalama / Vim Copy
   - SSH Kopyalama / SSH Copy

3. Sistem Askıya Alma / System Suspend
   - Askıya Alma Engelleme / Prevent Suspend
   - Dosya Kaydetme / Save Files
   - Sistem Durumu Kontrolü / System Status Check
   - Askıya Alma Yönetimi / Suspend Management
   - Zamanlı Askıya Alma / Timed Suspend

4. RDP Kurulumu / RDP Setup
   - XRDP Kurulumu / XRDP Installation
   - XRDP Servis Yönetimi / XRDP Service Management
   - Firewall Ayarları / Firewall Settings
   - Masaüstü Ortamı Ayarları / Desktop Environment Settings
   - Sorun Giderme / Troubleshooting
   - Güvenlik Önerileri / Security Recommendations
   - Bağlantı Bilgileri / Connection Information

5. LAMP install
*****************************************************
   
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

  Debian'da RDP (Remote Desktop Protocol) kurulumu için adım adım rehber:

**TÜRKÇE:**

1. **XRDP Kurulumu:**
```bash
# Sistem güncellemesi
sudo apt update
sudo apt upgrade -y

# XRDP ve XFCE4 masaüstü ortamı kurulumu
sudo apt install xrdp xfce4 xfce4-goodies -y
```

2. **XRDP Servisini Başlatma:**
```bash
# XRDP servisini başlat
sudo systemctl start xrdp

# Sistem başlangıcında otomatik başlatma
sudo systemctl enable xrdp
```

3. **Firewall Ayarları:**
```bash
# UFW ile port açma
sudo ufw allow 3389/tcp

# Firewall'u yeniden başlat
sudo ufw reload
```

4. **Masaüstü Ortamını Ayarlama:**
```bash
# XFCE4 yapılandırma dosyası oluşturma
echo xfce4-session > ~/.xsession

# XRDP yapılandırma dosyasını düzenleme
sudo nano /etc/xrdp/startwm.sh
```

Dosyanın sonuna ekleyin:
```bash
#!/bin/sh
unset DBUS_SESSION_BUS_ADDRESS
unset XDG_RUNTIME_DIR
startxfce4
```

5. **Servisi Yeniden Başlatma:**
```bash
sudo systemctl restart xrdp
```

6. **Bağlantı Durumunu Kontrol Etme:**
```bash
sudo systemctl status xrdp
```

**ENGLISH:**

1. **Installing XRDP:**
```bash
# System update
sudo apt update
sudo apt upgrade -y

# Install XRDP and XFCE4 desktop environment
sudo apt install xrdp xfce4 xfce4-goodies -y
```

2. **Starting XRDP Service:**
```bash
# Start XRDP service
sudo systemctl start xrdp

# Enable automatic start at boot
sudo systemctl enable xrdp
```

3. **Firewall Settings:**
```bash
# Open port with UFW
sudo ufw allow 3389/tcp

# Reload firewall
sudo ufw reload
```

4. **Setting Up Desktop Environment:**
```bash
# Create XFCE4 configuration file
echo xfce4-session > ~/.xsession

# Edit XRDP configuration file
sudo nano /etc/xrdp/startwm.sh
```

Add to end of file:
```bash
#!/bin/sh
unset DBUS_SESSION_BUS_ADDRESS
unset XDG_RUNTIME_DIR
startxfce4
```

5. **Restart Service:**
```bash
sudo systemctl restart xrdp
```

6. **Check Connection Status:**
```bash
sudo systemctl status xrdp
```

**Sorun Giderme / Troubleshooting:**

1. **Bağlantı Sorunları / Connection Issues:**
```bash
# Log kontrolü / Check logs
sudo tail -f /var/log/xrdp.log

# Servis durumu / Service status
sudo systemctl status xrdp
```

2. **İzin Sorunları / Permission Issues:**
```bash
# İzinleri düzenleme / Fix permissions
sudo chown xrdp:xrdp /var/run/xrdp.pid
sudo chown xrdp:xrdp /var/run/xrdp.sock
```

3. **Port Kontrolü / Port Check:**
```bash
# Port dinleme durumu / Port listening status
sudo netstat -tulpn | grep xrdp
```

4. **SSL Sertifika Yenileme / SSL Certificate Renewal:**
```bash
# Sertifikaları yenileme / Renew certificates
sudo xrdp-keygen xrdp auto
```

**Güvenlik Önerileri / Security Recommendations:**

1. **Güçlü Şifre Kullanımı / Strong Password Usage:**
```bash
# Şifre politikası ayarlama / Set password policy
sudo apt install libpam-pwquality
sudo nano /etc/security/pwquality.conf
```

2. **SSH Üzerinden Tünel / SSH Tunneling:**
```bash
# SSH tüneli oluşturma / Create SSH tunnel
ssh -L 3389:localhost:3389 kullanici@sunucu-ip
```

3. **Fail2ban Kurulumu / Install Fail2ban:**
```bash
sudo apt install fail2ban
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local
```

**Bağlantı Bilgileri / Connection Information:**
- Varsayılan Port / Default Port: 3389
- Protokol / Protocol: RDP
- Kullanıcı Adı / Username: Linux kullanıcı adınız / Your Linux username
- Şifre / Password: Linux kullanıcı şifreniz / Your Linux password

Windows'tan bağlanmak için "Uzak Masaüstü Bağlantısı" (Remote Desktop Connection) uygulamasını kullanabilirsiniz. / You can use Remote Desktop Connection application from Windows to connect.

Debian'da LAMP (Linux, Apache, MySQL, PHP) stack kurulumunu adım adım anlatayım:

1. Sistem Güncellemesi / System Update:
```bash
sudo apt update
sudo apt upgrade -y
```

2. Apache Web Server Kurulumu / Apache Installation:
```bash
# Apache kurulumu
sudo apt install apache2

# Apache'yi başlatma
sudo systemctl start apache2
sudo systemctl enable apache2

# Durumu kontrol
sudo systemctl status apache2
```

3. MySQL (MariaDB) Kurulumu / MySQL Installation:
```bash
# MySQL kurulumu
sudo apt install mariadb-server mariadb-client

# MySQL'i başlatma
sudo systemctl start mariadb
sudo systemctl enable mariadb

# Güvenlik yapılandırması
sudo mysql_secure_installation
```

4. PHP Kurulumu / PHP Installation:
```bash
# PHP ve gerekli modüllerin kurulumu
sudo apt install php php-mysql php-cli php-common php-mbstring php-gd php-curl php-xml php-zip

# Apache PHP modülü
sudo apt install libapache2-mod-php

# Apache'yi yeniden başlatma
sudo systemctl restart apache2
```

5. Test ve Doğrulama / Testing:
```bash
# PHP bilgi sayfası oluşturma
sudo nano /var/www/html/info.php
```

PHP test dosyası içeriği:
```php
<?php
phpinfo();
?>
```

6. İzinler ve Güvenlik / Permissions:
```bash
# Web dizini izinleri
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```

7. Firewall Ayarları / Firewall Settings:
```bash
# HTTP ve HTTPS portlarını açma
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw reload
```

8. PhpMyAdmin Kurulumu (Opsiyonel) / PhpMyAdmin Installation:
```bash
# PhpMyAdmin kurulumu
sudo apt install phpmyadmin

# Apache yapılandırması
sudo ln -s /usr/share/phpmyadmin /var/www/html/phpmyadmin
```

Önemli Dizinler / Important Directories:
```bash
# Web root dizini
/var/www/html/

# Apache yapılandırma
/etc/apache2/

# PHP yapılandırma
/etc/php/

# MySQL yapılandırma
/etc/mysql/
```

Temel Komutlar / Basic Commands:
```bash
# Apache yönetimi
sudo systemctl start|stop|restart|status apache2

# MySQL yönetimi
sudo systemctl start|stop|restart|status mariadb

# Apache hata logları
sudo tail -f /var/log/apache2/error.log

# PHP hata logları
sudo tail -f /var/log/php_errors.log
```

Güvenlik Önerileri / Security Tips:
1. Güçlü şifreler kullanın / Use strong passwords
2. Düzenli güncellemeleri yapın / Regular updates
3. SSL sertifikası kurun / Install SSL certificate
4. Güvenlik duvarını yapılandırın / Configure firewall
5. Dosya izinlerini kontrol edin / Check file permissions

SSL Sertifikası Kurulumu / SSL Certificate:
```bash
# Let's Encrypt kurulumu
sudo apt install certbot python3-certbot-apache

# Sertifika alma
sudo certbot --apache
```

Virtual Host Oluşturma / Creating Virtual Host:
```bash
# Yapılandırma dosyası oluşturma
sudo nano /etc/apache2/sites-available/site.conf

# Virtual host aktif etme
sudo a2ensite site.conf
sudo systemctl reload apache2
```

Hata Ayıklama / Troubleshooting:
1. Apache error logs kontrol
2. PHP error logs kontrol
3. MySQL error logs kontrol
4. İzinlerin doğruluğunu kontrol
5. Modüllerin aktif olduğunu kontrol

Not / Note:
- Her kurulumdan sonra servisleri yeniden başlatın
- Güvenlik güncellemelerini düzenli takip edin
- Yedekleme rutini oluşturun
- Performans optimizasyonu yapın
