# Project_Qr_scan
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Indofood Warehouse QR Scan</title>

<script src="https://unpkg.com/html5-qrcode"></script>

<style>
body{
    margin:0;
    font-family:Segoe UI,Arial,sans-serif;
    background:#f2f2f2;
}

/* HEADER */
header{
    background:linear-gradient(90deg,#b30000,#003a8f);
    text-align:center;
    padding:24px 10px;
    box-shadow:0 4px 12px rgba(0,0,0,.3);
}
header img{
    height:65px;
    display:block;
    margin:0 auto 10px;
}
header h1{
    margin:0;
    color:#fff;
    font-size:26px;
    letter-spacing:2px;
}

/* CONTAINER */
.container{
    padding:25px 15px;
    max-width:500px;
    margin:auto;
}

/* CARD */
.card{
    background:#fff;
    border-radius:18px;
    padding:25px;
    margin-bottom:25px;
    box-shadow:0 8px 20px rgba(0,0,0,.15);
    border-top:5px solid #b30000;
}
.card h2{
    text-align:center;
    color:#003a8f;
    margin-bottom:20px;
    border-bottom:2px solid #003a8f;
    padding-bottom:8px;
}

/* DATA */
.data-row{
    display:flex;
    justify-content:space-between;
    font-size:18px;
    margin:14px 0;
}
.label{font-weight:600;color:#555}
.value{font-weight:700}

.ok{color:#1fa84f}
.reject{color:#d60000}

/* FOOTER */
footer{
    text-align:center;
    font-size:13px;
    color:#777;
    padding-bottom:20px;
}
</style>
</head>

<body>

<header>
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAWgAAABkCAYAAACn5k+ZAAAACXBIWXMAAAsTAAALEwEAmpwYAAAGX0lEQVR4nO3dS2wUVRzH8e+2y7ZsFJQ0UAtNQkKQpCQtBBE0K0rQqgY2kA0sVJQY0gFEBSqYgQ0mQmC0pAgQFIk0YgG0E0hNCCwK0pJQ0i2y7z3Z2f3X9zv2fM7M3nvvPef8+7z3nPuQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAPhP7oZkY2Nj8+fPj4+Pf//+vb29vb+/v9OnT8fHx5ubm9PT07NmzY2Nj5ubm7u7u0tLS3Nzc9PT0wMDA6Ojo4uLi+vr6q1evFhYWKioqNjY2Ojo6Kioqtra2NjY2CwsLQ0NDc3NzR0dH6+vrGxsbKysrPz8/k5OTBwcHExMTq6urvLy8dHR0g4ODmZmZp6en6enpWVlZbW1tZGRkXFxcq6urV1dXExMTIyMjDw8P7+/vMzMzvLy8dHR0kJCQoqKipqammpqa6urq9vb2goKC2tra4ODg9PT0vLy8jIyM2NjYyMjI2NjYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAPgP/gMZQZqz9w4fYAAAAABJRU5ErkJggg==" alt="Logo Indofood">
<h1>WAREHOUSE QR SCAN SYSTEM</h1>
</header>

<div class="container">

<div class="card">
<h2>SCAN QR CODE</h2>
<div id="reader"></div>
</div>

<div class="card">
<h2>DETAIL PRODUK</h2>

<div class="data-row">
<span class="label">Nama Produk</span>
<span id="nama" class="value">-</span>
</div>

<div class="data-row">
<span class="label">Berat (KG)</span>
<span id="berat" class="value">-</span>
</div>

<div class="data-row">
<span class="label">Status</span>
<span id="status" class="value">-</span>
</div>
</div>

</div>

<footer>Soal Test Programmer – Sistem Gudang Indofood</footer>

<script>
const database={
"1":{nama:"Indomie Kari",berat:"100",status:"OKE"},
"2":{nama:"Indomie Soto",berat:"500",status:"REJECT"},
"3":{nama:"Indomie Goreng",berat:"600",status:"OKE"},
"4":{nama:"Sarimi",berat:"400",status:"REJECT"},
"5":{nama:"Supermi",berat:"200",status:"OKE"}
};

function onScanSuccess(text){
const id=text.match(/\d+/)?.[0];
if(!database[id]) return alert("Produk tidak ditemukan");

const d=database[id];
nama.innerText=d.nama;
berat.innerText=d.berat+" KG";
status.innerText=d.status;
status.className="value "+(d.status==="OKE"?"ok":"reject");
}

new Html5Qrcode("reader").start(
{facingMode:"environment"},
{fps:10,qrbox:260},
onScanSuccess
);
</script>

</body>
</html>
