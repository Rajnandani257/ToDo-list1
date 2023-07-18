# ToDo-list1


#HTML File

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TO-Do List</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container ">
        <div class="todo-app">
            <h2>To-Do List<img src="images/todo.png"></h2>
          <div class="row">
            <input type="text" id="input-box" placeholder="Add Your Elements">
            <button  onclick="addTask()">Add</button>

          </div>
          <ul id="list-container">
          <!---  <li class="checked">Task 1</li>
            <li>Task 2</li>
            <li>Task 3</li>-->

          </ul>
        </div>
    </div><script src="images/script1.js"></script>
</body>
</html>




#CSS file


*{
    margin:0;
    padding:0;
    font-family: 'poppins',sans-serif;
    box-sizing: border-box;
}
.container{
    width:100%;
    min-height: 100vh;
    background: linear-gradient(135deg,#671815,#c92d6e);
    padding:10px;
}
.todo-app{
    width:100%;
    max-width: 540px;
    background: white;
    margin: 100px auto 20px;
    padding:40px 30px 70px;
    border-radius: 10px;
}
.todo-app h2{
  color:#002765;
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.todo-app h2 img{
    width: 30px;
    margin-left: 10px;
}
.row{
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #edeef0;
    border-radius: 30px;
    padding-left: 20px;
    margin-bottom: 25px;
}
input{
    flex:1;
    border:none;
    outline: none;
    background: transparent;
    padding: 10px;

}
button{
    border:none;
    outline: none;
    background:#ff5945;
    padding: 16px 50px;
    color:#fff;
    font-size: 16px;
    cursor: pointer;
    border-radius: 40px;
}

ul li{
    list-style:none ;
    font-size:17px;
    padding: 12px 8px 12px 50px;
    user-select: none;
    cursor:pointer;
    position: relative;

}

ul li::before{
    content: '';
    position:absolute;
    height: 28px;
    width: 28px;
    border-radius: 50%;
    background-image: url('images/circle3.jpg');
    background-size:cover ;
    background-position: center;
    top: 12px;
    left:8px;

}

 ul li.checked{
    color:#555;
    text-decoration: line-through;

}

ul li.checked::before{
    background-image: url('images/checked.png');
}

ul li span{
    position:absolute;
    right: 0;
    top: 5px ;
    width:40px;
    height:40px;
    font-size: 22px;
    color:#555;
    line-height:40px;
    text-align: center;
    border-radius: 50%;
}

ul li span:hover{
    background: #edeef0;
}





#JAVASCRIPT file


const inputBox = document.getElementById('input-box');
const listcontainer = document.getElementById('list-container');


function addTask(){
    if(inputBox.value === ''){
        alert('you must write something');
    }
    else{
      let li = document.createElement('li');
      li.innerHTML = inputBox.value;
      listcontainer.appendChild(li);
      let span = document.createElement('span');
      span.innerHTML = ' \u00d7';
      li.appendChild(span);
    }
    inputBox.value = '';
    saveData();


}

listcontainer.addEventListener('click',function(e){
    if(e.target.tagName === 'LI'){
        e.target.classList.toggle('checked');
        saveData();
    }
    else if(e.target.tagName === 'SPAN'){
        e.target.parentElement.remove();
        saveData();
    }
},false);

function saveData(){
    localStorage.setItem('data',listcontainer.innerHTML);
}

function showTask(){
    listcontainer.innerHTML = localStorage.getItem('data');
}
showTask();
