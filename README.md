# GHARTAK-GROCERY[index.html](https://github.com/user-attachments/files/25456412/index.html)
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GharTak Grocery</title>

<style>
body{font-family:Arial;margin:0;background:#f1f1f1}
header{background:green;color:white;padding:15px;text-align:center;font-size:22px}
.banner{background:orange;color:white;padding:10px;text-align:center}
.container{display:flex;flex-wrap:wrap;justify-content:center}
.product{background:white;width:160px;margin:8px;padding:10px;border-radius:10px;text-align:center}
button{background:green;color:white;border:none;padding:7px;border-radius:5px}
#cart{background:white;margin:10px;padding:10px;border-radius:10px}
</style>
</head>

<body>

<header>🛒 GharTak Grocery</header>
<div class="banner">🚚 Free Delivery on order above ₹249</div>

<center>
<input type="text" placeholder="Search सामान खोजें" onkeyup="searchProduct()" id="search">
</center>

<div class="container" id="products"></div>

<div id="cart">
<h3>🧾 Cart</h3>
<ul id="cartItems"></ul>
<h3>Total ₹ <span id="total">0</span></h3>
<h4 id="deliveryMsg"></h4>

<a href="upi://pay?pa=9771622955@ybl&pn=GharTak Grocery">
<button>Pay via UPI</button></a>

<button onclick="orderNow()">Order on WhatsApp</button>
</div>

<script>

let productData=[
{name:"Aloo",price:30},
{name:"Pyaz",price:35},
{name:"Tamatar",price:40},
{name:"Rice",price:60},
{name:"Atta",price:260},
{name:"Arhar Dal",price:140},
{name:"Milk",price:60},
{name:"Paneer",price:340},
{name:"Parle-G",price:10},
{name:"Surf Excel",price:120}
];

let total=0;
let cartData="";

function loadProducts(){
let html="";
productData.forEach(p=>{
html+=`<div class="product">
<h4>${p.name}</h4>
<p>₹${p.price}</p>
<button onclick="addToCart('${p.name}',${p.price})">Add</button>
</div>`;
});
products.innerHTML=html;
}
loadProducts();

function addToCart(name,price){
cartData+=name+" ₹"+price+"%0A";
total+=price;
document.getElementById("total").innerText=total;

let li=document.createElement("li");
li.innerText=name+" ₹"+price;
cartItems.appendChild(li);

checkDelivery();
}

function checkDelivery(){
if(total>=249){
deliveryMsg.innerHTML="🎉 You got FREE Delivery";
deliveryMsg.style.color="green";
}
else{
deliveryMsg.innerHTML="Add ₹"+(249-total)+" more for FREE delivery";
deliveryMsg.style.color="red";
}
}

function orderNow(){
let msg="Order Details:%0A"+cartData+"Total ₹"+total+"%0AFree Delivery above ₹249";
window.open("https://wa.me/919771622955?text="+msg);
}

function searchProduct(){
let input=document.getElementById("search").value.toLowerCase();
let products=document.getElementsByClassName("product");
for(let i=0;i<products.length;i++){
products[i].style.display=products[i].innerText.toLowerCase().includes(input)?"block":"none";
}
}

</script>

</body>
</html>
