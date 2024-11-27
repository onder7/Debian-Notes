# Shell Script (Kabuk Programlama) Eğitimi

Bu eğitim dokümanı, Linux/Unix sistemlerinde shell script (kabuk programlama) konusunda kapsamlı bir rehber sunmaktadır. Temel kavramlardan başlayarak ileri düzey uygulamalara kadar adım adım örneklerle shell programlamanın inceliklerini öğrenebilirsiniz.

## Ne Öğreneceksiniz?
- Shell scripting temelleri ve sözdizimi
- Değişkenler, operatörler ve kontrol yapıları
- Fonksiyonlar ve modüler programlama
- Komut satırı araçları ve dosya işlemleri
- Pratik uygulamalar ve örnek projeler

## Kimler İçin Uygun?
- Linux/Unix sistemlerinde otomasyon yapmak isteyenler
- Sistem yöneticileri ve DevOps uzmanları
- Shell programlamaya başlamak isteyen geliştiriciler
- Komut satırı becerilerini geliştirmek isteyenler

Tüm konular örneklerle desteklenmiş olup, başlangıç seviyesinden ileri seviyeye kadar detaylı açıklamalar içermektedir.

[Detaylı içeriğe buradan ulaşabilirsiniz](#)

***************************
# Kabuk Programlamaya Giriş

## Kabuk Programlama (Shell Scripting) Nedir?
Kabuk programlama, Linux ortamında komutlar yazarak ve çalıştırarak görevleri otomatikleştirmenizi ve düzenlemenizi sağlayan güçlü bir programlama yöntemidir. Özellikle şu alanlarda değerlidir:
- Sistem yönetimi
- Görev otomatizasyonu
- Verimliliği artırma

## Kabuk (Shell) Türleri
İşte en yaygın kullanılan kabuklar:

1. **Bash (Bourne Again Shell)**
   - En yaygın kullanılan kabuk
   - Birçok Linux dağıtımında varsayılan kabuk

2. **sh (Bourne Shell)**
   - Orijinal Unix kabuğu
   - Bash'in öncüsü

3. **ksh (Korn Shell)**
   - csh ve sh'nin özelliklerini birleştirir
   - Unix ortamlarında popüler

4. **zsh (Z Shell)**
   - Gelişmiş özelliklere sahip modern kabuk
   - Yeni macOS sürümlerinde varsayılan kabuk

# Kabuk Türünüzü Kontrol Etme
Mevcut kabuğunuzu belirlemek için aşağıdaki komutu çalıştırın:
```bash
echo $0
```

# Dosya Oluşturma ve Kullanma
Unix ve Linux ortamlarında vi komutunu kullanarak dosya oluşturma ve düzenleme temel bir beceridir. İşte vi ile dosya oluşturma, içerik girme ve kaydetme adımları:

## 1. Yeni Dosya Oluşturmak için vi'yi Açma
- Terminalinizi açın
- Şu komutu yazın: `vi my_script.sh`
- Not: my_script.sh mevcut değilse, vi bu isimde yeni bir dosya oluşturacaktır

## 2. Temel vi Düzenleme Komutları
vi'yi açtığınızda, komut modundasınız. Yazma moduna geçmek için:
- `i` tuşuna basın. Artık dosyaya içerik yazabilirsiniz

## 3. vi'de İçerik Yazma
"Merhaba, Dünya!" yazan ve mevcut tarih/saati gösteren basit bir betik oluşturalım:
```bash
#!/bin/bash
# Bu betik bir karşılama mesajı ve mevcut tarih/saati yazdırır
echo "Merhaba, Dünya!"
echo "Mevcut tarih ve saat:"
date
```

## 4. Yazma Modundan Çıkma
- Komut moduna dönmek için `Esc` tuşuna basın

## 5. vi'de Kaydetme ve Çıkma
- Kaydet ve çık: `:wq` yazıp Enter'a basın
- Sadece kaydet: `:w` yazıp Enter'a basın
- Kaydetmeden çık: `:q!` yazıp Enter'a basın

## 6. Betiği Çalıştırılabilir Yapma
```bash
chmod +x my_script.sh
```

## 7. Betiği Çalıştırma
```bash
./my_script.sh
```

## 8. Çalıştırılabilir Yapmadan Betiği Çalıştırma
```bash
bash my_script.sh
```

Çıktı şuna benzer olacaktır:
```
Merhaba, Dünya!
Mevcut tarih ve saat:
Sal Kas 6 12:34:56 UTC 2023
```

# İşlem Kontrol Kısayolları
- `Ctrl + C`: Çalışan işlemi anında sonlandırır
- `Ctrl + Z`: İşlemi duraklatır ve arka plana gönderir (fg veya bg ile devam ettirilebilir)

# Kabuk Programlamada Yorumlar
Tek Satırlık Yorumlar:
```bash
# Bu bir tek satırlık yorumdur
echo "Merhaba, Dünya!"
```
# Çok Satırlı Yorumlar

Bash'te çok satırlı yorumlar için doğrudan bir sözdizimi yoktur, ancak bunu iki farklı yöntemle yapabilirsiniz:

## 1. Here-Document Kullanarak:
```bash
: <<'COMMENT'
Bu bir çok satırlı yorumdur.
Buraya birden fazla satır ekleyebilirsiniz.
İstediğiniz kadar satır yazabilirsiniz.
COMMENT
```

## 2. << Sözdizimini Doğrudan Kullanarak:
```bash
<<COMMENT
Bu da çok satırlı yorum için
alternatif bir yöntemdir.
İstediğiniz kadar satır ekleyebilirsiniz.
COMMENT
```

Not: Her iki yöntemde de 'COMMENT' yerine istediğiniz herhangi bir kelime kullanabilirsiniz, ancak başlangıç ve bitiş kelimeleri aynı olmalıdır.
# Değişkenler ve Dizilerle Çalışma

Değişkenler ve diziler, betiklerde veri depolama ve işleme olanağı sağlar, bu da otomasyonu daha esnek hale getirir.

## Değişkenler
Değişken tanımlama ve değerine erişmek için $ kullanma:
```bash
NAME="Linux"
echo "Welcome to $NAME Scripting"
```

## Sabitler
readonly ile salt okunur değişkenler oluşturma:
```bash
readonly VERSION="1.0"
```

## Diziler
Birden fazla değer depolama:
```bash
myArray=(1 2 3 "Hello" "World")
echo "${myArray[1]}"
# Çıktı: 2
```

### Dizi İşlemleri:

#### Dizi Uzunluğunu Alma:
```bash
echo "${#myArray[@]}"  # veya
echo "${#myArray[*]}"
# Dizideki toplam eleman sayısını döndürür
```

#### Diziden Belirli Değerleri Alma:
Belirli bir indeksten başlayarak değerleri alma:
```bash
echo "${myArray[*]:1}"
# İkinci elemandan (indeks 1) başlayarak tüm elemanları getirir
```

#### Belirli Aralıktaki Değerleri Alma:
```bash
echo "${myArray[*]:1:2}"
# İndeks 1'den başlayarak 2 eleman getirir
```

#### Dizi Güncelleme (Yeni eleman ekleme):
```bash
myArray+=(5 6 8)
```

### İlişkisel Dizilerle Çalışma:

#### Tanımlama ve Başlatma:
```bash
declare -A myArray
myArray=( [name]=Paul [age]=20 )
```

#### Değerlere Erişim:
```bash
echo "${myArray[name]}"
```

#### Dizi Uzunluğunu Alma:
```bash
echo "${#myArray[@]}"
```

#### Dizi Güncelleme:
```bash
myArray+=( [city]=NewYork )
```

💡 **İpucu**: Diziler, dosya adları veya yapılandırmalar gibi değer listelerini yönetmek için kullanışlıdır.

# Metin ve Aritmetik İşlemler

## Metin İşleme Örnekleri:

### Temel Metin İşlemleri:
```bash
str="Shell Scripting"

# Uzunluk
echo ${#str}      # Çıktı: 15

# Değiştirme
echo ${str/Scripting/Programming}   # Çıktı: Shell Programming

# Alt Metin Çıkarma
echo ${str:6:9}   # Çıktı: Scripting
```

### Gelişmiş Metin İşlemleri:
```bash
myVar="Hello World!"

# Metin uzunluğunu alma
length=${#myVar}
echo $length      # Çıktı: 12

# Büyük harfe çevirme
upper=${myVar^^}
echo $upper       # Çıktı: HELLO WORLD!

# Küçük harfe çevirme
lower=${myVar,,}
echo $lower       # Çıktı: hello world!

# Alt metin değiştirme
replace=${myVar/World/Buddy}
echo $replace     # Çıktı: Hello Buddy!

# Alt metin çıkarma (dilim)
slice=${myVar:6:5}
echo $slice       # Çıktı: World
```

# KULLANICI ETKİLEŞİMLERİ

## Kullanıcıdan Veri Alma

### Temel Veri Alma:
```bash
read var_name
echo "Girdiğiniz: $var_name"
# Örnek Çıktı: (Kullanıcı "John" yazar)
# Girdiğiniz: John
```

### İstemle Veri Alma:
```bash
read -p "Adınız: " NAME
echo "Merhaba, $NAME!"
# Örnek Çıktı: 
# Adınız: John
# Merhaba, John!
```

Temel Farklar:
- Temel Veri Alma: İstem olmadan veri alır
- İstemli Veri Alma: Kullanıcıyı yönlendiren bir istem gösterir

## Aritmetik İşlemler

### let Komutu Kullanımı:
```bash
# Artırma
let a++    # a değerini 1 artırır
```
# Kabuk Programlamada Koşullu İfadeler ve İşlemler

## Aritmetik İşlemler

### Çarpma ile Atama:
```bash
# let kullanarak
let a=5*10
echo $a    # Çıktı: 50

# (( )) kullanarak
((a=5*10))
echo $a    # Çıktı: 50
```

### Karmaşık Hesaplamalar:
```bash
echo $((5 * (3 + 2)))    # Çıktı: 25
```

Not: `let` geleneksel, `(( ))` ise daha modern ve karmaşık aritmetik ifadelere izin verir.

## Koşullu İfadeler

### if İfadesi:
```bash
if [ $a -gt $b ]; then
    echo "a, b'den büyüktür"
fi
```

### if-else İfadesi:
```bash
if [ $a -gt $b ]; then
    echo "a, b'den büyüktür"
else
    echo "a, b'den büyük değildir"
fi
```

### elif (else if) İfadesi:
```bash
if [ $a -gt $b ]; then
    echo "a, b'den büyüktür"
elif [ $a -eq $b ]; then
    echo "a, b'ye eşittir"
else
    echo "a, b'den küçüktür"
fi
```

### case İfadesi:
```bash
case $a in
    a) echo "a değeri 1" ;;
    b) echo "a değeri 2" ;;
    *) echo "a değeri ne 1 ne de 2" ;;
esac
```

## Karşılaştırma Operatörleri

- **Eşittir**: `-eq` veya `==`
  ```bash
  [ $a -eq $b ]
  ```

- **Büyük Eşittir**: `-ge`
  ```bash
  [ $a -ge $b ]
  ```

- **Küçük Eşittir**: `-le`
  ```bash
  [ $a -le $b ]
  ```

- **Eşit Değildir**: `-ne` veya `!=`
  ```bash
  [ $a -ne $b ]
  ```

- **Büyüktür**: `-gt`
  ```bash
  [ $a -gt $b ]
  ```

- **Küçüktür**: `-lt`
  ```bash
  [ $a -lt $b ]
  ```

**Önemli Notlar:**
- Koşullarda operatörlerin etrafında boşluk bırakın
- `elif` ve `else` isteğe bağlıdır ama çoklu koşullar için kullanışlıdır
# Mantıksal Operatörler ve Döngüler

## Mantıksal Operatörler

### && (VE) Operatörü:
```bash
a=10
b=5
if [ $a -gt 5 ] && [ $b -lt 10 ]; then
    echo "Her iki koşul da doğru"
else
    echo "Bir veya her iki koşul yanlış"
fi
```

### || (VEYA) Operatörü:
```bash
a=10
b=15
if [ $a -gt 5 ] || [ $b -lt 10 ]; then
    echo "En az bir koşul doğru"
else
    echo "Hiçbir koşul doğru değil"
fi
```

### && ve || Operatörlerini Birleştirme:
```bash
a=10
b=5
c=15
if [ $a -gt 5 ] && [ $b -lt 10 ] || [ $c -eq 15 ]; then
    echo "Koşul sağlandı"
else
    echo "Koşul sağlanmadı"
fi
```

Açıklama:
- `&&` her iki koşulun da doğru olmasını gerektirir
- `||` ilk koşul başarısız olursa ikinci koşulu kontrol eder

### Üçlü Operatör (Tek Satırlık If-Else):
```bash
a=10
[ $a -gt 5 ] && echo "Büyük" || echo "Büyük Değil"
```

## Döngüler

### For Döngüsü
Liste veya değer aralığı üzerinde yineleme yapar.

Temel Sözdizimi:
```bash
for item in liste; do
    # Her öğe için çalıştırılacak komutlar
done
```

Örnek:
```bash
for i in 1 2 3; do
    echo "Sayı: $i"
done
# Çıktı:
# Sayı: 1
# Sayı: 2
# Sayı: 3
```

Aralık Örneği:
```bash
for i in {1..3}; do
    echo "Sayaç: $i"
done
# Çıktı:
# Sayaç: 1
# Sayaç: 2
# Sayaç: 3
```

### While Döngüsü
Belirtilen koşul doğru olduğu sürece çalışır.

Sözdizimi:
```bash
while [ koşul ]; do
    # Çalıştırılacak komutlar
done
```

Örnek:
```bash
count=1
while [ $count -le 3 ]; do
    echo "Sayaç: $count"
    ((count++))  # Sayacı artır
done
# Çıktı:
# Sayaç: 1
# Sayaç: 2
# Sayaç: 3
```
# Döngü Türleri ve Kullanımları

## Until Döngüsü
Koşul doğru oluncaya kadar çalışmaya devam eder.

Sözdizimi:
```bash
until [ koşul ]; do
    # Çalıştırılacak komutlar
done
```

Örnek:
```bash
count=1
until [ $count -gt 3 ]; do
    echo "Sayaç: $count"
    ((count++))
done
# Çıktı:
# Sayaç: 1
# Sayaç: 2
# Sayaç: 3
```

## Sonsuz Döngüler
Manuel olarak durdurulana kadar (örn: Ctrl+C) çalışmaya devam eder.

### For ile Sonsuz Döngü:
```bash
for (( ; ; )); do
    echo "Bu bir sonsuz döngüdür"
done
```

### While ile Sonsuz Döngü:
```bash
while :; do
    echo "While ile sonsuz döngü"
done
```

### Until ile Sonsuz Döngü:
```bash
until false; do
    echo "Until ile sonsuz döngü"
done
```

## Select Döngüsü
Kullanıcının bir listeden seçim yapmasını sağlayan basit bir menü sistemi oluşturur.

Sözdizimi:
```bash
select seçenek in liste; do
    # Kullanıcı seçimine göre komutlar
done
```

Örnek:
```bash
PS3="Bir meyve seçin: "
select meyve in Elma Muz Portakal Çıkış; do
    case $meyve in
        Elma) echo "Elma'yı seçtiniz";;
        Muz) echo "Muz'u seçtiniz";;
        Portakal) echo "Portakal'ı seçtiniz";;
        Çıkış) break;;
        *) echo "Geçersiz seçenek";;
    esac
done
```

Örnek Çıktı:
```
1) Elma
2) Muz
3) Portakal
4) Çıkış
Bir meyve seçin: 2
Muz'u seçtiniz
```

Açıklama:
- `PS3` istem mesajını belirler
- `select` döngüsü seçenekleri gösterir ve her seçim ilgili case ifadesini çalıştırır
- `break` komutu kullanıcı "Çıkış"ı seçtiğinde döngüden çıkar

## Döngü Türlerinin Özeti
- **For Döngüsü**: Liste veya aralık üzerinde yineleme yapar
- **While Döngüsü**: Koşul doğru olduğu sürece devam eder
- **Until Döngüsü**: Koşul doğru oluncaya kadar devam eder
- **Sonsuz Döngü**: Kesintiye uğratılana kadar çalışır
- **Select Döngüsü**: Kullanıcı seçimi için menü gösterir

💡 **İpucu**: Döngüler tekrarlayan görevleri otomatikleştirmek için güçlü araçlardır. Dosyalar, diziler veya aralıklar üzerinde yineleme yapmak gibi çeşitli amaçlar için kullanılabilirler. Örneğin, bir dizindeki tüm dosyaları yeniden adlandırmak için döngü kullanabilirsiniz.

# Kabuk Programlamada Fonksiyonlar

## 1. Fonksiyon Tanımlama
İki farklı sözdizimi kullanılabilir:
```bash
function fonksiyon_adı {
    # kodlar
}
# veya
fonksiyon_adı() {
    # kodlar
}
```

## 2. Temel Fonksiyon
```bash
selamla() {
    echo "Merhaba, kabuk betiğine hoş geldiniz!"
}
selamla  # Fonksiyonu çağırma
```

## 3. Parametreli Fonksiyonlar
```bash
kullanici_selamla() {
    echo "Merhaba, $1!"
}
kullanici_selamla "Ahmet"
```

## 4. Dönüş Değerleri
```bash
sayilari_topla() {
    sonuc=$(( $1 + $2 ))
    echo $sonuc
}
toplam=$(sayilari_topla 3 5)
echo "Toplam: $toplam"
```

## 5. Koşullu Mantık ve Döngüler
```bash
cift_kontrol() {
    if (( $1 % 2 == 0 )); then
        echo "$1 çift sayıdır"
    else
        echo "$1 tek sayıdır"
    fi
}
cift_kontrol 7  # Çıktı: "7 tek sayıdır"
```

## 6. Özyineleme (Recursion)
```bash
faktoriyel() {
    if [ $1 -le 1 ]; then
        echo 1
    else
        onceki=$(faktoriyel $(( $1 - 1 )))
        echo $(( $1 * onceki ))
    fi
}
sonuc=$(faktoriyel 5)
echo "5'in faktöriyeli: $sonuc"
```

## 7. Varsayılan Değerler
```bash
selamla() {
    local isim=${1:-Misafir}
    echo "Merhaba, $isim!"
}
selamla "Ahmet"  # Çıktı: "Merhaba, Ahmet!"
selamla          # Çıktı: "Merhaba, Misafir!"
```

## 8. Referans ile Parametre Geçme
```bash
deger_degistir() {
    eval $1=\$2
}
deger_degistir degisken 100
echo "Değişkenin yeni değeri: $degisken"
```

## 9. Argüman Geçme
### Konumsal Argümanlar ($1, $2, $3, vb.)
```bash
selamla() {
    echo "Merhaba, $1! $2 yaşındasın."
}
selamla "Ahmet" 25
```

### Tüm Argümanlar ($@)
```bash
hepsini_yazdir() {
    for arg in "$@"; do
        echo "$arg"
    done
}
hepsini_yazdir "Elma" "Armut" "Kiraz"
```

### Tek String Olarak Tüm Argümanlar ($*)
```bash
string_olarak_yazdir() {
    echo "$*"
}
string_olarak_yazdir "Elma" "Armut" "Kiraz"
```

### Argüman Sayısı ($#)
```bash
arguman_say() {
    echo "Argüman sayısı: $#"
}
arguman_say "Elma" "Armut" "Kiraz"
```

## Özet
- Fonksiyonlar kodu düzenli ve yeniden kullanılabilir hale getirir
- Argümanlar $1, $2 vb. ile erişilebilir ve varsayılan değerler atanabilir
- Fonksiyonlar içinde döngüler ve koşullar kullanılabilir
- Fonksiyonlar echo ile değer döndürür ve bu değerler değişkenlerde saklanabilir

# Kabuk Programlamada Özel Komutlar ve Kontrol Yapıları

## shift Operatörü
Konumsal parametreleri (argümanları) sola kaydırmak için kullanılır.

Sözdizimi:
```bash
shift    # Bir pozisyon sola kaydırır
shift n  # n pozisyon sola kaydırır
```

### Örnek 1: Tek Pozisyon Kaydırma
```bash
kaydirma_ornegi() {
    echo "Orijinal argümanlar: $1, $2, $3"
    shift
    echo "Kaydırma sonrası: $1, $2, $3"
}
kaydirma_ornegi "bir" "iki" "üç"
# Çıktı:
# Orijinal argümanlar: bir, iki, üç
# Kaydırma sonrası: iki, üç
```

### Örnek 2: Çoklu Kaydırma
```bash
coklu_kaydirma() {
    echo "Orijinal argümanlar: $1, $2, $3, $4"
    shift 2
    echo "2 kez kaydırma sonrası: $1, $2"
}
coklu_kaydirma "elma" "armut" "kiraz" "erik"
```

### Örnek 3: Döngü ile Kullanım
```bash
argumanlari_isle() {
    while [ "$#" -gt 0 ]; do
        echo "İşlenen argüman: $1"
        shift
    done
}
argumanlari_isle "arg1" "arg2" "arg3" "arg4"
```

## Kontrol Komutları

### 1. break Komutu
Döngüyü erken sonlandırır.
```bash
for i in {1..5}; do
    if [ $i -eq 3 ]; then
        break
    fi
    echo $i
done
```

### 2. continue Komutu
Mevcut döngü iterasyonunu atlar.
```bash
for i in {1..5}; do
    if [ $i -eq 3 ]; then
        continue
    fi
    echo $i
done
```

### 3. İç İçe Döngülerde break ve continue
```bash
for i in {1..3}; do
    for j in {1..3}; do
        if [ $i -eq 2 ] && [ $j -eq 2 ]; then
            break 2  # İki seviye döngüden çıkar
        fi
        echo "i=$i, j=$j"
    done
done
```

### 4. sleep Komutu
Betiği belirli bir süre duraklatır.
```bash
sleep 5  # 5 saniye bekler
```

**Önemli Noktalar:**
- `shift` ilk argümanı ($1) kaldırır ve diğerlerini sola kaydırır
- `break n` ile iç içe döngülerden çıkılabilir
- `continue n` ile iç içe döngülerde iterasyon atlanabilir
- `sleep` komutu betik yürütmesini duraklatmak için kullanılır

# Temel Komutlar ve Genişletme Özellikleri

## Kontrol Komutları

### 1. exit Komutu
Betiği durum koduyla sonlandırır (0: başarılı, 0 dışı: hata)
```bash
exit 1  # Hata durumuyla çıkış
```

### 2. $? (Son Komut Çıkış Durumu)
Son çalıştırılan komutun çıkış durumunu saklar
```bash
mkdir myklasor
echo $?  # Başarılıysa 0, başarısızsa 1 döndürür
```

## seq Komutu
Sayı dizileri oluşturmak için kullanılır.

### Temel Kullanım:
```bash
# 1'den 5'e kadar sayılar
seq 1 5
# Çıktı: 1 2 3 4 5

# Özel adım boyutu (1'den 10'a 2'şer artarak)
seq 1 2 10
# Çıktı: 1 3 5 7 9

# Ondalık sayılar
seq 0 0.2 1
# Çıktı: 0.0 0.2 0.4 0.6 0.8 1.0

# Ters sıralama
seq 5 -1 1
# Çıktı: 5 4 3 2 1
```

### Döngü ile Kullanım:
```bash
for i in $(seq 1 5); do
    echo "Sayı: $i"
done
```

### seq Seçenekleri:
```bash
# Biçimlendirme (-f)
seq -f "Sayı: %.2f" 1 5
# Çıktı: Sayı: 1.00 Sayı: 2.00 ...

# Ayırıcı değiştirme (-s)
seq -s "," 1 5
# Çıktı: 1,2,3,4,5

# Sıfırla doldurma (-w)
seq -w 1 5
# Çıktı: 01 02 03 04 05
```

## Süslü Parantez Genişletmesi
Tek bir ifadeden birden çok metin dizisi oluşturma özelliği.

### Temel Örnekler:
```bash
# Kelime listesi
echo {elma,armut,kiraz}
# Çıktı: elma armut kiraz

# Sayı aralığı
echo {1..5}
# Çıktı: 1 2 3 4 5

# Harf aralığı
echo {a..e}
# Çıktı: a b c d e
```

**Özet:**
- `exit`: Betikten çıkış yapar
- `$?`: Son komutun durumunu kontrol eder
- `seq`: Sayı dizileri oluşturur
- Süslü parantez genişletmesi: Metin dizileri oluşturur

# Süslü Parantez Genişletmesi ve getops Komutu

## Gelişmiş Süslü Parantez Kullanımı

### Adım Boyutlu Aralık:
```bash
echo {1..10..2}
# Çıktı: 1 3 5 7 9
```

### Metin ile Değişken Birleştirme:
```bash
echo dosya{1..3}.txt
# Çıktı: dosya1.txt dosya2.txt dosya3.txt
```

### İç İçe Genişletme:
```bash
echo {A,B}{1,2}
# Çıktı: A1 A2 B1 B2
```

### Çoklu Eleman Genişletme:
```bash
echo {A,B,C}{1,2,3}
# Çıktı: A1 A2 A3 B1 B2 B3 C1 C2 C3
```

### Dosya ve Dizinlerle Kullanım:
```bash
mkdir klasor{1,2,3}
# klasor1, klasor2 ve klasor3 dizinlerini oluşturur
```

## getopts Komutu
Komut satırı seçeneklerini (bayrakları) işlemek için kullanılır.

### Temel Sözdizimi:
```bash
getopts "secenek_dizisi" degisken
```

### Örnek 1: Basit Seçenek İşleme
```bash
#!/bin/bash
while getopts "ab" secenek; do
    case $secenek in
        a) echo "A seçeneği seçildi" ;;
        b) echo "B seçeneği seçildi" ;;
        \?) echo "Geçersiz seçenek"; exit 1 ;;
    esac
done

# Kullanım:
# ./betik.sh -a
# Çıktı: A seçeneği seçildi
```

### Örnek 2: Argümanlı Seçenekler
```bash
#!/bin/bash
while getopts "f:n:" secenek; do
    case $secenek in
        f) echo "F seçeneği seçildi, argüman: $OPTARG" ;;
        n) echo "N seçeneği seçildi, argüman: $OPTARG" ;;
        \?) echo "Geçersiz seçenek"; exit 1 ;;
    esac
done

# Kullanım:
# ./betik.sh -f dosya.txt
# Çıktı: F seçeneği seçildi, argüman: dosya.txt
```

### Örnek 3: Uzun Seçeneklerle Kullanım
```bash
#!/bin/bash
while getopts "f:n:" secenek; do
    case $secenek in
        f) echo "Dosya seçeneği: $OPTARG" ;;
        n) echo "İsim seçeneği: $OPTARG" ;;
        \?) echo "Geçersiz seçenek"; exit 1 ;;
    esac
done

# Kullanım:
# ./betik.sh -f metin.txt -n Ahmet
```

**Önemli Noktalar:**
- Süslü parantez genişletmesi diğer kabuk işlemlerinden önce gerçekleşir
- Virgüller arasında boşluk olmamalıdır
- getopts ile seçenekler sistematik şekilde işlenebilir
- Argüman gerektiren seçenekler için `:` kullanılır

# Gelişmiş Komut Satırı İşlemleri ve Örnek Proje

## getopts Ayrıntılı Kullanımı

### Örnek 4: Çoklu Argüman ve Seçenek İşleme
```bash
#!/bin/bash
while getopts "a:b:c:" secenek; do
    case $secenek in
        a) echo "A seçeneği değeri: $OPTARG" ;;
        b) echo "B seçeneği değeri: $OPTARG" ;;
        c) echo "C seçeneği değeri: $OPTARG" ;;
        \?) echo "Geçersiz seçenek"; exit 1 ;;
    esac
done
```

## Dosya İşleme Komutları

### basename
```bash
# Dosya adını yoldan ayırır
basename /home/kullanici/dosya.txt        # Çıktı: dosya.txt
basename /home/kullanici/dosya.txt .txt   # Çıktı: dosya
```

### dirname
```bash
# Dizin yolunu döndürür
dirname /home/kullanici/dosya.txt         # Çıktı: /home/kullanici
```

### realpath
```bash
# Mutlak yolu döndürür
realpath dosya.txt   # Çıktı: /home/kullanici/belgeler/dosya.txt
```

## Dosya ve Dizin Kontrolleri
```bash
if [ -d /home/kullanici/Belgeler ]; then
    echo "Dizin mevcut"
fi

if [ ! -f /home/kullanici/olmayan.txt ]; then
    echo "Dosya mevcut değil"
fi
```

## Sistem Değişkenleri
```bash
echo $RANDOM                  # Rastgele sayı üretir
echo $((RANDOM % 101))       # 0-100 arası rastgele sayı
echo $UID                    # Mevcut kullanıcı ID'si
```

## nohup Kullanımı
```bash
# Arka planda çalıştırma
nohup ./betik.sh &

# Çıktıyı yönlendirme
nohup ./betik.sh > /dev/null 2>&1 &

# Çalışan işlemleri kontrol etme
ps aux | grep betik.sh
```

## Örnek Proje: Hesap Makinesi
```bash
#!/bin/bash

# Toplama fonksiyonu
topla() {
    echo "Sonuç: $(($1 + $2))"
}

# Çıkarma fonksiyonu
cikar() {
    echo "Sonuç: $(($1 - $2))"
}

# Çarpma fonksiyonu
carp() {
    echo "Sonuç: $(($1 * $2))"
}

# Bölme fonksiyonu
bol() {
    if [ $2 -eq 0 ]; then
        echo "Hata: Sıfıra bölme hatası!"
    else
        echo "Sonuç: $(($1 / $2))"
    fi
}

# Menü
echo "Basit Hesap Makinesi"
echo "İşlem seçin:"
echo "1. Toplama"
echo "2. Çıkarma"
echo "3. Çarpma"
echo "4. Bölme"

read -p "Seçiminiz (1/2/3/4): " secim
read -p "İlk sayı: " sayi1
read -p "İkinci sayı: " sayi2

case $secim in
    1) topla $sayi1 $sayi2 ;;
    2) cikar $sayi1 $sayi2 ;;
    3) carp $sayi1 $sayi2 ;;
    4) bol $sayi1 $sayi2 ;;
    *) echo "Geçersiz seçim" ;;
esac
```
# Hesap Makinesi Betiği - Kurulum ve Kullanım

## Kurulum Adımları

### 1. Betiği Çalıştırılabilir Yapma
```bash
chmod +x calculator.sh
```

### 2. Betiği Çalıştırma
```bash
./calculator.sh
```

## Betiğin Çalışma Mantığı
- Kullanıcıdan bir işlem seçmesini ister (toplama, çıkarma, çarpma, bölme)
- İki sayı girmesini bekler
- Seçilen işlemi gerçekleştirir
- Bölme işleminde sıfıra bölme kontrolü yapar

## Örnek Çalıştırma
```
$ ./calculator.sh
Basit Hesap Makinesi
İşlem seçin:
1. Toplama
2. Çıkarma
3. Çarpma
4. Bölme
Seçiminiz (1/2/3/4): 1
İlk sayı: 10
İkinci sayı: 5
Sonuç: 15
```

## Geliştirme Önerileri
Bu basit projeyi şu özelliklerle geliştirebilirsiniz:
- Karekök alma ve üs alma gibi ileri matematik işlemleri
- Sürekli çalışan bir döngü ile tekrarlı hesaplama
- Ondalıklı sayı desteği
- Hata kontrollerinin artırılması
- Geçmiş işlemleri kaydetme
- Bilimsel hesap makinesi özellikleri

Bu proje, kabuk programlamada temel kavramları öğrenmek için iyi bir örnektir:
- Koşullu ifadeler
- Kullanıcı girdisi alma
- Matematiksel işlemler
- Fonksiyon kullanımı
- Hata kontrolü

