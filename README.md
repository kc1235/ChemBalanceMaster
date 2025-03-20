<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ChemBalance Master 2.0</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #6200EA;
            --primary-light: #B388FF;
            --primary-dark: #4527A0;
            --accent-color: #00BFA5;
            --background-color: #F5F7FF;
            --card-bg: #FFFFFF;
            --text-color: #37474F;
            --text-light: #FFFFFF;
            --error-color: #F44336;
            --success-color: #4CAF50;
            --shadow-color: rgba(0, 0, 0, 0.15);
            --transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Poppins', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: var(--background-color);
            background-image: radial-gradient(circle at 10% 20%, rgba(98, 0, 234, 0.05) 0%, rgba(0, 191, 165, 0.07) 90%);
            color: var(--text-color);
            padding: 1rem;
        }

        .container {
            background-color: var(--card-bg);
            padding: 2.5rem;
            border-radius: 16px;
            box-shadow: 0 10px 30px var(--shadow-color);
            max-width: 850px;
            width: 95%;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .container::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 8px;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
        }

        h1 {
            text-align: center;
            color: var(--primary-color);
            margin-bottom: 1.5rem;
            font-weight: 700;
            letter-spacing: -0.5px;
            font-size: 2.2rem;
        }

        .tagline {
            text-align: center;
            margin-bottom: 2rem;
            color: var(--text-color);
            opacity: 0.8;
            font-size: 1rem;
        }

        .equation {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            margin: 1.5rem 0;
            font-size: 1.6rem;
            background-color: rgba(179, 136, 255, 0.1);
            padding: 1.5rem;
            border-radius: 10px;
            line-height: 2.5rem;
        }

        input {
            width: 48px;
            height: 48px;
            font-size: 1.5rem;
            text-align: center;
            margin: 0 0.5rem;
            border: none;
            border-bottom: 3px solid var(--primary-light);
            background-color: rgba(179, 136, 255, 0.15);
            border-radius: 8px;
            transition: var(--transition);
            color: var(--primary-dark);
            font-weight: 500;
            font-family: 'Poppins', sans-serif;
        }

        input:focus {
            outline: none;
            border-bottom: 3px solid var(--accent-color);
            box-shadow: 0 4px 8px rgba(0, 191, 165, 0.2);
            background-color: rgba(0, 191, 165, 0.1);
        }

        button {
            display: block;
            margin: 1.5rem auto;
            padding: 0.75rem 2rem;
            font-size: 1.1rem;
            background-color: var(--primary-color);
            color: var(--text-light);
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
            box-shadow: 0 4px 8px rgba(98, 0, 234, 0.25);
            font-weight: 500;
            font-family: 'Poppins', sans-serif;
            letter-spacing: 0.5px;
        }

        button:hover {
            background-color: var(--primary-dark);
            box-shadow: 0 6px 12px rgba(98, 0, 234, 0.35);
            transform: translateY(-2px);
        }

        button:active {
            transform: translateY(0);
            box-shadow: 0 2px 4px rgba(98, 0, 234, 0.25);
        }

        #result {
            text-align: center;
            margin-top: 1.5rem;
            font-weight: 500;
            min-height: 1.8em;
            transition: var(--transition);
            font-size: 1.2rem;
            padding: 0.75rem;
            border-radius: 8px;
        }

        #menu {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        #menu button {
            margin: 0.8rem;
            width: 240px;
        }

        #about {
            text-align: center;
            margin-top: 1.5rem;
            line-height: 1.6;
        }

        #about p {
            margin-bottom: 1rem;
        }

        .fade-in {
            animation: fadeIn 0.6s cubic-bezier(0.4, 0.0, 0.2, 1);
        }

        .slide-in {
            animation: slideIn 0.6s cubic-bezier(0.4, 0.0, 0.2, 1);
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideIn {
            from { transform: translateY(-30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(98, 0, 234, 0.4); }
            70% { box-shadow: 0 0 0 10px rgba(98, 0, 234, 0); }
            100% { box-shadow: 0 0 0 0 rgba(98, 0, 234, 0); }
        }

        .score-board {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: rgba(98, 0, 234, 0.9);
            color: var(--text-light);
            padding: 0.75rem 1.5rem;
            border-radius: 12px;
            margin-bottom: 1.5rem;
            box-shadow: 0 4px 8px var(--shadow-color);
        }

        .score-board div {
            font-weight: 600;
            font-size: 1.1rem;
        }

        #menuButton {
            position: absolute;
            top: 20px;
            right: 20px;
            background-color: var(--accent-color);
            padding: 0.5rem 1rem;
            font-size: 0.9rem;
            z-index: 10;
            box-shadow: 0 2px 6px rgba(0, 191, 165, 0.3);
        }

        #menuButton:hover {
            background-color: #00A896;
        }

        .difficulty {
            display: flex;
            justify-content: center;
            margin: 1rem 0;
            gap: 1rem;
        }

        .difficulty button {
            margin: 0;
            padding: 0.5rem 1rem;
            font-size: 0.9rem;
            width: auto;
        }

        .hint-button {
            background-color: var(--accent-color);
            font-size: 0.9rem;
            padding: 0.5rem 1rem;
            margin-top: 0;
        }

        .hint-button:hover {
            background-color: #00A896;
        }

        #hint {
            margin-top: 1rem;
            padding: 1rem;
            background-color: rgba(0, 191, 165, 0.1);
            border-radius: 8px;
            display: none;
            text-align: center;
            font-size: 0.9rem;
        }

        .level-indicator {
            display: flex;
            justify-content: center;
            margin-top: 1rem;
            gap: 0.5rem;
        }

        .level-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background-color: var(--primary-light);
            opacity: 0.3;
        }

        .level-dot.active {
            opacity: 1;
            background-color: var(--primary-color);
        }

        .streak-indicator {
            position: absolute;
            top: 20px;
            left: 20px;
            background-color: var(--primary-light);
            color: var(--text-light);
            padding: 0.4rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        @media (max-width: 768px) {
            .container {
                padding: 1.5rem;
            }

            h1 {
                font-size: 1.8rem;
            }

            .equation {
                font-size: 1.3rem;
                padding: 1rem;
                line-height: 2.2rem;
            }

            input {
                width: 40px;
                height: 40px;
                font-size: 1.3rem;
            }

            .score-board div {
                font-size: 1rem;
            }
        }

        @media (max-width: 480px) {
            .container {
                padding: 1rem;
            }

            h1 {
                font-size: 1.5rem;
            }

            .equation {
                font-size: 1.1rem;
                padding: 0.8rem;
                line-height: 2rem;
            }

            input {
                width: 32px;
                height: 32px;
                font-size: 1.1rem;
                margin: 0 0.3rem;
            }

            button {
                font-size: 1rem;
                padding: 0.6rem 1.5rem;
            }

            .score-board {
                padding: 0.5rem 1rem;
            }

            .score-board div {
                font-size: 0.9rem;
            }

            #menuButton {
                top: 10px;
                right: 10px;
                padding: 0.4rem 0.8rem;
                font-size: 0.8rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>ChemBalance Master 2.0</h1>
        <div id="menu" class="fade-in">
            <p class="tagline">Master chemical equation balancing with this interactive game!</p>
            <button onclick="startGame('easy')" class="slide-in pulse">Start Easy Mode</button>
            <button onclick="startGame('medium')" class="slide-in">Start Medium Mode</button>
            <button onclick="startGame('hard')" class="slide-in">Start Hard Mode</button>
            <button onclick="showAbout()" class="slide-in">About</button>
            <button onclick="quitGame()" class="slide-in">Quit</button>
        </div>
        <div id="gameArea" style="display:none;">
            <button id="menuButton" onclick="showMenu()">Menu</button>
            <div class="streak-indicator" id="streak">Streak: 0</div>
            <div class="score-board slide-in">
                <div id="level">Level: 1</div>
                <div id="score">Score: 0</div>
                <div id="difficulty">Easy</div>
            </div>
            <div class="equation" id="equationContainer"></div>
            <button onclick="checkBalance()">Check Balance</button>
            <button onclick="showHint()" class="hint-button">Hint</button>
            <div id="hint"></div>
            <div id="result"></div>
            <div class="level-indicator" id="levelIndicator"></div>
        </div>
        <div id="about" style="display:none;">
            <p>ChemBalance Master 2.0 is an educational game designed to improve your chemical equation balancing skills.</p>
            <p>The game features three difficulty levels with progressively challenging equations.</p>
            <p>Each correctly balanced equation increases your score and advances your level.</p>
            <p>Created by Anyanwu Kelechi Francis</p>
            <p>Updated in 2025</p>
            <button onclick="showMenu()">Back to Menu</button>
        </div>
    </div>

    <script>
        const easyEquations = [
            { reactants: ['H₂', 'O₂'], products: ['H₂O'], coefficients: [2, 1, 2], hint: "Count hydrogen and oxygen atoms on both sides" },
            { reactants: ['N₂', 'H₂'], products: ['NH₃'], coefficients: [1, 3, 2], hint: "Each NH₃ has 3 H atoms and 1 N atom" },
            { reactants: ['Na', 'Cl₂'], products: ['NaCl'], coefficients: [2, 1, 2], hint: "Each Cl₂ has 2 Cl atoms" },
            { reactants: ['CH₄', 'O₂'], products: ['CO₂', 'H₂O'], coefficients: [1, 2, 1, 2], hint: "Count carbon, hydrogen, and oxygen atoms" },
            { reactants: ['C₃H₈', 'O₂'], products: ['CO₂', 'H₂O'], coefficients: [1, 5, 3, 4], hint: "Balance carbon first, then hydrogen, then oxygen" },
            { reactants: ['Zn', 'HCl'], products: ['ZnCl₂', 'H₂'], coefficients: [1, 2, 1, 1], hint: "Each ZnCl₂ needs 2 Cl atoms" },
            { reactants: ['Fe', 'O₂'], products: ['Fe₂O₃'], coefficients: [4, 3, 2], hint: "Each Fe₂O₃ has 2 Fe atoms and 3 O atoms" },
            { reactants: ['H₂', 'N₂'], products: ['NH₃'], coefficients: [3, 1, 2], hint: "Each NH₃ has 3 H atoms and 1 N atom" },
            { reactants: ['Na', 'H₂O'], products: ['NaOH', 'H₂'], coefficients: [2, 2, 2, 1], hint: "Count sodium, hydrogen, and oxygen atoms" },
            { reactants: ['C₂H₆', 'O₂'], products: ['CO₂', 'H₂O'], coefficients: [2, 7, 4, 6], hint: "Balance carbon first, then hydrogen, then oxygen" }
        ];

        const mediumEquations = [
            { reactants: ['Al', 'HCl'], products: ['AlCl₃', 'H₂'], coefficients: [2, 6, 2, 3], hint: "Each AlCl₃ has 3 Cl atoms" },
            { reactants: ['NaHCO₃', 'HCl'], products: ['NaCl', 'H₂O', 'CO₂'], coefficients: [1, 1, 1, 1, 1], hint: "Count Na, H, C, O, and Cl atoms" },
            { reactants: ['C₆H₁₂O₆'], products: ['C₂H₅OH', 'CO₂'], coefficients: [1, 2, 2], hint: "Balance carbon first" },
            { reactants: ['KClO₃'], products: ['KCl', 'O₂'], coefficients: [2, 2, 3], hint: "Each KClO₃ has 3 O atoms" },
            { reactants: ['Cu', 'HNO₃'], products: ['Cu(NO₃)₂', 'NO', 'H₂O'], coefficients: [3, 8, 3, 2, 4], hint: "Balance Cu first, then N, then O, then H" },
            { reactants: ['Fe₂O₃', 'CO'], products: ['Fe', 'CO₂'], coefficients: [1, 3, 2, 3], hint: "Count iron, carbon, and oxygen atoms" },
            { reactants: ['SiCl₄', 'H₂O'], products: ['Si(OH)₄', 'HCl'], coefficients: [1, 4, 1, 4], hint: "Each SiCl₄ reacts with 4 H₂O molecules" },
            { reactants: ['Na₂CO₃', 'HCl'], products: ['NaCl', 'H₂O', 'CO₂'], coefficients: [1, 2, 2, 1, 1], hint: "Count Na, H, C, O, and Cl atoms" },
            { reactants: ['H₃PO₄', 'NaOH'], products: ['Na₃PO₄', 'H₂O'], coefficients: [1, 3, 1, 3], hint: "Each H₃PO₄ has 3 H atoms that can be replaced" },
            { reactants: ['Mg(OH)₂', 'HCl'], products: ['MgCl₂', 'H₂O'], coefficients: [1, 2, 1, 2], hint: "Count Mg, O, H, and Cl atoms" }
        ];

        const hardEquations = [
            { reactants: ['KMnO₄', 'HCl'], products: ['KCl', 'MnCl₂', 'H₂O', 'Cl₂'], coefficients: [2, 16, 2, 2, 8, 5], hint: "This is a redox reaction. Balance K, Mn first, then Cl" },
            { reactants: ['C₆H₁₂O₆', 'O₂'], products: ['CO₂', 'H₂O'], coefficients: [1, 6, 6, 6], hint: "Complete combustion. Count C, H, and O atoms" },
            { reactants: ['K₄Fe(CN)₆', 'H₂SO₄', 'H₂O'], products: ['K₂SO₄', 'FeSO₄', '(NH₄)₂SO₄', 'CO'], coefficients: [1, 6, 6, 2, 1, 3, 6], hint: "Balance K first, then Fe, C, N" },
            { reactants: ['K₂Cr₂O₇', 'H₂SO₄', 'C₂H₅OH'], products: ['Cr₂(SO₄)₃', 'K₂SO₄', 'CO₂', 'H₂O'], coefficients: [2, 8, 3, 2, 2, 6, 11], hint: "This is a redox reaction. Balance Cr and K first" },
            { reactants: ['Cu', 'HNO₃'], products: ['Cu(NO₃)₂', 'NO₂', 'H₂O'], coefficients: [1, 4, 1, 2, 2], hint: "Balance Cu first, then N, O, and H" },
            { reactants: ['Na₂S₂O₃', 'I₂'], products: ['Na₂S₄O₆', 'NaI'], coefficients: [2, 1, 1, 2], hint: "Count Na, S, O, and I atoms" },
            { reactants: ['KClO₃', 'KBr', 'HCl'], products: ['Br₂', 'KCl', 'H₂O', 'Cl₂'], coefficients: [1, 5, 6, 5, 6, 3, 3], hint: "This is a complex redox reaction. Balance K first" },
            { reactants: ['P₄', 'OH⁻', 'H₂O'], products: ['PH₃', 'HPO₃²⁻'], coefficients: [1, 3, 3, 1, 3], hint: "Balance P first, then H and O" },
            { reactants: ['H₂O₂', 'KMnO₄', 'H₂SO₄'], products: ['O₂', 'MnSO₄', 'K₂SO₄', 'H₂O'], coefficients: [5, 2, 3, 5, 2, 1, 8], hint: "This is a redox reaction. Balance Mn and K first" },
            { reactants: ['K₄[Fe(CN)₆]', 'KMnO₄', 'H₂SO₄'], products: ['KHSO₄', 'Fe₂(SO₄)₃', 'MnSO₄', 'HNO₃', 'CO₂'], coefficients: [1, 10, 98, 28, 1, 10, 10, 6], hint: "This is very complex. Balance K first, then Fe, Mn, N, C" }
        ];

        let currentLevel = 1;
        let score = 0;
        let streak = 0;
        let currentEquation = {};
        let currentDifficulty = 'easy';
        let equationsPool = easyEquations;
        let maxLevel = 10;

        const $ = (id) => document.getElementById(id);

        const loadGame = () => {
            currentLevel = parseInt(localStorage.getItem('level')) || 1;
            score = parseInt(localStorage.getItem('score')) || 0;
            streak = parseInt(localStorage.getItem('streak')) || 0;
            currentDifficulty = localStorage.getItem('difficulty') || 'easy';
            updateDisplay();
            updateLevelIndicator();
        };

        const saveGame = () => {
            localStorage.setItem('level', currentLevel);
            localStorage.setItem('score', score);
            localStorage.setItem('streak', streak);
            localStorage.setItem('difficulty', currentDifficulty);
        };

        const updateDisplay = () => {
            $('level').textContent = `Level: ${currentLevel}/${maxLevel}`;
            $('score').textContent = `Score: ${score}`;
            $('difficulty').textContent = currentDifficulty.charAt(0).toUpperCase() + currentDifficulty.slice(1);
            $('streak').textContent = `Streak: ${streak}`;
        };

        const updateLevelIndicator = () => {
            const indicator = $('levelIndicator');
            indicator.innerHTML = '';
            
            for (let i = 1; i <= maxLevel; i++) {
                const dot = document.createElement('div');
                dot.className = 'level-dot';
                if (i <= currentLevel) dot.classList.add('active');
                indicator.appendChild(dot);
            }
        };

        const generateEquation = () => {
            // Select equation based on current level and difficulty
            let equationIndex = (currentLevel - 1) % equationsPool.length;
            currentEquation = { ...equationsPool[equationIndex] };
            
            const container = $('equationContainer');
            container.innerHTML = '';

            const appendElement = (element) => container.appendChild(element);

            const createInput = () => {
                const input = document.createElement('input');
                input.type = 'number';
                input.min = '1';
                input.max = '20';
                input.classList.add('slide-in');
                return input;
            };

            const createText = (text) => {
                const span = document.createElement('span');
                span.textContent = text;
                span.classList.add('slide-in');
                return span;
            };

            currentEquation.reactants.forEach((reactant, index) => {
                if (index > 0) appendElement(createText(' + '));
                appendElement(createInput());
                appendElement(createText(' ' + reactant));
            });

            appendElement(createText(' → '));

            currentEquation.products.forEach((product, index) => {
                if (index > 0) appendElement(createText(' + '));
                appendElement(createInput());
                appendElement(createText(' ' + product));
            });

            // Hide hint
            $('hint').style.display = 'none';
        };

        const showHint = () => {
            const hintElement = $('hint');
            hintElement.textContent = currentEquation.hint || "Balance the number of atoms of each element on both sides of the equation.";
            hintElement.style.display = 'block';
            
            // Deduct points for using a hint
            score = Math.max(0, score - 2);
            updateDisplay();
            saveGame();
        };

        const checkBalance = () => {
            const inputs = document.querySelectorAll('input');
            const userCoefficients = Array.from(inputs).map(input => parseInt(input.value) || 0);
            const result = $('result');

            // Check if all inputs are filled
            if (userCoefficients.some(coef => coef === 0)) {
                result.textContent = "Please fill in all coefficients!";
                result.style.color = "var(--error-color)";
                result.style.backgroundColor = "rgba(244, 67, 54, 0.1)";
                return;
            }

            if (areCoefficientsEquivalent(userCoefficients, currentEquation.coefficients)) {
                result.textContent = "Correct! Moving to the next level.";
                result.style.color = "var(--success-color)";
                result.style.backgroundColor = "rgba(76, 175, 80, 0.1)";
                
                // Calculate score based on difficulty
                let levelScore = 10;
                if (currentDifficulty === 'medium') levelScore = 15;
                if (currentDifficulty === 'hard') levelScore = 25;
                
                // Add streak bonus
                streak++;
                let streakBonus = Math.min(5, Math.floor(streak / 3));
                score += levelScore + streakBonus;
                
                // Level progression
                currentLevel++;
                if (currentLevel > maxLevel) {
                    result.textContent = `Congratulations! You've completed all ${currentDifficulty} levels! Return to menu to try another difficulty.`;
                    result.style.color = "var(--primary-color)";
                    result.style.backgroundColor = "rgba(98, 0, 234, 0.1)";
                    setTimeout(() => {
                        showMenu();
                    }, 3000);
                } else {
                    setTimeout(() => {
                        generateEquation();
                        result.textContent = "";
                        result.style.backgroundColor = "transparent";
                    }, 1500);
                }
                
                updateDisplay();
                updateLevelIndicator();
                saveGame();
            } else {
                result.textContent = "Incorrect. Try again!";
                result.style.color = "var(--error-color)";
                result.style.backgroundColor = "rgba(244, 67, 54, 0.1)";
                score = Math.max(0, score - 5);
                streak = 0;
                updateDisplay();
                saveGame();
            }
        };

        // Function to check if coefficients are equivalent
        // (accounts for different valid ways to balance the same equation)
        const areCoefficientsEquivalent = (userCoefs, correctCoefs) => {
            if (userCoefs.length !== correctCoefs.length) return false;
            
            // Check if user coefficients are proportional to correct ones
            const ratio = userCoefs[0] / correctCoefs[0];
            
            for (let i = 0; i < userCoefs.length; i++) {
                if (userCoefs[i] / correctCoefs[i] !== ratio) return false;
            }
            
            return true;
        };

        const startGame = (difficulty) => {
            currentDifficulty = difficulty;
            currentLevel = 1;
            
            switch(difficulty) {
                case 'easy':
                    equationsPool = easyEquations;
                    break;
                case 'medium':
                    equationsPool = mediumEquations;
                    break;
                case 'hard':
                    equationsPool = hardEquations;
                    break;
                default:
                    equationsPool = easyEquations;
            }
            
            maxLevel = 10;
            
            $('menu').style.display = 'none';
            $('gameArea').style.display = 'block';
            $('about').style.display = 'none';
            $('gameArea').classList.add('fade-in');
            
            loadGame();
            generateEquation();
            updateLevelIndicator();
        };

        const showAbout = () => {
            $('menu').style.display = 'none';
            $('gameArea').style.display = 'none';
            $('about').style.display = 'block';
            $('about').classList.add('fade-in');
        };

        const showMenu = () => {
            $('menu').style.display = 'flex';
            $('gameArea').style.display = 'none';
            $('about').style.display = 'none';
            $('menu').classList.add('fade-in');
        };

        const quitGame = () => {
            if (confirm("Are you sure you want to quit? Your progress will be saved.")) {
                saveGame();
                window.close();
            }
        };

        showMenu();
    </script>
</body>
</html>
