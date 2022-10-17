# Writing & Presentation Week 4 - Web Development Advance
## Rafid Ammar Adinegoro
## 10-14 Oktober 2022

### **1. Asynchronous Fetch & Async/Await.**
### Asynchronous 
- Asynchronous yang biasa dikenal juga dengan sebutan non-blocking mengizinkan komputer kita untuk memproses perintah lain sambil menunggu suatu proses lain yang sedang berlangsung. Artinya kita bisa melakukan lebih dari 1 proses sekaligus (multi-thread)
### Async/Await
- Selain menggunakan *callback* dan *promise*, kita juga bisa menggunakan *async/await* untuk menggunakan *asynchronous* pada JavaScript.
- Ada 2 kata kunci yang memiliki pengertian sebagai berikut:
1. async, mengubah *function synchronous* menjadi *asynchronous*.
2. await, menunda eksekusi hingga proses *asynchronous* selesai.
- Sebuah *async function* bisa tidak berisi *await* sama sekali atau lebih dari satu *await*. *Keyword await* hanya bisa digunakan didalam *async function*, jika digunakan di luar *async function* maka akan terjadi *error*. Contoh : 
```
  // async menggunakan keyword function
  async function tesAsyncAwait() {
    return "Fulfilled";
  }
  console.log(tesAsyncAwait());

  // async menggunakan arrow function
  const tesAsyncAwait = async () => {
    return "Fulfilled";
  };
  console.log(tesAsyncAwait());
```
- Await hanya bisa digunakan dalam async function dan await adalah keyword dalam async yang digunakan untuk menunda hingga proses asynchronous selesai. Contoh : 
```
  // Definisikan dahulu promise yang ingin digunakan
  let condition = true;
  let tesAsyncAwait = async (condition) => {
    if (condition) {
      return "Condition is fulfilled!";
    } else {
      throw "Condition is rejected!";
    }
  };


  // Membuat fungsi run menjadi asynchronous menggunakan async/await
  const run = async (condition) => {
    try {
      const message = await tesAsyncAwait(condition);
      console.log(message);  // Output: Condition is fulfilled!
      console.log("After condition is fulfilled"); // Output: After condition is fulfilled
    } catch (error) {
      console.log(error);
    }
  };

  run(true);
```
### Fetch
- Dalam JavaScript kita bisa mengirimkan *network request* dan juga bisa mengambil informasi data terbaru dari *server* jika dibutuhkan. Contoh *network request* yang biasa kita lakukan:
1. Mengirimkan data dari sebuah *form*.
2. Mengambil data untuk ditampilkan dalam *list/table*.
3. Mendapatkan notifikasi.
- Dalam melakukan *network request*, JavaScript memiliki metode bernama`fetch()`.
- Proses melakukan `fetch()` adalah salah satu proses *asynchronous* di JavaScript sehingga kita perlu menggunakan salah satu diantara *promise* atau *async/await*.
- Contoh request data dengan fetch() menggunakan promise :
```
  fetch("https://jsonplaceholder.typicode.com/posts")
    .then(function (response) {
      return response.json();
    })
    .then(function (post) {
      console.log(post);
    });
```
- Contoh request data dengan fetch() menggunakan async/await :
```
  const tesFetchAsync = async () => {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts");
    response = await response.json();
    console.log(response);
  };
  tesFetchAsync();
```
- Kita masih mengambil data dari sumber end-point yang sama dengan fetch() sebelumnya yang menggunakan promise sehingga hasilnya pun masih sama persis seperti sebelumnya.

### **2. Git & Github Lanjutan.**
- Langkah-langkah Kolaborasi Github :
1. Team lead membuat Organization (pada organization dapat membuat banyak repo)
2. Invite anggota tim dan jadikan owner
3. Create repository
4. Repo dibuat public
5. Buat branch bernama dev (main sebagai branch utama, dev sebagai development, pada tahap development pusat nya ada pada dev, ketika dev sudah selesai baru diisi ke main)
- Mengecek pull request
1. setiap ada pull request, team lead akan mengeceknya
2. jika pull request belum sesuai, bisa dikasih komen atau beri kabar anggota yang melakukan pull request
3. jika sudah sesuai, lakukan merge
- Hacktoberfest
1. Repo diberi label hacktoberfest
2. Setiap pull request yang di acc, diberi label hacktoberfest-accepted
- Tahap kolaborasi :
1. anggota melakukan clone pada repo yang sudah dibuat (1x aja) ; git clone https(code). git clone itu download trus jadi folder
2. bagi tugas pada anggota
3. sebelum ngoding, lakukan git pull untuk update kode terbaru
4. anggota membuat branch dari dev
5. lakukan pengerjaan dalam branch tersebut : 
    - git switch dev
    - git branch “nama-fitur”
    - git switch “nama-fitur”
6. jika fitur sudah selesai/butuh code dari dev, lakukan commit seperti biasa (git add ., git commit -m “fitur”)
7. sebelum push, lakukan git merge dev untuk menghindari conflict di github
8. jika ada conflict, bereskan semuanya
9. jika sudah aman, commit lalu push branch ke github (git push -u origin “nama-fitur”)
10. lakukan pull request untuk merge ke branch dev (pull request :  permintaan untuk menggambungkan branch yang kita buat ke branch dev), abis itu assign pull request ke team lead
11. tunggu pull request di acc oleh team lead

### **Responsive Web Design**
### Responsive Web Design (RWD)
- Responsive Web Design (RWD) bertujuan membuat desain website kita dapat diakses dalam device apapun
- Dalam membuat aplikasi ktia harus memikirkan user yang akan menggunakannya. Device yang umumnya digunakan adalah laptop/PC, smartphone, dan tablet
- Setiap developer website wajib menggunakan tools bawaan dari setiap browser yang memudahkan proses development website. Pada browser chrome biasa disebut dengan Chrome Dev Tools, dan tools ini dapat digunakan untuk RWD
- Akses Chrome Tools Dev : Ctrl + Shift + J
- Klik icon yang mengilustrasikan phone dan tablet
- Add viewport di HTML :
- <meta name=”viewport” content=”width=device=width, initial-scale=1.0”>
- add styling max-width: 100% pada img agar tidak ada overflow width pada img :
### Media Query
- Media Query digunakan untuk membuat beberapa styles tergantung pada jenis device
- Media Query yang biasa digunakan adalah min-width dan max-width. Contoh :
```
  @media screen and (max-width: 500px){
    body{
      background-color: aquamarine;
    }
  }
```
- Breakpoint adalah perubahan yang terjadi pada tampilan saat berganti device atau ukuran width
- Misalnya ada 3 tampilan berbeda untuk 3 jenis device, maka ada 3 breakpoint
- Gunakan range media query min dan max untuk menerapkan tampilan pada range ukuran device tertentu. Contoh :
```
  @media screen and (min-width: 500px) and (max-width: 700px){
    body{
      background-color: aquamarine;
    }
  }
```
- RWD dilakukan sesuai kebutuhan konten. Jika konten yang ditampilkan sudah tidak bisa diakses atau sulit dilihat pada width tertentu, sudah saatnya kamu menggunakan media query





















