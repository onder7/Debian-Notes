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
6. OpenSSH install
7. Debian/Linux sisteminde saat ve tarih güncelleme işlemleri
8. Debian/Linux'ta uyku moduna girmeyi engelleme yöntemleri
9. FTP sunucusu kurulumu için vsftpd (Very Secure FTP Daemon) kullanacağız
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

8. PhpMyAdmin Kurulumu (Opsiyonel) / PhpMyAdmin Installation /phpMyAdmin secure Installation adım adım yapalım:

1. İlk olarak paket deposunu güncelleyelim:
```bash
sudo apt update
```

2. phpMyAdmin ve gerekli PHP paketlerini kuralım:
```bash
sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl
```

Kurulum sırasında şu adımlarla karşılaşacaksınız:

- Web sunucusu seçimi penceresi geldiğinde:
  - Apache2 kullanıyorsanız [*] Apache2'yi seçin (Space tuşu ile seçim yapılır)
  - Tab tuşu ile OK'a gelip Enter'a basın

- "Configuring phpmyadmin" ekranında:
  - "Yes" seçeneğini seçin ve phpMyAdmin veritabanını otomatik yapılandırmasına izin verin

- Veritabanı yapılandırması için bir şifre belirlemeniz istenecek:
  - Güvenli bir şifre belirleyin ve not alın
  - Şifreyi tekrar girin

3. PHP'yi yeniden başlatalım:
```bash
sudo systemctl restart apache2
```

4. Güvenlik için Apache'de phpMyAdmin konfigürasyonunu düzenleyelim:
```bash
sudo nano /etc/apache2/conf-available/phpmyadmin.conf
```

Bu dosyaya şu satırları ekleyin (veya düzenleyin):
```apache
<Directory /usr/share/phpmyadmin>
    Options FollowSymLinks
    DirectoryIndex index.php
    AllowOverride All
    
    <IfModule mod_php.c>
        php_flag magic_quotes_gpc Off
        php_flag track_vars On
        php_flag register_globals Off
        php_value include_path .
    </IfModule>
    
    # Limit access to localhost only
    Require local
</Directory>
```

5. Apache'yi yeniden başlatalım:
```bash
sudo systemctl restart apache2
```

Artık phpMyAdmin'e erişebilirsiniz:
- Web tarayıcınızda şu adresi açın: `http://localhost/phpmyadmin` veya `http://sunucu-ip-adresi/phpmyadmin`
- Kullanıcı adı olarak "root"
- Şifre olarak MySQL root şifrenizi kullanın

///////////////phpmayadmin//////////////

************gerekirsese yeniden yapılandırma************

Tamam, phpMyAdmin'i yeniden yapılandıralım:

1. Önce yeniden yapılandırma komutunu çalıştıralım:
```bash
sudo dpkg-reconfigure phpmyadmin
```

Bu komuttan sonra karşınıza aşağıdaki adımlar çıkacak:

2. Yapılandırma Adımları:
   - Web sunucusu seçimi ekranında:
     - [*] Apache2'yi seçin (Space tuşu ile)
     - Tab tuşu ile OK'a gelip Enter'a basın

   - "Configure database for phpmyadmin with dbconfig-common?" sorusuna:
     - "Yes" seçeneğini seçin

   - phpMyAdmin veritabanı için şifre belirleme:
     - Güvenli bir şifre girin (örneğin: şifreniz)
     - Şifreyi tekrar girin

3. Yapılandırma tamamlandıktan sonra, gerekli servisleri yeniden başlatalım:
```bash
sudo systemctl restart mysql
sudo systemctl restart apache2
```

4. İzinleri kontrol edelim:
```bash
sudo chown -R www-data:www-data /etc/phpmyadmin/
sudo chmod 644 /etc/phpmyadmin/config.inc.php
```

5. MySQL'de root kullanıcısının yetkilendirmesini yapalım:
```bash
sudo mysql
```

MySQL komut satırında:
```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'şifre';
FLUSH PRIVILEGES;
EXIT;
```

6. Son olarak, tüm ayarların doğru çalıştığından emin olmak için tekrar servisleri yeniden başlatalım:
```bash
sudo systemctl restart mysql
sudo systemctl restart apache2
```

Şimdi web tarayıcınızdan phpMyAdmin'e erişmeyi deneyin:
```
http://localhost/phpmyadmin
```
veya
```
http://sunucu-ip-adresi/phpmyadmin
```

Kullanıcı adı: root
Şifre: şifre

Eğer hala bir sorunla karşılaşırsanız, lütfen hatayı paylaşın. Size yardımcı olmaya devam edeceğim.

*********************************************************


Güvenlik İpuçları:
1. phpMyAdmin dizinini yeniden adlandırabilirsiniz
2. .htaccess ile ek güvenlik katmanı ekleyebilirsiniz
3. Erişimi belirli IP adreslerine kısıtlayabilirsiniz



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

  SSH Server kurulumunu adım adım anlatıyorum:

1. SSH Server Kurulumu / SSH Server Installation:
```bash
# Güncelleme
sudo apt update
sudo apt upgrade

# OpenSSH Server kurulumu
sudo apt install openssh-server
```

2. Servis Yönetimi / Service Management:
```bash
# Servisi başlatma
sudo systemctl start ssh

# Otomatik başlatma
sudo systemctl enable ssh

# Servis durumu kontrolü
sudo systemctl status ssh
```

3. Temel Güvenlik Ayarları / Basic Security Settings:
```bash
# SSH yapılandırma dosyası
sudo nano /etc/ssh/sshd_config

# Önemli güvenlik ayarları:
Port 2222                  # Varsayılan portu değiştir
PermitRootLogin no        # Root girişini engelle
PasswordAuthentication no  # Şifre ile girişi kapat
PubkeyAuthentication yes  # Anahtar ile girişe izin ver
AllowUsers kullanici1     # İzin verilen kullanıcılar
MaxAuthTries 3            # Maksimum deneme sayısı
```

4. Firewall Ayarları / Firewall Settings:
```bash
# SSH portu için güvenlik duvarını yapılandırma
sudo ufw allow 2222/tcp
sudo ufw enable
sudo ufw status
```

5. SSH Anahtar Yönetimi / SSH Key Management:
```bash
# Client tarafında anahtar oluşturma
ssh-keygen -t rsa -b 4096

# Açık anahtarı sunucuya kopyalama
ssh-copy-id -p 2222 kullanici@sunucu_ip
```

6. SSH Bağlantı Test / SSH Connection Test:
```bash
# SSH bağlantı testi
ssh -p 2222 kullanici@sunucu_ip
```

7. Log Kontrolü / Log Monitoring:
```bash
# SSH loglarını izleme
sudo tail -f /var/log/auth.log
```

8. Fail2ban Kurulumu / Fail2ban Installation:
```bash
# Fail2ban kurulumu
sudo apt install fail2ban

# Yapılandırma
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local
```

9. İzinler / Permissions:
```bash
# SSH dizini izinleri
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

10. Güvenlik İpuçları / Security Tips:
- Güçlü şifreler kullanın
- Varsayılan portu değiştirin
- Anahtar tabanlı kimlik doğrulama kullanın
- Fail2ban kullanın
- Logları düzenli kontrol edin

11. Sorun Giderme / Troubleshooting:
```bash
# Bağlantı sorunları için debug modu
ssh -vv kullanici@sunucu_ip

# SSH servis durumu
sudo systemctl status ssh

# Port kontrolü
sudo netstat -tulpn | grep ssh
```

12. SSH Config Örneği / SSH Config Example:
```bash
# ~/.ssh/config dosyası
Host sunucu_adi
    HostName sunucu_ip
    Port 2222
    User kullanici
    IdentityFile ~/.ssh/id_rsa
```

13. Otomatik Bağlantı / Auto Connection:
```bash
# Anahtar oluşturma (parolasız)
ssh-keygen -t rsa -N "" -f ~/.ssh/id_rsa

# Anahtarı sunucuya kopyalama
ssh-copy-id -i ~/.ssh/id_rsa.pub kullanici@sunucu_ip
```

Önemli Notlar / Important Notes:
- Her değişiklikten sonra servisi yeniden başlatın
- Güvenlik güncellemelerini düzenli yapın
- Yedekleme rutini oluşturun
- Sadece gerekli portları açık tutun
- SSH anahtarlarını güvenli saklayın

Yararlı Komutlar / Useful Commands:
```bash
# Bağlı kullanıcıları görme
who

# Aktif SSH oturumları
w

# SSH versiyonu kontrol
ssh -V

# SSH anahtar parmak izi
ssh-keygen -l -f ~/.ssh/id_rsa.pub
```
Debian/Linux sisteminde saat ve tarih güncelleme işlemleri

1. Manuel Saat/Tarih Ayarlama / Manual Date/Time Setting:
```bash
# Tarih ve saat ayarlama
sudo date --set="2024-11-24 14:30:00"

# Sadece saat ayarlama
sudo date +%T -s "14:30:00"

# Sadece tarih ayarlama
sudo date +%Y%m%d -s "20241124"
```

2. NTP (Network Time Protocol) ile Otomatik Ayarlama:
```bash
# NTP kurulumu
sudo apt update
sudo apt install ntp

# NTP servisi başlatma
sudo systemctl start ntp
sudo systemctl enable ntp

# NTP durumu kontrolü
sudo systemctl status ntp
```

3. Zaman Dilimi Ayarları / Timezone Settings:
```bash
# Mevcut zaman dilimini görme
timedatectl

# Kullanılabilir zaman dilimlerini listeleme
timedatectl list-timezones

# Zaman dilimini değiştirme
sudo timedatectl set-timezone Europe/Istanbul
```

4. Donanım Saati Senkronizasyonu:
```bash
# Sistem saatini donanım saatine yazma
sudo hwclock --systohc

# Donanım saatini okuma
sudo hwclock --show

# Donanım saatini ayarlama
sudo hwclock --set --date="2024-11-24 14:30:00"
```

5. Chrony ile Saat Senkronizasyonu:
```bash
# Chrony kurulumu
sudo apt install chrony

# Servisi başlatma
sudo systemctl start chronyd
sudo systemctl enable chronyd

# Durum kontrolü
chronyc tracking
```

Yararlı Komutlar / Useful Commands:
```bash
# Mevcut saat ve tarihi gösterme
date

# NTP sunucuları ile senkronizasyon durumu
ntpq -p

# Sistem saati ayarlarını görme
timedatectl status

# Zaman senkronizasyonunu kontrol etme
sudo timedatectl set-ntp true
```

Not / Notes:
- Sunucu sistemlerinde NTP kullanımı önerilir
- Zaman dilimi değişikliklerinde sistemin yeniden başlatılması gerekebilir
- Saat değişikliği bazı servisleri etkileyebilir
- Donanım saati UTC formatında tutulur

Debian/Linux'ta uyku moduna girmeyi engelleme yöntemleri:

1. Sistem Ayarlarından Engelleme / System Settings:
```bash
# Güç yönetimi ayarlarını değiştirme
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

# Servisleri kontrol etme
systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target
```

2. Komut Satırı ile Geçici Engelleme / Temporary Prevention:
```bash
# systemd-inhibit kullanımı
systemd-inhibit --what=sleep --who="$USER" --why="Prevent suspend" --mode=block sleep infinity

# caffeine benzeri uygulama
sudo apt install caffeine
```

3. Güç Yönetimi Ayarları / Power Management:
```bash
# GNOME için
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'nothing'
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 'nothing'

# KDE için
qdbus org.kde.Solid.PowerManagement /org/kde/Solid/PowerManagement set suppressSleep true
```

4. systemd Yapılandırması / systemd Configuration:
```bash
# logind.conf düzenleme
sudo nano /etc/systemd/logind.conf

# Eklenecek/değiştirilecek satırlar:
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
IdleAction=ignore
```

5. DPMS (Ekran Güç Yönetimi) Ayarları:
```bash
# DPMS'i devre dışı bırakma
xset -dpms
xset s off

# Kalıcı yapmak için ~/.xprofile'a ekleyin:
echo "xset -dpms" >> ~/.xprofile
echo "xset s off" >> ~/.xprofile
```

6. Otomatik Script Oluşturma / Create Automatic Script:
```bash
# Script oluşturma
sudo nano /usr/local/bin/prevent-suspend.sh

# Script içeriği
#!/bin/bash
while true; do
    xdotool keydown Shift; xdotool keyup Shift
    sleep 59
done

# Çalıştırılabilir yapma
sudo chmod +x /usr/local/bin/prevent-suspend.sh
```

7. Kernel Parametreleri / Kernel Parameters:
```bash
# GRUB yapılandırması
sudo nano /etc/default/grub

# Eklenecek parametre
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noacpi"

# GRUB güncelleme
sudo update-grub
```

8. Otomatik Başlangıç Ayarı / Autostart Setting:
```bash
# Autostart dosyası oluşturma
mkdir -p ~/.config/autostart
nano ~/.config/autostart/prevent-suspend.desktop

# Dosya içeriği
[Desktop Entry]
Type=Application
Name=Prevent Suspend
Exec=/usr/local/bin/prevent-suspend.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
```

Önemli Notlar / Important Notes:
- Bazı ayarlar masaüstü ortamına göre değişebilir
- Sistem güncellemelerinde ayarlar sıfırlanabilir
- Pil kullanımı artabilir
- Güvenlik güncellemeleri için sistem yeniden başlatılmalıdır

Sorun Giderme / Troubleshooting:
```bash
# Güç yönetimi durumu
powerprofilesctl get

# Uyku modu durumu
systemctl status systemd-suspend.service

# Aktif inhibitörleri görme
systemd-inhibit --list
```

GUI Uygulamaları / GUI Applications:
- Caffeine
- GNOME Tweaks
- KDE System Settings
- Power Manager Settings

Her masaüstü ortamı için ayarlar farklı olabilir, kullandığınız ortama göre uygun yöntemi seçin.

9. FTP sunucusu kurmak için vsftpd (Very Secure FTP Daemon) kullanacağız. Adım adım kuralım:

1. Önce vsftpd'yi yükleyelim:
```bash
sudo apt update
sudo apt install vsftpd
```

2. Orijinal config dosyasını yedekleyelim:
```bash
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.backup
```

3. vsftpd.conf dosyasını düzenleyelim:
```bash
sudo nano /etc/vsftpd.conf
```

vsftpd.conf içeriğini şu şekilde düzenleyelim:
```conf
# Temel Ayarlar
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES

# Güvenlik Ayarları
chroot_local_user=YES
allow_writeable_chroot=YES
ssl_enable=NO
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=40100

# Logging
xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES

# www klasörü için özel ayarlar
local_root=/var/www
user_sub_token=$USER
```

4. FTP için yeni bir kullanıcı oluşturalım:
```bash
sudo adduser ftpuser
```
(Sizden şifre ve kullanıcı bilgileri isteyecek, bunları doldurun)

5. Kullanıcıyı www-data grubuna ekleyelim:
```bash
sudo usermod -aG www-data ftpuser
```

6. www dizini için izinleri düzenleyelim:
```bash
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www
```

7. vsftpd servisini yeniden başlatalım:
```bash
sudo systemctl restart vsftpd
```

8. Firewall ayarlarını yapalım (eğer UFW kullanıyorsanız):
```bash
sudo ufw allow 20/tcp
sudo ufw allow 21/tcp
sudo ufw allow 40000:40100/tcp
sudo ufw enable
```

Artık FTP sunucunuz hazır! Şu bilgilerle bağlanabilirsiniz:
- Host: sunucu-ip-adresi
- Port: 21
- Kullanıcı adı: ftpuser
- Şifre: (oluşturduğunuz şifre)

FTP istemcisi olarak şunları kullanabilirsiniz:
- FileZilla
- WinSCP (Windows için)
- Cyberduck (Mac için)

Güvenlik İpuçları:
1. Güçlü şifreler kullanın
2. Mümkünse SFTP kullanın (daha güvenli)
3. Sadece gerekli dizinlere erişim verin
4. Düzenli olarak log dosyalarını kontrol edin

Örnek bir kullanıcı ve klasör erişimi için; kök dizinideki python klasörüne özel bir kullanıcı erişimi yapacağız.

Python klasörüne erişim için yeni bir FTP kullanıcısı oluşturalım:

1. Yeni bir kullanıcı oluşturalım:
```bash
sudo adduser pythonuser
```
(Şifre ve kullanıcı bilgilerini doldurun)

2. Python klasörünüz için (örneğin /python) dizin oluşturalım:
```bash
sudo mkdir /python
```

3. Klasör sahipliği ve izinlerini ayarlayalım:
```bash
sudo chown -R pythonuser:pythonuser /python
sudo chmod -R 755 /python
```

4. vsftpd.conf dosyasını düzenleyelim:
```bash
sudo nano /etc/vsftpd.conf
```

Dosyaya şu satırları ekleyelim (eğer yoksa):
```conf
# Kullanıcı bazlı dizin yapılandırması
user_sub_token=$USER
local_root=/home/$USER

# Güvenlik ayarları
chroot_local_user=YES
allow_writeable_chroot=YES
write_enable=YES

# Kullanıcı listesi ayarları
userlist_enable=YES
userlist_file=/etc/vsftpd.userlist
userlist_deny=NO
```

5. Kullanıcı listesi oluşturalım:
```bash
sudo nano /etc/vsftpd.userlist
```

Bu dosyaya kullanıcıları ekleyelim:
```
ftpuser
pythonuser
```

6. Python kullanıcısı için özel bir yapılandırma dosyası oluşturalım:
```bash
sudo mkdir -p /etc/vsftpd/users
sudo nano /etc/vsftpd/users/pythonuser
```

İçeriği şu şekilde olsun:
```
local_root=/python
```

7. Ana vsftpd.conf dosyasına bu kullanıcı yapılandırmasını ekleyelim:
```bash
sudo nano /etc/vsftpd.conf
```

Dosyanın sonuna ekleyin:
```conf
user_config_dir=/etc/vsftpd/users
```

8. Servisi yeniden başlatalım:
```bash
sudo systemctl restart vsftpd
```

9. İzinleri test edelim:
```bash
sudo -u pythonuser touch /python/test.txt
```

Artık şu bilgilerle bağlanabilirsiniz:
- Host: sunucu-ip-adresi
- Port: 21
- Kullanıcı adı: pythonuser
- Şifre: (oluşturduğunuz şifre)

Test etmek için:
1. FileZilla veya başka bir FTP istemcisi kullanın
2. Yukarıdaki bilgilerle bağlanın
3. /python dizinine dosya yüklemeyi deneyin

Güvenlik notları:
1. Python klasöründe çalıştırılabilir dosyalar için dikkatli olun
2. Düzenli olarak log dosyalarını kontrol edin
3. Güçlü şifre kullandığınızdan emin olun

Eğer bağlantı veya izin sorunları yaşarsanız, lütfen bildirin. Size yardımcı olmaya devam edeceğim.

