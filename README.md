<html>
  </head>
  <body>
      <h1 class="title">What's My Discount? </h1>
      <p id="currentTime"></p>
      <script src="script.js"></script>
  </body>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: white;
            font-family: Arial, sans-serif;
        }

        #logo {
            width: 300px; /* Adjust the size of your logo */
            margin-bottom: 20px; /* Space between logo and number box */
        }

        #numberBox {
            width: 200px;
            height: 100px;
            background-color: white;
            border: 4px solid #333;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 40px;
            font-weight: bold;
            color: #333;
            margin-bottom: 20px;
            transition: color 0.5s;
        }

        #generateBtn {
            padding: 15px 30px;
            font-size: 18px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            transition: background-color 0.3s;
        }

        #generateBtn:hover {
            background-color: #45a049;
        }

        @keyframes shake {
            0% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            50% { transform: translateX(5px); }
            75% { transform: translateX(-5px); }
            100% { transform: translateX(0); }
        }

        .shaking {
            animation: shake 0.1s;
            animation-iteration-count: 2;
        }
    </style>
</head>
<body>
    <!-- Add your logo here -->
    <img id="logo" src="https://www.proteindistrict.ae/web/image/website/1/logo/Protein%20District?unique=a808173" alt="Logo"> <!-- Replace with your logo URL -->
    <div id="numberBox">0%</div>
    <button id="generateBtn">Let's Go!</button>

    <script>
        const numberBox = document.getElementById('numberBox');
        const generateBtn = document.getElementById('generateBtn');
        let isAnimating = false;

        function generateRandomNumber() {
            if (isAnimating) return;
            
            isAnimating = true;
            generateBtn.disabled = true;
            let count = 0;
            const animationDuration = 2000; // 1 second
            const startTime = Date.now();

            function updateNumber() {
                if (Date.now() - startTime < animationDuration) {
                    numberBox.textContent = Math.floor(Math.random() * 20 + 5) + "%";
                    numberBox.classList.add('shaking');
                    requestAnimationFrame(updateNumber);
                } else {
                    const finalNumber = Math.floor(Math.random() * 20 + 5);
                    numberBox.textContent = finalNumber + "%";
                    numberBox.classList.remove('shaking');
                    isAnimating = false;
                    generateBtn.disabled = false;
                    
                    // Add color transition effect
                    numberBox.style.color = '#2196F3';
                    setTimeout(() => {
                        numberBox.style.color = 'green';
                    }, 500);
                }
            }

            updateNumber();
        }

        generateBtn.addEventListener('click', generateRandomNumber);
    </script>
</body>
</html>
