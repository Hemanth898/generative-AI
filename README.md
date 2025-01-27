HTML CODES:
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generative AI Project</title>
    <link rel="stylesheet" href="STYLE.css">
</head>

<body>
    <div class="container">
        <header>
            <h1>Generative AI Project</h1>
            <p>Your AI assistant for all your needs.</p>
        </header>
        <main>
            <section class="profile">
                <img src="https://herobot.app/wp-content/uploads/2022/11/AI-bot-1.jpg" alt="AI Profile Picture" class="profile-pic">
                <p class="profile-description">Meet your AI assistant, always ready to help you with your queries.</p>
            </section>
            <section class="features">
                <h2>Features</h2>
                <ul>
                    <li>Answering questions</li>
                    <li>Engaging in conversations</li>
                    <li>Providing information</li>
                </ul>
            </section>
            <section class="interaction">
                <h2>Interact with AI</h2>
                <div id="ai-interaction">
                    <input type="text" id="user-input" placeholder="Ask me anything...">
                    <button id="send-button">Send</button>
                    <div id="response"></div>
                </div>
            </section>
        </main>
        <footer>
            <p>Built with ❤️ during the Generative AI workshop</p>
        </footer>
    </div>
    <script src="AI.js"></script>
</body>

</html>



CSS CODES@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

body {
    font-family: 'Roboto', sans-serif;
    background: linear-gradient(135deg, #2C3E50, #4CA1AF);
    margin: 0;
    padding: 0;
    color: #ECF0F1;
}

.container {
    max-width: 800px;
    margin: 40px auto;
    padding: 20px;
    background-color: rgba(255, 255, 255, 0.1);
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
    border-radius: 10px;
}

header {
    text-align: center;
    margin-bottom: 20px;
}

header h1 {
    margin: 0;
    font-size: 2.5em;
    color: #FFFFFF;
}

header p {
    margin: 0;
    color: #BDC3C7;
}

.profile {
    text-align: center;
    margin-bottom: 20px;
}

.profile-pic {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    object-fit: cover;
    margin-bottom: 10px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
}

.profile-description {
    color: #BDC3C7;
}

.features {
    margin-bottom: 20px;
}

.features h2 {
    color: #FFFFFF;
}

.features ul {
    list-style-type: none;
    padding: 0;
}

.features li {
    background-color: rgba(44, 62, 80, 0.5);
    margin: 5px 0;
    padding: 10px;
    border-radius: 5px;
    color: #ECF0F1;
}

.interaction {
    margin-bottom: 20px;
}

.interaction h2 {
    color: #FFFFFF;
}

#ai-interaction {
    display: flex;
    flex-direction: column;
    align-items: center;
}

#user-input {
    width: 100%;
    max-width: 600px;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #2C3E50;
    color: #ECF0F1;
}

#send-button {
    padding: 10px 20px;
    border: none;
    background-color: #4CA1AF;
    color: #fff;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

#send-button:hover {
    background-color: #3B99A1;
}

#response {
    margin-top: 20px;
    width: 100%;
    max-width: 600px;
    padding: 10px;
    background-color: rgba(44, 62, 80, 0.5);
    border-radius: 5px;
    text-align: left;
    color: #ECF0F1;
}

footer {
    text-align: center;
    color: #BDC3C7;
    margin-top: 20px;
}


JAVASCRIPT CODE
document.addEventListener('DOMContentLoaded', function () {
    const userInput = document.getElementById('user-input');
    const sendButton = document.getElementById('send-button');
    const responseDiv = document.getElementById('response');

    sendButton.addEventListener('click', function () {
        const userText = userInput.value;
        if (userText.trim() !== '') {
            responseDiv.innerHTML = '<p>Thinking...</p>';
            fetch('https://api.example.com/ai-response', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': 'Bearer YOUR_API_KEY'
                },
                body: JSON.stringify({ query: userText })
            })
            .then(response => response.json())
            .then(data => {
                responseDiv.innerHTML = `<p>You asked: ${userText}</p><p>AI response: ${data.response}</p>`;
            })
            .catch(error => {
                responseDiv.innerHTML = `<p>Error: ${error.message}</p>`;
            });
        }
    });
});
