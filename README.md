<!DOCTYPE html>
<html>
<head>

<meta charset="UTF-8">

<title>Bản cam kết</title>

<script src="https://cdn.jsdelivr.net/npm/signature_pad@4.0.0/dist/signature_pad.umd.min.js"></script>

<style>

body{
font-family:Arial;
background:#f4f4f4;
text-align:center;
padding:20px;
}

.box{
background:white;
padding:20px;
border-radius:10px;
max-width:600px;
margin:auto;
}

canvas{
border:2px solid black;
width:100%;
height:200px;
}

button{
padding:10px;
margin:5px;
}

input{
padding:10px;
width:80%;
}

.signature{
margin-top:20px;
border-top:1px solid #ccc;
padding:10px;
}

img{
width:200px;
}

</style>

</head>

<body>

<div class="box">

<h2>BẢN CAM KẾT</h2>

<p>
Tôi cam kết sẽ thực hiện đúng những điều đã thống nhất.
Nếu vi phạm tôi sẽ chịu trách nhiệm với lời cam kết này.
</p>

<h3>Những người đã ký</h3>

<div id="list"></div>

<hr>

<input id="name" placeholder="Tên của bạn">

<br><br>

<canvas id="pad"></canvas>

<br>

<button onclick="clearPad()">Xóa chữ ký</button>

<button onclick="submitSign()">Cam kết</button>

</div>

<script>

const canvas=document.getElementById("pad");
const signaturePad=new SignaturePad(canvas);

let list=[];

function render(){

const box=document.getElementById("list");

box.innerHTML="";

list.forEach(p=>{

box.innerHTML+=`
<div class="signature">
<b>${p.name}</b>
<br>
<img src="${p.sign}">
</div>
`

})

}

function clearPad(){

signaturePad.clear()

}

function submitSign(){

const name=document.getElementById("name").value

if(name==""){
alert("Nhập tên trước")
return
}

if(signaturePad.isEmpty()){
alert("Hãy ký tên")
return
}

const sign=signaturePad.toDataURL()

list.push({
name:name,
sign:sign
})

signaturePad.clear()

render()

}

</script>

</body>

</html>
