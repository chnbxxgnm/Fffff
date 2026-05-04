<h2>🛒 รายการสั่งอาหาร</h2>
<div id="cart"></div>

<script>
let cart = [];

function addToCart(name, price) {
  cart.push({name, price});
  renderCart();
}

function renderCart() {
  let html = "";
  let total = 0;

  cart.forEach(item => {
    total += Number(item.price);
    html += `<div class="card">${item.name} - ${item.price} บาท</div>`;
  });

  html += `<h3>รวม: ${total} บาท</h3>`;
  document.getElementById("cart").innerHTML = html;
}

function sendOrder() {
  let text = "ออเดอร์:\n";
  let total = 0;

  cart.forEach(item => {
    text += `- ${item.name} ${item.price} บาท\n`;
    total += Number(item.price);
  });

  text += `รวม ${total} บาท`;

  window.open("https://line.me/R/msg/text/?" + encodeURIComponent(text));
}
</script>
