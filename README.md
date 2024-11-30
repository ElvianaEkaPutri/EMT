# MATERI GEOMETRI
Nama  : Elviana Eka Putri


NIM   : 23030630094


Kelas : Matematika E 2023


---

## Visualisasi dan Perhitungan Geometri dengan EMT

Euler menyediakan beberapa fungsi untuk melakukan visualisasi dan
perhitungan geometri, baik secara numerik maupun analitik (seperti
biasanya tentunya, menggunakan Maxima). Fungsi-fungsi untuk
visualisasi dan perhitungan geometeri tersebut disimpan di dalam file
program "geometry.e", sehingga file tersebut harus dipanggil sebelum
menggunakan fungsi-fungsi atau perintah-perintah untuk geometri.


\>load geometry


    Numerical and symbolic geometry.

## Fungsi-fungsi Geometri

Fungsi-fungsi untuk Menggambar Objek Geometri:


  defaultd:=textheight()*1.5: nilai asli untuk parameter d  
  setPlotrange(x1,x2,y1,y2): menentukan rentang x dan y pada bidang  

koordinat


  setPlotRange(r): pusat bidang koordinat (0,0) dan batas-batas
sumbu-x dan y adalah -r sd r


  plotPoint (P, "P"): menggambar titik P dan diberi label "P"


  plotSegment (A,B, "AB", d): menggambar ruas garis AB, diberi label
"AB" sejauh d


  plotLine (g, "g", d): menggambar garis g diberi label "g" sejauh d


  plotCircle (c,"c",v,d): Menggambar lingkaran c dan diberi label "c"


  plotLabel (label, P, V, d): menuliskan label pada posisi P


Fungsi-fungsi Geometri Analitik (numerik maupun simbolik):


  turn(v, phi): memutar vektor v sejauh phi  
  turnLeft(v):   memutar vektor v ke kiri  
  turnRight(v):  memutar vektor v ke kanan  
  normalize(v): normal vektor v  
  crossProduct(v, w): hasil kali silang vektorv dan w.  
  lineThrough(A, B): garis melalui A dan B, hasilnya [a,b,c] sdh.  

ax+by=c.


  lineWithDirection(A,v): garis melalui A searah vektor v


  getLineDirection(g): vektor arah (gradien) garis g


  getNormal(g): vektor normal (tegak lurus) garis g


  getPointOnLine(g):  titik pada garis g


  perpendicular(A, g):  garis melalui A tegak lurus garis g


  parallel (A, g):  garis melalui A sejajar garis g


  lineIntersection(g, h):  titik potong garis g dan h


  projectToLine(A, g):   proyeksi titik A pada garis g


  distance(A, B):  jarak titik A dan B


  distanceSquared(A, B):  kuadrat jarak A dan B


  quadrance(A, B): kuadrat jarak A dan B


  areaTriangle(A, B, C):  luas segitiga ABC


  computeAngle(A, B, C):   besar sudut &lt;ABC


  angleBisector(A, B, C): garis bagi sudut &lt;ABC


  circleWithCenter (A, r): lingkaran dengan pusat A dan jari-jari r


  getCircleCenter(c):  pusat lingkaran c


  getCircleRadius(c):  jari-jari lingkaran c


  circleThrough(A,B,C):  lingkaran melalui A, B, C


  middlePerpendicular(A, B): titik tengah AB


  lineCircleIntersections(g, c): titik potong garis g dan lingkran c


  circleCircleIntersections (c1, c2):  titik potong lingkaran c1 dan
c2


  planeThrough(A, B, C):  bidang melalui titik A, B, C


Fungsi-fungsi Khusus Untuk Geometri Simbolik:


  getLineEquation (g,x,y): persamaan garis g dinyatakan dalam x dan y  
  getHesseForm (g,x,y,A): bentuk Hesse garis g dinyatakan dalam x dan  

y dengan titik A pada


  sisi positif (kanan/atas) garis


  quad(A,B): kuadrat jarak AB


  spread(a,b,c): Spread segitiga dengan panjang sisi-sisi a,b,c, yakni
sin(alpha)^2 dengan


  alpha sudut yang menghadap sisi a.


  crosslaw(a,b,c,sa): persamaan 3 quads dan 1 spread pada segitiga
dengan panjang sisi a, b, c.


  triplespread(sa,sb,sc): persamaan 3 spread sa,sb,sc yang memebntuk
suatu segitiga


  doublespread(sa): Spread sudut rangkap Spread 2*phi, dengan
sa=sin(phi)^2 spread a.


## Contoh 1: Luas, Lingkaran Luar, Lingkaran Dalam Segitiga

Untuk menggambar objek-objek geometri, langkah pertama adalah
menentukan rentang sumbu-sumbu koordinat. Semua objek geometri akan
digambar pada satu bidang koordinat, sampai didefinisikan bidang
koordinat yang baru.


\>setPlotRange(-0.5,2.5,-0.5,2.5): // mendefinisikan bidang koordinat baru 


Sekarang tetapkan tiga poin dan plot mereka.


\>A=[1,0]; plotPoint(A,"A"); // definisi dan gambar tiga titik

\>B=[0,1]; plotPoint(B,"B");

\>C=[2,2]; plotPoint(C,"C");


Kemudian tiga segmen.


\>plotSegment(A,B,"c"); // c=AB

\>plotSegment(B,C,"a"); // a=BC

\>plotSegment(A,C,"b"); // b=AC


Fungsi geometri meliputi fungsi untuk membuat garis dan lingkaran.
Format garis adalah [a,b,c], yang mewakili garis dengan persamaan
ax+by=c.


\>lineThrough(B,C) // garis yang melalui B dan C


    [-1,  2,  2]

Hitunglah garis tegak lurus yang melalui A pada BC.


\>h=perpendicular(A,lineThrough(B,C)); // garis h tegak lurus BC melalui A


Dan persimpangannya dengan BC.


\>D=lineIntersection(h,lineThrough(B,C)); // D adalah titik potong h dan BC


Plot itu.


\>plotPoint(D,value=1); // koordinat D ditampilkan

\>aspect(1); plotSegment(A,D): // tampilkan semua gambar hasil plot...()


Hitung luas ABC:


\>norm(A-D)\*norm(B-C)/2 // AD=norm(A-D), BC=norm(B-C)


    1.5

Bandingkan dengan rumus determinan.


\>areaTriangle(A,B,C) // hitung luas segitiga langusng dengan fungsi


    1.5

Cara lain menghitung luas segitigas ABC:


\>distance(A,D)\*distance(B,C)/2


    1.5

Sudut di C


\>degprint(computeAngle(B,C,A))


    36°52'11.63''

Sekarang lingkaran luar segitiga.


\>c=circleThrough(A,B,C); // lingkaran luar segitiga ABC

\>R=getCircleRadius(c); // jari2 lingkaran luar 

\>O=getCircleCenter(c); // titik pusat lingkaran c 

\>plotPoint(O,"O"); // gambar titik "O"

\>plotCircle(c,"Lingkaran luar segitiga ABC"):


Tampilkan koordinat titik pusat dan jari-jari lingkaran luar.


\>O, R


    [1.16667,  1.16667]
    1.17851130198

Sekarang akan digambar lingkaran dalam segitiga ABC. Titik pusat lingkaran dalam adalah
titik potong garis-garis bagi sudut.


\>l=angleBisector(A,C,B); // garis bagi <ACB

\>g=angleBisector(C,A,B); // garis bagi <CAB

\>P=lineIntersection(l,g) // titik potong kedua garis bagi sudut


    [0.86038,  0.86038]

Tambahkan semuanya ke plot.


\>color(5); plotLine(l); plotLine(g); color(1); // gambar kedua garis bagi sudut

\>plotPoint(P,"P"); // gambar titik potongnya

\>r=norm(P-projectToLine(P,lineThrough(A,B))) // jari-jari lingkaran dalam


    0.509653732104

\>plotCircle(circleWithCenter(P,r),"Lingkaran dalam segitiga ABC"): // gambar lingkaran dalam


## Latihan

1. Tentukan ketiga titik singgung lingkaran dalam dengan sisi-sisi
segitiga ABC.


\>setPlotRange(-2.5,4.5,-2.5,4.5);

\>A=[-2,1]; plotPoint(A,"A");

\>B=[1,-2]; plotPoint(B,"B");

\>C=[4,4]; plotPoint(C,"C");

\>aspect(1):


2. Gambar segitiga dengan titik-titik sudut ketiga titik singgung
tersebut.


\>plotSegment(A,B,"c")

\>plotSegment(B,C,"a")

\>plotSegment(A,C,"b")

\>aspect(1):


4. Tunjukkan bahwa garis bagi sudut yang ke tiga juga melalui titik
pusat lingkaran dalam.


\>l=angleBisector(A,C,B);

\>g=angleBisector(C,A,B);

\>P=lineIntersection(l,g)


    [0.581139,  0.581139]

\>color(5); plotLine(l); plotLine(g); color(1);

\>plotPoint(P,"P");

\>r=norm(P-projectToLine(P,lineThrough(A,B)))


    1.52896119631

\>plotCircle(circleWithCenter(P,r),"Lingkaran dalam segitiga ABC"):


Jadi, terbukti bahwa garis bagi sudut yang ketiga juga melalui titik
pusat lingkaran dalam.


5. Gambar jari-jari lingkaran dalam.


\>r=norm(P-projectToLine(P,lineThrough(A,B)))


    1.52896119631

\>plotCircle(circleWithCenter(P,r),"Lingkaran dalam segitiga ABC"):


## Contoh 2: Geometri Simbolik

Kita dapat menghitung geometri eksak dan simbolik menggunakan Maxima.


File geometri.e menyediakan fungsi yang sama (dan lebih banyak lagi)
di Maxima. Namun, kita dapat menggunakan perhitungan simbolis
sekarang.


\>A &= [1,0]; B &= [0,1]; C &= [2,2]; // menentukan tiga titik A, B, C


Fungsi untuk garis dan lingkaran bekerja seperti fungsi Euler, tetapi
memberikan perhitungan simbolis.


\>c &= lineThrough(B,C) // c=BC


    
                                 [- 1, 2, 2]
    

Kita bisa mendapatkan persamaan garis dengan mudah.


\>$getLineEquation(c,x,y), $solve(%,y) | expand // persamaan garis c

\>$getLineEquation(lineThrough(A,[x1,y1]),x,y) // persamaan garis melalui A dan (x1, y1)

\>h &= perpendicular(A,lineThrough(B,C)) // h melalui A tegak lurus BC


    
                                  [2, 1, 2]
    

\>Q &= lineIntersection(c,h) // Q titik potong garis c=BC dan h


    
                                     2  6
                                    [-, -]
                                     5  5
    

\>$projectToLine(A,lineThrough(B,C)) // proyeksi A pada BC

\>$distance(A,Q) // jarak AQ

\>cc &= circleThrough(A,B,C); $cc // (titik pusat dan jari-jari) lingkaran melalui A, B, C

\>r&=getCircleRadius(cc); $r , $float(r) // tampilkan nilai jari-jari

\>$computeAngle(A,C,B) // nilai <ACB

\>$solve(getLineEquation(angleBisector(A,C,B),x,y),y)[1] // persamaan garis bagi <ACB

\>P &= lineIntersection(angleBisector(A,C,B),angleBisector(C,B,A)); $P // titik potong 2 garis bagi sudut

\>P() // hasilnya sama dengan perhitungan sebelumnya


    [0.86038,  0.86038]

## Garis dan Lingkaran yang Berpotongan

Tentu saja, kita juga dapat memotong garis dengan lingkaran, dan
lingkaran dengan lingkaran.


\>A &:= [1,0]; c=circleWithCenter(A,4);

\>B &:= [1,2]; C &:= [2,1]; l=lineThrough(B,C);

\>setPlotRange(5); plotCircle(c); plotLine(l);


Perpotongan garis dengan lingkaran menghasilkan dua titik dan jumlah
titik potong.


\>{P1,P2,f}=lineCircleIntersections(l,c);

\>P1, P2,


    [4.64575,  -1.64575]
    [-0.645751,  3.64575]

\>plotPoint(P1); plotPoint(P2):


Begitu pula di Maxima.


\>c &= circleWithCenter(A,4) // lingkaran dengan pusat A jari-jari 4


    
                                  [1, 0, 4]
    

\>l &= lineThrough(B,C) // garis l melalui B dan C


    
                                  [1, 1, 3]
    

\>$lineCircleIntersections(l,c) | radcan, // titik potong lingkaran c dan garis l


Akan ditunjukkan bahwa sudut-sudut yang menghadap bsuusr yang sama adalah sama besar.


\>C=A+normalize([-2,-3])\*4; plotPoint(C); plotSegment(P1,C); plotSegment(P2,C);

\>degprint(computeAngle(P1,C,P2))


    69°17'42.68''

\>C=A+normalize([-4,-3])\*4; plotPoint(C); plotSegment(P1,C); plotSegment(P2,C);

\>degprint(computeAngle(P1,C,P2))


    69°17'42.68''

\>insimg;


## Garis Sumbu

Berikut adalah langkah-langkah menggambar garis sumbu ruas garis AB:


1. Gambar lingkaran dengan pusat A melalui B.


2. Gambar lingkaran dengan pusat B melalui A.


3. Tarik garis melallui kedua titik potong kedua lingkaran tersebut. Garis ini merupakan
garis sumbu (melalui titik tengah dan tegak lurus) AB.


\>A=[2,2]; B=[-1,-2];

\>c1=circleWithCenter(A,distance(A,B));

\>c2=circleWithCenter(B,distance(A,B));

\>{P1,P2,f}=circleCircleIntersections(c1,c2);

\>l=lineThrough(P1,P2);

\>setPlotRange(5); plotCircle(c1); plotCircle(c2);

\>plotPoint(A); plotPoint(B); plotSegment(A,B); plotLine(l):


Selanjutnya, kami melakukan hal yang sama di Maxima dengan koordinat
umum.


\>A &= [a1,a2]; B &= [b1,b2];

\>c1 &= circleWithCenter(A,distance(A,B));

\>c2 &= circleWithCenter(B,distance(A,B));

\>P &= circleCircleIntersections(c1,c2); P1 &= P[1]; P2 &= P[2];


Persamaan untuk persimpangan cukup terlibat. Tetapi kita dapat
menyederhanakannya, jika kita memecahkan y.


\>g &= getLineEquation(lineThrough(P1,P2),x,y);

\>$solve(g,y)


Ini memang sama dengan tegak lurus tengah, yang dihitung dengan cara
yang sama sekali berbeda.


\>$solve(getLineEquation(middlePerpendicular(A,B),x,y),y)

\>h &=getLineEquation(lineThrough(A,B),x,y);

\>$solve(h,y)


Perhatikan hasil kali gradien garis g dan h adalah:


Artinya kedua garis tegak lurus.


## Contoh 3: Rumus Heron

Rumus Heron menyatakan bahwa luas segitiga dengan panjang sisi-sisi a,
b dan c adalah:


Untuk membuktikan hal ini kita misalkan C(0,0), B(a,0) dan A(x,y),
b=AC, c=AB. Luas segitiga ABC adalah


Nilai y didapat dengan menyelesaikan sistem persamaan:


\>sol &= solve([x^2+y^2 = b^2,(x-a)^2+y^2=c^2],[x,y]):

\>setPlotRange(-1,10,-1,8); plotPoint([0,0], "C(0,0)"); plotPoint([5.5,0], "B(a,0)");  ...  
\>   plotPoint([7.5,6], "A(x,y)");

\>plotSegment([0,0],[5.5,0], "a",25); plotSegment([5.5,0],[7.5,6],"c",15);  ...  
\>   plotSegment([0,0],[7.5,6],"b",25); 

\>plotSegment([7.5,6],[7.5,0],"t=y",25):

\>sol &= solve([x^2+y^2=b^2,(x-a)^2+y^2=c^2],[x,y]):


Ekstrak solusi y.


\>ysol &= y with sol[2][2] $ysol:


Kami mendapatkan rumus Heron.


\>function H(a,b,c) &= sqrt(factor((ysol\*a/2)^2)); $'H(a,b,c)=H(a,b,c)

\>$'Luas=H(3,4,5) // luas segitiga dengan panjang sisi-sisi 3, 4, 5


Dan buat fungsi ini.


\>function fx(a,c,d) &= rhs(s1[1]); $fx(a,c,d), function fy(a,c,d) &= rhs(s1[2]); $fy(a,c,d)


Sekarang kita bisa menggambar setnya. Sisi b bervariasi dari 1 hingga
4. Diketahui bahwa kita mendapatkan elips.


\>aspect(1); plot2d(&fx(3,x,5),&fy(3,x,5),xmin=1,xmax=4,square=1):


Kita dapat memeriksa persamaan umum untuk elips ini, yaitu.


di mana (xm,ym) adalah pusat, dan u dan v adalah setengah sumbu.


\>$ratsimp((fx(a,c,d)-a/2)^2/u^2+fy(a,c,d)^2/v^2 with [u=d/2,v=sqrt(d^2-a^2)/2])


Kita lihat bahwa tinggi dan luas segitiga adalah maksimal untuk x=0.
Jadi luas segitiga dengan a+b+c=d maksimal jika segitiga sama sisi.
Kami ingin menurunkan ini secara analitis.


\>eqns &= [diff(H(a,b,d-(a+b))^2,a)=0,diff(H(a,b,d-(a+b))^2,b)=0]; $eqns


Kami mendapatkan beberapa minima, yang termasuk dalam segitiga dengan
satu sisi 0, dan solusinya a=b=c=d/3.


\>$solve(eqns,[a,b])


\>B &= [0,0]; $B, C &= [a,0]; $C


Hitung tegak lurus tengah di Maxima.


\>h &= middlePerpendicular(A,B); g &= middlePerpendicular(B,C);


Dan pusat lingkaran.


\>U &= lineIntersection(h,g);


Kami mendapatkan rumus untuk jari-jari lingkaran.


\>&assume(a\>0,b\>0,c\>0); $distance(U,B) | radcan


Menggunakan geometri, kami memperoleh rumus sederhana


untuk radiusnya. Kami dapat memeriksa, apakah ini benar dengan Maxima.
Maxima akan memfaktorkan ini hanya jika kita kuadratkan.


\>$c^2/sin(computeAngle(A,B,C))^2  | factor


## Contoh 4: Garis Euler dan Parabola

Garis Euler adalah garis yang ditentukan dari sembarang segitiga yang
tidak sama sisi. Ini adalah garis tengah segitiga, dan melewati
beberapa titik penting yang ditentukan dari segitiga, termasuk
orthocenter, circumcenter, centroid, titik Exeter dan pusat lingkaran
sembilan titik segitiga.


Untuk demonstrasi, kami menghitung dan memplot garis Euler dalam
sebuah segitiga.


Pertama, kita mendefinisikan sudut-sudut segitiga di Euler. Kami
menggunakan definisi, yang terlihat dalam ekspresi simbolis.


\>A::=[-1,-1]; B::=[2,0]; C::=[1,2];


Untuk memplot objek geometris, kami menyiapkan area plot, dan
menambahkan titik ke sana. Semua plot objek geometris ditambahkan ke
plot saat ini.


\>setPlotRange(3); plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C");


Kita juga bisa menambahkan sisi segitiga.


\>plotSegment(A,B,""); plotSegment(B,C,""); plotSegment(C,A,""):


Berikut adalah luas segitiga, menggunakan rumus determinan. Tentu
saja, kita harus mengambil nilai absolut dari hasil ini.


\>$areaTriangle(A,B,C)


Kita dapat menghitung koefisien sisi c.


\>c &= lineThrough(A,B)


    
                                [- 1, 3, - 2]
    

Dan juga dapatkan rumus untuk baris ini.


\>$getLineEquation(c,x,y)


Untuk bentuk Hesse, kita perlu menentukan sebuah titik, sehingga titik
tersebut berada di sisi positif dari bentuk Hesse. Memasukkan titik
menghasilkan jarak positif ke garis.


\>$getHesseForm(c,x,y,C), $at(%,[x=C[1],y=C[2]])


Sekarang kita hitung lingkaran luar ABC.


\>LL &= circleThrough(A,B,C); $getCircleEquation(LL,x,y)

\>O &= getCircleCenter(LL); $O


Gambarkan lingkaran dan pusatnya. Cu dan U adalah simbolis. Kami
mengevaluasi ekspresi ini untuk Euler.


\>plotCircle(LL()); plotPoint(O(),"O"):


Kita dapat menghitung perpotongan ketinggian di ABC (orthocenter)
secara numerik dengan perintah berikut.


\>H &= lineIntersection(perpendicular(A,lineThrough(C,B)),...  
\>     perpendicular(B,lineThrough(A,C))); $H


Sekarang kita dapat menghitung garis Euler dari segitiga.


\>el &= lineThrough(H,O); $getLineEquation(el,x,y)


Tambahkan ke plot kami.


\>plotPoint(H(),"H"); plotLine(el(),"Garis Euler"):


Pusat gravitasi harus berada di garis ini.


\>M &= (A+B+C)/3; $getLineEquation(el,x,y) with [x=M[1],y=M[2]]

\>plotPoint(M(),"M"): // titik berat


Teorinya memberitahu kita MH=2*MO. Kita perlu menyederhanakan dengan
radcan untuk mencapai ini.


\>$distance(M,H)/distance(M,O)|radcan


Fungsi termasuk fungsi untuk sudut juga.


\>$computeAngle(A,C,B), degprint(%())


    60°15'18.43''

Persamaan untuk pusat incircle tidak terlalu bagus.


\>Q &= lineIntersection(angleBisector(A,C,B),angleBisector(C,B,A))|radcan; $Q


Mari kita hitung juga ekspresi untuk jari-jari lingkaran yang
tertulis.


\>r &= distance(Q,projectToLine(Q,lineThrough(A,B)))|ratsimp; $r

\>LD &=  circleWithCenter(Q,r); // Lingkaran dalam


Mari kita tambahkan ini ke plot.


\>color(5); plotCircle(LD()):


## Parabola

Selanjutnya akan dicari persamaan tempat kedudukan titik-titik yang berjarak sama ke titik C
dan ke garis AB.


\>p &= getHesseForm(lineThrough(A,B),x,y,C)-distance([x,y],C); $p='0


Persamaan tersebut dapat digambar menjadi satu dengan gambar sebelumnya.


\>plot2d(p,level=0,add=1,contourcolor=6):


Ini seharusnya menjadi beberapa fungsi, tetapi pemecah default Maxima
hanya dapat menemukan solusinya, jika kita kuadratkan persamaannya.
Akibatnya, kami mendapatkan solusi palsu.


\>akar &= solve(getHesseForm(lineThrough(A,B),x,y,C)^2-distance([x,y],C)^2,y)


    
            [y = - 3 x - sqrt(70) sqrt(9 - 2 x) + 26, 
                                  y = - 3 x + sqrt(70) sqrt(9 - 2 x) + 26]
    

Solusi pertama adalah


maxima: akar[1]


Menambahkan solusi pertama ke plot menunjukkan, bahwa itu memang jalan
yang kita cari. Teorinya memberi tahu kita bahwa itu adalah parabola
yang diputar.


\>plot2d(&rhs(akar[1]),add=1):

\>function g(x) &= rhs(akar[1]); $'g(x)= g(x)// fungsi yang mendefinisikan kurva di atas

\>T &=[-1, g(-1)]; // ambil sebarang titik pada kurva tersebut

\>dTC &= distance(T,C); $fullratsimp(dTC), $float(%) // jarak T ke C

\>U &= projectToLine(T,lineThrough(A,B)); $U // proyeksi T pada garis AB 

\>dU2AB &= distance(T,U); $fullratsimp(dU2AB), $float(%) // jatak T ke AB


Ternyata jarak T ke C sama dengan jarak T ke AB. Coba Anda pilih titik T yang lain dan
ulangi perhitungan-perhitungan di atas untuk menunjukkan bahwa hasilnya juga sama.


## Contoh 5: Trigonometri Rasional

Ini terinspirasi dari ceramah N.J.Wildberger. Dalam bukunya "Divine
Proportions", Wildberger mengusulkan untuk mengganti pengertian klasik
tentang jarak dan sudut dengan kuadrat dan penyebaran. Dengan
menggunakan ini, memang mungkin untuk menghindari fungsi trigonometri
dalam banyak contoh, dan tetap "rasional".


Berikut ini, saya memperkenalkan konsep, dan memecahkan beberapa
masalah. Saya menggunakan perhitungan simbolik Maxima di sini, yang
menyembunyikan keuntungan utama dari trigonometri rasional bahwa
perhitungan hanya dapat dilakukan dengan kertas dan pensil. Anda
diundang untuk memeriksa hasil tanpa komputer.


Intinya adalah bahwa perhitungan rasional simbolis sering kali
menghasilkan hasil yang sederhana. Sebaliknya, trigonometri klasik
menghasilkan hasil trigonometri yang rumit, yang hanya mengevaluasi
perkiraan numerik.


\>load geometry;


Untuk pengenalan pertama, kami menggunakan segitiga persegi panjang
dengan proporsi Mesir terkenal 3, 4 dan 5. Perintah berikut adalah
perintah Euler untuk merencanakan geometri bidang yang terdapat dalam
file Euler "geometry.e".


\>C&:=[0,0]; A&:=[4,0]; B&:=[0,3]; ...  
\>   setPlotRange(-1,5,-1,5); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   plotSegment(B,A,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   insimg(30);


Tentu saja,


di mana wa adalah sudut di A. Cara yang biasa untuk menghitung sudut
ini, adalah dengan mengambil invers dari fungsi sinus. Hasilnya adalah
sudut yang tidak dapat dicerna, yang hanya dapat dicetak kira-kira.


\>wa := arcsin(3/5); degprint(wa)


    36°52'11.63''

Trigonometri rasional mencoba menghindari hal ini.


Gagasan pertama trigonometri rasional adalah kuadran, yang
menggantikan jarak. Sebenarnya, itu hanya jarak kuadrat. Berikut ini,
a, b, dan c menunjukkan kuadrat dari sisi-sisinya.


Teorema Pythogoras menjadi a+b=c.


\>a &= 3^2; b &= 4^2; c &= 5^2; &a+b=c


    
                                   25 = 25
    

Pengertian kedua dari trigonometri rasional adalah penyebaran. Spread
mengukur pembukaan antar baris. Ini adalah 0, jika garis-garisnya
sejajar, dan 1, jika garis-garisnya persegi panjang. Ini adalah
kuadrat sinus sudut antara dua garis.


Penyebaran garis AB dan AC pada gambar di atas didefinisikan sebagai:


di mana a dan c adalah kuadrat dari sembarang segitiga siku-siku
dengan salah satu sudut di A.


\>sa &= a/c; $sa


Ini lebih mudah dihitung daripada sudut, tentu saja. Tetapi Anda
kehilangan properti bahwa sudut dapat ditambahkan dengan mudah.


Tentu saja, kita dapat mengonversi nilai perkiraan untuk sudut wa
menjadi sprad, dan mencetaknya sebagai pecahan.


\>fracprint(sin(wa)^2)


    9/25

Hukum kosinus trgonometri klasik diterjemahkan menjadi "hukum silang"
berikut.


Di sini a, b, dan c adalah kuadrat dari sisi-sisi segitiga, dan sa
adalah penyebaran sudut A. Sisi a, seperti biasa, berhadapan dengan
sudut A.


Hukum ini diimplementasikan dalam file geometri.e yang kami muat ke
Euler.


\>$crosslaw(aa,bb,cc,saa)


Dalam kasus kami, kami mendapatkan


\>$crosslaw(a,b,c,sa)


Mari kita gunakan crosslaw ini untuk mencari spread di A. Untuk
melakukan ini, kita buat crosslaw untuk kuadran a, b, dan c, dan
selesaikan untuk spread yang tidak diketahui sa.


Anda dapat melakukannya dengan tangan dengan mudah, tetapi saya
menggunakan Maxima. Tentu saja, kami mendapatkan hasilnya, kami sudah
memilikinya.


\>$crosslaw(a,b,c,x), $solve(%,x)


Kita sudah tahu ini. Definisi spread adalah kasus khusus dari
crosslaw.


Kita juga dapat menyelesaikan ini untuk umum a,b,c. Hasilnya adalah
rumus yang menghitung penyebaran sudut segitiga yang diberikan kuadrat
dari ketiga sisinya.


\>$solve(crosslaw(aa,bb,cc,x),x)


Kita bisa membuat fungsi dari hasilnya. Fungsi seperti itu sudah
didefinisikan dalam file geometri.e dari Euler.


\>$spread(a,b,c)


Sebagai contoh, kita dapat menggunakannya untuk menghitung sudut
segitiga dengan sisi


Hasilnya rasional, yang tidak begitu mudah didapat jika kita
menggunakan trigonometri klasik.


\>$spread(a,a,4\*a/7)


Ini adalah sudut dalam derajat.


\>degprint(arcsin(sqrt(6/7)))


    67°47'32.44''

## Contoh lain

Sekarang, mari kita coba contoh yang lebih maju.


Kami mengatur tiga sudut segitiga sebagai berikut.


\>A&:=[1,2]; B&:=[4,3]; C&:=[0,4]; ...  
\>   setPlotRange(-1,5,1,7); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   plotSegment(B,A,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   insimg;


Menggunakan Pythogoras, mudah untuk menghitung jarak antara dua titik.
Saya pertama kali menggunakan jarak fungsi file Euler untuk geometri.
Jarak fungsi menggunakan geometri klasik.


\>$distance(A,B)


Euler juga mengandung fungsi untuk kuadran antara dua titik.


Dalam contoh berikut, karena c+b bukan a, maka segitiga itu bukan
persegi panjang.


\>c &= quad(A,B); $c, b &= quad(A,C); $b, a &= quad(B,C); $a,


Pertama, mari kita hitung sudut tradisional. Fungsi computeAngle
menggunakan metode biasa berdasarkan hasil kali titik dua vektor.
Hasilnya adalah beberapa pendekatan floating point.


\>wb &= computeAngle(A,B,C); $wb, $(wb/pi\*180)()


    32.4711922908

Dengan menggunakan pensil dan kertas, kita dapat melakukan hal yang
sama dengan hukum silang. Kami memasukkan kuadran a, b, dan c ke dalam
hukum silang dan menyelesaikan x.


\>$crosslaw(a,b,c,x), $solve(%,x), //(b+c-a)^=4b.c(1-x)


Yaitu, apa yang dilakukan oleh penyebaran fungsi yang didefinisikan
dalam "geometry.e".


\>sb &= spread(b,a,c); $sb


Maxima mendapatkan hasil yang sama menggunakan trigonometri biasa,
jika kita memaksanya. Itu menyelesaikan istilah sin(arccos(...))
menjadi hasil pecahan. Sebagian besar siswa tidak dapat melakukan ini.


\>$sin(computeAngle(A,B,C))^2


Setelah kita memiliki spread di B, kita dapat menghitung tinggi ha di
sisi a. Ingat bahwa


Menurut definisi.


\>ha &= c\*sb; $ha


Menurut definisi, panjang ha adalah akar kuadrat dari kuadratnya.


\>$sqrt(ha)


Sekarang kita dapat menghitung luas segitiga. Jangan lupa, bahwa kita
berhadapan dengan kuadrat!


\>$sqrt(ha)\*sqrt(a)/2


Rumus determinan biasa menghasilkan hasil yang sama.


\>$areaTriangle(B,A,C)


## Rumus Bangau

Sekarang, mari kita selesaikan masalah ini secara umum!


\>&remvalue(a,b,c,sb,ha);


Pertama kita hitung spread di B untuk segitiga dengan sisi a, b, dan
c. Kemudian kita menghitung luas kuadrat ("quadrea"?), faktorkan
dengan Maxima, dan kita mendapatkan rumus Heron yang terkenal.


Memang, ini sulit dilakukan dengan pensil dan kertas.


\>$spread(b^2,c^2,a^2), $factor(%\*c^2\*a^2/4)


## Aturan Triple Spread

Kerugian dari spread adalah mereka tidak lagi hanya menambahkan sudut
yang sama.


Namun, tiga spread dari sebuah segitiga memenuhi aturan "triple
spread" berikut.


\>&remvalue(sa,sb,sc); $triplespread(sa,sb,sc)


Aturan ini berlaku untuk setiap tiga sudut yang menambah 180 °.


Sejak menyebar


sama, aturan triple spread juga benar, jika


Karena penyebaran sudut negatif adalah sama, aturan penyebaran rangkap
tiga juga berlaku, jika


Misalnya, kita dapat menghitung penyebaran sudut 60°. Ini 3/4.
Persamaan memiliki solusi kedua, bagaimanapun, di mana semua spread
adalah 0.


\>$solve(triplespread(x,x,x),x)


Sebaran 90° jelas 1. Jika dua sudut dijumlahkan menjadi 90°,
sebarannya menyelesaikan persamaan sebaran rangkap tiga dengan a,b,1.
Dengan perhitungan berikut kita mendapatkan a+b=1.


\>$triplespread(x,y,1), $solve(%,x)


Karena sebaran 180°-t sama dengan sebaran t, rumus sebaran rangkap
tiga juga berlaku, jika satu sudut adalah jumlah atau selisih dua
sudut lainnya.


Jadi kita dapat menemukan penyebaran sudut berlipat ganda. Perhatikan
bahwa ada dua solusi lagi. Kami membuat ini fungsi.


\>$solve(triplespread(a,a,x),x), function doublespread(a) &= factor(rhs(%[1]))


    
                                - 4 (a - 1) a
    

## Pembagi Sudut

Ini situasinya, kita sudah tahu.


\>C&:=[0,0]; A&:=[4,0]; B&:=[0,3]; ...  
\>   setPlotRange(-1,5,-1,5); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   plotSegment(B,A,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   insimg;


Mari kita hitung panjang garis bagi sudut di A. Tetapi kita ingin
menyelesaikannya untuk umum a,b,c.


\>&remvalue(a,b,c);


Jadi pertama-tama kita hitung penyebaran sudut yang dibagi dua di A,
dengan menggunakan rumus sebaran rangkap tiga.


Masalah dengan rumus ini muncul lagi. Ini memiliki dua solusi. Kita
harus memilih yang benar. Solusi lainnya mengacu pada sudut terbelah
180 °-wa.


\>$triplespread(x,x,a/(a+b)), $solve(%,x), sa2 &= rhs(%[1]); $sa2


Mari kita periksa persegi panjang Mesir.


\>$sa2 with [a=3^2,b=4^2]


Kami dapat mencetak sudut dalam Euler, setelah mentransfer penyebaran
ke radian.


\>wa2 := arcsin(sqrt(1/10)); degprint(wa2)


    18°26'5.82''

Titik P adalah perpotongan garis bagi sudut dengan sumbu y.


\>P := [0,tan(wa2)\*4]


    [0,  1.33333]

\>plotPoint(P,"P"); plotSegment(A,P):


Mari kita periksa sudut dalam contoh spesifik kita.


\>computeAngle(C,A,P), computeAngle(P,A,B)


    0.321750554397
    0.321750554397

Sekarang kita hitung panjang garis bagi AP.


Kami menggunakan teorema sinus dalam segitiga APC. Teorema ini
menyatakan bahwa


berlaku dalam segitiga apa pun. Kuadratkan, itu diterjemahkan ke dalam
apa yang disebut "hukum penyebaran"


di mana a,b,c menunjukkan qudrances.


Karena spread CPA adalah 1-sa2, kita dapatkan darinya bisa/1=b/(1-sa2)
dan dapat menghitung bisa (kuadran dari garis-bagi sudut).


\>&factor(ratsimp(b/(1-sa2))); bisa &= %; $bisa


Mari kita periksa rumus ini untuk nilai-nilai Mesir kita.


\>sqrt(mxmeval("at(bisa,[a=3^2,b=4^2])")), distance(A,P)


    4.21637021356
    4.21637021356

Kita juga dapat menghitung P menggunakan rumus spread.


\>py&=factor(ratsimp(sa2\*bisa)); $py


Nilainya sama dengan yang kita dapatkan dengan rumus trigonometri.


\>sqrt(mxmeval("at(py,[a=3^2,b=4^2])"))


    1.33333333333

## Sudut Akord

Perhatikan situasi berikut.


\>setPlotRange(1.2); ...  
\>   color(1); plotCircle(circleWithCenter([0,0],1)); ...  
\>   A:=[cos(1),sin(1)]; B:=[cos(2),sin(2)]; C:=[cos(6),sin(6)]; ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   color(3); plotSegment(A,B,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   color(1); O:=[0,0];  plotPoint(O,"0"); ...  
\>   plotSegment(A,O); plotSegment(B,O); plotSegment(C,O,"r"); ...  
\>   insimg;


Kita dapat menggunakan Maxima untuk menyelesaikan rumus penyebaran
rangkap tiga untuk sudut-sudut di pusat O untuk r. Jadi kita
mendapatkan rumus untuk jari-jari kuadrat dari pericircle dalam hal
kuadrat dari sisi.


Kali ini, Maxima menghasilkan beberapa nol kompleks, yang kita
abaikan.


\>&remvalue(a,b,c,r); // hapus nilai-nilai sebelumnya untuk perhitungan baru

\>rabc &= rhs(solve(triplespread(spread(b,r,r),spread(a,r,r),spread(c,r,r)),r)[4]); $rabc


Kita dapat menjadikannya sebagai fungsi Euler.


\>function periradius(a,b,c) &= rabc;


Mari kita periksa hasilnya untuk poin A,B,C.


\>a:=quadrance(B,C); b:=quadrance(A,C); c:=quadrance(A,B);


Jari-jarinya memang 1.


\>periradius(a,b,c)


    1

Faktanya, spread CBA hanya bergantung pada b dan c. Ini adalah teorema
sudut chord.


\>$spread(b,a,c)\*rabc | ratsimp


Sebenarnya spreadnya adalah b/(4r), dan kita melihat bahwa sudut chord
dari chord b adalah setengah dari sudut pusat.


\>$doublespread(b/(4\*r))-spread(b,r,r) | ratsimp


## Contoh 6: Jarak Minimal pada Bidang

## Catatan awal

Fungsi yang, ke titik M di bidang, menetapkan jarak AM antara titik
tetap A dan M, memiliki garis level yang agak sederhana: lingkaran
berpusat di A.


\>&remvalue();

\>A=[-1,-1];

\>function d1(x,y):=sqrt((x-A[1])^2+(y-A[2])^2)

\>fcontour("d1",xmin=-2,xmax=0,ymin=-2,ymax=0,hue=1, ...  
\>   title="If you see ellipses, please set your window square"):


dan grafiknya juga agak sederhana: bagian atas kerucut:


\>plot3d("d1",xmin=-2,xmax=0,ymin=-2,ymax=0):


Tentu saja minimal 0 dicapai di A.


## Dua poin

Sekarang kita lihat fungsi MA+MB dimana A dan B adalah dua titik
(tetap). Ini adalah "fakta yang diketahui" bahwa kurva level adalah
elips, titik fokusnya adalah A dan B; kecuali untuk AB minimum yang
konstan pada segmen [AB]:


\>B=[1,-1];

\>function d2(x,y):=d1(x,y)+sqrt((x-B[1])^2+(y-B[2])^2)

\>fcontour("d2",xmin=-2,xmax=2,ymin=-3,ymax=1,hue=1):


Grafiknya lebih menarik:


\>plot3d("d2",xmin=-2,xmax=2,ymin=-3,ymax=1):


Pembatasan garis (AB) lebih terkenal:


\>plot2d("abs(x+1)+abs(x-1)",xmin=-3,xmax=3):


## Tiga poin

Sekarang hal-hal yang kurang sederhana: Ini sedikit kurang terkenal
bahwa MA+MB+MC mencapai minimum pada satu titik pesawat tetapi untuk
menentukan itu kurang sederhana:


1) Jika salah satu sudut segitiga ABC lebih dari 120° (katakanlah di
A), maka minimum dicapai pada titik ini (misalnya AB+AC).


Contoh:


\>C=[-4,1];

\>function d3(x,y):=d2(x,y)+sqrt((x-C[1])^2+(y-C[2])^2)

\>plot3d("d3",xmin=-5,xmax=3,ymin=-4,ymax=4);

\>insimg;

\>fcontour("d3",xmin=-4,xmax=1,ymin=-2,ymax=2,hue=1,title="The minimum is on A");

\>P=(A\_B\_C\_A)'; plot2d(P[1],P[2],add=1,color=12);

\>insimg;


2) Tetapi jika semua sudut segitiga ABC kurang dari 120 °, minimumnya
adalah pada titik F di bagian dalam segitiga, yang merupakan
satu-satunya titik yang melihat sisi-sisi ABC dengan sudut yang sama
(maka masing-masing 120 ° ):


\>C=[-0.5,1];

\>plot3d("d3",xmin=-2,xmax=2,ymin=-2,ymax=2):

\>fcontour("d3",xmin=-2,xmax=2,ymin=-2,ymax=2,hue=1,title="The Fermat point");

\>P=(A\_B\_C\_A)'; plot2d(P[1],P[2],add=1,color=12);

\>insimg;


Merupakan kegiatan yang menarik untuk mewujudkan gambar di atas dengan
perangkat lunak geometri; misalnya, saya tahu soft yang ditulis di
Jawa yang memiliki instruksi "garis kontur" ...


Semua ini di atas telah ditemukan oleh seorang hakim Perancis bernama
Pierre de Fermat; dia menulis surat kepada dilettants lain seperti
pendeta Marin Mersenne dan Blaise Pascal yang bekerja di pajak
penghasilan. Jadi titik unik F sedemikian rupa sehingga FA+FB+FC
minimal, disebut titik Fermat segitiga. Tetapi tampaknya beberapa
tahun sebelumnya, Torriccelli Italia telah menemukan titik ini sebelum
Fermat melakukannya! Bagaimanapun tradisinya adalah mencatat poin ini
F...


## Empat poin

Langkah selanjutnya adalah menambahkan 4 titik D dan mencoba
meminimalkan MA+MB+MC+MD; katakan bahwa Anda adalah operator TV kabel
dan ingin mencari di bidang mana Anda harus meletakkan antena sehingga
Anda dapat memberi makan empat desa dan menggunakan panjang kabel
sesedikit mungkin!


\>D=[1,1];

\>function d4(x,y):=d3(x,y)+sqrt((x-D[1])^2+(y-D[2])^2)

\>plot3d("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5):

\>fcontour("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5,hue=1);

\>P=(A\_B\_C\_D)'; plot2d(P[1],P[2],points=1,add=1,color=12);

\>insimg;


Masih ada minimum dan tidak tercapai di salah satu simpul A, B, C atau
D:


\>function f(x):=d4(x[1],x[2])

\>neldermin("f",[0.2,0.2])


    [0.142858,  0.142857]

Tampaknya dalam kasus ini, koordinat titik optimal adalah rasional
atau mendekati rasional...


Sekarang ABCD adalah persegi, kami berharap bahwa titik optimal akan
menjadi pusat ABCD:


\>C=[-1,1];

\>plot3d("d4",xmin=-1,xmax=1,ymin=-1,ymax=1):

\>fcontour("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5,hue=1);

\>P=(A\_B\_C\_D)'; plot2d(P[1],P[2],add=1,color=12,points=1);

\>insimg;


## Contoh 7: Bola Dandelin dengan Povray

Anda dapat menjalankan demonstrasi ini, jika Anda telah menginstal
Povray, dan pvengine.exe di jalur program.


Pertama kita hitung jari-jari bola.


Jika Anda melihat gambar di bawah, Anda melihat bahwa kita membutuhkan
dua lingkaran yang menyentuh dua garis yang membentuk kerucut, dan
satu garis yang membentuk bidang yang memotong kerucut.


Kami menggunakan file geometri.e dari Euler untuk ini.


\>load geometry;


Pertama dua garis yang membentuk kerucut.


\>g1 &= lineThrough([0,0],[1,a])


    
                                 [- a, 1, 0]
    

\>g2 &= lineThrough([0,0],[-1,a])


    
                                [- a, - 1, 0]
    

Kemudian saya baris ketiga.


\>g &= lineThrough([-1,0],[1,1])


    
                                 [- 1, 2, 1]
    

Kami merencanakan semuanya sejauh ini.


\>setPlotRange(-1,1,0,2);

\>color(black); plotLine(g(),"")

\>a:=2; color(blue); plotLine(g1(),""), plotLine(g2(),""):


Sekarang kita ambil titik umum pada sumbu y.


\>P &= [0,u]


    
                                    [0, u]
    

Hitung jarak ke g1.


\>d1 &= distance(P,projectToLine(P,g1)); $d1


Hitung jarak ke g.


\>d &= distance(P,projectToLine(P,g)); $d


Dan temukan pusat kedua lingkaran yang jaraknya sama.


\>sol &= solve(d1^2=d^2,u); $sol


Ada dua solusi.


Kami mengevaluasi solusi simbolis, dan menemukan kedua pusat, dan
kedua jarak.


\>u := sol()


    [0.333333,  1]

\>dd := d()


    [0.149071,  0.447214]

Plot lingkaran ke dalam gambar.


\>color(red);

\>plotCircle(circleWithCenter([0,u[1]],dd[1]),"");

\>plotCircle(circleWithCenter([0,u[2]],dd[2]),"");

\>insimg;


## Plot dengan Povray

Selanjutnya kami merencanakan semuanya dengan Povray. Perhatikan bahwa
Anda mengubah perintah apa pun dalam urutan perintah Povray berikut,
dan menjalankan kembali semua perintah dengan Shift-Return.


Pertama kita memuat fungsi povray.


\>load povray;

\>defaultpovray="C:\\Program Files\\POV-Ray\\v3.7\\bin\\pvengine.exe"


    C:\Program Files\POV-Ray\v3.7\bin\pvengine.exe

Kami mengatur adegan dengan tepat.


\>povstart(zoom=11,center=[0,0,0.5],height=10°,angle=140°);


Selanjutnya kita menulis dua bidang ke file Povray.


\>writeln(povsphere([0,0,u[1]],dd[1],povlook(red)));

\>writeln(povsphere([0,0,u[2]],dd[2],povlook(red)));


Dan kerucutnya, transparan.


\>writeln(povcone([0,0,0],0,[0,0,a],1,povlook(lightgray,1)));


Kami menghasilkan bidang terbatas pada kerucut.


\>gp=g();

\>pc=povcone([0,0,0],0,[0,0,a],1,"");

\>vp=[gp[1],0,gp[2]]; dp=gp[3];

\>writeln(povplane(vp,dp,povlook(blue,0.5),pc));


Sekarang kita menghasilkan dua titik pada lingkaran, di mana bola
menyentuh kerucut.


\>function turnz(v) := return [-v[2],v[1],v[3]]

\>P1=projectToLine([0,u[1]],g1()); P1=turnz([P1[1],0,P1[2]]);

\>writeln(povpoint(P1,povlook(yellow)));

\>P2=projectToLine([0,u[2]],g1()); P2=turnz([P2[1],0,P2[2]]);

\>writeln(povpoint(P2,povlook(yellow)));


Kemudian kami menghasilkan dua titik di mana bola menyentuh bidang.
Ini adalah fokus dari elips.


\>P3=projectToLine([0,u[1]],g()); P3=[P3[1],0,P3[2]];

\>writeln(povpoint(P3,povlook(yellow)));

\>P4=projectToLine([0,u[2]],g()); P4=[P4[1],0,P4[2]];

\>writeln(povpoint(P4,povlook(yellow)));


Selanjutnya kita hitung perpotongan P1P2 dengan bidang.


\>t1=scalp(vp,P1)-dp; t2=scalp(vp,P2)-dp; P5=P1+t1/(t1-t2)\*(P2-P1);

\>writeln(povpoint(P5,povlook(yellow)));


Kami menghubungkan titik-titik dengan segmen garis.


\>writeln(povsegment(P1,P2,povlook(yellow)));

\>writeln(povsegment(P5,P3,povlook(yellow)));

\>writeln(povsegment(P5,P4,povlook(yellow)));


Sekarang kita menghasilkan pita abu-abu, di mana bola menyentuh
kerucut.


\>pcw=povcone([0,0,0],0,[0,0,a],1.01);

\>pc1=povcylinder([0,0,P1[3]-defaultpointsize/2],[0,0,P1[3]+defaultpointsize/2],1);

\>writeln(povintersection([pcw,pc1],povlook(gray)));

\>pc2=povcylinder([0,0,P2[3]-defaultpointsize/2],[0,0,P2[3]+defaultpointsize/2],1);

\>writeln(povintersection([pcw,pc2],povlook(gray)));


Mulai program Povray.


\>povend();


Untuk mendapatkan Anaglyph ini kita perlu memasukkan semuanya ke dalam
fungsi scene. Fungsi ini akan digunakan dua kali kemudian.


\>function scene () ...


    global a,u,dd,g,g1,defaultpointsize;
    writeln(povsphere([0,0,u[1]],dd[1],povlook(red)));
    writeln(povsphere([0,0,u[2]],dd[2],povlook(red)));
    writeln(povcone([0,0,0],0,[0,0,a],1,povlook(lightgray,1)));
    gp=g();
    pc=povcone([0,0,0],0,[0,0,a],1,"");
    vp=[gp[1],0,gp[2]]; dp=gp[3];
    writeln(povplane(vp,dp,povlook(blue,0.5),pc));
    P1=projectToLine([0,u[1]],g1()); P1=turnz([P1[1],0,P1[2]]);
    writeln(povpoint(P1,povlook(yellow)));
    P2=projectToLine([0,u[2]],g1()); P2=turnz([P2[1],0,P2[2]]);
    writeln(povpoint(P2,povlook(yellow)));
    P3=projectToLine([0,u[1]],g()); P3=[P3[1],0,P3[2]];
    writeln(povpoint(P3,povlook(yellow)));
    P4=projectToLine([0,u[2]],g()); P4=[P4[1],0,P4[2]];
    writeln(povpoint(P4,povlook(yellow)));
    t1=scalp(vp,P1)-dp; t2=scalp(vp,P2)-dp; P5=P1+t1/(t1-t2)*(P2-P1);
    writeln(povpoint(P5,povlook(yellow)));
    writeln(povsegment(P1,P2,povlook(yellow)));
    writeln(povsegment(P5,P3,povlook(yellow)));
    writeln(povsegment(P5,P4,povlook(yellow)));
    pcw=povcone([0,0,0],0,[0,0,a],1.01);
    pc1=povcylinder([0,0,P1[3]-defaultpointsize/2],[0,0,P1[3]+defaultpointsize/2],1);
    writeln(povintersection([pcw,pc1],povlook(gray)));
    pc2=povcylinder([0,0,P2[3]-defaultpointsize/2],[0,0,P2[3]+defaultpointsize/2],1);
    writeln(povintersection([pcw,pc2],povlook(gray)));
    endfunction
</pre>
Anda membutuhkan kacamata merah/sian untuk menghargai efek berikut.


\>povanaglyph("scene",zoom=11,center=[0,0,0.5],height=10°,angle=140°);


## Contoh 8: Geometri Bumi

Dalam buku catatan ini, kami ingin melakukan beberapa perhitungan
sferis. Fungsi-fungsi tersebut terdapat dalam file "spherical.e" di
folder contoh. Kita perlu memuat file itu terlebih dahulu.


\>load "spherical.e";


Untuk memasukkan posisi geografis, kami menggunakan vektor dengan dua
koordinat dalam radian (utara dan timur, nilai negatif untuk selatan
dan barat). Berikut koordinat Kampus FMIPA UNY.


\>FMIPA=[rad(-7,-46.467),rad(110,23.05)]


    [-0.13569,  1.92657]

Anda dapat mencetak posisi ini dengan sposprint (cetak posisi
spherical).


\>sposprint(FMIPA) // posisi garis lintang dan garis bujur FMIPA UNY


    S 7°46.467' E 110°23.050'

Mari kita tambahkan dua kota lagi, Solo dan Semarang.


\>Solo=[rad(-7,-34.333),rad(110,49.683)]; Semarang=[rad(-6,-59.05),rad(110,24.533)];

\>sposprint(Solo), sposprint(Semarang),


    S 7°34.333' E 110°49.683'
    S 6°59.050' E 110°24.533'

Pertama kita menghitung vektor dari satu ke yang lain pada bola ideal.
Vektor ini [pos,jarak] dalam radian. Untuk menghitung jarak di bumi,
kita kalikan dengan jari-jari bumi pada garis lintang 7°.


\>br=svector(FMIPA,Solo); degprint(br[1]), br[2]\*rearth(7°)-\>km // perkiraan jarak FMIPA-Solo


    65°20'26.60''
    53.8945384608

Ini adalah perkiraan yang baik. Rutinitas berikut menggunakan
perkiraan yang lebih baik. Pada jarak yang begitu pendek hasilnya
hampir sama.


\>esdist(FMIPA,Semarang)-\>" km", // perkiraan jarak FMIPA-Semarang


    88.0114026318 km

Ada fungsi untuk heading, dengan mempertimbangkan bentuk elips bumi.
Sekali lagi, kami mencetak dengan cara yang canggih.


\>sdegprint(esdir(FMIPA,Solo))


         65.34°

Sudut segitiga melebihi 180° pada bola.


\>asum=sangle(Solo,FMIPA,Semarang)+sangle(FMIPA,Solo,Semarang)+sangle(FMIPA,Semarang,Solo); degprint(asum)


    180°0'10.77''

Ini dapat digunakan untuk menghitung luas segitiga. Catatan: Untuk
segitiga kecil, ini tidak akurat karena kesalahan pengurangan dalam
asum-pi.


\>(asum-pi)\*rearth(48°)^2-\>" km^2", // perkiraan luas segitiga FMIPA-Solo-Semarang


    2116.02948749 km^2

Ada fungsi untuk ini, yang menggunakan garis lintang rata-rata
segitiga untuk menghitung jari-jari bumi, dan menangani kesalahan
pembulatan untuk segitiga yang sangat kecil.


\>esarea(Solo,FMIPA,Semarang)-\>" km^2", //perkiraan yang sama dengan fungsi esarea()


    2123.64310526 km^2

Kita juga dapat menambahkan vektor ke posisi. Sebuah vektor berisi
heading dan jarak, keduanya dalam radian. Untuk mendapatkan vektor,
kami menggunakan vektor. Untuk menambahkan vektor ke posisi, kami
menggunakan vektor sadd.


\>v=svector(FMIPA,Solo); sposprint(saddvector(FMIPA,v)), sposprint(Solo),


    S 7°34.333' E 110°49.683'
    S 7°34.333' E 110°49.683'

Fungsi-fungsi ini mengasumsikan bola yang ideal. Hal yang sama di
bumi.


\>sposprint(esadd(FMIPA,esdir(FMIPA,Solo),esdist(FMIPA,Solo))), sposprint(Solo),


    S 7°34.333' E 110°49.683'
    S 7°34.333' E 110°49.683'

Mari kita beralih ke contoh yang lebih besar, Tugu Jogja dan Monas
Jakarta (menggunakan Google Earth untuk mencari koordinatnya).


\>Tugu=[-7.7833°,110.3661°]; Monas=[-6.175°,106.811944°];

\>sposprint(Tugu), sposprint(Monas)


    S 7°46.998' E 110°21.966'
    S 6°10.500' E 106°48.717'

Menurut Google Earth, jaraknya adalah 429,66 km. Kami mendapatkan
pendekatan yang baik.


\>esdist(Tugu,Monas)-\>" km", // perkiraan jarak Tugu Jogja - Monas Jakarta


    431.565659488 km

Judulnya sama dengan judul yang dihitung di Google Earth.


\>degprint(esdir(Tugu,Monas))


    294°17'2.85''

Namun, kita tidak lagi mendapatkan posisi target yang tepat, jika kita
menambahkan heading dan jarak ke posisi semula. Hal ini terjadi,
karena kita tidak menghitung fungsi invers secara tepat, tetapi
mengambil perkiraan jari-jari bumi di sepanjang jalan.


\>sposprint(esadd(Tugu,esdir(Tugu,Monas),esdist(Tugu,Monas)))


    S 6°10.500' E 106°48.717'

Namun, kesalahannya tidak besar.


\>sposprint(Monas),


    S 6°10.500' E 106°48.717'

Tentu kita tidak bisa berlayar dengan tujuan yang sama dari satu
tujuan ke tujuan lainnya, jika kita ingin menempuh jalur terpendek.
Bayangkan, Anda terbang NE mulai dari titik mana pun di bumi. Kemudian
Anda akan berputar ke kutub utara. Lingkaran besar tidak mengikuti
heading yang konstan!


Perhitungan berikut menunjukkan bahwa kami jauh dari tujuan yang
benar, jika kami menggunakan pos yang sama selama perjalanan kami.


\>dist=esdist(Tugu,Monas); hd=esdir(Tugu,Monas);


Sekarang kita tambahkan 10 kali sepersepuluh dari jarak, menggunakan
pos ke Monas, kita sampai di Tugu.


\>p=Tugu; loop 1 to 10; p=esadd(p,hd,dist/10); end;


Hasilnya jauh.


\>sposprint(p), skmprint(esdist(p,Monas))


    S 6°11.250' E 106°48.372'
         1.529km

Sebagai contoh lain, mari kita ambil dua titik di bumi pada garis
lintang yang sama.


\>P1=[30°,10°]; P2=[30°,50°];


Jalur terpendek dari P1 ke P2 bukanlah lingkaran garis lintang 30°,
melainkan jalur terpendek yang dimulai 10° lebih jauh ke utara di P1.


\>sdegprint(esdir(P1,P2))


         79.69°

Tapi, jika kita mengikuti pembacaan kompas ini, kita akan berputar ke
kutub utara! Jadi kita harus menyesuaikan arah kita di sepanjang
jalan. Untuk tujuan kasar, kami menyesuaikannya pada 1/10 dari total
jarak.


\>p=P1;  dist=esdist(P1,P2); ...  
\>     loop 1 to 10; dir=esdir(p,P2); sdegprint(dir), p=esadd(p,dir,dist/10); end;


         79.69°
         81.67°
         83.71°
         85.78°
         87.89°
         90.00°
         92.12°
         94.22°
         96.29°
         98.33°

Jaraknya tidak tepat, karena kita akan menambahkan sedikit kesalahan,
jika kita mengikuti heading yang sama terlalu lama.


\>skmprint(esdist(p,P2))


         0.203km

Kami mendapatkan perkiraan yang baik, jika kami menyesuaikan pos
setelah setiap 1/100 dari total jarak dari Tugu ke Monas.


\>p=Tugu; dist=esdist(Tugu,Monas); ...  
\>     loop 1 to 100; p=esadd(p,esdir(p,Monas),dist/100); end;

\>skmprint(esdist(p,Monas))


         0.000km

Untuk keperluan navigasi, kita bisa mendapatkan urutan posisi GPS di
sepanjang lingkaran besar menuju Monas dengan fungsi navigasi.


\>load spherical; v=navigate(Tugu,Monas,10); ...  
\>     loop 1 to rows(v); sposprint(v[#]), end;


    S 7°46.998' E 110°21.966'
    S 7°37.422' E 110°0.573'
    S 7°27.829' E 109°39.196'
    S 7°18.219' E 109°17.834'
    S 7°8.592' E 108°56.488'
    S 6°58.948' E 108°35.157'
    S 6°49.289' E 108°13.841'
    S 6°39.614' E 107°52.539'
    S 6°29.924' E 107°31.251'
    S 6°20.219' E 107°9.977'
    S 6°10.500' E 106°48.717'

Kami menulis sebuah fungsi, yang memplot bumi, dua posisi, dan posisi
di antaranya.


\>function testplot ...


    useglobal;
    plotearth;
    plotpos(Tugu,"Tugu Jogja"); plotpos(Monas,"Tugu Monas");
    plotposline(v);
    endfunction
</pre>
Sekarang rencanakan semuanya.


\>plot3d("testplot",angle=25, height=6,\>own,\>user,zoom=4):


Atau gunakan plot3d untuk mendapatkan tampilan anaglyph. Ini terlihat
sangat bagus dengan kacamata merah/sian.


\>plot3d("testplot",angle=25,height=6,distance=5,own=1,anaglyph=1,zoom=4):


## MENCOBA RUMUS-RUMUS PADA MATERI DI ATAS

## Geometri Simbolik

\>A &:= [2,0]; B &:= [0,2]; C &:= [3,3]; // menentukan tiga titik A, B, C

\>c &:= lineThrough(B,C) // c=BC


    [-1,  3,  6]

\>$getLineEquation(c,x,y), $solve(%,y) | expand // persamaan garis c

\>h &= perpendicular(A,lineThrough(B,C)) // h melalui A tegak lurus BC


    
                                  [3, 1, 6]
    

\>Q &= lineIntersection(c,h) // Q titik potong garis c=BC dan h


    
                                    6  12
                                   [-, --]
                                    5  5
    

\>$projectToLine(A,lineThrough(B,C)) // proyeksi A pada BC

\>$distance(A,Q) // jarak AQ

\>cc &= circleThrough(A,B,C); $cc // (titik pusat dan jari-jari) lingkaran melalui A, B, C

\>r&=getCircleRadius(cc); $r , $float(r) // tampilkan nilai jari-jari

\>$computeAngle(A,C,B) // nilai <ACB

\>$solve(getLineEquation(angleBisector(A,C,B),x,y),y)[1] // persamaan garis bagi <ACB

\>P &= lineIntersection(angleBisector(A,C,B),angleBisector(C,B,A)); $P // titik potong 2


## Garis dan Lingkaran yang berpotongan

\>A &:= [2,0]; c =circleWithCenter(A,4);

\>B &:= [2,3]; C &:= [3,2]; l =lineThrough(B,C);

\>setPlotRange(5); plotCircle(c); plotLine(l);

\>{P1,P2,f}=lineCircleIntersections(l,c);

\>P1, P2,


    [5.89792,  -0.897916]
    [1.10208,  3.89792]

\>plotPoint(P1); plotPoint(P2):


\>c &= circleWithCenter(A,4) // lingkaran dengan pusat A jari-jari 4


    
                                  [2, 0, 4]
    

\>l &= lineThrough(B,C) // garis l melalui B dan C


    
                                  [1, 1, 5]
    

\>$lineCircleIntersections(l,c) | radcan, // titik potong lingkaran c dan garis l


\>C=A+normalize([-3,-4])\*4; plotPoint(C); plotSegment(P1,C); plotSegment(P2,C);

\>degprint(computeAngle(P1,C,P2))


    57°58'20.06''

\>C=A+normalize([-4,-5])\*4; plotPoint(C); plotSegment(P1,C); plotSegment(P2,C);

\>degprint(computeAngle(P1,C,P2))


    57°58'20.06''

\>insimg;


##  Garis Sumbu

\>A &:=[3,3]; B &:=[-2,-3];

\>c1=circleWithCenter(A,distance(A,B));

\>c2=circleWithCenter(B,distance(A,B));

\>{P1,P2,f}=circleCircleIntersections(c1,c2);

\>l=lineThrough(P1,P2);

\>setPlotRange(5); plotCircle(c1); plotCircle(c2);

\>plotPoint(A); plotPoint(B); plotSegment(A,B); plotLine(l):

\>A &= [a1,a2]; B &= [b1,b2];

\>c1 &= circleWithCenter(A,distance(A,B));

\>c2 &= circleWithCenter(B,distance(A,B));

\>P &= circleCircleIntersections(c1,c2); P1 &= P[1]; P2 &= P[2];

\>g &= getLineEquation(lineThrough(P1,P2),x,y);

\>$solve(g,y)

\>$solve(getLineEquation(middlePerpendicular(A,B),x,y),y)

\>h &=getLineEquation(lineThrough(A,B),x,y);

\>$solve(h,y)


## Garis Euler dan Parabola

\>A &:=[-1.5,-1.5]; B &:=[3,0]; C &:=[1.5,3];

\>setPlotRange(3); plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C");


\>plotSegment(A,B,""); plotSegment(B,C,""); plotSegment(C,A,""):

\>$areaTriangle(A,B,C)


\>c &= lineThrough(A,B)


    
                                   3  9    9
                                [- -, -, - -]
                                   2  2    2
    

\>$getLineEquation(c,x,y)

\>$getHesseForm(c,x,y,C), $at(%,[x=C[1],y=C[2]])


\>LL &= circleThrough(A,B,C); $getCircleEquation(LL,x,y)

\>O &= getCircleCenter(LL); $O

\>plotCircle(LL()); plotPoint(O(),"O"):

\>H &= lineIntersection(perpendicular(A,lineThrough(C,B)),...  
\>     perpendicular(B,lineThrough(A,C))); $H


\>el &= lineThrough(H,O); $getLineEquation(el,x,y)


\>plotPoint(H(),"H"); plotLine(el(),"Garis Euler"):


\>M &= (A+B+C)/3; $getLineEquation(el,x,y) with [x=M[1],y=M[2]]

\>plotPoint(M(),"M"): // titik berat

\>$distance(M,H)/distance(M,O)|radcan


\>$computeAngle(A,C,B), degprint(%())


    60°15'18.43''

\>Q &= lineIntersection(angleBisector(A,C,B),angleBisector(C,B,A))|radcan; $Q

\>r &= distance(Q,projectToLine(Q,lineThrough(A,B)))|ratsimp; $r

\>LD &=  circleWithCenter(Q,r); // Lingkaran dalam


\>color(5); plotCircle(LD()):


## contoh lain dari materi trigonometri rasional

\>A &:=[2,3]; B &:=[5,4]; C &:=[0,5]; ...  
\>   setPlotRange(-1,5,1,7); ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   plotSegment(B,A,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   insimg;

\>$distance(A,B)

\>c &= quad(A,B); $c, b &= quad(A,C); $b, a &= quad(B,C); $a,


\>wb &= computeAngle(A,B,C); $wb, $(wb/pi\*180)()


    29.7448812969

\>$crosslaw(a,b,c,x), $solve(%,x), //(b+c-a)^=4b.c(1-x)

\>sb &= spread(b,a,c); $sb

\>$sin(computeAngle(A,B,C))^2

\>ha &= c\*sb; $ha

\>$sqrt(ha)

\>$sqrt(ha)\*sqrt(a)/2


\>$areaTriangle(B,A,C)


## Aturan penyebaran 3 kali lipat

\>setPlotRange(1); ...  
\>   color(1); plotCircle(circleWithCenter([0,0],1)); ...  
\>   A:=[cos(1),sin(1)]; B:=[cos(2),sin(2)]; C:=[cos(6),sin(6)]; ...  
\>   plotPoint(A,"A"); plotPoint(B,"B"); plotPoint(C,"C"); ...  
\>   color(3); plotSegment(A,B,"c"); plotSegment(A,C,"b"); plotSegment(C,B,"a"); ...  
\>   color(1); O:=[0,0];  plotPoint(O,"0"); ...  
\>   plotSegment(A,O); plotSegment(B,O); plotSegment(C,O,"r"); ...  
\>   insimg;

\>&remvalue(a,b,c,r); // hapus nilai-nilai sebelumnya untuk perhitungan baru

\>rabc &= rhs(solve(triplespread(spread(b,r,r),spread(a,r,r),spread(c,r,r)),r)[4]); $rabc


\>function periradius(a,b,c) &= rabc;


\>a:=quadrance(B,C); b:=quadrance(A,C); c:=quadrance(A,B);


\>periradius(a,b,c)


    1

\>$spread(b,a,c)\*rabc | ratsimp

\>$doublespread(b/(4\*r))-spread(b,r,r) | ratsimp


## Contoh 6: Jarak Minimal pada Bidang

## Catatan awal

Fungsi yang, ke titik M di bidang, menetapkan jarak AM antara titik
tetap A dan M, memiliki garis level yang agak sederhana: lingkaran
berpusat di A.


\>&remvalue();

\>A=[-2,-2];

\>function d1(x,y):=sqrt((x-A[1])^2+(y-A[2])^2)

\>fcontour("d1",xmin=-2,xmax=0,ymin=-2,ymax=0,hue=1, ...  
\>   title="If you see ellipses, please set your window square"):


dan grafiknya juga agak sederhana: bagian atas kerucut:


\>plot3d("d1",xmin=-2,xmax=0,ymin=-2,ymax=0):


Ternyata setelah mencoba yang bisa hanya dengan memasukkan angka 1,
karena ketika memakai angka 2, plot tidak membentuk kerucut diatas.


## Dua poin

\>B=[2,-2];

\>function d2(x,y):=d1(x,y)+sqrt((x-B[1])^2+(y-B[2])^2)

\>fcontour("d2",xmin=-2,xmax=2,ymin=-3,ymax=1,hue=1):


Grafiknya lebih menarik:


\>plot3d("d2",xmin=-2,xmax=2,ymin=-3,ymax=1):


Pembatasan garis (AB) lebih terkenal:


\>plot2d("abs(x+1)+abs(x-1)",xmin=-3,xmax=3):


## Tiga poin



Contoh:


\>C=[-3,2];

\>function d3(x,y):=d2(x,y)+sqrt((x-C[1])^2+(y-C[2])^2)

\>plot3d("d3",xmin=-5,xmax=3,ymin=-4,ymax=4);

\>insimg;

\>fcontour("d3",xmin=-4,xmax=1,ymin=-2,ymax=2,hue=1,title="The minimum is on A");

\>P=(A\_B\_C\_A)'; plot2d(P[1],P[2],add=1,color=12);

\>insimg;


Tetapi jika semua sudut segitiga ABC kurang dari 120 °, minimumnya
adalah pada titik F di bagian dalam segitiga, yang merupakan
satu-satunya titik yang melihat sisi-sisi ABC dengan sudut yang sama
(maka masing-masing 120 ° ):


\>C=[-1,2];

\>plot3d("d3",xmin=-2,xmax=2,ymin=-2,ymax=2):

\>fcontour("d3",xmin=-2,xmax=2,ymin=-2,ymax=2,hue=1,title="The Fermat point");

\>P=(A\_B\_C\_A)'; plot2d(P[1],P[2],add=1,color=12);

\>insimg;


## Empat poin

Langkah selanjutnya adalah menambahkan 4 titik D dan mencoba
meminimalkan MA+MB+MC+MD; katakan bahwa Anda adalah operator TV kabel
dan ingin mencari di bidang mana Anda harus meletakkan antena sehingga
Anda dapat memberi makan empat desa dan menggunakan panjang kabel
sesedikit mungkin!


\>D=[2,21];

\>function d4(x,y):=d3(x,y)+sqrt((x-D[1])^2+(y-D[2])^2)

\>plot3d("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5):

\>fcontour("d4",xmin=-1.5,xmax=1.5,ymin=-1.5,ymax=1.5,hue=1);

\>P=(A\_B\_C\_D)'; plot2d(P[1],P[2],points=1,add=1,color=12);

\>insimg;


## Contoh 7: Bola Dandelin dengan Povray

\>load geometry;


Pertama dua garis yang membentuk kerucut.


\>g1 &= lineThrough([0,0],[2,a])


    
                                 [- a, 2, 0]
    

\>g2 &= lineThrough([0,0],[-2,a])


    
                                [- a, - 2, 0]
    

\>g &= lineThrough([-2,0],[2,2])


    
                                 [- 2, 4, 4]
    

\>setPlotRange(-2,2,0,3);

\>color(black); plotLine(g(),"")

\>a:=2; color(blue); plotLine(g1(),""), plotLine(g2(),""):


Sekarang kita ambil titik umum pada sumbu y.


\>P &= [0,u]


    
                                    [0, u]
    

Hitung jarak ke g1.


\>d1 &= distance(P,projectToLine(P,g1)); $d1


Hitung jarak ke g.


\>d &= distance(P,projectToLine(P,g)); $d


Dan temukan pusat kedua lingkaran yang jaraknya sama.


\>sol &= solve(d1^2=d^2,u); $sol


Ada dua solusi.


\>u := sol()


    [0.558482,  4.77485]

\>dd := d()


    [0.394906,  3.37633]

Plot lingkaran ke dalam gambar.


\>color(red);

\>plotCircle(circleWithCenter([0,u[1]],dd[1]),"");

\>plotCircle(circleWithCenter([0,u[2]],dd[2]),"");

\>insimg;


## Latihan

1. Gambarlah segi-n beraturan jika diketahui titik pusat O, n, dan
jarak titik pusat ke titik-titik sudut segi-n tersebut (jari-jari
lingkaran luar segi-n), r.


Petunjuk:


* 
Besar sudut pusat yang menghadap masing-masing sisi segi-n adalah
* (360/n).

* 
Titik-titik sudut segi-n merupakan perpotongan lingkaran luar segi-n
* dan garis-garis yang melalui pusat dan saling membentuk sudut sebesar
* kelipatan (360/n).

* 
Untuk n ganjil, pilih salah satu titik sudut adalah di atas.

* 
Untuk n genap, pilih 2 titik di kanan dan kiri lurus dengan titik
* pusat.

* 
Anda dapat menggambar segi-3, 4, 5, 6, 7, dst beraturan.


Penyelesaian :


\>load geometry


    Numerical and symbolic geometry.

\>setPlotRange(-3.5,3.5,-3.5,3.5);

\>A=[-2,-2]; plotPoint(A,"A");

\>B=[2,-2]; plotPoint(B,"B");

\>C=[0,3]; plotPoint(C,"C");

\>plotSegment(A,B,"c");

\>plotSegment(B,C,"a");

\>plotSegment(A,C,"b");

\>aspect(1):

\>c=circleThrough(A,B,C);

\>R=getCircleRadius(c);

\>O=getCircleCenter(c);

\>plotPoint(O,"O");

\>l=angleBisector(A,C,B);

\>color(2); plotLine(l); color(1);

\>plotCircle(c,"Lingkaran luar segitiga ABC"):


2. Gambarlah suatu parabola yang melalui 3 titik yang diketahui.


Petunjuk:


- Misalkan persamaan parabolanya y= ax^2+bx+c.


- Substitusikan koordinat titik-titik yang diketahui ke persamaan
tersebut.


- Selesaikan SPL yang terbentuk untuk mendapatkan nilai-nilai a, b, c.


Penyelesaian :


\>load geometry;

\>setPlotRange(5); P=[2,0]; Q=[4,0]; R=[0,-4];

\>plotPoint(P,"P"); plotPoint(Q,"Q"); plotPoint(R,"R"):

\>sol &= solve([a+b=-c,16\*a+4\*b=-c,c=-4],[a,b,c])


    
                         [[a = - 1, b = 5, c = - 4]]
    

Sehingga didapatkan nilai a = -1, b = 5 dan c = -4


\>function y&=-x^2+5\*x-4


    
                                   2
                                - x  + 5 x - 4
    

\>plot2d("-x^2+5\*x-4",-5,5,-5,5):


3. Gambarlah suatu segi-4 yang diketahui keempat titik sudutnya,
misalnya A, B, C, D.


   - Tentukan apakah segi-4 tersebut merupakan segi-4 garis singgung
(sisinya-sisintya merupakan garis singgung lingkaran yang sama yakni
lingkaran dalam segi-4 tersebut).


   - Suatu segi-4 merupakan segi-4 garis singgung apabila keempat
garis bagi sudutnya bertemu di satu titik.


   - Jika segi-4 tersebut merupakan segi-4 garis singgung, gambar
lingkaran dalamnya.


   - Tunjukkan bahwa syarat suatu segi-4 merupakan segi-4 garis
singgung apabila hasil kali panjang sisi-sisi yang berhadapan sama.


Penyelesaian :


\>load geometry


    Numerical and symbolic geometry.

\>setPlotRange(-4.5,4.5,-4.5,4.5);

\>A=[-3,-3]; plotPoint(A,"A");

\>B=[3,-3]; plotPoint(B,"B");

\>C=[3,3]; plotPoint(C,"C");

\>D=[-3,3]; plotPoint(D,"D");

\>plotSegment(A,B,"");

\>plotSegment(B,C,"");

\>plotSegment(C,D,"");

\>plotSegment(A,D,"");

\>aspect(1):

\>l=angleBisector(A,B,C);

\>m=angleBisector(B,C,D);

\>P=lineIntersection(l,m);

\>color(5); plotLine(l); plotLine(m); color(1);

\>plotPoint(P,"P"):


Dari gambar diatas terlihat bahwa keempat garis bagi sudutnya bertemu
di satu titik yaitu titik P.


\>r=norm(P-projectToLine(P,lineThrough(A,B)));

\>plotCircle(circleWithCenter(P,r),"Lingkaran dalam segiempat ABCD"):


Dari gambar diatas, terlihat bahwa sisi-sisinya merupakan garis
singgung lingkaran yang sama yaitu lingkaran dalam segiempat.


Akan ditunjukkan bahwa hasil kali panjang sisi-sisi yang berhadapan
sama.


\>AB=norm(A-B) //panjang sisi AB


    6

\>CD=norm(C-D) //panjang sisi CD


    6

\>AD=norm(A-D) //panjang sisi AD


    6

\>BC=norm(B-C) //panjang sisi BC


    6

\>AB.CD


    36

\>AD.BC


    36

Terbukti bahwa hasil kali panjang sisi-sisi yang berhadapan sama yaitu
36. Jadi dapat dipastikan bahwa segiempat tersebut merupakan segiempat
garis singgung.


4. Gambarlah suatu ellips jika diketahui kedua titik fokusnya,
misalnya P dan Q. Ingat ellips dengan fokus P dan Q adalah tempat
kedudukan titik-titik yang jumlah jarak ke P dan ke Q selalu sama
(konstan).


Penyelesaian :


Diketahui kedua titik fokus P = [-1,-1] dan Q = [1,-1]


\>P=[-1,-1]; Q=[1,-1];

\>function d1(x,y):=sqrt((x-P[1])^2+(y-P[2])^2)

\>Q=[1,-1]; function d2(x,y):=sqrt((x-P[1])^2+(y-P[2])^2)+sqrt((x-Q[1])^2+(y-Q[2])^2)

\>fcontour("d2",xmin=-2,xmax=2,ymin=-3,ymax=1,hue=1):


Grafik yang lebih menarik


\>plot3d("d2",xmin=-2,xmax=2,ymin=-3,ymax=1):


Batasan ke garis PQ


\>plot2d("abs(x+1)+abs(x-1)",xmin=-3,xmax=3):


5. Gambarlah suatu hiperbola jika diketahui kedua titik fokusnya,
misalnya P dan Q. Ingat ellips dengan fokus P dan Q adalah tempat
kedudukan titik-titik yang selisih jarak ke P dan ke Q selalu sama
(konstan).


Penyelesaian :


\>P=[-1,-1]; Q=[1,-1];

\>function d1(x,y):=sqrt((x-p[1])^2+(y-p[2])^2)

\>Q=[1,-1]; function d2(x,y):=sqrt((x-P[1])^2+(y-P[2])^2)+sqrt((x+Q[1])^2+(y+Q[2])^2)

\>fcontour("d2",xmin=-2,xmax=2,ymin=-3,ymax=1,hue=1):


Grafik yang lebih menarik


\>plot3d("d2",xmin=-2,xmax=2,ymin=-3,ymax=1):

\>plot2d("abs(x+1)+abs(x-1)",xmin=-3,xmax=3):

