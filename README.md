<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Chatbot</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      background-color: #f7f7f7;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .chat-container {
      background-color: black;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      width: 400px;
      height: 500px;
      display: flex;
      flex-direction: column;
    }

    .chat-box {
      flex-grow: 1;
      padding: 10px;
      overflow-y: auto;
      border-bottom: 1px solid #ddd;
      display: flex;
      flex-direction: column;
    }

    .user-input {
      display: flex;
      padding: 10px;
      background-color: #f1f1f1;
      border-top: 1px solid #ddd;
    }

    .user-input input {
      flex-grow: 1;
      padding: 8px;
      border: none;
      border-radius: 4px;
      font-size: 16px;
    }

    .user-input button {
      padding: 8px 16px;
      background-color: green;
      color: #fff;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      margin-left: 8px;
    }

    .user-input button:hover {
      background-color: #0056b3;
    }

    .message {
      margin: 5px;
      padding: 10px;
      border-radius: 6px;
      max-width: 70%;
    }

    .user-message {
      background-color: greenyellow;
      color: #fff;
      align-self: flex-end;
    }

    .bot-message {
      background-color: #f1f1f1;
      color: purple;
      align-self: flex-start;
    }
  </style>
</head>
<body>
  <div class="chat-container">
    <div class="chat-box" id="chat-box">
      <!-- Chat messages will appear here -->
    </div>
    <div class="user-input">
      <input type="text" id="user-message" placeholder="Type a message..." />
      <button onclick="sendMessage()">Send</button>
    </div>
  </div>

  <script>
    // A simple list of responses for the bot
    const botResponses = {
      "hello": "Hi! How can I help you today?",
      "how are you": "I'm good, thanks for asking! How can I assist you?",
      "bye": "Goodbye! Have a great day!",
      "what is my name": "your name is Mohsin",
      "what is my friend name": "your friend name is Anas",
    };

    // Function to send user message
    function sendMessage() {
      const userMessage = document.getElementById("user-message").value;
      if (!userMessage) return;

      // Display user message
      displayMessage(userMessage, 'user');

      // Clear input field
      document.getElementById("user-message").value = "";

      // Get bot response
      const botResponse = getBotResponse(userMessage.toLowerCase());
      
      // Display bot message after 1 second delay
      setTimeout(() => displayMessage(botResponse, 'bot'), 1000);
    }

    // Function to display a message in the chat box
    function displayMessage(message, sender) {
      const chatBox = document.getElementById("chat-box");
      
      const messageDiv = document.createElement("div");
      messageDiv.classList.add("message", sender === 'user' ? "user-message" : "bot-message");
      messageDiv.innerText = message;

      chatBox.appendChild(messageDiv);
      chatBox.scrollTop = chatBox.scrollHeight;  // Scroll to the latest message
    }

    // Function to get bot's response based on user input
    function getBotResponse(userMessage) {
      if (botResponses[userMessage]) {
        return botResponses[userMessage];
      } else {
        return "Hello, Iam chatboot how can I help you";
      }
    
      }
      
      
  </script>
</body>
</html>
