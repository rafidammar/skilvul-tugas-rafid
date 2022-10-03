# Writing & Presentation Week 2 - Web Development Basic
## Rafid Ammar Adinegoro
## 26-30 September 2022

### **1. Scope dan Function.**
### Scope
- Scope adalah konsep dalam flow data variabel. Konsep yang dimaksud adalah menentukan suatu variabel bisa diakses pada scope tertentu atau tidak
- Analogi : **Kita semua bisa melihat bintang-bintang dilangit karena bumi bersifat global. Namun jika kamu tinggal di Bandung, kamu tidak akan bisa melihat monas yang berada dijakarta. Monas bersifat local yaitu hanya berada di Jakarta.**
- Blocks adalah code yang berada didalam curly braces{}. Conditional, function, dan looping mnggunakan blocks
- Global scope berarti variabel yang kita buat dapat diakses dimanapun dalam suatu file. Agar menjadi Global scope, suatu variabel harus dideklarasikan diluar Blocks
- Local scope berarti variabel nya dideklarasikan didalam blocks, maka hanya bisa didalam blocks itu saja
### Function
- Function adalah sebuah blok kode dalam sebuah grup untuk menyelesaikan 1 task/1 fitur. Fitur tersebut kemudian bisa kita gunakan kembali jika kita membutuhkannya
```
  function greet(){
    console.log(’Hello World’)
  } 
  greet() // memanggil function
```
- Parameter Function.
- Dengan parameter, function dapat menerima sebuah inputan data dan menggunakannya untuk melakukan task/tugas
- Contoh :
```
  function penambahan(a, b){
    return a + b;
  } // dimana (a, b) adalah parameter
```
- Argumen Function. 
- Argumen adalah nilai yang digunakan saat memanggil function. Jumlah argumen harus sama dengan jumlah parameternya. Jadi jika pada function terdapat 2 parameter. Saat kita memanggil function kita gunakan 2 nilai argumen
- Contoh :
```
  function penambahan(a, b){
    return a + b;
  }
  console.log(penambahan(5, 5)) // (5, 5) adalah agrumen
``` 
- Default Parameters bisa digunakan untuk memberi nilai default pada parameter. Ini juga bisa digunakan agar fungsi tidak error saat dipanggil tanpa argumen
- Contoh :
```
  function greet(name = “User”){
    return “Hello “ + name;
  }
  console.log(greet(”Rafid”)) // Output : “Hello Rafid”
  console.log(greet()) // Output : “Hello User” | User adalah default parameter
```
- Arrow Function adalah cara lain menuliskan function
- Contoh :
```
  const greeting = () ⇒ {
    return “Hello world”
  )
  
  const penambahan = (a. b) ⇒ {
  return a + b
  }
```
### **2. Data Type, Built in Prototypes, dan Method**
### Data Types
- Primitive :
1. String
2. Number
3. Boolean
4. Null
5. Undefined
6. BigInt
7. Symbol
- Non-Primitive :
1. Array
2. Object
- Operator **typeof** dapat digunakan untuk mengecek tipe data
### Properties & Method
- **Properties** adalah ciri-ciri. **Method** adalah built-in function. Tipe data di javascript memiliki properties dan method nya masing-masing.
- **String**
- ${} untuk menyisipkan variabel ke dalam sebuah string
- Contoh : 
```
  let hewan = “kancil”
  
  console.log(”ini adalah “ + hewan”)
  console.log(`ini adalah ${hewan}`)
```
- Contoh Properties pada string : .length = mengembalikan panjang dari sebuah string
```
  let hewan = “kancil”
  console.log(hewan.length) // 6
  console.log("kancil".length) // 6
```
- Contoh method pada string :
```
  .toUpperCase() // mengubah string ke huruf kapital semua
  console.log(hewan.toUpperCase()) // KANCIL
  .toLowerCase() // mengubah string ke huruf kecil semua
  .charAt(index) // mengembalikan karakter di index tertentu
  .includes(string) // cek apakah string berisi string tertentu, return true or false
  .split() // memisah string berdasarkan yg didalam () menjadi array
  .indexOf() // mengembalikan index pertama dimana suatu elemen dapat ditemukan di array
  let arr = ["rafid", "ammar", "adinegoro"]
  arr.indexOf("ammar") // 1
  .lastIndexOf() // mengembalikan index terakhir dimana suatu elemen dapat ditemukan di array
  dll
```
- **Number**
- Number bisa digunakan sebagai function, mengubah string atau value lain menjadi tipe data number, jika tidak bisa di konversi, akan mengembalikan NaN.
- Contoh :
```
  Number(value)
  Number("123") // 123
  Number(123) // 123
  Number(satu) // NaN
```
- Contoh method pada number :
```
   isNaN(value) // cek apakah NaN atau bukan
   .toString() // mengubah number jadi string
   .toFixed(value) // menentukan jumlah angka dibelakang koma
   Number.parseInt(value) // konversi menjadi integer
   Number.parseFloat(value) // konversi menjadi float
```
- **Math**
- Math merupakan built in object, bisa digunakan untuk mengolah data dan fungi matematika
- Contoh properies pada math :
```
  PI // angka PI
  Math.PI // 3.141592653589793
  dan nilai-nilai konstanta matematika lainnya
```
- Contoh method pada math :
```
  Math.abs(number) // merubah menjadi angka bulat
  Math.pow(number, power)
  Math.sqrt(number) // kuadrat
  Math.round(number) // menghilangkan koma
  Math.floor(number) // membulatkan kebawah
  Math.ceil(number) // membulatkan keatas
  Math.random(number) // angka acak
  dll
```
- **Object Prototypes**
- Object Prototypes adalah mekanisme dimana javascript object dapat menurunkan fiturnya, artinya kita bisa membuat method sendiri dengan .prototype.namaMethod menggunakan function yang kita buat.
- Contoh :
```
  String.prototype.reverse = function(){
    let s =""
    for(let i=String(this).length;i>0;i--){
      s = s + String(this)[i] 
    }
    return s
  }
  
  console.log(”hallo”.reverse()) // return “alloh” (ini method dari string)
  
  // atau bisa juga dengan :
  console.log(reverse(”hallo”)) //ini function dgn argumen string
```
- Membuat object menggunakan constructor. Contoh :
```
  function Kucing(nama, makanan){
    this.nama = nama
    this.makanan = makanan
  }
  const tom = new Kucing(”tom”, “ikan”)
  console.log(tom.nama) // memunculkan tom
```
### **3. DOM Introduction, Selecting Elements, & Transversing Elements**
### DOM (Document Object Model)
- Jadi, ketika halaman website kita diload, browser kita akan membuat Document Object Model dari halaman website kita.
- Dengan adanya DOM ini, JavaScript diberi akses untuk memanipulasi dan berinteraksi dengan halaman HTML, seperti:
1. Mengubah element HTML pada halaman website.
2. Mengubah attribute HTML pada halaman website.
3. Mengubah CSS style pada halaman website.
4. Menambah dan/atau menghapus element maupun attribute HTML.
5. Menambah HTML event (contoh: efek klik pada mouse, hover pada mouse, dan lain-lain) pada halaman website.
6. Berinteraksi dengan semua HTML event di website.
- Di HTML DOM, semua element HTML dari sebuah website dianggap sebagai objek. Dan sama seperti objek JavaScript pada umumnya, objek element HTML di HTML DOM juga mempunyai properti dan method atau yang lebih dikenal dengan istilah DOM Property dan DOM Method.
- Jadi untuk mengubah nilai properti dari element HTML, kita bisa menggunakan DOM Property dan untuk memanggil fungsi dari suatu element HTML, kita bisa menggunakan DOM Method.
- Contoh :
```
  // html
  <input id="umur" type="text" value="20" />
  // js
  let umur = document.getElementById("umur").value;
  console.log(umur); // Output: 20
```
- DOM Method lainnya :
- getElementById(id) : mengakses element HTML berdasarkan nilai `id`-nya
- getElementsByClassName(className) : mengakses element-element HTML berdasarkan nilai attribute class-nya.
Karena tulisannya Elements, dengan s, maka DOM method akan mengambil banyak element dan untuk mengakses elemen didalamnya harus menggunakan index. Contoh :
```
// html
  <h1 class="header">Hello, World!</h1>
  <p>Selamat Datang di Skilvul</p>
  <span class="header">Mari Belajar JavaScript</span>
  <ul class="list">
    <li class="item">satu</li>
    <li class="item">dua</li>
    <li class="item">tiga</li>
  </ul>
// js
let semuaClassHeader = document.getElementsByClassName("header");

console.log(semuaClassHeader); // Output: HTMLCollection(2) [h1.header, span.header]
console.log(semuaClassHeader[0]); // Output: <h1 class="header">Hello, World!</h1>
console.log(semuaClassHeader[1]); // Output: <span class="header">Mari Belajar JavaScript</span>

let list = document.getElementsByClassName("list")

console.log(list[0]) // Output : <ul class="list">...</ul>
console.log(list[0].children) // Output : HTML Collection(3) [li.item,li.item,li.item]
```
- getElementsByTagName(tag) : mengakses element-element HTML berdasarkan jenis tag-nya
- querySelectorAll(cssSelector) : mengakses element-element HTML berdasarkan CSS Selector-nya. Contoh :
```
// html
<h1 class="header">Hello, World!</h1>
<p id="header2">Selamat Datang di Skilvul</p>
<span class="header">Mari Belajar JavaScript</span>
// js
let h1ClassHeader = document.querySelectorAll('h1.header');

console.log(h1ClassHeader); // Output: NodeList [h1.header]
console.log(h1ClassHeader[0]); // Output: <h1 class="header">Hello, World!</h1>

let idHeader2 = document.querySelectorAll('#header2');

console.log(idHeader2); // Output: NodeList [p#header2]
console.log(idHeader2[0]); // Output: <p id="header2">Selamat Datang di Skilvul</p>
```
- Perbedaan querySelector dan querySelectorAll. Contoh :
```
//html
<ul class="list">
	<li class="item">satu</li>
	<li class="item">dua</li>
	<li class="item">tiga</li>
</ul>

// js
let list = document.querySelector(".list")
console.log(list) // <ul class="list">...</ul>
let item = document.querySelector(".item")
console.log(item) // <li class="item">satu</li>
let itemAll = document.querySelector(".item")
console.log(itemAll) // NodeList(3) [li.item,li.item,li.item]
```
- HTML Collection mirip array tapi bukan array, jadi tidak bisa menggunakan method-method array seperti push(), pop(), dan join()
- Method pada  HTML Collection : length dan item(). Contoh :
```
// html
<ul class="list">
	<li class="item">satu</li>
	<li class="item">dua</li>
	<li class="item">tiga</li>
</ul>

// js
let items = getElementsByClassName(”item”)
    
console.log(items.length) // Output : 3
console.log(items.item(1) // Output : <li class="item">dua</li>
```
- Perbedaan HTML Collection dan Nodelist :
1. HTML Collection adalah document elements, Nodelist adalah document nodes
2. HTML Collection adalah live collection, Nodelist static collection
3. Jadi HTML Collection bagus untuk akses, nodelist bagus untuk manipulasi
- DOM Method lainnya (ke atas dan ke samping) :
1. Method parentElement untuk akses parentnya.
2. Method closest() untuk akses orang tua terjauhnya
3. Method previousElementSibling untuk akses saudara sebelumnya
4. Method nextElementSibling untuk akses saudara setelahnya
- Contoh :
```
// html
<ul class="list">
	<li class="item">satu</li>
	<li class="item">dua</li>
	<li class="item">tiga</li>
</ul>
    
// js
let items = getElementsByClassName(”item”)
    
console.log(items.parentElement) // Output : <ul class="list">…</ul>
console.log(items.closest(”body”) // Output : <body …></body>
console.log(items.closest(.list) // Output : <body …></body>
console.log(items.previousElementSibling) // Output : null
console.log(items.nextElementSibiling) // Output : <li class="item">dua</li>
```
### **4. DOM : Manipulating Elements & Manipulating Styles**
- Memberikan konten HTML. Contoh :
``` 
// html
<div id="app"></div>
    
// js
let app = document.getElementById("app")
app.innerHTML = "Hallo”
```
- Membuat element. Contoh :
```
// js
let p = document.createElement("p")
p.innerText = "ini adalah paragraf”
```
- Menambahkan child(element) kedalam parent
```
app.append(p)

let p2 = document.createElement("p")
p2.innerText = "paragraf ke-2”

app.appendChild(p2)
```
- append vs appendChild
- appendChild ga bisa input data string. Contoh :
```
app.append("menggunakan append")

// app.appendChild("appendChild”) // error
```
- Remove element
```
<div id="end">

let end = document.getElementById("end")

end.remove()
```
- Attribute
```
<div class="container">
  <a href="[google.com](http://google.com/)" class="link">Google</a>
</div>

let link = document.getElementsByClassName("link")[0]

console.log(link.attributes) // [] list attribute
console.log(link.getAttribute("href")); // ambil isi attribute

link.setAttribute("id", "google") // add attribute
```
- Memberikan style
```
link.style.color = "black”

link.style.border = "1px solid black”

link.style.padding = "5px 20px”

link.style.backgroundColor = "aqua”

link.style.removeProperty("border") // menghapus style property
```
- Mendapatkan style dari element
```
// html
<div id="tess"></div>

// js
let tess = document.getElementById("tess")
let tessStyle = getComputedStyle(tess)

console.log(tessStyle.height)
```
- Class
```
<div class="container">
  <a href="[google.com](http://google.com/)" class="link">Google</a>
</div>

let container = document.getElementsByClassName("container")[0]

console.log(container.classList); // [] list of class

container.classList.add("home") // menambahnkan class
container.classList.remove("container") // menghapus class
```
### **5. DOM : DOM Events & Forms**
- Event : kegiatan.interaksi yang terjadi pada website
- Macam-macam events :
1. click
2. submit
3. focus
4. blur
5. hover
6. change
7. scroll
- 3 Cara memberikan event:
1. di HTML Attribute
2. Event property
3. addEventListener()
- Event onclick : Kegiatan yang akan dilakukan ketika di click
- Cara 1 memberikan event :
```
<h1 onclick="alert('selamat datang')">Hallo</h1>
```
- Cara 2 :
```
// html
<p id="paragraf">click me</p>

// js
let paragraf = document.getElementById("paragraf")

paragraf.onclick = function () {
  alert("ini dari paragraf")
}

// atau

function tampilkanAlert () {
  alert("ini alert")
}

paragraf.onclick = tampilkanAlert
```
- Cara 3 :
```
// html
<button id="btn">klik saya</button>

// js
let button = document.getElementById("btn")

button.addEventListener("click",  () {
  alert("ini dari button")
})

// atau

function tampilkanAlert () {
  alert("ini alert")
}

button.addEventListener("click", tampilkanAlert)
```
- Membuat counter
```
div>
	<button id="decrement">-</button>
	<span id="counter">0</span>
	<button id="increment">+</button>
</div>

// js 

let btnDecrement = document.getElementById("decrement")
let btnIncrement = document.getElementById("increment")
let counter = document.getElementById("counter")

let angka = 0

btnIncrement.addEventListener("click", function() {
  angka = angka + 1
  counter.innerText = angka
  // console.log(angka)
  // console.log("increment");
})

btnDecrement.addEventListener("click", function() {
  angka--
  counter.innerText = angka
})
```
- Membuat Form
```
// html
<div class="container">
	<form id="sign-in">
        <h1>Sign In</h1>

        <div class="field">
          <label for="username">username</label>
          <input type="text" id="username" name="username" />
        </div>

        <div class="field">
          <label for="password">password</label>
          <input type="text" id="password" name="password" />
        </div>

        <button type="submit">login</button>
  </form>
</div

// js
let loginForm = document.querySelector("#sign-in")
let inputUsername = document.querySelector('#username')
let inputPassword = document.querySelector('#password')

let user = {
  username: "auzan",
  password: "123"
}

loginForm.addEventListener("submit", (event) => {
  event.preventDefault()

  let userLogin = {
    username: inputUsername.value,
    password: inputPassword.value
  }

  console.log(userLogin);

  let login = userLogin.username == user.username && 
              userLogin.password == user.password;

  if (login) {
    console.log("selamat anda berhasil login")
  } else {
    console.log("username dan password anda salah");
  }
    
  // Membersihkan form
  // cara 1
  loginForm.reset()

  // cara 2
  // inputUsername.value = ""
  // inputPassword.value = ""

})
```




























































































































































