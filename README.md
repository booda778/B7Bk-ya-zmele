<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حساب السعرات - بودا محمد</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f9;
            margin: 0;
            padding: 20px;
            direction: rtl;
        }
        .header {
            background-color: #007BFF;
            color: white;
            padding: 20px;
            font-size: 24px;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            padding: 10px 20px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
        }
        .footer {
            margin-top: 20px;
            font-size: 14px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="header">بحبك يا صديقي بودا محمد ❤️</div>
    <div class="container">
        <h1>حساب السعرات اليومية</h1>
        <p>أدخل البيانات لمعرفة السعرات اللازمة لزيادة أو نقصان الوزن</p>
        <form id="calorieForm">
            <input type="number" id="weight" placeholder="الوزن بالكيلوجرام" required>
            <input type="number" id="height" placeholder="الطول بالسنتيمتر" required>
            <input type="number" id="age" placeholder="العمر بالسنوات" required>
            <select id="goal">
                <option value="maintain">الحفاظ على الوزن</option>
                <option value="gain">زيادة الوزن</option>
                <option value="lose">خسارة الوزن</option>
            </select>
            <button type="button" onclick="calculateCalories()">احسب</button>
        </form>
        <div class="result" id="result"></div>
    </div>
    <div class="footer">تم تصميم الموقع لصديقي بودا محمد ❤️</div>

    <script>
        function calculateCalories() {
            const weight = parseFloat(document.getElementById('weight').value);
            const height = parseFloat(document.getElementById('height').value);
            const age = parseInt(document.getElementById('age').value);
            const goal = document.getElementById('goal').value;

            if (!weight || !height || !age) {
                alert("من فضلك أدخل القيم الصحيحة");
                return;
            }

            // حساب معدل الحرق الأساسي (BMR) باستخدام معادلة Mifflin-St Jeor
            const bmr = (10 * weight) + (6.25 * height) - (5 * age) + 5; // ذكر
            let dailyCalories = bmr * 1.2; // النشاط اليومي منخفض

            if (goal === "gain") {
                dailyCalories += 500; // إضافة سعرات لزيادة الوزن
            } else if (goal === "lose") {
                dailyCalories -= 500; // تقليل سعرات لخسارة الوزن
            }

            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `
                <p>السعرات اليومية المطلوبة: <strong>${dailyCalories.toFixed(2)}</strong> سعر حراري</p>
                <p>هدفك هو: <strong>${goal === "gain" ? "زيادة الوزن" : goal === "lose" ? "خسارة الوزن" : "الحفاظ على الوزن"}</strong></p>
            `;
        }
    </script>
</body>
</html>
