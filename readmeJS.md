# javaScript capstone Web app
## table of content
1. variable naming 
2. function naming
3. array & object usage
4. array method
5. looping/iteration
6. JSON Data Handeling
7. Web Storge
8. Saving/Retriving User Data
9. COokies with expiry
10. DOM manipultion
11. CSS Manipulation via JS
12. theme preference
13. comments & code realability
14. Error handeling & debuging
15. regex validtion
16. timer & date object
17. math,string,ramndom methods
18. event listeners
19. real-time search & history
20. crud functionality
## variable naming
````javaScript
let total = 0;
````
## function naming
````javaScript
function displayCard(itemList) {};
````
## array & object usage
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
````
## array method
````javaScript
// add quantity list
  const mas = document.createElement('button');
  mas.id = `list-${itemL.name}-+`;
  mas.type = 'button';
  mas.classList = 'btn btn-primary';
  mas.textContent = '+';
  buttonContainer.appendChild(mas);
````
## looping/iteration
````javaScript
list.forEach(lit=>{
    total+=lit.quantity*lit.price;
  })
````
## JSON Data Handeling
````javaScript
let str = localStorage.getItem('list');
    let str1 = JSON.parse(str);
````
##  Web Storge
````javaScript
localStorage.setItem('list', JSON.stringify([itemL]));
````
## Saving/Retriving User Data
````javaScript
 let str = localStorage.getItem('list');
````
## Cookies with expiry
````javaScript
  document.cookie = `${name}=; expires=Thu, 01 Jan 1970 00:00:00; path=/`;
````
## DOM manipulation
````javaScript
const card = document.createElement('div');
    card.classList = 'cart shadow p-3 mb-5 bg-body-tertiary rounded';
    
````
## CSS Manipulation via JS
````javaScript
card.style = 'width: 18rem;';
````
## theme preference
````javaScript
document.getElementById('dark-theme').addEventListener('click', () => {
  document.getElementsByTagName('html')[0].dataset.bsTheme = 'dark';
  localStorage.setItem('theme', 'dark');
});
````
## comments & code realability
````javaScript
 // add quantity list
  const mas = document.createElement('button');
  mas.id = `list-${itemL.name}-+`;
  mas.type = 'button';
  mas.classList = 'btn btn-primary';
  mas.textContent = '+';
  buttonContainer.appendChild(mas);
````
## Error handeling & debuging

````javaScript
 try{
  let list = localStorage.getItem('list');
  list = JSON.parse(list);
  let total=0;
  list.forEach(lit=>{
    total+=lit.quantity*lit.price;
  })
  
    document.getElementById('total').textContent=`the total amount for your purchase is $${total}`;
}catch{}
````
## regex validtion
````javaScript
document.getElementById('searchBar').addEventListener('keyup', () => {
  const word = document.getElementById('searchBar').value.toLowerCase();
  const filtered = itemList1.filter(item => item.name.toLowerCase().includes(word));
  displayCard(filtered);
});
````
## timer & date object
````javaScript
setInterval(() => {
  time++;
  document.getElementById('timer').textContent = `${minutes(time)} hour(s) spend on this app`;
sessionStorage.setItem('time', JSON.stringify(time));
}, 1000);
````
## math,string,ramndom methods

````javaScript
function minutes(n) {
  let hour,minute,seconds;
  hour=parseInt(n/3600);
  minute=parseInt((n-(hour*3600))/60);
  seconds=n-((hour*3600)+(minute*60));  
  return `${hour}:${minute}:${seconds}`;
}
````
## event listeners
````javaScript
document.getElementById(`list-${itemL.name}-+`).addEventListener
````
## real-time search & history
````javaScript
document.getElementById('searchBar').addEventListener('keyup', () => {
  const word = document.getElementById('searchBar').value.toLowerCase();
  const filtered = itemList1.filter(item => item.name.toLowerCase().includes(word));
  displayCard(filtered);
});
````
## crud functionality
````javaScript
list.push(itemL);
````

