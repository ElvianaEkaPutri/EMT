# MATERI KALKULUS
Nama : Elviana Eka Putri


NIM  : 23030630094


Kelas: Matematika E 2023


# Kalkulus dengan EMT

Materi Kalkulus mencakup di antaranya:


* 
Fungsi (fungsi aljabar, trigonometri, eksponensial, logaritma,
* komposisi fungsi)

* 
Limit Fungsi,

* 
Turunan Fungsi,

* 
Integral Tak Tentu,

* 
Integral Tentu dan Aplikasinya,

* 
Barisan dan Deret (kekonvergenan barisan dan deret).


EMT (bersama Maxima) dapat digunakan untuk melakukan semua perhitungan
di dalam kalkulus, baik secara numerik maupun analitik (eksak).


## Mendefinisikan Fungsi

Terdapat beberapa cara mendefinisikan fungsi pada EMT, yakni:


* 
Menggunakan format nama_fungsi := rumus fungsi (untuk fungsi
* numerik),

* 
Menggunakan format nama_fungsi &amp;= rumus fungsi (untuk fungsi
* simbolik, namun dapat dihitung secara numerik),

* 
Menggunakan format nama_fungsi &amp;&amp;= rumus fungsi (untuk fungsi
* simbolik murni, tidak dapat dihitung langsung),

* 
Fungsi sebagai program EMT.


Setiap format harus diawali dengan perintah function (bukan sebagai
ekspresi).


Berikut adalah adalah beberapa contoh cara mendefinisikan fungsi.


\>function f(x) := 2\*x^2+exp(sin(x)) // fungsi numerik

\>f(0), f(1), f(pi)


    1
    4.31977682472
    20.7392088022

\>function g(x) := sqrt(x^2-3\*x)/(x+1)

\>g(3)


    0

\>g(0)


    0

\>g(5)


    0.527046276695

\>f(g(5)) // komposisi fungsi


    2.20920171961

\>g(f(5))


    0.950898070639

\>f(0:10) // nilai-nilai f(1), f(2), ..., f(10)


    [1,  4.31978,  10.4826,  19.1516,  32.4692,  50.3833,  72.7562,
    99.929,  130.69,  163.51,  200.58]

\>fmap(0:10) // sama dengan f(0:10), berlaku untuk semua fungsi


    [1,  4.31978,  10.4826,  19.1516,  32.4692,  50.3833,  72.7562,
    99.929,  130.69,  163.51,  200.58]

Misalkan kita akan mendefinisikan fungsi


Fungsi tersebut tidak dapat didefinisikan sebagai fungsi numerik
secara "inline" menggunakan format :=, melainkan didefinisikan sebagai
program. Perhatikan, kata "map" digunakan agar fungsi dapat menerima
vektor sebagai input, dan hasilnya berupa vektor. Jika tanpa kata
"map" fungsinya hanya dapat menerima input satu nilai.


\>function map f(x) ...


      if x>0 then return x^3
      else return x^2
      endif;
    endfunction
</pre>
\>f(1)


    1

\>f(-2)


    4

\>f(-5:5)


    [25,  16,  9,  4,  1,  0,  1,  8,  27,  64,  125]

\>aspect(1.5); plot2d("f(x)",-5,5):

\>function f(x) &= 2\*E^x // fungsi simbolik


    
                                        x
                                     2 E
    

\>function g(x) &= 3\*x+1


    
                                   3 x + 1
    

\>function h(x) &= f(g(x)) // komposisi fungsi


    
                                     3 x + 1
                                  2 E
    

# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, hitung beberapa nilainya, baik
untuk satu nilai maupun vektor. Gambar grafik tersebut.


Juga, carilah fungsi beberapa (dua) variabel. Lakukan hal sama seperti
di atas.


Jawab:


1. Fungsi 1


\>function k(x) := x\*(x^5+3)^3

\>k(3), k(5), k(7)


    44660808
    153027765760
    3.3250729687e+13

\>kmap(-3:3)


    [4.1472e+07,  48778,  -8,  0,  64,  85750,  4.46608e+07]

\>plot2d("k(x)"):


2. Fungsi 2


\>function m(x) := (x)^4/(3-x^2) 

\>m(2), m(-2), m(1)


    -16
    -16
    0.5

\>mmap(-5:-5)


    -28.4090909091

\>plot2d("m(x)"):


3. Fungsi 3


\>function n(x) := 3\*x/(x+5)+2

\>n(2), n(-1), n(-3), n(4)


    2.85714285714
    1.25
    -2.5
    3.33333333333

\>nmap(2:5)


    [2.85714,  3.125,  3.33333,  3.5]

\>plot2d("n(x)"):


4. Fungsi 4


\>function l(x) := 3\*x^3/(x^4-3)

\>l(5), l(4), l(3)


    0.602893890675
    0.758893280632
    1.03846153846

\>lmap(5:8)


    [0.602894,  0.50116,  0.429108,  0.375275]

\>plot2d("l(x)",-3,3,-600,600):


5. Fungsi 5


\>function j(x) := (cos(x))\*sin(2\*x)

\>j(pi), j(0), j(pi/3)


    0
    0
    0.433012701892

\>jmap(0:3pi)


    [0,  0.491295,  0.314941,  0.276619,  -0.646688,  -0.154318,
    -0.515201,  0.746821,  0.0418899,  0.684247]

\>plot2d("j(x)"):


6. Fungsi 6


\>function o(x) := x\*sqrt(x+2)

\>o(3), o(5), o(7)


    6.7082039325
    13.2287565553
    21

\>omap(3:12)


    [6.7082,  9.79796,  13.2288,  16.9706,  21,  25.2982,  29.8496,
    34.641,  39.6611,  44.8999]

\>plot2d("o(x)"):


1. Fungsi 1


\>function a(x,y) ...


    return x^2+y^2-24
    endfunction
</pre>
\>a(2,1), a(5,4), a(2,4)


    -19
    17
    -4

\>amap(-2:2,3:3)


    [-11,  -14,  -15,  -14,  -11]

\>aspect=1.5; plot3d("a(x,y)",a=-100,b=100,c=-80,d=80,angle=35°,height=30°,r=pi,n=100):


2. Fungsi 2


\>function q(x,y) ...


    return y^2/(x^2/3)
    endfunction
</pre>
\>q(4,2), q(2,3), q(4,3)


    0.75
    6.75
    1.6875

\>qmap(2:2,-2:2)


    [3,  0.75,  0,  0.75,  3]

\>aspect=1.5; plot3d("q(x,y)",a=-100,b=100,c=-80,d=80,angle=35°,height=30°,r=pi,n=100):


# Menghitung Limit

Perhitungan limit pada EMT dapat dilakukan dengan menggunakan fungsi
Maxima, yakni "limit". Fungsi "limit" dapat digunakan untuk menghitung
limit fungsi dalam bentuk ekspresi maupun fungsi yang sudah
didefinisikan sebelumnya. Nilai limit dapat dihitung pada sebarang
nilai atau pada tak hingga (-inf, minf, dan inf). Limit kiri dan limit
kanan juga dapat dihitung, dengan cara memberi opsi "plus" atau
"minus". Hasil limit dapat berupa nilai, "und' (tak definisi), "ind"
(tak tentu namun terbatas), "infinity" (kompleks tak hingga).


Perhatikan beberapa contoh berikut. Perhatikan cara menampilkan
perhitungan secara lengkap, tidak hanya menampilkan hasilnya saja.


\>$showev('limit(1/(2\*x-1),x,0))

\>$showev('limit((x^2-3\*x-10)/(x-5),x,5))

\>$showev('limit(sin(x)/x,x,0))

\>plot2d("sin(x)/x",-pi,pi):

\>$showev('limit(sin(x^3)/x,x,0))

\>$showev('limit(log(x), x, minf))

\>$showev('limit((-2)^x,x, inf))

\>$showev('limit(t-sqrt(2-t),t,2,minus))

\>$showev('limit(t-sqrt(2-t),t,5,plus)) // Perhatikan hasilnya

\>plot2d("x-sqrt(2-x)",-2,5):

\>$showev('limit((x^2-9)/(2\*x^2-5\*x-3),x,3))

\>$showev('limit((1-cos(x))/x,x,0))

\>$showev('limit((x^2+abs(x))/(x^2-abs(x)),x,0))

\>$showev('limit((1+1/x)^x,x,inf))

\>$showev('limit((1+k/x)^x,x,inf))

\>$showev('limit((1+x)^(1/x),x,0))

\>$showev('limit((x/(x+k))^x,x,inf))

\>$showev('limit(sin(1/x),x,0))

\>$showev('limit(sin(1/x),x,inf))

\>plot2d("sin(1/x)",-5,5):


# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, hitung nilai limit fungsi
tersebut di beberapa nilai dan di tak hingga. Gambar grafik fungsi
tersebut untuk mengkonfirmasi nilai-nilai limit tersebut.


Jawab:


1. Fungsi 1


\>$showev('limit((3\*x-6)/(x+2),x,2))

\>plot2d("(3\*x-6)/(x+2)",-2,3.5,-1,5):


2. Fungsi 2


\>$showev('limit(cos(2\*x)/(sin(x) - cos (x)),x,0))

\>plot2d("cos(2\*x)/(sin(x) - cos (x))",-1,1):


3. Fungsi 3


\>$showev('limit(((2\*x^2-2\*x+5)/(3\*x^2+x-6)),x,3))

\>plot2d("(2\*x^2-2\*x+5)/(3\*x^2+x-6)",-2,10,-10,5):


4. Fungsi 4


\>$showev('limit((4\*x^2-3),x,0))

\>plot2d("(4\*x^2-3)"):


5. Fungsi 5


\>$showev('limit((x^(x^(x))),x,0,plus))

\>plot2d("(x^(x^(x)))",-3,3,-1,7):


6. Fungsi 6


\>$showev('limit((3\*x\*tan(x))/(1-cos(4\*x)),x,0))

\>plot2d("(3\*x\*tan(x))/(1-cos(4\*x))",-pi/2,2pi,0,2pi):


# Turunan Fungsi

Definisi turunan:


Berikut adalah contoh-contoh menentukan turunan fungsi dengan
menggunakan definisi turunan (limit).


\>$showev('limit(((x+h)^2-x^2)/h,h,0)) // turunan x^2


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut benar, sehingga benar turunan fungsinya benar.  Tulis
penjelasan Anda di komentar ini.


Sebagai petunjuk, ekspansikan (x+h)^2 dengan menggunakan teorema
binomial.


Jawab:


\>$showev('limit((-sin(x)+ sin(x+h))/h,h,0)) // turunan sin(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda
di komentar ini.


Sebagai petunjuk, ekspansikan sin(x+h) dengan menggunakan rumus jumlah
dua sudut.


Jawab:


\>$showev('limit((log(x+h)-log(x))/h,h,0)) // turunan log(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda
di komentar ini.


Sebagai petunjuk, gunakan sifat-sifat logaritma dan hasil limit pada
bagian sebelumnya di atas.


Jawab:


Bukti:


\>$showev('limit((1/(x+h)-1/x)/h,h,0)) // turunan 1/x

\>$showev('limit((e^(x+h)-e^x)/h,h,0)) // turunan f(x)=e^x


    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Maxima is asking
    Acceptable answers are: yes, y, Y, no, n, N, unknown, uk
    Is x an integer?
    
    Use assume!
    Error in:
     $showev('limit((e^(x+h)-e^x)/h,h,0)) // turunan f(x)=e^x ...
                                         ^

Maxima bermasalah dengan limit:


Oleh karena itu diperlukan trik khusus agar hasilnya benar.


\>$showev('limit((E^h-1)/h,h,0))

\>$factor(E^(x+h)-E^x)

\>$showev('limit(factor((E^(x+h)-E^x)/h),h,0)) // turunan f(x)=e^x

\>function f(x) &= x^x


    
                                       x
                                      x
    

\>$showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x


Di sini Maxima juga bermasalah terkait limit:


Dalam hal ini diperlukan asumsi nilai x.


\>&assume(x\>0); $showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x

\>&forget(x\>0) // jangan lupa, lupakan asumsi untuk kembali ke semula


    
                                   [x &gt; 0]
    

\>&forget(x<0)


    
                                   [x &lt; 0]
    

\>&facts()


    
                                      []
    

\>$showev('limit((asin(x+h)-asin(x))/h,h,0)) // turunan arcsin(x)

\>$showev('limit((tan(x+h)-tan(x))/h,h,0)) // turunan tan(x)

\>function f(x) &= sinh(x) // definisikan f(x)=sinh(x)


    
                                   sinh(x)
    

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]):


# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, tentukan turunannya dengan
menggunakan definisi turunan (limit), seperti contoh-contoh tersebut.
Gambar grafik fungsi asli dan fungsi turunannya pada sumbu koordinat
yang sama.


Jawab:


1. Fungsi 1


\>function f(x) := x^2

\>$showev('limit((((x+h)^2-x^2)/h),h,0)) // turunan x^2

\>function df(x) &= limit((((x+h)^2-x^2)/h),h,0);  $df(x)// df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]), label("f(x)",2,0.6), label("df(x)",2,0.17):


2. Fungsi 2


\>function f(x) := sin(x)\*cos(x)

\>$showev('limit(((sin(x+h)\*cos(x+h))-sin(x)\*cos(x))/h,h,0)) // turunan sin(x)\*cos(x)

\>function df(x) &= limit(((sin(x+h)\*cos(x+h))-sin(x)\*cos(x))/h,h,0);  $df(x)// df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]), label("f(x)",1,0), label("df(x)",2.3,1.2):


3. Fungsi 3


\>function f(x) := sqrt(x)\*4

\>$showev('limit((sqrt(x+h)\*4-sqrt(x)\*4)/h,h,0)) // turunan sqrt(x)\*4

\>function df(x) &= limit((sqrt(x+h)\*4-sqrt(x)\*4)/h,h,0);  $df(x)// df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]), label("f(x)",-2,11), label("df(x)",-2,-10):


4. Fungsi 4


\>function f(x) := cos(1/x)

\>$showev('limit((cos(1/(x+h))-cos(1/x))/h,h,0)) // turunan cos(1/x)

\>function df(x) &= limit((cos(1/(x+h))-cos(1/x))/h,h,0);  $df(x)// df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]), label("f(x)",2,0.4), label("df(x)",1,-0.5):


5. Fungsi 5


\>function f(x) := (log(x))^5

\>$showev('limit(((log(x+h))^5-(log(x))^5)/h,h,0)) // turunan (log(x))^5

\>function df(x) &= limit(((log(x+h))^5-(log(x))^5)/h,h,0);  $df(x)// df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-50,100,-10,50,color=[blue,red]), label("f(x)",25,35), label("df(x)",50,1):


6. Fungsi 6


\>function f(x) := sqrt(tan(x))

\>$showev('limit((sqrt(tan(x+h))-sqrt(tan(x)))/h,h,0)) // turunan exp(x)\*cos(x)

\>function df(x) &= limit((sqrt(tan(x+h))-sqrt(tan(x)))/h,h,0);  $df(x)// df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-10,10,-10,10,color=[blue,red]), label("f(x)",4.5,0), label("df(x)",5.5,5):


# Integral

EMT dapat digunakan untuk menghitung integral, baik integral tak tentu
maupun integral tentu. Untuk integral tak tentu (simbolik) sudah tentu
EMT menggunakan Maxima, sedangkan untuk perhitungan integral tentu EMT
sudah menyediakan beberapa fungsi yang mengimplementasikan algoritma
kuadratur (perhitungan integral tentu menggunakan metode numerik).


Pada notebook ini akan ditunjukkan perhitungan integral tentu dengan
menggunakan Teorema Dasar Kalkulus:


Fungsi untuk menentukan integral adalah integrate. Fungsi ini dapat
digunakan untuk menentukan, baik integral tentu maupun tak tentu (jika
fungsinya memiliki antiderivatif). Untuk perhitungan integral tentu
fungsi integrate menggunakan metode numerik (kecuali fungsinya tidak
integrabel, kita tidak akan menggunakan metode ini).


\>$showev('integrate(x^n,x))


    Answering "Is n equal to -1?" with "no"

\>$showev('integrate(1/(1+x),x))

\>$showev('integrate(1/(1+x^2),x))

\>$showev('integrate(1/sqrt(1-x^2),x))

\>$showev('integrate(sin(x),x,0,pi))

\>$showev('integrate(sin(x),x,a,b))

\>$showev('integrate(x^n,x,a,b))


    Answering "Is n positive, negative or zero?" with "positive"

\>$showev('integrate(x^2\*sqrt(2\*x+1),x))

\>$showev('integrate(x^2\*sqrt(2\*x+1),x,0,2))

\>$ratsimp(%)

\>$showev('integrate((sin(sqrt(x)+a)\*E^sqrt(x))/sqrt(x),x,0,pi^2))

\>$factor(%)

\>function map f(x) &= E^(-x^2); $f(x)

\>$showev('integrate(f(x),x))


Fungsi f tidak memiliki antiturunan, integralnya masih memuat integral
lain.


Kita tidak dapat menggunakan teorema Dasar kalkulus untuk menghitung
integral tentu fungsi tersebut jika semua batasnya berhingga. Dalam
hal ini dapat digunakan metode numerik (rumus kuadratur).


Misalkan kita akan menghitung:


maxima: 'integrate(f(x),x,0,pi)


\>x=0:0.1:pi-0.1; plot2d(x,f(x+0.1),\>bar); plot2d("f(x)",0,pi,\>add):


Integral tentu


maxima: 'integrate(f(x),x,0,pi)


dapat dihampiri dengan jumlah luas persegi-persegi panjang di bawah
kurva y=f(x) tersebut. Langkah-langkahnya adalah sebagai berikut.


\>t &= makelist(a,a,0,pi-0.1,0.1); // t sebagai list untuk menyimpan nilai-nilai x

\>fx &= makelist(f(t[i]+0.1),i,1,length(t)); // simpan nilai-nilai f(x)

\>// jangan menggunakan x sebagai list, kecuali Anda pakar Maxima!


Hasilnya adalah:


maxima: 'integrate(f(x),x,0,pi) = 0.1*sum(fx[i],i,1,length(fx))


Jumlah tersebut diperoleh dari hasil kali lebar sub-subinterval (=0.1)
dan jumlah nilai-nilai f(x) untuk x = 0.1, 0.2, 0.3, ..., 3.2.


\>0.1\*sum(f(x+0.1)) // cek langsung dengan perhitungan numerik EMT


    0.836219610253

Untuk mendapatkan nilai integral tentu yang mendekati nilai sebenarnya, lebar
sub-intervalnya dapat diperkecil lagi, sehingga daerah di bawah kurva tertutup
semuanya, misalnya dapat digunakan lebar subinterval 0.001. (Silakan dicoba!)


Meskipun Maxima tidak dapat menghitung integral tentu fungsi tersebut untuk
batas-batas yang berhingga, namun integral tersebut dapat dihitung secara eksak jika
batas-batasnya tak hingga. Ini adalah salah satu keajaiban di dalam matematika, yang
terbatas tidak dapat dihitung secara eksak, namun yang tak hingga malah dapat
dihitung secara eksak.


\>$showev('integrate(f(x),x,0,inf))


Berikut adalah contoh lain fungsi yang tidak memiliki antiderivatif, sehingga
integral tentunya hanya dapat dihitung dengan metode numerik.


\>function f(x) &= x^x; $f(x)

\>$showev('integrate(f(x),x,0,1))

\>x=0:0.1:1-0.01; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,1,\>add):


Maxima gagal menghitung integral tentu tersebut secara langsung menggunakan perintah
integrate. Berikut kita lakukan seperti contoh sebelumnya untuk mendapat hasil atau
pendekatan nilai integral tentu tersebut.


\>t &= makelist(a,a,0,1-0.01,0.01);

\>fx &= makelist(f(t[i]+0.01),i,1,length(t));


# Latihan

* 
Bukalah buku Kalkulus.

* 
Cari dan pilih beberapa (paling sedikit 5 fungsi berbeda
* tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian definisikan di
* EMT pada baris-baris perintah berikut (jika perlu tambahkan lagi).

* 
Untuk setiap fungsi, tentukan anti turunannya (jika ada), hitunglah
* integral tentu dengan batas-batas yang menarik (Anda tentukan
* sendiri), seperti contoh-contoh tersebut.

* 
Lakukan hal yang sama untuk fungsi-fungsi yang tidak dapat
* diintegralkan (cari sedikitnya 3 fungsi).

* 
Gambar grafik fungsi dan daerah integrasinya pada sumbu koordinat
* yang sama.

* 
Gunakan integral tentu untuk mencari luas daerah yang dibatasi oleh
* dua kurva yang berpotongan di dua titik. (Cari dan gambar kedua kurva
* dan arsir (warnai) daerah yang dibatasi oleh keduanya.)

* 
Gunakan integral tentu untuk menghitung volume benda putar kurva y=
* f(x) yang diputar mengelilingi sumbu x dari x=a sampai x=b, yakni


(Pilih fungsinya dan gambar kurva dan benda putar yang dihasilkan.
Anda dapat mencari contoh-contoh bagaimana cara menggambar benda hasil
perputaran suatu kurva.)


- Gunakan integral tentu untuk menghitung panjang kurva y=f(x) dari
x=a sampai x=b dengan menggunakan rumus:


(Pilih fungsi dan gambar kurvanya.)


Jawab:


1. Fungsi 1


\>function f(x) &= 5\*x^2; $f(x)

\>$showev('integrate(f(x),x))

\>$showev('integrate(f(x),x,2,3))

\>x=0.01:0.03:4; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",2,3,\>add):


2. Fungsi 2


\>function f(x) &= cos(2\*x+5); $f(x)

\>$showev('integrate(f(x),x))

\>$showev('integrate(f(x),x,pi,2\*pi))

\>x=0:0.05:pi-0.1; plot2d(x,f(x+0.03),\>bar); plot2d("f(x)",pi,2\*pi,\>add):


3. Fungsi 3


\>function f(x) &= (sin(x))\*(cos((x)))^2; $f(x)

\>$showev('integrate(f(x),x))

\>$showev('integrate(f(x),x,0,pi))

\>x=-pi:0.04:pi; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,pi,\>add):


4. Fungsi 4


\>function f(x) &= (x^2\*(2-x^3)^(1/2)); $f(x)

\>$showev('integrate(f(x),x))

\>$showev('integrate(f(x),x,0,1))

\>x=-1:0.04:1; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,1,\>add):


5. Fungsi 5


\>function f(x) &= sqrt(24-x^2); $f(x)

\>$showev('integrate(f(x),x))

\>$showev('integrate(f(x),x,1,2))

\>x=-2:0.04:1; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",1,2,\>add):


6. Fungsi 6


\>t &= makelist(a,a,0,1-0.01,0.01);

\>fx &= makelist(f(t[i]+0.01),i,1,length(t));

\>function f(x) &= x^2+50; $f(x)

\>x=0:0.1:pi-0.01; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,pi,\>add):

\>0.01\*sum(f(x+0.01))


    17.051552

7. Fungsi 7


\>t &= makelist(a,a,0,1-0.01,0.01);

\>fx &= makelist(f(t[i]+0.01),i,1,length(t));

\>function f(x) &= cos(x)/x; $f(x)

\>x=-pi:0.07:pi-0.01; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,pi,\>add):

\>0.01\*sum(f(x+0.01))


    0.415163991256

8. Fungsi 8


\>t &= makelist(a,a,0,1-0.01,0.01);

\>fx &= makelist(f(t[i]+0.01),i,1,length(t));

\>function f(x) &= sqrt(x^2-1); $f(x)

\>x=3:0.04:pi-0.01; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,2,\>add):

\>0.01\*sum(f(x+0.01))


    0.11610107668

## Luas daerah dibatasi 2 kurva

1). Fungsi 1


\>function f(x) &= x^3; $f(x)

\>function g(x) &= x; $g(x)

\>plot2d(["x^4","x^3"],-2,2,-1,2):

\>function h(x) &= f(x)-g(x); $h(x)

\>$showev('integrate(h(x),x))

\>$&solve(f(x)=g(x))

\>$showev('integrate(h(x),x,0,1)) // menghitung luas daerah yang dibatasi 2 kurva


\>x=-1:0.01:1; plot2d(x,f(x),\>bar,\>filled,style="-",fillcolor=orange,\>grid); plot2d(x,g(x),\>bar,\>add,\>filled,style="-",fillcolor=white); label("f(x)",0,2.1); label("g(x)",0.5,0.3):


2). Fungsi 2


\>function f(x) &= x^3+1; $f(x)

\>function g(x) &= x^2; $g(x)

\>plot2d(["-x^2+2","x^2"],-2,2,-1,2):

\>function h(x) &= f(x)-g(x); $h(x)

\>$&solve(f(x)=g(x))

\>$showev('integrate(h(x),x,-1,1)) // menghitung luas daerah yang dibatasi 2 kurva


\>x=-1:0.01:1; plot2d(x,f(x),\>bar,\>filled,style="-",fillcolor=orange,\>grid); plot2d(x,g(x),\>bar,\>add,\>filled,style="-",fillcolor=white); label("f(x)",0,2.1); label("g(x)",0.5,0.3):


## Volume benda putar

Menghitung volume hasil perputaran kurva




dari x=-1 sampai x=0. Diputar terhadap sumbu-x.


Jawab:


\>function m(x) &= x^4+3; $m(x)

\>$showev('integrate(pi\*(m(x))^2,x,-1,0)) // Menghitung volume hasil perputaran m(x)


Daerah di bawah kurva yang akan dirotasi terhadap sumbu x sebagai
berikut:


\>plot2d("m(x)",-1,0,-1,2,grid=7,\>filled, style="/\\"): 


Hasil perputaran m(x) terhadap sumbu x sebagai berikut:


\>plot3d("m(x)",-1,0,-1,1,\>rotate,angle=6.3,\>hue,\>contour,color=redgreen,height=11):


## Menghitung panjang kurva



Menghitung panjang kurva




dari x=1 sampai x=3.


\>function d(x) &= x^2-x+1; $d(x)

\>plot2d("d(x)",-5,6): // gambar kurva d(x)

\>$showev('limit((d(x+h)-d(x))/h,h,0))

\>function dd(x) &= limit((d(x+h)-d(x))/h,h,0); $dd(x)

\>function q(x) &= ((dd(x))^2); $q(x)

\>$showev('integrate(sqrt(1+q(x)),x,1,3)) // menghitung panjang kurva


Jadi, panjang kurva




dari x=0 sampai x=4 adalah


# Barisan dan Deret

(Catatan: bagian ini belum lengkap. Anda dapat membaca contoh-contoh
pengguanaan EMT dan Maxima untuk menghitung limit barisan, rumus
jumlah parsial suatu deret, jumlah tak hingga suatu deret konvergen,
dan sebagainya. Anda dapat mengeksplor contoh-contoh di EMT atau
perbagai panduan penggunaan Maxima di software Maxima atau dari
Internet.)


Barisan dapat didefinisikan dengan beberapa cara di dalam EMT, di
antaranya:


* 
dengan cara yang sama seperti mendefinisikan vektor dengan
* elemen-elemen beraturan (menggunakan titik dua ":");

* 
menggunakan perintah "sequence" dan rumus barisan (suku ke -n);

* 
menggunakan perintah "iterate" atau "niterate";

* 
menggunakan fungsi Maxima "create_list" atau "makelist" untuk
* menghasilkan barisan simbolik;

* 
menggunakan fungsi biasa yang inputnya vektor atau barisan;

* 
menggunakan fungsi rekursif.


EMT menyediakan beberapa perintah (fungsi) terkait barisan, yakni:


* 
sum: menghitung jumlah semua elemen suatu barisan

* 
cumsum: jumlah kumulatif suatu barisan

* 
differences: selisih antar elemen-elemen berturutan


EMT juga dapat digunakan untuk menghitung jumlah deret berhingga
maupun deret tak hingga, dengan menggunakan perintah (fungsi) "sum".
Perhitungan dapat dilakukan secara numerik maupun simbolik dan eksak.


Berikut adalah beberapa contoh perhitungan barisan dan deret
menggunakan EMT.


\>1:10 // barisan sederhana


    [1,  2,  3,  4,  5,  6,  7,  8,  9,  10]

\>1:2:30


    [1,  3,  5,  7,  9,  11,  13,  15,  17,  19,  21,  23,  25,  27,  29]

\>sum(1:2:30), sum(1/(1:2:30))


    225
    2.33587263431

\>$'sum(k, k, 1, n) = factor(ev(sum(k, k, 1, n),simpsum=true)) // simpsum:menghitung deret secara simbolik

\>$'sum(1/(3^k+k), k, 0, inf) = factor(ev(sum(1/(3^k+k), k, 0, inf),simpsum=true))

\>$'sum(1/x^2, x, 1, inf)= ev(sum(1/x^2, x, 1, inf),simpsum=true) // ev: menghitung nilai ekspresi

\>$'sum((-1)^(k-1)/k, k, 1, inf) = factor(ev(sum((-1)^(x-1)/x, x, 1, inf),simpsum=true))


Di sini masih gagal, hasilnya tidak dihitung.


\>$'sum((-1)^k/(2\*k-1), k, 1, inf) = factor(ev(sum((-1)^k/(2\*k-1), k, 1, inf),simpsum=true))

\>$ev(sum(1/n!, n, 0, inf),simpsum=true)


Di sini masih gagal, hasilnya tidak dihitung, harusnya hasilnya e.


\>&assume(abs(x)<1); $'sum(a\*x^k, k, 0, inf)=ev(sum(a\*x^k, k, 0, inf),simpsum=true), &forget(abs(x)<1);


# Deret Taylor

Deret Taylor suatu fungsi f yang diferensiabel sampai tak hingga di
sekitar x=a adalah:


\>$'e^x =taylor(exp(x),x,0,10) // deret Taylor e^x di sekitar x=0, sampai suku ke-11

\>$'log(x)=taylor(log(x),x,1,10)// deret log(x) di sekitar x=1

