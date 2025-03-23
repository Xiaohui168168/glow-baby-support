<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>グローバビーサポート (Glow Baby Support)</title>
    <style>
        /* 原有样式代码保留，此处省略，需确保样式完整 */
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">
            <h1>グローバビーサポート (Glow Baby Support)</h1>
        </div>
        <!-- 消息显示区域 -->
        <div class="chat-messages" id="chat-messages"></div> 
        <!-- 输入框和发送按钮 -->
        <div class="chat-input">
            <input type="text" id="user-input" placeholder="メッセージを入力してください">
            <button id="send-button">送信</button>
        </div>
    </div>
    <script>
        // 获取页面元素
        const chatMessages = document.getElementById('chat-messages');
        const userInput = document.getElementById('user-input');
        const sendButton = document.getElementById('send-button');

        // 生成回复的函数（可根据业务需求扩展回复逻辑）
        function generateReply(customerMessage) {
            if (customerMessage.includes('产品效果')) {
                return "こちらの商品は、多くのお客様から高い評価をいただいており、実際に効果があることが証明されていますよ😊。";
            } else if (customerMessage.includes('价格')) {
                return "価格は合理的で、今のところ特典もありますので、お得にお買い求めいただけますよ😃。";
            } else {
                return "お問い合わせいただきありがとうございます。もう少し詳しく教えていただけると、より適切な回答ができます🙏。";
            }
        }

        // 发送消息逻辑
        function sendMessage() {
            const message = userInput.value.trim();
            if (!message) return;

            // 显示用户消息
            const userDiv = document.createElement('div');
            userDiv.className = 'chat-message user-message';
            userDiv.textContent = message;
            chatMessages.appendChild(userDiv);

            // 生成并显示机器人回复
            const reply = generateReply(message);
            const botDiv = document.createElement('div');
            botDiv.className = 'chat-message bot-message';
            botDiv.textContent = reply;
            chatMessages.appendChild(botDiv);

            userInput.value = ''; // 清空输入框
            chatMessages.scrollTop = chatMessages.scrollHeight; // 滚动到最新消息
        }

        // 绑定按钮点击和回车发送事件
        sendButton.addEventListener('click', sendMessage);
        userInput.addEventListener('keydown', (e) => {
            if (e.key === 'Enter') sendMessage();
        });
    </script>
</body>
</html>
