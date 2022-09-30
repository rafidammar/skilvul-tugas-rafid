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

































































































































































