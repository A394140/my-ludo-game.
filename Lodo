<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advance Ludo Game</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        #game-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        #ludo-board {
            width: 600px;
            height: 600px;
            background-color: #fff;
            border: 5px solid #333;
            display: grid;
            grid-template: repeat(15, 40px) / repeat(15, 40px);
            position: relative;
        }
        .cell {
            border: 1px solid #ccc;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 12px;
        }
        .home {
            background-color: #ff4d4d;
        }
        .path {
            background-color: #ffeb3b;
        }
        .safe {
            background-color: #4caf50;
        }
        .token {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            position: absolute;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
        }
        #dice {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 18px;
            background-color: #2196f3;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        #dice:hover {
            background-color: #1976d2;
        }
        #chat-box {
            width: 300px;
            height: 150px;
            margin-top: 20px;
            border: 1px solid #ccc;
            padding: 10px;
            overflow-y: scroll;
            background-color: #fff;
        }
        #chat-input {
            width: 300px;
            margin-top: 10px;
            padding: 5px;
        }
        #send-chat {
            padding: 5px 10px;
            background-color: #2196f3;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div id="game-container">
        <div id="ludo-board"></div>
        <button id="dice" onclick="rollDice()">Roll Dice</button>
        <div id="chat-box"></div>
        <input type="text" id="chat-input" placeholder="Type your message...">
        <button id="send-chat" onclick="sendMessage()">Send</button>
    </div>

    <script>
        const board = document.getElementById('ludo-board');
        const chatBox = document.getElementById('chat-box');
        const chatInput = document.getElementById('chat-input');
        let players = [
            { color: 'red', tokens: [{ id: 1, pos: 0 }, { id: 2, pos: 0 }], start: 0 },
            { color: 'green', tokens: [{ id: 1, pos: 0 }, { id: 2, pos: 0 }], start: 14 }
        ];
        let currentPlayer = 0;

        // Create the Ludo board
        function createBoard() {
            for (let i = 0; i < 15; i++) {
                for (let j = 0; j < 15; j++) {
                    const cell = document.createElement('div');
                    cell.classList.add('cell');
                    if ((i < 6 && j < 6) || (i < 6 && j >= 9) || (i >= 9 && j < 6) || (i >= 9 && j >= 9)) {
                        cell.classList.add('home');
                    } else if ((i === 6 || i === 8) && j >= 6 && j <= 8 || (j === 6 || j === 8) && i >= 6 && i <= 8) {
                        cell.classList.add('path');
                    } else if (i === 7 && j === 7) {
                        cell.classList.add('safe');
                    }
                    board.appendChild(cell);
                }
            }
            placeTokens();
        }

        // Place tokens on the board
        function placeTokens() {
            players.forEach(player => {
                player.tokens.forEach(token => {
                    const tokenEl = document.createElement('div');
                    tokenEl.classList.add('token');
                    tokenEl.style.backgroundColor = player.color;
                    tokenEl.innerText = token.id;
                    tokenEl.id = `${player.color}-${token.id}`;
                    board.appendChild(tokenEl);
                    moveToken(tokenEl, token.pos, player.start);
                });
            });
        }

        // Move token to a position
        function moveToken(tokenEl, pos, start) {
            const path = [/* Define a simple path for movement */];
            let cellIndex = start + pos;
            if (cellIndex >= 225) cellIndex = 224; // Boundary check
            const row = Math.floor(cellIndex / 15);
            const col = cellIndex % 15;
            tokenEl.style.left = `${col * 40 + 5}px`;
            tokenEl.style.top = `${row * 40 + 5}px`;
        }

        // Roll the dice
        function rollDice() {
            const diceResult = Math.floor(Math.random() * 6) + 1;
            alert(`Player ${currentPlayer + 1} rolled: ${diceResult}`);
            const player = players[currentPlayer];
            player.tokens[0].pos += diceResult;
            const tokenEl = document.getElementById(`${player.color}-1`);
            moveToken(tokenEl, player.tokens[0].pos, player.start);
            currentPlayer = (currentPlayer + 1) % players.length;
        }

        // Send chat message
        function sendMessage() {
            const message = chatInput.value;
            if (message.trim()) {
                const msgEl = document.createElement('div');
                msgEl.innerText = `Player ${currentPlayer + 1}: ${message}`;
                chatBox.appendChild(msgEl);
                chatBox.scrollTop = chatBox.scrollHeight;
                chatInput.value = '';
            }
        }

        // Initialize the game
        createBoard();
    </script>
</body>
</html>
