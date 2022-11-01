# Writing & Presentation Week 6 - Front-end Bootcamp
## Rafid Ammar Adinegoro
## 24-28 Oktober 2022

### **1. React JS**
- React JS adalah framework view library Javascript untuk membuat tampilan (user interface) pada website
- Dengan node JS, Javascript dapat dijalankan diluar web browser
- React JS is Fast
- React JS membuat aplikasi front-end menjadi lebih cepat walaupun harus menghandle berbagai data
- React JS is Modular
- Kita dapat menerapkan konsep Modular javascript pada React JS. React JS membagi 1 tampilang pada website menjadi komponen-komponen kecil
- React JS is Scalable
- React JS dapat digunakan pada aplikasi berskala kecil hingga besar dan kompleks
- Sifat React JS : Declarative, Component-Based, Learn Once, Write Anywhere
### Tahapan membuat react project :
1. npm create vite@latest nama-folder --template react
2. cd nama-folder
3. npm install
4. npm run dev
- jsx adalah file extension dari React
- Sebelum di tampilkan, jsx perlu dicompile terlebih dahulu untuk menjadi Javascript.
### Component
- Component membagi UI dalam satuan-satuan kecil. Maka dalam 1 pada ada beberapa component. Contohnya component navbar, component form, component text title, dll
- Nama folder, file dan function component harus menggunakan huruf besar diawal dan kata selanjutnya
- Pada tiap component terdapat 1 atau lebih file .jsx, kemudian component jsx tersebut dipanggil pada App.jsx
- kemudian lakukan styling pada App.css
- Contoh file HelloWorld.jsx dengan fungsi HelloWorld:
```
  import React from ‘react’
  function HelloWorld(){
    return(
      <h1>Hello World</h1> 
    )
  }
   export default HelloWorld
```
Contoh file App.jsx :
```
  import React from ‘react’
  import HelloWorld from ‘./HelloWorld’

  function App(){
    return(
      <>
        <Hello World /> 
     </> 
    )
  }

  export default App
```
- Setiap JSX hanya bisa memiliki 1 parent element. Solusi :
- Gunakan tag element <div> atau <></> sebagai parent dari element lain pada komponen
- Virtual DOM
- React JS mempunyai fitur virtual DOM. Virtual DOM adalah duplikasi dari real DOM
- React JS hanya akan melakukan render ulang data pada komponen yang di update, tidak perlu melakukan render pada seluruh page, ini lah yang membuat React JS lebih cepat dalam performance
- Pada jsx atribut class menggunakan className
- Gunakan curly braces untuk menggunakan syntax Javascript pada jsx
- Contoh : 
```
  <h1>{2 + 3}</h1>
  <h1>{’Rafid Ammar’.toUpperCase()}</h1>
```
- Gunakan curly braces juga untuk akses variabel pada jsx
- Contoh :
```
const name = ‘Rafid Ammar’
return(
  <div>
    <h1>{name.toUpperCase()}</h1>
  </div>
)
```
Event in jsx. Contoh :
```
  const onClickFunction = () ⇒{
    alert(’You clicked image’)
  }
  return(
    <img onClick={onClickFunction} />
  )
```
- .map pada jsx. Contoh :
```
  function HelloWorld(){
    const numbers = [1, 2, 3, 4, 5]
    const listItems = numbers.map((number) ⇒{
    return(
      <ul>
        <li>{number}</li>
      </ul>
    )
    }
    
    return(
      <div>
        {listItems}
      </div>
    )
  }
    
```
### **2. React JS State, Props, dan Hooks**
- props dan state adalah javascript objects untuk menyimpan data di react. Kemudian ketika ada perubahan, akan di render.
- props digunakan untuk komunikasi(pengiriman data) dari komponen parent sama child.
- props mirip seperti parameter di function (mengirim sesuatu untuk di tangkap di function), yang dikirim lewat state.
- useState bisa digunakan untuk menyimpan data yang data nya berubah, mirip dengan inisialisasi variabel
- Stateless Component berarti tidak memiliki state. Stateful Component berarti memiliki state
### Hooks
- Inti dari Hooks, adalah untuk memudahkan penggunaan functional
components agar bisa menggunakan state, dan lifecycle lainnya.
- State ( setState ) dan lifecycle ( componentDidMount,
componentDidUpdate ) hanya bisa digunakan di class component,
namun dengan hooks, kita bisa menggunakannya di functional
component.
- Functional components akan melakukan “hooks” terhadap hal hal yang hanya ada di class agar bisa digunakan di functional components dengan mudah
- Hooks yang sering digunakan, adalah useState, dan useEffect, dua hal
ini sama dengan state, dan lifecycle di class yang biasa kita sering
gunakan
- Contoh penggunaan UseState Hooks :
```
  import {useState} from "react”
  const [name, setName] = useState("Rafid")
  <p>Halo, saya {nama}</p>
  <button onClick ={setNama(”Ammar”)}> Ubah </button>
```
- Contoh array dalam useState :
```
  const [pengalaman, setPengalaman] = useState([])
  <div>
    {pengalaman.map((item) ⇒ {
      return <li>{item}</li>
    })}
    <input type =”text” onChange={(evt) ⇒ setKota(evt.target.value)} /> 
    <input type = ”text” onChange={(evt) ⇒ (pengalamNow = evt.target.value)} /> 
    <button onClick ={() ⇒ setPengalaman([ … pengalaman, pengalamanNow])}>Add </button>
  </div>
```
- UseState, biasanya akan digunakan saat kamu menyimpan data suatu
form yang nantinya akan dipost ke api untuk di proses.
- Saat melakukan call api, kita bisa menyimpan data hasil get dari api tersebut kedalam state menggunakan UuseState
- UseEffect
- UseEffect adalah hooks yang bisa digunakan untuk menggunakan lifecycle pada functional component dengan mudah
- LifeCycle
- LifeCycle bisa dianggap seperti lingkaran kehidupan selama 24 jam mulai dari bangun tidur hingga tidur lagi
- LifeCycle pada hooks hanya menggunakan UseEffect yang menyatukan componentDidMount, componentDidUpdate, dan componentWilUnmount
- Penggunaan useEffect, bisa dimasukan sebelum melakukan render,
useEffect sendiri biasanya ditempatkan dibawah useState.
- Nantinya, apa yang kita tuliskan dalam useEffect akan dijalankan setiap
component baru di mount ( componentDidMount ), terjadi perubahan (
componentDidUpdate ), dan pada saat component akan ditinggalkan (
componentWillUnmount ).
- Contoh useEffect :
```
  import {useState} from "react"

  const Counter = () => {
      // let count = 0
      const [count, setCount] = useState(0)

      const increment = () => {
          setCount(count+1)
          //count += 1
          console.log(count)
      }

      const decrement = () => {
          setCount(count-1)
          //count -= 1
          console.log(count)
      }

      return(
          <>
              <h2>Simple Counter</h2>
              <button onClick={decrement}>-</button>
              <span>{count}</span>
              <button onClick={increment}>+</button>
          </>
      )
  }
  export default Counter
```








