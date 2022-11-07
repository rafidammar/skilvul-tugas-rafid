# Writing & Presentation Week 7 - Front-end Bootcamp
## Rafid Ammar Adinegoro
## 31 Oktober - 4 November 2022

### **1. React JS Lanjutan, Prop Types.**
### Prop Types
- Prop types merupakan lib untuk mengecek tipe data props agar sesuai ekspektasi. jika tidak sesuai, makan akan muncul pesan error
- props itu memiliki parent(tempat manggil komponen) dan child (komponen). misal mau ngirim props dari parent ke child. Misal child menerima number, tapi parent  lalu ngirim nya string, jadi ge sesuai ekspektasi
### install prop types
- npm install prop-types
- Contoh penggunaan :
- import PropTypes from ‘prop-types’ :
```
  function Header(props){
      return(
          <>
            <h2>Nama: {props.char}</h2>
            <h2>Age: {props.age}</h2>
          </>
      )
  }

  Header.propTypes = {
    char: PropTypes.string,
    age: PropTypes.number
  }
```
### **2. React Router.**
### React Router
- React Router bisa digunakan untuk berpindah-pindah halaman (page)
- cara install dan menggunakan react router :
- npm install react-router-dom@6
**main.jsx **
 ```
  import { BrowserRouter } from "react-router-dom"
  import { Routes, Route, Link } from "react-router-dom" // link utk menggantikan anchor
  import React from "react";
  import App from "./App";
  import ReactDOM from "react-dom/client";

  ReactDOM.createRoot(document.getElementById("root")).render(
    <React.StrictMode>
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </React.StrictMode>
  )
 ```
**app.jsx**
```
// kalo ada routingan dibungkus pake <Routes>
<>
	<nav>
		<Link to={"/"}>Home |</Link>
		<Link to={"/about"}>About</Link>
	</nav>
	<Routes>
	    <Route path="/" element={<HomePage />} />
        {/* route params*/}
        <Route path="/detail/:id" element={<DetailPage />} />

        {/* penggunaan nested route */}
        <Route path="/about" element={<AboutPage />}>
          <Route path="student" element={<AboutStudent />} />
          <Route path="teacher" element={<AboutTeacher />} />
          {/* index digunakan agar element AboutSchool langsung ditampilkan pertama kali ketika page about dibuka */}
          <Route index element={<AboutSchool />} />
        </Route>
        {/* tambahkan path="*" untuk menampilkan halaman yg tidak ditemukan. case nya adalah ketika user mengakses path tertentu yang tidak terdaftar di routingan yang kita miliki*/}
        <Route path="*" element={<NotFound />} />
	</Routes>
</>
```
### Contoh : 
**HomePage.jsx **
```
import {useNavigate} from "react-router-dom"

const HomePage = () => {
	let data = [
		{
			id: 1,
			name: "Mika,
		},
		{
			id: 2,
			name: "Reyhan",
		},
		{
			id: 3,
			name: "Asep",
		},
	]

const handleDetail = (id) => {
	// untuk pindah halaman ke page detail sekaligus membawa id params
	navigation(`/detail/${id}`)
}
	
	return (
		<>
			<h1>Ini Home Page</h1>
			{data.map((el) => {
				return (
					// kalo tombol detail di klik, akan ngirim idnya si 'nama'
					<div key={el.id}>
						<h2>Nama: {el.name}</h2>
						<button onClick={() => handleDetail(el.id)}>Detail</button>
					</div>
				)
			})}
			<Link to={"about/student"}>About Student |</Link>
      <Link to={"about/teacher"}>About Teacher</Link>
		</>
	)
}
```
**DetailPage.jsx **
```
import { useParams } from "react-router-dom";

const DetailPage = () => {
  // useParams untuk menangkap id yang kita kirim dari halaman home
  const { id } = useParams();
  console.log(id);

  const detailInfo = [
    {
      id: 1,
      name: "Mika",
      address: "jakarta",
      hobby: "menari",
    },
    {
      id: 2,
      name: "Reyhan",
      address: "bandung",
      hobby: "memancing",
    },
    {
      id: 3,
      name: "Asep",
      address: "malang",
      hobby: "membaca",
    },
  ];
  // ide:
  // 1. filter data dari detailInfo dan dicocokkan dengan id yg kita kirim dari home (yg ditangkap di params)
  // 2. Mapping data untuk menampilkan hasil yang sesuai dari data filter
  return (
    <>
      {detailInfo
        .filter((el) => el.id === +id)
        .map((el) => {
          return (
            <div key={el.id}>
              <h2>Name: {el.name}</h2>
              <h2>Address: {el.address}</h2>
              <h2>Hobby: {el.hobby}</h2>
            </div>
          );
        })}
    </>
  );
};
```
### **3. React Redux.**
### Redix
- Redux adalah salah satu state management. Redux juga menawarkan tools untuk masing-masing browser contoh [chrome redux devtools](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=en)
 untuk memonitor keadaan state kita saat ini.
- Redux didukung package middleware yang bertebaran di npm yang mana memudahkan kita untuk melakukan development seperti redux-thunk, redux-saga, redux-persist dan sebagainya. Kalau kita memilih context API dibanding redux bisa-bisa saja tapi untuk logic seperti thunk nanti kita butuh melakukan extra karena harus buat dari scratch.
- **Action** adalah sebuah function yang mereturn sebuah objek. Objek tersebut memiliki sebuah property wajib yaitu type. Type inilah yang menentukan bagaimana statenya akan diubah.
- **Reducer a**dalah sebuah fungsi yang tugasnya untuk mengolah state yang ada di store. Misal menambah data, menghapus data, mengambil data, dsb. Ada 2 parameter wajib dari reducer, yaitu state dan action.
- **Store** adalah tempat untuk menampung state. Jadi store ibarat database untuk frontend.
- Alur kerjanya seperti berikut:
1. Pertama akan ada triger dari UI
2. Kemudian akan ke action
3. Dari action reducer akan mengubah state yang sesuai dengan type dari action tadi
4. Terahir update UI lagi
### Contoh aplikasi react yang mengimplementasi redux :
**App.jsx**
```
import { useState } from 'react'
import Keranjang from './components/Keranjang'
import ListProduct from './components/ListProduct'
import SummaryPembelian from './components/SummaryPembelian'


function App() {
  const [count, setCount] = useState(0)

  return (
    <div className="App">
      <Keranjang />
      <br />

      <ListProduct />
      <br />

      <SummaryPembelian/>
    </div>
  )
}

export default App
```
**main.jsx**
```
import React from 'react'
import ReactDOM from 'react-dom/client'
import { Provider } from 'react-redux'
import App from './App'
import store from './redux/store'

ReactDOM.createRoot(document.getElementById('root')).render(
  // <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  // </React.StrictMode>
)
```
**Counter.jsx**
```
import React, { useState } from "react";
import { useDispatch } from "react-redux";

import {
  incrementKeranjang,
  decrementKeranjang,
} from "../redux/action/keranjangAction";

function Counter() {
  const dispatch = useDispatch();
  const [count, setCount] = useState(0);

  const increment = () => {
    dispatch(incrementKeranjang())
    setCount(count + 1);
  };

  const decrement = () => {
    dispatch({
      type: "DECREMENT_KERANJANG"
    })
    setCount(count - 1);
  };

  return (
    <>
      <button onClick={decrement}>-</button>
      <span>{count}</span>
      <button onClick={increment}>+</button>
    </>
  );
}
```
**Keranjang.jsx**
```
import React from 'react'
import { useSelector } from 'react-redux'

function Keranjang() {
  const {totalKeranjang} = useSelector(state => state)

  // console.log(state)

  return (
    <div>
      <span>Keranjang</span>
      <span> {totalKeranjang}</span>
    </div>
  )
}
```
**ListProduct.jsx**
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
```
**SummaryPembelian.jsx**
```
import React from 'react'
import { useSelector } from 'react-redux'

function SummaryPembelian() {
  const {totalKeranjang} = useSelector(state => state)

  return (
    <div>
      <h1>Summary Pembelian</h1>

      <h2>jumlah barang yg dibeli ada {totalKeranjang}</h2>
    </div>
  )
}
```
**Redux store**
```
import { createStore } from 'redux'
import keranjangReducer from '../reducer/keranjangReducer'

const store = createStore(keranjangReducer)

export default store
```
**Redux action**
```
export const INCREMENT_KERANJANG = "INCREMENT_KERANJANG"
export const DECREMENT_KERANJANG = "DECREMENT_KERANJANG"

export function incrementKeranjang() {
  console.log("action dipanggil")
  return {
    type: INCREMENT_KERANJANG
  }
}

export function decrementKeranjang() {
  return {
    type: DECREMENT_KERANJANG
  }
}
```
**Redux reducer**
```
import {
  INCREMENT_KERANJANG,
  DECREMENT_KERANJANG,
} from "../action/keranjangAction";

const initialState = {
  totalKeranjang: 0,
};

function keranjangReducer(state = initialState, action) {
  console.log(action);

  switch (action.type) {
    case INCREMENT_KERANJANG: 
      return {
        totalKeranjang: state.totalKeranjang + 1
      }
    case DECREMENT_KERANJANG: 
      return {
        totalKeranjang: state.totalKeranjang - 1
      } 
    default:
      return state;
  }
}
```
### Contoh App Todo List dan Counter dengen mengimplementasikan redux
**main.jsx**
```
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'

import { Provider } from 'react-redux'
import store from './redux/store'

ReactDOM.createRoot(document.getElementById('root')).render(
  // <React.StrictMode>
  <Provider store={store}>
    <App />
  </Provider>
  // </React.StrictMode>
)
```
**App.jsx**
```
import Counter from './components/Counter'
import TodoList from './components/TodoList'

function App() {

  return (
    <div className="App">
      <Counter />

      <TodoList />
    </div>
  )
}

export default App
```
**Counter.jsx**
```
import React from 'react'
import { useDispatch, useSelector } from 'react-redux'
import { decrement, increment } from '../redux/action/counterAction'

function Counter() {
  const dispatch = useDispatch()
  const {count} = useSelector(state => state.counter)

  return (
    <div>
      <button onClick={() => dispatch(decrement())}>-</button>
      <span>{count}</span>
      <button onClick={() => dispatch(increment())}>+</button>
    </div>
  )
}

export default Counter
```
**TodoList.jsx**
```
import React, { useState } from "react";
import { useDispatch, useSelector } from "react-redux";
import { addTodo } from "../redux/action/todoAction";

function TodoList() {
  const dispatch = useDispatch()
  const [inputTodo, setInputTodo] = useState("");
  const todos = useSelector((state) => state.todo.data);

  const handleSubmit = (e) => {
    e.preventDefault();

    console.log(inputTodo, "dari event");
    dispatch(addTodo(inputTodo))
  };

  const handleChange = (e) => {
    setInputTodo(e.target.value);
  };

  return (
    <div>
      <form onSubmit={handleSubmit}>
        <h2>Todo List</h2>
        <input
          type="text"
          name="inputTodo"
          value={inputTodo}
          onChange={handleChange}
        />
        <button>add</button>
      </form>

      <ul>
        {todos.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
}

export default TodoList;
```
**Redux storex**
```
import { combineReducers, createStore } from "redux";
import counterReducer from "../reducer/counterReducer";
import todoReducer from "../reducer/todoReducer";

const allReducer = combineReducers({
  counter: counterReducer,
  todo: todoReducer
})

const store = createStore(allReducer);

export default store;
```
**Redux action**
```
// counterAction.js

export const INCREMENT = "INCREMENT"
export const DECREMENT = "DECREMENT"

export function increment() {
  return {
    type: INCREMENT
  }
}

export function decrement() {
  return {
    type: DECREMENT
  }
}

// todoAction.js
export const ADD_TODO = "ADD_TODO"

export function addTodo(todo) {
  console.log(todo, "dari action");
  return {
    type: ADD_TODO,
    payload: todo
  }
}
```
**Redux reducer**
```
// counterReducer.js
import { DECREMENT, INCREMENT } from "../action/counterAction"

const initialState = {
  count: 0
}

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case INCREMENT:
      return {
        count: state.count + 1
      }
    case DECREMENT:
      return {
        count: state.count - 1
      }
    default: return state
  }
}
export default counterReducer

// todoReducer.js
import { ADD_TODO } from "../action/todoAction"

const initialState = {
  data: ["belajar redux", "redux itu gampng"]
}

function todoReducer(state = initialState, action) {
  switch (action.type) {
    case ADD_TODO:
     console.log(action.payload)
     
      return {
        data: [...state.data, action.payload]
      }

    default: return state
  }
}
export default todoReducer
```
### **4. Redux-Thunk**
- Redux Thunk adalah sebuah middleware yang memungkinkan kita untuk menulis Action yang mengembalikan function, bukan action.
- Redux mengembalikan dalam bentuk props actions yang telah di definisikan oleh Reducers namun masalahnya jika kita ingin mengembalikan sebuah function, redux tidak dapat menanganinya, oleh karena itu kita membutuhkan middleware yang berfungsi untuk mengembalikan action.
### Contoh app To Do list mengimplementasikan redux-thunk :
**main.jsx**
```
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'

import { Provider } from 'react-redux';
import store from './redux/store';

ReactDOM.createRoot(document.getElementById('root')).render(
  // <React.StrictMode>
  <Provider store={store}>
    <App />
  </Provider>
  // </React.StrictMode>
)
```
**App.jsx**
```
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'

import { Provider } from 'react-redux';
import store from './redux/store';

ReactDOM.createRoot(document.getElementById('root')).render(
  // <React.StrictMode>
  <Provider store={store}>
    <App />
  </Provider>
  // </React.StrictMode>
)
```
**TodoList.jsx**
```
import React, { useEffect } from "react";
import { useDispatch, useSelector } from "react-redux";
import { getTodo } from "../redux/action/todoAction";

function TodoList() {
  const dispatch = useDispatch();
  const { todos, isLoading } = useSelector((state) => state.todo);

  useEffect(() => {
    dispatch(getTodo());
  }, []);

  return (
    <div>
      <h2>Todo List</h2>

      <ul>
        {isLoading ? (
          <span>Loading...</span>
        ) : (
          todos.map((item) => <li key={item.id}>{item.todo}</li>)
        )}
      </ul>
    </div>
  );
}

export default TodoList;
```
**Redux Store**
```
import { createStore, combineReducers, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import todoReducer from '../reducer/todoReducer';

const allReducer = combineReducers({
  todo: todoReducer,
  // user: userReducer,
  // product: productReducer
})

const store = createStore(allReducer, applyMiddleware(thunk))

export default store
```
**Redux Action**
```
import axios from "axios";

export const GET_TODO = "GET_TODO";
export const FETCH_START = "FETCH_START";
export const SUCCESS_GET_TODO = "SUCCESS_GET_TODO";

function fetchStart() {
  return {
    type: FETCH_START,
  };
}

function successGetTodo(data) {
  return {
    type: SUCCESS_GET_TODO,
    payload: data,
  };
}

export const getTodo = () => {
  return async (dispatch) => {
    // ubah loading jadi true
    dispatch(fetchStart());

    // axios -> isi data todos, loading jadi false
    const result = await axios.get(
      "https://63478a450484786c6e82998f.mockapi.io/todo"
    );
    dispatch(successGetTodo(result.data));
  };
};

// export const addTodo = () => async (dispatch) => {
//   // ubah loading jadi true
//   dispatch(fetchStart());

//   // axios -> isi data todos, loading jadi false
//   const result = await axios.post(
//     "https://63478a450484786c6e82998f.mockapi.io/todo"
//   , {todo: "thunk itu mudah"});
//   dispatch(successGetTodo(result.data));
// };
```
**Redux Thunk**
```
import { FETCH_START, SUCCESS_GET_TODO } from "../action/todoAction";

const initialState = {
  todos: [],
  isLoading: false,
  err: null,
};

const todoReducer = (state = initialState, action) => {
  switch (action.type) {
    case FETCH_START:
      return {
        ...state,
        isLoading: true
      }
    case SUCCESS_GET_TODO:
      return {
        ...state,
        todos: action.payload,
        isLoading: false
      }
    default:
      return state;
  }
};

export default todoReducer;
```

