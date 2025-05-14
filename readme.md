# shoping spreen
this app porpuse is to fasilitate the user to buy the store items from the internet kepp trak of the recipt and mark how long has the user stay in the app
## table of content
1. [HTML Structure](#html-structure)
3. [JavaScript Functionality](#JavaScript-fucntionality)

## HTML structure
the html is use to mark the structure of the file to ensure a proper interface
````html
  <!-- header -->
  <style>
    *{
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    :root{
      --main-color:#4caf50;
    }
    .main {
      display: flex;
    }
    .list {
      width: auto;
    }
    #shop {
      display: flex;
      flex-wrap: wrap;
      flex-direction: row;
      width: auto;
    }
    .cart {
      margin: 5px;
    }
    .Qbutton{
      padding: 5px;
    }
  </style>
  <nav id="navar" class="navbar navbar-expand-lg bg-body-tertiary bg-primary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">The Shop</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">Home</a>
          </li>
          <!-- theme -->
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
              theme
            </a>
            <ul class="dropdown-menu">
              <li><button class="dropdown-item" id="light-theme">light</button></li>
              <li><button class="dropdown-item" id="dark-theme">dark</button></li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <div id="timer" class="fixed-button">...</div>
  <!-- search barr -->
  <form class="d-flex" role="search">
    <button id="cart-button" class="btn btn-primary" type="button" data-bs-toggle="collapse" data-bs-target="#collapseWidthExample" aria-expanded="true" aria-controls="collapseWidthExample">cart</button>
    <input id="searchBar" class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
    <button class="btn btn-outline-success" type="submit">Search</button>
  </form>

  <!-- main cotainer -->
  <div class="container-fluid main">
    <!-- list container -->
    <div id="item0" class="container text-center" style="max-width:350px; padding: 0; margin: 0;">
      <div class="collapse collapse-horizontal row align-items-start" id="collapseWidthExample">
        <ul id="list" class="list-group list-group-flush">
          <li id="total" class="list-group-item"></li>
        </ul>
      </div>
    </div>

    <!-- item contianer -->
    <div id='shop' class="container-fluid"></div>
  </div>
````
### key components
- a style section to set all the nessesary values to zero 
- header that consist of a nav bar to facilitate the navegation trough the page and deside for the theme of the page

    - tittle of the page
    - home button
    - toggle the theme of the page

- abutton to toggle the lsit of items selected to buy that show the total price 
- a search bar that show the items in real time and a search button 
- a container that can be hiden using the button above 
- the complete list of abailable items 
---
## javascript components
this javscript code is use to make the page responsive to the user's input

````javaScript
class Item {
  constructor(name, price, description, img, quantity) {
    this.name = name;
    this.price = price;
    this.description = description;
    this.img = img;
    this.quantity = quantity;
  }
}

const itemList1 = [
  new Item('Milk', 7, 'Fresh whole milk, 1 liter.', 'milk-removebg-preview.png', 0),
  new Item('Bread', 3, 'Soft white sandwich bread.', 'bread-removebg-preview.png', 0),
  new Item('Eggs', 5, 'A dozen farm-fresh eggs.', 'eggs-removebg-preview.png', 0),
  new Item('Butter', 4, 'Creamy unsalted butter.', 'butter-removebg-preview.png', 0),
  new Item('Cheese', 6, 'Mild cheddar cheese block.', 'cheese-removebg-preview.png', 0),
  new Item('Apples', 4, 'Crisp red apples, 1kg.', 'apple.png', 0),
  new Item('Bananas', 2, 'Ripe bananas, 1kg.', 'bananas-removebg-preview.png', 0),
  new Item('Rice', 8, 'White basmati rice, 2kg.', 'rice-removebg-preview.png', 0),
  new Item('Pasta', 3, 'Durum wheat spaghetti.', 'pasta-removebg-preview.png', 0),
  new Item('Tomato Sauce', 2, 'Classic tomato pasta sauce.', 'sauce-removebg-preview.png', 0),
  new Item('Cereal', 5, 'Honey oat breakfast cereal.', 'cereal-removebg-preview.png', 0),
  new Item('Juice', 4, 'Orange juice, 1 liter.', 'juice-removebg-preview.png', 0),
  new Item('Yogurt', 3, 'Plain Greek yogurt.', 'yogurt-removebg-preview.png', 0),
  new Item('Coffee', 10, 'Ground Arabica coffee.', 'coffee-removebg-preview.png', 0),
  new Item('Tea', 4, 'Black tea bags, 25 count.', 'tea-removebg-preview.png', 0),
  new Item('Toilet Paper', 6, 'Pack of 6 rolls.', 'toiletpaper-removebg-preview.png', 0),
  new Item('Soap', 2, 'Mild body soap bar.', 'soap-removebg-preview.png', 0),
  new Item('Shampoo', 5, 'Herbal shampoo, 250ml.', 'shampoo-removebg-preview.png', 0),
  new Item('Toothpaste', 3, 'Minty fresh toothpaste.', 'toothpaste-removebg-preview.png', 0),
  new Item('Detergent', 7, 'Laundry detergent, 1kg.', 'detergent-removebg-preview.png', 0)
];
````
in order to populate the web page and give the nessesary information classes are utilise and initialise in this section

````javaScript

function displayList(itemL) {
  const listItem = document.createElement('li');
  listItem.id = `item-${itemL.name}.jpg`;
  listItem.classList = 'list-group-item';
  listItem.setAttribute('style', 'display: flex; flex-direction: row;');

  const p = document.createElement('p');
  p.classList = 'col';
  p.textContent = `${itemL.name} $${itemL.price}`;
  listItem.appendChild(p);

  const buttonContainer = document.createElement('div');
  buttonContainer.classList = 'col';

  const menos = document.createElement('button');
  menos.id = `list-${itemL.name}--`;
  menos.type = 'button';
  menos.classList = 'btn btn-primary';
  menos.textContent = '-';
  buttonContainer.appendChild(menos);

  const quantity = document.createElement('button');
  quantity.id = `list-${itemL.name}-q`;
  quantity.classList = 'Qbutton';
  quantity.textContent = itemL.quantity;
  buttonContainer.appendChild(quantity);

  const mas = document.createElement('button');
  mas.id = `list-${itemL.name}-+`;
  mas.type = 'button';
  mas.classList = 'btn btn-primary';
  mas.textContent = '+';
  buttonContainer.appendChild(mas);

  const clear1 = document.createElement('button');
  clear1.id = `list-${itemL.name}-menos`;
  clear1.type = 'button';
  clear1.classList = 'btn btn-danger';
  clear1.textContent = 'delete';
  buttonContainer.appendChild(clear1);

  listItem.append(buttonContainer);
  document.getElementById('list').append(listItem);

  document.getElementById(`list-${itemL.name}-+`).addEventListener('click', function () {
    let q = Number(document.getElementById(`list-${itemL.name}-q`).textContent);
    document.getElementById(`list-${itemL.name}-q`).textContent = q + 1;
    itemL.quantity = q + 1;
    setQ(itemL.name, q + 1);
    displayTotal()
  });

  document.getElementById(`list-${itemL.name}--`).addEventListener('click', function () {
    let q = Number(document.getElementById(`list-${itemL.name}-q`).textContent);
    if (q !== 0) {
      document.getElementById(`list-${itemL.name}-q`).textContent = q - 1;
      itemL.quantity = q - 1;
      setQ(itemL.name, q - 1);
    }
    displayTotal()
  });

  document.getElementById(`list-${itemL.name}-menos`).addEventListener('click', function () {
    document.getElementById(`item-${itemL.name}.jpg`).remove();
    let str = localStorage.getItem('list');
    let str1 = JSON.parse(str);

    const str2 = str1.filter(item => item.name !== itemL.name);
    localStorage.setItem('list', JSON.stringify(str2));
    displayTotal()
  });
}
function displayTotal(){
  try{
  let list = localStorage.getItem('list');
  list = JSON.parse(list);
  let total=0;
  list.forEach(lit=>{
    total+=lit.quantity*lit.price;
  })
  
    document.getElementById('total').textContent=`the total amount for your purchase is $${total}`;
}catch{}
}
````
this function takes an array of clases to populate the list of selecteditems
````javaScript
function displayCard(itemList) {
  document.getElementById('shop').innerHTML = '';
  itemList.forEach((itemL) => {
    const card = document.createElement('div');
    card.classList = 'cart shadow p-3 mb-5 bg-body-tertiary rounded';
    card.style = 'width: 18rem;';

    const img = document.createElement('img');
    img.src = `img/${itemL.img}`;
    img.className = 'cart-img-top';
    img.alt = '...';
    card.append(img);

    const body = document.createElement('div');
    body.className = 'cart-body';

    const name = document.createElement('h5');
    name.textContent = `${itemL.name}  $${itemL.price}`;
    name.className = 'cart-title';
    body.append(name);

    const text = document.createElement('p');
    text.className = 'cart-text';
    text.textContent = `${itemL.description}`;
    body.append(text);

    const buttons = document.createElement('div');
    buttons.classList = 'btn-group container-fluid';
    buttons.role = 'group';

    const buttonMenos = document.createElement('button');
    buttonMenos.id = `cart-${itemL.name}--`;
    buttonMenos.type = 'button';
    buttonMenos.classList = 'btn btn-primary';
    buttonMenos.textContent = '-';
    buttons.append(buttonMenos);

    const buttonQ = document.createElement('button');
    buttonQ.id = `cart-${itemL.name}-q`;
    buttonQ.classList = 'Qbutton';
    buttonQ.textContent = '0';
    buttons.append(buttonQ);

    const buttonMas = document.createElement('button');
    buttonMas.id = `cart-${itemL.name}-+`;
    buttonMas.type = 'button';
    buttonMas.classList = 'btn btn-primary';
    buttonMas.textContent = '+';
    buttons.append(buttonMas);

    const buttonAd = document.createElement('button');
    buttonAd.id = `cart-${itemL.name}-add`;
    buttonAd.type = 'button';
    buttonAd.classList = 'btn btn-success';
    buttonAd.textContent = 'add to cart';
    buttons.append(buttonAd);

    body.append(buttons);
    card.append(body);
    document.getElementById('shop').append(card);

    document.getElementById(`cart-${itemL.name}-+`).addEventListener('click', () => {
      let q = Number(document.getElementById(`cart-${itemL.name}-q`).textContent);
      document.getElementById(`cart-${itemL.name}-q`).textContent = q + 1;
      itemL.quantity = q + 1;
    });

    document.getElementById(`cart-${itemL.name}--`).addEventListener('click', () => {
      let q = Number(document.getElementById(`cart-${itemL.name}-q`).textContent);
      if (q !== 0) {
        document.getElementById(`cart-${itemL.name}-q`).textContent = q - 1;
        itemL.quantity = q - 1;
      }
    });

    document.getElementById(`cart-${itemL.name}-add`).addEventListener('click', () => {
      try {
        let q = Number(document.getElementById(`cart-${itemL.name}-q`).textContent);
        let listq = Number(document.getElementById(`list-${itemL.name}-q`).textContent);
        document.getElementById(`list-${itemL.name}-q`).textContent = q + listq;
        document.getElementById(`cart-${itemL.name}-q`).innerHTML = 0;
        setQ(itemL.name, q + listq);
      } catch {
        document.getElementById(`cart-${itemL.name}-q`).innerHTML = 0;
        displayList(itemL);
        displayTotal();
        try {
          let list = localStorage.getItem('list');
          list = JSON.parse(list);
          list.push(itemL);
          localStorage.setItem('list', JSON.stringify(list));
        } catch {
          localStorage.setItem('list', JSON.stringify([itemL]));
        }
      }
      displayTotal()
    });
  });
}
````
this functio takes an array and populates the section that show the abailable items in the page
````javaScript
document.getElementById('searchBar').addEventListener('keyup', () => {
  const word = document.getElementById('searchBar').value.toLowerCase();
  const filtered = itemList1.filter(item => item.name.toLowerCase().includes(word));
  displayCard(filtered);
});
````
this event listener only shoe the items that match in name in real time whith the input of the search barr
````javaScript
displayCard(itemList1);

if (getCookie('visited')) {
  alert('Welcome, nice to have you again');
} else {
  alert('Hi, thanks for visiting');
}

setCookie('visited', true);
try{
let list3 = localStorage.getItem('list');
list3 = JSON.parse(list3);
list3.forEach(lit => {
  displayList(lit);
});
displayTotal();
}catch{}
function setQ(name, quantity) {
  let list4 = localStorage.getItem('list');
  list4 = JSON.parse(list4);
  list4.forEach(lit => {
    if (lit.name === name) {
      lit.quantity = quantity;
    }
  });
  localStorage.setItem('list', JSON.stringify(list4));
}

function deleteCookie(name) {
  document.cookie = `${name}=; expires=Thu, 01 Jan 1970 00:00:00; path=/`;
}

function setCookie(name, value) {
  const date = new Date();
  date.setDate(date.getDate() + 7);
  document.cookie = `${name}=${value}; expires=${date}; path=/`;
}

function getCookie(name) {
  const match = document.cookie.split("; ").find(row => row.startsWith(name + "="));
  return match?.split("=")[1];
}

````
this section will chech is the user have visited before show the respective mesage and popolate the item list if the user had someting on there 
````javaScript
let time;

try {
  time = sessionStorage.getItem('time');
  time = JSON.parse(time);
} catch {
  sessionStorage.setItem('time', '0');
  time = 0;
}

setInterval(() => {
  time++;
  document.getElementById('timer').textContent = `${minutes(time)} hour(s) spend on this app`;
sessionStorage.setItem('time', JSON.stringify(time));
}, 1000);

function minutes(n) {
  let hour,minute,seconds;
  hour=parseInt(n/3600);
  minute=parseInt((n-(hour*3600))/60);
  seconds=n-((hour*3600)+(minute*60));  
  return `${hour}:${minute}:${seconds}`;
}

````
this section will keep track of the time spend in the app
````javaScript
document.getElementById('dark-theme').addEventListener('click', () => {
  document.getElementsByTagName('html')[0].dataset.bsTheme = 'dark';
  localStorage.setItem('theme', 'dark');
});

document.getElementById('light-theme').addEventListener('click', () => {
  document.getElementsByTagName('html')[0].dataset.bsTheme = 'light';
  localStorage.setItem('theme', 'light');
});

try {
  document.getElementsByTagName('html')[0].dataset.bsTheme = localStorage.getItem('theme');
} catch {}
````
this section is to chnage the theme of the page the options are light and dark
