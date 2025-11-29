<!DOCTYPE html>
<html>
<head>
    <title>My Calculator</title>
<style>

#display {
    width: 250px;
    height: 50px;
    font-size: 24px;
    text-align: right;
    border: 2px solid #333;
    border-radius: 10px;
    margin-bottom: 20px;
    padding-right: 10px;
}

button {
    width: 60px;
    height: 60px;
    font-size: 22px;
    margin: 5px;
    border: none;
    border-radius: 10px;
    background-color: #444;
    color: white;
    cursor: pointer;
}

button:hover {
    background-color: #666;
}

.equal {
    background-color: #28a745;
    color: white;
}

.equal:hover {
    background-color: #218838;
}

.clear {
    background-color: #dc3545;
    color: white;
}

.clear:hover {
    background-color: #c82333;
}

div {
    margin-bottom: 5px;
}

#calculator {
    background-color: white;
    padding: 20px;
    width: 300px;
    margin: auto;
    border-radius: 15px;
    box-shadow: 0 0 20px rgba(0,0,0,0.2);
}

@media (max-width: 400px) {
    #calculator {
        width: 90%;
    }
    #display {
        width: 100%;
        font-size: 22px;
    }
    button {
        width: 70px;
        height: 60px;
        font-size: 20px;
    }
}

</style>
</head>

<body>

<div id="calculator">

    <input id="display" type="text">

    <div>
        <button onclick="press('1')">1</button>
        <button onclick="press('2')">2</button>
        <button onclick="press('3')">3</button>
    </div>

    <div>
        <button onclick="press('4')">4</button>
        <button onclick="press('5')">5</button>
        <button onclick="press('6')">6</button>
    </div>

    <div>
        <button onclick="press('7')">7</button>
        <button onclick="press('8')">8</button>
        <button onclick="press('9')">9</button>
    </div>

    <div>
        <button onclick="press('0')">0</button>
        <button onclick="press('+')">+</button>
        <button onclick="press('-')">-</button>
    </div>

    <div>
        <button onclick="press('*')">*</button>
        <button onclick="press('/')">/</button>
        <button class="equal" onclick="calculate()">=</button>
    </div>

    <div>
        <button class="clear" onclick="clearDisplay()">C</button>
    </div>

</div>

<script>

function press(value) {
    document.getElementById("display").value += value;
}

function calculate() {
    let expression = document.getElementById("display").value;
    document.getElementById("display").value = eval(expression);
}

function clearDisplay() {
    document.getElementById("display").value = "";
}

document.addEventListener("keydown", function(event) {
    let key = event.key;

    if ("0123456789+-*/".includes(key)) {
        press(key);
    }

    if (key === "Enter") {
        calculate();
    }

    if (key === "Backspace") {
        let display = document.getElementById("display");
        display.value = display.value.slice(0, -1);
    }

    if (key === "Escape") {
        clearDisplay();
    }
});

</script>

</body>
</html>
