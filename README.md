// 

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/css/bootstrap.min.css" integrity="sha384-/Y6pD6FV/Vv2HJnA6t+vslU6fwYXjCFtcEpHbNJ0lyAFsXTsjBbfaDjzALeQsN6M" crossorigin="anonymous">
  <title>Item Lister</title>
</head>
<body>
  <header id="main-header" class="bg-success text-white p-4 mb-3">
    <div class="container">
    
      <div>
      <h1 id="header-title">Item Lister <span style="display:none">123</span></h1>
      <div  class="col-md-6 aling-self-center">
        <input type="text"class="form-control" id="filter" placeholder="search items...">
      </div>
     </div>
    </div>

  </header>
  <div class="container">
   <div id="main" class="card card-body">
    <h2 class="title">Add Items</h2>

    <form  id="addform"class="form-inline mb-3">
      <input  id="Item" class="form-control mr-2">
      <input type="submit" class="btn btn-dark" value="Submit">
    </form>
    <h2 class="title">Items</h2>
    <ul id="items" class="list-group">
      <li class="list-group-item">Item 1  <button class="btn btn-danger btn-sm float-right delete">X</button> </li>
      <li class="list-group-item">Item 2  <button class="btn btn-danger btn-sm float-right delete">X</button></li>
      <li class="list-group-item">Item 3  <button class="btn btn-danger btn-sm float-right delete">X</button></li>
      <li class="list-group-item">Item 4  <button class="btn btn-danger btn-sm float-right delete">X</button></li>
    </ul>
   </div>
  </div>
 <script src="main.js"></script>
</body>
</html>

/// 
///javasctipcode

var form = document.getElementById('addform');
var itemList = document.getElementById('items');
var filter = document.getElementById('filter');

// form submit event
 form.addEventListener('submit', addItem);
//delete event
itemList.addEventListener('click', removeitem)
// filter event
filter.addEventListener('keyup',filteritems)


//  creating function to add items
 function addItem(e){
   e.preventDefault();
   
   //get inout value
   var newitem = document.getElementById('Item').value;
   
   // create new li  element
   var li = document.createElement('li');
   // add class name
   li.className = 'list-group-item';
   console.log(li);
   // add text node with input value
    li.appendChild(document.createTextNode(newitem));

    // crate deletebutton eleembt
    var deletebtn = document.createElement('button');
     deletebtn.className='btn btn-danger btn-sm float-right delete'
     //append text  node
     deletebtn.appendChild(document.createTextNode('X'));
    // append button to li
     li.appendChild(deletebtn);

    itemList.appendChild(li);
   }

   // crataing function to remove items

   function removeitem(e){
       if(e.target.classList.contains('delete')){
         if(confirm('are sure to delete this')){
          var li = e.target.parentElement;
          itemList.removeChild(li);

         }
       }
   }

   // crating function for filter items

   function filteritems(e){
    // converting lowercase
     var text = e.target.value.toLowerCase();
     // get li from itemlist
     var items=itemList.getElementsByTagName('li');
     // convert to array
     Array.from(items).forEach(function(items){
       var itemName = items.firstChild.textContent;
      if(itemName.toLowerCase().indexOf(text) != -1 ) {
       items.style.display = 'block';
       } else{
        items.style.display = 'none';

        }

     });

     
     }
    


