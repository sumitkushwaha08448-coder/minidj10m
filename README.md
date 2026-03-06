<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Minidj_10m Store</title>
<style>
body{margin:0;font-family:Arial;background:#0e0e0e;color:white}
header{background:#111;padding:15px 30px;display:flex;justify-content:space-between;align-items:center}
.logo{font-size:24px;color:#00eaff;font-weight:bold}
.products{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:20px;padding:30px}
.card{background:#1b1b1b;border-radius:12px;padding:20px;text-align:center}
.card img{width:100%;border-radius:10px}
.price{font-size:20px;margin:10px 0;color:#00eaff}
button{padding:10px 16px;border:none;border-radius:6px;background:#00eaff;font-weight:bold;cursor:pointer}
.cart{position:fixed;right:0;top:0;background:#151515;width:300px;height:100%;padding:20px;overflow:auto}
.cart h2{margin-top:0}
.checkout{margin-top:20px;background:#25D366;color:white;width:100%}
footer{text-align:center;padding:20px;background:#111}
</style>
</head>
<body><header>
<div class="logo">🎧 Minidj_10m</div>
<div>Mini DJ Products Store</div>
</header><section class="products" id="productList"></section><div class="cart" id="cart">
<h2>Cart</h2>
<ul id="cartItems"></ul>
<h3 id="total">Total: ₹0</h3>
<button class="checkout" onclick="payUPI()">Pay with UPI</button>
<button class="checkout" style="margin-top:10px" onclick="checkout()">Order on WhatsApp</button>
</div><footer>
📍 Jhansi, Uttar Pradesh<br>
Order WhatsApp: 7068969479
</footer><script>
const products=[
{name:"Mini DJ Speaker",price:1499,img:"https://images.unsplash.com/photo-1519677100203-a0e668c92439"},
{name:"Mini DJ Light",price:699,img:"https://images.unsplash.com/photo-1514525253161-7a46d19cd819"},
{name:"Mini DJ Controller",price:2499,img:"https://images.unsplash.com/photo-1505740420928-5e560c06d30e"}
];

let cart=[];

function renderProducts(){
const container=document.getElementById("productList");
products.forEach((p,i)=>{
container.innerHTML+=`<div class='card'>
<img src='${p.img}'>
<h3>${p.name}</h3>
<div class='price'>₹${p.price}</div>
<button onclick='addToCart(${i})'>Add to Cart</button>
</div>`
});
}

function addToCart(i){
cart.push(products[i]);
updateCart();
}

function updateCart(){
const list=document.getElementById("cartItems");
list.innerHTML="";
let total=0;
cart.forEach(p=>{
list.innerHTML+=`<li>${p.name} - ₹${p.price}</li>`;

total+=p.price;
});

document.getElementById("total").innerText="Total: ₹"+total;
}

function payUPI(){
let total=0;
cart.forEach(p=>{ total+=p.price; });
if(total===0){ alert("Cart is empty"); return; }
const upi=`upi://pay?pa=skcup@ybl&pn=Minidj_10m&am=${total}&cu=INR`;
window.location.href=upi;
}

function checkout(){
let text="Order from Minidj_10m:%0A";
let total=0;
cart.forEach(p=>{
text+=p.name+" - ₹"+p.price+"%0A";

total+=p.price;
});
text+="Total: ₹"+total+"%0A(Payment via UPI: skcup@ybl)";

window.open("https://wa.me/917068969479?text="+text);
});
text+="Total: ₹"+total;

window.open("https://wa.me/917068969479?text="+text);
}

renderProducts();
</script></body>
</html>
