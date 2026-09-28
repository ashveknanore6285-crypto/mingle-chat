```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Chat</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      background: #0b0b12;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .home {
      text-align: center;
      padding: 30px;
    }

    .home h1 {
      font-size: 42px;
      margin-bottom: 12px;
    }

    .home p {
      color: #aaa;
      margin-bottom: 30px;
    }

    .start-btn {
      border: none;
      padding: 15px 35px;
      border-radius: 30px;
      background: #7c3aed;
      color: white;
      font-size: 18px;
      cursor: pointer;
    }

    .start-btn:active {
      transform: scale(0.96);
    }

    .chat {
      display: none;
      width: 100%;
      max-width: 600px;
      height: 100vh;
      background: #11111a;
      position: relative;
      flex-direction: column;
    }

    .chat-header {
      padding: 18px;
      background: #181824;
      border-bottom: 1px solid #292936;
      font-size: 20px;
      font-weight: bold;
    }

    .messages {
      flex: 1;
      padding: 20px;
      overflow-y: auto;
    }

    .message {
      background: #7c3aed;
      padding: 10px 14px;
      border-radius: 18px;
      margin-bottom: 10px;
      max-width: 75%;
      margin-left: auto;
      word-wrap: break-word;
    }

    .input-area {
      display: flex;
      padding: 12px;
      gap: 8px;
      background: #181824;
    }

    .input-area input {
      flex: 1;
      padding: 13px;
      border: none;
      outline: none;
      border-radius: 25px;
      background: #292936;
      color: white;
      font-size: 16px;
    }

    .send-btn {
      border: none;
      width: 50px;
      border-radius: 50%;
      background: #7c3aed;
      color: white;
      font-size: 20px;
      cursor: pointer;
    }
  </style>
</head>

<body>

  <!-- HOME PAGE -->
  <div class="home" id="home">
    <h1>💬 My Chat</h1>
    <p>Welcome to your private chat space.</p>
    <button class="start-btn" onclick="openChat()">Start Chat</button>
  </div>

  <!-- CHAT PAGE -->
  <div class="chat" id="chat">

    <div class="chat-header">
      💬 My Chat
    </div>

    <div class="messages" id="messages">
      <div class="message">
        Welcome! 👋
      </div>
    </div>

    <div class="input-area">
      <input
        type="text"
        id="messageInput"
        placeholder="Type a message..."
        onkeydown="handleEnter(event)"
      >

      <button class="send-btn" onclick="sendMessage()">➤</button>
    </div>

  </div>

  <script>
    function openChat() {
      document.getElementById("home").style.display = "none";
      document.getElementById("chat").style.display = "flex";
    }

    function sendMessage() {
      const input = document.getElementById("messageInput");
      const message = input.value.trim();

      if (message === "") return;

      const messageBox = document.createElement("div");
      messageBox.className = "message";
      messageBox.textContent = message;

      document.getElementById("messages").appendChild(messageBox);

      input.value = "";

      const messages = document.getElementById("messages");
      messages.scrollTop = messages.scrollHeight;
    }

    function handleEnter(event) {
      if (event.key === "Enter") {
        sendMessage();
      }
    }
  </script>

</body>
</html>
```
