<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Keyboard Mistake Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            line-height: 1.6;
        }
        textarea {
            width: 100%;
            height: 100px;
            margin-bottom: 20px;
            padding: 10px;
            font-size: 16px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
        #result {
            margin-top: 20px;
            padding: 10px;
            background: #f4f4f4;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <h1>Keyboard Mistake Converter</h1>
    <p>Enter the text with incorrect keyboard language:</p>
    <textarea id="inputText" placeholder="Type here..."></textarea>
    <br>
    <button onclick="convertText()">Convert</button>
    <div id="result"></div>

    <script>
        // جدول تحويل الحروف
        const arabicToEnglish = {
            'ذ': '`', 'ض': 'q', 'ص': 'w', 'ث': 'e', 'ق': 'r', 'ف': 't', 'غ': 'y', 'ع': 'u', 'ه': 'i', 'خ': 'o', 'ح': 'p', 'ج': '[' , 'د': ']',
            'ش': 'a', 'س': 's', 'ي': 'd', 'ب': 'f', 'ل': 'g', 'ا': 'h', 'ت': 'j', 'ن': 'k', 'م': 'l',
            'ك': ';', 'ط': "'", 'ئ': 'z', 'ء': 'x', 'ؤ': 'c', 'ر': 'v', 'لا': 'b', 'ى': 'n', 'ة': 'm', 'و': ',',
            'ز': '.', 'ظ': '/'
        };

        const englishToArabic = Object.fromEntries(
            Object.entries(arabicToEnglish).map(([arabic, english]) => [english, arabic])
        );

        function convertText() {
            const inputText = document.getElementById('inputText').value;
            let result = '';

            // تحويل النص حرف حرف
            for (let char of inputText) {
                // إذا كان الحرف في اللغة العربية، نحوله إلى الإنجليزي
                if (arabicToEnglish[char]) {
                    result += arabicToEnglish[char];
                } 
                // إذا كان الحرف في اللغة الإنجليزية، نحوله إلى العربي
                else if (englishToArabic[char]) {
                    result += englishToArabic[char];
                } 
                // إذا لم يكن الحرف موجودًا في الجدولين، نتركه كما هو
                else {
                    result += char;
                }
            }

            // عرض النتيجة
            document.getElementById('result').textContent = result;
        }
    </script>
</body>
</html>
