# Writing & Presentation Week 1 - Web Development Basic
## Rafid Ammar Adinegoro
## 19-23 September 2022

### **1. Unix Commmand Line, Git, dan Github dasar. 19 September 2022.**
### Unix Command Line
Saat kita menyebut "command line" atau "command line interface", sebenarnya yang dimaksud adalah shell yang berbasis teks. Shell ini adalah program yang menerima perintah, kemudian meneruskan perintah tersebut ke system untuk dieksekusi.  Selain command line, kita juga punya shell berbasis grafis yang lebih dikenal dengan nama GUI atau graphical user interface.
- Shell, program yang digunakan untuk berkomunikasi atau memerintah sistem
- Command Line Interface, jenis shell yang berbasis teks
- Terminal Emulator = aplikasi untuk mengakses CLI
### Filesystem
- Sebuah filesystem mengatur bagaimana data disimpan di dalam sebuah system
- Sistem operasi Windows & Unix-like menyusun file dan direktori menggunakan struktur yang bentuknya mirip tree
### Command pada command line :
- Command “pwd” (print working directory) untuk melihat nama direktori kita berada saat ini.
- “ls” (lists) untuk melihat isi dari direktori
- “cd” (change directory) untuk pindah ke direktori lain
- “head” command untuk melihat beberapa line awal dari sebuah file text
- “tail” command untuk melihat beberapa line awal dari sebuah file text
- “cat” command untuk melihat isi sebuah file
- “touch” command untuk membuat sebuah file
- “mkdir” command untuk membuat sebuah direktori
- “cp” command untuk mengcopy files atau directory
- “mv” command untuk memindahkan files atau directory, bisa gunakan juga untuk rename
- “rm” command untuk menghapus file atau directory
- “nano” command untuk membuka file
### Git dan Github
- GIT adalah sebagai version control system, Tugasnya adalah mencatat setiap perubahan pada File (termasuk code yang kita buat) pada suatu proyek baik dikerjakan secara individu maupun tim
- File-file yg disimpan menggunakan git akan terlacak seluruh perubahannya, termasuk siapa yang mengubah.
### Command git :
- git init (1x aja) = memasang git ke dalam projek atau membuat repository lokal
- git status = melacak perubahan
- git add = menambahkan file baru di repository yang dipilih.
- git commit = menyimpan perubahan yang sudah dilakukan, namun tidak ada perubahan yang terjadi pada remote repository
- git remote (1x aja) = Untuk menambahkan remote baru, petunjuk ke versi repositori yang biasanya disimpan di server lain
- git push = mengirimkan perubahan file yang dilakukan setelah di commit ke remote repository
- git branch = melihat semua cabang di repository
- git checkout = menukar branch yang aktif dengan branch yang sudah dipilih.
- git merge = menggabungkan cabang aktif serta cabang yang dipilih
- git clone = mengkloning repository lokal
### **2. HTML. 20 September 2022.**
### HTML
- HTML adalah singkatan dari Hypertext Markup Language
- HTML digunakan untuk menampilkan konten pada browser.
- HTML adalah singkatan dari Hypertext Markup Language.
- HTML digunakan untuk menampilkan konten pada browser.
- Contoh konten yang dapat ditampilkan seperti Text, Image, Video, Link, dan masih banyak lainnya.
- HTML bukanlah sebuah bahasa pemrograman, artinya HTML tidak bisa dinamis mengolah data.
- Visual Studio Code adalah code editor yang dikembangkan oleh tim engineer Microsoft
- HTML Structure. HTML tersusun sebagai kesatuan dari sebuah tingkatan (family tree relationship). Saat sebuah element berada di dalam element lain, maka disebut child element. Element yang berada diatas element lain disebut parent element.
- HTML element didefinisikan dengan opening tag, content, dan closing tag
- Attribute adalah properties dari sebuah HTML Element. Semua HTML Element memiliki attribute.
- HTML Comment, Dengan HTML Comment, kita dapat memberikan penjelasan maksud dari line code yang kita kerjakan. Comment tidak akan dieksekusi oleh sistem. Comment hanya untuk dibaca oleh sesama programmer.
- Kita bisa menjalankan HTML dengan mencari lokasi file HTML kita lalu membukanya via browser. Atau menggunakan extension dari Visual Studio Code bernama Live Server. Dengan Live Server kita bisa menjalankan HTML tanpa harus refresh setiap ada perubahan
- Tidak semua HTML Element memiliki content. Seperti element <br> Element ini disebut empty element. Empty element tidak memiliki closing tag.
- Tag img untuk menampilkan gambar. 
```
  <img src =” “ alt=” “>
```
src atau source adalah  attribute untuk memberitahukan sumber gambar. Kita bisa menampilkan gambar melalui file lokal komputer kita atau menggunakan link dari internet. Alt adalah alternative ketika gambar tidak berhasil muncul, kita bisa memberi tahu ke user di tag img kita menampilkan gambar apa.
- Tag video untuk menampilkan video 
```
  <video controls>
    <src=” “ type=” “>
  </video> 
```
controls berguna untuk kita bisa mengatur videonya di play / pause dan indikator menit.
- Semantic HTML : Semantic artinya kita menggunakan element html yang sesuai dengan kebutuhan konten. Contoh : 
```
<nav>
<header>
<footer>
<article>
<main>
<aside>
```
- Kegunaan semantic HTML = Meningkatkan Accessibility, Meningkatkan SEO, memudahkan untuk dimaintain.
- Deploy HTML : Deploy adalah sebuah proses untuk menyebarkan aplikasi yang sudah kita kerjakan supaya bisa digunakan oleh orang-orang. Jika aplikasi kita HTML atau Web App kita perlu mendeploy ke server. Kita gunakan tools bernama Netlify.
### **3. CSS. 21 September 2022.**
### Inline CSS, External CSS
- Inline CSS, yaitu menggunakan attribute style untuk menyisipkan kode CSS langsung di dalam HTML element.
- Internal CSS, yaitu menggunakan element <style> untuk menyisipkan kode CSS. Element <style> tersebut diletakkan di dalam element .
- External CSS, yaitu sebuah file CSS terpisah yang disambungkan dengan file HTML dengan menggunakan element <link>.
### CSS Selector
```
  selector{
    property: value;
  }
```
- Memberi style di element dengan nama class tertentu
Kita bisa memberikan tanda pengenal berupa class kepada element tertentu. Setelahnya, kita bisa memberikan style pada element dengan class tersebut dengan menuliskan sebuah tanda titik (.) yang diikuti class dari element tersebut.
Contoh :
- HTML : 
```
  <div class="highlight">
    <p>Saya rafid</p>
  </div>
```
- CSS : 
```
  .highlight{
    background-color: black;
    color: white;
  }
```
### Pseudo Class
- Pseudo class digunakan untuk mendefinisikan keadaan khusus pada suatu element. Contoh : memberikan style pada link saat di hover.
CSS : 
```
  h1:hover{
    background-color: black;
    color: white;
  }
```
### Box Model
- margin yaitu area terluar yang kosong setelah border. Margin bersifat transparan.
- border yaitu garis tepi yang membungkus padding dan konten.
- padding yaitu area kosong di antara konten dan border. Padding bersifat transparan.
- content yaitu konten (value/nilai) dari HTML element. Bisa berupa teks, gambar, video, ataupun suara.
### Properti box-sizing
- Properti box-sizing itu menentukan bagaimana cara menghitung tinggi dan lebar dari sebuah element. Saat kita memberi properti box-sizing: border-box pada sebuah element, pemberian properti width dan height tidak lagi menentukan lebar dan tinggi dari konten, melainkan lebar dan tinggi dari element. Saat kita memberi properti box-sizing: border-box pada sebuah element, ukuran dari konten di dalamnya akan menyesuaikan dengan tinggi dan lebar element.
### Properti display
- Dengan properti display, kita bisa mengatur bagaimana box tersebut ditampilkan. Kalau kita menggunakan properti display: none, tampilan dari element di sekitarnya juga ikut berubah. Kenapa? Saat kita menggunakan properti itu, halaman web kita akan ditampilkan seolah-olah element tersebut tidak ada. Saat kita memberi visibility: hidden pada gambar, ia akan tidak ditampilkan, namun ruang yang tadinya ia tempati tetap akan ada di situ.
- display: block. block-level element adalah element HTML yang memiliki properti display: block secara default. block-level element adalah element HTML yang memiliki properti display: block secara default.
- display: inline pada sebuah element akan membuat ukuran box dari element tersebut hanya sebesar konten di dalamnya saja. Element yang kita beri properti inline tidak bisa diatur lebar maupun tingginya.
- display: inline-block. Element dengan display: inline-block bisa kita atur lebar dan tingginya. Dan secara default hanya akan mengambil ruang sebesar konten di dalamnya
### Properti position
- position: static. Secara default semua element mempunyai properti position bernilai static. Element dengan properti tersebut tidak akan terpengaruh oleh properti top, bottom, left, dan right
- position: relative. ketika diberi properti top, bottom, left, atau right, akan berpindah posisi relatif dari posisi aslinya.
- position-fixed. tetap relatif terhadap viewport, di mana akan selalu berada di tempat yang sama jika walaupun halaman website di-scroll.
- position: absolute. diposisikan relatif terhadap parentnya yg memiliki display properti bukan static
- position: sticky. seperti campuran relatif dan fixed. Awalnya relative, kemudian pada titik tertentu saat discroll, itu menjadi fixed. Dengan kata lain ia akan diam di lokasi relatif terhadap viewport tadi.
### Properti max-width
- max-width : 100%. Kita bisa menggunakan properti max-width: 100% untuk menentukan lebar maksimal dari suatu element.
- Kita bisa menggunakan persentase untuk menentukan lebar suatu element agar sama dengan lebar parent element-nya.
### Media Query
- Dengan menggunakan media query, kita bisa mengatur lebar suatu element dan/atau memberikan style lain yang berbeda-beda sesuai dengan ukuran dari browser.
```
  @media (max-width: 600px){
    .button-group{
      display: flex;
      flex-direction: column;
    }
  }
```
- @media (max-width: 600px) merujuk kepada jendela browser yang lebarnya maksimal 600px. Dengan kata lain, semua rule/kode CSS di dalam @media ini akan diterapkan jika layarnya memiliki lebar 600px atau kurang.
### Flexbox (display: flex)
- Container adalah element yang membungkus dan mengatur tampilan dari element di dalamnya,
- Item adalah element dalam container yang diatur tampilannya.
- Dengan flexbox, memungkinkan untuk mengatur fleksibilitas dan ukuran elemen berbeda didalam wadah tanpa penataan item di dalam container.
- Flex memiliki main-axis dan cross-axis. Defaultnya adalah main-axis adalah horizontal (row), dan cross-axis adalah vertical (column). Ini diatur dalam properti flex-direction
- Justify content. dengan justify content, flexbox juga bisa mengatur tata letak dan ruang di antara item tersebut, seperti : flex-start(kiri), flex-end(kanan), flex-center(tengah), space-between(memberi ruang antara item yg bersebelahan), space-around(memberi ruang yang seimbang pada setiap item)
### **4. Algoritma dan Intro to Javascript. 22 September 2022.**
### Algoritma
- Algoritma adalah deskripsi berupa step-step yang dibutuhkan untuk menyelesaikan suatu masalah
- Kualitas wajib dari algoritma :
- 1. Input dan output harus didefinisikan terlebih dahulu dengan tepat
- 2. Setiap step harus benar-benar clear dan tidak ambigu
- 3. Algoritma seharusnya tidak mengandung suatu code pada bahasa pemograman tertentu. Algoritma harus dibuat agar dapat digunakan dalam bahasa pemograman apapun.
- Pseudocode : Pseudocode adalah menuliskan algoritma dengan umumnya bahasa inggris sebelum kita implementasikan ke bahasa pemograman tertentu.
- Cara menulis pseudocode :
- 1. Menggunakan HURUF BESAR pada kata kunci (key commands). Contoh : IF number is > 10 THEN
- 2. 1 statement = 1 baris
- 3. Gunakan indentasi
- 4. Spesifik tapi tetap simpel
### Javascript
- Javascript adalah bahasa pemrograman yang digunakan untuk logic pada sebuah website. Javascript juga dapat membuat website menjadi interfaktif dan dinamis.
### Syntax dan Statement
- Syntax bisa dianalogikan seperti kosa kata (vocabulary) dan tata cara (grammar) pada bahasa pemograman. Kita menggunakan syntax tertentu untuk membuat statement program, instruksi untuk djalankan/dieksekusi oleh web browser, compiler, ataupun intrepreter
- Contoh Syntax : alert(), prompt(), confirm(),
- Console log adalah tempat kita untuk cek logic pemrograman web yang kita kembangkan. Console log juga tempat kita untuk melakukan debugging (mengetahui error pada code) pada pemograman web.
### Tipe Data
- Tipe data : Tipe data adalah klasifikasi yang kita berikan untuk berbagai macam data yang digunakan dalam programming. Tipe data fundamental pada javascript : number, string, boolean, null, undefined, object.
- Tipe data null biasanya diperoleh dalam kondisi normal dan sudah kita rencanakan.
- Tipe data undefined biasanya didapat dari hasil kesalahan program (error), kelalaian programmer, dan tidak direncanakan.
### Variabel
- Variable adalah container/tempat untuk menyimpan sebuah nilai.
- 3 hal yang dapat dilakukan pada variable
- 1.Membuat variabel dengan nama yang jelas dan menggambarkan tentang data tersebut.
- 2.Menyimpan dan mengupdate informasi/data yang disimpan
- 3.Mendapatkan/menampilan data yang tersimpan
- Mendefinisikan variable dengan let dan const. Gunakan const jika variable tidak dapat diubah nilainya
### Operator, Macam-macam Operator :
- Assignment Operator (=)
- Mathematical operator (+=)
- Increment (++) dan Decrement (—) : menambah atau mengurangi sebesar 1 nilai
- Arithmetic Opertator (+,-,*,/,%), Modulus(%) adalah hasil dari sisa bagi
- Comparison Operator (<,>,≤.≥,===,!==) hasilnya true atau false
- Logical Operator (AND(&&), OR(||), NOT(!)) hasilnya true atau false
### **5. JavaScript Conditional & Looping. 23 September 2022.**
### Conditional
- Conditional merupakan statement percabangan yang menggambarkan suatu kondisi
- Conditional digunakan saat dibutuhkan percabangan kasus. Komputer akan melakukan suatu tindakan jika suatu kondisi terpenuhi. Contoh : Jika hari ini tidak hujan, maka Bob pergi ke pasar, jika tidak maka Bob dirumah aja. Jika tidak terpenuhi, maka tidak akan dijalankan.
- Contoh conditional : IF Statement
```
  let lapar = true;
  if (lapar){
    console.log("Yuk Makan");
  };
```
- Contoh conditional : IF ELSE Statement
```
  let lapar = false;
  if (lapar){
    console.log("Yuk Makan");
  }else{
    console.log("tidak makan");
  }
```
- IF ELSE IF Statement : jika mempunyai berbagai kondisi
```
  let stoplight = 'yellow';
  
  if(stoplight === 'red'){
    console.log('stop!');
  }else if(stoplight === 'yellow'){
    console.log('slow down');
  }else if(stoplight === 'green'){
    console.log('Go!');
  }else{
    console.log('caution, unknown!');
  }
```
- Switch Case Conditional : untuk jika kondisi dan percabangan terlalu banyak
```
  switch (expression){
    case value_:
      statement_1;
      break;
    case value_2:
      statement_2;
      break;
    case value_3:
      statement_3;
      break;
    default:
      default_statement;
  }
```
### Looping
- Looping adalah statement yang mengulang sebuah intruksi hingga kondisi terpenuhi atau jika kondisi stop/berhenti tercapai
- For Loop merupakan instruksi pengulangan yang dapat kita berikan pada program yang kita kembangkan
- Gunakan for loop jika tahu seberapa banyak nilai pasti untuk pengulangannya
- For (inisialisasi; kondisi; post-expression)
- Inisialisasi : sebagai inisialisasi awal dari mana mulainya sebuah pengulangan. Kita memberikan nilai awal/default pada parameter ini
- Condition : For loop akan terus berjalan selama kondisi ini terpenuhi
- Post-expression (increment/decrement) : Iterasi yang digunakan untuk mengupdate variabel yang menjadi kontrol pada pengulangan
```
  let angka = 1;
  for(angka; angka<=10; angka++){
    console.log(angka)
  }
```
- Gunakan while loop jika kita tidak mengetahui jumlah pasti pengulangan
```
  let angka = 1;
  while(angka<=10){
    console.log(angka);
    angka++
  }
```
- Gunakan do while jika kita ingin setidaknya menjalankan pengulangan 1 kali sebelum dilakukan pengecekan kondisi
```
  let bensin = 9;
  do{
    console.log('nyalakan mesin!');
    bensin--;
 }while(bensin>0)
```



















































































