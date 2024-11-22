<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arb-Eng shifting Mistake Repair</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f7f7f7;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
        }

        h1 {
            color: #333;
            font-size: 32px;
            margin-bottom: 20px;
        }

        p {
            color: #555;
            font-size: 16px;
            margin-bottom: 10px;
        }

        textarea {
            width: 80%;
            max-width: 600px;
            height: 150px;
            margin-bottom: 20px;
            padding: 15px;
            font-size: 16px;
            border-radius: 8px;
            border: 1px solid #ccc;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        textarea:focus {
            border-color: #4CAF50;
            outline: none;
            box-shadow: 0 2px 8px rgba(76, 175, 80, 0.3);
        }

        button {
            padding: 12px 30px;
            font-size: 16px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #45a049;
        }

        #result {
            margin-top: 20px;
            padding: 20px;
            width: 80%;
            max-width: 600px;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            word-wrap: break-word;
            color: #333;
            font-size: 16px;
        }

        /* Add a smooth background color transition */
        body {
            background: #e0f7fa;
            transition: background 0.3s ease;
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
