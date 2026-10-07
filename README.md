<!DOCTYPE html>
<html lang="mn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Social Test Generator</title>

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
            margin-bottom: 25px;
        }

        button {
            display: block;
            margin: 20px auto;
            padding: 14px 30px;
            font-size: 18px;
            cursor: pointer;
            border: none;
            border-radius: 8px;
        }

        .question {
            margin-top: 25px;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 10px;
        }

        .question h3 {
            margin-top: 0;
        }

        .answer {
            margin: 8px 0;
        }

        #result {
            margin-top: 25px;
        }

        @media print {
            button {
                display: none;
            }

            body {
                background: white;
            }
        }
    </style>
</head>

<body>

<div class="container">

    <h1>📚 Нийгмийн ухааны тестийн сан</h1>

    <p class="info">
        Санамсаргүй асуулт сонгон шалгалтын материал үүсгэгч
    </p>

    <button onclick="generateTest()">
        🎲 Шалгалт үүсгэх
    </button>

    <div id="result"></div>

</div>

<script>

const questions = [

{
    question: "Монгол Улс НҮБ-д хэдэн онд элссэн бэ?",
    answers: [
        "1945 он",
        "1955 он",
        "1961 он",
        "1971 он"
    ],
    correct: 2
},

{
    question: "Соёлын үндсэн бүрэлдэхүүнд аль нь хамаарах вэ?",
    answers: [
        "Хэл",
        "Бэлгэдэл",
        "Үнэт зүйл",
        "Дээрх бүгд"
    ],
    correct: 3
},

{
    question: "Нийгэм гэж юу вэ?",
    answers: [
        "Зөвхөн хүмүүсийн бөөгнөрөл",
        "Харилцан үйлдэл бүхий хүмүүсийн тогтвортой харилцааны тогтолцоо",
        "Зөвхөн гэр бүл",
        "Зөвхөн төр"
    ],
    correct: 1
},

{
    question: "Инфляци гэж юу вэ?",
    answers: [
        "Ажилгүйдэл буурах",
        "Бараа үйлчилгээний үнийн ерөнхий түвшин өсөх",
        "Цалин буурах",
        "Экспорт нэмэгдэх"
    ],
    correct: 1
},

{
    question: "Монгол Улсын Үндсэн хууль хэдэн онд батлагдсан бэ?",
    answers: [
        "1924 он",
        "1940 он",
        "1960 он",
        "1992 он"
    ],
    correct: 3
},

{
    question: "Нийгмийн давхраажилт гэж юу вэ?",
    answers: [
        "Нийгмийн бүлгүүдийг ялган ангилах үзэгдэл",
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
        "Ажиллах насны бүх хүн ажилгүй байх",
        "Ажиллах чадвартай, ажиллах хүсэлтэй боловч ажилгүй байх",
        "Сургуульд сурах"
    ],
    correct: 2
},

{
    question: "Эдийн засгийн гол нөөцийн нэг аль вэ?",
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

    let newArray = [...array];

    for (let i = newArray.length - 1; i > 0; i--) {

        const j = Math.floor(Math.random() * (i + 1));

        [newArray[i], newArray[j]] =
        [newArray[j], newArray[i]];
    }

    return newArray;
}


function generateTest() {

    const selected =
        shuffle(questions).slice(0, 5);

    let html =
        "<h2>📝 Шалгалтын материал</h2>";

    selected.forEach((q, index) => {

        html += `
        <div class="question">

            <h3>
                ${index + 1}. ${q.question}
            </h3>

            ${q.answers.map((answer, i) => `
                <div class="answer">
                    ${String.fromCharCode(65 + i)}. ${answer}
                </div>
            `).join("")}

        </div>
        `;

    });

    html += `
        <button onclick="window.print()">
            🖨️ Хэвлэх
        </button>
    `;

    document.getElementById("result").innerHTML = html;
}

</script>

</body>
</html>
