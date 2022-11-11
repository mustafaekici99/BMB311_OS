# Projeler

## Proje 0 - B205 Guc Ayarlari Isinin Otomatize Edilmesi (Ekstra Proje)

* Bu projede istenilenleri yerine getiren ogrenciler ekstra odev puani alacaklardir. 
* Bu projenin yapilmasi istege baglidir. Bu projeyi yapmadan da dersin odev notundan 100 alabilmeniz mumkundur.
* Bu projede 4 kisiye kadar takim calismasi yapabilirsiniz.

### Problem Tanimi

B205 laboratuvarina yeni alinan makinalardaki Windows 11 sistemlere
[Deep Freeze](https://www.faronics.com/en-uk/products/deep-freeze) yazilimi kurulmustur. Windows sistemlere bu 
yazilimin kurulmasinin ana nedenleri:
* Bilgisayarlari kullanan ogrencilerin Windows sistemlere kalici olarak program yuklemesinin
* Diske kaydedilen ve sonradan silinmeyen dosyalarla diskin sismesinin
onune gecebilmektedir.

Sistemde Deep Freeze aktive edildikten (frozen durumu) sonra diskte yapilan degisikler kalici olmamaktadir. Bilgisayar
yeniden baslatildiginda Deep Freeze'in aktive edildigi zamandaki sisteme geri donulmektedir.

Bu durumda sistemde degisiklik yapabilmek icin once Deep Freze programini thawed durumuna 
(bilgisayari yeniden baslatmayi gerektiriyor - boot thawed) getirmek ve gerekli degisikleri
yapip sistemde Deep Freeze'i yeniden frozen duruma getirmek (bilgisayari yeniden baslatma gerektiriyor - boot frozen) gerekmektedir.
Deep Freeze'in calisma mantigini daha iyi anlamak icin bu programi kendi bilgisayarinizda denemeniz faydali olabilir.

B205'deki yeni Dell bilgisayarlara Windows sistemler kurulurken guc ayarlari dogru yapilmamistir. Monitor uzerindeki
guc tusuna basildiginda bilgisayarlar kendini uykuya almaktadir ama guc tusuna basildiginda bilgisayarin kendini kapamasi
istenmektedir. Bu degisikligin yapilabilmesi icin Deep Freeze once deaktive edilmelidir. Daha sonra sisteme bu degisiklik
uygulandiktan sonra Deep Freeze yeniden aktive edilmelidir. Bu adimlari her yeni Dell bilgisayar icin tekrarlamaktansa bu isi 
otomatize edecek bir script/program yazmak bu isin yapimini hizlandiracak ve vakit kaybinin onune gececektir.

### Ek Bilgiler

* Windows bilgisayarlarda [SSH](https://www.baeldung.com/cs/ssh-intro) sunucusu calismaktadir. Windows bilgisayarlara lokal IP adresleri kullanilarak SSH ile 
baglanilabilir. Yazacaginiz script/program belirli bir prefix'e sahip (Ornegin `10.202.17.***`) tum IP adreslerine 
SSH ile baglanmaya calisabilir. Yazacaginiz program SSH taramasi yapilacak IP prefix'ini, Windows admin hesabinin
sifresini, Deep Freeze sifresini ve programin paralel mi, seri mi calistirilmak istendigini parametre olarak alabilir. 
Asagida programin nasil paralel islemler yapabilecegi anlatilmaktadir.
* Deep Freeze CLI'e [https://www.faronics.com/assets/DF_RemoteAdministration.pdf](https://www.faronics.com/assets/DF_RemoteAdministration.pdf)
baglantisindaki dokumandan erisebilirsiniz. Deep Freeze'i aktive, deaktive etmek ve sistemin ne durumda (frozen veya thawed)
tespit edebilmek icin bu dokumanda belirtilen komutlar kullanilabilir.
* Komut satirindan guc ayarlarini degistirmek icin [https://winaero.com/change-power-button-action-windows-10/](https://winaero.com/change-power-button-action-windows-10/)
dokumani incelenebilir.
* Yazacaginiz script veya programin Linux sistemler uzerinden kolayca calistirilabilmesi gerekmektedir. Size verilen laboratuvar sorununu cozmek
icin bir Bash scripti yazmaniz tercih edilir ama isterseniz bu sorunu cozecek kodu sevdiginiz bir programlama dilinde de 
kodlayabilirsiniz. 
   * Nasil Bash scriptleri yazabileceginizi ogrenmek icin 
[https://ryanstutorials.net/bash-scripting-tutorial/](https://ryanstutorials.net/bash-scripting-tutorial/) baglantisindaki notlari okuyabilirsiniz.
Bash scripti yazabilmek icin Linux komut satiri hakkinda da temel duzeyde bilgi sahibi olmaniz gerekmektedir.
   * Programlama dillerinin sagladigi kutuphaneleri kullanarak da terminal komutlarini calistirabilirsiniz.
Ornegin Python'da terminal komutlarinin nasil calistirilabilecegi
[https://janakiev.com/blog/python-shell-commands/](https://janakiev.com/blog/python-shell-commands/) dokumaninda aciklanmaktadir. 
* Yazacaginiz script veya programin paralel SSH baglantilari yapmasi tercih edilmektedir. Ornegin `10.202.17.1` adresine
yapilacak olan SSH baglantisi ile `10.202.17.15` adresine yapilacak olan SSH baglantisi es zamanli olabilir. Eger bir
bilgisayardaki guc ayarlari degistirildikten sonra baska bir bilgisayara SSH baglantisi yapilirsa her bir bilgisayarda
guc ayarlarini degistirmenin 5 dakika vakit aldigi varsayilirsa programiniz labdaki tum yeni bilgisayarlarin guc
ayarlarini degistirmesi 5 * 40 = 200 dakika surebilir. SSH baglantilari paralel yapilirsa programiniz tum yeni 
bilgisayarlarin guc ayarlarini degistirmesi yaklasik 5 dakikada tamamlanabilir.
* Bir bilgisayar yeniden baslatildiginda farkli bir lokal IP adresi alabilecegini goz onunde bulundurunuz. 
Her bilgisayarin B205A1, B205C5 gibi farkli bir hostname'i vardir. Hostname bilgisi ile bilgisayarlari birbirinden ayirt etmeye belki gerek duyabilirsiniz.
* Yazdiginiz script veya programin nasil derlenebilecegini (script degilse) ve calistirilabilecegini projenizde 
yer alacak `README.md` isimli bir dosyada ayrintili bir sekilde aciklayiniz. Ayni dosyada projenize katki saglayanlarin
(kendiniz ve varsa proje grup uyelerinin) isim soyisim ve ogrenci numara bilgilerine yer veriniz.
* Mumkunse laboratuvar kosullarini Deep Freeze yuklu birkac bilgisayari ayni lokal aga baglayarak simule ederek yazdiginiz kodun
cozmesi beklenen sorunu cozup cozemedigini test ediniz.
* Her ihtimale karsi Windows bilgisayarlariniza Deep Freeze yuklemeden onemli verileriniz yedekleyiniz!

### Proje Gonderimi - Submission

* Son gonderim tarihi: `23 Ekim 2022 - 23:59`
* Proje reponuzu [https://classroom.github.com/a/tq66HZgD](https://classroom.github.com/a/tq66HZgD) 
davet linki (Github Classroom) uzerinden olusturunuz. Bu yolla olusturulacak repositoryler daha kolay izlenebilmekte
ve toplu olarak indirilebilmektedir.

## Proje No: 1 - 1023 Cocuk Process Olusturma

[Proje Dave Linki](https://classroom.github.com/a/VP9bCWRY)

* Calistirildiginda 1023 tane cocuk process (child process) olusturan bir program yaziniz.
* Ana process (ilk process) ile beraber program calistirildiginda toplam 1024 (1 + 1023) process olusturulmalidir.
* Cocuk processlerin hepsi ana processin dogrudan cocugu olacak sekilde olusturulabilir.
* Programiniz POSIX API sistemlerde (ornegin Linux) calistirilabilir olmalidir.
* Programinizi C dili kullanarak yaziniz. 
* Tum C kodunu main.c isimli bir dosya icinde yaziniz.
* Davet linkini tiklayarak repo olusturdugunuzda size bos bir main.c dosyasi verilecektir.
* Bu dosya uzerinde gerekli degisikleri yaptiktan sonra kodunuzu commit edebilirsiniz.
* Bu programi yazabilmek icin `fork` ve `wait` sistem cagrilarini kullanmaniz gerekmektedir.
* `fork` ve `wait` sistem cagrilari hakkinda detayli bilgiye `man fork` ve `man wait` komutlarini kullanarak erisebilirsiniz.
* Olusturulan cocuk processler herhangi bir is yapmak zorunda degildir.
* Yazacaginiz program 50 satirdan uzun olmasin.
* Ana process ve onun olusturacagi cocuk processlerin herhangi bir is yapmasi gerekmemektedir. 
* Dilerseniz ana process ve cocuk process icinde ekrana bir takim bilgiler (process ID gibi) yazdirabilirsiniz.
* Gonderdiginiz kodun sorunsuz derlenebildiginden emin olunuz. Derleme hatasi alacak projeler 0 puan olacaktir!
* Bu projeyi yapmak icin [https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-api.pdf](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-api.pdf)
kitap bolumunu ve [https://github.com/remzi-arpacidusseau/ostep-code/tree/master/cpu-api](https://github.com/remzi-arpacidusseau/ostep-code/tree/master/cpu-api)
adresindeki kodlari incelemeniz faydali olacaktir.

### Ornek Kod

Asagida verilen ornek kod `main.c` 7 cocuk process olusturmaktadir.

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main(int argc, char *argv[])
{
    int id1 = fork();
    int id2 = fork();
    int id3 = fork();

    printf("%d-%d-%d\n", id1, id2, id3);
    wait(&id1);
    wait(&id2);
    wait(&id3);

    exit(0);
}
```

### Derleme ve Calistirma

Bu kod terminalde `gcc -o main main.c` komutu ile derlenebilir. 
Kod derlendiginde programin ciktisi asagidaki ciktiya benzer olacaktir.
Ekrana olusturulan processlerin ID degerleri yazdirildigi icin asagidaki ciktinin birebir aynisini almayi beklemeyin.

```
773516-773517-773518
773516-773517-0
773516-0-773520
0-773519-773521
0-773519-0
0-0-773522
0-0-0
773516-0-0
```

### Strace

`strace` komutu ile calisan bir procesin cagirdigi sistem cagrilarini gorebilirsiniz. 

Ornek program icin `strace -cf ./main` komutunu calistirirsaniz asagidakine benzer bir cikti alacaksaniz:

```bash
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 43.43    0.000248          35         7           clone
 13.13    0.000075           7        10           newfstatat
 11.91    0.000068           2        24        17 wait4
  7.71    0.000044           2        17           brk
  6.48    0.000037          12         3           mprotect
  4.73    0.000027           3         8           set_robust_list
  4.20    0.000024          24         1           munmap
  3.85    0.000022           2         8           write
  1.75    0.000010           1         8           getrandom
  1.58    0.000009           9         1           rseq
  1.23    0.000007           7         1           prlimit64
  0.00    0.000000           0         1           read
  0.00    0.000000           0         2           close
  0.00    0.000000           0         8           mmap
  0.00    0.000000           0         4           pread64
  0.00    0.000000           0         1         1 access
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         2         1 arch_prctl
  0.00    0.000000           0         1           set_tid_address
  0.00    0.000000           0         2           openat
------ ----------- ----------- --------- --------- ----------------
100.00    0.000571           5       110        19 total
```

`fork` sistem cagrisi kendi icinde `clone` sistem cagrisini yapmaktadir. Dolayisiyla yukaridaki tablodan ornek programimiz
calistirildiginda toplamda 7 kez fork sistem cagrisinin yapildigi sonucuna varabiliriz. Buradan da calistirdigimiz programin
toplamda 7 cocuk process olusturdugunu soyleyebiliriz. 

Proje icin yazacaginiz kodun gercekten 1023 cocuk process olusturup olusturmadigini siz de `strace` komutu ile test edebilirsiniz.
`strace` komutunu neden `-cf` secenekleri (options) ile kullandigimizi arastiriniz. 

### Proje Gonderimi - Submission

* Son gonderim tarihi: `26 Kasim 2022 - 23:59`

