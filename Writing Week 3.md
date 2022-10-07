# Writing & Presentation Week 3 - Web Development Advance
## Rafid Ammar Adinegoro
## 03-07 Oktober 2022

### **1. Array.**
### Array
- Array adalah tipe data list order yang dapat menyimpan tipe data apapun di dalamnya. Array dapat menyimpan tipe data String, Number, Boolean, dan lainnya. Contoh :
```
  let productTeam = ["Product Manager", "Front End Developer", "Back End Developer"]
  console.log(productTeam) 
  // Output : (3) ['Product Manager', 'Front End Developer', 'Back End Developer']
```
- Array pada javascript dihitung dari index data ke-0. Data pertama adalah index ke-0. Contoh :
```
  let productTeam = ["Product Manager", "Front End Developer", "Back End Developer"];
  console.log(productTeam[0]) // Output : “Product Manager”
  console.log(productTeam[1]) // Output : "Front End Developer"
```
### Update Array
```
  let productTeam = ["Product Manager", "Front End Developer", "Back End Developer"];
  productTeam[0] = “Product Designer”
  console.log(productTeam[0]) // Output : “Product Designer”
```
### Const in Array
- Jika menggunakan let, kita dapat mengubah array dengan array baru dan konten nilai yang ada di dalam array dengan nilai lain
- Const tidak bisa melakukan update data. Namun pada Array kita dapat melakukan update konten nilai di dalam array (mutable). Harus masukin index
- Yang tidak bisa adalah mengubah array dengan array yang baru jika menggunakan const
- Contoh :
```
    const cars = ["tesla", "honda", "toyota"]; 
    cars = ["bmw", "ford", "mercedes"];    // error
    cars[2] = “nissan” atau [“nissan”] // success
```
### Array Properties
- Array memiliki 5 properties yang sering digunakan yaitu constructor, length, index, input, dan prototype
- .length akan mengembalikan nilai dari jumlah panjang data suatu array. Contoh :
```
  let cars = ["tesla", "honda", "toyota"];
  console.log(cars.length) // Output : 3
```
### Array Method
- Array memiliki method atau biasa disebut built-in methods. Kita tidak perlu
 membuat function lagi jika method yang kita butuhkan sudah tersedia. Contoh :
- .push() adalah method untuk menambahkan item array pada urutan yang paling akhir. Contoh :
```
    let cars = ["tesla", "honda", "toyota"];
    cars.push(”ford”)
    console.log(cars) // Output : ["tesla", "honda", "toyota",”ford”]
```
- .pop() adalah method yang menghapus item array index terakhir. Contoh :
```
    cars.push()
    console.log(cars) // Output : ["tesla", "honda", "toyota"]
```
- .shift() adalah method untuk menghapus item array index pertama. Contoh :
```
    cars.shift()
    console.log(cars) // Output : ["honda", "toyota"]
```
- .unshift() adalah method untuk menambahkan item array index pertama. Contoh :
```
    cars.shift(”mercedes”)
    console.log(cars) // Output : [”mercedes”, "honda", "toyota"]
```
- .sort() adalah method untuk mengurutkan secara Ascending atau Descending Alphanumeric. Contoh :
```
  const numbers = [1,5,6,7,4]
  numbers.sort()
  console.log(numbers) // Output : [1,4,5,6,7]
```
### Looping pada array
- Array memiliki built in methods untuk melakukan looping yaitu .map() dan .forEach()
- **.forEach()** adalah method untuk melakukan looping pada setiap elemen array. Contoh :
```
  const cars = ["tesla", "honda", "toyota"];
  cars.forEach(element ⇒ {
         console.log(element)
    }) // Output : “tesla”, “honda”, “nissan”
```
- **.map()** melakukan perulangan dengan membuat array baru
```
  let arr = [1,2,3,4,5]
  let doubled = arr.map(num⇒ {
    return num * 2
  })
  console.log(doubled) // Output : [2,4,6,8,10]
```
- Perbedaannya adalah .forEach() tidak dapat membuat array baru. Jadi gunakan .forEach() jika hanya memerlukan looping untuk menampilkan saja atau menyimpan ke database. Gunakan .map() jika akan melakukan operasi pada array seperti yang dapat mengubah nilai array sebelumnya

### **2. Javascript Object.**
### Object 
- Pada programming, object adalah sebuah tipe data pada variabel yang menyimpan **properti** dan **fungsi (method**
- **Properti** adalah data lengkap dari sebuah object.
- **Method** adalah action dari sebuah object. Apa saja yang dapat dilakukan dari suatu object.
- Contoh : Misalkan objek dianalogikan seperti laptop. Laptop ini memiliki properti seperti warna, merk, jenis processor, dll. Kemudian methodnya adalah menyalakan laptop, mematikan laptop, membuka aplikasi, dll
- Sama seperti array, didalam object kita dapat menyimpan properti dengan tipe data apapun
- Object dapat di assign pada variabel. Contoh :
```
  let person = {}; // empty object
  let person = {  // object dengan property
  name: “John Doe”,
  age: 25,
  isVerified: true,
  } 
  
  // mengakses seluruh objek
  console.log(person) // Output : {name: “John Doe”, age: 25, isVerified: true}
  console.log(person.name) // Output : “John Doe”
```
- Object dapat mengupdate value dari key yang sudah tersedia
- Object dapat menambahkan key dan value baru
- Contoh :
```
  let person = {
    name: “John Doe”,
    age: 25,
    isVerified: true,
  }
  people.age = 27
  people.address = “Cambridge, UK”
  
  console.log(people) // Output : {name: “John Doe”, age: 27, isVerified: true, address: “Cambridge, UK”}
```
- Jika menggunakan const pada variabel object. Kita tidak bisa mengganti seluruh data dengan object yang baru.
- delete operator dapat digunakan untuk menghapus properti dari object. Contoh :
- delete people.age;
- Jika value yang kita masukkan pada property itu berupa function, maka itu disebut method. Contoh method :
```
  const greeting = {
    welcome: function(){
        return “Halo selamat datang”
        }
        afterTransaction: function(){
        return “Terima kasih sudah membeli produk kami”
        }
    }
    console.log(greeting.welcome()) // Output : “Halo selamat datang”
```
- Nested Object : object didalam object. Contoh :
```
const news = {
    title: “Impact Byte”
    desc: “Lorem Ipsum”
    author: {
        people: {
            name: “Rafid”
            age: 25
            }
        }
    }
    console.log(news.author.people.name) // Output: Rafid
```
- Passed by reference : mengubah data yang ada pada object melalui sebuah function dan memasukkan object sebagai parameter function. Contoh :
```
  let number = {
      originA: 2,
      originB: 3,
  }

  function changeData (obj) {
    obj.originA = 4
    obj,originB = 6 
  }
    
  changeData(number)
  console.log(number.originA) // 4 
  console.log(number.originB) // 6 
```
- Looping untuk menampilkan seluruh properti pada objek. Contoh :
```
  const news = {
    title: “Impact Byte”
    desc: “Lorem Ipsum”
    author: {
      people: {
      name: “Rafid”
      age: 25
      }
    }
  }
  for(let data in news){
    console.log(news[data])
  }
  // “Impact Byte” 
  // “Lorem Ipsum”
  // people {…}
    
  for(let author in news.author.people){
    console.log(news.author.people[author]
  }
    
  // “Rafid”
  // 25
```
- Array of object : Object didalam array
```
  let student = [
     name: “Rafid”,
     age: 21,
     isVerified: true,
  },
  {
     name: “Fathur”,
     age: 22,
     isVerified: true,
  },
  {
     name: “Adit”,
     age: 25,
     isVerified: false,
  }
]
  // forEach jika objek dalam array
  students.forEach((listStudents) ⇒ {
    console.log(listStudent)
  })
```
### **3. Rekursif**
### Rekursif
- Rekursif adalah function yang memanggil dirinya sendiri sampai kondisi tertentu
- Rekursif kebanyakan digunakan untuk case yang berhubungan dengan matematika
```
  function recursive(){
    if(condition){
       // stop calling itself
    } else {
       recursive()
    }
  }
```
- Fungsi rekursif selalu memiliki kondisi yang menyatakan kapan fungsi tersebut berhenti.
- Fungsi rekursif selalu memanggil dirinya sendiri sambil mengurangi atau memecahkan data masukan setiap panggilannya. Hal ini penting diingat, karena tujuan utama dari rekursif ialah memecahkan masalah dengan mengurangi masalah tersebut menjadi masalah-masalah kecil.
- Contoh fungsi rekursif :
```
  function countDown(fromNumber){
    console.log(fromNumber)
    let nextNumber = fromNumber - 1
      if(nextNumber>0){
        countDown(nextNumber)
      }        
    }
  countDown(3)
  // Output : 
  3
  2
  1
```
- Contoh rekursif mencari hasil dari nilai pangkat :
```
  function pow(x, n){
    if(n == 1){
       return x;
    } else {
        return x * pow(x, n-1)
    }
  }
  console.log(pow(2, 3))
```
### **4. Asynchronous**
### Synchronous
- Synchronous adalah saat kita mengeksekusi perintah satu persatu dan berurutan. Ketika ada 1 perintah masuk maka dia akan dieksekusi terlebih dahulu. Jika perintah belum selesai dan sudah ada perintah baru maka perintah kedua (yang baru) akan mengantri sampai perintah 1 selesai. Proses seperti ini disebut blocking dan membuat perintah kita tereksekusi dengan lambat. 
### Asynchronous
- Asynchronous yang biasa dikenal juga dengan sebutan non-blocking mengizinkan komputer kita untuk memproses perintah lain sambil menunggu suatu proses lain yang sedang berlangsung. Artinya kita bisa melakukan lebih dari 1 proses sekaligus (multi-thread)
- Menjalankan *Asynchronous* pada JavaScript
1. `setTimeout(function, milliseconds)` digunakan untuk simulasi pemanggilan kembali proses asynchronous yang sedang/sudah selesai dijalankan. Pemanggilan hanya dilakukan 1 kali.
2. `setInterval(function, milliseconds)` digunakan untuk simulasi pemanggilan proses asynchronous yang sedang/sudah dijalankan dalam interval waktu tertentu. Pemanggilan dilakukan berkali-kali sesuai interval waktu yang ditentukan.
- Contoh asynchronous menggunakan setTimeout() :
```
  setTimeout(() => {
  console.log("Cuci baju"); // proses asynchronous
  }, 1000);
  
  console.log("Menyapu");
  console.log("Mengepel");
  console.log("Memasak");

  // 1000 ms = 1 second

  // Output:
  // Menyapu
  // Mengepel
  // Memasak
  // Cuci baju
```
- Contoh asynchronous menggunakan setInterval() :
```
  setInterval(() => {
  console.log("Cuci baju"); // proses asynchronous
  }, 3000);
  console.log("Menyapu");
  console.log("Mengepel");
  console.log("Memasak");

  // 3000 ms = 3 second

  // Output:
  // Menyapu
  // Mengepel
  // Memasak
  // Cuci baju (x time)

  // Cuci baju akan dijalankan setiap 3 detik sekali
```
- Permasalahan bisa terjadi saat menggunakan asynchronous, ada satu perintah yang bergantung pada output eksekusi asynchronous sebelumnya.  Untuk mengatasi permasalahan tersebut, kita dapat menggunakan :
1. Callback
2. Promises
3. Async / Await
### Callback
- Callback adalah sebuah function, namun bedanya, callback adalah function yang dijadikan sebagai argumen
- Analogi dari konsep callback adalah seperti ketika kita membeli dari seorang penjual rujak untuk membeli rujak, sambil penjual membuat rujaknya, kita membeli ketoprak. Ketika penjual rujak sudah selesai, penjual rujak akan memanggil kita kembali (callback) untuk memberitahu kita bahwa rujaknya sudah siap dan harus kita bayar.
- Contoh aynchronous menggunakan callback :
```
  function proses1() {
    console.log("proses 1 selesai dijalankan");
  }

  function proses2(callback) {
    setTimeout(function () {
      console.log("proses 2 selesai dijalankan");
      callback();
    }, 100);
  }

  function proses3() {
    console.log("proses 3 selesai dijalankan");
  }
  proses1();
  proses2(proses3);

  /*
  Hasil Output
  proses1 selesai dijalankan
  proses2 selesai dijalankan
  proses3 selesai dijalankan
  */
```
- Callback function
- Kita dapat memanggil *callback* pada sebuah *function* dengan cara memanggilnya ke dalam parameter dan digunakan di dalam *function*. Contoh :
```
  function greeting(name) {
    console.log(`Halo ${name}, selamat datang di Skilvul!`);
  }

  function introduction(firstName, lastName, callback) {
    const fullName = `${firstName} ${lastName}`;

    callback(fullName);
  }

  introduction("Miftah", "Faris", greeting); // Halo Miftah Faris, selamat datang di Skilvul !
```
### Promise Object
- Object Promise berisi producing code (yang memerlukan waktu) dan memanggil ke consuming code (yang harus nunggu hasil)
- Analogi dari sebuah *promise* di JavaScript itu sama seperti kita saat mengambil suatu data baik itu dari *database* maupun *Request API*. Akan ada 3 kondisi yaitu data sedang diproses, data berhasil didapatkan, atau data gagal didapatkan.
- Pada *promise* analogi di atas bisa diartikan seperti:
1. *pending*, jika data sedang diproses.
2. *fulfilled*, jika data telah berhasil didapatkan.
3. *rejected*, jika data gagal didapatkan.
- Contoh promise in variabel : 
```
  let nontonPromise = new Promise((resolve, reject) => {
    if(true){
      resolve("nonton terpenuhi")
    }
    reject("gagal")
  })

  // eksekusi proses. ..
  console.log("A")


  // Karena promise butuh waktu, jadi di pending dulu
  nontonPromise
    .then((result) => {   // .then() untuk menangkap resolve
      console.log(result)
      return `${result} bareng doi`
    })
    .then((result) => {  // hasil return masuk ke result disini lalu di console
      console.log(result)
    })
    .catch((err) => {    // .catch() untuk menangkap reject
    console.log(err)
    })

  console.log("C") 

  // Output :
  A
  C
  nonton terpenuhi
  nonton terpenuhi bareng doi
```
- Contoh promise in function
```
  let nonton = () => {
    return new Promise((resolve, reject) => { // function nonton mengembalikan objek Promise
      if (kondisi == "jalan") {
        resolve("nonton terpenuhi")
      }
      reject("batal nonton")
    })
  }
  nonton("jalan")
  .then(result => {
    console.log(result)
  })
  .then(err => {
    console.log(err)
  })

  // Output :
  nonton terpenuhi
```
### **5. Web Storage**
- Web Storage adalah tempat untuk menyimpan data pada browser
- Ada beberapa cara untuk menyimpan data pengguna seperti riwayat pencarian, preferensi user(darkmode), setting(translate), score, posisi video, dll ke lokal (*browser*) menggunakan W*eb Storage* seperti *cookies*, *local storage*, dan *session storage*.
### Cookies
- Cookies adalah data kecil yang dikirim dari situs web dan disimpan di komputer kita oleh web browser saat kita menjelajah (maks 4 KB)
- Biasanya data yang disimpan di  cookies adalah access token pengguna saat login atau data pencarian saat melakukan pencarian pada situs web tertentu.
### Local Storage & Session Storage 
- Dengan memanfaatkan local storage dan session storage, kita dapat menyimpan data lebih besar yaitu 5MB per page tanpa mempengaruhi kinerja situs web. Perbedaan diantara keduanya adalah localStorage menyimpan data tanpa ada kadaluarsa, sessionStorage menyimpan data pada 1 sesi (data hilang ketika browser ditutup)
- Local storage memiliki karakteristik sebagai berikut:
1. Menyimpan data tanpa tanggal kadaluarsa.
2. Data tidak akan dihapus ketika web browser ditutup dan akan tersedia seterusnya selama kita tidak menghapus data local storage pada web browser.
3. Dapat menyimpan data hingga 5MB.
4. Hanya dapat menyimpan data *string*.
- Menyimpan data pada local storage menggunakan method setItem(”key”, value) yang membutuhkan 2 parameter. Contoh : 
```
  // html 
  <form>
      <input type="text" id="searchkey" name="searchkey" placeholder="Search Something"><br>
      <input type="submit" value="Search" onclick="onSearch()">
     </form

  // js
  var searchList = [];
  function onSearch() {
    var searchValue = document.getElementById('searchkey').value;
    searchList.push(searchValue) // memasukan kata pencarian ke dalam array

    var searchListString = JSON.stringify(searchList); // mengubah array menjadi string
    localStorage.setItem('searchKey', searchListString); // menyimpan pencarian dengan key 'searchKey'
  }
  // key "searchKey" dengan value "skilvul" sudah tersimpan di local storage
```
- Mengambil data yang telah tersimpan pada local storage dengan method getItem() yang membutuhkan 1 parameter. setItem(”key”). Contoh :
```
  // html
  <h4>Riwayat Pencarian</h4>
  <div id="search-history"></div>

  // js
  var searchList = JSON.parse(localStorage.getItem('searchKey')) || []; // jika searchKey bernilai undefined, maka set searchList sebagai empty array
  ... // json.parse() untuk mengembalikan string menjadi array kembali
  ...

  function getSearchHistory() {
      var list = '';
      for (var i = 0; i < searchList.length; i++) {
          list += `<div>${searchList[i]}</div>`;
      }
      document.getElementById('search-history').innerHTML = list;
  }

  // memanggil fungsi getSearchHistory
  if (searchList.length > 0) {  // Jika panjang array searchList > 0
        getSearchHistory(); // panggil fungsi getSearchHistory
  }
```
- Menghapus data menggunakan  method removeItem() yang  membutuhkan satu parameter yaitu removeItem(”key”) atau dengan .clear() untuk menghapus semua key. Contoh : 
```
  // html
    ...
    ...
    <h4>Riwayat Pencarian</h4>
    <div id="search-history"></div>
    <button onclick="clearSearchHistory()" style="margin-top: 20px;">Hapus Riwayat</button>

  // js
  function clearSearchHistory() {
    localStorage.removeItem("searchKey"); // menghapus data pada localStorage dengan key "searchKey"
    document.getElementById('search-history').innerHTML = ""; // mengosongkan riwayat pencarian
  }
```
- Membuat **To Do List**
```
  // html
  <form action="" class="container">
        <input type="text" placeholder="Hari ini saya akan..." />
        <ul id="list-container"></ul>
  </form>
  <button id="toggle">Toggle</button>

  // js
  // init penampung list dari todo
  const todos = [];

  if (localStorage.getItem("todo")) {
    const todoStore = JSON.parse(localStorage.getItem("todo"));

    todoStore.map((todo) => {
      const li = document.createElement("li");
      li.innerText = todo;

      const container = document.querySelector("#list-container");
      return container.appendChild(li);
    });
  }

  document.querySelector("form").addEventListener("submit", (ev) => {
    ev.preventDefault();
    const userInput = document.querySelector("input").value;

    const li = document.createElement("li");
    li.innerText = userInput;

    todos.push(userInput);

    localStorage.setItem("todo", JSON.stringify(todos));

    const container = document.querySelector("#list-container");
    container.appendChild(li);
  });

  /* 
    Notes:
    JSON.parse -> ubah string ke object 
    JSON.stringify -> ubah apapun ke string JSON
  */
```
- Membuat fitur **darkmode**
```
  // html
  <button id="toggle">Toggle</button>

  // js
  // ==================== check ketika pertama kali website di buka, apakah ada key: theme dan value: dark di storage
  if (localStorage.getItem("theme") === "dark") {
    document.body.classList.add("dark");
  } else {
    document.body.classList.remove("dark");
  }

  document.getElementById("toggle").onclick = () => {
    if (localStorage.getItem("theme")) {
      localStorage.removeItem("theme");
      document.body.classList.remove("dark");
    } else {
      localStorage.setItem("theme", "dark");
      document.body.classList.add("dark");
    }
  };
```






















































































