<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Нийгмийн ухааны тест үүсгэгч</title>

<style>
body {
    font-family: Arial, sans-serif;
    background: #f2f4f7;
    margin: 0;
    padding: 30px;
}

.container {
    max-width: 900px;
    margin: auto;
    background: white;
    padding: 30px;
    border-radius: 15px;
}

h1 {
    text-align: center;
}

.info {
    text-align: center;
    color: #555;
}

button {
    display: block;
    margin: 25px auto;
    padding: 14px 30px;
    font-size: 18px;
    cursor: pointer;
}

.question {
    margin-top: 20px;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 10px;
}

.answer {
    margin: 10px 0;
}
</style>
</head>

<body>

<div class="container">

<h1>📚 Нийгмийн ухааны тестийн сан</h1>

<p class="info">
Санамсаргүй асуулт сонгон шалгалтын материал үүсгэгч
</p>

<button id="generateButton">
🎲 Шалгалт үүсгэх
</button>

<div id="result"></div>

</div>

<script>

const questions = [

{
question: "Монгол Улс НҮБ-д хэдэн онд элссэн бэ?",
answers: ["1945 он", "1955 он", "1961 он", "1971 он"],
correct: 2
},

{
question: "Соёлын үндсэн бүрэлдэхүүнд аль нь хамаарах вэ?",
answers: ["Хэл", "Бэлгэдэл", "Үнэт зүйл", "Дээрх бүгд"],
correct: 3
},

{
question: "Нийгэм гэж юу вэ?",
answers: [
"Зөвхөн хүмүүсийн бөөгнөрөл",
"Харилцан үйлдэл бүхий хүмүүсийн тогтолцоо",
"Зөвхөн гэр бүл",
"Зөвхөн төр"
],
correct: 1
},

{
question: "Инфляци гэж юу вэ?",
answers: [
"Бараа үйлчилгээний үнийн ерөнхий түвшин өсөх",
"Ажилгүйдэл буурах",
"Цалин буурах",
"Экспорт нэмэгдэх"
],
correct: 0
},

{
question: "Монгол Улсын Үндсэн хууль хэдэн онд батлагдсан бэ?",
answers: ["1924", "1940", "1960", "1992"],
correct: 3
},

{
question: "Нийгмийн давхраажилт гэж юу вэ?",
answers: [
"Нийгмийн бүлгүүдийн ялгарал",
"Зөвхөн насны ялгаа",
"Зөвхөн хүйсийн ялгаа",
"Зөвхөн хэлний ялгаа"
],
correct: 0
},

{
question: "Ардчиллын үндсэн зарчмын нэг аль вэ?",
answers: [
"Иргэдийн оролцоо",
"Нэг хүний эрх мэдэл",
"Цэргийн засаглал",
"Хаант засаглал"
],
correct: 0
},

{
question: "Ажилгүйдэл гэж юу вэ?",
answers: [
"Ажиллах хүсэлгүй байх",
"Ажиллах чадвартай, ажиллах хүсэлтэй боловч ажилгүй байх",
"Бүх хүн ажилгүй байх",
"Сургуульд сурах"
],
correct: 1
},

{
question: "Эдийн засгийн үндсэн нөөцийн нэг аль вэ?",
answers: [
"Газар",
"Зөвхөн мөнгө",
"Зөвхөн компьютер",
"Зөвхөн үйлдвэр"
],
correct: 0
},

{
question: "Хүний эрхийн үндсэн шинж аль вэ?",
answers: [
"Хүн бүрт хамаарна",
"Зөвхөн баян хүнд хамаарна",
"Зөвхөн төрийн албан хаагчид хамаарна",
"Зөвхөн насанд хүрэгчдэд хамаарна"
],
correct: 0
}

];


function shuffle(array) {

let newArray = array.slice();

for (let i = newArray.length - 1; i > 0; i--) {

let j = Math.floor(Math.random() * (i + 1));

let temp = newArray[i];

newArray[i] = newArray[j];

newArray[j] = temp;

}

return newArray;

}


function generateTest() {

let selected = shuffle(questions).slice(0, 5);

let html = "<h2>📝 Шалгалтын материал</h2>";

selected.forEach(function(q, index) {

html += "<div class='question'>";

html += "<h3>" + (index + 1) + ". " + q.question + "</h3>";

q.answers.forEach(function(answer, i) {

html += "<div class='answer'>";

html += String.fromCharCode(65 + i) + ". " + answer;

html += "</div>";

});

html += "</div>";

});

html += "<button onclick='window.print()'>🖨️ Хэвлэх</button>";

document.getElementById("result").innerHTML = html;

}


document.getElementById("generateButton").addEventListener(
"click",
generateTest
);

</script>

</body>
</html>
