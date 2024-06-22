<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>แบบทดสอบก่อนเรียน-หลังเรียน กลอนบทละคร ม.2/1</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f4f4f4;
        }
        .question, .info {
            margin-bottom: 20px;
        }
        .question h3, .info h3 {
            margin-bottom: 10px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 20px;
        }
        .message {
            margin-top: 20px;
            font-size: 16px;
            font-weight: bold;
            color: green; 
        }
    </style>
</head>
<body>
    <h1>แบบทดสอบก่อนเรียน-หลังเรียน กลอนบทละคร ม.2</h1>

    <div class="info">
        <h3>กรุณากรอกชื่อ-สกุลของคุณ</h3>
        <input type="text" id="name" placeholder="ชื่อ-สกุล"><br>
        <h3>กรุณากรอกเลขที่ของคุณ</h3>
        <input type="text" id="studentNumber" placeholder="เลขที่">
    </div>

    <div class="result" id="result"></div>

    <div class="question">
        <h3>๑. การอ่านกลอนบทละคร ถ้าจำนวนคำในวรรคมี ๖ คำควรแบ่งคำอย่างไร</h3>
        <label><input type="radio" name="q1" value="ก"> ก. ๑/๒/๓</label><br>
        <label><input type="radio" name="q1" value="ข"> ข. ๒/๒/๒</label><br>
        <label><input type="radio" name="q1" value="ค"> ค. ๓/๑/๒</label><br>
        <label><input type="radio" name="q1" value="ง"> ง. ๑/๔/๑</label>
    </div>

    <div class="question">
        <h3>๒. เพราะเหตุใด กลอนบทละคร จึงควรมีจำนวนคำในแต่ละวรรค ๖ – ๗ คำ ซึ่งถือว่าเหมาะสมที่สุด</h3>
        <label><input type="radio" name="q2" value="ก"> ก. เพื่อให้มีความหมายที่ครบถ้วนและกระชับ</label><br>
        <label><input type="radio" name="q2" value="ข"> ข. เพื่อให้สอดคล้องกับจังหวะการร้องและการรำ</label><br>
        <label><input type="radio" name="q2" value="ค"> ค. เพื่อให้สามารถแสดงความรู้สึกและอารมณ์ได้มากขึ้น</label><br>
        <label><input type="radio" name="q2" value="ง"> ง. เพื่อให้มีการเล่นเสียงสัมผัสภายในวรรคอย่างสวยงาม</label>
    </div>

    <div class="question">
        <h3>๓. ข้อใด ไม่ใช่ คำขึ้นต้นของกลอนบทละคร</h3>
        <label><input type="radio" name="q3" value="ก"> ก. บัดนั้น</label><br>
        <label><input type="radio" name="q3" value="ข"> ข. เมื่อนั้น</label><br>
        <label><input type="radio" name="q3" value="ค"> ค. ตอนนั้น</label><br>
        <label><input type="radio" name="q3" value="ง"> ง. มาจะกล่าวบทไป</label>
    </div>

    <div class="question">
        <h3>๔. การขึ้นต้นเรื่อง หรือเริ่มเหตุการณ์ใหม่ ใช้คำขึ้นต้นใด</h3>
        <label><input type="radio" name="q4" value="ก"> ก. บัดนั้น</label><br>
        <label><input type="radio" name="q4" value="ข"> ข. เมื่อนั้น</label><br>
        <label><input type="radio" name="q4" value="ค"> ค. ตอนนั้น</label><br>
        <label><input type="radio" name="q4" value="ง"> ง. มาจะกล่าวบทไป</label>
    </div>

    <div class="question">
        <h3>๕. การกล่าวถึงตัวละครที่เป็นตัวเอก ใช้คำขึ้นต้นใด</h3>
        <label><input type="radio" name="q5" value="ก"> ก. บัดนั้น</label><br>
        <label><input type="radio" name="q5" value="ข"> ข. เมื่อนั้น</label><br>
        <label><input type="radio" name="q5" value="ค"> ค. ตอนนั้น</label><br>
        <label><input type="radio" name="q5" value="ง"> ง. มาจะกล่าวบทไป</label>
    </div>

    <button onclick="checkAnswers()">ส่งคำตอบ</button>

    <div class="message" id="message"></div>

    <script>
        function checkAnswers() {
            const correctAnswers = {
                q1: 'ข',
                q2: 'ข',
                q3: 'ค',
                q4: 'ง',
                q5: 'ข'
            };

            let score = 0;
            let allAnswered = true;
            for (const [question, answer] of Object.entries(correctAnswers)) {
                const selected = document.querySelector(`input[name="${question}"]:checked`);
                if (!selected) {
                    allAnswered = false;
                    break;
                }
                if (selected.value === answer) {
                    score++;
                }
            }

            const name = document.getElementById('name').value.trim();
            const studentNumber = document.getElementById('studentNumber').value.trim();

            if (name === "" || studentNumber === "") {
                alert("กรุณากรอกชื่อ-สกุลและเลขที่ของคุณ");
                return;
            }

            if (!allAnswered) {
                alert("กรุณาตอบคำถามทุกข้อ");
                return;
            }

            document.getElementById('result').innerText = `${name} คุณได้คะแนน ${score} / 5`;
            document.getElementById('message').innerText = "ตรวจสอบคะแนนของคุณด้านบน";
        }
    </script>
</body>
</html>
