# Writing & Presentation Week 8 - Front-end Bootcamp Week 4
## Rafid Ammar Adinegoro
## 7 - 11 November 2022

### **1. React Context.**
- React Context dapat digunakan untuk menghindari props drilling, context dapat provide a way to pass data through the component tree without having to pass props down manually at every level
- Pertama buat component context untuk memprovide semua component lain pada apps
- Context bisa ngeshare/simpan data dan dianggap global, seperti autentikasi, tema, atau bahasa yg dipilih
- Context juga bisa menyimpan banyak data dengan object
- Context juga bisa lebih dari 1 context
- Context dapat digunakan untuk menyimpan data atau state secara global
- keranjang app React Context dengan useState :
- dengan context, contextnya akan menyimpan jumlah keranjang yang disimpan di KeranjangCount ketika counter ditambah
- **Contoh :**
- **KeranjangCountProvider.jsx :**
```
  import React, { createContext, useState } from 'react'

  //ini context nya, di export biar bisa dipanggil di componentnya
  export const KeranjangCountContext = createContext()

  function KeranjangCountProvider({children}) {
    const [keranjangCount, setKeranjangCount] = useState(0)

    return (
      //contextnya di panggil di provider
      //gara2 context ini, state keranjangCount menjadi global
      <KeranjangCountContext.Provider value={{keranjangCount, setKeranjangCount}}>
        {/*children ini berisi app nya, dan dipanggil lg di provider*/}
        {children}
      </KeranjangCountContext.Provider>
    )
  }

  export default KeranjangCountProvider
```
- **main.jsx :
```
  import React from "react";
  import ReactDOM from "react-dom/client";
  import App from "./App";
  import KeranjangCountProvider from "./KeranjangCountProvider";
  import UserProvider from "./UserProvider";

  ReactDOM.createRoot(document.getElementById("root")).render(
    //bungkus lagi dengan provider atau contextnya
    <UserProvider>
      {//provider ngebungkus app, dan app akan masuk 
      {//menjadi propsnya provider}
      <KeranjangCountProvider>{//keranjang taro didalam ketika keranjang butuh data dari user, jadi yg dalem bisa ngambil yg luar}
        <App />
      </KeranjangCountProvider>
    </UserProvider>

  );
```
- Component-componentnya :
- **Keranjang.jsx : 
```
  import React, { useContext } from 'react'
  import { KeranjangCountContext } from '../KeranjangCountProvider'

  function Keranjang() {
    //panggil context untuk mengambil data dari contextnya
    const stateKeranjang = useContext(KeranjangCountContext)
    const totalKeranjang = stateKeranjang.keranjangCount

    // console.log(tes)

    return (
      <div>
        <span>Keranjang</span>
        <span> {totalKeranjang}</span>
      </div>
    )
  }

  export default Keranjang
```
- **SummaryPembelian.jsx
```
  import React, { useContext } from "react";
  import { KeranjangCountContext } from "../KeranjangCountProvider";

  function SummaryPembelian() {
    //panggil context untuk mengambil data dari contextnya
    const { keranjangCount } = useContext(KeranjangCountContext);

    return (
      <div>
        <h1>Summary Pembelian</h1>

        <h2>jumlah barang yg dibeli ada {keranjangCount}</h2>
      </div>
    );
  }

  export default SummaryPembelian;
```
- **Counter.jsx : 
```
  import React, { useContext, useState } from "react";
  import { KeranjangCountContext } from "../KeranjangCountProvider";

  function Counter() {
    //panggil context
    const { keranjangCount, setKeranjangCount } = useContext(KeranjangCountContext)
    const [count, setCount] = useState(0);

    const increment = () => {
      setCount(count + 1);
      //ubah isi keranjang
      setKeranjangCount(keranjangCount + 1)
    };

    const decrement = () => {
      setCount(count - 1);
      //ubah isi keranjang
      setKeranjangCount(keranjangCount - 1)
    };

    return (
      <>
        <button onClick={decrement}>-</button>
        <span>{count}</span>
        <button onClick={increment}>+</button>
      </>
    );
  }

  export default Counter;
```
- **ListProduct.jsx
```
  import React, { useState } from 'react'
  import Counter from './Counter'

  function ListProduct() {
    const [products, setProducts] = useState([
      {id: 1, nama: "buku"},
      {id: 2, nama: "pulpen"},
    ])

    return (
      <div>
        {products.map(item => (
          <div key={item.id}>
            <span>{item.nama}</span>
            <Counter />
          </div>
        ))}
      </div>
    )
  }

  export default ListProduct
```
- **Context ke 2 :
- **UserProvider.jsx
```
  import React, { createContext, useState } from 'react'

  export const UserContext = createContext()

  function UserProvider({children}) {
    const [user, setUser] = useState({
      name: "alpha",
      email: "alpha@gmail.com"
    })

    return (
      <UserContext.Provider value={{user, setUser}}>
        {children}
      </UserContext.Provider>
    )
  }

  export default UserProvider
```
- App.jsx
```
  import { useContext } from "react";
  import Keranjang from "./components/Keranjang";
  import ListProduct from "./components/ListProduct";
  import SummaryPembelian from "./components/SummaryPembelian";
  import { UserContext } from "./UserProvider";

  function App() {
    //panggil context
    const { user } = useContext(UserContext);

    return (
      <div className="App">
        <Keranjang />
        <br />

        <ListProduct />
        <SummaryPembelian />

        <h1>{user.name}</h1>
      </div>
    );
  }

  export default App;
```
- **React Context dengan useReducer**
- Cntext mengubah data nya menjadi global, dengan useReducer, reducer dapat memanage data nya didalam reducer bukan di component
- Contoh Counter app React Context dengan useState biasa :
- **Counter1.jsx :
```
  import React, { useContext } from "react";
  import { CounterContext } from "../context/Counter1Provider";

  // komponen ini terhubung dengan Counter1Provider
  function Counter1() {
    const { count, setCount } = useContext(CounterContext);

    return (
      <div>
        <button onClick={() => setCount(count - 1) }>-</button>
        <span>{count}</span>
        <button onClick={() => setCount(count + 1)}>+</button>
      </div>
    );
  }

  export default Counter1;
```
- Counter1Provider.jsx :
```
  import React, { createContext, useReducer, useState } from "react";

  export const CounterContext = createContext();

  function Counte1Provider({ children }) {
    const [count, setCount] = useState(0)

    return (
      <CounterContext.Provider value={{ count, setCount }}>
        {children}
      </CounterContext.Provider>
    );
  }

  export default Counte1Provider;
```
- **main.jsx : 
```
  import React from "react";
  import ReactDOM from "react-dom/client";
  import App from "./App";
  import Counter2Provider from "./context/Counter2Provider";
  import Counter1Provider from "./context/Counter1Provider";
  import TodoProvider from "./context/TodoProvider";

  ReactDOM.createRoot(document.getElementById("root")).render(
    // <React.StrictMode>
    <TodoProvider>
      <Counter2Provider>
        <Counter1Provider>
          <App />
        </Counter1Provider>
      </Counter2Provider>
    </TodoProvider>
    // </React.StrictMode>
  );
```
- **useReducer** : alternatif dari useState, reducer menghasilkan state dan dispatch method
- kita bisa menggunakan useReducer ketika state nya diubah dengan cara macem2
- **Contoh : **
- Counter 2 : menggunakan reducer
- Counter2Provider.jsx :
```
  import React, { createContext, useReducer, useState } from "react";

  export const CounterContext = createContext();

  // membuat const variabel dari increment dan decrement
  const INCREMENT = "INCREMENT";
  const DECREMENT = "DECREMENT";

  // initialState berupa object
  const initialState = {
    count: 0,
  };

  function reducer(state, action) {
    switch (action.type) {
      // dari type dispatch nya
      case INCREMENT:
        return { count: state.count + 1 }; //return object karena statenya object
      case DECREMENT:
        return { count: state.count - 1 };
      default:
        return state;
    }
  }

  function Counter2Provider({ children }) {
    // function reducer dan initialState diatas dimasukin ke useReducer
    // state diambil dari initialState
    const [state, dispatch] = useReducer(reducer, initialState);

    // increment akan menjalankan dispatch
    const increment = () => {
      //dispatch akan merubah reducer,jadi klo mau ubah state, gunakan dispatch
      dispatch({ type: INCREMENT });
    };

    const decrement = () => {
      dispatch({ type: DECREMENT });
    };

    return (
      // state, inc, dec dipanggil ke value, state ini dari useReducer
      <CounterContext.Provider value={{ state, increment, decrement }}>
        {children}
      </CounterContext.Provider>
    );
  }

  export default Counter2Provider;
```
- **Counter2.jsx :
```
  import React, { useContext } from "react";
  import { CounterContext } from "../context/Counter2Provider";

  // komponen ini terhubung dengan Counter2Provider
  function Counter() {
    const { 
      state, 
      increment, 
      decrement 
    } = useContext(CounterContext);

    return (
      <div>
        <button onClick={decrement}>-</button>
        <span>{state.count}</span>
        <button onClick={increment}>+</button>
      </div>
    );
  }

  export default Counter;
```
- Contoh lain, **TodoApp with context
- **TodoProvider.jsx :
```
  import React, { createContext, useReducer } from 'react'

  export const TodoContext = createContext()

  const DELETE_TODO = "DELETE_TODO"

  const initialState = {
    todos: ["belajar reaact", "belajar context", "belajar redux"]
  }

  function reducer(state, action) {
    switch (action.type) {
      case DELETE_TODO:
        //newTodo akan memfilter dan mengambil semua todo yang indexnya
        //BUKAN indexnya action, atau ambil semua data kecuali yg index action
        const newTodo = state.todos.filter((item, index) => index != action.index )
        return {
         todos: newTodo 
        }
      default: return state
    }
  }

  function TodoProvider({children}) {
    const [state, dispatch] = useReducer(reducer, initialState)

    const deleteTodo = (index) => {
      dispatch({
        type: DELETE_TODO,
        index
      })
    }

    return (
      <TodoContext.Provider value={{state, deleteTodo}}>
        {children}
      </TodoContext.Provider>
    )
  }

  export default TodoProvider
```
- **TodoList.jsx :
```
  import React, { useContext } from 'react'
  import { TodoContext } from '../context/TodoProvider'

  function TodoList() {
    const {state, deleteTodo} = useContext(TodoContext)

    return (
      <div>
        <h1>Todo</h1>
        <form>
          <input type="text" name="" id="" />
          <button>add</button>
        </form>

        <ul>
          {state.todos.map((item, index) => (
            <li key={index}><span>{item}</span>
              <button onClick={() => deleteTodo(index)}>x</button>
            </li>
          ))}
        </ul>
      </div>
    )
  }

  export default TodoList
```
- **App.jsx : 
```
  import Counter1 from './components/Counter1'
  import Counter2 from './components/Counter2'
  import TodoList from './components/TodoList'

  function App() {
    return (
      <div className="App">
        <h3>Counter with context</h3>
        <Counter1 />

        <h3>Counter with context and useReducer</h3>
        <Counter2 />

        <TodoList />
      </div>
    )
  }

  export default App
```
### **2. React Testing.**
- Manual testing biasanya dengan cara ngecek tombol, routes, dan halaman nya satu persatu, sesuai ekspektasi atau tidak
- Automation testing menggunakan kode, kita buat kode testing, lalu kode nya yg lakuin pengujian
- **Automation test dibagi jadi 3 : unit test, integration, dan E2E (end-to-end), unit paling cepat & murah dan E2E paling lambat & mahal
1. Unit test (biasanya dilakukan oleh developer) : testing pada bagian paling kecil, misalnya function
2. Integration : testing yg berhubung ke aplikasi lain, misalnya yg terhubung ke database atau sistem lain
3. E2E (bisa hire Quality Assurance engineer, dia pake software lain. bisa jg pake dev yg pake software lain) : testing dari sisi user, apa yg dialami user
- Unit testing dapat menggunakan jest dan RTL, misalnya unit testing nya funtion sum(1.2) → 3 (function sum 1 + 2 = 3)
- **jest** adalah library js untuk melakukan testing
- **RTL** (React Testing Library) udah include dengan jest, RTL ini unit test tapi semi-E2E karena bikin kode berdasarkan user experience nya
- 2 cara menulis testing :
1. buat fitur → testing (buat fiturnya dulu sampe jadi dulu baru di testing)
2. testing → buat fitur (buat kode testing dulu , ekspektasi nya apa, baru bikin fitur nya). contoh :
  - ekspektasi : sum(1,2) → 3 ⇒ ketika function sum diisi 1 dan 2, ekspektasi nya 3,
  - maka functionnya adalah : function sum(x, y) { return x+y }
  - note : nulis testing itu lama, harus jelas spesifikasi app yang ingin dibuat
  - install jest :
  - npm install -D jest
  - tambahin di package.json : 
  ```
    "scripts":{
      "test": "jest"
    },
  ```
  - lalu npm run test untuk ngerun jest
- Contoh testing manual
- **App.js : 
```
  // Soal : buat fungsi penjumlahan dengan 2 parameter

  function sum(x, y) {
     return x + y
  }

  ekspektasi :
  console.log(sum(0,0)) // 0
  console.log(sum(1,0)) // 1
  console.log(sum(0,1)) // 1
  console.log(sum(1,2)) // 3
  console.log(sum(2,2)) // 0
```
- **Contoh testing dengan jest :
- **App.js :  (ini functionnya)
```
  // Soal : buat fungsi penjumlahan dengan 2 parameter

  const sum = (x, y) => x + y

  const checkGG = (n) => {
    if (n % 2 == 1) return "Ganjil"
    return "Genap"
  }

  const isOdd = (n) => {
    if (n % 2 == 1) return true
  }

  // ini mirip export default
  module.exports = {sum, checkGG, isOdd} 
```
- **App.test.js (ini kode testingnya)
```
  const {sum, checkGG, isOdd} = require('./app');

  test('menjumlahkan angka pada sum()', () => {
    expect(sum(0, 0)).toBe(0) //kalau sum diinput 0 dan 0, maka toBe atau hasilnya atau ngereturn 0
    expect(sum(0, 1)).toBe(1)
    expect(sum(1, 1)).toBe(2)
    expect(sum(2, 2)).toBe(4)
  })

  test('check ganjil atau genap', () => {
    expect(checkGG(1)).toBe("Ganjil")
    expect(checkGG(2)).toBe("Genap")
    expect(checkGG(3)).toBe("Ganjil")
  })

  test('check ganjil', () => {
    expect(isOdd(1)).toBeTruthy() //returnnya harus true
    expect(isOdd(2)).toBeFalsy()
    expect(isOdd(3)).toBeTruthy()
  })
```
- **RTL (React Testing Library)**
- **RTL adalah package library yang membantu testing tampilan component secara user-centric
- biasanya saat create-react-app udah otomatis nge install RTL ke package.json nya
- untuk nge run testing dengan npm run test
- pada RTL pola nya pertama bikin test box, dalam test box ada
- - render component
- - find element
- - interact with element (optional)
- - assert the result (ekspektasi akhirnya apa)
- dari kumpulan test block dimasukan kedalam describe block
- **TDD circle :**
- test fails (red) → test passes (green) → refactor (blue) → test fails (red)
- **Contoh RTL :
```
  import { render, screen } from '@testing-library/react'
  import App from './App'

  test('reenders learn react link', () => {
    render (<App />) //render component
    //getBy cuma boleh ada 1 element yg dicari, klo ga error
    const linkElement = screen.getByText(/learn react/i) //find element using screen
    expect(linkElement).toBeInTheDocument() //assert result
  })
```
- Selain getBy ada findBy, queryBy, getAllBy, findAllBy, queryAllBy
- Contoh lain :
- **Counter.js : 
```
  import React, { useState } from 'react'

  function Counter() {
    const [count, setCount] = useState(0)

    return (
      <div>
        <button onClick={() => setCount(count-1)}>-</button>
        <span>{count}</span>
        <button onClick={() => setCount(count+1)}>+</button>
      </div>
    )
  }

  export default Counter
```
- **Conter.test.js :
```
  import { fireEvent, render, screen } from '@testing-library/react';
  import Counter from './Counter';

  test("render counter", () => {
    render(<Counter/>)
    const decrementBtn = screen.getByText("-")
    const count = screen.getByText("0")
    const incrementBtn = screen.getByText("+")

    expect(decrementBtn).toBeInTheDocument()
    expect(count).toBeInTheDocument()
    expect(incrementBtn).toBeInTheDocument()
  })

  test('click increment button', () => { 
    render(<Counter/>)
    const incrementBtn = screen.getByText("+")
    const count = screen.getByText("0")

    //textContent untuk melihat yang ada dalam span
    expect(count.textContent).toBe("0") 

    //fireEvent.eventName untuk ngecek event nya
    fireEvent.click(incrementBtn)
    //setelah tombolnya di click, kita expect textContentnya 1
    expect(count.textContent).toBe("1")
  })
```
- 10 - 11 November 2022
- Brief Group Project dan Diskusi Group Project & Tanya Jawab



















