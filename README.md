<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8" />
    <title>TO DO LIST</title>
    <style>
*{
    margin: 0;
    padding: 0;
    font-family: 'popins',sans-serif;
    box-sizing: border-box;
}
input{
    flex :1;
    border: none;
    outline: none;
    background: transparent;
    padding:10px;
    font-weight: 14px;
}
.container{
 width: 100%;
 min-height: 100vh;
 background : linear-gradient(135deg, #153677,#4e085f);
 padding: 10px;
}
.row{
  display:flex;
  align-items: center;
  justify-content: space-between;
  background: #edeef0;
  border-radius: 30px;
  padding-left: 20px;
  margin-bottom: 25px;
}
.todoapp{
    width: 100%;
    max-width: 540px;
    background: #fff;
    margin:100px auto 20px;
    padding:40px 30px 70px;
    border-radius: 10px;
}
.todoapp h2{
    color : #002765;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
}
.todoapp h2 img{
    width: 30px;
    margin-left: 10px;
}
button{
    border:none;
    outline: none;
    padding: 16px 50px;
    background: #ff5954;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
    border-radius: 40px;
}
ul li{
    list-style: none;
    font-size: 20px;
    padding: 12px 8px 12px 50px;
    user-select: none;
    cursor: pointer;
    position: relative;
}
ul li::before{
    content:'';
    position: absolute;
    height:28px;
    width:30px;
    border-radius: 50%;
    background-image: url(https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTQ7KqUIkz_IglE_VgyGodnrqkERyBizV1B9AlY0A7-Iw&s);
    background-size: cover;
    background-position: center;
    top:12px;
    left:8px;
}
ul li.checked{
    color:#555;
    text-decoration: line-through;
}
ul li.checked::before{
    background-image: url(data:image/jpeg;base64,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);

}
ul li span{
    position: absolute;
    right:0;
    top:5px;
    width:40px;
    height:40px;
    font-size: 22px;
    color:#555;
    line-height: 40px;
    text-align: center;
    border-radius: 50px;
}
ul li span:hover{
    background: #edeef0;
}
        </style>
</head>
<body>
    <div class="container">
        <div class="todoapp">
        <h2>TO-DO LIST<img src="data:image/png;base64,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" style="width: 100px;height:100px;"></h2>
       <div class="row">
        <input type="text"  id="input-box" placeholder="enter text here">
      <button onclick="addTask()">ADD</button>
       </div>
       <ul id="list-container">
      <!----  <li class="checked">TASK 1</li>
        <li class="checked">TASK 2</li>
        <li class="checked">TASK 3</li> --->
        </ul>
       </div>
       </div>
       <script>
        const inputBox = document.getElementById("input-box");
        const listcontainer = document.getElementById("list-container");
         function addTask(){
            if(inputBox.value === ''){
                alert(" you must write something!!");
            } 
            else{
                let li =document.createElement("li");
                li.innerHTML = inputBox.value;
                listcontainer.appendChild(li);
                let span =document.createElement("span");
                span.innerHTML = "\u00d7";
                li.appendChild(span);
            }
            inputBox.value = "";
            saveData();
         }
         listcontainer.addEventListener("click", function(e){

            if(e.target.tagName === "LI"){
                e.target.classList.toggle("checked");
                saveData();
            }
            else if(e.target.tagName === "SPAN"){
                e.target.parentElement.remove();
                saveData();
            }
            } ,false);
        function saveData(){
            localStorage.setItem("data", listcontainer.innerHTML);
        }
        function showTask(){
            listcontainer.innerHTML = localStorage.getItem("data");
        }
        showTask();
        </script>
    </body>
</html>
