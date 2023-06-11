# Todo-Application-
## AIM
To create complete Todo application with all features using React
## ALGORITHM 
1. Import the required modules: React and other components.
2. Define the functional component TodoList that represents a single todo item in the list.
3. The TodoList component receives two props: item (the text of the todo item) and deleteItem (a function to delete the item).
4. Define the main component App that represents the todo list application.
5. Use the useState hook to initialize the listTodo state as an empty array.
6. Define a function addList that takes an inputText parameter. If the input text is not empty, add it to the listTodo state using the spread operator and set the updated state.
7. Define the main component App that represents the todo list application.
8. Use the useState hook to initialize the listTodo state as an empty array.
9. Define a function addList that takes an inputText parameter. If the input text is not empty, add it to the listTodo state using the spread operator and set the updated state.
10. Export the App component as the default export.

## PROGRAM
### App.js
```
import React, {useState} from 'react'
import "./App.css"
import TodoInput  from './components/TodoInput'
import TodoList from './components/TodoList';
function App() {
  const [listTodo,setListTodo]=useState([]);
  let addList = (inputText)=>{
    if(inputText!=='')
    setListTodo([...listTodo,inputText]);
  }
  const deleteListItem = (key)=>{
    let newListTodo = [...listTodo];
    newListTodo.splice(key,1)
    setListTodo([...newListTodo])

  }
  return (
    <div className="main-container">
      <div className="center-container">
<TodoInput addList={addList}/>
<h1 className="app-heading">Todo</h1>
<hr/>
{listTodo.map((listItem,i)=>{
  return (
    <TodoList key={i} index={i} item={listItem} deleteItem={deleteListItem}/>
  )
})}
      </div>
    </div>
  
  )
}
export default App
```
### TodoList.js
```
import React from 'react'

function TodoList(props) {
  return (
    <li className="list-item">
        {props.item}
        <span className="icons">
        <i className="fa-sharp fa-solid fa-trash icon-delete"
        onClick={e=>{
            props.deleteItem(props.index)
        }}></i>
        </span>
    </li>
  )
}

export default TodoList
```
### TodoInput.js
```
import React,{useState} from 'react'

function TodoInput(props) {
    const [inputText,setInputText] = useState('');
    const handleEnterPress = (e) =>{
        if(e.keyCode===13){
            props.addList(inputText)
            setInputText("")
        }
    }
  return (
    <div className="input-container">
        <input 
        type="text" 
        className="input-box-todo"
        placeholder="Enter your todo"
        value={inputText}
        onChange={e=>{
            setInputText(e.target.value)
        }}
        onKeyDown={handleEnterPress}/>
        <button className='add-btn'
        onClick={()=>{
            props.addList(inputText)
            setInputText("")
        }}>+</button>
        
    </div>
  );
}

export default TodoInput
```
### App.css
```
*{
  margin: 0;
  padding: 0;
}
body{
  background-color: #333;
}
.main-container{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.center-container{
  height: 500px;
  width: 350px;
}
.app-heading{
  padding: 4px;
  color: white;  
  /* text-align: center; */
  font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  text-transform: uppercase;
}
.input-container{
  display: flex;
  justify-content: center;
  margin-bottom: 10px;
}
.input-box-todo{
  margin-left: 10px;
  width: 70%;
  height: 40px;
  border-radius: 14px;
  border:1px solid black;
  padding-left: 10px;  
  box-shadow: 0px 10px 20px rgba(0,0,0,0.3);
  outline: none;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  font-size: large;
}
.add-btn{
  width:40px;
  height:40px;
  border-radius: 50%;
  border:none;
  background-color:#316fc1;
  color: white;
  font-weight: bolder;
  font-size: larger;
  margin-left: 10px;  
  cursor: pointer;
  box-shadow: 0px 5px 10px rgba(11, 10, 10, 0.3);
  transition: 0.3s;
}
.add-btn:active{
  box-shadow: none;
}
.list-container{
  display: flex;
  align-items: center;
  margin-top: 5px;
}
.list-item{
  list-style-type: none;
  /* background-color: #596e8b; */
  border:2px solid rgb(161, 158, 158);
  color:white;
  padding:3px;
  padding-left: 5px;
  border-radius: 5px; 
  width: 100%;
  height: 30px;
  display: flex;
  align-items: center;
  position: relative;
  margin-top: 10px;
}
.icons{
  position: absolute;
  right: 10px;
}
.icons i{
  margin: 4px;
  font-size: large;
  cursor: pointer;
  transition: 0.1s;   
}
.icons i:hover{
  transform: scale(1.2);  
}
.icon-delete:hover{
  color:red;

}
```
## OUTPUT
<img width="960" alt="Screenshot 2023-06-11 084343" src="https://github.com/Shavedha/Todo-Application-/assets/93427376/86f4b026-bd01-4777-a1a6-201b490aab6a">
<img width="960" alt="Screenshot 2023-06-11 084427" src="https://github.com/Shavedha/Todo-Application-/assets/93427376/5b1effe3-795c-42c2-9296-874ae9fc8064">
<img width="960" alt="Screenshot 2023-06-11 084438" src="https://github.com/Shavedha/Todo-Application-/assets/93427376/e3fce36b-64e8-4e73-9304-47a74e463fd7">
<img width="960" alt="Screenshot 2023-06-11 084448" src="https://github.com/Shavedha/Todo-Application-/assets/93427376/8202c4e2-7f4b-4607-8073-728c9295a8b9">



## RESULT
Thus a To-do application is created using React.
