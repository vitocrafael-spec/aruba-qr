[index.html](https://github.com/user-attachments/files/25474542/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ARUBA QR</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
<style>
body{
font-family:'Inter',sans-serif;
background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);
color:white;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
margin:0;
}
.container{
background:#111;
padding:30px;
border-radius:20px;
width:350px;
text-align:center;
box-shadow:0 10px 30px rgba(0,0,0,0.5);
}
h1{
margin-bottom:20px;
}
select,input{
width:100%;
padding:10px;
margin:8px 0;
border:none;
border-radius:10px;
font-size:14px;
}
button{
background:#00c6ff;
border:none;
padding:12px;
border-radius:10px;
width:100%;
margin-top:10px;
font-weight:bold;
cursor:pointer;
}
#qrcode{
margin-top:20px;
display:flex;
justify-content:center;
}
.download{
background:#28a745;
margin-top:10px;
}
</style>
</head>
<body>

<div class="container">
<h1>ARUBA QR</h1>

<select id="type">
<option value="whatsapp">WhatsApp</option>
<option value="link">Link</option>
<option value="text">Texto</option>
</select>

<input type="text" id="data" placeholder="Digite o número ou link">
<input type="color" id="color" value="#000000">

<button onclick="generateQR()">Gerar QR Code</button>

<div id="qrcode"></div>

<button class="download" onclick="downloadQR()">Baixar PNG</button>

</div>

<script>
let qr;

function generateQR(){
const type=document.getElementById("type").value;
let data=document.getElementById("data").value;
const color=document.getElementById("color").value;

if(type==="whatsapp"){
data="https://wa.me/"+data.replace(/\D/g,'');
}

document.getElementById("qrcode").innerHTML="";

qr=new QRCode(document.getElementById("qrcode"),{
text:data,
width:200,
height:200,
colorDark:color,
colorLight:"#ffffff"
});
}

function downloadQR(){
const img=document.querySelector("#qrcode img");
if(!img){alert("Gere um QR primeiro!");return;}
const link=document.createElement("a");
link.href=img.src;
link.download="aruba-qr.png";
link.click();
}
</script>

</body>
</html>
