<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Basit Çeviri</title>
<style>
body{
font-family: Arial;
text-align:center;
background:#f2f2f2;
padding:30px;
}

textarea{
width:80%;
height:120px;
margin:10px;
padding:10px;
}

button{
padding:10px 20px;
font-size:16px;
cursor:pointer;
}
</style>
</head>

<body>

<h2>Çeviri Sitesi</h2>

<textarea id="inputText" placeholder="Metin yaz"></textarea>
<br>

<select id="targetLang">
<option value="en">İngilizce</option>
<option value="tr">Türkçe</option>
<option value="de">Almanca</option>
<option value="fr">Fransızca</option>
</select>

<br><br>

<button onclick="translateText()">Çevir</button>

<textarea id="outputText" placeholder="Çeviri burada çıkacak"></textarea>

<script>
async function translateText() {

let text = document.getElementById("inputText").value;
let target = document.getElementById("targetLang").value;

let url = "https://api.mymemory.translated.net/get?q=" + text + "&langpair=tr|" + target;

let response = await fetch(url);
let data = await response.json();

document.getElementById("outputText").value = data.responseData.translatedText;

}
</script>

</body>
</html>
